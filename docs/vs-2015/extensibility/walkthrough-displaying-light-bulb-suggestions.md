---
title: 'İzlenecek yol: ampul önerilerini görüntüleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f135247241e8cf441cba2c1f63984dc69f7114c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64850655"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>İzlenecek Yol: Ampul Önerilerini Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hafif bulbs, Visual Studio düzenleyicisinde, yerleşik kod Çözümleyicileri veya kod yeniden düzenleme tarafından tanımlanan sorunların düzeltmeleri gibi bir dizi eylemi göstermek üzere genişleterek kullanılan simgelerdir.  
  
 Visual C# ve Visual Basic düzenleyicilerinde Ayrıca, açık bulbs 'leri otomatik olarak görüntüleyen eylemlerle kendi kod Çözümleyicileri yazmak ve paketlemek için .NET Compiler Platform ("Roslyn") de kullanabilirsiniz. Daha fazla bilgi için bkz.  
  
- [Nasıl yapılır: C# tanısı ve kod onarımı yazma](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
- [Nasıl yapılır: Visual Basic tanılama ve kod onarımı yazma](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
  C++ gibi diğer diller Ayrıca, söz konusu işlevin saplama uygulamasını oluşturma önerisi gibi bazı hızlı eylemler için hafif bulbs sağlar.  
  
  İşte ampul şöyle görünür. Visual Basic veya Visual C# projesinde, geçersiz olduğunda bir değişken adının altında kırmızı renkli bir çizgi görünür. Geçersiz tanımlayıcı üzerinde fare yaptığınızda imlecin yakınında bir ampul görüntülenir.  
  
  ![ampul](../extensibility/media/lightbulb.png "Ampul")  
  
  Ampul ışığının aşağı okuna tıkladığınızda, bir dizi Önerilen eylem, seçili eylemin önizlemesi ile birlikte görüntülenir. Bu durumda, eylemi çalıştırırsanız kodunuzda yapılacak değişiklikleri gösterir.  
  
  ![ampul Önizleme](../extensibility/media/lightbulbpreview.png "Açık Bulbpreview")  
  
  Açık bulbs kullanarak kendi önerdiğimiz eylemleri sağlayabilirsiniz. Örneğin, küme ayracını yeni bir satıra taşımak veya önceki satırın sonuna taşımak için Eylemler sağlayabilirsiniz. Aşağıdaki izlenecek yol, geçerli kelimede görüntülenen ve iki önerilen eyleme sahip olan bir ampul oluşturmayı gösterir: **büyük harfe Dönüştür** ve **küçük harfe Dönüştür**.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma  
  
1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `LightBulbTest` .  
  
2. Projeye bir **Düzenleyici sınıflandırıcı** öğe şablonu ekleyin. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Varolan sınıf dosyalarını silin.  
  
4. Aşağıdaki başvuruyu projeye ekleyin ve yereli **Kopyala** ' yı ayarlayın `False` :  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
5. Yeni bir sınıf dosyası ekleyin ve onu **Lightbulbtest**olarak adlandırın.  
  
6. Deyimleri kullanarak aşağıdakileri ekleyin:  
  
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
  
## <a name="implementing-the-light-bulb-source-provider"></a>Ampul kaynak sağlayıcısını uygulama  
  
1. LightBulbTest.cs sınıf dosyasında, LightBulbTest sınıfını silin. Öğesini uygulayan **Testmütedadctionssourceprovider** adlı bir sınıf ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> . **Önerilen bir test eylemi** adı ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ile dışarı aktarın.  
  
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
  
3. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>Bir nesne döndürmek için yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> . Kaynağı bir sonraki bölümde ele alınacaktır.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>ISuggestedActionSource uygulama  
 Önerilen eylem kaynağı, önerilen eylemlerin kümesini toplamaktan ve bunları doğru bağlama göre eklemekten sorumludur. Bu durumda, bağlam geçerli sözcüklerdir ve Önerilen Eylemler, aşağıdaki bölümde tartışacak olan en üst **üsteetmüm** ve küçük **casemümüm**.  
  
1. Uygulayan bir **Testmüteakctionssource** sınıfı ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2. Önerilen eylem kaynak sağlayıcısı, metin arabelleği ve metin görünümü için özel salt okuma alanları ekleyin.  
  
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
  
4. İmlecin altında olan sözcüğü döndüren özel bir yöntem ekleyin. Aşağıdaki yöntem imlecin geçerli konumuna bakar ve metin yapısı Gezginine sözcüğün kapsamını sorar. İmleç bir sözcükse, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> Out parametresinde döndürülür; Aksi takdirde `out` parametre olur `null` ve Yöntem döndürülür `false` .  
  
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
  
5. Yöntemini uygulayın <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> . Düzenleyici, ampulün görüntülenip görüntülenmeyeceğini öğrenmek için bu yöntemi çağırır. Bu çağrı oldukça sık yapılır, örneğin, imleç bir satırdan diğerine geçilişinde veya fare bir hata dalgalı çizgi üzerine geldiğinde. Bu yöntem çalışırken diğer kullanıcı arabirimi işlemlerinin tamamlanmasına izin vermek için zaman uyumsuzdur. Çoğu durumda, bu yöntemin geçerli satırı ayrıştırma ve analiz gerçekleştirmesi gerekir, bu nedenle işleme biraz zaman alabilir.  
  
     Uygulamamızda zaman uyumsuz olarak alır <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> ve kapsamın önemli olup olmadığını belirler, yani, boşluk dışında bir metin içerip içermediğini belirler.  
  
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
    > Ve uygulamalarının tutarlı olduğundan emin olmanız gerekir `HasSuggestedActionsAsync()` `GetSuggestedActions()` ; Yani, `HasSuggestedActionsAsync()` döndürürse `true` `GetSuggestedActions()` görüntülenecek eylemlere sahip olmalıdır. Çoğu durumda `HasSuggestedActionsAsync()` hemen hemen çağrılır `GetSuggestedActions()` , ancak bu her zaman durum değildir. Örneğin, Kullanıcı (CTRL +.) tuşuna basarak ampul eylemlerini çağrılırsa, yalnızca `GetSuggestedActions()` çağırılır.  
  
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
  
8. Uygulamayı gerçekleştirmek için ve yöntemlerine yönelik uygulamalar ekleyin `Dispose()` `TryGetTelemetryId()` . Telemetriyi yapmak istemiyorum, bu yüzden yalnızca false döndürün ve GUID 'yi Empty olarak ayarlayın.  
  
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
  
## <a name="implementing-light-bulb-actions"></a>Ampul gerçekleştirme eylemleri  
  
1. Projede, Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll bir başvuru ekleyin ve yereli **Kopyala** olarak ayarlayın `False` .  
  
2. İlk adlandırılmış `UpperCaseSuggestedAction` ve ikinci adlı iki sınıf oluşturun `LowerCaseSuggestedAction` . Her iki sınıf de uygular <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> .  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Her iki sınıf de tek bir çağrı <xref:System.String.ToUpper%2A> ve diğer çağrılar dışında benzer <xref:System.String.ToLower%2A> . Aşağıdaki adımlar yalnızca büyük harfli eylem sınıfını kapsar, ancak her iki sınıfı da uygulamanız gerekir. Büyük harfli eylemi, küçük harfli eylemi uygulamak için bir model olarak uygulama adımlarını kullanın.  
  
3. Bu sınıflar için aşağıdaki using deyimlerini ekleyin:  
  
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
    > Ampul eylemi **çağırma** yönteminin Kullanıcı arabirimini göstermesi beklenmez.  Eyleminiz yeni kullanıcı arabirimi (örneğin, önizleme veya seçim iletişim kutusu) alıyorsa, Kullanıcı arabirimini doğrudan **Invoke** yönteminin içinden görüntülememeyin, bunun yerine **Invoke**'tan döndükten sonra Kullanıcı arabirimini görüntülemeyi zamanlayın.  
  
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
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
 Bu kodu test etmek için, LightBulbTest çözümünü derleyin ve deneysel örnekte çalıştırın.  
  
1. Çözümü derleyin.  
  
2. Bu projeyi hata ayıklayıcıda çalıştırdığınızda, Visual Studio 'nun ikinci bir örneği oluşturulur.  
  
3. Bir metin dosyası oluşturun ve metin yazın. Metnin solunda bir ampul görmeniz gerekir.  
  
     ![ampul sınamasını yapın](../extensibility/media/testlightbulb.png "Testlightampul")  
  
4. Ampul ışığı üzerine gelin. Aşağı ok görmeniz gerekir.  
  
5. Ampul ' i tıklattığınızda, seçili eylemin önizlemesiyle birlikte önerilen iki eylem görüntülenmelidir.  
  
     ![test ampul, genişletilmiş](../extensibility/media/testlightbulbexpanded.gif "Testlightbulbgenişletilen")  
  
6. İlk eyleme tıklarsanız, geçerli sözcükteki tüm metinlerin büyük harfe dönüştürülmesi gerekir. İkinci eyleme tıklarsanız, tüm metinlerin küçük harfe dönüştürülmesi gerekir.
