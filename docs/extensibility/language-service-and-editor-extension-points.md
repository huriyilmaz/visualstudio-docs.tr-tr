---
title: Dil hizmeti ve Düzenleyici uzantı noktaları | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703053"
---
# <a name="language-service-and-editor-extension-points"></a>Dil hizmeti ve Düzenleyici uzantı noktaları
Düzenleyici, çoğu dil hizmeti özelliği de dahil olmak üzere Managed Extensibility Framework (MEF) bileşen parçaları olarak genişletebileceğinizi uzantı noktaları sağlar. Bunlar ana uzantı noktası kategorileridir:

- İçerik türleri

- Sınıflandırma türleri ve sınıflandırma biçimleri

- Kenar boşlukları ve kaydırma çubukları

- Etiketler

- Satırdaki kenarlıkları

- Fare işlemcileri

- İşleyicileri bırak

- Seçenekler

- IntelliSense

## <a name="extend-content-types"></a>İçerik türlerini Genişlet
 İçerik türleri, düzenleyici tarafından işlenen metin türlerinin tanımlardır, örneğin, "metin", "kod" veya "CSharp". Türünde bir değişken bildirerek <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> ve yeni içerik türüne benzersiz bir ad vererek yeni bir içerik türü tanımlarsınız. İçerik türünü düzenleyiciye kaydetmek için aşağıdaki özniteliklerle birlikte dışarı aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , içerik türünün adıdır.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> Bu içerik türünün türetildiği içerik türünün adıdır. İçerik türü, birden fazla diğer içerik türünden devralınabilir.

  <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>Sınıfı mühürlenmiş olduğundan, türü parametre olmadan dışarı aktarabilirsiniz.

  Aşağıdaki örnek, içerik türü tanımında dışarı aktarma özniteliklerini gösterir.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 İçerik türleri sıfır veya daha önceden var olan içerik türlerini temel alabilir. Bunlar yerleşik türlerdir:

- Any: temel içerik türü. Diğer tüm içerik türlerinin üst öğesi.

- Metin: projeksiyon olmayan içerik için temel tür. "Any" öğesinden devralır.

- Düz metin: kod olmayan metin için. "Metin" öğesinden devralır.

- Kod: tüm türlerdeki kodlar için. "Metin" öğesinden devralır.

- Inert: metni herhangi bir işleme türüyle dışlar. Bu içerik türünün metninde hiçbir uzantı uygulanmadı.

- Projeksiyon: projeksiyon arabelleklerinin içeriği için. "Any" öğesinden devralır.

- IntelliSense: IntelliSense içeriği için. "Metin" öğesinden devralır.

- Sıghelp: imza yardımı. "IntelliSense" öğesinden devralır.

- Sıghelp-doc: imza yardım belgeleri. "IntelliSense" öğesinden devralır.

  Visual Studio tarafından tanımlanan bazı içerik türleri ve Visual Studio 'da barındırılan bazı diller şunlardır:

- Temel

- C/C++

- ConsoleOutput

- Step\chapter

- CSS

- ENC

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  Kullanılabilir içerik türleri listesini saptamak için, <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> Düzenleyici için içerik türleri koleksiyonunu tutan öğesini içeri aktarın. Aşağıdaki kod bu hizmeti bir özellik olarak içeri aktarır.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Bir içerik türünü bir dosya adı uzantısıyla ilişkilendirmek için kullanın <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> .

> [!NOTE]
> Visual Studio 'da, dosya adı uzantıları <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> bir dil hizmeti paketi kullanılarak kaydedilir. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>BIR MEF içerik türünü, bu şekilde kaydedilmiş bir dosya adı uzantısıyla ilişkilendirir.

 Dosya adı uzantısını içerik türü tanımına dışarı aktarmak için aşağıdaki öznitelikleri eklemeniz gerekir:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: dosya adı uzantısını belirtir.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: içerik türünü belirtir.

  <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>Sınıfı mühürlenmiş olduğundan, türü parametre olmadan dışarı aktarabilirsiniz.

  Aşağıdaki örnek, bir dosya adı uzantısında içerik türü tanımına dışarı aktarma özniteliklerini gösterir.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 , <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> Dosya adı uzantıları ve içerik türleri arasındaki ilişkilendirmeleri yönetir.

