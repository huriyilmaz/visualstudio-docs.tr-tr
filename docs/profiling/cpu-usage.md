---
title: Cpu kullanımını analiz Performans Profili Oluşturucu
description: C++, C#, Visual Basic ve JavaScript uygulamalarındaki kodun yürütülmesi için harcanan CPU süresi ve yüzdesini gösteren CPU Kullanımı performans aracı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 04/02/2020
ms.topic: how-to
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2e8db1683fa44ffa75ba6e0ac6aa1a5101c812c8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726838"
---
# <a name="analyze-cpu-usage-without-debugging-in-the-performance-profiler"></a>Cpu kullanımını hata ayıklama olmadan analiz Performans Profili Oluşturucu

Uygulamanıza ilişkin performans sorunlarını araştırmaya başlamanın iyi bir yolu, CPU kullanımını anlamaktır. **CPU Kullanımı performans** aracı C++, C#/Visual Basic ve JavaScript uygulamalarındaki kodun yürütülmesi için harcanan CPU süresi ve yüzdesini gösterir.

CPU Kullanımı aracı açık bir Visual Studio projesinde, yüklü bir Microsoft Store uygulamada veya çalışan bir uygulamaya ya da işleme bağlı olarak çalışıyor olabilir. HATA AYıKLAMA ile veya hata ayıklama olmadan CPU Kullanımı aracını çalıştırabilirsiniz. Daha fazla bilgi için [bkz. Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

Aşağıdaki yönergelerde, hata ayıklayıcı olmadan CPU Kullanımı aracının nasıl ve nasıl Visual Studio Performans Profili Oluşturucu. Örneklerde yerel makinede Yayın derlemesi 2. Yayın derlemeleri gerçek uygulama performansının en iyi görünümünü sağlar. Hata ayıklama derlemeleri (hata ayıklayıcı ekli) ile CPU kullanımını analiz etmek için bkz. Performans [profili oluşturma için başlangıç kılavuzu.](../profiling/beginners-guide-to-performance-profiling.md)

Genellikle, yerel makine en iyi şekilde yüklü uygulama yürütmeyi çoğaltır. Uzak bir cihazdan veri toplamak için uygulamayı doğrudan cihazda çalıştırın, uygulamayı bir Uzak Masaüstü Bağlantısı.

>[!NOTE]
>Windows kullanmak için 7 veya daha yeni [bir](../profiling/profiling-feature-tour.md)Performans Profili Oluşturucu.

## <a name="collect-cpu-usage-data"></a>CPU kullanım verilerini toplama

1. Visual Studio projesinde, çözüm yapılandırmasını Yayınla olarak ayarlayın ve dağıtım hedefi **olarak Yerel** Windows Hata Ayıklayıcısı (veya Yerel **Makine)** öğesini seçin. 

    ![Yayın ve Yerel Makine'yi seçin](../profiling/media/cpuuse_selectreleaselocalmachine.png "Yayın ve Yerel Makine'yi seçin")

1. Hata **ayıkla'Performans Profili Oluşturucu.**  >  

1. Kullanılabilir **araçlar'ın** altında **CPU Kullanımı'nın ardından** Başlat'ı **seçin.**

    ![CPU Kullanımı'ı seçin](../profiling/media/cpuuse_lib_choosecpuusage.png "CPU Kullanımı'ı seçin")

4. Uygulama başlatıldıktan sonra tanılama oturumu başlar ve CPU kullanım verilerini görüntüler. Veri toplamayı bitirdikten sonra Koleksiyonu **Durdur'a seçin.**

   ![CPU Kullanımı veri toplamayı durdurma](../profiling/media/cpu_use_wt_stopcollection.png "CPU Kullanımı veri toplamayı durdurma")

   CPU Kullanımı aracı verileri analiz eder ve raporu görüntüler.

   ![CPU Kullanımı raporu](../profiling/media/cpu_use_wt_report.png "CPU Kullanımı raporu")

## <a name="analyze-the-cpu-usage-report"></a>CPU Kullanımı raporunu analiz etme

Tanılama raporu, En yüksekten en **düşerek Toplam CPU'ya** göre sıralanmış. Sütun üst bilgilerini seçerek sıralama sıralama veya sıralama sütununu değiştirme. Görüntülemek istediğiniz **iş** parçacıklarını seçmek veya seçimini kaldırmak  için Filtre açılan listesinden belirli bir iş parçacığını veya düğümü aramak için Arama kutusunu kullanın.

::: moniker range=">=vs-2019"
2019'Visual Studio başlayarak, çağrı ağacı görünümünde CPU'nun en yüksek yüzdesini kullanan işlev çağrılarını görmek için Hot **Path** Genişlet ve Hot **Path** Göster düğmelerine tıklarsiniz.
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> CPU Kullanımı veri sütunları

|Ad|Açıklama|
|-|-|
|**Toplam CPU [birim, %]**|![Toplam % veri denklemi](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> İşleve yapılan çağrılar tarafından kullanılan milisaniye ve CPU yüzdesi ile seçilen zaman aralığında işlev tarafından çağrılan işlevler. Bu, bir zaman **aralığındaki toplam CPU** etkinliğini toplam kullanılabilir CPU ile karşılaştıran CPU Kullanımı zaman çizelgesi grafiğinden farklıdır.|
|**Kendi KENDINE CPU [birim, %]**|![Kendi kendine % denklemi](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> İşlev tarafından çağrılan işlevler hariç olmak üzere, seçilen zaman aralığında işleve yapılan çağrılar tarafından kullanılan milisaniye ve CPU yüzdesi.|
|**Modül**|İşlevi içeren modülün adı.

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> CPU Kullanımı çağrı ağacı

Çağrı ağacını görüntülemek için raporda üst düğümü seçin. **CPU Kullanımı** sayfası **Arayan/Çağrılı görünümünü** açar. Geçerli Görünüm **açılan listesinde** Çağrı Ağacı'ı **seçin.**

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> Çağrı ağacı yapısı

::: moniker range=">=vs-2019"
![Çağrı ağacı yapısı](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "Çağrı ağacı yapısı")
::: moniker-end
::: moniker range="vs-2017"
![Çağrı ağacı yapısı](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "Çağrı ağacı yapısı")
::: moniker-end

|Görüntü|Description|
|-|-|
|![1. Adım](../profiling/media/procguid_1.png "ProcGuid_1")|CPU Kullanımı çağrı ağaçlarında üst düzey düğüm, sözde düğüm olur.|
|![2. Adım](../profiling/media/procguid_2.png "ProcGuid_2")|Çoğu uygulama için Dış Kodu **Göster seçeneği** devre dışı bırakılmıştır ve ikinci düzey düğüm bir **[Dış Kod] düğümü** olur. Düğüm, uygulamayı başlatan ve durduran, kullanıcı arabirimini çizen, iş parçacığı zamanlamayı kontrol eden ve uygulamaya diğer alt düzey hizmetleri sağlayan sistem ve çerçeve kodunu içerir.|
|![3. Adım](../profiling/media/procguid_3.png "ProcGuid_3")|İkinci düzey düğümün altları, ikinci düzey sistem ve çerçeve kodu tarafından çağrılarak veya oluşturulan kullanıcı kodu yöntemleri ve zaman uyumsuz yordamlardır.|
|![4. Adım](../profiling/media/procguid_4.png "ProcGuid_4")|Bir yöntemin alt düğümleri yalnızca üst yöntemin çağrıları için verilere sahip olur. Dış **Kodu Göster devre** dışı bırakılmıştır, uygulama yöntemleri bir **[Dış Kod] düğümü de** içerebilir.|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a> Dış kod

Kodunuz tarafından yürütülen sistem ve çerçeve işlevleri dış kod *olarak çağrılır.* Dış kod işlevleri uygulamayı başlatabilir ve durdurabilir, kullanıcı arabirimini çizebilir, iş parçacığını kontrol eder ve uygulamaya diğer alt düzey hizmetleri sağlar. Çoğu durumda dış kodla ilgilenmezsiniz, bu nedenle CPU Kullanımı çağrı ağacı bir kullanıcı yönteminin dış işlevlerini tek **bir [Dış Kod] düğümünde** toplar.

Dış kodun çağrı yollarını görüntülemek için ana tanılama raporu sayfasında  (sağ bölme),  Filtre açılan listesinden Dış Kodu Göster'i seçin ve uygula'yı **seçin.** ARDıNDAN **CPU Kullanımı** sayfasının Çağrı **Ağacı** görünümü dış kod çağrılarını genişlettir. (Filtre  açılan listesinde ayrıntılı görünümler değil ana tanılama sayfasında kullanılabilir.)

![Dış Kodu Göster](../profiling/media/cpu_use_wt_filterview.png "Dış kodu göster")

Birçok dış kod çağrısı zinciri iç içe geçmiştir, bu nedenle zincirin genişliği İşlev Adı sütununu görüntüleme **genişliğini aşabilir.** İşlev adları daha sonra **... olarak görünür.**

![Çağrı ağacında iç içe dış kod](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "Çağrı ağacındaki iç içe dış kod")

Bulmak istediğiniz işlev adını bulmak için arama kutusunu kullanın. Seçili satırın üzerine gelin veya verileri görüntülemek için yatay kaydırma çubuğunu kullanın.

::: moniker range=">=vs-2019"
![İç içe dış kod arama](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "İç içe geçmiş dış kodu arayın")
::: moniker-end
::: moniker range="vs-2017"
![İç içe dış kod arama](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "İç içe geçmiş dış kodu arayın")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> CPU kullanımı çağrı ağacında zaman uyumsuz işlevler

 Derleyici zaman uyumsuz bir yöntemle karşılaştığında, yöntemin yürütülmesini kontrol etmek için gizli bir sınıf oluşturur. Kavramsal olarak, sınıfı bir durum makinesidir. sınıfı, özgün yöntemleri zaman uyumsuz olarak çağıran derleyici tarafından oluşturulan işlevlere ve bunları çalıştırmak için gereken geri çağırmalara, zamanlayıcıya ve iterators'a sahiptir. Bir üst yöntem özgün yöntemi çağırsa, derleyici yöntemi üst öğenin yürütme bağlamından kaldırır ve gizli sınıf yöntemlerini uygulama yürütmeyi kontrol eden sistem ve çerçeve kodu bağlamında çalıştırır. Zaman uyumsuz yöntemler genellikle bir veya daha fazla farklı iş parçacığında yürütülür ancak her zaman yürütülmez. Bu kod, **CPU Kullanımı çağrı** ağacında, ağacın üst düğümünün hemen altında **[Dış Kod]** düğümünün altları olarak görünür.

Aşağıdaki örnekte, **[Dış Kod]** altındaki ilk iki düğüm, durum makinesi sınıfının derleyici tarafından oluşturulan yöntemleridir. Üçüncü düğüm, özgün yöntemine yapılan çağrıdır.

![Zaman uyumsuz düğüm](media/cpu_use_wt_getmaxnumberasync_selected.png "Zaman uyumsuz düğüm")

Neler olduğunu göstermek için oluşturulan yöntemleri genişletin:

![Genişletilmiş zaman uyumsuz düğüm](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "Genişletilmiş zaman uyumsuz düğüm")

- `MainPage::GetMaxNumberAsyncButton_Click` yalnızca görev değerlerinin listesini yönetir, en yüksek sonuçları hesaplar ve çıkışı görüntüler.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` , çağrıyı olarak sarmalanmış 48 görevi zamanlaması ve başlatması için gereken etkinliği `GetNumberAsync` gösterir.

- `MainPage::<GetNumberAsync>b__b` çağıran görevlerin etkinliğini `GetNumber` gösterir.
