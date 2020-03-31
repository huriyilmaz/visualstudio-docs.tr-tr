---
title: Uygulamalarınızdaki CPU kullanımını ölçün
description: Hata ayıklama tümleşik tanılama araçlarını kullanarak uygulamanızdaki CPU performans sorunlarını analiz edin.
ms.custom: seodec18
ms.date: 04/03/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ac7d23c1d4cb245366ecf03c1a8a0e67b11cb55
ms.sourcegitcommit: 0ba0cbff77eac15feab1a73eeee3667006794b29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80412019"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>CPU kullanımını analiz ederek uygulama performansını ölçme

Uygulamanızdaki performans sorunlarını çözümlemek için Visual Studio profil oluşturma araçlarını kullanabilirsiniz. Bu makalede, uygulamanız için performans verileri elde etmek için Tanılama Araçları'nın **CPU Kullanımı** sekmesinin nasıl kullanılacağı gösterilmektedir.

Hata ayıklama duraklatıldığında, **CPU Kullanım** aracı uygulamanızda çalıştırılabilen işlevler hakkında bilgi toplar. Araç, işi gerçekleştiren işlevleri listeler ve örnekleme oturumunun belirli kesimlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar.

Tanılama hub'ı, tanılama oturumunuzu çalıştırmak ve yönetmek için size birçok seçenek sunar. **CPU Kullanımı** size ihtiyacınız olan verileri [vermezse, diğer profil oluşturma araçları](../profiling/profiling-feature-tour.md) size yardımcı olabilecek farklı türde bilgiler sağlar. Çoğu durumda, uygulamanızın performans darboğazı, bellek, kullanıcı arabirimi oluşturma veya ağ isteği süresi gibi CPU'nuz dışında başka bir şeyden kaynaklanabilir. Tanılama hub'ı, bu tür verileri kaydetmek ve çözümlemek için size birçok seçenek sunar.

> [!Important]
> Tanılama Araçları, Visual Studio'da ASP.NET ve yerel/C++ geliştirme dahil .NET geliştirme için desteklenir.

Bu makalede, normal hata ayıklama iş akışınızda CPU kullanımını çözümlemeyi tartışacağız. Cpu kullanımını ekli bir hata ayıklayıcı olmadan veya çalışan bir uygulamayı hedefleyerek de analiz edebilirsiniz - [Run profiling tools with or without the debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)daha fazla bilgi için [bkz.](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) Ayrıca başka bir profil oluşturma aracı kullanabilirsiniz, [PerfTips](../profiling/perftips.md), kod üzerinden adım ve tamamlamak için belirli işlevleri veya kod blokları ne kadar sürdüğünü belirlemek için.

Profil oluşturma araçlarını Windows 7 ve sonraki hata ayıklama olmadan kullanabilirsiniz. Windows 8 ve daha sonra hata ayıklama **(Tanılama Araçları** penceresi) ile profil oluşturma araçları çalıştırmak için gereklidir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * CPU kullanım verilerini toplama
> * CPU kullanım verilerini analiz edin

## <a name="step-1-collect-profiling-data"></a>Adım 1: Profil oluşturma verilerini toplama

1. Visual Studio'da hata ayıklamak istediğiniz projeyi açın ve CPU kullanımını incelemek istediğiniz noktada uygulamanızda bir kesme noktası ayarlayın.

2. Çözümlemek istediğiniz işlevin veya kod bölgesinin sonunda ikinci bir kesme noktası ayarlayın.

    İki kesme noktası ayarlayarak, veri toplamayı çözümlemek istediğiniz kod bölümleriyle sınırlayabilirsiniz.

3. **Tanılama Araçları** penceresi, siz kapatmadığınız sürece otomatik olarak görüntülenir. Pencereyi yeniden açmak için **Hata Ayıklama** > **Windows** > **Show Tanılama Araçları'nı**tıklatın.

