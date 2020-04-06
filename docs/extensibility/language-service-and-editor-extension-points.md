---
title: Dil Servisi ve Editör EkStansiyon Noktaları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703053"
---
# <a name="language-service-and-editor-extension-points"></a>Dil hizmeti ve editör uzantı noktaları
Düzenleyici, çoğu dil hizmeti özelliği de dahil olmak üzere Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçaları olarak genişletebileceğiniz uzantı noktaları sağlar. Bu ana uzantı noktası kategorileri şunlardır:

- İçerik türleri

- Sınıflandırma türleri ve sınıflandırma biçimleri

- Kenar boşlukları ve kaydırma çubukları

- Etiketler

- Süsleme -leri

- Fare işlemcileri

- Damla işleyicileri

- Seçenekler

- IntelliSense

## <a name="extend-content-types"></a>İçerik türlerini genişletme
 İçerik türleri, editör tarafından işlenen metin türlerinin tanımlarıdır, örneğin, "metin", "kod", veya "CSharp". Türün <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> değişkenini bildirerek ve yeni içerik türüne benzersiz bir ad vererek yeni bir içerik türü tanımlarsınız. İçerik türünü editöre kaydetmek için aşağıdaki özniteliklerle birlikte dışa aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>içerik türünün adıdır.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>bu içerik türünün türetildiği içerik türünün adıdır. İçerik türü birden çok içerik türünden devralınabilir.

  <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Sınıf mühürlü olduğundan, türü parametresi olmadan dışa aktarabilirsiniz.

  Aşağıdaki örnek, içerik türü tanımındaki dışa aktarma özniteliklerini gösterir.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 İçerik türleri sıfır veya daha fazla önceden varolan içerik türlerine dayalı olabilir. Bunlar yerleşik türleri şunlardır:

- Any: temel içerik türü. Diğer tüm içerik türlerinin üst öğesi.

- Metin: projeksiyon dışı içerik için temel tür. "Herhangi bir"den miras kalır.

- Düz metin: kod olmayan metin için. "metin"den devralır.

- Kod: her türlü kod için. "metin"den devralır.

- Durağan: metni her türlü işlemeden dışlar. Bu içerik türünün metnine hiçbir zaman herhangi bir uzantı uygulanmaz.

- Projeksiyon: projeksiyon arabelleklerinin içeriği için. "Herhangi bir"den miras kalır.

- Intellisense: IntelliSense içeriği için. "metin"den devralır.

- Sighelp: imza yardımı. "Intellisense"den miras kalır.

- Sighelp-doc: imza yardım belgeleri. "Intellisense"den miras kalır.

  Bunlar Visual Studio tarafından tanımlanan içerik türlerinden bazıları ve Visual Studio'da barındırılan dillerden bazılarıdır:

- Temel

- C/C++

- Konsol Çıktısı

- Csharp

- CSS

- Enc

- Sonuçları Bul

- F#

- HTML

- JScript

- XAML

- XML

  Kullanılabilir içerik türlerinin listesini bulmak <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>için, düzenleyici için içerik türlerinin toplanmasını sağlayan , Aşağıdaki kod bu hizmeti bir özellik olarak içeri aktlar.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 İçerik türünü dosya adı uzantısı ile <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>ilişkilendirmek için .

> [!NOTE]
> Visual Studio'da, dosya adı uzantıları <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> bir dil servis paketi kullanılarak kaydedilir. Mef <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> içerik türünü bu şekilde kaydedilmiş bir dosya adı uzantısı ile ilişkilendirer.

 Dosya adı uzantısını içerik türü tanımına aktarmak için aşağıdaki öznitelikleri eklemeniz gerekir:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: dosya adı uzantısını belirtir.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: içerik türünü belirtir.

  <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Sınıf mühürlü olduğundan, türü parametresi olmadan dışa aktarabilirsiniz.

  Aşağıdaki örnekte, bir içerik türü tanımına dosya adı uzantısı dışa aktarma öznitelikleri gösterilmektedir.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 Dosya <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> adı uzantıları ve içerik türleri arasındaki ilişkileri yönetir.

