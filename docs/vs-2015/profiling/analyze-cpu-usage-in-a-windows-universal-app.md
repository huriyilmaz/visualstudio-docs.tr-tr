---
title: Windows Evrensel uygulamasında CPU kullanımını analiz etme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: def581f547db19a8db4cebc4d63739ff09bb5fab
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531670"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Windows Evrensel uygulamasında CPU kullanımını analiz etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Uygulamanızdaki performans sorunlarını araştırmanız gerektiğinde, baştan başlamak, CPU 'YU nasıl kullandığını öğreniyor. **CPU kullanımı** Aracı, CPU 'nun kod yürütme süresini harcadığı zamanı gösterir. Belirli senaryolara odaklanmak için CPU kullanımı, [XAML UI yanıt verme](https://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) Aracı, [CPU kullanım aracı](../profiling/cpu-usage.md) aracı veya tek bir tanılama oturumunda her iki araçla çalıştırılabilir.  
  
> [!NOTE]
> **CPU kullanım** aracı Windows Phone Silverlight 8,1 uygulamalarıyla birlikte kullanılamaz.  
  
 Bu izlenecek yol, basit bir Windows Evrensel XAML uygulamasının CPU kullanımını toplama ve çözümleme konusunda size kılavuzluk eden bir işlemdir.  
  
## <a name="create-the-cpuusedemo-project"></a><a name="BKMK_Create_the_CpuUseDemo_project"></a>CpuUseDemo projesi oluşturma  
 **Cpuusedemo** , CPU kullanım verilerinin nasıl toplanacağını ve çözümlendiğini göstermek için oluşturulmuş bir uygulamadır. Düğmeler, bir işleve birden çok çağrının en büyük değerini seçen bir yöntemi çağırarak bir sayı üretir. Çağrılan işlev çok fazla sayıda rastgele değer oluşturur ve sonra son olanı döndürür. Veriler bir metin kutusunda görüntülenir.  
  