4. Araç çubuğundaki **Araçları Seç** ayarı ile **CPU Kullanımı,** [Bellek Kullanımı](../profiling/Memory-Usage.md)veya her ikisini de görünüp görünmeyeceğinizi seçebilirsiniz. Visual Studio Enterprise'ı çalıştırıyorsanız, IntelliTrace in **Tools** > **Options** > **IntelliTrace'i**etkinleştirebilir veya devre dışı kullanabilirsiniz.

     ![Tanılama Araçlarını Göster](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     Biz esas olarak CPU kullanımı bakıyor olacak, bu yüzden **CPU Kullanımı** etkin olduğundan emin olun (varsayılan olarak etkindir).

5. **Hata Ayıklama** > **Başlat Hata Ayıklama'yı** (veya araç çubuğunda **başlat'ı** veya **F5'i)** tıklatın.

     Uygulama yüklemeyi bitirdiğinde, Tanılama Araçlarının Özet görünümü görüntülenir. Pencereyi açmanız gerekiyorsa, **Hata Ayıklama** > **Windows** > **Show Tanılama Araçları'nı**tıklatın.

     ![Tanılama Araçları Özet Sekmesi](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     Olaylar hakkında daha fazla bilgi için [Tanılama Araçları penceresinin Olaylar sekmesini arama ve filtreleme bölümüne](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)bakın.

6. İlk kesme noktanızın vurulmasına neden olacak senaryoyu çalıştırın.

7. Hata ayıklama duraklatılmış olsa da, CPU Kullanım verilerinin toplanmasını etkinleştirin ve ardından **CPU Kullanım** sekmesini açın.

     ![Tanılama Araçları CPU profil oluşturmayı etkinleştirin](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfiling")

     **Cpu Profili Kaydet'i**seçtiğinizde, Visual Studio işlevlerinizi kaydetmeye başlar ve bunların yürütülmesi ne kadar sürer. Toplanan bu verileri yalnızca uygulamanız bir kesme noktasında durdurulduğunda görüntüleyebilirsiniz.

8. Uygulamayı ikinci kesme noktanıza çalıştırmak için F5 tuşuna basın.

     Şimdi, uygulamanız için özellikle iki kesme noktası arasında çalışan kod bölgesi için performans verilerine sahipsiniz.

     Profil oluşturucu iş parçacığı verilerini hazırlamaya başlar. Bitmesini bekle.

     ![Diagnostik Araçları İplik Hazırlama](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     CPU Kullanımı aracı raporu **CPU Kullanımı** sekmesinde görüntüler.

     ![Tanılama Araçları CPU Kullanım Sekmesi](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. Çözümlemek için daha özel bir kod bölgesi seçmek istiyorsanız, CPU zaman çizelgesinde bir bölge seçin (profil oluşturma verilerini gösteren bir bölge olmalıdır).

     ![Tanılama Araçları Zaman Dilimi Ni Seçme](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     Bu noktada, verileri çözümlemeye başlayabilirsiniz.

     > [!TIP]
     >  Performans sorunlarını belirlemeye çalışırken, birden çok ölçüm alın. Performans doğal olarak çalıştırılacak kadar değişir ve kod yolları genellikle DL'lerin yüklenmesi, JIT derleme yöntemleri ve önbellekleri başlatma gibi tek seferlik başlatma çalışmaları nedeniyle ilk kez çalıştıklarında daha yavaş çalıştırılabın. Birden çok ölçüm alarak, gösterilen ölçümün aralığı ve ortancası hakkında daha iyi bir fikir edinebilirsiniz, bu da kod alanının sabit durum performansıyla ilk kez karşılaştırmanızı sağlar.

## <a name="step-2-analyze-cpu-usage-data"></a>Adım 2: CPU kullanım verilerini analiz edin

CPU Kullanımı kapsamındaki işlevlerin listesini inceleyerek, en çok iş yapan işlevleri tanımlayarak ve sonra her birine daha yakından göz atarak verilerinizi çözüme güncellemenizi öneririz.

1. İşlev listesinde, en çok iş yapan işlevleri inceleyin.

    ![Tanılama Araçları CPU Kullanım Fonksiyonu Listesi](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > İşlevler, en çok işi yapanlarla başlayarak sırayla listelenir (çağrı sırasına göre değillerdir). Bu, en uzun çalışan işlevleri hızla belirlemenize yardımcı olur.

2. İşlev listesinde, çok fazla iş yapan uygulama işlevlerinizden birini çift tıklatın.

    Bir işlevi çift tıklattığınızda, **Arayan/Çağrı** görünümü sol bölmede açılır.

    ![Tanılama Araçları Arayan Callee Görünümü](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    Bu görünümde, seçili işlev başlıkta ve **Geçerli İşlev** kutusunda (GetNumber, bu örnekte) görünür. Geçerli işlev olarak adlandırılan **işlev, Arama İşlevleri**altında solda gösterilir ve geçerli işlev tarafından çağrılan işlevler sağdaki **Çağrı Işlevleri** kutusunda gösterilir. (Geçerli işlevi değiştirmek için her iki kutuyu seçebilirsiniz.)

    Bu görünüm, toplam uygulamanın tamamlanma süresinin (ms) ve genel uygulamanın çalışma süresinin yüzdesini gösterir.
    **Fonksiyon Gövdesi** ayrıca, arama ve çağrılan işlevler dışında işlev gövdesinde harcanan toplam süreyi (ve zaman yüzdesini) gösterir. (Bu örnekte, 2389 ms'den 2367'si işlev gövdesinde, geri kalan 22 ms ise bu işlev tarafından çağrılan dış kodda harcandı).

    > [!TIP]
    > **İşlev Gövdesindeki** yüksek değerler, işlevin kendi içinde bir performans darboğazına işaret edebilir.

3. Işlevlerin çağrıldığı sırayı gösteren daha üst düzey bir görünüm görmek için bölmenin üst kısmındaki açılır listeden **Çağrı Ağacı'nı** seçin.

    Şekildeki her numaralanmış alan yordamdaki bir adımla ilgilidir.

    ::: moniker range=">=vs-2019"
    ![Tanılama Araçları Çağrı Ağacı](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Tanılama Araçları Çağrı Ağacı](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |||
    |-|-|
    |![1. Adım](../profiling/media/ProcGuid_1.png "ProcGuid_1")|CPU Kullanımı çağrı ağaçlarındaki üst düzey düğüm bir sözde düğümdür|
    |![2. Adım](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Çoğu uygulamada, [Dış Kodu Göster](#view-external-code) seçeneği devre dışı bırakıldığında, ikinci düzey düğüm, uygulamayı başlatan ve durduran, kullanıcı ayını çizen, iş parçacığı zamanlamasını kontrol eden ve uygulamaya diğer düşük düzeyli hizmetleri sağlayan sistem ve çerçeve kodunu içeren bir **[Dış Kod]** düğümüdür.|
    |![3. Adım](../profiling/media/ProcGuid_3.png "ProcGuid_3")|İkinci düzey düğümün alt ları, ikinci düzey sistem ve çerçeve kodu tarafından çağrılan veya oluşturulan kullanıcı kodu yöntemleri ve eşzamanlı yordamlarıdır.|
    |![Adım 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Yöntemin alt düğümleri yalnızca üst yöntemin çağrıları için veri içerir. **Dış Kodu Göster** devre dışı bırakıldığında, uygulama yöntemleri bir **[Dış Kod]** düğümü de içerebilir.|

    Sütun değerleri hakkında daha fazla bilgi aşağıda verilmiştir:

    - **Toplam CPU,** işlev ve onun tarafından çağrılan işlevler tarafından ne kadar iş yapıldığını gösterir. Yüksek toplam CPU değerleri, genel olarak en pahalı işlevleri gösterir.

    - **Self CPU,** işlev gövdesindeki kod tarafından ne kadar iş yapıldığını gösterir, bu işlevler tarafından çağrılan işlevler tarafından yapılan iş hariç. Yüksek **Self CPU** değerleri, işlevin kendi içinde bir performans darboğazını gösterebilir.

    - **Modüller** İşleviçeren modülün adı veya [Dış Kod] düğümündeki işlevleri içeren modül sayısı.

    ::: moniker range=">=vs-2019"
    Çağrı ağacı görünümünde CPU'nun en yüksek yüzdesini kullanan işlev çağrılarını görmek **için, Sıcak Yolu Genişlet'i**tıklatın.

    ![Teşhis Araçları Sıcak Yol](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > Çağrı ağacında "bozuk" kod veya "çözülemeyen yığın" olarak işaretlenmiş kod görürseniz, bu, Windows için Olay İzleme (ETW) olaylarının büyük olasılıkla bırakıldığını gösterir. Sorunu gidermek için aynı izlemeyi ikinci kez toplamayı deneyin.

## <a name="view-external-code"></a>Dış kodu görüntüleme

Dış kod, yazdığınız kod tarafından yürütülen sistem ve çerçeve bileşenlerindeki işlevlerdir. Dış kod, uygulamayı başlatan ve durduran, UI'yi çizen, iş parçacığı nı kontrol eden ve uygulamaya diğer düşük düzeyli hizmetleri sağlayan işlevleri içerir. Çoğu durumda, dış kodla ilgilenmezsiniz ve bu nedenle CPU Kullanım aracı bir kullanıcı yönteminin dış işlevlerini tek bir **[Dış Kod]** düğümünde toplar.

Harici kodun çağrı yollarını görüntülemek istiyorsanız, **Filtre görünüm** listesinden Dış **Kodu Göster'i** seçin ve ardından **Uygula'yı**seçin.

![Filtre Görünümü'ni seçin, ardından Dış Kodu Göster](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

İşlev Adı sütununun genişliğinin bilgisayar monitörlerinin en büyüğü dışındaki tüm ekran genişliğini aşabilmesi için birçok dış kod çağrı zincirinin derinden iç içe geçtiğine dikkat edin. Bu durumda, işlev adları **[...]** olarak gösterilir.

Aradığınız düğümü bulmak için arama kutusunu kullanın ve ardından verileri görüntülemek için yatay kaydırma çubuğunu kullanın.

> [!TIP]
> Windows işlevlerini çağıran harici kodun profilini çıkartırsanız, en güncel koda sahip olduğunuzdan emin olmalısınız. *pdb* dosyaları. Bu dosyalar olmadan, rapor görünümleriniz şifreli ve anlaşılması zor Windows işlev adlarını listeler. İhtiyacınız olan dosyalara sahip olduğundan emin olmak için [Specify symbol (.pdb) and source files in the debugger](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)bkz.

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, CPU kullanım verilerini nasıl toplayıp analiz edeceğiz öğrendiniz. [Profil oluşturma araçlarına ilk bakışı](../profiling/profiling-feature-tour.md)tamamladıysanız, uygulamalarınızdaki bellek kullanımını nasıl analiz ettiğinize hızlıca bakmak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio’da bellek kullanımının profilini oluşturma](../profiling/memory-usage.md)
