---
title: Araç Penceresine Arama Ekleme | Microsoft Docs
description: Arama kutusu, filtreleme ve ilerleme göstergesi gibi arama işlevlerini bir araç penceresine ekleme hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e3c581f1f2c5fbd1c80860241ef4d33608489143
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725332"
---
# <a name="add-search-to-a-tool-window"></a>Araç penceresine arama ekleme
Uzantıda bir araç penceresi güncelleştirmeyi veya güncelleştirmeyi tamamlarsanız, uzantının başka bir yerinde görünen arama Visual Studio. Bu işlevsellik aşağıdaki özellikleri içerir:

- Her zaman araç çubuğunun özel bir alanında bulunan bir arama kutusu.

- Arama kutusunun üzerinde yer alan ilerleme göstergesi.

- Her karakteri girer girmez (anlık arama) veya yalnızca **Enter** tuşuna (isteğe bağlı arama) girdikten sonra sonuçları gösterebilme özelliği.

- Son zamanlarda arama yapılan terimleri gösteren bir liste.

- Arama hedeflerinin belirli alanlarına veya yönlerine göre aramaları filtreleme özelliği.

Bu izlenecek yolu kullanarak aşağıdaki görevleri nasıl gerçekleştirebilirsiniz?

1. VSPackage projesi oluşturun.

2. Salt okunur TextBox ile UserControl içeren bir araç penceresi oluşturun.

3. Araç penceresine bir arama kutusu ekleyin.

4. Arama uygulamasını ekleyin.

5. Bir ilerleme çubuğunun anlık arama ve görüntülemesini etkinleştirin.

6. Bir **Büyük/küçük harf eşleşmesi seçeneği** ekleyin.

7. Yalnızca arama **satırları filtresi** ekleyin.

## <a name="to-create-a-vsix-project"></a>VSIX projesi oluşturmak için

