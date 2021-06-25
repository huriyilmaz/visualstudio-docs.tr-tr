---
title: Dil Hizmeti ve Düzenleyici Uzantı Noktaları | Microsoft Docs
description: Çoğu dil hizmeti özelliği de dahil olmak Visual Studio kod düzenleyicisinde uzantı noktaları hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 293851f1f3e72508a9bc119fb7551b0118ab2a9b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903153"
---
# <a name="language-service-and-editor-extension-points"></a>Dil hizmeti ve düzenleyici uzantısı noktaları
Düzenleyici, çoğu dil hizmeti özelliği dahil olmak üzere Managed Extensibility Framework (MEF) bileşen parçaları olarak genişletebilirsiniz uzantı noktaları sağlar. Bunlar ana uzantı noktası kategorileridir:

- İçerik türleri

- Sınıflandırma türleri ve sınıflandırma biçimleri

- Kenar boşlukları ve kaydırma çubuğu

- Etiketler

- Süsleme -leri

- Fare işlemcileri

- İşleyicileri bırakma

- Seçenekler

- IntelliSense

## <a name="extend-content-types"></a>İçerik türlerini genişletme
 İçerik türleri, düzenleyici tarafından iş yapılan metin türlerinin tanımlarıdır; örneğin, "text", "code" veya "CSharp". Türünde bir değişken bildirerek ve yeni içerik türüne benzersiz bir ad vererek <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> yeni bir içerik türü tanımlarsiniz. İçerik türünü düzenleyiciye kaydetmek için aşağıdaki özniteliklerle birlikte dışarı aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , içerik türünün adıdır.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> , bu içerik türünün türetilen içerik türünün adıdır. İçerik türü, diğer birden çok içerik türünden devralabilir.

  Sınıfı <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> korumalı olduğundan, tür parametresi ile dışarı aktarın.

  Aşağıdaki örnek, bir içerik türü tanımında dışarı aktarma özniteliklerini gösterir.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 İçerik türleri sıfır veya daha fazla önceden var olan içerik türlerini temel alarak olabilir. Bunlar yerleşik türlerdir:

- Herhangi bir: temel içerik türü. Diğer tüm içerik türlerinin üst öğesi.

- Metin: Projeksiyon olmayan içerik için temel tür. "Any" tarafından devralınıyor.

- Düz metin: Kod olmayan metinler için. "Text" (metinden) devralıyor.

- Kod: Her türlü kod için. "Text" (metinden) devralıyor.

- Inert: Metni herhangi bir işlemenin dışında sunar. Bu içerik türünün metnine hiçbir zaman uzantı uygulanmaz.

- Projeksiyon: Projeksiyon arabelleklerinin içeriği için. "Any" tarafından devralınıyor.

- IntelliSense: IntelliSense'in içeriği için. "Text" (metinden) devralıyor.

- Sighelp: imza yardımı. "Intellisense" tarafından devralınıyor.

- Sighelp-doc: imza yardım belgeleri. "Intellisense" tarafından devralınıyor.

  Bunlar, Visual Studio tarafından tanımlanan içerik türlerinden bazıları ve Visual Studio:

- Temel

- C/C++

- ConsoleOutput

- Csharp

- CSS

- Enc

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  Kullanılabilir içerik türlerinin listesini bulmak için, düzenleyici için <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> içerik türlerinin koleksiyonunu bulunduran 'i içeri aktarın. Aşağıdaki kod, bu hizmeti bir özellik olarak içeri aktarmaktadır.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 İçerik türünü bir dosya adı uzantısıyla ilişkilendirmek için <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> kullanın.

> [!NOTE]
> Bu Visual Studio, dosya adı uzantıları bir dil hizmet <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> paketinde kullanılarak kaydedilir. , <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> bir MEF içerik türünü bu şekilde kaydedilmiş bir dosya adı uzantısıyla ilişkilendirır.

 Dosya adı uzantısını içerik türü tanımına dışarı aktarmanız için aşağıdaki öznitelikleri dahil etmek gerekir:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: dosya adı uzantısını belirtir.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: İçerik türünü belirtir.

  Sınıfı <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> korumalı olduğundan, tür parametresi ile dışarı aktarın.

  Aşağıdaki örnek, bir dosya adı uzantısında yer alan öznitelikleri bir içerik türü tanımına dışarı aktarmayı gösterir.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>, dosya adı uzantıları ve içerik türleri arasındaki ilişkilendirmeleri yönetir.

