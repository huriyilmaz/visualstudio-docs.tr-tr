---
title: Araç penceresine arama ekleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b648b0202e00ea0fa3bc659b90f2f9a7d709768f
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903404"
---
# <a name="add-search-to-a-tool-window"></a>Araç penceresine arama ekleme
Uzantınızın bir araç penceresini oluştururken veya güncelleştirdiğinizde, Visual Studio 'da başka bir yerde görünen aynı arama işlevini ekleyebilirsiniz. Bu işlevsellik aşağıdaki özellikleri içerir:

- Araç çubuğunun özel bir alanında her zaman bulunan bir arama kutusu.

- Arama kutusunun kendisi üzerinde yer alan bir ilerleme göstergesi.

- Her karakteri (anında arama) girdikten hemen sonra veya anahtarı **gir** (isteğe bağlı ara) seçeneğini belirledikten sonra sonuçları gösterme özelliği.

- En son aradığınız koşulları gösteren bir liste.

- Belirli alanlara veya arama hedeflerinin yönlerini göre aramaları filtreleme özelliği.

Bu izlenecek yolu izleyerek aşağıdaki görevleri nasıl gerçekleştireceğinizi öğreneceksiniz:

1. VSPackage projesi oluşturun.

2. Salt okunurdur metin kutusuna sahip bir UserControl içeren bir araç penceresi oluşturur.

3. Araç penceresine bir arama kutusu ekleyin.

4. Arama uygulamasını ekleyin.

5. Anlık aramayı etkinleştirin ve ilerleme çubuğunun görüntülenmesini sağlayın.

6. **Match Case** seçeneği ekleyin.

7. Yalnızca bir **arama çizgisi** filtresi ekleyin.

## <a name="to-create-a-vsix-project"></a>VSıX projesi oluşturmak için

