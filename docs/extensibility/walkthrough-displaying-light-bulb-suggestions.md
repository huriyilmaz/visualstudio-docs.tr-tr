---
title: 'Walkthrough: Ampul Önerileri Görüntüleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697479"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Walkthrough: Ekran ampul önerileri
Ampuller, Visual Studio düzenleyicisinde bir dizi eylemi görüntülemek için genişleyen simgelerdir, örneğin, yerleşik kod çözümleyicileri veya kod yeniden düzenleme tarafından tanımlanan sorunları giderir.

 Visual C# ve Visual Basic editörlerinde, ampulleri otomatik olarak görüntüleyen eylemlerle kendi kod çözümleyicilerinizi yazmak ve paketlemek için .NET Derleyici Platformu'nu ("Roslyn") de kullanabilirsiniz. Daha fazla bilgi için bkz.

- [Nasıl Yazılır: C# tanılama ve kod düzeltmesi yazma](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Nasıl YapılSın: Visual Basic tanılama ve kod düzeltmesi yazma](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  C++ gibi diğer diller de, bu işlevin saplama uygulaması oluşturmak için bir öneri gibi bazı hızlı eylemler için ampuller sağlar.

  İşte ampul ün nasıl göründüğü. Visual Basic veya Visual C# projesinde, geçersiz olduğunda değişken bir ad altında kırmızı bir dalgalı belirir. Geçersiz tanımlayıcının üzerinden fare yle yaklaşırsanız, imlecin yanında bir ampul görüntülenir.

  ![Ampul](../extensibility/media/lightbulb.png "Ampul")

  Ampulün yanında aşağı ok'u tıklattığınızda, seçili eylemin önizlemesiyle birlikte önerilen eylemler kümesi görüntülenir. Bu durumda, eylemi yürütürseniz kodunuzda yapılan değişiklikleri gösterir.

  ![ampul önizleme](../extensibility/media/lightbulbpreview.png "AmpulÖnizleme")

  Kendi önerilen eylemleri sağlamak için ampuller kullanabilirsiniz. Örneğin, kıvırcık ayraçları yeni bir satıra taşımak veya önceki satırın sonuna taşımak için eylemler sağlayabilirsiniz. Aşağıdaki izlenme, geçerli sözcükte görünen ve önerilen iki eylemi olan bir ampulün nasıl oluşturulup oluşturulabildiğini gösterir: **Büyük harfe dönüştürün** ve **küçük harfe dönüştürün.**

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) projesi oluşturma

1. Bir C# VSIX projesi oluşturun. (Yeni **Proje** iletişim kutusunda Visual **C# / Genişletilebilirlik,** ardından **VSIX Project'i**seçin.) Çözümü `LightBulbTest`adlandırın.

2. Projeye **Bir Düzenleyici Sınıflandırıcı** öğesi şablonu ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Varolan sınıf dosyalarını silin.

4. Projeye aşağıdaki başvuruyu ekleyin ve Yerel `False` **Kopyala'yı** şu şekilde ayarlayın:

     *Microsoft.VisualStudio.Language.Intellisense*

5. Yeni bir sınıf dosyası ekleyin ve **lightBulbTest**adını.

6. Yönergeleri kullanarak aşağıdakileri ekleyin:

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

## <a name="implement-the-light-bulb-source-provider"></a>Ampul kaynak sağlayıcısını uygulayın

1. *LightBulbTest.cs* sınıfı dosyasında, LightBulbTest sınıfını silin. Uygulayan **TestSuggestedActionsSourceProvider** adlı bir <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>sınıf ekleyin. **Test Önerilen Eylemler** adı ve bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ile dışa aktarın.

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Kaynak sağlayıcı sınıfı içinde, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> içe aktarın ve bir özellik olarak ekleyin.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Bir <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> nesneyi döndürmek için yöntemi uygulayın. Kaynak sonraki bölümde ele alınmıştır.

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

## <a name="implement-the-isuggestedactionsource"></a>ISuggestedActionSource'u uygulayın
 Önerilen eylem kaynağı, önerilen eylem kümesini toplamaktan ve bunları doğru bağlamda eklemekten sorumludur. Bu durumda, bağlam geçerli sözcüktür ve önerilen eylemler aşağıdaki bölümde tartışılan **UpperCaseSuggestedAction** ve **LowerCaseSuggestedAction'dır.**

1. Bir sınıf **TestSuggestedActionsSource** uygular <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>ekleyin.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Önerilen eylem kaynağı sağlayıcısı, metin arabelleği ve metin görünümü için özel, salt okunur alanlar ekleyin.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Özel alanları ayarlayan bir oluşturucu ekleyin.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. İmlecin altında şu anda sözcüğü döndüren özel bir yöntem ekleyin. Aşağıdaki yöntem imlecin geçerli konumuna bakar ve sözcüğün kapsamını metin yapısı gezginine sorar. İmleç bir sözcükteyse, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> çıkış parametresi döndürülür; aksi takdirde, `out` parametre `null` ve `false`yöntem döndürür.

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