## <a name="extend-classification-types-and-classification-formats"></a>Sınıflandırma türlerini ve sınıflandırma biçimlerini genişletme
 Sınıflandırma türlerini, farklı işleme sağlamak istediğiniz metin türlerini tanımlamak için kullanabilirsiniz (örneğin, "anahtar sözcük" metnini mavi ve "açıklama" metnini yeşil renklendirme). Türünde bir değişken bildirerek ve benzersiz bir ad vererek <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> yeni bir sınıflandırma türü tanımlayın.

 Sınıflandırma türünü düzenleyiciye kaydetmek için aşağıdaki özniteliklerle birlikte dışarı aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: sınıflandırma türünün adı.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: Bu sınıflandırma türünün devralınan sınıflandırma türünün adı. Tüm sınıflandırma türleri "metin" türünden devralınabilir ve bir sınıflandırma türü diğer birden çok sınıflandırma türünden devralabilir.

  Sınıfı <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> korumalı olduğundan, tür parametresi ile dışarı aktarın.

  Aşağıdaki örnek, sınıflandırma türü tanımında dışarı aktarma özniteliklerini gösterir.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>, standart sınıflandırmalara erişim sağlar. Yerleşik sınıflandırma türleri şunlardır:

- "text"

- "doğal dil" ("metinden" türetilmektedir)

- "biçimsel dil" ("metin" dilinden türetilmektedir)

- "string" ("değişmez" dizeden türetilmektedir)

- "character" ("değişmez" karakterden türetilmektedir)

- "sayısal" ("değişmez" değerden türetilmektedir)

  Bir dizi farklı hata türü, 'den <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> devralındı. Aşağıdaki hata türlerini içerir:

- "söz dizimi hatası"

- "derleyici hatası"

- "diğer hata"

