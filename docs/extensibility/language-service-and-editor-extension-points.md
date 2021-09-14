---
title: Dil hizmeti ve Düzenleyici uzantı noktaları | Microsoft Docs
description: çoğu dil hizmeti özelliği de dahil olmak üzere Visual Studio kod düzenleyicisinde genişletebileceğinizi uzantı noktaları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c3a97b75f1df66d8353c06acf74f8d69b26a6e8c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628904"
---
# <a name="language-service-and-editor-extension-points"></a>Dil hizmeti ve Düzenleyici uzantı noktaları
düzenleyici, çoğu dil hizmeti özelliği de dahil olmak üzere Managed Extensibility Framework (MEF) bileşen parçaları olarak genişletebileceğinizi uzantı noktaları sağlar. Bunlar ana uzantı noktası kategorileridir:

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

  bunlar, Visual Studio tarafından tanımlanan bazı içerik türlerinden ve Visual Studio barındırılan bazı dillerden bazılarıdır:

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
> Visual Studio, dosya adı uzantıları <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> bir dil hizmeti paketi kullanılarak kaydedilir. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>BIR MEF içerik türünü, bu şekilde kaydedilmiş bir dosya adı uzantısıyla ilişkilendirir.

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

 Kullanılabilir biçimlerin listesini bulmak için düzenleyicinin <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> biçim koleksiyonunu bulunduran 'i içeri aktarın. Aşağıdaki kod bu hizmeti bir özellik olarak içeri aktarmaktadır.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Kenar boşluklarını ve kaydırma çubuklarını genişletme
 Kenar boşlukları ve kaydırma çubuğu, metin görünümünün kendisine ek olarak düzenleyicinin ana görünüm öğeleridir. Metin görünümünün etrafında görünen standart kenar boşluklarının yanı sıra istediğiniz sayıda kenar boşluğu sabilirsiniz.

 Dış boşluğu <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> tanımlamak için bir arabirim uygulama. Kenar boşluğu oluşturmak için <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> arabirimini de uygulamalısiniz.

 Dış boşluk sağlayıcısını düzenleyiciye kaydetmek için sağlayıcıyı aşağıdaki özniteliklerle birlikte dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kenar boşluğu adı.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: diğer kenar boşluklarının göreli olarak kenar boşluğunda göründüğü sıra.

   Bunlar yerleşik kenar boşluklarıdır:

  - "Wpf Yatay Kaydırma Çubuğu"

  - "Wpf Dikey Kaydırma Çubuğu"

  - "Wpf Satır Numarası Kenar Boşluğu"

    sıralama özniteliğine sahip yatay kenar boşlukları yerleşik kenar boşluğu altında, sıralama özniteliğine sahip yatay kenar boşlukları ise yerleşik kenar `After="Wpf Horizontal Scrollbar"` `Before ="Wpf Horizontal Scrollbar"` boşluğun üzerinde görüntülenir. sıralama özniteliğine sahip sağ dikey kenar `After="Wpf Vertical Scrollbar"` boşlukları kaydırma çubuğunun sağ tarafından görüntülenir. sipariş özniteliğine sahip sol dikey kenar boşlukları, çizgi sayı kenar boşluğunda `After="Wpf Line Number Margin"` (görünürse) sol tarafta görünür.

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
 Etiketler, verileri farklı metin türleriyle bir şekilde bir arada bulundurabilirsiniz. Çoğu durumda, ilişkili veriler görsel bir etki olarak görüntülenir, ancak tüm etiketlerin görsel sunumu yoktur. uygulayarak kendi etiket türlerinizi <xref:Microsoft.VisualStudio.Text.Tagging.ITag> tanımlayabilirsiniz. Ayrıca, verilen bir metin aralığı kümesi için etiketleri sağlamak için ve etiketger sağlamak için <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> bir de uygulamanız gerekir. Tagger sağlayıcısını aşağıdaki özniteliklerle birlikte dışarı aktarmalısiniz:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: etiketinizin geçerli olduğu içerik türü ("metin" veya "kod") .

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: etiket tün.

  Aşağıdaki örnek, bir etiket sağlayıcısında dışarı aktarma özniteliklerini gösterir.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> Aşağıdaki etiket türleri yerleşiktir:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: bir ile <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> ilişkilendirildi.

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: hata türleriyle ilişkilendirildi.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: bir donatma ile ilişkili.

  > [!NOTE]
  > bir örneği için, <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> [Walkthrough: Highlighting Text](../extensibility/walkthrough-highlighting-text.md)içinde HighlightWordTag tanımına bakın.

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: altı çizili olarak genişletilen veya daraltılmış bölgeler ile ilişkilendirildi.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: bir donatma metninin kapladığı alanı tanımlar. Alan anlaşmaları hakkında daha fazla bilgi için aşağıdaki bölüme bakın.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: donatma için otomatik aralık ve boyutlandırma sağlar.

  Arabellekler ve görünümler için etiketleri bulmak ve kullanmak üzere, veya türünü içeri aktarın. Bu, size istenen türde <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> bir veri <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> sağlar. Aşağıdaki kod bu hizmeti bir özellik olarak içeri aktarmaktadır.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Etiketler ve MarkerFormatDefinitions
 Bir etiketin <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> görünümünü tanımlamak için sınıfını genişletebilirsiniz. Sınıfınızı (olarak) aşağıdaki <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> özniteliklerle dışarı aktarmanız gerekir:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: bu biçime başvuru yapmak için kullanılan ad

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Bu, biçimin kullanıcı arabiriminde görünmesine neden olur

  Oluşturucuda etiketin görünen adını ve görünümünü tanımlarsiniz. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> dolgu rengini tanımlar ve <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> kenarlık rengini tanımlar. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>, biçim tanımının yerelleştirilebilir adıdır.

  Aşağıda, bir biçim tanımı örneği ve ardından ve bir örnek ve ardından ve bir örnek ve ardından bir biçim tanımı ve daha fazla bilgi ve daha fazla bilgi ve daha fazla

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

 Bu biçim tanımını bir etikete uygulamak için sınıfın name özniteliğinde ayar adınıza (görünen ad değil) başvurabilirsiniz.

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

 Donatma örneğini başlatarak olayı uygulayan <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> ve <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> işleyen ikinci bir sınıf oluşturmanız gerekir. Bu sınıfı aşağıdaki özniteliklerle birlikte dışarı aktarın:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: donatma geçerli olduğu içerik türü (örneğin, "metin" veya "kod").

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: Bu donatma için geçerli metin görünümü. sınıfı, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> önceden tanımlanmış metin görünümü rolleri kümesine sahiptir. Örneğin, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> öncelikle dosyaların metin görünümleri için kullanılır. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> , bir kullanıcının fare ve klavye kullanarak düzenleyemez veya gezine metne yönelik görünümler için kullanılır. Görünümlere <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> örnek olarak düzenleyici metin görünümü ve Çıkış **penceresi** gösterilir.

  Aşağıdaki örnek, donatma sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Boşluk anlaşmalı donatma, alanı metinle aynı düzeyde kaplar. Bu tür bir donatma oluşturmak için, donatma kapladığı alan miktarını tanımlayan 'den devralan <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> bir etiket sınıfı tanımlamanız gerekir.

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

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: bu bırakma işleyicinin geçerli olduğu metin biçimi. Aşağıdaki biçimler, öncelik sırasına göre en yüksekten en düş düşmektedir:

  1. Herhangi bir özel biçim

  2. Filedrop

  3. EnhancedMetafile

  4. Waveaudio

  5. Rıff

  6. Dıf

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

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: varsayılan bırakma işleyicisinden önce veya sonra bırakma işleyicisinin sıralaması. Visual Studio için varsayılan bırakma işleyicisi "defaultfiledrophandler" olarak adlandırılmıştır.

  Aşağıdaki örnek, bir bırakma işleyici sağlayıcısında dışarı aktarma özniteliklerini gösterir.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Düzenleyici seçeneklerini genişletme
 Seçenekleri yalnızca belirli bir kapsamda (örneğin, bir metin görünümünde) geçerli olacak şekilde tanımlayabilirsiniz. düzenleyici, bu öntanımlı seçenekler kümesini sağlar: düzenleyici seçenekleri, görüntüleme seçenekleri ve Windows Presentation Foundation (WPF) görünüm seçenekleri. Bu seçenekler <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> ,, ve içinde bulunabilir <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

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