5. Yöntemi <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> uygulayın. Editör ampul görüntülemek için olup olmadığını öğrenmek için bu yöntemi çağırır. Bu çağrı genellikle, örneğin imleç bir satırdan diğerine geçtiğinde veya fare bir hata squiggle üzerinde gezinirken yapılır. Bu yöntem çalışırken diğer Kullanıcı Bira sı işlemlerinin devam etmesine izin vermek için kullanılan bir senkrondur. Çoğu durumda, bu yöntemin geçerli satırın bazı ayrışma ve çözümleme gerçekleştirmek gerekir, bu nedenle işleme biraz zaman alabilir.

     Bu uygulamada, eşzamanlı olarak alır <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> ve ölçüde önemli olup olmadığını belirler, gibi, beyaz alan dışında bazı metin olup olmadığını.

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

6. Farklı <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> nesneleri içeren bir dizi nesne döndüren yöntemi uygulayın. Bu yöntem ampul genişletildiğinde denir.

    > [!WARNING]
    > Uygulamaların tutarlı `HasSuggestedActionsAsync()` ve `GetSuggestedActions()` tutarlı olduğundan emin olmalısınız; diğer bir `HasSuggestedActionsAsync()` de, döndürürse, `true`görüntülemek için bazı eylemler `GetSuggestedActions()` olmalıdır. Birçok durumda, `HasSuggestedActionsAsync()` hemen önce `GetSuggestedActions()`denir, ama bu her zaman böyle değildir. Örneğin, kullanıcı **(CTRL+** .) tuşuna basarak ampul `GetSuggestedActions()` eylemlerini çağırırsa yalnızca çağrılır.

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

7. Bir `SuggestedActionsChanged` olayı tanımlayın.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Uygulamayı tamamlamak için, uygulamalar `Dispose()` ve `TryGetTelemetryId()` yöntemler ekleyin. Telemetri yapmak istemiyorsanız, geri dönün `false` ve GUID'i `Empty`.

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

## <a name="implement-light-bulb-actions"></a>Ampul eylemlerini uygulayın

1. Projede, *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* adresine bir başvuru ekleyin `False`ve **Copy Local'ı** .

2. İlk adlandırılmış `UpperCaseSuggestedAction` ve ikincisi adlandırılmış `LowerCaseSuggestedAction`iki sınıf oluşturun. Her iki <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>sınıf da uygular.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Her iki sınıf da bir <xref:System.String.ToUpper%2A> arama ve <xref:System.String.ToLower%2A>diğer aramalar dışında benzerdir. Aşağıdaki adımlar yalnızca büyük harfeylem sınıfını kapsar, ancak her iki sınıfı da uygulamanız gerekir. Küçük harf eylemini uygulamak için bir desen olarak büyük harf eylemini uygulamak için adımları kullanın.

3. Bu sınıflar için yönergeleri kullanarak aşağıdakileri ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Özel alanlar kümesini bildirin.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Alanları ayarlayan bir oluşturucu ekleyin.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Eylemi <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> önizlemesini görüntüleyebilmek için yöntemi uygulayın.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> Boş bir <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> numaralandırmayı döndürebilecek şekilde yöntemi uygulayın.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Özellikleri aşağıdaki gibi uygulayın.

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

9. Açıktaki <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> metni büyük harf eşdeğeriyle değiştirerek yöntemi uygulayın.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Ampul eylem **Invoke** yöntemi UI göstermek için beklenmiyor. Eyleminiz yeni UI'yi (örneğin önizleme veya seçim iletişim kutusu) gündeme getiriyorsa, UI'yi doğrudan **Çağırma** yönteminin içinden görüntülemeyin, bunun yerine **Çağrı'dan**döndükten sonra UI'nizi görüntülemek için zamanlayın.

10. Uygulamayı tamamlamak için, `Dispose()` ve `TryGetTelemetryId()` yöntemleri ekleyin.

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

11. Ekran metnini "Dönüştür ' `LowerCaseSuggestedAction` ' küçük harfe dönüştürmek"{0}ve ' için <xref:System.String.ToUpper%2A> çağrı <xref:System.String.ToLower%2A>yapmak için aynı şeyi yapmayı unutmayın.

## <a name="build-and-test-the-code"></a>Kodu oluşturma ve test edin
 Bu kodu test etmek için, LightBulbTest çözüm oluşturmak ve Deneysel örnekte çalıştırın.

1. Çözümü derleyin.

2. Bu projeyi hata ayıklamada çalıştırdığınızda, Visual Studio'nun ikinci bir örneği başlatılır.

3. Bir metin dosyası oluşturun ve bazı metin yazın. Metnin solunda bir ampul görmelisiniz.

     ![ampultest](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Ampulü işaret edin. Aşağı bir ok görmelisin.

5. Ampulü tıklattığınızda, önerilen iki eylem, seçili eylemin önizlemesiyle birlikte görüntülenmelidir.

     ![test ampul, genişletilmiş](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. İlk eylemi tıklattığınızda, geçerli sözcükteki tüm metin büyük harfe dönüştürülmelidir. İkinci eylemi tıklattığınızda, tüm metin küçük harfe dönüştürülmelidir.