- "uyarı"

  Kullanılabilir sınıflandırma türlerinin listesini bulmak için, düzenleyici için <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> sınıflandırma türlerinin koleksiyonunu bulunduran 'i içeri aktarın. Aşağıdaki kod, bu hizmeti bir özellik olarak içeri aktarmaktadır.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Yeni sınıflandırma türünüz için bir sınıflandırma biçimi tanımı tanımlayabilirsiniz. sınıfından bir sınıf <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> türetin ve türüyle <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> birlikte aşağıdaki özniteliklerle dışarı aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: biçimin adı.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: biçimin görünen adı.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: biçimin Seçenekler iletişim kutusunun Yazı Tipleri **ve Renkler** sayfasında **görüntülendiğinden** emin olur.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: biçimin önceliği. Geçerli değerler <xref:Microsoft.VisualStudio.Text.Classification.Priority> konumundandır.

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: Bu biçimin eşlenmiş olduğu sınıflandırma türünün adı.

  Aşağıdaki örnek, sınıflandırma biçimi tanımında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Kullanılabilir biçimlerin listesini bulmak için düzenleyicinin <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> biçim koleksiyonunu bulunduran 'i içeri aktarın. Aşağıdaki kod, bu hizmeti bir özellik olarak içeri aktarmaktadır.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Kenar boşluklarını ve kaydırma çubuklarını genişletme
 Kenar boşlukları ve kaydırma çubuğu, metin görünümünün kendisine ek olarak düzenleyicinin ana görünüm öğeleridir. Metin görünümünün etrafında görünen standart kenar boşluklarının yanı sıra istediğiniz sayıda kenar boşluğu sabilirsiniz.

 Dış boşluğu <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> tanımlamak için bir arabirim uygulama. Kenar boşluğu oluşturmak için <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> arabirimini de uygulamalısiniz.

 Dış boşluk sağlayıcısını düzenleyiciye kaydetmek için sağlayıcıyı aşağıdaki özniteliklerle birlikte dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kenar boşluğun adı.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: diğer kenar boşluklarının göreli olarak kenar boşluğunda göründüğü sıra.

   Bunlar yerleşik kenar boşluklarıdır:

  - "Wpf Yatay Kaydırma Çubuğu"

  - "Wpf Dikey Kaydırma Çubuğu"

  - "Wpf Satır Numarası Kenar Boşluğu"

    sıralama özniteliğine sahip yatay kenar boşlukları yerleşik kenar boşluğu altında, sıralama özniteliğine sahip yatay kenar boşlukları ise yerleşik kenar boşluğun `After="Wpf Horizontal Scrollbar"` `Before ="Wpf Horizontal Scrollbar"` üzerinde görüntülenir. sıralama özniteliğine sahip sağ dikey kenar `After="Wpf Vertical Scrollbar"` boşlukları kaydırma çubuğunun sağ tarafından görüntülenir. sipariş özniteliğine sahip sol dikey kenar boşlukları, çizgi sayı kenar boşluğunda `After="Wpf Line Number Margin"` (görünürse) sol tarafta görünür.

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: kenar boşluğu (sol, sağ, üst veya alt) tür.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: kenar boşluğun geçerli olduğu içerik türü ("metin" veya "kod") .

  Aşağıdaki örnek, satır numarası kenar boşluğunda sağda görünen bir kenar boşluğu için dış boşluk sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Etiketleri genişletme
 Etiketler, verileri farklı metin türleriyle bir şekilde irdeler. Çoğu durumda, ilişkili veriler görsel bir etki olarak görüntülenir, ancak tüm etiketlerin görsel sunumu yoktur. uygulayarak kendi etiket türlerinizi <xref:Microsoft.VisualStudio.Text.Tagging.ITag> tanımlayabilirsiniz. Ayrıca, verilen bir metin aralığı kümesi için etiketleri sağlamak için ve etiketger sağlamak için <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> bir de uygulamanız gerekir. Tagger sağlayıcısını aşağıdaki özniteliklerle birlikte dışarı aktarmalısiniz:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: etiketinizin geçerli olduğu içerik türü ("metin" veya "kod") .

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: etiket tün.

  Aşağıdaki örnek, bir etiket sağlayıcısında dışarı aktarma özniteliklerini gösterir.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> Aşağıdaki etiket türleri yerleşiktir:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: bir ile <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> ilişkilendirildi.

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: hata türleriyle ilişkilendirildi.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: bir donatma ile ilişkili.

  > [!NOTE]
  > bir örneği için, <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> [Walkthrough: Highlighting Text](../extensibility/walkthrough-highlighting-text.md)içinde HighlightWordTag tanımına bakın.

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: altı çizili olarak genişletilen veya daraltılmış bölgeler ile ilişkili.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: bir donatıcının metin görünümünde kapladığı alanı tanımlar. Alan anlaşmaları hakkında daha fazla bilgi için aşağıdaki bölüme bakın.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: donatma için otomatik aralık ve boyutlandırma sağlar.

  Arabellekler ve görünümler için etiketleri bulmak ve kullanmak üzere, veya türünü içeri aktarın. Bu, size istenen türde <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> bir veri <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> sağlar. Aşağıdaki kod, bu hizmeti bir özellik olarak içeri aktarmaktadır.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Etiketler ve MarkerFormatDefinitions
 Bir etiketin <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> görünümünü tanımlamak için sınıfını genişletebilirsiniz. Sınıfınızı (olarak) aşağıdaki <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> özniteliklerle dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: bu biçime başvuru yapmak için kullanılan ad

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Bu, biçimin kullanıcı arabiriminde görünmesine neden olur

  Oluşturucuda etiketin görünen adını ve görünümünü tanımlarsiniz. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> dolgu rengini tanımlar ve <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> kenarlık rengini tanımlar. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>, biçim tanımının yerelleştirilebilir adıdır.

  Aşağıda bir biçim tanımı örneği ve ardından ve bir örnek ve ardından ve bir örnek ve bir örnek ve ardından ve bir biçim tanımı ve daha fazla bilgi ve daha fazla bilgi

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

 Bu biçim tanımını bir etikete uygulamak için sınıfın name özniteliğinde ayar istediğiniz ada (görünen ad değil) bakın.

> [!NOTE]
> Bir örneği için, <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> [Walkthrough: Highlighting Text](../extensibility/walkthrough-highlighting-text.md)içinde HighlightWordFormatDefinition sınıfına bakın.