1. `TestToolWindowSearch` **Testsearch**adlı bir araç penceresi Ile adlı bir VSIX projesi oluşturun. Bu işlemi gerçekleştirmek için yardıma ihtiyacınız varsa, bkz. [bir araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Bir araç penceresi oluşturmak için

1. `TestToolWindowSearch`Projede *Testsearchcontrol. xaml* dosyasını açın.

2. Mevcut bloğunu, `<StackPanel>` araç penceresine salt bir okuma ekleyen aşağıdaki blokla değiştirin <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.UserControl> .

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. *TestSearchControl.xaml.cs* dosyasında, aşağıdaki using yönergesini ekleyin:

    ```csharp
    using System.Text;
    ```

4. Yöntemi kaldırın `button1_Click()` .

     **Testsearchcontrol** sınıfında aşağıdaki kodu ekleyin.

     Bu kod <xref:System.Windows.Controls.TextBox> **Searchresultstextbox** adlı ortak bir özellik ve **searchcontent**adlı bir genel dize özelliği ekler. Oluşturucuda, SearchResultsTextBox metin kutusu olarak ayarlanır ve SearchContent, yeni bir dize kümesi olarak başlatılır. Metin kutusunun içeriği, dizeler kümesine de başlatılır.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio 'nun deneysel örneği görüntülenir.

6. Menü çubuğunda **View**  >  **diğer Windows**  >  **testsearch**'ü görüntüle ' yi seçin.

     Araç penceresi görünür, ancak arama denetimi henüz görünmez.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Araç penceresine bir arama kutusu eklemek için

1. *TestSearch.cs* dosyasında, sınıfına aşağıdaki kodu ekleyin `TestSearch` . Kod, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Get erişimcisinin döndürdüğü şekilde özelliği geçersiz kılar `true` .

     Aramayı etkinleştirmek için, özelliğini geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> . <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>Sınıfı uygular <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> ve aramayı etkinleştiremeyen varsayılan bir uygulama sağlar.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

3. Visual Studio 'nun deneysel örneğinde **Testsearch**' u açın.

     Araç penceresinin üst kısmında, arama filigranı ve büyüteç simgesiyle **bir arama denetimi** görünür. Ancak arama işlemi uygulanmadığı için arama henüz çalışmaz.

## <a name="to-add-the-search-implementation"></a>Arama uygulamasını eklemek için
 Bir üzerinde aramayı etkinleştirdiğinizde <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> , önceki yordamda olduğu gibi, araç penceresi bir arama ana bilgisayarı oluşturur. Bu konak, bir arka plan iş parçacığında her zaman gerçekleşen arama işlemlerini ayarlar ve yönetir. Sınıfı, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> arama konağının oluşturulmasını ve aramanın kurulumunu yönettiğinden, yalnızca bir arama görevi oluşturmanız ve arama yöntemi sağlamanız gerekir. Arama işlemi bir arka plan iş parçacığında gerçekleşir ve Kullanıcı arabirimi iş parçacığında araç penceresi denetimine yapılan çağrılar oluşur. Bu nedenle, denetimle ilgili olarak yaptığınız tüm çağrıları yönetmek için [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) metodunu kullanmanız gerekir.

1. *TestSearch.cs* dosyasında aşağıdaki `using` yönergeleri ekleyin:

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

2. Sınıfında, aşağıdaki `TestSearch` eylemleri gerçekleştiren aşağıdaki kodu ekleyin:

    - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>Arama görevi oluşturma yöntemini geçersiz kılar.

    - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>Metin kutusunun durumunu geri yüklemek için yöntemini geçersiz kılar. Bu yöntem, bir Kullanıcı bir arama görevini iptal ettiğinde ve Kullanıcı seçenekleri ya da filtreleri ayarlarsa ya da ayarlarsa çağrılır. Her ikisi de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> UI iş parçacığında çağırılır. Bu nedenle, [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) yöntemi aracılığıyla metin kutusuna erişmeniz gerekmez.

    - `TestSearchTask` <xref:Microsoft.VisualStudio.Shell.VsSearchTask> Varsayılan bir uygulamasını sağlayan öğesinden devralan adlı bir sınıf oluşturur <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> .

         İçinde `TestSearchTask` , Oluşturucu araç penceresine başvuran bir özel alan ayarlar. Arama yöntemini sağlamak için ve yöntemlerini geçersiz kılarsınız <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> . <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>Yöntemi, arama işlemini uyguladığınız yerdir. Bu işlem aramanın tamamlanmasının, arama sonuçlarının metin kutusunda görüntülenmesine ve aramanın tamamlandığını raporlamak için bu yöntemin temel sınıf uygulamasını çağırmaya dahildir.

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

    1. Projeyi yeniden derleyin ve hata ayıklamayı başlatın.

    2. Visual Studio 'nun deneysel örneğinde, araç penceresini yeniden açın, arama penceresinde bir arama metni girin ve **ENTER**' a tıklayın.

         Doğru sonuçlar görünmelidir.

## <a name="to-customize-the-search-behavior"></a>Arama davranışını özelleştirmek için
 Arama ayarlarını değiştirerek, arama denetiminin görünme ve aramanın nasıl gerçekleştirildiği gibi çeşitli değişiklikler yapabilirsiniz. Örneğin, filigranı (arama kutusunda görünen varsayılan metin), arama denetiminin en düşük ve en yüksek genişliğini ve ilerleme çubuğunun gösterilip gösterilmeyeceğini değiştirebilirsiniz. Ayrıca, arama sonuçlarının görüntüleneceği noktayı (isteğe bağlı veya anında arama) ve en son aradığınız koşulların bir listesini gösterip göstermeyeceğinizi de değiştirebilirsiniz. Tüm ayarların listesini <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> sınıfında bulabilirsiniz.

1. * TestSearch.cs * dosyasında, sınıfına aşağıdaki kodu ekleyin `TestSearch` . Bu kod, isteğe bağlı arama yerine anında arama sağlar (kullanıcının **ENTER**'a tıklamasından başka bir deyişle). Kod, `ProvideSearchSettings` `TestSearch` sınıfının varsayılan ayarlarını değiştirmek için gerekli olan yöntemini geçersiz kılar.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Çözümü yeniden oluşturarak ve hata ayıklayıcıyı yeniden başlatarak yeni ayarı test edin.

     Arama kutusuna her seferinde bir karakter girdiğinizde arama sonuçları görüntülenir.

3. Yönteminde, `ProvideSearchSettings` ilerleme çubuğunun görüntülenmesini sağlayan aşağıdaki satırı ekleyin.

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

     İlerleme çubuğunun görünmesi için ilerleme durumu bildirilmelidir. İlerlemeyi raporlamak için, sınıfının yönteminde aşağıdaki kodun açıklamasını kaldırın `OnStartSearch` `TestSearchTask` :

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. İlerleme çubuğunun görünür olduğunu yeterince yavaş işlemek için, sınıfının yönteminde aşağıdaki satırın açıklamasını kaldırın `OnStartSearch` `TestSearchTask` :

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Çözümü yeniden oluşturarak ve hata ayıklamaya başlayarak yeni ayarları test edin.

     Her arama yaptığınızda arama penceresinde (arama metin kutusunun altında bir mavi çizgi olarak) ilerleme çubuğu görüntülenir.

## <a name="to-enable-users-to-refine-their-searches"></a>Kullanıcıların aramalarını iyileştirmesini sağlamak için
 Kullanıcıların aramalarını, **büyük/küçük harf eşleştirme** veya **sözcüğün tamamını eşleştirme**gibi seçenekler aracılığıyla iyileştirmelerine izin verebilirsiniz. Seçenekler, düğme olarak görünen onay kutuları veya komutlar olarak görünen Boole olabilir. Bu izlenecek yol için bir Boole seçeneği oluşturacaksınız.

1. *TestSearch.cs* dosyasında, sınıfına aşağıdaki kodu ekleyin `TestSearch` . Kod, `SearchOptionsEnum` Arama uygulamasının belirli bir seçeneğin açık veya kapalı olduğunu algılamasına izin veren yöntemini geçersiz kılar. İçindeki kod, `SearchOptionsEnum` bir Numaralandırıcı ile büyük/küçük harf eşleştirmek için bir seçenek ekler <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> . Büyük/küçük harf eşleştirme seçeneği de özellik olarak kullanılabilir hale getirilir `MatchCaseOption` .

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

2. `TestSearchTask`Sınıfında, yönteminde aşağıdaki satırın açıklamasını kaldırın `OnStartSearch` :

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Bu seçeneği test edin:

    1. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

    2. Araç penceresinde, metin kutusunun sağ tarafındaki aşağı oku seçin.

         **Büyük/küçük harf eşleştir** onay kutusu görüntülenir.

    3. **Büyük/küçük harf eşleştir** onay kutusunu seçin ve ardından bazı aramalar gerçekleştirin.

## <a name="to-add-a-search-filter"></a>Arama filtresi eklemek için
 Kullanıcıların arama hedefleri kümesini iyileştirmesine izin veren arama filtreleri ekleyebilirsiniz. Örneğin, dosya Gezgini 'ndeki dosyaları en son değiştirildiği tarih ve bunların dosya adı uzantılarına göre filtreleyebilirsiniz. Bu kılavuzda, yalnızca çift satırlar için bir filtre ekleyeceksiniz. Kullanıcı bu filtreyi seçtiğinde, arama ana bilgisayarı belirttiğiniz dizeleri arama sorgusuna ekler. Daha sonra bu dizeleri arama yönteminizin içinde tanımlayabilir ve arama hedeflerini buna göre filtreleyebilirsiniz.

1. *TestSearch.cs* dosyasında, sınıfına aşağıdaki kodu ekleyin `TestSearch` . Kod, `SearchFiltersEnum` <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> arama sonuçlarının yalnızca çift satır görünecek şekilde filtreleneceğini belirten bir ekleyerek uygular.

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

     Arama denetimi artık arama filtresini görüntülüyor `Search even lines only` . Kullanıcı filtreyi seçtiğinde, dize `lines:"even"` arama kutusunda görünür. Diğer arama ölçütleri de filtreyle aynı anda görünebilir. Arama dizeleri filtreden önce, filtreden sonra veya her ikisiyle de görünebilir.

2. *TestSearch.cs* dosyasında, sınıfındaki sınıfına aşağıdaki yöntemleri ekleyin `TestSearchTask` `TestSearch` . Bu yöntemler, bir `OnStartSearch` sonraki adımda değiştireceğiniz yöntemini destekler.

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

3. Sınıfında, `TestSearchTask` `OnStartSearch` aşağıdaki kodla yöntemi güncelleştirin. Bu değişiklik, filtreyi desteklemek için kodu güncelleştirir.

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

5. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio 'nun deneysel örneğinde araç penceresini açın ve arama denetimindeki aşağı oku seçin.

     **Büyük/küçük harf eşleştir** onay kutusu ve **yalnızca arama satırları** filtresi görüntülenir.

6. Filtreyi seçin.

     Arama kutusu şu **satırları içerir: "çift"** ve aşağıdaki sonuçlar görünür:

     2 iyi

     4 iyi

     6 güle

7. `lines:"even"`Arama kutusundan Sil, **büyük/küçük harf eşleştir** onay kutusunu seçin ve `g` Arama kutusuna girin.

     Aşağıdaki sonuçlar görüntülenir:

     1 git

     2 iyi

     5 güle

8. Arama kutusunun sağ tarafındaki X seçeneğini belirleyin.

     Arama temizlenir ve özgün içerik görüntülenir. Ancak, **büyük/küçük harf eşleştir** onay kutusu hala seçilidir.
