---
title: 'İzlenecek yol: metni vurgulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d398164e910f7700645c01d26afbc631b1d434bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693332"
---
# <a name="walkthrough-highlighting-text"></a>İzlenecek Yol: Metni Vurgulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Managed Extensibility Framework (MEF) bileşen bölümleri oluşturarak düzenleyiciye farklı görsel etkiler ekleyebilirsiniz. Bu izlenecek yol, bir metin dosyasında geçerli sözcüğün her geçtiği yeri vurgulamanın nasıl yapılacağını gösterir. Bir kelime bir metin dosyasında birden çok kez oluşursa ve giriş işaretini tek bir tekrara konumlandırdıysanız, her oluşum vurgulanır.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF projesi oluşturma  
  
1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `HighlightWordTest` .  
  
2. Projeye bir düzenleyici sınıflandırıcı öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Varolan sınıf dosyalarını silin.  
  
## <a name="defining-a-textmarkertag"></a>TextMarkerTag tanımlama  
 Metni vurgulamanın ilk adımı, alt sınıfını <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ve görünümünü tanımlamanızı sağlar.  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Bir TextMarkerTag ve bir MarkerFormatDefinition tanımlamak için  
  
1. Bir sınıf dosyası ekleyin ve bunu **Highlightwordtag**olarak adlandırın.  
  
2. Aşağıdaki başvuruları ekleyin:  
  
    1. Microsoft. VisualStudio. CoreUtility  
  
    2. Microsoft. VisualStudio. Text. Data  
  
    3. Microsoft. VisualStudio. Text. Logic  
  
    4. Microsoft. VisualStudio. Text. UI  
  
    5. Microsoft. VisualStudio. Text. UI. WPF  
  
    6. System. ComponentModel. Composition  
  
    7. Presentation. Core  
  
    8. Presentation. Framework  
  
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
  
4. Öğesinden devralan bir sınıf oluşturun <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ve bunu adlandırın `HighlightWordTag` .  
  
    ```csharp  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5. Öğesinden devralan ikinci bir sınıf oluşturun <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> ve bunu HighlightWordFormatDefinition olarak adlandırın. Etiketinize yönelik bu biçim tanımını kullanmak için aşağıdaki özniteliklerle dışarı aktarmanız gerekir:  
  
    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: etiketleri bu biçime başvurmak için bunu kullanır  
  
    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Bu, biçimin kullanıcı arabiriminde görünmesine neden olur  
  
    ```csharp  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6. HighlightWordFormatDefinition oluşturucusunda, görünen adını ve görünümünü tanımlayın. Background özelliği, Fill rengini tanımlar, ön plan özelliği de kenarlık rengini tanımlar.  
  
    ```csharp  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7. HighlightWordTag kurucusunda, az önce oluşturduğunuz biçim tanımının adını geçirin.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>Uygulanan bir uygulama  
 Sonraki adım, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> arabirimini uygulamaktır. Bu arabirim, belirli bir metin arabelleğine, metin vurgulama ve diğer görsel etkileri sağlayan etiketlere atar.  
  
#### <a name="to-implement-a-tagger"></a>Bir Tagger uygulamak için  
  
1. Türünü uygulayan bir sınıf oluşturun <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `HighlightWordTag` ve bunu adlandırın `HighlightWordTagger` .  
  
    ```csharp  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2. Sınıfına aşağıdaki özel alanları ve özellikleri ekleyin:  
  
    - <xref:Microsoft.VisualStudio.Text.Editor.ITextView>Geçerli metin görünümüne karşılık gelen bir.  
  
    - <xref:Microsoft.VisualStudio.Text.ITextBuffer>Metin görünümünün altındaki metin arabelleğine karşılık gelen bir.  
  
    - <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>Metin bulmak için kullanılan bir.  
  
    - <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>Metin yayılmaları içinde gezinmek için yöntemler içeren bir.  
  
    - <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>Vurgulamak için sözcük kümesini içeren A.  
  
    - <xref:Microsoft.VisualStudio.Text.SnapshotSpan>Geçerli sözcüğe karşılık gelen bir.  
  
    - Giriş <xref:Microsoft.VisualStudio.Text.SnapshotPoint> işaretinin geçerli konumuna karşılık gelen bir.  
  
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
  
