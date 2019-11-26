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
ms.openlocfilehash: f699666216d38c34583ebeb15e2bb6ba4953b671
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300752"
---
# <a name="cpu-usage"></a>CPU Kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızdaki performans sorunlarını araştırmanız gerektiğinde, baştan başlamak, CPU 'YU nasıl kullandığını öğreniyor. **CPU kullanımı** Aracı, CPU 'nun Visual C++, Visual C#/Visual Basic ve JavaScript kodu yürütme zamanının nerede harcamaya yönelik olduğunu gösterir.  
  
 Visual Studio 2015 güncelleştirme 1 ' den başlayarak, hata ayıklayıcıdan çıkmadan CPU kullanımının işlev başına dökümünü görebilirsiniz. Hata ayıklama sırasında CPU profili oluşturmayı ve devre dışı bırakabilirsiniz ve örneğin bir kesme noktasında yürütme durdurulduğunda sonuçları görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 2015 ' de hata ayıklayıcıda CPU 'Yu profil](https://devblogs.microsoft.com/devops/profile-your-cpu-in-the-debugger-in-visual-studio-2015/).  
  
 Bir Windows Mağazası uygulamasının performansını analiz eden bir anlatım için bkz. [Mağaza UYGULAMALARıNDA CPU kullanımını çözümleme](https://msdn.microsoft.com/library/windows/apps/dn641982.aspx).  
  
 Performans ve tanılama hub 'ı, tanılama oturumunuzu çalıştırmak ve yönetmek için size çok sayıda seçenek sunar. Örneğin, **CPU kullanımı** aracını yerel veya uzak makinelerde veya bir simülatör ya da öykünücü içinde çalıştırabilirsiniz. Visual Studio 'da bir açık projenin performansını analiz edebilir, çalışan bir uygulamaya iliştirilir veya Windows Mağazası 'ndan yüklenen bir uygulamayı başlatabilirsiniz. Daha fazla bilgi için bkz. [profil oluşturma araçlarını hata ayıklama olmadan çalıştırma](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
## <a name="BKMK_Collect_CPU_usage_data"></a>CPU kullanım verilerini topla  
  
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
  
   CPU kullanımı aracı verileri çözümler ve rapor görüntüler.  
  
   ![CpuUsage raporu](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>CPU kullanımı raporunu analiz etme  
  
### <a name="BKMK_The_CPU_Usage_call_tree"></a>CPU kullanımı çağrı ağacı  
 Çağrı ağacı bilgilerini anlamak için `GetMaxNumberButton_Click` segmentini yeniden seçin ve çağrı ağacı ayrıntılarına bakın.  
  
#### <a name="BKMK_Call_tree_structure"></a>Çağrı ağacı yapısı  
 ![GetMaxNumberButton&#95;çağrı ağacı öğesine tıklayın](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![1. adım](../profiling/media/procguid-1.png "ProcGuid_1")|CPU kullanımı çağrı ağaçları en üst düzey düğüm sözde düğümüdür|  
|![2. adım](../profiling/media/procguid-2.png "ProcGuid_2")|Çoğu uygulamalarda, **dış kodu göster** seçeneği devre dışı bırakıldığında, ikinci düzey düğüm, uygulamayı başlatan ve durduran sistem ve çerçeve kodunu içeren bir **[Dış kod]** düğümüdür, Kullanıcı arabirimini çizer, iş parçacığı zamanlamasını denetler ve uygulamaya diğer alt düzey hizmetler sağlar.|  
|![3. adım](../profiling/media/procguid-3.png "ProcGuid_3")|İkinci düzey düğümünün alt öğeleri, kullanıcı kodu yöntemleri ve çağrılan veya framework kodu ve ikinci düzey sistem tarafından oluşturulan zaman uyumsuz yordamlarını verilmiştir.|  
|![4. adım](../profiling/media/procguid-4.png "ProcGuid_4")|Bir yöntemin alt düğümleri yalnızca üst yöntem çağrıları için veri içerir. **Dış kodu göster** devre dışı bırakıldığında, uygulama yöntemleri bir **[Dış kod]** düğümü de içerebilir.|  
  
#### <a name="BKMK_External_Code"></a>Dış kod  
 Dış kod, System ve Framework bileşenlerinde yazdığınız kod tarafından yürütülen işlevlerdir. Dış kod Başlat ve uygulamayı durdurun, UI çizme, iş parçacığı oluşturma denetleyen ve uygulama diğer alt düzey hizmetler sağlayan işlevler içerir. Çoğu durumda, harici kod ile ilgilenmezsiniz ve bu nedenle CPU kullanımı çağrı ağacı bir Kullanıcı yönteminin dış işlevlerini tek bir **[harici kod]** düğümüne toplar.  
  
 Dış kodun çağrı yollarını görüntülemek istediğinizde, **filtre görünümü** listesinden **dış kodu göster** ' i seçin ve ardından **Uygula**' yı seçin.  
  
 ![Filtre görünümü ' ne ve ardından dış kodu göster ' i seçin](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Böylece işlev adı sütun genişliğini tüm bilgisayar monitörü en büyük görüntü genişliğini aşabilir birçok dış kod arama zincirleri iç içe girmiş olduğunu, unutmayın. Bu durumda, işlev adları **[...]** olarak gösterilir:  
  
 ![Çağrı ağacındaki iç içe dış kod](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Aradığınız düğümü bulmak için arama kutusunu kullanın, ardından verileri görünüme getirmek için yatay kaydırma çubuğunu kullanın:  
  
 ![İç içe geçmiş dış kodu arayın](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="BKMK_Call_tree_data_columns"></a>Ağaç veri sütunlarını çağır  
  
|||  
|-|-|  
|**Toplam CPU (%)**|![Toplam% veri denklemi](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> İşleve yapılan çağrılar ve işlev tarafından çağrılan işlevler tarafından kullanılan seçili zaman aralığındaki uygulamanın CPU etkinliğinin yüzdesi. Bu, bir zaman aralığındaki uygulamanın toplam etkinliğini toplam kullanılabilir CPU kapasitesine karşılaştıran **CPU kullanımı** zaman çizelgesi grafiğinden farklı olduğunu unutmayın.|  
|**Self CPU (%)**|![Kendi kendine denklemi](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> İşlev tarafından çağrılan işlevlerin etkinliği hariç olmak üzere, işlev çağrıları tarafından kullanılan seçili zaman aralığındaki uygulamanın CPU etkinliğinin yüzdesi.|  
|**Toplam CPU (MS)**|Seçili zaman aralığındaki işleve yapılan çağrılar ve işlev tarafından çağrılan işlevler için harcanan milisaniye sayısı.|  
|**Self CPU (MS)**|Seçili zaman aralığındaki işleve yapılan çağrılar ve işlev tarafından çağrılan işlevler için harcanan milisaniye sayısı.|  
|**Module**|İşlevi içeren modülün adı veya [Dış kod] düğümündeki işlevleri içeren modül sayısı.|  
  
### <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a>CPU kullanım çağrısı ağacındaki zaman uyumsuz işlevler  
 Derleyici zaman uyumsuz bir yöntemle karşılaştığında, yöntemin yürütmesini denetlemek için gizli bir sınıf oluşturur. Kavramsal olarak, sınıfı, özgün yöntemin işlemlerini zaman uyumsuz olarak çağıran derleyici tarafından oluşturulan işlevlerin bir listesini ve bunları doğru bir şekilde gereken geri çağırmaları, zamanlayıcıyı ve yineleyicilerini çağıran bir durum makinedir. Özgün yöntem bir üst yöntem tarafından çağrıldığında, çalışma zamanı, yöntemi üst öğenin yürütme bağlamından kaldırır ve gizli sınıfın yöntemlerini, uygulamanın yürütülmesini denetleyen sistem ve çerçeve kodu bağlamında çalıştırır. Zaman uyumsuz yöntemler genellikle, ancak her zaman, bir veya daha fazla farklı iş parçacıkları üzerinde yürütülür. Bu kod, ağacın üst düğümünün hemen altındaki **[Dış kod]** düğümünün alt ÖĞELERI olarak CPU kullanım çağrısı ağacında gösterilir.  
  
 Bunu örneğimizde görmek için zaman çizelgesinde `GetMaxNumberAsyncButton_Click` segmentini yeniden seçin.  
  
 ![GetMaxNumberAsyncButton&#95;rapor seçimi](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 **[External Code]** altındaki ilk iki düğüm, durum makinesi sınıfının derleyici tarafından oluşturulan yöntemleridir. Üçüncü, özgün metoda yapılan çağrıdır. Oluşturulan yöntemlerin genişletilmesi, neler olduğunu gösterir.  
  
 ![Genişletilmiş GetMaxNumberAsyncButton&#95;tıklama çağrı ağacı](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click` çok az; görev değerlerinin bir listesini yönetir, sonuçların maksimum sayısını hesaplar ve çıktıyı görüntüler.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext`, `GetNumberAsync`çağrısını sarması gereken 48 görevlerini zamanlamak ve başlatmak için gereken etkinliği gösterir.  
  
- `MainPage::<GetNumberAsync>b__b`, `GetNumber`çağıran görevlerin etkinliğini gösterir.
