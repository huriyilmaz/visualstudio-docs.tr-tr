---
title: 'Adım adım kılavuz: Metin | Microsoft Docs'
description: Bu kılavuzda düzenleyiciye görsel etkiler ekleyerek bir metin dosyasında geçerli sözcüğün her oluşumunu vurgulamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0ccbc7dd098112706fb26d19a35e7d961fd89842
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725771"
---
# <a name="walkthrough-highlight-text"></a>Adım adım kılavuz: Metni vurgulama
Düzenleyiciye farklı görsel efektler eklemek için Managed Extensibility Framework (MEF) bileşeni parçaları oluşturabilirsiniz. Bu kılavuzda, geçerli sözcüğün bir metin dosyasındaki her oluşumunu vurgulamayı gösterir. Metin dosyasında bir sözcük birden fazla kez oluşursa ve dikkati bir kez konumlandırmanız, her oluşum vurgulanır.

## <a name="prerequisites"></a>Önkoşullar
 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Kurulumda isteğe bağlı bir özellik olarak Visual Studio dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. C# VSIX projesi oluşturun. (Yeni **Project** iletişim kutusunda Visual **C# / Genişletilebilirlik'i** seçin, ardından **VSIX Project**.) Çözüme adını `HighlightWordTest` girin.

2. Projeye bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz. Düzenleyici öğesi şablonuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Mevcut sınıf dosyalarını silin.

## <a name="define-a-textmarkertag"></a>TextMarkerTag tanımlama
 Metni vurgulamanın ilk adımı, alt sınıfa ekleme ve <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> görünümünü tanımlamadır.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>TextMarkerTag ve MarkerFormatDefinition tanımlamak için

1. Bir sınıf dosyası ekleyin ve **Bunu HighlightWordTag olarak adlayın.**

2. Aşağıdaki başvuruları ekleyin:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. Presentation.Core

    8. Presentation.Framework

3. Aşağıdaki ad alanlarını içeri aktarın.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. sınıfından devralan ve olarak <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ad alan bir sınıf `HighlightWordTag` oluşturun.

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. 'den devralan ikinci bir sınıf oluşturun <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> ve olarak ad `HighlightWordFormatDefinition` girin. Etiketiniz için bu biçim tanımını kullanmak üzere aşağıdaki özniteliklerle dışarı aktarmanız gerekir:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: etiketler bu biçime başvuru yapmak için bunu kullanır

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Bu, biçimin kullanıcı arabiriminde görünmesine neden olur

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. HighlightWordFormatDefinition oluşturucus nda görünen adını ve görünümünü tanımlayın. Background özelliği dolgu rengini tanımlarken Ön plan özelliği kenarlık rengini tanımlar.

    ```csharp
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. HighlightWordTag oluşturucus unda, oluşturduğunuz biçim tanımının adını girin.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>ITagger uygulama
 Sonraki adım arabirimini <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> uygulamaktır. Bu arabirim, belirli bir metin arabelleğine metin vurgulama ve diğer görsel etkileri sağlayan etiketler atar.

### <a name="to-implement-a-tagger"></a>Bir etiketger uygulamak için

1. türünde uygulayan bir <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> sınıf oluşturun ve olarak ad `HighlightWordTag` `HighlightWordTagger` girin.

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Sınıfına aşağıdaki özel alanları ve özellikleri ekleyin:

    - Geçerli <xref:Microsoft.VisualStudio.Text.Editor.ITextView> metin görünümüne karşılık gelen bir .

    - Metin <xref:Microsoft.VisualStudio.Text.ITextBuffer> görünümünün altında yer alan metin arabelleğine karşılık gelen bir .

    - Metin <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> bulmak için kullanılan bir .

    - Metin <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> aralıkları içinde gezinmek için yöntemleri olan bir .

    - Vurgulanan <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> sözcük kümesi içeren bir .

    - Geçerli <xref:Microsoft.VisualStudio.Text.SnapshotSpan> söze karşılık gelen bir .

    - Bir <xref:Microsoft.VisualStudio.Text.SnapshotPoint> , caret'in geçerli konumunu ifade ediyor.

    - Kilit nesnesi.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Daha önce listelenen özellikleri başlatan ve ve olay işleyicileri <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ekleyen <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> bir oluşturucu ekleyin.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. Her iki olay işleyicisi de yöntemini `UpdateAtCaretPosition` çağırıyor.

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. Update yöntemi tarafından `TagsChanged` çağrılan bir olay da eklemeniz gerekir.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkhighlightwordtest/cs/highlightwordtag.cs" id="Snippet10":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhighlightwordtest/vb/highlightwordtag.vb" id="Snippet10":::


6. yöntemi, metin arabelleğinde imlecin bulunduğu sözcükle aynı olan her sözcüğü bulur ve sözcüğün oluşumlarını karşılık gelen nesnelerin `UpdateAtCaretPosition()` <xref:Microsoft.VisualStudio.Text.SnapshotSpan> listesini oluşturur. Ardından, `SynchronousUpdate` olayı yükselten `TagsChanged` çağrısında bulundu.

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. `SynchronousUpdate`, ve özelliklerinde zaman uyumlu bir `WordSpans` güncelleştirme gerçekleştirir ve olayı `CurrentWord` `TagsChanged` yükselter.

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. yöntemini <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> uygulamalısiniz. Bu yöntem nesnelerinin <xref:Microsoft.VisualStudio.Text.SnapshotSpan> bir koleksiyonunu alır ve etiket aralıklarının bir numaralama döndürür.

     C# içinde, bu yöntemi etiketlerin yavaş değerlendirmesini (yalnızca tek öğelere erişilirken kümenin değerlendirilmesini) sağlayan bir verim iticisi olarak gerçekleştirin. Bu Visual Basic, etiketleri listeye ekleyin ve listeyi geri ekleyin.

     Burada yöntemi, mavi <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> arka plan sağlayan "mavi" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> bir nesnesi döndürür.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Tagger sağlayıcısı oluşturma
 Tagger'ını oluşturmak için bir uygulamanız <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> gerekir. Bu sınıf bir MEF bileşeni bölümü olduğu için, bu uzantının tanınması için doğru öznitelikleri ayarlayabilirsiniz.

> [!NOTE]
> MEF hakkında daha fazla bilgi için [bkz. Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Bir etiket sağlayıcısı oluşturmak için

1. uygulayan adlı bir sınıf oluşturun ve "text" ve bir ile dışarı `HighlightWordTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> aktarın.

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Etiketçinin örneğini almak için iki düzenleyici hizmeti (ve <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ) içeri aktarın.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. bir <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> örneğini dönmek için yöntemini `HighlightWordTagger` uygulama.

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Kodu derleme ve test
 Bu kodu test etmek için HighlightWordTest çözümünü derleme ve deneysel örnekte çalıştırma.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>HighlightWordTest çözümünü derlemek ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklayıcısında çalıştırarak ikinci bir Visual Studio başlat.

3. Bir metin dosyası oluşturun ve sözcüklerin tekrarlanan bir metin (örneğin, "hello hello hello" gibi) yazın.

4. İmleci "hello" oluşumlarından birinin üzerine getirin. Her oluşum mavi renkle vurgulanmış olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: İçerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