## <a name="extend-adornments"></a>Donatmalarını genişletme
 Donatma, bir metin görünümünde görüntülenen metne veya metin görünümünün kendisine eklenilen görsel etkileri tanımlar. Kendi donatmanızı herhangi bir tür olarak <xref:System.Windows.UIElement> tanımlayabilirsiniz.

 Donatma sınıfınıza bir <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> bildirin. Donatma katmanınızı kaydetmek için aşağıdaki özniteliklerle birlikte dışarı aktarın:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: donatma adı.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: diğer donatma katmanlarına göre donatma sırası. sınıfı dört <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> varsayılan katmanı tanımlar: Seçim, Açıklama, Giriş Ve Metin.

  Aşağıdaki örnek, bir donatma katmanı tanımında dışarı aktarma özniteliklerini gösterir.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Donatma örneğini başlatarak olayı <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> uygulayan ve <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> işleyen ikinci bir sınıf oluşturmanız gerekir. Bu sınıfı aşağıdaki özniteliklerle birlikte dışarı aktarın:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: donatma geçerli olduğu içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: Bu donatma için geçerli olan metin görünümü. sınıfı, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> önceden tanımlanmış metin görünümü rolleri kümesine sahiptir. Örneğin, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> öncelikle dosyaların metin görünümleri için kullanılır. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> , bir kullanıcının fare ve klavye kullanarak düzenleyemez veya gezine metne yönelik görünümler için kullanılır. Görünümlere <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> örnek olarak düzenleyici metin görünümü ve Çıkış **penceresi** gösterilir.

  Aşağıdaki örnek, donatma sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Boşluk anlaşmalı donatma, metinle aynı düzeyde alanı kaplar. Bu tür bir donatma oluşturmak için, donatma kapladığı alan miktarını tanımlayan 'den devralan <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> bir etiket sınıfı tanımlamanız gerekir.

 Tüm donatmalarda olduğu gibi, donatma katmanı tanımını dışarı aktarmalısiniz.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Alan anlaşmalı donatma örneğini oluşturmak için uygulayan sınıfa ek olarak (diğer donatma türleri gibi) uygulayan bir <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> sınıf oluşturmanız gerekir.

 Tagger sağlayıcısını kaydetmek için aşağıdaki özniteliklerle birlikte dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: donatma sürenizin geçerli olduğu içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: Bu etiketin veya donatmanın geçerli olduğu metin görünümü. sınıfı, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> önceden tanımlanmış metin görünümü rolleri kümesine sahiptir. Örneğin, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> öncelikle dosyaların metin görünümleri için kullanılır. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> , bir kullanıcının fare ve klavye kullanarak düzenleyemez veya gezine metne yönelik görünümler için kullanılır. Görünümlere <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> örnek olarak düzenleyici metin görünümü ve Çıkış **penceresi** gösterilir.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: tanımlandığı etiket veya donatma tür. için bir saniye eklemeniz <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> gerekir.

  Aşağıdaki örnek, alan anlaşmalı donatma etiketi için tagger sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Fare İşlemcilerini Genişletme
 Fare girişi için özel işleme ekebilirsiniz. 'den devralan ve işlemek <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> istediğiniz giriş için fare olaylarını geçersiz kilen bir sınıf oluşturun. Ayrıca ikinci bir sınıfta da uygulamalı ve fare işleyicinizin geçerli olduğu içerik <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> (örneğin, "metin" veya "kod") türüyle birlikte dışarı <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> aktarmanız gerekir.

 Aşağıdaki örnek, fare işlemcisi sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Bırakma işleyicilerini genişletme
 Belirli metin türleri için bırakma işleyicilerinin davranışını, uygulayan bir sınıf ve bırakma işleyicisi oluşturmak için uygulayan ikinci bir sınıf oluşturarak <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> özelleştirebilirsiniz. Bırakma işleyicisini aşağıdaki özniteliklerle birlikte dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: bu bırakma işleyicinin geçerli olduğu metin biçimi. Aşağıdaki biçimler öncelik sırasına göre en yüksekten en düşe doğru iş sırasına göre işleme:

  1. Herhangi bir özel biçim

  2. Filedrop

  3. EnhancedMetafile

  4. Waveaudio

  5. Rıff

  6. Dıf

  7. Yerel Ayar

  8. Palet

  9. PenData

  10. Serileştirilebilir

  11. Sembolik Bağlantı

  12. Xaml

  13. XamlPackage

  14. Tıff

  15. Bitmap

  16. Dıb

  17. Meta DosyaPicture

  18. CSV

  19. System

  20. HTML Biçimi

  21. Unicodetext

  22. OEMText

  23. Metin

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: bırakma işleyicisi adı.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: varsayılan bırakma işleyiciden önce veya sonra bırakma işleyicinin sıralaması. Visual Studio için varsayılan bırakma işleyicisi "DefaultFileDropHandler" olarak adlandırılmıştır.

  Aşağıdaki örnek, bırakma işleyicisi sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Düzenleyici Seçeneklerini Genişletme
 Yalnızca belirli bir kapsamda (örneğin, metin görünümünde) geçerli olacak seçenekleri tanımlayabilirsiniz. Düzenleyici şu önceden tanımlanmış seçenekler kümesi sağlar: düzenleyici seçenekleri, görünüm seçenekleri ve Windows Presentation Foundation (WPF) görüntüleme seçenekleri. Bu seçenekler , <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> ve içinde <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> bulunabilir.

 Yeni bir seçenek eklemek için, şu seçenek tanımı sınıflarından bir sınıf türetin:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Aşağıdaki örnekte, Boole değerine sahip bir seçenek tanımının nasıl dışarı aktar olduğu gösterir.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>IntelliSense'i genişletme
 IntelliSense, yapılandırılmış metin ve deyim tamamlama hakkında bilgi sağlayan bir özellik grubu için genel bir terimdir. Bu özellikler deyim tamamlama, imza yardımı, Hızlı Bilgi ve ampulleri içerir. Deyim tamamlama, kullanıcıların dil anahtar sözcüğünü veya üye adını doğru yazmalarını sağlar. İmza yardımı, kullanıcının az önce yazarak yöntemine yönelik imzayı veya imzaları görüntüler. Hızlı Bilgi, fare üzerine geldiğinde bir tür veya üye adı için tam bir imza görüntüler. Ampul belirli bağlamlarda belirli tanımlayıcılar için ek eylemler sağlar; örneğin, bir oluşum yeniden adlandırıldıktan sonra bir değişkenin tüm oluşumlarını yeniden adlandırma.

 IntelliSense özelliğinin tasarımı her durumda çok aynıdır:

