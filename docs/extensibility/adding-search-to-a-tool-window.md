---
title: Araç Penceresine Arama Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9112a3368ba604c4291f9018e763022e953c4fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740143"
---
# <a name="add-search-to-a-tool-window"></a>Araç penceresine arama ekleme
Uzantınızda bir araç penceresi oluşturduğunuzda veya güncellediğinizde, Visual Studio'nun başka bir yerinde görünen aynı arama işlevini ekleyebilirsiniz. Bu işlevsellik aşağıdaki özellikleri içerir:

- Araç çubuğunun özel bir alanında her zaman bulunan bir arama kutusu.

- Arama kutusunun üzerine konmuş bir ilerleme göstergesi.

- Her karaktere (anında arama) girer girmez veya **yalnızca Enter** tuşunu seçtikten sonra (isteğe bağlı arama) sonuçları gösterebilme özelliği.

- En son aradığınız terimleri gösteren bir liste.

- Aramaları belirli alanlara veya arama hedeflerinin yönlerine göre filtreleme yeteneği.

Bu izbiyi izleyerek, aşağıdaki görevleri nasıl gerçekleştireceğinizi öğreneceksiniz:

1. Bir VSPackage projesi oluşturun.

2. Salt okunur TextBox içeren bir araç penceresi oluşturun.

3. Araç penceresine bir arama kutusu ekleyin.

4. Arama uygulamasını ekleyin.

5. İlerleme çubuğunun anında aranmasını ve görüntülenmesini etkinleştirin.

6. **Eşle'lik durumu** seçeneği ekleyin.

7. Bir **Arama çift satırları yalnızca** filtre ekleyin.

## <a name="to-create-a-vsix-project"></a>Bir VSIX projesi oluşturmak için

