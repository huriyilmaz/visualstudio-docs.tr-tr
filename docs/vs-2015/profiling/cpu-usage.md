---
title: CPU kullanımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7732a5757281e83c501a8258dd1d44b4f329a87a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548063"
---
# <a name="cpu-usage"></a>CPU Kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızdaki performans sorunlarını araştırmanız gerektiğinde, baştan başlamak, CPU 'YU nasıl kullandığını öğreniyor. **CPU kullanımı** Aracı, cpu 'nun Visual C++, Visual C#/Visual Basic ve JavaScript kodu yürütme zamanının nerede harcamaya yönelik olduğunu gösterir.  
  
 Visual Studio 2015 güncelleştirme 1 ' den başlayarak, hata ayıklayıcıdan çıkmadan CPU kullanımının işlev başına dökümünü görebilirsiniz. Hata ayıklama sırasında CPU profili oluşturmayı ve devre dışı bırakabilirsiniz ve örneğin bir kesme noktasında yürütme durdurulduğunda sonuçları görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 2015 ' de hata ayıklayıcıda CPU 'Yu profil](https://devblogs.microsoft.com/devops/profile-your-cpu-in-the-debugger-in-visual-studio-2015/).  
  
 Bir Windows Mağazası uygulamasının performansını analiz eden bir anlatım için bkz. [Mağaza UYGULAMALARıNDA CPU kullanımını çözümleme](https://msdn.microsoft.com/library/windows/apps/dn641982.aspx).  
  
 Performans ve tanılama hub 'ı, tanılama oturumunuzu çalıştırmak ve yönetmek için size çok sayıda seçenek sunar. Örneğin, **CPU kullanımı** aracını yerel veya uzak makinelerde veya bir simülatör ya da öykünücü içinde çalıştırabilirsiniz. Visual Studio 'da bir açık projenin performansını analiz edebilir, çalışan bir uygulamaya iliştirilir veya Windows Mağazası 'ndan yüklenen bir uygulamayı başlatabilirsiniz. Daha fazla bilgi için bkz. [profil oluşturma araçlarını hata ayıklama olmadan çalıştırma](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
## <a name="collect-cpu-usage-data"></a><a name="BKMK_Collect_CPU_usage_data"></a> CPU kullanım verilerini topla  
  
1. Visual Studio 'da çözüm yapılandırmasını **serbest bırakma** olarak ayarlayın ve dağıtım hedefini seçin.  
  
    ![Yayın ve yerel makine seçin](../profiling/media/cpuuse-selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
   - Uygulamayı **yayın** modunda çalıştırmak, uygulamanızın gerçek performansının daha iyi bir görünümünü sağlar.  
  
   - Uygulamayı yerel makinede çalıştırmak, yüklenen uygulamanın yürütülmesini en iyi şekilde çoğaltır.  
  
   - Uzak bir cihazdan veri topluyorsanız uygulamayı bir Uzak Masaüstü Bağlantısı kullanarak değil doğrudan cihazda çalıştırın.  
  
   - Windows Phone uygulamalar için, verilerin doğrudan **cihazdan** toplanması en doğru verileri sağlar.  
  
2. **Hata Ayıkla** menüsünde, performans profili **Oluşturucu...** öğesini seçin.  
  
3. **CPU kullanımı** ' nı seçin ve ardından **Başlat**' ı seçin.  
  
    ![CPU kullanımı seçin](../profiling/media/cpuuse-lib-choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4. Uygulama başladığında, **en fazla sayıyı al**' a tıklayın. Çıktı görüntülendikten sonra ikinci bir saniye bekleyip, **en fazla zaman uyumsuz olarak al**' ı seçin. Düğme tıklamasının beklenmesi, tanılama raporundaki düğme tıklama yordamlarını yalıtmak için daha kolay hale gelir.  
  
5. İkinci çıkış satırı göründükten sonra performans ve tanılama hub 'ında **toplamayı durdur** ' u seçin.  
  
   ![CpuUsage veri toplamayı durdur](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   CPU kullanımı aracı verileri analiz eder ve raporu görüntüler.  
  
   ![CpuUsage raporu](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>CPU kullanımı raporunu analiz etme  
  
### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> CPU kullanımı çağrı ağacı  
 Çağrı ağacı bilgilerini anlamak için, segmenti yeniden seçin `GetMaxNumberButton_Click` ve çağrı ağacı ayrıntılarına bakın.  
  
#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> Çağrı ağacı yapısı  
 ![GetMaxNumberButton&#95;çağrı ağacı ' na tıklayın](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|Görüntü|Description|  
|-|-|  
|![1. Adım](../profiling/media/procguid-1.png "ProcGuid_1")|CPU kullanım çağrısı ağaçlarında en üst düzey düğüm bir sözde düğümdür|  
|![2. Adım](../profiling/media/procguid-2.png "ProcGuid_2")|Çoğu uygulamalarda, **dış kodu göster** seçeneği devre dışı bırakıldığında, ikinci düzey düğüm, uygulamayı başlatan ve durduran sistem ve çerçeve kodunu içeren bir **[Dış kod]** düğümüdür, Kullanıcı arabirimini çizer, iş parçacığı zamanlamasını denetler ve uygulamaya diğer alt düzey hizmetler sağlar.|  
|![3. Adım](../profiling/media/procguid-3.png "ProcGuid_3")|İkinci düzey düğümün alt öğeleri, ikinci düzey sistem ve Framework kodu tarafından çağrılan veya oluşturulan kullanıcı kodu yöntemleri ve zaman uyumsuz yordamlardır.|  
|![4. adım](../profiling/media/procguid-4.png "ProcGuid_4")|Bir metodun alt düğümleri yalnızca üst yöntemin çağrıları için veri içerir. **Dış kodu göster** devre dışı bırakıldığında, uygulama yöntemleri bir **[Dış kod]** düğümü de içerebilir.|  
  
#### <a name="external-code"></a><a name="BKMK_External_Code"></a> Dış kod  
 Dış kod, System ve Framework bileşenlerinde yazdığınız kod tarafından yürütülen işlevlerdir. Dış kod, uygulamayı başlatıp durduran, Kullanıcı arabirimini çizdiğiniz, iş parçacığı denetleyen ve diğer alt düzey Hizmetleri uygulamaya sağlayan işlevleri içerir. Çoğu durumda, harici kod ile ilgilenmezsiniz ve bu nedenle CPU kullanımı çağrı ağacı bir Kullanıcı yönteminin dış işlevlerini tek bir **[harici kod]** düğümüne toplar.  
  
 Dış kodun çağrı yollarını görüntülemek istediğinizde, **filtre görünümü** listesinden **dış kodu göster** ' i seçin ve ardından **Uygula**' yı seçin.  
  
 ![Filtre görünümü ' ne ve ardından dış kodu göster ' i seçin](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Çok sayıda dış kod çağrı zincirinin derin iç içe geçmiş olduğunu unutmayın. böylece, Işlev adı sütununun genişliği, bilgisayar izlemelerinin en büyük bir bütün boyutunu aşabilirler. Bu durumda, işlev adları **[...]** olarak gösterilir:  
  
 ![Çağrı ağacındaki iç içe dış kod](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Aradığınız düğümü bulmak için arama kutusunu kullanın, ardından verileri görünüme getirmek için yatay kaydırma çubuğunu kullanın:  
  
 ![İç içe geçmiş dış kodu arayın](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="call-tree-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> Ağaç veri sütunlarını çağır  
  
|Özellik|Açıklama|
|-|-|  
|**Toplam CPU (%)**|![Toplam% veri denklemi](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> İşleve yapılan çağrılar ve işlev tarafından çağrılan işlevler tarafından kullanılan seçili zaman aralığındaki uygulamanın CPU etkinliğinin yüzdesi. Bu, bir zaman aralığındaki uygulamanın toplam etkinliğini toplam kullanılabilir CPU kapasitesine karşılaştıran **CPU kullanımı** zaman çizelgesi grafiğinden farklı olduğunu unutmayın.|  
|**Self CPU (%)**|![Kendi kendine denklemi](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> İşlev tarafından çağrılan işlevlerin etkinliği hariç olmak üzere, işlev çağrıları tarafından kullanılan seçili zaman aralığındaki uygulamanın CPU etkinliğinin yüzdesi.|  
|**Toplam CPU (MS)**|Seçili zaman aralığındaki işleve yapılan çağrılar ve işlev tarafından çağrılan işlevler için harcanan milisaniye sayısı.|  
|**Self CPU (MS)**|Seçili zaman aralığındaki işleve yapılan çağrılar ve işlev tarafından çağrılan işlevler için harcanan milisaniye sayısı.|  
|**Modül**|İşlevi içeren modülün adı veya [Dış kod] düğümündeki işlevleri içeren modül sayısı.|  
  
### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> CPU kullanım çağrısı ağacındaki zaman uyumsuz işlevler  
 Derleyici zaman uyumsuz bir yöntemle karşılaştığında, yöntemin yürütmesini denetlemek için gizli bir sınıf oluşturur. Kavramsal olarak, sınıfı, özgün yöntemin işlemlerini zaman uyumsuz olarak çağıran derleyici tarafından oluşturulan işlevlerin bir listesini ve bunları doğru bir şekilde gereken geri çağırmaları, zamanlayıcıyı ve yineleyicilerini çağıran bir durum makinedir. Özgün yöntem bir üst yöntem tarafından çağrıldığında, çalışma zamanı, yöntemi üst öğenin yürütme bağlamından kaldırır ve gizli sınıfın yöntemlerini, uygulamanın yürütülmesini denetleyen sistem ve çerçeve kodu bağlamında çalıştırır. Zaman uyumsuz yöntemler çoğunlukla, her zaman bir veya daha fazla farklı iş parçacığında yürütülürler. Bu kod, ağacın üst düğümünün hemen altındaki **[Dış kod]** düğümünün alt ÖĞELERI olarak CPU kullanım çağrısı ağacında gösterilir.  
  
 Bunu örneğimizde görmek için `GetMaxNumberAsyncButton_Click` zaman çizelgesinde segmenti yeniden seçin.  
  
 ![GetMaxNumberAsyncButton&#95;rapor seçimi ' ne tıklayın](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 **[External Code]** altındaki ilk iki düğüm, durum makinesi sınıfının derleyici tarafından oluşturulan yöntemleridir. Üçüncü, özgün metoda yapılan çağrıdır. Oluşturulan yöntemlerin genişletilmesi, neler olduğunu gösterir.  
  
 ![Genişletilmiş GetMaxNumberAsyncButton&#95;çağrı ağacı ' na tıklayın](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click` çok az; görev değerlerinin bir listesini yönetir, sonuçların maksimum sayısını hesaplar ve çıktıyı görüntüler.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` çağrıyı kaydırmak için gereken 48 görevlerini zamanlamak ve başlatmak için gereken etkinliği gösterir `GetNumberAsync` .  
  
- `MainPage::<GetNumberAsync>b__b` çağıran görevlerin etkinliğini gösterir `GetNumber` .