## <a name="extend-classification-types-and-classification-formats"></a>Sınıflandırma türlerini ve sınıflandırma biçimlerini genişletme
 Farklı işleme sağlamak istediğiniz metin türlerini tanımlamak için sınıflandırma türlerini kullanabilirsiniz (örneğin, "anahtar sözcüğü" metni maviyi ve "Açıklama" metnini yeşil şekilde renklendirme). Türünde bir değişken bildirerek <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> ve benzersiz bir ad vererek yeni bir sınıflandırma türü tanımlayın.

 Sınıflandırma türünü düzenleyiciye kaydetmek için aşağıdaki özniteliklerle birlikte dışarı aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Sınıflandırma türünün adı.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: Bu sınıflandırma türünün devraldığı Sınıflandırma türünün adı. Tüm sınıflandırma türleri "metin" öğesinden devralınır ve bir sınıflandırma türü birden fazla diğer sınıflandırma türünden devralınabilir.

  <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>Sınıfı mühürlenmiş olduğundan, türü parametre olmadan dışarı aktarabilirsiniz.

  Aşağıdaki örnek, bir sınıflandırma türü tanımında dışarı aktarma özniteliklerini gösterir.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 , <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> Standart sınıflandırmalara erişim sağlar. Yerleşik sınıflandırma türleri şunları içerir:

- metinleri

- "doğal dil" ("metin" öğesinden türetilir)

- "biçimsel dil" ("metin" öğesinden türetilir)

- "String" ("literal" sınıfından türetilir)

- "karakter" ("literal" öğesinden türetilir)

- "sayısal" ("değişmez değer" öğesinden türetilir)

  Öğesinden kalıtımla alınan farklı hata türleri kümesi <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Bunlar aşağıdaki hata türlerini içerir:

- "sözdizimi hatası"

- "derleyici hatası"

- "diğer hata"