1. **TestSearch**adlı bir `TestToolWindowSearch` araç penceresi ile adında bir VSIX projesi oluşturun. Bunu yaparken yardıma ihtiyacınız varsa, [bkz.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="to-create-a-tool-window"></a>Araç penceresi oluşturmak için

1. Projede `TestToolWindowSearch` *TestSearchControl.xaml* dosyasını açın.

2. Varolan `<StackPanel>` bloğu, araç penceresindeki salt okunur <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.UserControl> ekleyen aşağıdaki blokla değiştirin.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. *TestSearchControl.xaml.cs* dosyasına, aşağıdaki yönergeyi ekleyin:

    ```csharp
    using System.Text;
    ```

4. `button1_Click()` Yöntemi kaldırın.

     **TestSearchControl** sınıfına aşağıdaki kodu ekleyin.

     Bu kod, <xref:System.Windows.Controls.TextBox> **SearchResultsTextBox** adlı bir ortak özellik ve **SearchContent**adlı bir ortak dize özelliği ekler. Oluşturucuda, SearchResultsTextBox metin kutusuna ayarlanır ve SearchContent yeni bir çizgi-sınırlı dize kümesine başharfle ayarlanır. Metin kutusunun içeriği de dizeleri kümesine başharfle ayarlanır.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Projeyi oluşturun ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneği ortaya çıkar.

6. Menü çubuğunda**Diğer Windows** > **TestAramasını** **Görüntüle'yi** > seçin.

     Araç penceresi görüntülenir, ancak arama denetimi henüz görünmüyor.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Araç penceresine arama kutusu eklemek için

1. *TestSearch.cs* dosyasında, `TestSearch` sınıfa aşağıdaki kodu ekleyin. Kod, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> erişime erişim sağlayanın döndürür. `true`

     Aramayı etkinleştirmek için özelliği <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> geçersiz kılmanız gerekir. Sınıf, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> aramayı etkinleştirmeden varsayılan bir uygulama uygular ve sağlar.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir.

3. Visual Studio'nun deneysel örneğinde, **TestSearch'ü**açın.

     Araç penceresinin üst kısmında, **arama** filigranı ve büyüteç simgesiyle bir arama denetimi görüntülenir. Ancak, arama işlemi uygulanmadığından arama henüz çalışmaz.

## <a name="to-add-the-search-implementation"></a>Arama uygulamasını eklemek için
 Bir , <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>önceki yordamda olduğu gibi arama etkinleştirdiğinizde, araç penceresi bir arama ana bilgisayar oluşturur. Bu ana bilgisayar, her zaman bir arka plan iş parçacığı üzerinde oluşan arama işlemlerini kurar ve yönetir. <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Sınıf, arama ana bilgisayarının oluşturulmasını ve aramanın ayarını yönettiğinden, yalnızca bir arama görevi oluşturmanız ve arama yöntemini sağlamanız gerekir. Arama işlemi bir arka plan iş parçacığı üzerinde oluşur ve araç penceresi denetimine çağrılar UI iş parçacığı üzerinde oluşur. Bu nedenle, denetimle ilgili olarak yaptığınız aramaları yönetmek için [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) yöntemini kullanmanız gerekir.

1. *TestSearch.cs* dosyasına aşağıdaki `using` yönergeleri ekleyin:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. `TestSearch` Sınıfta, aşağıdaki eylemleri gerçekleştiren aşağıdaki kodu ekleyin:

    - Arama görevi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> oluşturmak için yöntemi geçersiz kılar.

    - Metin kutusunun <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> durumunu geri yüklemek için yöntemi geçersiz kılar. Bu yöntem, bir kullanıcı bir arama görevini iptal ettiğinde ve bir kullanıcı seçenekleri ayarladığında veya filtrelediğinde çağrır. Her <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> ikisi de ve UI iş parçacığı denir. Bu nedenle, [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) yöntemi ile metin kutusuna erişmeniz gerekmez.

    - 'den `TestSearchTask` <xref:Microsoft.VisualStudio.Shell.VsSearchTask>devralınan, varsayılan bir uygulama sağlayan bir sınıf <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>oluşturur.

         Kurucu, `TestSearchTask`araç penceresine başvuran özel bir alan ayarlar. Arama yöntemini sağlamak için, <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> yöntemleri <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> ve yöntemleri geçersiz kılarsınız. Yöntem, <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> arama işlemini uyguladığınız yerdir. Bu işlem, aramayı gerçekleştirmeyi, metin kutusunda arama sonuçlarını görüntülemeyi ve aramanın tamamolduğunu bildirmek için bu yöntemin taban sınıf uygulamasını çağırmayı içerir.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. Aşağıdaki adımları gerçekleştirerek arama uygulamanızı test edin:

    1. Projeyi yeniden oluştur ve hata ayıklamaya başlayın.

    2. Visual Studio'nun deneysel örneğinde, araç penceresini yeniden açın, arama penceresine bazı arama metni girin ve **ENTER'u**tıklatın.

         Doğru sonuçlar görünmelidir.

## <a name="to-customize-the-search-behavior"></a>Arama davranışını özelleştirmek için
 Arama ayarlarını değiştirerek, arama denetiminin nasıl göründüğü ve aramanın nasıl gerçekleştirildiği konusunda çeşitli değişiklikler yapabilirsiniz. Örneğin, filigranı (arama kutusunda görünen varsayılan metin), arama denetiminin minimum ve maksimum genişliğini ve ilerleme çubuğugösterip göstermeyeceğini değiştirebilirsiniz. Ayrıca, arama sonuçlarının görünmeye başladığı noktayı (isteğe bağlı veya anında arama) ve yakın zamanda arama yaptığınız terimlerin listesini gösterip göstermeyeceğiniz de değiştirebilirsiniz. <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> Sınıfta ayarların tam listesini bulabilirsiniz.

1. * TestSearch.cs* dosyasında sınıfa aşağıdaki `TestSearch` kodu ekleyin. Bu kod isteğe bağlı arama yerine anında arama yapılmasını sağlar (yani kullanıcı **ENTER'ı**tıklatmak zorunda değildir). Kod, varsayılan `ProvideSearchSettings` ayarları değiştirmek `TestSearch` için gerekli olan sınıftayöntemi geçersiz kılar.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Çözümü yeniden oluşturarak ve hata ayıklamayı yeniden başlatarak yeni ayarı test edin.

     Arama kutusuna her karakter girdiğinizde arama sonuçları görüntülenir.

3. `ProvideSearchSettings` Yöntemde, ilerleme çubuğunun görüntülenmesini sağlayan aşağıdaki satırı ekleyin.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     İlerleme çubuğunun görünmesi için ilerlemenin bildirilmesi gerekir. İlerlemeyi bildirmek için, `OnStartSearch` `TestSearchTask` sınıfın yönteminde aşağıdaki kodu açıklamamayı bırakın:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. İlerleme çubuğunun görünür olmasını yeterince yavaşlatmak için, `OnStartSearch` `TestSearchTask` sınıfın yönteminde aşağıdaki satırı açıklamamayı bırakın:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Çözümü yeniden oluşturarak ve hata ayıklama başlatarak yeni ayarları test edin.

     İlerleme çubuğu, her arama yaptığınızda arama penceresinde (arama metin kutusunun altındaki mavi çizgi olarak) görünür.

## <a name="to-enable-users-to-refine-their-searches"></a>Kullanıcıların aramalarını hassaslaştırmalarını sağlamak için
 Kullanıcıların **aramalarını, büyük/küçük/küçük harf le eşleştirme** veya tüm **sözcüğü eşleştir**gibi seçenekler le hassaslaştırmalarına izin verebilirsiniz. Seçenekler, onay kutuları olarak görünen boolean veya düğme olarak görünen komutlar olabilir. Bu izbis için bir boolean seçeneği oluşturursunuz.

1. *TestSearch.cs* dosyasında, `TestSearch` sınıfa aşağıdaki kodu ekleyin. Kod, arama `SearchOptionsEnum` uygulamasının belirli bir seçeneğin açılıp kapalı olup olmadığını algılamasına olanak tanıyan yöntemi geçersiz kılar. Kod, `SearchOptionsEnum` büyük/küçük harfle bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> sayısalatörle eşleşme seçeneği ekler. Kasayla eşleşme seçeneği de `MatchCaseOption` özellik olarak kullanılabilir hale getirilir.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. `TestSearchTask` Sınıfta, `OnStartSearch` yöntemde aşağıdaki satırı açıklama:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Seçeneği test edin:

    1. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir.

    2. Araç penceresinde, metin kutusunun sağ tarafındaki Aşağı ok'u seçin.

         **Eşle' nin büyük/küçük harf** onay kutusu görüntülenir.

    3. **Eşle'nin büyük/küçük harf** onay kutusunu seçin ve ardından bazı aramalar gerçekleştirin.

## <a name="to-add-a-search-filter"></a>Arama filtresi eklemek için
 Kullanıcıların arama hedefleri kümesini hassaslaştırmasına olanak tanıyan arama filtreleri ekleyebilirsiniz. Örneğin, Dosya Gezgini'ndeki dosyaları en son değiştirildikleri tarihlere ve dosya adı uzantılarına göre filtreleyebilirsiniz. Bu izbarada, yalnızca eşit satırlar için bir filtre eklersiniz. Kullanıcı bu filtreyi seçtiğinde, arama ana bilgisayarı arama sorgusuna belirttiğiniz dizeleri ekler. Daha sonra arama yönteminiz içindeki bu dizeleri tanımlayabilir ve arama hedeflerini buna göre filtreleyebilirsiniz.

1. *TestSearch.cs* dosyasında, `TestSearch` sınıfa aşağıdaki kodu ekleyin. Kod, yalnızca `SearchFiltersEnum` eşit <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> satırların görünmesi için arama sonuçlarını filtrelemek için bir belirti ekleyerek uygular.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Şimdi arama denetimi arama `Search even lines only`filtresini görüntüler. Kullanıcı filtreyi seçtiğinde, dize `lines:"even"` arama kutusunda görünür. Diğer arama ölçütleri filtreyle aynı anda görünebilir. Arama dizeleri filtreden önce, filtreden sonra veya her ikisi birden görünebilir.

2. *TestSearch.cs* dosyasında, `TestSearchTask` `TestSearch` sınıfta bulunan sınıfa aşağıdaki yöntemleri ekleyin. Bu yöntemler, `OnStartSearch` bir sonraki adımda değiştireceğiniz yöntemi destekler.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. `TestSearchTask` Sınıfta, `OnStartSearch` yöntemi aşağıdaki kodla güncelleştirin. Bu değişiklik, filtreyi desteklemek için kodu güncelleştirir.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. Kodunuzu test edin.

5. Projeyi oluşturun ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneğinde, araç penceresini açın ve ardından arama denetimindeki Down okunu seçin.

     **Eşle'nin durum denetim** kutusu ve **Arama çift satırları yalnızca** filtre görünür.

6. Filtreyi seçin.

     Arama kutusu **satırları içerir:"çift"** ve aşağıdaki sonuçlar görünür:

     2 iyi

     4 İyi

     6 Güle Güle

7. Arama `lines:"even"` kutusundan silin, **Büyük/Küçük Harf Kutusu'nu eşleştir** onay kutusunu seçin ve ardından arama kutusuna girin. `g`

     Aşağıdaki sonuçlar görüntülenir:

     1 git

     2 iyi

     5 güle güle

8. Arama kutusunun sağ tarafındaki X'i seçin.

     Arama temizlendi ve orijinal içerik ler görüntülenir. Ancak, **Match case** onay kutusu hala seçilir.