## <a name="extend-classification-types-and-classification-formats"></a>Sınıflandırma türlerini ve sınıflandırma biçimlerini genişletme
 Sınıflandırma türlerini, farklı işleme sağlamak istediğiniz metin türlerini tanımlamak için kullanabilirsiniz (örneğin, "anahtar kelime" metnimavive "yorum" metni ni yeşil boyama). Bir tür <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> değişkeni beyan ederek ve ona benzersiz bir ad vererek yeni bir sınıflandırma türü tanımlayın.

 Sınıflandırma türünü editöre kaydetmek için aşağıdaki özniteliklerle birlikte dışa aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: sınıflandırma türünün adı.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: bu sınıflandırma türünün devraldığı sınıflandırma türünün adı. Tüm sınıflandırma türleri "metin"den miras kalır ve bir sınıflandırma türü birden çok diğer sınıflandırma türünden devralınabilir.

  <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> Sınıf mühürlü olduğundan, türü parametresi olmadan dışa aktarabilirsiniz.

  Aşağıdaki örnek, bir sınıflandırma türü tanımında dışa aktarma özniteliklerini gösterir.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 Standart <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> sınıflandırmalara erişim sağlar. Yerleşik sınıflandırma türleri şunlardır:

- "metin"

- "doğal dil" ("metin"den türetilmiştir)

- "resmi dil" ("metin"den türetilmiştir)

- "string" ("literal"den türetilmiştir)

- "karakter" ("literal"den türetilmiştir)

- "sayısal" ("literal"den türetilmiştir)

  Farklı hata türleri kümesi <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>devralır. Bunlar aşağıdaki hata türlerini içerir:

- "sözdizimi hatası"

- "derleyici hatası"

- "diğer hata"

- "uyarı"

  Kullanılabilir sınıflandırma türlerinin listesini bulmak <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>için, düzenleyici için sınıflandırma türlerinin toplanmasını sağlayan , Aşağıdaki kod bu hizmeti bir özellik olarak içeri aktlar.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Yeni sınıflandırma türünüz için bir sınıflandırma biçimi tanımı tanımlayabilirsiniz. Bir sınıfı aşağıdaki <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> özniteliklerle birlikte <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>türle türetin ve dışa aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: biçimin adı.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: biçimin görüntü adı.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: biçimin **Seçenekler** iletişim kutusunun **Yazı Tipleri ve Renkler** sayfasında görünüp görünmediğini belirtir.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: biçimin önceliği. Geçerli değerler <xref:Microsoft.VisualStudio.Text.Classification.Priority>.

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: bu biçimin eşlendiği sınıflandırma türünün adı.

  Aşağıdaki örnek, bir sınıflandırma biçimi tanımında dışa aktarma özniteliklerini gösterir.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Kullanılabilir biçimlerin listesini bulmak için, <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>düzenleyici için biçimlerin toplanmasını sağlayan , Aşağıdaki kod bu hizmeti bir özellik olarak içeri aktlar.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Kenar boşluklarını ve kaydırma çubuklarını genişletme
 Kenar boşlukları ve kaydırma çubukları, metin görünümünün kendisine ek olarak düzenleyicinin ana görünüm öğeleridir. Metin görünümü nde görünen standart kenar boşluklarına ek olarak istediğiniz sayıda kenar boşluğu sağlayabilirsiniz.

 Kenar <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> boşluğu tanımlamak için bir arabirim uygulayın. Ayrıca kenar boşluğu <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> oluşturmak için arabirimi uygulamanız gerekir.

 Kenar boşluğu sağlayıcısını düzenleyiciye kaydettirmek için, sağlayıcıyı aşağıdaki özniteliklerle birlikte dışa aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kenar boşluğunun adı.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: diğer kenar boşluklarına göre marjın görüntülenme sırası.

   Yerleşik kenar boşlukları şunlardır:

  - "Wpf Yatay Kaydırma Çubuğu"

  - "Wpf Dikey Kaydırma Çubuğu"

  - "Wpf Satır Sayısı Kenar Boşluğu"

    Sipariş özniteliği `After="Wpf Horizontal Scrollbar"` olan yatay kenar boşlukları yerleşik kenar boşluğunun altında görüntülenir ve sipariş özniteliğiolan `Before ="Wpf Horizontal Scrollbar"` yatay kenar boşlukları yerleşik kenar boşluğunun üzerinde görüntülenir. Sipariş özniteliği `After="Wpf Vertical Scrollbar"` olan sağ dikey kenar boşlukları kaydırma çubuğunun sağında görüntülenir. Satır numarası kenar boşluğunun `After="Wpf Line Number Margin"` solunda görünen bir sipariş özniteliği olan sol dikey kenar boşlukları (görünürse).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: kenar boşluğu türü (sol, sağ, üst veya alt).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: marjınızın geçerli olduğu içerik türü (örneğin, "metin" veya "kod").

  Aşağıdaki örnek, satır numarası kenar boşluğunun sağında görünen bir kenar boşluğu için kenar boşluğu sağlayıcısındaki dışa aktarma özniteliklerini gösterir.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Etiketleri genişlet
 Etiketler, verileri farklı metin türleri ile ilişkilendirme yoludur. Çoğu durumda, ilişkili veriler görsel efekt olarak görüntülenir, ancak tüm etiketlerin görsel bir sunusu yoktur. Kendi etiketinizi uygulayarak <xref:Microsoft.VisualStudio.Text.Tagging.ITag>tanımlayabilirsiniz. Ayrıca, belirli <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> bir metin aralığı kümesi için etiketleri sağlamak <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ve etiketciyi sağlamak için de uygulamanız gerekir. Tagger sağlayıcısını aşağıdaki özniteliklerle birlikte dışa aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: etiketinizin geçerli olduğu içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: etiket türü.

  Aşağıdaki örnek, bir etiket sağlayıcıda dışa aktarma özniteliklerini gösterir.