1. **BlankApp** şablonunu kullanarak **cpuusedemo** adlı yeni bir C# Windows Universal App projesi oluşturun.  
  
     ![CpuUseDemoProject oluşturma](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2. MainPage. xaml ' i [Bu kodla](#BKMK_MainPage_xaml)değiştirin.  
  
3. MainPage.xaml.cs değerini [Bu kodla](#BKMK_MainPage_xaml_cs)değiştirin.  
  
4. Uygulamayı derleyin ve deneyin. Uygulama, CPU kullanımı veri analizinin bazı yaygın durumlarını gösterecek kadar basittir.  
  
## <a name="collect-cpu-usage-data"></a><a name="BKMK_Collect_CPU_usage_data"></a>CPU kullanım verilerini topla  
 ![Simülatör 'de uygulamanın yayın yapısını Çalıştır](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1. Visual Studio 'da dağıtım hedefini **simülatör** olarak ayarlayın ve **Yayınla**çözüm yapılandırmasını yapın.  
  
   - Uygulamayı benzeticide çalıştırmak, uygulama ve Visual Studio IDE arasında kolayca geçiş yapmanızı sağlar.  
  
   - Bu uygulamayı **yayın** modunda çalıştırmak, uygulamanızın gerçek performansının daha iyi bir görünümünü sağlar.  
  
2. **Hata Ayıkla** menüsünde, performans profili **Oluşturucu...** öğesini seçin.  
  
3. Performans ve tanılama hub 'ında **CPU kullanımı** ' nı seçin ve ardından **Başlat**' ı seçin.  
  
    ![CpuUsage tanılama oturumunu başlatın](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4. Uygulama başladığında, **en fazla sayıyı al**' a tıklayın. Çıktı görüntülendikten sonra ikinci bir saniye bekleyip, **en fazla zaman uyumsuz olarak al**' ı seçin. Düğme tıklamasının beklenmesi, tanılama raporundaki düğme tıklama yordamlarını yalıtmak için daha kolay hale gelir.  
  
5. İkinci çıkış satırı göründükten sonra performans ve tanılama hub 'ında **toplamayı durdur** ' u seçin.  
  
   ![CpuUsage veri toplamayı durdur](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   CPU kullanımı aracı verileri analiz eder ve raporu görüntüler.  
  
   ![CpuUsage raporu](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a><a name="BKMK_Analyze_the_CPU_Usage_report"></a>CPU kullanımı raporunu analiz etme  
  
### <a name="cpu-utilization-timeline-graph"></a><a name="BKMK_CPU_utilization_timeline_graph"></a>CPU kullanımı zaman çizelgesi grafiği  
 ![Cpukullanım &#40;% &#41; zaman çizelgesi grafiği](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 CPU kullanım grafiğinde, uygulamanın CPU etkinliği, cihazdaki tüm işlemci çekirdekleri için tüm CPU süresinin yüzdesi olarak gösterilir. Bu raporun verileri bir çift çekirdekli makinede toplandı. İki büyük ani artışlar iki düğme tıklamasının CPU etkinliğini temsil eder. `GetMaxNumberButton_Click`tek bir çekirdek üzerinde zaman uyumlu olarak gerçekleştirerek yöntemin grafik yüksekliğinin hiçbir zaman %50 ' ı aşmadığını anlamlı hale getirir. `GetMaxNumberAsycButton_Click`Her iki çekirdekte zaman uyumsuz olarak çalışır; bu nedenle, her iki çekirdekte CPU kaynaklarının tümünün kullanılmasıyla hemen sonra ani bir daha yakın olduğunu araştırır.  
  
#### <a name="select-timeline-segments-to-view-details"></a><a name="BKMK_Select_timeline_segments_to_view_details"></a>Ayrıntıları görüntülemek için zaman çizelgesi segmentlerini seçin  
 GetMaxNumberButton_Click verilerine odaklanmak için **Tanılama oturumu** zaman çizelgesindeki seçim çubuklarını kullanın:  
  
 ![GetMaxNumberButton&#95;seçili öğesine tıklayın](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 **Tanılama oturumu** zaman çizelgesi artık seçili segmentte harcanan süreyi (Bu raporda 2 saniyeden uzun bir süre) görüntüler ve çağrı ağacını seçimde çalıştırılan yöntemlere filtreler.  
  
 Şimdi segmenti seçin `GetMaxNumberAsyncButton_Click` .  
  
 ![GetMaxNumberAsyncButton&#95;rapor seçimi ' ne tıklayın](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Bu yöntem yaklaşık bir saniyeden daha hızlı tamamlanır `GetMaxNumberButton_Click` , ancak çağrı ağacı girişlerinin anlamı daha az belirgin olur.  
  
### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a>CPU kullanımı çağrı ağacı  
 Çağrı ağacı bilgilerini anlamak için, segmenti yeniden seçin `GetMaxNumberButton_Click` ve çağrı ağacı ayrıntılarına bakın.  
  
#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a>Çağrı ağacı yapısı  
 ![GetMaxNumberButton&#95;çağrı ağacı ' na tıklayın](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|Görüntü|Açıklama|  
|-|-|  
|![1. Adım](../profiling/media/procguid-1.png "ProcGuid_1")|CPU kullanım çağrısı ağaçlarında en üst düzey düğüm bir sözde düğümdür|  
|![2. Adım](../profiling/media/procguid-2.png "ProcGuid_2")|Çoğu uygulamalarda, **dış kodu göster** seçeneği devre dışı bırakıldığında, ikinci düzey düğüm, uygulamayı başlatan ve durduran sistem ve çerçeve kodunu içeren bir **[Dış kod]** düğümüdür, Kullanıcı arabirimini çizer, iş parçacığı zamanlamasını denetler ve uygulamaya diğer alt düzey hizmetler sağlar.|  
|![3. Adım](../profiling/media/procguid-3.png "ProcGuid_3")|İkinci düzey düğümün alt öğeleri, ikinci düzey sistem ve Framework kodu tarafından çağrılan veya oluşturulan kullanıcı kodu yöntemleri ve zaman uyumsuz yordamlardır.|  
|![4. adım](../profiling/media/procguid-4.png "ProcGuid_4")|Bir metodun alt düğümleri yalnızca üst yöntemin çağrıları için veri içerir. **Dış kodu göster** devre dışı bırakıldığında, uygulama yöntemleri bir **[Dış kod]** düğümü de içerebilir.|  
  
#### <a name="external-code"></a><a name="BKMK_External_Code"></a>Dış kod  
 Dış kod, System ve Framework bileşenlerinde yazdığınız kod tarafından yürütülen işlevlerden oluşur. Dış kod, uygulamayı başlatıp durduran, Kullanıcı arabirimini çizdiğiniz, iş parçacığı denetleyen ve diğer alt düzey Hizmetleri uygulamaya sağlayan işlevleri içerir. Çoğu durumda, harici kod ile ilgilenmezsiniz ve bu nedenle CPU kullanımı çağrı ağacı bir Kullanıcı yönteminin dış işlevlerini tek bir **[harici kod]** düğümüne toplar.  
  
 Dış kodun çağrı yollarını görüntülemek istediğinizde, **filtre görünümü** listesinden **dış kodu göster** ' i seçin ve ardından **Uygula**' yı seçin.  
  
 ![Filtre görünümü ' ne ve ardından dış kodu göster ' i seçin](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Çok sayıda dış kod çağrı zincirinin derin iç içe geçmiş olduğunu unutmayın. böylece, Işlev adı sütununun genişliği, bilgisayar izlemelerinin en büyük bir bütün boyutunu aşabilirler. Bu durumda, işlev adları **[...]** olarak gösterilir:  
  
 ![Çağrı ağacındaki iç içe dış kod](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Aradığınız düğümü bulmak için arama kutusunu kullanın, ardından verileri görünüme getirmek için yatay kaydırma çubuğunu kullanın:  
  
 ![İç içe geçmiş dış kodu arayın](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="call-tree-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a>Ağaç veri sütunlarını çağır  
  
|Özellik|Açıklama|  
|-|-|  
|**Toplam CPU (%)**|![Toplam% veri denklemi](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> İşleve yapılan çağrılar ve işlev tarafından çağrılan işlevler tarafından kullanılan seçili zaman aralığındaki uygulamanın CPU etkinliğinin yüzdesi. Bu, bir zaman aralığındaki uygulamanın toplam etkinliğini toplam kullanılabilir CPU kapasitesine karşılaştıran **CPU kullanımı** zaman çizelgesi grafiğinden farklı olduğunu unutmayın.|  
|**Self CPU (%)**|![Kendi kendine denklemi](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> İşlev tarafından çağrılan işlevlerin etkinliği hariç olmak üzere, işlev çağrıları tarafından kullanılan seçili zaman aralığındaki uygulamanın CPU etkinliğinin yüzdesi.|  
|**Toplam CPU (MS)**|Seçili zaman aralığındaki işleve yapılan çağrılar ve işlev tarafından çağrılan işlevler için harcanan milisaniye sayısı.|  
|**Self CPU (MS)**|Seçili zaman aralığındaki işleve yapılan çağrılar ve işlev tarafından çağrılan işlevler için harcanan milisaniye sayısı.|  
|**Modül**|İşlevi içeren modülün adı veya [Dış kod] düğümündeki işlevleri içeren modül sayısı.|  
  
### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a>CPU kullanım çağrısı ağacındaki zaman uyumsuz işlevler  
 Derleyici zaman uyumsuz bir yöntemle karşılaştığında, yöntemin yürütmesini denetlemek için gizli bir sınıf oluşturur. Kavramsal olarak, sınıfı, özgün yöntemin işlemlerini zaman uyumsuz olarak çağıran derleyici tarafından oluşturulan işlevlerin bir listesini ve bunları doğru bir şekilde gereken geri çağırmaları, zamanlayıcıyı ve yineleyicilerini çağıran bir durum makinedir. Özgün yöntem bir üst yöntem tarafından çağrıldığında, çalışma zamanı, yöntemi üst öğenin yürütme bağlamından kaldırır ve gizli sınıfın yöntemlerini, uygulamanın yürütülmesini denetleyen sistem ve çerçeve kodu bağlamında çalıştırır. Zaman uyumsuz yöntemler çoğunlukla, her zaman bir veya daha fazla farklı iş parçacığında yürütülürler. Bu kod, ağacın üst düğümünün hemen altındaki **[Dış kod]** düğümünün alt ÖĞELERI olarak CPU kullanım çağrısı ağacında gösterilir.  
  
 Bunu örneğimizde görmek için `GetMaxNumberAsyncButton_Click` zaman çizelgesinde segmenti yeniden seçin.  
  
 ![GetMaxNumberAsyncButton&#95;rapor seçimi ' ne tıklayın](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 **[External Code]** altındaki ilk iki düğüm, durum makinesi sınıfının derleyici tarafından oluşturulan yöntemleridir. Üçüncü, özgün metoda yapılan çağrıdır. Oluşturulan yöntemlerin genişletilmesi, neler olduğunu gösterir.  
  
 ![Genişletilmiş GetMaxNumberAsyncButton&#95;çağrı ağacı ' na tıklayın](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click`çok az; görev değerlerinin bir listesini yönetir, sonuçların maksimum sayısını hesaplar ve çıktıyı görüntüler.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext`çağrıyı kaydırmak için gereken 48 görevlerini zamanlamak ve başlatmak için gereken etkinliği gösterir `GetNumberAsync` .  
  
- `MainPage::<GetNumberAsync>b__b`çağıran görevlerin etkinliğini gösterir `GetNumber` .  
  
## <a name="next-steps"></a><a name="BKMK_Next_steps"></a>Sonraki adımlar  
 CpuUseDemo uygulaması en parlak uygulamalar değildir, ancak bunu kullanarak yardımcı programını, performans ve tanılama hub 'ındaki zaman uyumsuz işlem ve diğer araçlarla denemeler yapmak için kullanabilirsiniz.  
  
- `MainPage::<GetNumberAsync>b__b`[Dış kod] Içinde GetNumber metodunu yürüttüğünden daha fazla zaman harcadığını unutmayın. Bu sürenin çoğu zaman uyumsuz işlemlerin ek yüküdür. Görev sayısını artırmayı deneyin ( `NUM_TASKS` MainPage.xaml.cs 'in sabitinde ayarlanır) ve içindeki yineleme sayısını azaltın `GetNumber` ( `MIN_ITERATIONS` değeri değiştirin). Koleksiyon senaryosunu çalıştırın ve CPU etkinliğini `MainPage::<GetNumberAsync>b__b` ORIJINAL CPU kullanımı tanılama oturumunda olacak şekilde karşılaştırın. Görevleri azaltmayı ve yinelemeleri artırmayı deneyin.  
  
- Kullanıcılar genellikle uygulamanızın gerçek performansını dikkate vermez; Bu uygulamalar, algılanan performans ve uygulamanın yanıt verme bilgilerini dikkate alırlar. XAML Kullanıcı Arabirimi yanıt verme aracı, Kullanıcı arabirimi iş parçacığında, yanıt verdiğini algılanan etkinliğin ayrıntılarını gösterir.  
  
     Tanılama ve performans hub 'ında yeni bir oturum oluşturun ve hem XAML UI yanıt verme aracını hem de CPU kullanımı aracını ekleyin. Toplama senaryosunu çalıştırın. Bu konuyu en fazla okumadıysanız, rapor büyük olasılıkla henüz iletişime etmemiş olduğunuz herhangi bir şeyi söylemez, ancak iki yöntem için **UI Iş parçacığı kullanım** zaman çizelgesi grafiğindeki farklılıklar göz harcar. Karmaşık, gerçek dünyada uygulamalar, araçların birleşimi çok faydalı olabilir.  
  
## <a name="mainpagexaml"></a><a name="BKMK_MainPage_xaml"></a>MainPage. xaml  
  
```csharp  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
## <a name="mainpagexamlcs"></a><a name="BKMK_MainPage_xaml_cs"></a>MainPage.xaml.cs  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```
