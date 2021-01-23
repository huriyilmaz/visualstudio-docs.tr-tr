---
title: Performans Profiler 'da CPU kullanımını analiz etme
description: C++, C#, Visual Basic ve JavaScript uygulamalarında kod çalıştırırken harcanan CPU süresini ve yüzdesini gösteren CPU kullanımı performans aracı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 04/02/2020
ms.topic: how-to
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 902974c195cabf09abf5f29334a1e28316da54e5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719363"
---
# <a name="analyze-cpu-usage-without-debugging-in-the-performance-profiler"></a>Performans profil oluşturucusu 'nda hata ayıklama olmadan CPU kullanımını çözümleme

Uygulamanızdaki performans sorunlarını araştırmaya başlamak için iyi bir yöntem, CPU kullanımını anlamaktır. **CPU kullanımı** performans aracı, C++, C#/Visual Basic ve JavaScript uygulamalarında kod ÇALıŞTıRıRKEN harcanan CPU süresini ve yüzdesini gösterir.

CPU kullanımı aracı açık bir Visual Studio projesi üzerinde, yüklü bir Microsoft Store uygulamasında veya çalışan bir uygulamaya veya işleme bağlı olarak çalışabilir. CPU kullanımı aracını hata ayıklama olmadan veya olmadan çalıştırabilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Aşağıdaki yönergeler, Visual Studio performans profil oluşturucuyu kullanarak, hata ayıklayıcı olmadan CPU kullanımı aracının nasıl kullanılacağını göstermektedir. Örnekler yerel bir makinede bir yayın derlemesi kullanır. Yayın yapıları gerçek uygulama performansının en iyi görünümünü sağlar. Hata ayıklama Derlemeleriyle CPU kullanımını çözümlemek için (hata ayıklayıcı ekli), bkz. [Başlangıç Kılavuzu, performans profili oluşturma](../profiling/beginners-guide-to-performance-profiling.md).

Genellikle, yerel makine yüklü uygulama yürütmeyi en iyi şekilde çoğaltır. Uzak bir cihazdan veri toplamak için, uygulamayı bir Uzak Masaüstü Bağlantısı değil doğrudan cihazda çalıştırın.

>[!NOTE]
>[Performans profil oluşturucuyu](../profiling/profiling-feature-tour.md)kullanmak için Windows 7 veya üzeri gereklidir.

## <a name="collect-cpu-usage-data"></a>CPU kullanım verilerini topla

1. Visual Studio projesinde, çözüm yapılandırmasını **yayınlama** olarak ayarlayın ve dağıtım hedefi olarak **yerel Windows hata ayıklayıcısı** 'Nı (veya **yerel makine**) seçin.

    ![Yayın ve yerel makine seçin](../profiling/media/cpuuse_selectreleaselocalmachine.png "Yayın ve yerel makine seçin")

1. **Hata ayıklama**  >  **performans profil oluşturucuyu** seçin.

1. **Kullanılabilir araçlar**' ın altında **CPU kullanımı**' nı seçin ve ardından **Başlat**' ı seçin.

    ![CPU kullanımını seçin](../profiling/media/cpuuse_lib_choosecpuusage.png "CPU kullanımını seçin")

4. Uygulama başladıktan sonra, Tanılama oturumu başlar ve CPU kullanım verilerini görüntüler. Verileri toplamayı tamamladığınızda, **toplamayı durdur**' u seçin.

   ![CPU kullanımı veri toplamayı durdur](../profiling/media/cpu_use_wt_stopcollection.png "CPU kullanımı veri toplamayı durdur")

   CPU kullanımı aracı verileri analiz eder ve raporu görüntüler.

   ![CPU kullanımı raporu](../profiling/media/cpu_use_wt_report.png "CPU kullanımı raporu")

## <a name="analyze-the-cpu-usage-report"></a>CPU kullanımı raporunu analiz etme

