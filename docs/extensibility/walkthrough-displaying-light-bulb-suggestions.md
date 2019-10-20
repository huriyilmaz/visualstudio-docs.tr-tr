---
title: 'İzlenecek yol: ampul önerilerini görüntüleme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9d0c0893e7e8bee2b28b095cab08165c8cafa08
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632627"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>İzlenecek yol: ampul önerilerini görüntüleme
Hafif bulbs, Visual Studio düzenleyicisinde, yerleşik kod Çözümleyicileri veya kod yeniden düzenleme tarafından tanımlanan sorunlara yönelik düzeltmeler gibi bir dizi eylemi görüntüleyecek şekilde genişlettiğinde simgeler.

 Görsel C# ve Visual Basic düzenleyicilerde, açık bulbs 'leri otomatik olarak görüntüleyen eylemlerle kendi kod Çözümleyicileri yazmak ve paketlemek için .net Compiler platform ("Roslyn") de kullanabilirsiniz. Daha fazla bilgi için bkz.:

- [Nasıl yapılır: C# tanılama ve kod onarımı yazma](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Nasıl yapılır: Visual Basic tanılama ve kod onarımı yazma](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  C++ Ayrıca, gibi diğer diller, söz konusu işlevin saplama uygulamasını oluşturma önerisi gibi bazı hızlı eylemler için hafif bulbs de sağlar.

  İşte ampul şöyle görünür. Visual Basic veya Visual C# projesinde, geçersiz olduğunda bir değişken adının altında kırmızı renkli bir çizgi görünür. Geçersiz tanımlayıcı üzerinde fare yaparsanız imlecin yakınında bir ampul belirir.

  ![ampul](../extensibility/media/lightbulb.png "Ampul")

  Ampul için aşağı oka tıklarsanız, bir dizi Önerilen eylem, seçili eylemin önizlemesi ile birlikte görüntülenir. Bu durumda, eylemi çalıştırırsanız kodunuzda yapılan değişiklikleri gösterir.

  ![ampul Önizleme](../extensibility/media/lightbulbpreview.png "Açık Bulbpreview")

  Açık bulbs kullanarak kendi önerdiğimiz eylemleri sağlayabilirsiniz. Örneğin, küme ayracını yeni bir satıra taşımak veya önceki satırın sonuna taşımak için Eylemler sağlayabilirsiniz. Aşağıdaki izlenecek yol, geçerli kelimede görüntülenen ve iki önerilen eyleme sahip olan bir ampul oluşturmayı gösterir: **büyük harfe Dönüştür** ve **küçük harfe Dönüştür**.

## <a name="prerequisites"></a>Prerequisites
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma

1. C# VSIX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **görsel C# /genişletilebilirlik**, sonra **VSIX projesi**' ni seçin.) @No__t_4 çözümü adlandırın.

2. Projeye bir **Düzenleyici sınıflandırıcı** öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Varolan sınıf dosyalarını silin.

4. Aşağıdaki başvuruyu projeye ekleyin ve **Yerel kopyayı** `False` olarak ayarlayın:

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

1. *LightBulbTest.cs* sınıf dosyasında, LightBulbTest sınıfını silin. @No__t_1 uygulayan **Testmütedadctionssourceprovider** adlı bir sınıf ekleyin. **Test önerilen eylemlerin** bir adı ve bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" ile dışarı aktarın.

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Kaynak sağlayıcısı sınıfının içinde, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> içeri aktarıp bir özellik olarak ekleyin.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Bir <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> nesnesi döndürmek için <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> yöntemini uygulayın. Kaynak, sonraki bölümde ele alınmıştır.

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

1. @No__t_1 uygulayan bir **Testmüteakctionssource** sınıfı ekleyin.

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

4. İmlecin altında olan sözcüğü döndüren özel bir yöntem ekleyin. Aşağıdaki yöntem imlecin geçerli konumuna bakar ve metin yapısı Gezginine sözcüğün kapsamını sorar. İmleç bir sözcükte ise, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> Out parametresinde döndürülür; Aksi takdirde, `out` parametresi `null` ve yöntemi `false` döndürür.

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

5. @No__t_0 yöntemini uygulayın. Düzenleyici, ampulün görüntülenip görüntülenmeyeceğini öğrenmek için bu yöntemi çağırır. Bu çağrı genellikle Örneğin, imleç bir satırdan diğerine gittiğinde veya fare bir hata dalgalı çizgi üzerine geldiğinde oluşur. Bu yöntem çalışırken diğer kullanıcı arabirimi işlemlerinin tamamlanmasına izin vermek için zaman uyumsuzdur. Çoğu durumda, bu yöntemin geçerli satırı ayrıştırma ve analiz gerçekleştirmesi gerekir, bu nedenle işleme biraz zaman alabilir.

     Bu uygulamada, zaman uyumsuz olarak <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> alır ve kapsamın, boşluk dışında bir metin içerip içermediğini belirler.

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

6. Farklı <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> nesneleri içeren <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> nesnelerden oluşan bir dizi döndüren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> yöntemini uygulayın. Bu yöntem, ampul genişletildiğinde çağrılır.

    > [!WARNING]
    > @No__t_0 ve `GetSuggestedActions()` uygulamalarının tutarlı olduğundan emin olun; diğer bir deyişle, `HasSuggestedActionsAsync()` `true` döndürürse `GetSuggestedActions()` bazı eylemleri görüntülemesi gerekir. Çoğu durumda, `HasSuggestedActionsAsync()` `GetSuggestedActions()` hemen önce çağrılır, ancak bu her zaman durum değildir. Örneğin, Kullanıcı (**CTRL +** .) tuşuna basarak ampul eylemlerini çağrılırsa yalnızca `GetSuggestedActions()` çağrılır.

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

7. @No__t_0 bir olay tanımlayın.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Uygulamayı gerçekleştirmek için, `Dispose()` ve `TryGetTelemetryId()` yöntemlerine yönelik uygulamalar ekleyin. Telemetri yapmak istemezsiniz, bu nedenle `false` döndürür ve GUID 'yi `Empty` olarak ayarlamanız yeterlidir.

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

1. Projede, *Microsoft. VisualStudio. Imaging. Interop. 14.0. DesignTime. dll* öğesine bir başvuru ekleyin ve **Yerel kopyayı** `False` olarak ayarlayın.

2. İlk adlandırılmış `UpperCaseSuggestedAction` ve ikinci adlandırılmış `LowerCaseSuggestedAction` olmak üzere iki sınıf oluşturun. Her iki sınıf de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> uygular.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Her iki sınıf de <xref:System.String.ToUpper%2A> ve diğer çağrılar <xref:System.String.ToLower%2A>. Aşağıdaki adımlar yalnızca büyük harfli eylem sınıfını kapsar, ancak her iki sınıfı da uygulamanız gerekir. Büyük harfli eylemi, küçük harfli eylemi uygulamak için bir model olarak uygulama adımlarını kullanın.

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

6. @No__t_0 yöntemini, eylem önizlemesini görüntüleyecek şekilde uygulayın.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Boş bir <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> numaralandırması döndüren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> yöntemini uygulayın.

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

9. Yayılma alanındaki metni büyük harfli eşdeğerleriyle değiştirerek <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> yöntemini uygulayın.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Ampul eylemi **çağırma** yönteminin Kullanıcı arabirimini göstermesi beklenmez. Eyleminiz yeni kullanıcı arabirimi (örneğin, önizleme veya seçim iletişim kutusu) alıyorsa, Kullanıcı arabirimini doğrudan **Invoke** yönteminin içinden görüntülememeyin, bunun yerine **Invoke**'tan döndükten sonra Kullanıcı arabirimini görüntülemeyi zamanlayın.

10. Uygulamayı tamamlamaya yönelik `Dispose()` ve `TryGetTelemetryId()` yöntemlerini ekleyin.

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

11. Görüntüleme metnini "' {0} ' öğesini küçük harfe Dönüştür" olarak değiştirmek `LowerCaseSuggestedAction` için aynı şeyi gerçekleştirmeyin ve çağrı <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A>.

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin
 Bu kodu test etmek için, LightBulbTest çözümünü derleyin ve deneysel örnekte çalıştırın.

1. Çözümü oluşturun.

2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve metin yazın. Metnin solunda bir ampul görmeniz gerekir.

     ![ampul sınamasını yapın](../extensibility/media/testlightbulb.png "Testlightampul")

4. Ampul ışığı üzerine gelin. Aşağı ok görmeniz gerekir.

5. Ampul ' e tıkladığınızda, önerilen iki eylem, seçili eylemin önizlemesiyle birlikte görüntülenir.

     ![test ampul, genişletilmiş](../extensibility/media/testlightbulbexpanded.gif "Testlightbulbgenişletilen")

6. İlk eyleme tıklarsanız, geçerli sözcükteki tüm metinlerin büyük harfe dönüştürülmesi gerekir. İkinci eyleme tıklarsanız, tüm metinlerin küçük harfe dönüştürülmesi gerekir.