3. Daha önce listelenen özellikleri Başlatan, <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ve olay işleyicilerini ekleyen bir Oluşturucu ekleyin <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> .  
  
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
  
4. Olay işleyicileri her ikisi de `UpdateAtCaretPosition` yöntemini çağırır.  
  
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
  
5. Ayrıca `TagsChanged` Update yöntemi tarafından çağrılacak bir olay da eklemeniz gerekir.  
  
     [!code-csharp[VSSDKHighlightWordTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkhighlightwordtest/cs/highlightwordtag.cs#10)]
     [!code-vb[VSSDKHighlightWordTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhighlightwordtest/vb/highlightwordtag.vb#10)]  
  
6. `UpdateAtCaretPosition()`Yöntemi, metin arabelleğindeki, imlecin bulunduğu sözcüğe benzer ve sözcüğün oluşumlarına karşılık gelen nesnelerin bir listesini oluşturan her sözcüğü bulur <xref:Microsoft.VisualStudio.Text.SnapshotSpan> . Sonra `SynchronousUpdate` olayı oluşturan çağırır `TagsChanged` .  
  
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
  
7. , `SynchronousUpdate` Ve özellikleri üzerinde bir zaman uyumlu güncelleştirme gerçekleştirir `WordSpans` `CurrentWord` ve `TagsChanged` olayı yükseltir.  
  
    ```vb  
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
  
8. Yöntemini uygulamanız gerekir <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> . Bu yöntem bir nesne koleksiyonu alır <xref:Microsoft.VisualStudio.Text.SnapshotSpan> ve etiket yayılmaları listesini döndürür.  
  
     C# ' de, bu yöntemi, Etiketler için yavaş değerlendirmeyi (yani, yalnızca tek tek öğeler erişildiğinde küme değerlendirmesi) sağlayan bir yield Yineleyici olarak uygulayın. Visual Basic, etiketleri bir listeye ekleyin ve listeyi geri döndürün.  
  
     Bu yöntem, mavi bir <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> arka plan sağlayan "mavi" içeren bir nesne döndürür <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
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
  
## <a name="creating-a-tagger-provider"></a>Tagger sağlayıcısı oluşturma  
 Etiketinizi oluşturmak için bir uygulamanız gerekir <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . Bu sınıf bir MEF bileşeni bölümüdür, bu nedenle bu uzantının tanınması için doğru öznitelikleri ayarlamanız gerekir.  
  
> [!NOTE]
> MEF hakkında daha fazla bilgi için bkz. [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-create-a-tagger-provider"></a>Bir Tagger sağlayıcısı oluşturmak için  
  
1. Uygulayan adlı bir sınıf oluşturun `HighlightWordTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> ve bunu bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ve bir ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
    ```csharp  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2. <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>Etiketi oluşturmak için ve olmak üzere iki düzenleyici hizmetini içeri aktarmanız gerekir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .  
  
    ```csharp  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3. <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>Örneğini döndürmek için yöntemini uygulayın `HighlightWordTagger` .  
  
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
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
 Bu kodu test etmek için HighlightWordTest çözümünü derleyin ve deneysel örnekte çalıştırın.  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>HighlightWordTest çözümünü derlemek ve test etmek için  
  
1. Çözümü derleyin.  
  
2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği oluşturulur.  
  
3. Bir metin dosyası oluşturun ve sözcüklerin tekrarlandığı bir metin yazın, örneğin "Merhaba Merhaba Merhaba".  
  
4. İmleci "Hello" oluşumlarından birine konumlandırır. Her oluşum mavi renkle vurgulanmıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