1. TestSearch adlı bir araç penceresiyle adlı bir VSIX `TestToolWindowSearch` **projesi oluşturun.** Bunu yaparken yardıma ihtiyacınız varsa [bkz. Araç penceresiyle uzantı oluşturma.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="to-create-a-tool-window"></a>Araç penceresi oluşturmak için

1. Projede `TestToolWindowSearch` *TestSearchControl.xaml dosyasını* açın.

2. Mevcut bloğu `<StackPanel>` aşağıdaki blokla değiştirin. Bu blok, araç <xref:System.Windows.Controls.TextBox> penceresindeki <xref:System.Windows.Controls.UserControl> bloğuna salt okunur ekler.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. *TestSearchControl.xaml.cs* dosyasına aşağıdaki using yönergesi ekleyin:

    ```csharp
    using System.Text;
    ```

4. yöntemini `button1_Click()` kaldırın.

     **TestSearchControl sınıfında** aşağıdaki kodu ekleyin.

     Bu kod, <xref:System.Windows.Controls.TextBox> **SearchResultsTextBox adlı** bir ortak özellik ve **SearchContent** adlı bir ortak dize özelliği ekler. Oluşturucuda SearchResultsTextBox metin kutusuna ayarlanır ve SearchContent yeni satırla ayrılmış dize kümesine başlatılır. Metin kutusunun içeriği de dize kümesine başlatılır.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/toolwindowsearch/cs/mycontrol.xaml.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/toolwindowsearch/vb/mycontrol.xaml.vb" id="Snippet1":::

5. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek Visual Studio görünür.

6. Menü çubuğunda Diğer Öğeleri **Görüntüle'yi**  >  **seçin Windows**  >  **TestSearch.**

     Araç penceresi görünür ancak arama denetimi henüz görünmez.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Araç penceresine arama kutusu eklemek için

1. *TestSearch.cs dosyasında* aşağıdaki kodu sınıfına `TestSearch` ekleyin. Kod, get <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> erişimcinin döndüren özelliğini geçersiz `true` kılar.

     Arama özelliğini etkinleştirmek için özelliğini geçersiz <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> kılmalı. sınıfı, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> arama <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> etkinleştirmez varsayılan bir uygulama sağlar ve sağlar.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür.

3. Deneysel Visual Studio **TestSearch'i açın.**

     Araç penceresinin en üstünde Arama filigranı  ve büyüteç simgesi bulunan bir arama denetimi görüntülenir. Ancak arama işlemi uygulanmamış olduğundan arama henüz çalışmıyor.

## <a name="to-add-the-search-implementation"></a>Arama uygulamasını eklemek için
 Önceki yordamda olduğu <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> gibi, bir üzerinde arama etkinleştir ilkeniz olduğunda, araç penceresi bir arama ana bilgisayarı oluşturur. Bu konak, her zaman arka plan iş parçacığında oluşan arama işlemlerini ayarlar ve yönetir. sınıfı arama ana bilgisayarının oluşturulmasını ve aramanın kurulmasını yönetecek olduğundan, yalnızca bir arama görevi oluşturmanız ve arama <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> yöntemini sağlamanız gerekir. Arama işlemi bir arka plan iş parçacığında gerçekleşir ve kullanıcı arabirimi iş parçacığında araç penceresi denetimine yapılan çağrılar gerçekleşir. Bu nedenle, denetimle ilgilenmek üzere yapılan çağrıları yönetmek için [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) yöntemini kullanabilirsiniz.

1. *TestSearch.cs dosyasına* aşağıdaki yönergeleri `using` ekleyin:

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

2. sınıfında, `TestSearch` aşağıdaki eylemleri gerçekleştiren aşağıdaki kodu ekleyin:

    - Arama görevi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> oluşturmak için yöntemini geçersiz kılar.

    - Metin kutusunun <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> durumunu geri yüklemek için yöntemini geçersiz kılar. Bu yöntem, kullanıcı bir arama görevini iptal edip bir kullanıcı seçenekleri veya filtreleri ayarsıyor ya da sildi. Hem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> hem de kullanıcı arabirimi iş <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> parçacığında çağrılır. Bu [nedenle, ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) yöntemiyle metin kutusuna erişmeniz gerek değildir.

    - 'den devralan adlı `TestSearchTask` bir sınıf oluşturur ve bu da varsayılan uygulamasını <xref:Microsoft.VisualStudio.Shell.VsSearchTask> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> sağlar.

         içinde `TestSearchTask` oluşturucu, araç penceresine başvurulan özel bir alan ayarlar. Arama yöntemini sağlamak için ve yöntemlerini <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> geçersiz <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> kılar. yöntemi, <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> arama işlemini uygulayan yöntemdir. Bu işlem aramayı gerçekleştirmeyi, arama sonuçlarını metin kutusunda görüntülemeyi ve aramanın tamam olduğunu rapor etmek için bu yöntemin temel sınıf uygulamasını çağırmayı içerir.

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

    1. Projeyi yeniden oluşturma ve hata ayıklamayı başlatma.

    2. Deneysel Visual Studio araç penceresini yeniden açın, arama penceresine biraz arama metni girin ve **ENTER'a tıklayın.**

         Doğru sonuçlar görün gerekir.

## <a name="to-customize-the-search-behavior"></a>Arama davranışını özelleştirmek için
 Arama ayarlarını değiştirerek, arama denetimi nasıl göründüğü ve aramanın nasıl gerçekleştir olduğu hakkında çeşitli değişiklikler yapabilirsiniz. Örneğin, filigranı (arama kutusunda görünen varsayılan metin), arama denetimi için minimum ve maksimum genişliği ve ilerleme çubuğunun gösterip göstermeyeceklerini değiştirebilirsiniz. Ayrıca arama sonuçlarının görünmeye başlama noktasını (isteğe bağlı veya anlık arama) ve son arama yapılan terimlerin listesinin gösterip göstermeyeceklerini de değiştirebilirsiniz. Ayarların tam listesini sınıfında <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> bulabilirsiniz.

1. * TestSearch.cs* dosyasında sınıfına aşağıdaki kodu `TestSearch` ekleyin. Bu kod, isteğe bağlı arama yerine anında arama sağlar (kullanıcının **ENTER'a** tıklaması gerek yoktur). Kod, `ProvideSearchSettings` sınıfındaki yöntemini geçersiz `TestSearch` kılar ve varsayılan ayarları değiştirmek için gereklidir.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Çözümü yeniden yapılandırarak ve hata ayıklayıcıyı yeniden başlatarak yeni ayarı test etmek.

     Arama kutusuna her karakter girmenizde arama sonuçları görüntülenir.

3. `ProvideSearchSettings`yönteminde, ilerleme çubuğunun görüntülemesini sağlayan aşağıdaki satırı ekleyin.

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

     İlerleme çubuğunun görünmesi için ilerleme durumunun bildiriliyor olması gerekir. İlerlemeyi rapor etmek için sınıfının yönteminde aşağıdaki `OnStartSearch` kodun açıklamalarını `TestSearchTask` yapın:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. İlerleme çubuğunun görünür olduğu kadar işlemeyi yeterince yavaşlatmak için sınıfının yönteminde aşağıdaki `OnStartSearch` satırı `TestSearchTask` açıklamayın:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Çözümü yeniden oluşturarak ve hata ayıklamaya başlayarak yeni ayarları test edin.

     İlerleme çubuğu, her arama gerçekleştir her eylemde arama penceresinde (arama metin kutusunun altında mavi bir çizgi olarak) görünür.

## <a name="to-enable-users-to-refine-their-searches"></a>Kullanıcıların aramalarını iyileştirmesini sağlamak için
 Kullanıcıların Aramalarını Büyük/Büyük/Büyük Harf eşleşmesi veya Sözcüğün tamamını **eşle** gibi **seçeneklerle iyileştirmesine izin veebilirsiniz.** Seçenekler, onay kutuları olarak görünen boole veya düğme olarak görünen komutlar olabilir. Bu kılavuzda bir boole seçeneği oluşturabilirsiniz.

1. *TestSearch.cs dosyasında* aşağıdaki kodu sınıfına `TestSearch` ekleyin. Kod, arama uygulamasının belirli bir seçeneğin kapalı mı olduğunu `SearchOptionsEnum` algılaması için yöntemini geçersiz kılar. 'daki `SearchOptionsEnum` kod, büyük/büyük harfle bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> numaralayıcıyı eşleyen bir seçenek ekler. Büyük/büyük/büyük harf eşleşme seçeneği özelliği olarak da `MatchCaseOption` kullanılabilir.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
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

2. sınıfında, `TestSearchTask` yönteminde aşağıdaki satırın açıklamalarını `OnStartSearch` uncomment:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Seçeneğini test etmek için:

    1. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür.

    2. Araç penceresinde, metin kutusunun sağ tarafındaki Aşağı okunu seçin.

         Eşleşme **durumu onay** kutusu görüntülenir.

    3. Durumu **eşle onay** kutusunu seçin ve ardından bazı aramalar gerçekleştirin.

## <a name="to-add-a-search-filter"></a>Arama filtresi eklemek için
 Kullanıcıların arama hedefleri dizisini iyileştirmesine olanak sağlayan arama filtreleri ekleyebilirsiniz. Örneğin, dosyaları en son Dosya Gezgini tarihlere ve dosya adı uzantılarına göre filtre yapabilirsiniz. Bu kılavuzda yalnızca tek satırlar için bir filtre eklenecektir. Kullanıcı bu filtreyi seçtiğinde, arama ana bilgisayarı belirttiğiniz dizeleri arama sorgusuna ekler. Daha sonra bu dizeleri arama yönteminizin içinde tanımlayabilir ve arama hedeflerini buna göre filtreleyebilirsiniz.

1. *Testsearch. cs* dosyasında sınıfına aşağıdaki kodu ekleyin `TestSearch` . Kod, `SearchFiltersEnum` <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> arama sonuçlarının yalnızca çift satır görünecek şekilde filtreleneceğini belirten bir ekleyerek uygular.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Arama denetimi artık arama filtresini görüntülüyor `Search even lines only` . Kullanıcı filtreyi seçtiğinde, dize `lines:"even"` arama kutusunda görünür. Diğer arama ölçütleri de filtreyle aynı anda görünebilir. Arama dizeleri filtreden önce, filtreden sonra veya her ikisiyle de görünebilir.

2. *Testsearch. cs* dosyasında, sınıfındaki sınıfına aşağıdaki yöntemleri ekleyin `TestSearchTask` `TestSearch` . Bu yöntemler, bir `OnStartSearch` sonraki adımda değiştireceğiniz yöntemini destekler.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

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
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
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

5. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio deneysel örneğinde araç penceresini açın ve arama denetimindeki aşağı oku seçin.

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