- Warning

  Kullanılabilir sınıflandırma türlerinin listesini saptamak için, <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> Düzenleyici için sınıflandırma türleri koleksiyonunu tutan öğesini içeri aktarın. Aşağıdaki kod bu hizmeti bir özellik olarak içeri aktarır.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Yeni sınıflandırma türü için bir sınıflandırma biçim tanımı tanımlayabilirsiniz. ' Dan bir sınıf türet <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> ve <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> aşağıdaki özniteliklerle birlikte türü ile dışarı aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: biçimin adı.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: biçimin görünen adı.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: biçimin **Seçenekler** Iletişim kutusunun **yazı tipleri ve renkler** sayfasında görüntülenip görüntülenmeyeceğini belirtir.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: biçimin önceliği. Geçerli değerler şunlardır <xref:Microsoft.VisualStudio.Text.Classification.Priority> .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: bu biçimin eşlendiği Sınıflandırma türünün adı.

  Aşağıdaki örnek, bir sınıflandırma biçim tanımında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Kullanılabilir biçimlerin listesini öğrenmek için, <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> Düzenleyici için biçim koleksiyonunu tutan öğesini içe aktarın. Aşağıdaki kod bu hizmeti bir özellik olarak içeri aktarır.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Kenar boşluklarını ve kaydırma çubuklarını genişletme
 Kenar boşlukları ve kaydırma çubukları, metin görünümüne ek olarak düzenleyicinin ana görünüm öğeleridir. Metin görünümü etrafında görüntülenen standart kenar boşluklarına ek olarak istediğiniz sayıda kenar boşluğu sağlayabilirsiniz.

 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin>Bir kenar boşluğu tanımlamak için bir arabirim uygulayın. Ayrıca, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> kenar boşluğunu oluşturmak için arabirimini de uygulamalısınız.

 Kenar boşluğu sağlayıcısını düzenleyici ile kaydetmek için, sağlayıcıyı aşağıdaki özniteliklerle birlikte dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kenar boşluğunun adı.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kenar boşluğunun diğer kenar boşluklarına göre göründüğü sıra.

   Bunlar yerleşik kenar boşluklardır:

  - "WPF yatay kaydırma çubuğu"

  - "WPF dikey kaydırma çubuğu"

  - "WPF satır numarası kenar boşluğu"

    Order özniteliği olan yatay kenar boşlukları `After="Wpf Horizontal Scrollbar"` yerleşik kenar boşluğunun altında görüntülenir ve Order özniteliği olan yatay kenar boşlukları `Before ="Wpf Horizontal Scrollbar"` yerleşik kenar boşluğunun üzerinde görüntülenir. Order özniteliği olan sağ dikey kenar boşlukları `After="Wpf Vertical Scrollbar"` , kaydırma çubuğunun sağında görüntülenir. Order özniteliği olan sol dikey kenar boşlukları `After="Wpf Line Number Margin"` satır numarası kenar boşluğunun solunda görünür (görünür durumdaysa).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: kenar boşluğu türü (sol, sağ, üst veya alt).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: kenar boşlukta geçerli olan içerik türü (örneğin, "metin" veya "kod").

  Aşağıdaki örnek, satır numarası kenar boşluğunun sağında görüntülenen bir kenar boşluğu için bir kenar boşluğu sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Etiketleri Genişlet
 Etiketler, verileri farklı metin türleriyle ilişkilendirmenin bir yoludur. Birçok durumda, ilişkili veriler görsel bir efekt olarak görüntülenir, ancak etiketlerin hepsi bir görsel sunuya sahip değildir. Uygulayarak kendi etiket türünü tanımlayabilirsiniz <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Ayrıca <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> , belirli bir metin yayılma kümesi için Etiketler sağlamak üzere öğesini ve <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> Tagger sağlamak için öğesini uygulamalısınız. Tagger sağlayıcısını aşağıdaki özniteliklerle birlikte dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: etiketinizdeki geçerli olduğu içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: etiket türü.

  Aşağıdaki örnek, bir Tagger sağlayıcısında dışarı aktarma özniteliklerini gösterir.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> Aşağıdaki tür Etiketler yerleşik olarak bulunur:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: ile ilişkili <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: hata türleriyle ilişkili.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: bir kenarlığı ile ilişkili.

  > [!NOTE]
  > Bir örneği için <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> bkz. [izlenecek yol: metin vurgulama](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: Ana hat içinde genişletilebilen veya daraltılabilen bölgelerle ilişkili.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: bir kenarlığı 'in bir metin görünümünde kapladığı alanı tanımlar. Yer alan donmanlar hakkında daha fazla bilgi için aşağıdaki bölüme bakın.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: kenarlığı için otomatik aralama ve boyutlandırma sağlar.

  Arabellekler ve görünümler için etiketleri bulmak ve kullanmak üzere, <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> size istenen türden bir veren olan veya öğesini içeri aktarın <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> . Aşağıdaki kod bu hizmeti bir özellik olarak içeri aktarır.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Etiketler ve MarkerFormatDefinitions
 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>Bir etiketin görünümünü tanımlamak için sınıfını genişletebilirsiniz. Sınıfınızı (olarak <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> ) aşağıdaki özniteliklerle dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: bu biçime başvurmak için kullanılan ad

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Bu, biçimin kullanıcı arabiriminde görünmesine neden olur

  Oluşturucuda, etiketin görünen adını ve görünümünü tanımlarsınız. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> , Fill rengini tanımlar ve <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> kenarlık rengini tanımlar. , <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> Biçim tanımının yerelleştirilebilir adıdır.

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

 Bu biçim tanımını bir etikete uygulamak için, sınıfının name özniteliğinde ayarladığınız ada (görünen ad değil) başvurun.

> [!NOTE]
> Bir örneği için <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> bkz. [izlenecek yol: metin vurgulama](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Donmanları Genişlet
 Donnments, metin görünümünde veya metin görünümünde görüntülenen metne eklenebilen görsel etkiler tanımlar. Kendi kenarlığı herhangi bir tür olarak tanımlayabilirsiniz <xref:System.Windows.UIElement> .

 Kenarlığı sınıfınıza bir belirtmeniz gerekir <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> . Kenarlığı katmanını kaydetmek için aşağıdaki özniteliklerle birlikte dışarı aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kenarlığı adı.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: diğer kenarlığı katmanlarına göre kenarlığı sıralaması. Sınıf <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> dört varsayılan katmanı tanımlar: seçim, anahat oluşturma, giriş işareti ve metin.

  Aşağıdaki örnek, kenarlığı katman tanımında dışarı aktarma özniteliklerini gösterir.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>Kenarlığı örneğini oluşturarak olayını uygulayan ve işleyen ikinci bir sınıf oluşturmanız gerekir <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> . Bu sınıfı aşağıdaki özniteliklerle birlikte dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: kenarlığı geçerli olduğu içerik türü (örneğin, "Text" veya "Code").

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: Bu kenarlığı geçerli olduğu metin görünümü türü. Sınıfında <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> önceden tanımlanmış metin görünümü rolleri kümesi vardır. Örneğin, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> öncelikle dosyaların metin görünümlerinde kullanılır. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> bir kullanıcının fare ve klavye kullanarak düzenleyebileceği veya gezinebilecekleri metin görünümleri için kullanılır. Görünüm örnekleri <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> , düzenleyici metin görünümü ve **Çıkış** penceresidir.

  Aşağıdaki örnek, kenarlığı sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Alan üzerinde anlaşmaya varan kenarlığı, metinle aynı düzeyde yer kaplayan bir alandır. Bu tür bir kenarlığı oluşturmak için, <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> kenarlığı 'in kapladığı alan miktarını tanımlayan öğesinden devralan bir etiket sınıfı tanımlamanız gerekir.

 Tüm donatılarda olduğu gibi, kenarlığı katman tanımını dışarı aktarmanız gerekir.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Alan üzerinde anlaşmaya varkenarlığı sağlamak için, <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> uygulayan sınıfa ek olarak <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (diğer donatıl türlerinde olduğu gibi) öğesini uygulayan bir sınıf oluşturmanız gerekir.

 Tagger sağlayıcısını kaydetmek için aşağıdaki özniteliklerle birlikte dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: kenarlığı için geçerli olan içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: Bu etiketin veya kenarlığı geçerli olduğu metin görünümü türü. Sınıfında <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> önceden tanımlanmış metin görünümü rolleri kümesi vardır. Örneğin, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> öncelikle dosyaların metin görünümlerinde kullanılır. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> bir kullanıcının fare ve klavye kullanarak düzenleyebileceği veya gezinebilecekleri metin görünümleri için kullanılır. Görünüm örnekleri <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> , düzenleyici metin görünümü ve **Çıkış** penceresidir.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: tanımladığınız etiket veya kenarlığı türü. İçin bir saniye eklemeniz gerekir <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  Aşağıdaki örnek, bir boşluk anlaşması kenarlığı etiketi için Tagger sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Fare Işlemcilerini genişletme
 Fare girişi için özel işleme ekleyebilirsiniz. <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>İşlemek istediğiniz giriş için fare olaylarını devralan ve geçersiz kılacak bir sınıf oluşturun. Ayrıca <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> , ikinci bir sınıfta uygulamanız gerekir ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> fare işleyicinizin geçerli olduğu içerik türünü (örneğin, "metin" veya "kod") belirten ile birlikte dışarı aktarmanız gerekir.

 Aşağıdaki örnek, bir fare işlemcisi sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Bırakma işleyicilerini Genişlet
 Öğesini uygulayan bir sınıf <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> ve <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> bırakma işleyicisini oluşturmak için uygulayan ikinci bir sınıf oluşturarak, belirli metin türleri için bırakma işleyicilerinin davranışını özelleştirebilirsiniz. Bırakma işleyicisini aşağıdaki özniteliklerle birlikte dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: Bu bırakma işleyicisinin geçerli olduğu metin biçimi. Aşağıdaki biçimler, en yüksekten en düşüğe öncelik sırasına göre işlenir:

  1. Herhangi bir özel biçim

  2. FileDrop

  3. EnhancedMetafile

  4. Dalga sesi

  5. Riff

  6. Dif

  7. Yerel Ayar

  8. İnizdeki

  9. PenData

  10. Seri hale getirilebilir

  11. Semboliclınk

  12. Xaml

  13. XamlPackage

  14. Dosyalarında

  15. Biteş

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System. String

  20. HTML biçimi

  21. UnicodeText

  22. OEMText

  23. Metin

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: bırakma işleyicisinin adı.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: varsayılan bırakma işleyicisinden önce veya sonra bırakma işleyicisinin sıralaması. Visual Studio için varsayılan bırakma işleyicisi "DefaultFileDropHandler" olarak adlandırılmıştır.

  Aşağıdaki örnek, bir bırakma işleyici sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Düzenleyici seçeneklerini genişletme
 Seçenekleri yalnızca belirli bir kapsamda (örneğin, bir metin görünümünde) geçerli olacak şekilde tanımlayabilirsiniz. Düzenleyici, bu öntanımlı seçenekler kümesini sağlar: düzenleyici seçenekleri, görüntüleme seçenekleri ve Windows Presentation Foundation (WPF) görünüm seçenekleri. Bu seçenekler <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> ,, ve içinde bulunabilir <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Yeni bir seçenek eklemek için, bu seçenek tanım sınıflarından birini bir sınıf türetirsiniz:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Aşağıdaki örnek, Boole değeri olan bir seçenek tanımının nasıl dışarı aktarılacağını gösterir.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>IntelliSense 'i genişletme
 IntelliSense, yapılandırılmış metin ve bunun için deyimi tamamlama hakkında bilgi sağlayan bir dizi özellik için genel bir terimdir. Bu özellikler; deyimin tamamlanmasını, imza yardımını, hızlı bilgileri ve hafif bulbs 'leri içerir. Deyimin tamamlanması, kullanıcıların bir dil anahtar sözcüğünü veya üye adını doğru şekilde yazmasının sağlar. İmza yardımı, kullanıcının yeni girdiği yönteme ait imza veya imzaları görüntüler. Hızlı bilgi, fare üzerine getirildiğinde bir tür veya üye adı için tamamen imza görüntüler. Ampul, belirli bağlamlardaki belirli tanımlayıcılar için ek eylemler sağlar, örneğin, bir oluşum yeniden adlandırıldıktan sonra bir değişkenin tüm tekrarlamalarını yeniden adlandırma.

 IntelliSense özelliğinin tasarımı her durumda çok aynıdır:

- Bir IntelliSense *Aracısı* , genel işlemden sorumludur.

- Bir IntelliSense *oturumu* , sunucunun tetiklenmesi ile seçimin komite veya iptalinin arasındaki olayların sırasını temsil eder. Oturum genellikle bazı Kullanıcı hareketi tarafından tetiklenir.

- Bir IntelliSense *denetleyicisi* , oturumun ne zaman başlayıp bitmeyeceğine karar vermekten sorumludur. Ayrıca, bilgilerin ne zaman yürütülmesi gerektiğini ve oturumun ne zaman iptal edilip edilmeyeceğine de karar verir.

- IntelliSense *kaynağı* içeriği sağlar ve en iyi eşleşmeyi belirler.

- Bir IntelliSense *sunucu* , içeriğin görüntülenmesini sağlamaktan sorumludur.

  Çoğu durumda, en az bir kaynak ve denetleyici sağlamanızı öneririz. Ayrıca, görüntülemeyi özelleştirmek istiyorsanız bir sunucu da sağlayabilirsiniz.

### <a name="implement-an-intellisense-source"></a>Bir IntelliSense kaynağı uygulama
 Bir kaynağı özelleştirmek için aşağıdaki kaynak arabirimlerinden bir (veya daha fazla) uygulamanız gerekir:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> kullanım dışı bırakılmıştır <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 Ayrıca, aynı türde bir sağlayıcı uygulamanız gerekir:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> kullanım dışı bırakılmıştır <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 Sağlayıcıyı aşağıdaki özniteliklerle birlikte dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kaynağın adı.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: kaynağın uygulandığı içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kaynağın görünmesi gereken sıra (diğer kaynaklara göre).

- Aşağıdaki örnek, bir tamamlama kaynak sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 IntelliSense kaynaklarını uygulama hakkında daha fazla bilgi için aşağıdaki izlenecek yollara bakın:

- [İzlenecek yol: hızlı bilgi araç ipuçlarını görüntüle](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [İzlenecek yol: Imza yardımını görüntüle](../extensibility/walkthrough-displaying-signature-help.md)

- [İzlenecek yol: görüntüleme ifadesinin tamamlanması](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>IntelliSense denetleyicisi uygulama
 Bir denetleyiciyi özelleştirmek için arabirimini uygulamanız gerekir <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> . Ayrıca, aşağıdaki özniteliklerle bir denetleyici sağlayıcısı uygulamanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: denetleyicinin adı.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: denetleyicinin uygulandığı içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: denetleyicinin görüntüleneceği sıra (diğer denetleyicilere göre).

  Aşağıdaki örnek, bir tamamlama denetleyicisi sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 IntelliSense denetleyicilerini kullanma hakkında daha fazla bilgi için aşağıdaki izlenecek yollara bakın:

- [İzlenecek yol: hızlı bilgi araç ipuçlarını görüntüle](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
