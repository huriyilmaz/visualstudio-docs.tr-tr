---
title: Editör İthalat | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712008"
---
# <a name="editor-imports"></a>Düzenleyici alma
Uzantınızı çekirdek düzenleyiciye farklı türde erişim sağlayan bir dizi düzenleyici hizmeti, fabrika ve aracı yı içe aktarabilirsiniz. Örneğin, belirli bir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> içerik türü için <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> bir sağlamak için içe aktarabilirsiniz. (Bu gezgin, metin arabelleği üzerinde farklı türde aramalar yapmanızı sağlar.)

 Bir düzenleyici alma kullanmak için, yönetilen genişletilebilirlik çerçevesi bileşeni parçası dışa aktaran bir sınıfın alanı veya özelliği olarak içe aktarın.

> [!NOTE]
> Yönetilen Genişletilebilirlik Çerçevesi hakkında daha fazla bilgi için yönetilen [genişletilebilirlik çerçevesine (MEF)](/dotnet/framework/mef/index)bakın.

## <a name="import-syntax"></a>Sözdizimini alma
 Aşağıdaki örnek, düzenleyici seçenekleri fabrika hizmetini nasıl içe aktarılabildiğini gösterir.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Hizmeti bir özellik olarak değil, alan olarak almak istiyorsanız, `null` derleyicinin bir değişkene atamama uyarılarını önlemek için bunu beyannamede ayarlamanız gerekir:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Aktarımları kullanmayla ilgili daha fazla örnek için aşağıdaki izçıkışlara bakın:

- [Walkthrough: Bir kenar boşluğu gph oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [İzlenme: Metin görünümünü özelleştirme](../extensibility/walkthrough-customizing-the-text-view.md)

- [Walkthrough: Metni vurgulama](../extensibility/walkthrough-highlighting-text.md)

- [Walkthrough: QuickInfo araç ipuçlarını görüntüleyin](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Walkthrough: İmza Yardım Görüntüle](../extensibility/walkthrough-displaying-signature-help.md)

- [Walkthrough: Görüntü deyimi tamamlama](../extensibility/walkthrough-displaying-statement-completion.md)

- [Walkthrough: Ekran ampul önerileri](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Servis sağlayıcıyı içe aktarma
 Visual Studio hizmetlerine <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> erişmek için aynı şekilde (Microsoft.VisualStudio.Shell.Immutable.10.0 adresinde bulunan derlemede bulunan) bir araç da içe aktarabilirsiniz:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Bkz. Walkthrough: Daha fazla bilgi için [düzenleyici uzantısından DTE nesnesi](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) erişin.

## <a name="services"></a>Hizmetler
 Düzenleyici hizmetleri genellikle bir hizmet sağlayan ve birden çok bileşen arasında paylaşılan tek varlıklardır.

|İçeri Aktarma|Sağ -lar|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Dosya uzantıları ve <xref:Microsoft.VisualStudio.Utilities.IContentType> nesneler arasındaki ilişki.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> nesneleri topluluğu.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>Nesne.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Birçok düzenleyici bağdaştırıcı nesnesi:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Belirli <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> bir metin görünümü için bir nesne.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Farklılıklar. <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Farklılıklar. <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> ya <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>da.|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> <xref:Microsoft.VisualStudio.Text.ITextBuffer> nesne kümesi için.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Bir <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> için <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Bir <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> için <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Bir <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> için <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Bir <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> için <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Nesnelerin toplanmasını korur.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> metin arabelleği için.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Metin <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> görünümü için bir.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Belirtilen <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> kapsam için.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Metin <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> görünümü için bir.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Bir <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> için <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> Nesneler aracılığıyla otomatik girintiyi alır.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>için yönetir .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Anlık görüntü açıklıklarından RTF biçimli metin oluşturur.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> için <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Görünümdeki metin satırlarını biçimlendirmek için a. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> nesne <xref:Microsoft.VisualStudio.Text.Editor.ITextView>için bir .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Metin anlık görüntüsünü arar.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Bir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> by <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>için .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Metin <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> görünümü için bir.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standart bir glifler kümesi.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> için <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Klavye kullanımını izler.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standart <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> nesneler.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Metin arabellekleri ve <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> nesneler arasındaki ilişkiyi korur.|

## <a name="other-imports"></a>Diğer ithalatlar
 Sağlayıcı fabrikaları ve aracıları genellikle birden çok bileşende birden çok örneği olan varlıklardır.

|İçeri Aktarma|Sağ -lar|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Verilen <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> arabellek için a tipi). <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Bir metin işaretleyici <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> tagger <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>(bir tür.|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Belirli <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>için bir .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve editör uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
