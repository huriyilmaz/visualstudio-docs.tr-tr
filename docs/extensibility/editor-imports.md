---
title: Düzenleyici Içeri aktarmaları | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712008"
---
# <a name="editor-imports"></a>Düzenleyici içeri aktarmaları
Uzantınız için çekirdek düzenleyiciye farklı türlerde erişim sağlayan bir dizi Düzenleyici hizmeti, fabrikası ve aracıları içeri aktarabilirsiniz. Örneğin, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> belirli bir içerik türü için size bir sağlamak üzere öğesini içeri aktarabilirsiniz <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> . (Bu gezgin, bir metin arabelleğinde farklı türlerde aramalar gerçekleştirmenize olanak tanır.)

 Bir düzenleyici içeri aktarması kullanmak için, onu Managed Extensibility Framework bileşen parçasını dışarı aktaran bir sınıfın alanı veya özelliği olarak içeri aktarırsınız.

> [!NOTE]
> Managed Extensibility Framework hakkında daha fazla bilgi için bkz. [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Sözdizimini içeri aktar
 Aşağıdaki örnek, düzenleyici seçenekleri fabrikası hizmetinin nasıl içe aktarılacağını gösterir.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Hizmeti bir özellik değil bir alan olarak içeri aktarmak istiyorsanız, `null` bir değişkene atamamak üzere derleyici uyarılarını önlemek için bildirimi bildirimde ayarlamanız gerekir:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 İçeri aktarmaları kullanma hakkında daha fazla örnek için aşağıdaki izlenecek yollara bakın:

- [İzlenecek yol: kenar boşluğu karakteri oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [İzlenecek yol: metin görünümünü özelleştirme](../extensibility/walkthrough-customizing-the-text-view.md)

- [İzlenecek yol: metni vurgula](../extensibility/walkthrough-highlighting-text.md)

- [İzlenecek yol: hızlı bilgi araç ipuçlarını görüntüle](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [İzlenecek yol: Imza yardımını görüntüle](../extensibility/walkthrough-displaying-signature-help.md)

- [İzlenecek yol: görüntüleme ifadesinin tamamlanması](../extensibility/walkthrough-displaying-statement-completion.md)

- [İzlenecek yol: ampul önerilerini görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Hizmet sağlayıcısını içeri aktarma
 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>Visual Studio Hizmetleri 'ne erişim sağlamak için aynı zamanda (Microsoft. VisualStudio. Shell. sabit. 10.0 derlemesinde bulunur) bir de içeri aktarabilirsiniz:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Daha fazla bilgi için bkz. [Izlenecek yol: bir düzenleyici UZANTıSıNDAN DTE nesnesine erişme](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) .

## <a name="services"></a>Hizmetler
 Düzenleyici Hizmetleri, genellikle bir hizmet sağlayan ve birden çok bileşen genelinde paylaşılan tek varlıklardır.

|İçeri Aktar|Saðlar|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Dosya uzantıları ve nesneler arasındaki ilişki <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|<xref:Microsoft.VisualStudio.Utilities.IContentType> nesneleri topluluğu.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> nesneyi.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Birçok Düzenleyici bağdaştırıcı nesnesi:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>Belirli bir metin görünümü için nesne.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.ITextDocument> .|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>Farklar.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>Farklar.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> veya bir <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> nesne kümesi için <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Bir için bir <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Bir için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>Bir için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>Bir için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Nesne koleksiyonunu tutar <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> .|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> metin arabelleği için.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> metin görünümü için.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>Belirtilen kapsam için.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> metin görünümü için.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>Bir için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Nesneler aracılığıyla otomatik Girintiyi alır <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Bir için öğesini yönetir <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Bir anlık görüntü yayılma kümesinden RTF biçimli metin oluşturur.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Bir <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Bir <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> görünümdeki metin satırlarını biçimlendirmek için.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>İçin bir nesnesi <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Bir metin anlık görüntüsünü arar.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>İçin bir <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Bir <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> metin görünümü için.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Standart bir karakter kümesi.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>Bir için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Klavye işlemesini izler.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standart <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> nesneler.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Metin arabellekleri ve nesneler arasındaki ilişkiyi korur  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> .|

## <a name="other-imports"></a>Diğer içeri aktarmalar
 Sağlayıcı fabrikaları ve aracılar genellikle birden çok bileşende birden fazla örneğe sahip olan varlıklardır.

|İçeri Aktar|Saðlar|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Bir <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> türü <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> ) verilen arabellek için.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Metin işaretçisi etiketi oluşturma ( <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> türü <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>Verilen için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Bir <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession> .|

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
