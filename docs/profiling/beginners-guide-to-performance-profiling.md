---
title: Uygulamalarınızda CPU kullanımını ölçme
description: Hata ayıklayıcı ile tümleşik tanılama araçlarını kullanarak uygulamanızdaki CPU performans sorunlarını çözümleyin.
ms.custom: seodec18
ms.date: 04/03/2021
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 349d4c076c820c6f75291b8048617216cc73717c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628395"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>CPU kullanımını çözümleyerek uygulama performansını ölçme

Hata ayıklayıcı ile tümleşik **CPU kullanımı** Tanılama aracı ile hata ayıklarken performans sorunlarını bulun.  Ayrıca, bir hata ayıklayıcı ekli veya çalışan bir uygulamayı hedefleyerek CPU kullanımını çözümleyebilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Hata ayıklayıcı durakladığında, Tanılama Araçları penceresindeki **CPU kullanımı** aracı uygulamanızda yürütülen işlevlerle ilgili bilgiler toplar. Araç, çalışmayı gerçekleştiren işlevleri listeler ve örnekleme oturumunun belirli kesimlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar.

> [!Important]
> hata ayıklayıcı ile tümleşik tanılama araçları, ASP.NET, ASP.NET Core ve yerel/C++ geliştirmesi gibi Visual Studio .net geliştirme için desteklenir. karşılık gelen Visual Studio [iş yükü](../install/modify-visual-studio.md) gereklidir. hata ayıklayıcı (**Tanılama Araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * CPU kullanım verilerini topla
> * CPU kullanım verilerini çözümleme

**CPU kullanımı** size ihtiyacınız olan verileri sağlamıyorsa, [performans Profiler](../profiling/profiling-feature-tour.md#post_mortem) 'daki diğer profil oluşturma araçları sizin için yararlı olabilecek farklı türde bilgiler sağlar. Çoğu durumda, uygulamanızın performans sorununa bellek, işleme Kullanıcı arabirimi veya ağ isteği süresi gibi CPU 'nuzun bir neden olabilir.

## <a name="step-1-collect-profiling-data"></a>1. Adım: profil oluşturma verilerini toplama

1. Visual Studio hata ayıklamak istediğiniz projeyi açın ve uygulamanızda, CPU kullanımını incelemek istediğiniz noktada bir kesme noktası ayarlayın.

2. Çözümlemek istediğiniz işlevin veya kod bölgesinin sonunda ikinci bir kesme noktası ayarlayın.

    İki kesme noktası ayarlayarak, veri toplamayı çözümlemek istediğiniz kod bölümleriyle sınırlayabilirsiniz.

3. **Tanılama araçları** penceresi devre dışı bırakılmadığı takdirde otomatik olarak görünür. pencereyi yeniden getirmek için **hata ayıkla**  >  **Windows**  >  **Tanılama Araçları göster**' e tıklayın.

4. Araç çubuğundaki **araçları seç** ayarı Ile **CPU kullanımı**, [bellek kullanımı](../profiling/Memory-Usage.md)veya her ikisinin de görüntülenip görüntülenmeyeceğini seçebilirsiniz. Visual Studio Enterprise çalıştırıyorsanız, **araç**  >  **seçenekleri**  >  **ıntellitrace**' de ıntellitrace ' i etkinleştirebilir veya devre dışı bırakabilirsiniz.

     ![Tanılama araçlarını göster](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     Temel olarak CPU kullanımına bakıyoruz, bu nedenle **CPU kullanımının** etkinleştirildiğinden emin olun (varsayılan olarak etkindir).

5. Hata   >  **ayıklamayı Başlat** ' a tıklayın (veya araç çubuğundan veya **F5**' i **başlatın** ).

     Uygulamanın yüklenmesi bittiğinde, tanılama araçlarının Özet görünümü görüntülenir. pencereyi açmanız gerekiyorsa, **hata ayıkla**  >  **Windows**  >  **Tanılama Araçları göster**' e tıklayın.

     ![Tanılama araçları Özet sekmesi](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     Olaylar hakkında daha fazla bilgi için, [Tanılama Araçları penceresinin Olaylar sekmesinde arama ve filtreleme](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)bölümüne bakın.

6. İlk kesme noktasının isabet çekmesine neden olacak senaryoyu çalıştırın.

7. Hata ayıklayıcı duraklatıldığında, CPU kullanım verilerinin toplanmasını etkinleştirin ve ardından **CPU kullanımı** sekmesini açın.

     ![Tanılama araçları CPU profilini oluşturmayı etkinleştirir](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfiling")

     **CPU profilini kaydet**' i seçtiğinizde Visual Studio işlevlerinizi kaydetmeye başlar ve ne kadar süre sürer. Bu toplanan verileri yalnızca, uygulamanız bir kesme noktasında durdurulduğunda görüntüleyebilirsiniz.

8. Uygulamanızı ikinci kesme noktasına çalıştırmak için F5 'e basın.

     Artık, özellikle iki kesme noktası arasında çalışan kod bölgesi için uygulamanız için performans verileri vardır.

     Profil Oluşturucu iş parçacığı verilerini hazırlamaya başlar. Bitmesini bekleyin.

     ![Tanılama araçları Iş parçacıklarını hazırlama](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     CPU kullanımı aracı, raporu **CPU kullanımı** sekmesinde görüntüler.

     ![Tanılama araçları CPU kullanımı sekmesi](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. Analiz etmek için daha belirli bir kod bölgesi seçmek istiyorsanız, CPU zaman çizelgesinde bir bölge seçin (profil oluşturma verilerini gösteren bir bölge olmalıdır).

     ![Tanılama araçları bir zaman dilimi seçme](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     Bu noktada, verileri çözümlemeye başlayabilirsiniz.

     > [!TIP]
     >  Performans sorunlarını belirlemeye çalışırken, birden çok ölçü alın. Performans doğal olarak çalıştırma, çalıştırma ve kod yollarının, dll 'Leri yükleme, JıT derleme yöntemleri ve önbellekleri başlatma gibi bir kerelik başlatma işi nedeniyle genellikle daha yavaş yürütülür. Birden çok ölçüm gerçekleştirerek, gösterilen ölçümün aralığı ve ortancası hakkında daha iyi fikir edinirsiniz. Bu, bir kod alanının sabit durum performansına karşı ilk kez karşılaştırmanızı sağlar.

## <a name="step-2-analyze-cpu-usage-data"></a>2. Adım: CPU kullanım verilerini çözümleme

CPU kullanımı altındaki işlevlerin listesini inceleyerek, en çok iş yapan işlevleri tanımlayarak ve sonra her birine daha yakından bakarak verilerinizi analiz etmeye başlamanızı öneririz.

1. İşlev listesinde, en çok iş yapan işlevleri inceleyin.

    ![Tanılama araçları CPU kullanımı Işlev listesi](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > İşlevler, en çok iş yapmaktan (çağrı sırasıyla değil) başlayarak sırayla listelenir. Bu, en uzun çalışan işlevleri hızlıca belirlemenize yardımcı olur.

2. İşlev listesinde, çok sayıda iş yapan uygulama işlevlerinizin birine çift tıklayın.

    Bir işleve çift tıkladığınızda, **çağıran/çağrılan** görünümü sol bölmede açılır.

    ![Tanılama araçları çağıran çağrılan görünümü](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    Bu görünümde, seçilen işlev başlıkta ve **geçerli işlev** kutusunda (getnumber, bu örnekte) görüntülenir. Geçerli işlevi çağıran işlev, sol tarafta **çağırma işlevleri** altında gösterilir ve geçerli işlev tarafından çağrılan işlevler sağ taraftaki **çağrılan işlevler** kutusunda gösterilir. (Geçerli işlevi değiştirmek için iki kutuyu da seçebilirsiniz.)

    Bu görünümde, işlevin tamamlanışında toplam süre (MS) ve Toplam uygulama çalışma zamanının yüzdesi gösterilir.
    **Işlev gövdesi** Ayrıca, işlev gövdesinde harcanan ve çağrılan işlevlerde harcanan süre hariç toplam süreyi (ve zaman yüzdesini) gösterir. (Bu örnekte, işlev gövdesinde 2367 MS 'tan 2389 tanesi harcanmış ve kalan 22 MS, bu işlev tarafından çağrılan harici kodda harcanmıştı).

    > [!TIP]
    > **Işlev gövdesindeki** yüksek değerler işlevin içinde bir performans sorununa işaret edebilir.

3. İşlevlerin çağrıldığı sırayı gösteren daha yüksek düzeyde bir görünüm görmek için bölmenin en üstündeki açılan listeden bir adım **Seç ' i seçin** .

    Şekildeki her numaralanmış alan, yordamdaki adımla ilgilidir.

    ::: moniker range=">=vs-2019"
    ![Tanılama araçları çağrı ağacı](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Tanılama araçları çağrı ağacı](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |Görüntü|Description|
    |-|-|
    |![1. Adım](../profiling/media/ProcGuid_1.png "ProcGuid_1")|CPU kullanım çağrısı ağaçlarında en üst düzey düğüm bir sözde düğümdür|
    |![2. Adım](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Çoğu uygulamalarda, [dış kodu göster](#view-external-code) seçeneği devre dışı bırakıldığında, ikinci düzey düğüm, uygulamayı başlatan ve durduran sistem ve çerçeve kodunu içeren bir **[Dış kod]** düğümüdür, Kullanıcı arabirimini çizer, iş parçacığı zamanlamasını denetler ve uygulamaya diğer alt düzey hizmetler sağlar.|
    |![3. Adım](../profiling/media/ProcGuid_3.png "ProcGuid_3")|İkinci düzey düğümün alt öğeleri, ikinci düzey sistem ve Framework kodu tarafından çağrılan veya oluşturulan kullanıcı kodu yöntemleri ve zaman uyumsuz yordamlardır.|
    |![4. adım](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Bir metodun alt düğümleri yalnızca üst yöntemin çağrıları için veri içerir. **Dış kodu göster** devre dışı bırakıldığında, uygulama yöntemleri bir **[Dış kod]** düğümü de içerebilir.|

    Sütun değerleri hakkında daha fazla bilgi aşağıda verilmiştir:

    - **Toplam CPU** , işlev tarafından ne kadar iş yapıldığını ve onun tarafından çağrılan işlevleri gösterir. Yüksek toplam CPU değerleri en pahalı olan işlevlere işaret edilir.

    - **Self CPU** , işlev gövdesinde kod tarafından yapılan çalışmanın ne kadar iş yaptığını gösterir ve bu, tarafından çağrılan işlevler tarafından gerçekleştirilen iş hariç olur. Yüksek **kendı CPU** değerleri işlevin içinde bir performans sorununa işaret edebilir.

    - **Modüller** İşlevi içeren modülün adı veya [Dış kod] düğümündeki işlevleri içeren modül sayısı.

    ::: moniker range=">=vs-2019"
    Çağrı ağacı görünümünde en yüksek CPU yüzdesini kullanan işlev çağrılarını görmek için, **etkin yolu genişlet**' e tıklayın.

    ![Tanılama araçları etkin yolu](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > çağrı ağacında "bozuk" kod veya "tasene yığın" olarak işaretlenen kodu görürseniz, bu durum Windows (ETW) olaylarının olay izlemenin büyük olasılıkla bırakılmakta olduğunu gösterir. Sorunu çözmek için ikinci kez aynı izlemeyi toplamayı deneyin.

## <a name="view-external-code"></a>Dış kodu görüntüle

Dış kod, System ve Framework bileşenlerinde yazdığınız kod tarafından yürütülen işlevlerdir. Dış kod, uygulamayı başlatıp durduran, Kullanıcı arabirimini çizdiğiniz, iş parçacığı denetleyen ve diğer alt düzey Hizmetleri uygulamaya sağlayan işlevleri içerir. Çoğu durumda, harici kod ile ilgilenmezsiniz ve CPU kullanımı aracı bir Kullanıcı yönteminin dış işlevlerini tek bir **[harici kod]** düğümüne toplar.

Dış kodun çağrı yollarını görüntülemek istiyorsanız, **filtre görünümü** listesinden **dış kodu göster** ' i seçin ve ardından **Uygula**' yı seçin.

![Filtre görünümü ' ne ve ardından dış kodu göster ' i seçin](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

Çok sayıda dış kod çağrı zincirinin derin iç içe geçmiş olduğunu unutmayın. böylece, Işlev adı sütununun genişliği, bilgisayar izlemelerinin en büyük bir bütün boyutunu aşabilirler. Bu durumda, işlev adları **[...]** olarak gösterilir.

Aradığınız düğümü bulmak için arama kutusunu kullanın, ardından verileri görünüme getirmek için yatay kaydırma çubuğunu kullanın.

> [!TIP]
> Windows işlevleri çağıran harici kodu profilleriniz varsa en güncel olduğundan emin olmanız gerekir. *pdb* dosyaları. Bu dosyalar olmadan rapor görünümleriniz, Windows zor olan işlev adlarını listelemektedir. Size gereken dosyalara sahip olduğundan emin olmak için bkz. Hata ayıklayıcısında sembol [(.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)ve kaynak dosyaları belirtme.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide CPU kullanım verilerini toplamayı ve analiz etme hakkında bilgi edinebilirsiniz. Profil oluşturma araçlarına [ilk bakış adımlarını](../profiling/profiling-feature-tour.md)tamamladınız, uygulamalarınız için bellek kullanımını analiz etme adımlarını hızlı bir şekilde incelemeniz iyi olabilir.

> [!div class="nextstepaction"]
> [Visual Studio’da bellek kullanımının profilini oluşturma](../profiling/memory-usage.md)
