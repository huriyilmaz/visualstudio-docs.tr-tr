---
title: CPU kullanımını analiz et | Microsoft Dokümanlar
ms.custom: seodec18
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 351247f50560896d53267fcf8d7f4a66a81b9461
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553633"
---
# <a name="analyze-cpu-usage"></a>CPU kullanımını analiz etme

Uygulamanızdaki performans sorunlarını araştırmaya başlamanın iyi bir yolu, uygulamanın CPU kullanımını anlamaktır. **CPU Kullanımı** performans aracı, C++, C#/Visual Basic ve JavaScript uygulamalarında kod yürütme için harcanan CPU süresini ve yüzdesini gösterir.

**CPU Kullanımı** aracı açık bir Visual Studio projesinde, yüklü bir Microsoft Mağazası uygulamasında veya çalışan bir uygulamaya veya işleme bağlı olarak çalıştırılabilir. Aracı yerel veya uzak makinelerde veya bir simülatör veya emülatörde çalıştırabilirsiniz. Daha fazla bilgi için [bkz.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

**Cpu Kullanım** aracını hata ayıklama ile veya hata ayıklama olmadan çalıştırabilirsiniz. Hata ayıklamada, CPU profil oluşturmayı açıp kapatabilir ve CPU kullanımının işlev başına dökümünü görebilirsiniz. Yürütme duraklatıldığında, örneğin bir kesme noktasında CPU kullanım sonuçlarını görüntüleyebilirsiniz.

Aşağıdaki yönergeler, Visual Studio **Performance Profiler'ı**kullanarak cpu **kullanım** aracının hata ayıklayıcısı olmadan nasıl kullanılacağını gösterir. Örnekler, yerel bir makine de Sürüm oluşturma yı kullanır. Sürüm oluşturmaları, gerçek uygulama performansının en iyi görünümünü sağlar. Cpu kullanımını Hata Ayıklama yapılarıyla analiz etmek [için, performans profiloluşturma için Başlangıç kılavuzuna](../profiling/beginners-guide-to-performance-profiling.md)bakın.

Genellikle, yerel makine en iyi yüklü uygulama yürütme çoğaltıyor. Windows Phone uygulamaları için, doğrudan cihazdan veri toplamak en doğru verileri sağlar. Uzak bir aygıttan veri toplamak için uygulamayı Uzak Masaüstü Bağlantısı üzerinden değil, doğrudan aygıtta çalıştırın.

>[!NOTE]
>Windows 7 veya daha sonra [Performans Profilleyicisi](../profiling/profiling-feature-tour.md)kullanmak için gereklidir.

## <a name="collect-cpu-usage-data"></a>CPU kullanım verilerini toplama

1. Visual Studio projesinde, çözüm yapılandırmasını **Release'e** ayarlayın ve dağıtım hedefi olarak **Yerel Makine'yi** seçin.

    ![Serbest Bırakma ve Yerel Makine'yi seçin](../profiling/media/cpuuse_selectreleaselocalmachine.png "Serbest Bırakma ve Yerel Makine'yi seçin")

1. **Hata Ayıklama** > **Performans Profilcisi'ni**seçin.

1. **Kullanılabilir araçlar**altında, **CPU Kullanımı'nı**seçin ve ardından **Başlat'ı**seçin.

    ![CPU Kullanımını Seçin](../profiling/media/cpuuse_lib_choosecpuusage.png "CPU Kullanımını Seçin")

4. Uygulama başladıktan sonra tanılama oturumu başlar ve CPU kullanım verilerini görüntüler. Veri toplamayı bitirdiğinizde, **Koleksiyonu Durdur'u**seçin.

   ![CPU Kullanımını Durdur veri toplama](../profiling/media/cpu_use_wt_stopcollection.png "CPU Kullanımını Durdur veri toplama")

   CPU Kullanımı aracı verileri analiz eder ve raporu görüntüler.

   ![CPU Kullanım raporu](../profiling/media/cpu_use_wt_report.png "CPU Kullanım raporu")

## <a name="analyze-the-cpu-usage-report"></a>CPU Kullanım raporunu analiz edin

Tanılama **raporu, En**yüksekten en düşüke, Toplam CPU'ya göre sıralanır. Sütun üstbilgilerini seçerek sıralama sırasını veya sıralama sütununu değiştirin. Görüntülemek için iş parçacıklarını seçmek veya seçmek için **Filtre** açılır dosyasını kullanın ve belirli bir iş parçacığı veya düğümü aramak için **Arama** kutusunu kullanın.

::: moniker range=">=vs-2019"
Visual Studio 2019'dan başlayarak, çağrı ağacı görünümünde CPU'nun en yüksek yüzdesini kullanan işlev çağrılarını görmek için **Sıcak Yolu Genişlet** ve Sıcak Yolu **Göster** düğmelerini tıklatabilirsiniz.
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a>CPU Kullanım veri sütunları

|||
|-|-|
|**Toplam CPU [birim, %]**|![Toplam % veri denklemi](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> İşlev çağrıları tarafından kullanılan milisaniye ve CPU yüzdesi ve işlev tarafından çağrılan işlevler, seçili zaman aralığında. Bu, bir zaman aralığındaki toplam CPU etkinliğini kullanılabilir toplam CPU ile karşılaştıran **CPU Kullanım** zaman çizelgesi grafiğinden farklıdır.|
|**Self CPU [birim, %]**|![Öz % denklemi](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> İşlev tarafından çağrılan işlevler hariç olmak üzere, seçili zaman aralığındaki işleve yapılan çağrılar tarafından kullanılan milisaniye ve CPU yüzdesi.|
|**Modül**|İşleviçeren modülün adı.

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a>CPU Kullanımı çağrı ağacı

Çağrı ağacını görüntülemek için, rapordaki ana düğümü seçin. **CPU Kullanımı** sayfası **Arayan/Callee** görünümüne açılır. Geçerli **Görünüm** açılır açılır düşüşünde **Çağrı Ağacı'nı**seçin.

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a>Çağrı ağacı yapısı

::: moniker range=">=vs-2019"
![Çağrı ağacı yapısı](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "Çağrı ağacı yapısı")
::: moniker-end
::: moniker range="vs-2017"
![Çağrı ağacı yapısı](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "Çağrı ağacı yapısı")
::: moniker-end

|||
|-|-|
|![1. Adım](../profiling/media/procguid_1.png "ProcGuid_1")|CPU Kullanımı çağrı ağaçlarındaki üst düzey düğüm bir sözde düğümdür.|
|![2. Adım](../profiling/media/procguid_2.png "ProcGuid_2")|Çoğu uygulamada, **Dış Kodu Göster** seçeneği devre dışı bırakıldığında, ikinci düzey düğüm bir **[Dış Kod]** düğümüdür. Düğüm, uygulamayı başlatan ve durduran, kullanıcı ayını çizen, iş parçacığı zamanlamasını kontrol eden ve uygulamaya diğer alt düzey hizmetleri sağlayan sistem ve çerçeve kodunu içerir.|
|![3. Adım](../profiling/media/procguid_3.png "ProcGuid_3")|İkinci düzey düğümün alt ları, ikinci düzey sistem ve çerçeve kodu tarafından çağrılan veya oluşturulan kullanıcı kodu yöntemleri ve eşzamanlı yordamlarıdır.|
|![Adım 4](../profiling/media/procguid_4.png "ProcGuid_4")|Yöntemin alt düğümleri yalnızca üst yöntemin çağrıları için veriye sahiptir. **Dış Kodu Göster** devre dışı bırakıldığında, uygulama yöntemleri bir **[Dış Kod]** düğümü de içerebilir.|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a>Dış kod

Kodunuz tarafından yürütülen sistem ve çerçeve *işlevlerine dış kod*denir. Dış kod işlevleri uygulamayı başlatıp durdurur, uI'yi çizer, iş parçacığı işlemini denetler ve uygulamaya diğer düşük seviyeli hizmetler sağlar. Çoğu durumda, dış kodla ilgilenmezsiniz, bu nedenle CPU Kullanımı çağrı ağacı bir kullanıcı yönteminin dış işlevlerini tek bir **[Dış Kod]** düğümünde toplar.

Dış kodun çağrı yollarını görüntülemek için ana tanılama raporu sayfasında (sağ bölmede), **Filtre** açılır sayfasından **Dış Kodu Göster'i** seçin ve ardından **Uygula'yı**seçin. **CPU Kullanımı** sayfasının **Çağrı Ağacı** görünümü daha sonra dış kod çağrılarını genişletir. (Filtre **Filter** açılır sayfası ayrıntılı görünümler değil, ana tanılama sayfasında kullanılabilir.)

![Dış Kodu Göster](../profiling/media/cpu_use_wt_filterview.png "Dış Kodu Göster")

Birçok dış kod çağrı zincirleri derinden iç içe dir, bu nedenle zincirin genişliği **İşlev Adı** sütununun ekran genişliğini aşabilir. İşlev adları daha sonra ... olarak **görünür.**

![Çağrı ağacında iç içe dış kod](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "Çağrı ağacında iç içe dış kod")

Aradığınız işlev adını bulmak için arama kutusunu kullanın. Seçili çizginin üzerine gidin veya verileri görüntülemek için yatay kaydırma çubuğunu kullanın.

::: moniker range=">=vs-2019"
![İç içe dış kodu arama](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "İç içe dış kodu arama")
::: moniker-end
::: moniker range="vs-2017"
![İç içe dış kodu arama](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "İç içe dış kodu arama")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a>CPU kullanım çağrı ağacındaki eşzamanlı işlevler

 Derleyici bir eşzamanlı yöntemle karşılaştığında, yöntemin yürütülmesini denetlemek için gizli bir sınıf oluşturur. Kavramsal olarak, sınıf bir durum makinesidir. Sınıf, özgün yöntemleri eş zamanlı olarak adlandırdığı derleyici tarafından oluşturulan işlevlere ve bunları çalıştırmak için gereken geri arama, zamanlayıcı ve yineleyicilere sahiptir. Bir üst yöntem özgün yöntemi aradığında, derleyici yöntemi üst uygulama bağlamından kaldırır ve uygulama yürütmeyi denetleyen sistem ve çerçeve kodu bağlamında gizli sınıf yöntemlerini çalıştırAr. Eşzamanlı yöntemler genellikle, ancak her zaman değil, bir veya daha fazla farklı iş parçacığı üzerinde yürütülür. Bu **kod, [Dış** **Kod]** düğümünün alt bölümü olarak CPU Kullanımı çağrı ağacında ağacın üst düğümünün hemen altında görünür.

Aşağıdaki örnekte, **[Dış Kod]** altında ilk iki düğüm durum makine sınıfının derleyici tarafından oluşturulan yöntemleridir. Üçüncü düğüm özgün yönteme çağrıdır.

![Asynchronous düğümü](media/cpu_use_wt_getmaxnumberasync_selected.png "Asynchronous düğümü")

Neler olduğunu göstermek için oluşturulan yöntemleri genişletin:

![Genişletilmiş asynchronous düğümü](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "Genişletilmiş asynchronous düğümü")

- `MainPage::GetMaxNumberAsyncButton_Click`görev değerlerinin bir listesini yönetir, sonuçların en üst kısmını görüntüler ve çıktıyı görüntüler.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext`aramayı saran 48 görevi zamanlamanız ve başlatmak için `GetNumberAsync`gereken etkinliği gösterir.

- `MainPage::<GetNumberAsync>b__b`arayan `GetNumber`görevlerin etkinliğini gösterir.