\<CodeContentPlaceHolder></CodeContentPlaceHolder> 8 Aşağıdaki etiket türleri yerleşiktir:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: ile <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>ilişkili bir .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: hata türleri ile ilişkilidir.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: bir süs ile ilişkilidir.

  > [!NOTE]
  > Bir örnek <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>için, Walkthrough'daki HighlightWordTag [tanımına bakın: Metni Vurgulama](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: anahatlarında genişletilebilen veya daraltılabilen bölgelerle ilişkilidir.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: bir süslemenin metin görünümünde kapsaolduğu alanı tanımlar. Uzay pazarlığı süsleri hakkında daha fazla bilgi için aşağıdaki bölüme bakın.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: süs için otomatik aralık ve boyutlandırma sağlar.

  Arabellek ve görünümler için etiketleri <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> bulmak <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>ve kullanmak için, size istenen türden bir <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> bilgi veren veya alan veya alan. Aşağıdaki kod bu hizmeti bir özellik olarak içeri aktlar.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Etiketler ve MarkerFormatDefinitions
 Bir etiketin <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> görünümünü tanımlamak için sınıfı genişletebilirsiniz. Sınıfınızı dışa aktarmanız <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>gerekir (aşağıdaki özniteliklere sahip olarak:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: bu biçime başvurmak için kullanılan ad

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: bu, biçimin UI'de görünmesine neden olur

  Oluşturucuolarak, görüntü adını ve etiketgörünümünü tanımlarsınız. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>dolgu rengini tanımlar ve <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> kenarlık rengini tanımlar. Biçim <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> tanımının yerelleştirilebilir adıdır.

  Aşağıda biçim tanımına bir örnek verilmiştir:

```
[Export(typeof(EditorFormatDefinition))]
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
[UserVisible(true)]
internal class HighlightWordFormatDefinition : MarkerFormatDefinition
{
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
}

```

 Bu biçim tanımını bir etikete uygulamak için sınıfın ad özniteliğine ayarladığınız adı (görüntü adı değil) başvurun.

> [!NOTE]
> Bir örnek <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>için, Walkthrough'daki HighlightWordFormatDefinition [sınıfına bakın: Metni Vurgulama](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Süslemeleri genişletin
 Süslemeler, metin görünümünde görüntülenen metne veya metin görünümünün kendisine eklenebilecek görsel efektler tanımlar. Kendi süslemenizi herhangi bir tür <xref:System.Windows.UIElement>olarak tanımlayabilirsiniz.

 Süs sınıfınızda, bir <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Süs katmanınızı kaydetmek için aşağıdaki özniteliklerle birlikte dışa aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: süsün adı.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: diğer süsleme katmanları ile ilgili olarak süsleme sipariş. Sınıf <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> dört varsayılan katman tanımlar: Seçim, Anahat Oluşturma, Caret ve Metin.

  Aşağıdaki örnek, bir süsleme katmanı tanımında dışa aktarma özniteliklerini gösterir.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Süslemeyi <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> anında gerçekleştirerek <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> etkinliğini uygulayan ve işleyen ikinci bir sınıf oluşturmanız gerekir. Bu sınıfı aşağıdaki özniteliklerle birlikte dışa aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: süsleyici içeriğin geçerli olduğu içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: bu süslemenin geçerli olduğu metin görünümü türüdür. Sınıfın <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> önceden tanımlanmış metin görünümü rolleri kümesi vardır. Örneğin, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> öncelikle dosyaların metin görünümleri için kullanılır. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>bir kullanıcının fare ve klavye kullanarak edinebileceği veya gezinebileceği metin görünümleri için kullanılır. Görünümörnekleri <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> düzenleyici metin görünümü ve **Çıktı** penceresidir.

  Aşağıdaki örnek, süs sağlayıcısındaki dışa aktarma özniteliklerini gösterir.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Bir boşluk müzakere süsleme metin ile aynı düzeyde yer kaplar biridir. Bu tür bir süsleme oluşturmak için, adornment'in <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>kapladığı alan miktarını tanımlayan bir etiket sınıfı tanımlamanız gerekir.

 Tüm süslemelerde olduğu gibi, süs katmanı tanımını dışa aktarmanız gerekir.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Alan pazarlığı süsleyicisini anında oluşturmak için, uygulayan sınıfa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ek olarak <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (diğer süsleme türlerinde olduğu gibi) uygulayan bir sınıf oluşturmanız gerekir.

 Tagger sağlayıcısını kaydetmek için, aşağıdaki özniteliklerle birlikte dışa aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: süsünüzün geçerli olduğu içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: bu etiketin veya süslemenin geçerli olduğu metin görünümü türüdür. Sınıfın <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> önceden tanımlanmış metin görünümü rolleri kümesi vardır. Örneğin, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> öncelikle dosyaların metin görünümleri için kullanılır. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>bir kullanıcının fare ve klavye kullanarak edinebileceği veya gezinebileceği metin görünümleri için kullanılır. Görünümörnekleri <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> düzenleyici metin görünümü ve **Çıktı** penceresidir.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: tanımladığınız etiket veya süs türü. <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>Bir saniye <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> eklemeniz gerekir.

  Aşağıdaki örnek, bir alan pazarlığı süsleme etiketi için etiket sağlayıcısında dışa aktarma özniteliklerini gösterir.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Fare İşlemcilerini Genişletme
 Fare girişi için özel yol tutuşu ekleyebilirsiniz. Işlemek istediğiniz giriş için <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> fare olaylarını devralan ve geçersiz kılınan bir sınıf oluşturun. Ayrıca ikinci <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> bir sınıfta uygulamanız ve fare <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> işleyicinizin geçerli olduğu içeriğin türünü (örneğin" "metin" veya "kod") belirten içerikle birlikte dışa aktarmanız gerekir.

 Aşağıdaki örnekte, fare işlemci sağlayıcısında dışa aktarma öznitelikleri gösterilmektedir.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Damla işleyicilerini uzat
 Bırak işleyicilerinin davranışını, uygulayan bir sınıf <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> ve damla işleyicisini oluşturmak <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> için uygulayan ikinci bir sınıf oluşturarak belirli metin türleri için özelleştirebilirsiniz. Damla işleyicisini aşağıdaki özniteliklerle birlikte dışa aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: bu bırakma işleyicisinin geçerli olduğu metin biçimi. Aşağıdaki biçimler en yüksekten en alta doğru öncelik sırasına göre işlenir:

  1. Herhangi bir özel biçim

  2. Filedrop

  3. GeliştirilmişMetafile

  4. Waveaudio

  5. Rıff

  6. Dıf

  7. Yerel Ayar

  8. Palet

  9. Kalem Verileri

  10. Serileştirilebilir

  11. Sembolik Bağlantı

  12. Xaml

  13. XamlPaketi

  14. Tıff

  15. Bitmap

  16. Dıb

  17. MetafileResim

  18. CSV

  19. System

  20. HTML Biçimi

  21. Unicodetext

  22. OEMText

  23. Metin

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: damla işleyicisinin adı.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: varsayılan damla işleyicisinden önce veya sonra damla işleyicisinin sıralanması. Visual Studio için varsayılan damla işleyicisi "DefaultFileDropHandler" olarak adlandırılır.

  Aşağıdaki örnek, bir damla işleyici sağlayıcısında dışa aktarma özniteliklerini gösterir.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Düzenleyici Seçeneklerini Genişletme
 Seçenekleri yalnızca belirli bir kapsamda ( örneğin, metin görünümünde) geçerli olacak şekilde tanımlayabilirsiniz. Düzenleyici bu önceden tanımlanmış seçenek kümesini sağlar: düzenleyici seçenekleri, görünüm seçenekleri ve Windows Sunu Temeli (WPF) görünüm seçenekleri. Bu seçenekler <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, , <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>ve <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.

 Yeni bir seçenek eklemek için, aşağıdaki seçenek tanımı sınıflarından birinden bir sınıf türetin:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Aşağıdaki örnek, Boolean değeri olan bir seçenek tanımının nasıl dışa aktarılabildiğini gösterir.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>IntelliSense'i Genişlet
 IntelliSense, yapılandırılmış metin hakkında bilgi sağlayan bir dizi özellik ve bunun için deyim tamamlama için genel bir terimdir. Bu özellikler ifade tamamlama, imza yardımı, Hızlı Bilgi ve ampulleri içerir. Ekstre tamamlama, kullanıcıların bir dil anahtar sözcüğüveya üye adını doğru yazmanıza yardımcı olur. İmza yardımı, kullanıcının yazdığı yöntemiçin imzayı veya imzaları görüntüler. Hızlı Bilgi, fare üzerinde yken bir tür veya üye adı için tam bir imza görüntüler. Ampul, belirli bağlamlarda belirli tanımlayıcılar için ek eylemler sağlar, örneğin, bir olay yeniden adlandırıldıktan sonra bir değişkenin tüm oluşumlarını yeniden adlandırma.

 Bir IntelliSense özelliğinin tasarımı her durumda aynıdır:

- Bir IntelliSense *broker* genel işlem sorumludur.

- IntelliSense *oturumu,* sunucunun tetikleme setetikle seçimin committal veya iptali arasındaki olayların sırasını temsil eder. Oturum genellikle bazı kullanıcı hareketi tarafından tetiklenir.

- Bir IntelliSense *denetleyicisi,* oturumun ne zaman başlayıp ne zaman biteceğini belirlemekten sorumludur. Ayrıca, bilgilerin ne zaman işitilmesi ve oturumun ne zaman iptal edilmesi gerektiğine de karar verir.

- Bir IntelliSense *kaynağı* içeriği sağlar ve en iyi eşleşmeye karar verir.

- İçeriği görüntülemekten bir IntelliSense *sunucusu* sorumludur.

  Çoğu durumda, en az bir kaynak ve denetleyici sağlamanızı öneririz. Ekranı özelleştirmek istiyorsanız bir sunucu da sağlayabilirsiniz.

### <a name="implement-an-intellisense-source"></a>IntelliSense Kaynağı Uygulayın
 Bir kaynağı özelleştirmek için aşağıdaki kaynak arabirimlerinden birini (veya daha fazlasını) uygulamanız gerekir:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>lehine amortismana <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>uymuştur.

 Ayrıca, aynı türde bir sağlayıcı uygulamanız gerekir:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>lehine amortismana <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>uymuştur.

 Sağlayıcıyı aşağıdaki özniteliklerle birlikte dışa aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kaynağın adı.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: kaynağın geçerli olduğu içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kaynağın (diğer kaynaklara göre) görünmesi gereken sıra.

- Aşağıdaki örnek, bir tamamlama kaynak sağlayıcısında dışa aktarma özniteliklerini gösterir.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 IntelliSense kaynaklarının uygulanması hakkında daha fazla bilgi için aşağıdaki gözden geçirme lere bakın:

- [Walkthrough: QuickInfo araç ipuçlarını görüntüleyin](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Walkthrough: İmza Yardım Görüntüle](../extensibility/walkthrough-displaying-signature-help.md)

- [Walkthrough: Görüntü deyimi tamamlama](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>IntelliSense denetleyicisi uygulayın
 Denetleyiciyi özelleştirmek için <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> arabirimi uygulamanız gerekir. Buna ek olarak, aşağıdaki özniteliklerle birlikte bir denetleyici sağlayıcı uygulamanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: denetleyicinin adı.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: denetleyicinin geçerli olduğu içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: denetleyicinin görünmesi gereken sıra (diğer denetleyicilere göre).

  Aşağıdaki örnek, bir tamamlama denetleyici sağlayıcısında dışa aktarma özniteliklerini gösterir.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 IntelliSense denetleyicilerini kullanma hakkında daha fazla bilgi için aşağıdaki izçıkışlara bakın:

- [Walkthrough: QuickInfo araç ipuçlarını görüntüleyin](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
