---
title: Uygulamalarınız için CPU kullanımını ölçme
description: Hata ayıklayıcısıyla tümleşik tanılama araçlarını kullanarak uygulamanıza cpu performans sorunlarını analiz edin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084876"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>CPU kullanımını analiz ederek uygulama performansını ölçme

Hata ayıklayıcısıyla tümleşik CPU Kullanımı tanılama aracıyla hata ayıklama sırasında **performans sorunlarını** bulun.  Ayrıca, bir hata ayıklayıcısı ekli olmadan veya çalışan bir uygulamayı hedefleerek CPU kullanımını analiz edin. Daha fazla bilgi için [bkz. Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

Hata ayıklayıcı duraklatılırken, Tanılama Araçları penceresindeki **CPU** Kullanımı aracı, uygulamanıza yürütülen işlevler hakkında bilgi toplar. Araç, çalışma gerçekleştiren işlevleri listeler ve örnekleme oturumunun belirli segmentlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar.

> [!Important]
> Hata ayıklayıcısı ile tümleşik Tanılama Araçları Visual Studio, ASP.NET, ASP.NET Core ve yerel/C++ geliştirme dahil olmak üzere Visual Studio.NET geliştirmesi için de desteklemektedir. Buna karşılık Visual Studio [iş](../install/modify-visual-studio.md) yükü gereklidir. Windows 8 aracılarını hata ayıklayıcısıyla **(profil** oluşturma penceresiyle) çalıştırmak için Tanılama Araçları gerekir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * CPU kullanım verilerini toplama
> * CPU kullanım verilerini analiz etme

**CPU Kullanımı** size ihtiyacınız olan verileri vermezse, Performans Profili Oluşturucu profil [](../profiling/profiling-feature-tour.md#post_mortem) oluşturma araçları size yardımcı olacak farklı türlerde bilgiler sağlar. Çoğu durumda, cpu' dışında bellek, işleme kullanıcı arabirimi veya ağ isteği süresi gibi bir şey, uygulama performans sorununa neden olabilir.

## <a name="step-1-collect-profiling-data"></a>1. Adım: Profil oluşturma verilerini toplama

1. Hata ayıklamak istediğiniz projeyi Visual Studio cpu kullanımını incelemek istediğiniz noktada uygulamanıza bir kesme noktası ayarlayın.

2. İşlevin veya analiz etmek istediğiniz kodun bölgesi sonunda ikinci bir kesme noktası ayarlayın.

    İki kesme noktası ayarerek veri toplamayı analiz etmek istediğiniz kod bölümleriyle sınırabilirsiniz.

3. Siz **Tanılama Araçları** pencere otomatik olarak görüntülenir. Pencereyi yeniden getirmek için Hata Ayıkla'ya **tıklayın**  >  **Windows**  >  **Show Tanılama Araçları**.

4. Araç çubuğundaki Araçları Seç **ayarıyla CPU** [Kullanımı,](../profiling/Memory-Usage.md)Bellek Kullanımı veya her ikisini **birden** görüntülemeyi seçebilirsiniz. IntelliTrace'i Visual Studio Enterprise, Araçlar Seçenekleri   >    >  **IntelliTrace'de IntelliTrace'i** de etkinleştirebilirsiniz veya devre dışı abilirsiniz.

     ![Tanılama Araçlarını Göster](../profiling/media/diag-tools-select-tool.png "Diagaraçları selecttool")

     Temelde CPU kullanımına bakacağız, bu nedenle CPU Kullanımının **etkinleştirildiğinden** emin olun (varsayılan olarak etkindir).

5. Hata **AyıklamaYı**  >  **Başlat 'a** tıklayın (veya araç **çubuğunda** Başlat'a veya **F5'e tıklayın.**

     Uygulamanın yüklenmesi tamam olduğunda Tanılama Araçları'nın Özet görünümü görüntülenir. Pencereyi açmamız gerekirse, Hata Ayıkla'ya tıklayın  >  **Windows**  >  **Show Tanılama Araçları**.

     ![Tanılama Araçları Özet Sekmesi](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     Olaylar hakkında daha fazla bilgi için, Tanılama Araçları penceresinin [Olaylar sekmesini arama ve filtreleme.](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)

6. İlk kesme noktanıza isabet etmek için senaryoyu çalıştırın.

7. Hata ayıklayıcı duraklatılmışken CPU Kullanımı verilerini toplamayı etkinleştirin ve ardından CPU Kullanımı **sekmesini** açın.

     ![Tanılama Araçları CPU profili oluşturmayı etkinleştirme](../profiling/media/diag-tools-enable-cpu-profiling.png "Diagtoolsenablecpuprofil oluşturma")

     CPU Profilini **Kayded'i** Visual Studio işlevlerinizi kaydetmeye ve ne kadar süreyle yürütüleceklerini kaydetmeye başlar. Toplanan bu verileri yalnızca uygulama bir kesme noktası durdurulduğu zaman görüntüebilirsiniz.

8. Uygulamayı ikinci kesme noktanıza çalıştırmak için F5'e tıklayın.

     Şimdi, iki kesme noktası arasında çalışan kodun bölgesi için özel olarak uygulamanıza yönelik performans verilerine sahipsiniz.

     Profilleyici iş parçacığı verilerini hazırlamaya başlar. Bitimini bekleyin.

     ![Tanılama Araçları İş Parçacıklarını Hazırlama](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     CPU Kullanımı aracı raporu CPU Kullanımı **sekmesinde** görüntüler.

     ![Tanılama Araçları CPU Kullanımı Sekmesi](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. Analiz etmek için daha belirli bir kod bölgesi seçmek için CPU zaman çizelgesinde bir bölge seçin (profil oluşturma verilerini gösteren bir bölge olması gerekir).

     ![Tanılama Araçları Zaman Segmenti Seçme](../profiling/media/diag-tools-select-time-segment.png "Diagaraçları Selecttimesegment")

     Bu noktada, verileri analiz etmek için başlayabilirsiniz.

     > [!TIP]
     >  Performans sorunlarını belirlemeye çalışırken birden çok ölçüme göz atabilirsiniz. Performans, çalıştırmadan çalıştırmaya göre doğal olarak değişiklik gösterir ve kod yolları genellikle ILK çalıştırılma zamanlarının daha yavaş yürütülebilir. Bunun nedeni, DLL'lerin yüklenmesi, JIT derleme yöntemleri ve önbelleklerin başlatılma gibi tek bir kez başlatma çalışmasıdır. Birden çok ölçüm alarak, gösterilen ölçümün aralığı ve ortası hakkında daha iyi bir fikir elde edilir ve bu da bir kod alanında ilk kez yapılanla kararlı durum performansını karşılaştırmaya olanak sağlar.

## <a name="step-2-analyze-cpu-usage-data"></a>2. Adım: CPU kullanım verilerini analiz etme

CPU Kullanımı altındaki işlev listesini inceler, en çok işi yapan işlevleri belirleyip her birini daha yakından inceler ve verilerinizi analiz ederek verilerinizi analize başlamanızı öneririz.

1. İşlev listesinde, en çok işi yapan işlevleri inceler.

    ![Tanılama Araçları CPU Kullanımı İşlev Listesi](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > İşlevler, en çok işi yapanlarla (çağrı sırasına göre değil) sırayla listelenir. Bu, en uzun süre çalışan işlevleri hızlıca tanımlamanıza yardımcı olur.

2. İşlev listesinde, çok fazla iş yapan uygulama işlevlerinize çift tıklayın.

    Bir işleve çift tıklarken, **sol bölmede Arayan/Çağrılı** görünümü açılır.

    ![Tanılama Araçları Çağıran Çağrılı Görünümü](../profiling/media/diag-tools-caller-callee.png "Diagtoolscallerçağrılan")

    Bu görünümde, seçilen işlev başlığında ve Geçerli İşlev kutusunda (bu **örnekte** GetNumber) görünür. Geçerli işlevi çağıran işlev sol tarafta İşlevleri Çağırma altında gösterilir ve geçerli işlev tarafından çağrılır tüm işlevler sağ tarafta **İşlevler Çağrılı** kutusunda gösterilir. (Geçerli işlevi değiştirmek için iki kutudan birini de seçin.)

    Bu görünümde, işlevin tamamlanması için gereken toplam süre (ms) ve genel uygulama çalışma süresi yüzdesi yer a gösterir.
    **İşlev Gövdesi** ayrıca, çağrılan ve çağrılan işlevlerde harcanan süre hariç olmak üzere işlev gövdesinde harcanan toplam süre miktarını (ve zaman yüzdesini) gösterir. (Bu örnekte, 2389 ms'den 2367'sinde işlev gövdesine, kalan 22 ms ise bu işlev tarafından çağrılır dış koda harcandı).

    > [!TIP]
    > İşlev **Gövdesi'nde yüksek** değerler, işlevin içinde bir performans sorunu olduğunu gösteriyor olabilir.

3. İşlevlerin çağrıldığ sırayı gösteren daha üst düzey bir  görünüm görmek için bölmenin üst kısmında açılan listeden Çağrı Ağacı'ı seçin.

    Şekilde numaralı her alan, yordamda bir adımla ilgilidir.

    ::: moniker range=">=vs-2019"
    ![Tanılama Araçları Çağrı Ağacı](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Tanılama Araçları Çağrı Ağacı](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |Görüntü|Açıklama|
    |-|-|
    |![1. Adım](../profiling/media/ProcGuid_1.png "ProcGuid_1")|CPU Kullanımı çağrı ağaçlarında üst düzey düğüm, sözde düğüm|
    |![2. Adım](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Çoğu uygulamada, Dış [](#view-external-code) Kodu Göster seçeneği devre dışı bırakılmıştır, ikinci düzey düğüm uygulamayı başlatan ve durduran, kullanıcı arabirimini çizen, iş parçacığı zamanlamasını kontrol eden ve uygulamaya diğer alt düzey hizmetleri sağlayan sistem ve çerçeve kodunu içeren bir **[Dış Kod]** düğümü olur.|
    |![3. Adım](../profiling/media/ProcGuid_3.png "ProcGuid_3")|İkinci düzey düğümün altları, ikinci düzey sistem ve çerçeve kodu tarafından çağrılarak veya oluşturulan kullanıcı kodu yöntemleri ve zaman uyumsuz yordamlardır.|
    |![4. Adım](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Bir yöntemin alt düğümleri yalnızca üst yöntemin çağrıları için verileri içerir. Dış **Kodu Göster devre** dışı bırakılmıştır, uygulama yöntemleri bir **[Dış Kod] düğümü de** içerebilir.|

    Sütun değerleri hakkında daha fazla bilgi aşağıda vetir:

    - **Toplam CPU** işlevi tarafından ne kadar iş olduğunu ve işlev tarafından çağrılan işlevleri gösterir. Yüksek toplam CPU değerleri, genel olarak en pahalı işlevlere işaret eder.

    - **Kendi KENDINE CPU** işlevi gövdesinin kod tarafından ne kadar iş olduğunu gösterir; bu, işlev tarafından çağrılan işlevler tarafından yapılan işler hariçtir. Yüksek **Kendi Kendine CPU** değerleri, işlevin kendi içinde bir performans sorunu olduğunu gösteriyor olabilir.

    - **Modüller** İşlevi içeren modülün adı veya bir [Dış Kod] düğümünde işlevleri içeren modüllerin sayısı.

    ::: moniker range=">=vs-2019"
    Çağrı ağacı görünümünde CPU'nun en yüksek yüzdesini kullanan işlev çağrılarını görmek için, Yoğun Yolu **Genişlet'e tıklayın.**

    ![Tanılama Araçları Hot Path](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > Çağrı ağacında "bozuk" kod veya "gezilemez yığın" olarak işaretlenmiş kod görüyorsanız bu, Windows (ETW) olayları için Olay İzleme'nin büyük olasılıkla bırakıldı olduğunu gösterir. Sorunu çözmek için aynı izlemeyi ikinci kez toplamayı deneyin.

## <a name="view-external-code"></a>Dış kodu görüntüleme

Dış kod, sistem ve çerçeve bileşenlerinde bulunan ve sizin yazarak yürütülen işlevlerdir. Dış kod, uygulamayı başlatan ve durduran, kullanıcı arabirimini çizen, iş parçacığını kontrol altına alan ve uygulamaya diğer alt düzey hizmetleri sağlayan işlevleri içerir. Çoğu durumda dış kodla ilgilenmezsiniz ve bu nedenle CPU Kullanımı aracı bir kullanıcı yönteminin dış işlevlerini tek **bir [Dış Kod] düğümünde** toplar.

Dış kodun çağrı yollarını görüntülemek için Filtre görünümü listesinden **Dış** Kodu **Göster'i** seçin ve uygula'ya **tıklayın.**

![Filtre Görünümü'ne ve ardından Dış Kodu Göster'e tıklayın](../profiling/media/diag-tools-show-external-code.png "Diagaraçları Showexternalcode")

Birçok dış kod çağrısı zincirinin iç içe geçmiş olduğunu, böylece İşlev Adı sütununu genişliğinin bilgisayar izleyicilerinin en büyükleri dışında tüm ekran genişliğini aşabilir. Bu durumda işlev adları **olarak gösterilir .**

Arama kutusunu kullanarak istediğiniz düğümü bulun ve ardından verileri görünüme getirmek için yatay kaydırma çubuğunu kullanın.

> [!TIP]
> Bu işlevleri çağıran dış Windows profili gerçekleştirirsiniz, en güncel koduna sahip olduğundan emin olun. *pdb* dosyaları. bu dosyalar olmadan rapor görünümleriniz, şifreli ve anlaşılması zor Windows işlev adlarını listeler. İhtiyacınız olan dosyalara sahip olduğunuzdan emin olmak hakkında daha fazla bilgi için bkz. [hata ayıklayıcıda sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, CPU kullanım verilerini nasıl toplayacağınızı ve analiz edeceğinizi öğrendiniz. [Profil oluşturma araçlarındaki ilk görünümü](../profiling/profiling-feature-tour.md)zaten tamamladıysanız, uygulamalarınızda bellek kullanımını çözümleme hakkında hızlı bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio’da bellek kullanımının profilini oluşturma](../profiling/memory-usage.md)