- Genel işlemden *intelliSense* aracısı sorumludur.

- IntelliSense *oturumu,* sunucu tetikleme ile işleme veya seçimin iptali arasındaki olay dizisini temsil eder. Oturum genellikle bir kullanıcı hareketiyle tetiklenir.

- IntelliSense *denetleyicisi,* oturumun ne zaman başlayacağına ve bitim tarihine karar vermekle sorumludur. Ayrıca bilgilerin ne zaman işlendiklerine ve ne zaman iptal edileceklerine de karar verir.

- IntelliSense *kaynağı içeriği* sağlar ve en iyi eşleşmeye karar verir.

- İçeriğin görüntülenmesi *intelliSense* sunucusu tarafından sorumludur.

  Çoğu durumda, en az bir kaynak ve denetleyici sağlamanız önerilir. Ayrıca, ekranı özelleştirmek için bir sunucu da sebilirsiniz.

### <a name="implement-an-intellisense-source"></a>IntelliSense Kaynağı Uygulama
 Bir kaynağı özelleştirmek için aşağıdaki kaynak arabirimlerden birini (veya daha fazlasını) uygulamanız gerekir:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> , için kullanım <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> dışıdır.

 Ayrıca, aynı tür bir sağlayıcıyı da uygulamalısiniz:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> , için kullanım <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> dışıdır.

 Sağlayıcıyı aşağıdaki özniteliklerle birlikte dışarı aktarmalısiniz:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kaynağın adı.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: kaynağın uygulandığı içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kaynağın görünme sırası (diğer kaynaklara göre).

- Aşağıdaki örnek, tamamlama kaynak sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 IntelliSense kaynaklarını uygulama hakkında daha fazla bilgi için aşağıdaki kılavuzlara bakın:

- [Adım adım kılavuz: QuickInfo araç ipucu görüntüleme](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [adım adım kılavuz: İmza Yardımı Görüntüleme](../extensibility/walkthrough-displaying-signature-help.md)

- [Adım adım kılavuz: Deyim tamamlamayı görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>IntelliSense denetleyicisi uygulama
 Bir denetleyiciyi özelleştirmek için arabirimini uygulamanız <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> gerekir. Ayrıca, aşağıdaki özniteliklerle birlikte bir denetleyici sağlayıcısı da uygulamanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: denetleyicinin adı.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: denetleyicinin uygulandığı içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: denetleyicinin görünme sırası (diğer denetleyicilere göre).

  Aşağıdaki örnek, bir tamamlama denetleyicisi sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 IntelliSense denetleyicilerini kullanma hakkında daha fazla bilgi için aşağıdaki kılavuzlara bakın:

- [Adım adım kılavuz: QuickInfo araç ipucu görüntüleme](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
