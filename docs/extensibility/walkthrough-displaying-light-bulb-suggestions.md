---
title: 'adım adım kılavuz: Ampul Önerilerini görüntüleme | Microsoft Docs'
description: Bu izlenecek yolu kullanarak geçerli sözcükte Visual Studio ve önerilen iki eyleme sahip olan bir ampulü düzenleyicide nasıl oluşturabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0cdb146d44b768912a157a5d60a91d20957553c13f3c2303a5bdd8d9cf82d58f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375032"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Adım adım kılavuz: Ampul önerilerini görüntüleme
Ampuller, Visual Studio düzenleyicide bulunan ve yerleşik kod çözümleyicileri veya kod yeniden düzenlemesi tarafından tanımlanan sorunlara yönelik düzeltmeler gibi bir dizi eylemi görüntülemek için genişletilen simgelerdir.

 Visual C# ve Visual Basic düzenleyicilerde, .NET Compiler Platform ("Roslyn") kullanarak kendi kod çözümleyicilerinizi otomatik olarak ampulleri görüntüleme eylemleriyle yazabilir ve paketleyebilirsiniz. Daha fazla bilgi için bkz.

- [Nasıl: C# tanılama ve kod düzeltmesi yazma](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix.md)

- [Nasıl Visual Basic: Tanılama ve kod düzeltmesi yazma](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix.md)

  C++ gibi diğer diller de, bu işlevin saplama uygulaması oluşturma önerisi gibi bazı hızlı eylemler için ampuller sağlar.

  Ampul şu şekildedir. Bir Visual Basic veya Visual C# projesinde, geçersiz olduğunda değişken adının altında kırmızı bir geçiş görünür. Fareyle geçersiz tanımlayıcının üzerine gelirsiniz, imlecin yanında bir ampul görünür.

  ![Ampul](../extensibility/media/lightbulb.png "Ampul")

  Ampulün aşağı okuna tıklarsanız, seçilen eylemin önizlemesi ile birlikte bir dizi önerilen eylem görüntülenir. Bu durumda, eylemi yürütürsanız kodunda yapılan değişiklikler gösterir.

  ![ampul önizlemesi](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Kendi önerdiğiniz eylemleri sağlamak için ampulleri kullanabilirsiniz. Örneğin, açılış küme ayraçlarını yeni bir satıra taşımak veya önceki satırın sonuna taşımak için eylemler sebilirsiniz. Aşağıdaki kılavuzda, geçerli sözcükte görünen ve önerilen iki eyleme sahip bir ampulün nasıl oluşturularak ilgili bilgiler **verilmektedir:** **Büyük** harfe dönüştürme ve Küçük harfe dönüştür.

## <a name="prerequisites"></a>Önkoşullar
 2015 Visual Studio den başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Kurulumda isteğe bağlı bir özellik olarak Visual Studio dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma

1. C# VSIX projesi oluşturun. (Yeni **Project** iletişim kutusunda Visual **C# / Genişletilebilirlik'i** seçin, ardından **VSIX Project**.) Çözüme adını `LightBulbTest` girin.

2. Projeye **bir Düzenleyici Sınıflandırıcı** öğesi şablonu ekleyin. Daha fazla bilgi için [bkz. Düzenleyici öğesi şablonuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Mevcut sınıf dosyalarını silin.

4. Projeye aşağıdaki başvuru ekleyin ve Yereli **Kopyala'ya** `False` ayarlayın:

     *Microsoft.VisualStudio.Language.IntelliSense*

5. Yeni bir sınıf dosyası ekleyin ve **LightBulbTest olarak ad girin.**

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

1. *LightBulbTest.cs* sınıf dosyasında LightBulbTest sınıfını silin. uygulayan **TestSuggestedActionsSourceProvider adlı** bir sınıf <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> ekleyin. Test Önerilen Eylemleri adı ve **"metin"** <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ile dışarı aktarın.

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Kaynak sağlayıcı sınıfının içinde, içeri <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> aktarın ve bir özellik olarak ekleyin.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Nesnesini <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> geri dönmek için yöntemini <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> uygulama. Kaynak, sonraki bölümde ele alınmıştır.

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
 Önerilen eylem kaynağı, önerilen eylem kümelerini toplamak ve bunları doğru bağlamda eklemekten sorumludur. Bu durumda bağlam geçerli sözcüktür ve önerilen eylemler, aşağıdaki bölümde ele alınmıştır: **UpperCaseSuggestedAction** ve **LowerCaseSuggestedAction.**

1. uygulayan **bir TestSuggestedActionsSource** sınıfı <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> ekleyin.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Önerilen eylem kaynağı sağlayıcısı, metin arabelleği ve metin görünümü için özel, salt okunur alanlar ekleyin.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Özel alanları ayaran bir oluşturucu ekleyin.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. İmlecin altında bulunan sözcüğü döndüren özel bir yöntem ekleyin. Aşağıdaki yöntem imlecin geçerli konumunu kontrol eder ve metin yapısı gezginine sözcüğün kapsamını sorar. İmleç bir sözcük üzerinde ise, out parametresinde döndürülür; aksi takdirde <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> parametresi olur ve yöntemi `out` `null` `false` döndürür.

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

5. yöntemini <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> uygulama. Düzenleyici bu yöntemi çağırarak ampulün görüntü olup olmadığını bulur. Bu çağrı genellikle imleç bir satırdan diğerine her hareket ettiğinde veya fare bir hata geçişin üzerine geldiğinde yapılır. Bu yöntem çalışırken diğer kullanıcı arabirimi işlemlerinin devamsına izin vermek zaman uyumsuz bir işlemdir. Çoğu durumda, bu yöntemin geçerli satırda bazı ayrıştırma ve analiz işlemleri gerçekleştirmesi gerekir, bu nedenle işlem biraz zaman alır.

     Bu uygulamada, uzantıyı zaman uyumsuz olarak alır ve içinde olduğu gibi, boşluk dışında bir metin olup olmadığını önemli olup <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> olmadığını belirler.

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

6. Farklı <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> nesneleri içeren bir nesne dizisi <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> döndüren yöntemini <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> uygulama. Ampul genişletilirken bu yöntem çağrılır.

    > [!WARNING]
    > ve uygulamalarının tutarlı olduğundan emin olun; yani `HasSuggestedActionsAsync()` `GetSuggestedActions()` , `HasSuggestedActionsAsync()` `true` döndürürse, görüntü için bazı `GetSuggestedActions()` eylemlere sahip olmalıdır. Çoğu durumda, `HasSuggestedActionsAsync()` hemen önce `GetSuggestedActions()` çağrılır, ancak her zaman böyle değildir. Örneğin, kullanıcı ampul eylemlerini yalnızca **(CTRL+** .) tuşlarına basarak `GetSuggestedActions()` çağırırsa çağrılır.

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

7. Bir olay `SuggestedActionsChanged` tanımlayın.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Uygulamasını tamamlamak için ve yöntemlerine yönelik `Dispose()` `TryGetTelemetryId()` uygulamalar ekleyin. Telemetri yapmak istemiyor, bu nedenle yalnızca dönüp `false` GUID'i olarak `Empty` ayarlayın.

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

1. Proje içinde, yerel dosyanıza bir başvuru *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* ve **Yereli Kopyala'ya** `False` ayarlayın.

2. İlk adı ve adlı ikinci `UpperCaseSuggestedAction` sınıf olmak için iki sınıf `LowerCaseSuggestedAction` oluşturun. Her iki sınıf da <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> uygulanır.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Her iki sınıf da bir çağrısı ve diğer <xref:System.String.ToUpper%2A> çağrılar dışında birbirine <xref:System.String.ToLower%2A> benzer. Aşağıdaki adımlar yalnızca büyük harf eylem sınıfını içerir, ancak her iki sınıfı da uygulamalısiniz. Küçük harf eylemini uygulamak için büyük harf eylemini desen olarak uygulamak için adımları kullanın.

3. Bu sınıflar için aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Bir dizi özel alan bildir.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Alanları ayaran bir oluşturucu ekleyin.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Eylem <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> önizlemesini görüntülemek için yöntemini uygulama.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Boş <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> bir numaralama döndüren <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> yöntemi uygulama.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Özellikleri aşağıdaki gibi uygulama.

    ```csharp
    public bool HasActionSets
    {
        get { return false; }
    }
    public string DisplayText
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

9. Yayma <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> süresinde metni büyük harf eşdeğeri ile değiştirerek yöntemini uygulama.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Ampul eylemi **Invoke yönteminin** kullanıcı arabirimini göstermesi beklenmiyor. Eyleminiz yeni kullanıcı arabirimini getiriyorsa (örneğin önizleme veya seçim iletişim kutusu), kullanıcı arabirimini doğrudan **Invoke** yönteminin içinde görüntülemez, bunun yerine Çağır'dan döndüren kullanıcı arabiriminizi görüntülemek üzere **zamanlamayın.**

10. Uygulamasını tamamlamak için ve `Dispose()` `TryGetTelemetryId()` yöntemlerini ekleyin.

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

11. Görüntüleme metnini "Convert ' to lower case" (''küçük harfe dönüştür) olarak değiştirmek ve çağrısı yapmak için `LowerCaseSuggestedAction` {0} de aynı şeyi <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A> unutmayın.

## <a name="build-and-test-the-code"></a>Kodu derleme ve test
 Bu kodu test etmek için LightBulbTest çözümünü derleme ve Deneysel örnekte çalıştırma.

1. Çözümü derleyin.

2. Bu projeyi hata ayıklayıcısında çalıştırarak ikinci bir Visual Studio başlat.

3. Bir metin dosyası oluşturun ve metin yazın. Metnin sol tarafından bir ampul görüyor gerekir.

     ![ampulü test etmek](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Ampule işaret et. Bir aşağı ok görüyor gerekir.

5. Ampule tıklarken, seçilen eylemin önizlemesi ile birlikte önerilen iki eylem görüntüleniyor gerekir.

     ![test ampulü, genişletilmiş](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. İlk eyleme tıklarsanız, geçerli sözcükteki tüm metnin büyük harfe dönüştürülmesi gerekir. İkinci eyleme tıklarsanız, tüm metin küçük harfe dönüştürülmesi gerekir.
