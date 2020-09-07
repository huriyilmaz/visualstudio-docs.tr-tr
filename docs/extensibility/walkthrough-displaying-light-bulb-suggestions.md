---
title: 'İzlenecek yol: ampul önerilerini görüntüleme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86412b82b291ee395b35d654d3cde6d326e956f0
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508957"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>İzlenecek yol: ampul önerilerini görüntüleme
Hafif bulbs, Visual Studio düzenleyicisinde, yerleşik kod Çözümleyicileri veya kod yeniden düzenleme tarafından tanımlanan sorunlara yönelik düzeltmeler gibi bir dizi eylemi görüntüleyecek şekilde genişlettiğinde simgeler.

 Visual C# ve Visual Basic düzenleyicilerinde Ayrıca, açık bulbs 'leri otomatik olarak görüntüleyen eylemlerle kendi kod Çözümleyicileri yazmak ve paketlemek için .NET Compiler Platform ("Roslyn") de kullanabilirsiniz. Daha fazla bilgi için bkz.

- [Nasıl yapılır: C# tanısı ve kod onarımı yazma](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix.md)

- [Nasıl yapılır: Visual Basic tanılama ve kod onarımı yazma](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix.md)

  C++ gibi diğer diller Ayrıca, söz konusu işlevin saplama uygulamasını oluşturma önerisi gibi bazı hızlı eylemler için hafif bulbs de sağlar.

  İşte ampul şöyle görünür. Visual Basic veya Visual C# projesinde, geçersiz olduğunda bir değişken adının altında kırmızı renkli bir çizgi görünür. Geçersiz tanımlayıcı üzerinde fare yaparsanız imlecin yakınında bir ampul belirir.

  ![ampul](../extensibility/media/lightbulb.png "Ampul")

  Ampul için aşağı oka tıklarsanız, bir dizi Önerilen eylem, seçili eylemin önizlemesi ile birlikte görüntülenir. Bu durumda, eylemi çalıştırırsanız kodunuzda yapılan değişiklikleri gösterir.

  ![ampul Önizleme](../extensibility/media/lightbulbpreview.png "Açık Bulbpreview")

  Açık bulbs kullanarak kendi önerdiğimiz eylemleri sağlayabilirsiniz. Örneğin, küme ayracını yeni bir satıra taşımak veya önceki satırın sonuna taşımak için Eylemler sağlayabilirsiniz. Aşağıdaki izlenecek yol, geçerli kelimede görüntülenen ve iki önerilen eyleme sahip olan bir ampul oluşturmayı gösterir: **büyük harfe Dönüştür** ve **küçük harfe Dönüştür**.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma

1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `LightBulbTest` .

2. Projeye bir **Düzenleyici sınıflandırıcı** öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

4. Aşağıdaki başvuruyu projeye ekleyin ve yereli **Kopyala** ' yı ayarlayın `False` :

     *Microsoft. VisualStudio. Language. IntelliSense*

5. Yeni bir sınıf dosyası ekleyin ve onu **Lightbulbtest**olarak adlandırın.

6. Aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using System;
    using System.Linq;
    using System.Collections.Generic;
    using System.Threading.Tasks;
    using Microsoft.VisualStudio.Language.Intellisense;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;
    using System.Threading;

    ```

## <a name="implement-the-light-bulb-source-provider"></a>Ampul kaynak sağlayıcısını uygulama

1. *LightBulbTest.cs* sınıf dosyasında, LightBulbTest sınıfını silin. Öğesini uygulayan **Testmütedadctionssourceprovider** adlı bir sınıf ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> . **Önerilen bir test eylemi** adı ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ile dışarı aktarın.

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Kaynak sağlayıcısı sınıfının içinde öğesini içeri aktarıp <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> özellik olarak ekleyin.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>Bir nesne döndürmek için yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> . Kaynak, sonraki bölümde ele alınmıştır.

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>ISuggestedActionSource uygulama
 Önerilen eylem kaynağı, önerilen eylemlerin kümesini toplamaktan ve bunları doğru bağlama göre eklemekten sorumludur. Bu durumda, bağlam geçerli sözcüklerdir ve Önerilen Eylemler, aşağıdaki bölümde ele alınan en büyük bir **tekertedavction** ve küçük **casemütetik**.

1. Uygulayan bir **Testmüteakctionssource** sınıfı ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Önerilen eylem kaynak sağlayıcısı, metin arabelleği ve metin görünümü için özel, salt okuma alanları ekleyin.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Özel alanları ayarlayan bir Oluşturucu ekleyin.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. İmlecin altında olan sözcüğü döndüren özel bir yöntem ekleyin. Aşağıdaki yöntem imlecin geçerli konumuna bakar ve metin yapısı Gezginine sözcüğün kapsamını sorar. İmleç bir sözcükse, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> Out parametresinde döndürülür; Aksi takdirde, `out` parametresi `null` ve yöntemi döner `false` .

    ```csharp
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)
    {
        ITextCaret caret = m_textView.Caret;
        SnapshotPoint point;

        if (caret.Position.BufferPosition > 0)
        {
            point = caret.Position.BufferPosition - 1;
        }
        else
        {
            wordExtent = default(TextExtent);
            return false;
        }

        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);

        wordExtent = navigator.GetExtentOfWord(point);
        return true;
    }
    ```

5. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> . Düzenleyici, ampulün görüntülenip görüntülenmeyeceğini öğrenmek için bu yöntemi çağırır. Bu çağrı genellikle Örneğin, imleç bir satırdan diğerine gittiğinde veya fare bir hata dalgalı çizgi üzerine geldiğinde oluşur. Bu yöntem çalışırken diğer kullanıcı arabirimi işlemlerinin tamamlanmasına izin vermek için zaman uyumsuzdur. Çoğu durumda, bu yöntemin geçerli satırı ayrıştırma ve analiz gerçekleştirmesi gerekir, bu nedenle işleme biraz zaman alabilir.

     Bu uygulamada, zaman uyumsuz olarak ' i alır <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> ve kapsamın önemli olup olmadığını, boşluk dışında bir metin içerip içermediğini belirler.

    ```csharp
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        return Task.Factory.StartNew(() =>
        {
            TextExtent extent;
            if (TryGetWordUnderCaret(out extent))
            {
                // don't display the action if the extent has whitespace
                return extent.IsSignificant;
              }
            return false;
        });
    }
    ```

6. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>Farklı nesneleri içeren bir nesne dizisi döndüren yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> . Bu yöntem, ampul genişletildiğinde çağrılır.

    > [!WARNING]
    > Ve uygulamalarının tutarlı olduğundan emin olmanız gerekir `HasSuggestedActionsAsync()` `GetSuggestedActions()` ; Yani, `HasSuggestedActionsAsync()` döndürürse `true` `GetSuggestedActions()` görüntülenecek eylemlere sahip olmalıdır. Çoğu durumda, `HasSuggestedActionsAsync()` yalnızca daha önce çağrılır `GetSuggestedActions()` , ancak bu her zaman durum değildir. Örneğin, Kullanıcı (**CTRL +** .) tuşuna basarak ampul eylemlerini çağrılırsa, yalnızca `GetSuggestedActions()` çağırılır.

    ```csharp
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        TextExtent extent;
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)
        {
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };
        }
        return Enumerable.Empty<SuggestedActionSet>();
    }
    ```

7. Bir `SuggestedActionsChanged` olay tanımlayın.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Uygulamayı gerçekleştirmek için ve yöntemlerine yönelik uygulamalar ekleyin `Dispose()` `TryGetTelemetryId()` . Telemetriyi yapmak istemezsiniz, bu yüzden yalnızca `false` GUID değerini döndürün ve olarak ayarlayın `Empty` .

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample provider and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

## <a name="implement-light-bulb-actions"></a>Ampul eylemlerini uygulama

1. Projede, *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* bir başvuru ekleyin ve yereli **Kopyala** olarak ayarlayın `False` .

2. İlk adlandırılmış `UpperCaseSuggestedAction` ve ikinci adlı iki sınıf oluşturun `LowerCaseSuggestedAction` . Her iki sınıf de uygular <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> .

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Her iki sınıf de tek bir çağrı <xref:System.String.ToUpper%2A> ve diğer çağrılar dışında benzer <xref:System.String.ToLower%2A> . Aşağıdaki adımlar yalnızca büyük harfli eylem sınıfını kapsar, ancak her iki sınıfı da uygulamanız gerekir. Büyük harfli eylemi, küçük harfli eylemi uygulamak için bir model olarak uygulama adımlarını kullanın.

3. Bu sınıflar için aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Özel alanlar kümesi bildirin.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Alanları ayarlayan bir Oluşturucu ekleyin.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Yöntemi, <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> eylem önizlemesini görüntüleyecek şekilde uygulayın.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>Yöntemi boş bir sabit listesi döndüren şekilde uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> .

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Özellikleri aşağıdaki şekilde uygulayın.

    ```csharp
    public bool HasActionSets
    {
        get { return false; }
    }
    public string DisplayText
    {
        get { return m_display; }
    }
    public ImageMoniker IconMoniker
    {
       get { return default(ImageMoniker); }
    }
    public string IconAutomationText
    {
        get
        {
            return null;
        }
    }
    public string InputGestureText
    {
        get
        {
            return null;
        }
    }
    public bool HasPreview
    {
        get { return true; }
    }
    ```

9. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>Yayılma alanındaki metni büyük harfli eşdeğerleriyle değiştirerek yöntemini uygulayın.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Ampul eylemi **çağırma** yönteminin Kullanıcı arabirimini göstermesi beklenmez. Eyleminiz yeni kullanıcı arabirimi (örneğin, önizleme veya seçim iletişim kutusu) alıyorsa, Kullanıcı arabirimini doğrudan **Invoke** yönteminin içinden görüntülememeyin, bunun yerine **Invoke**'tan döndükten sonra Kullanıcı arabirimini görüntülemeyi zamanlayın.

10. Uygulamayı gerçekleştirmek için `Dispose()` ve `TryGetTelemetryId()` yöntemlerini ekleyin.

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample action and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

11. `LowerCaseSuggestedAction`Görüntülenecek metni "' ' öğesini {0} küçük harfe Dönüştür" ve çağrısı olacak şekilde değiştirmek için aynı şeyi yapmayın <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A> .

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için, LightBulbTest çözümünü derleyin ve deneysel örnekte çalıştırın.

1. Çözümü derleyin.

2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve metin yazın. Metnin solunda bir ampul görmeniz gerekir.

     ![ampul sınamasını yapın](../extensibility/media/testlightbulb.png "Testlightampul")

4. Ampul ışığı üzerine gelin. Aşağı ok görmeniz gerekir.

5. Ampul ' e tıkladığınızda, önerilen iki eylem, seçili eylemin önizlemesiyle birlikte görüntülenir.

     ![test ampul, genişletilmiş](../extensibility/media/testlightbulbexpanded.gif "Testlightbulbgenişletilen")

6. İlk eyleme tıklarsanız, geçerli sözcükteki tüm metinlerin büyük harfe dönüştürülmesi gerekir. İkinci eyleme tıklarsanız, tüm metinlerin küçük harfe dönüştürülmesi gerekir.
