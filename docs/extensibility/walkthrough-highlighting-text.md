---
title: 'Walkthrough: Metin Vurgulama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697397"
---
# <a name="walkthrough-highlight-text"></a>Walkthrough: Metni vurgulama
Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçaları oluşturarak düzenleyiciye farklı görsel efektler ekleyebilirsiniz. Bu gözden geçirme, bir metin dosyasındaki geçerli sözcüğün her oluşumunu nasıl vurgulayabilirsiniz gösterir. Bir sözcük metin dosyasında birden fazla kez oluşursa ve caret'i tek bir oluşumda konumlandırSanız, her olay vurgulanır.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. Bir C# VSIX projesi oluşturun. (Yeni **Proje** iletişim kutusunda Visual **C# / Genişletilebilirlik,** ardından **VSIX Project'i**seçin.) Çözümü `HighlightWordTest`adlandırın.

2. Projeye Bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Varolan sınıf dosyalarını silin.

## <a name="define-a-textmarkertag"></a>TextMarkerTag tanımlama
 Metni vurgulamanın ilk adımı alt <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> sınıfve görünümünü tanımlamaktır.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>TextMarkerTag ve MarkerFormatDefinition tanımlamak için

1. Bir sınıf dosyası ekleyin ve **highlightWordTag**adını.

2. Aşağıdaki referansları ekleyin:

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

4. Devralan <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> bir sınıf oluşturun ve `HighlightWordTag`adını.

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Devralan <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>ikinci bir sınıf oluşturun ve `HighlightWordFormatDefinition`adını. Etiketiniz için bu biçim tanımını kullanmak için aşağıdaki özniteliklerle dışa aktarmanız gerekir:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: etiketler bu biçime başvurmak için bunu kullanır

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: bu, biçimin UI'de görünmesine neden olur

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. HighlightWordFormatDefinition için oluşturucu olarak, ekran adını ve görünümünü tanımlayın. Arka Plan özelliği dolgu rengini, Foreground özelliği ise kenarlık rengini tanımlar.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. HighlightWordTag'ın oluşturucusunda, oluşturduğunuz biçim tanımının adına geçirin.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Bir ITagger uygulayın
 Bir sonraki adım <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> arabirimi uygulamaktır. Bu arabirim, belirli bir metin arabelleği, metin vurgulama ve diğer görsel efektler sağlayan etiketleratar.

### <a name="to-implement-a-tagger"></a>Bir etiketer uygulamak için

1. Türü <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `HighlightWordTag`uygulayan bir sınıf oluşturun ve `HighlightWordTagger`adlandırın.

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Sınıfa aşağıdaki özel alanları ve özellikleri ekleyin:

    - Geçerli <xref:Microsoft.VisualStudio.Text.Editor.ITextView>metin görünümüne karşılık gelen bir ,

    - Metin <xref:Microsoft.VisualStudio.Text.ITextBuffer>görünümünün altında yatan metin arabelleğine karşılık gelen bir ,

    - Metni <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>bulmak için kullanılan bir, bir.

    - Metin <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>açıklıkları içinde gezinme yöntemleri olan bir, bir.

    - A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, vurgulamak için kelime kümesini içeren.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, geçerli sözcüğüne karşılık gelir.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, hangi caret geçerli konumuna karşılık gelir.

    - Kilit nesnesi.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Daha önce listelenen özellikleri başharfve ekler <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ve <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> olay işleyicileri bir oluşturucu ekleyin.

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

4. Olay işleyicileri her `UpdateAtCaretPosition` ikisi de yöntemi çağırır.

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

5. Ayrıca, güncelleştirme `TagsChanged` yöntemi tarafından çağrılan bir olay eklemeniz gerekir.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. Yöntem, `UpdateAtCaretPosition()` metin arabelleğindeki imlecin konumlandırıldığı sözcükle aynı olan her sözcüğü <xref:Microsoft.VisualStudio.Text.SnapshotSpan> bulur ve sözcüğün oluşumlarına karşılık gelen nesnelerin listesini kurar. Daha sonra `SynchronousUpdate`, `TagsChanged` bu olay yükseltir çağırır.

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
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
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
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. Bu, `SynchronousUpdate` özellikler `WordSpans` ve özellikler `CurrentWord` üzerinde eşzamanlı bir `TagsChanged` güncelleştirme gerçekleştirir ve olayı yükseltir.

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

8. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Yöntemi uygulamanız gerekir. Bu yöntem nesnelerin <xref:Microsoft.VisualStudio.Text.SnapshotSpan> bir koleksiyon alır ve etiket yayılmaları bir numaralandırma döndürür.

     C#'da, etiketlerin tembel değerlendirmesini (diğer bir deyişle, kümenin yalnızca tek tek öğelere erişildiğinde değerlendirilmesi) sağlayan bir verim yineleyicisi olarak bu yöntemi uygulayın. Visual Basic'te etiketleri bir listeye ekleyin ve listeyi döndürün.

     Burada yöntem mavi <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> bir arka plan <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>sağlayan bir "mavi" olan bir nesne döndürür.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

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
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Tagger sağlayıcısı oluşturma
 Etiketcünüzü oluşturmak için bir <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Bu sınıf bir MEF bileşeni parçasıdır, bu nedenle bu uzantı nın tanınması için doğru öznitelikleri ayarlamanız gerekir.

> [!NOTE]
> MEF hakkında daha fazla bilgi için [Yönetilen Genişletilebilirlik Çerçevesi 'ne (MEF)](/dotnet/framework/mef/index)bakın.

### <a name="to-create-a-tagger-provider"></a>Etiket sağlayıcı oluşturmak için

1. `HighlightWordTaggerProvider` Uygulayan <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>adlı bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> sınıf oluşturun ve "metin" ve bir <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>' ile dışa aktarın.

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Tagger'ı anında atabilmek için iki düzenleyici hizmeti, <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> ve , <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>içe aktarmanız gerekir.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Bir <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> örneğini döndürmek için `HighlightWordTagger`yöntemi uygulayın.

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Kodu oluşturma ve test edin
 Bu kodu sınamak için HighlightWordTest çözümlerini oluşturun ve deneme örneğinde çalıştırın.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>HighlightWordTest çözümlerini oluşturmak ve test etmek için

1. Çözümü derleyin.

2. Bu projeyi hata ayıklamada çalıştırdığınızda, Visual Studio'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve sözcüklerin yinelendiği bazı metinler yazın, örneğin , "merhaba merhaba".

4. İmleci "merhaba" olaylarından birine yerleştirin. Her olay mavi ile vurgulanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Walkthrough: İçerik türünü dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
