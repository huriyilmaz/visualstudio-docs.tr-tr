---
title: Düzenleyici İçeri Aktarma | Microsoft Docs
description: Uzantınıza çekirdek düzenleyiciye farklı türlerde erişim sağlayan düzenleyici hizmetlerini, fabrikaları ve aracıları içeri aktarmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f2fa91b41017512b3f38ad61b800b293e0abaa1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898350"
---
# <a name="editor-imports"></a>Düzenleyici içeri aktarmaları
Uzantınıza çekirdek düzenleyiciye farklı türlerde erişim sağlayan çeşitli düzenleyici hizmetlerini, fabrikaları ve aracıları içeri aktarabilirsiniz. Örneğin, size verilen içerik <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> türü için bir sağlamak için içeri <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> aktarabilirsiniz. (Bu gezgin, metin arabelleği üzerinde farklı türlerde aramalar gerçekleştirmeye olanak sağlar.)

 Bir düzenleyici içeri aktarmayı kullanmak için, bunu bir bileşen bölümünü dışarı aktaran bir sınıfın alanı veya özelliği Managed Extensibility Framework içeri aktarabilirsiniz.

> [!NOTE]
> Daha fazla bilgi için Managed Extensibility Framework bkz. [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>İçeri aktarma söz dizimi
 Aşağıdaki örnekte, düzenleyici seçenekleri fabrika hizmetinin nasıl içeri aktar olduğu gösterir.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Hizmeti bir özellik olarak değil alan olarak içeri aktararak değişkene atamamayla ilgili derleyici uyarılarından kaçınmak için bildiriminde olarak `null` ayarlayabilirsiniz:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 İçeri aktarmaları kullanma hakkında daha fazla örnek için aşağıdaki adım adım kılavuzlara bakın:

- [Adım adım kılavuz: Kenar boşluğu ifadesi oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Adım adım kılavuz: Metin görünümünü özelleştirme](../extensibility/walkthrough-customizing-the-text-view.md)

- [Adım adım kılavuz: Metni vurgulama](../extensibility/walkthrough-highlighting-text.md)

- [Adım adım kılavuz: QuickInfo araç ipucu görüntüleme](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [adım adım kılavuz: İmza Yardımı Görüntüleme](../extensibility/walkthrough-displaying-signature-help.md)

- [Adım adım kılavuz: Deyim tamamlamayı görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md)

- [Adım adım kılavuz: Ampul önerilerini görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Hizmet sağlayıcısını içeri aktarma
 Ayrıca, bir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (Microsoft.VisualStudio.Shell.Immutable.10.0 derlemesinde bulunur) içeri aktararak da Visual Studio erişebilirsiniz:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Daha [fazla bilgi için bkz. Kılavuz: Düzenleyici uzantısından DTE](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) nesnesine erişme.

## <a name="services"></a>Hizmetler
 Düzenleyici hizmetleri genellikle bir hizmet sağlayan ve birden çok bileşen arasında paylaşılan tek varlıklardır.

|İçeri Aktar|Sağ -lar|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Dosya uzantıları ve nesneler arasındaki <xref:Microsoft.VisualStudio.Utilities.IContentType> ilişki.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> nesneleri topluluğu.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> Nesne.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Birçok düzenleyici bağdaştırıcısı nesnesi:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Verilen <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> metin görünümü için bir nesne.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.ITextDocument> .|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Farklılıklardan <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> biri.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Farklılıklardan <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> biri.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> veya <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> bir .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> nesne kümesi <xref:Microsoft.VisualStudio.Text.ITextBuffer> için.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|için <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> bir <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|için <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|için <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|için <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Nesne koleksiyonunu <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> sürdürür.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Metin <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> arabelleği için.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Metin <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> görünümü için.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Belirtilen <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> kapsam için .|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Metin <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> görünümü için.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|için <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Otomatik girintiyi nesneler aracılığıyla <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> alır.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|için <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> yönetir.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Bir anlık görüntü aralığı kümesinden RTF biçimli metin üretir.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|için <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Görünümdeki <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> metin satırlarını biçimlendirmek için .|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|için <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> nesnesi.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Metin anlık görüntüsünü arar.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|bir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> için <xref:Microsoft.VisualStudio.Text.ITextBuffer> by <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Metin <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> görünümü için.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standart bir dizi glyph.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|için <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Klavye işlemeyi izler.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standart <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> nesneler.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Metin arabellekleri ile nesneler arasındaki ilişkiyi  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> sürdürür.|

## <a name="other-imports"></a>Diğer içeri aktarmalar
 Sağlayıcı fabrikaları ve aracıları genellikle birden çok bileşende birden çok örneğine sahip olan varlıklardır.

|İçeri Aktar|Sağ -lar|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Verilen <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> arabellek için türünde ) <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> .|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Metin işaretçisi etiketleyicisi <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> (türünde). <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Verilen <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> için <xref:Microsoft.VisualStudio.Text.Editor.ITextView> bir .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession> .|

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve düzenleyici uzantısı noktaları](../extensibility/language-service-and-editor-extension-points.md)