Tanılama raporu, en yüksekten en düşüğe kadar **toplam CPU**'ya göre sıralanır. Sütun üstbilgilerini seçerek sıralama düzenini veya sıralama sütununu değiştirin. Görüntülenecek iş parçacıklarını seçmek veya seçimlerini kaldırmak için **filtre** açılan listesini kullanın ve belirli bir iş parçacığı veya düğüm aramak için **arama** kutusunu kullanın.

::: moniker range=">=vs-2019"
Visual Studio 2019 ' den başlayarak, çağrı ağacı görünümünde CPU 'nun en yüksek yüzdesini kullanan işlev çağrılarını görmek için **etkin yolu genişlet** ve **etkin yolu göster** düğmelerini tıklayabilirsiniz.
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> CPU kullanım verileri sütunları

|Ad|Açıklama|
|-|-|
|**Toplam CPU [Birim,%]**|![Toplam% veri denklemi](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> İşlev çağrıları tarafından kullanılan milisaniye ve CPU yüzdesi ve işlev tarafından çağrılan işlevler, seçili zaman aralığında. Bu, bir zaman aralığındaki toplam CPU etkinliğini toplam kullanılabilir CPU ile karşılaştıran **CPU kullanımı** zaman çizelgesi grafiğinden farklıdır.|
|**Self CPU [Birim,%]**|![Kendi kendine denklemi](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> İşlev tarafından çağrılan işlevler hariç olmak üzere seçilen zaman aralığındaki işleve yapılan çağrılar tarafından kullanılan milisaniye ve CPU yüzdesi.|
|**Modül**|İşlevi içeren modülün adı.

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> CPU kullanımı çağrı ağacı

Çağrı ağacını görüntülemek için, rapordaki üst düğümü seçin. **CPU kullanımı** sayfası **arayan/çağrılan** görünümüne açılır. **Geçerli görünüm** açılır listesinde, **çağrı ağacı**' nı seçin.

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> Çağrı ağacı yapısı

::: moniker range=">=vs-2019"
![Çağrı ağacı yapısı](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "Çağrı ağacı yapısı")
::: moniker-end
::: moniker range="vs-2017"
![Çağrı ağacı yapısı](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "Çağrı ağacı yapısı")
::: moniker-end

|Görüntü|Açıklama|
|-|-|
|![1. Adım](../profiling/media/procguid_1.png "ProcGuid_1")|CPU kullanım çağrısı ağaçlarında en üst düzey düğüm bir sözde düğümdür.|
|![2. Adım](../profiling/media/procguid_2.png "ProcGuid_2")|Çoğu uygulamalarda, **dış kodu göster** seçeneği devre dışı bırakıldığında, ikinci düzey düğüm bir **[Dış kod]** düğümüdür. Düğüm, uygulamayı başlatan ve durduran sistem ve çerçeve kodunu içerir, Kullanıcı arabirimini çizer, iş parçacığı zamanlamasını denetler ve uygulamaya diğer alt düzey hizmetler sağlar.|
|![3. Adım](../profiling/media/procguid_3.png "ProcGuid_3")|İkinci düzey düğümün alt öğeleri, ikinci düzey sistem ve Framework kodu tarafından çağrılan veya oluşturulan kullanıcı kodu yöntemleri ve zaman uyumsuz yordamlardır.|
|![4. adım](../profiling/media/procguid_4.png "ProcGuid_4")|Bir metodun alt düğümleri yalnızca üst metodun çağrılarına ait verilere sahiptir. **Dış kodu göster** devre dışı bırakıldığında, uygulama yöntemleri bir **[Dış kod]** düğümü de içerebilir.|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a> Dış kod

Kodunuz tarafından yürütülen System ve Framework işlevlerine *dış kod* denir. Dış kod işlevleri uygulamayı başlatıp durdurur, Kullanıcı arabirimini çizer, iş parçacığı denetimi yapın ve uygulamaya diğer alt düzey hizmetler sağlar. Çoğu durumda, dış kodla ilgilenmiyorsanız, CPU kullanım çağrısı ağacı bir Kullanıcı yönteminin dış işlevlerini tek bir **[Dış kod]** düğümüne toplar.

Dış kodun çağrı yollarını görüntülemek için, ana tanılama raporu sayfasında (sağ bölme), **filtre** açılan listesinden **dış kodu göster** ' i seçin ve ardından **Uygula**' yı seçin. **CPU kullanımı** sayfasının **çağrı ağacı** görünümü daha sonra dış kod çağrılarını genişletir. ( **Filtre** açılan listesi, ayrıntılı görünümlerde değil, ana tanılama sayfasında kullanılabilir.)

![Dış kodu göster](../profiling/media/cpu_use_wt_filterview.png "Dış kodu göster")

Birçok harici kod çağrısı zinciri daha fazla iç içe geçmiş olduğundan, zincirin genişliği, **Işlev adı** sütununun görüntüleme genişliğini aşabilir. Sonra işlev adları **..**. olarak görünür.

![Çağrı ağacındaki iç içe dış kod](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "Çağrı ağacındaki iç içe dış kod")

Aradığınız bir işlev adını bulmak için arama kutusunu kullanın. Seçili çizginin üzerine gelin veya verileri görüntülemek için yatay kaydırma çubuğunu kullanın.

::: moniker range=">=vs-2019"
![İç içe geçmiş dış kodu arayın](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "İç içe geçmiş dış kodu arayın")
::: moniker-end
::: moniker range="vs-2017"
![İç içe geçmiş dış kodu arayın](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "İç içe geçmiş dış kodu arayın")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> CPU kullanım çağrısı ağacındaki zaman uyumsuz işlevler

 Derleyici zaman uyumsuz bir yöntemle karşılaştığında, yöntemin yürütmesini denetlemek için gizli bir sınıf oluşturur. Kavramsal olarak, sınıfı bir durum makinedir. Sınıfında, özgün yöntemleri zaman uyumsuz olarak çağıran ve geri çağırmalar, Zamanlayıcı ve yineleyiciler çalıştırmak için gereken derleyici tarafından üretilmiş işlevler bulunur. Bir üst yöntem özgün yöntemi çağırdığında, derleyici yöntemi üst öğenin yürütme bağlamından kaldırır ve gizli sınıf yöntemlerini uygulama yürütmeyi denetleyen sistem ve çerçeve kodu bağlamında çalıştırır. Zaman uyumsuz yöntemler çoğunlukla, her zaman bir veya daha fazla farklı iş parçacığında yürütülürler. Bu kod, ağacın üst düğümünün hemen altındaki **[Dış kod]** düğümünün alt öğeleri olarak **CPU kullanım** çağrısı ağacında görüntülenir.

Aşağıdaki örnekte, **[External Code]** altındaki ilk iki düğüm, durum makinesi sınıfının derleyici tarafından oluşturulan yöntemleridir. Üçüncü düğüm, özgün yönteme yapılan çağrıdır.

![Zaman uyumsuz düğüm](media/cpu_use_wt_getmaxnumberasync_selected.png "Zaman uyumsuz düğüm")

Oluşturulan yöntemleri genişleterek neler olduğunu gösterebilirsiniz:

![Genişletilmiş zaman uyumsuz düğüm](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "Genişletilmiş zaman uyumsuz düğüm")

- `MainPage::GetMaxNumberAsyncButton_Click` yalnızca görev değerlerinin bir listesini yönetir, sonuçların maksimum sayısını hesaplar ve çıktıyı görüntüler.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` çağrıyı kaydırmak için gereken 48 görevlerini zamanlamak ve başlatmak için gereken etkinliği gösterir `GetNumberAsync` .

- `MainPage::<GetNumberAsync>b__b` çağıran görevlerin etkinliğini gösterir `GetNumber` .
