---
title: Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını | Microsoft Docs
description: Profil oluşturma araçları için kullanılabilen farklı modlar arasındaki farkları öğrenin
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9d697a96a0b91554342ba57a6265b4a087c8458a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157403"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçları çalıştırma

Visual Studio performans ölçümü ve profil oluşturma araçları sunar. CPU Kullanımı ve Bellek Kullanımı gibi bazı araçlar hata ayıklayıcıyla veya hata ayıklayıcı olmadan ve sürüm veya hata ayıklama derleme yapılandırmalarında çalışır. Tanılama Araçları penceresinde [görünen araçlar yalnızca](../profiling/profiling-feature-tour.md#measure-performance-while-debugging) bir hata ayıklama oturumu sırasında çalıştırabilirsiniz. Hata ayıklayıcı [olmadan Performans Profili Oluşturucu](../profiling/profiling-feature-tour.md#post_mortem) araçlar çalıştırabilirsiniz ve siz durdurarak toplamayı seçtikten sonra (son inceleme analizi için) sonuçları analiz edersiniz.

>[!NOTE]
>Hata ayıklayıcı olmayan performans araçlarını 7 ve sonraki bir Windows kullanabilirsiniz. Windows 8 hata ayıklayıcısıyla tümleşik profil oluşturma araçlarını çalıştırmak için bir veya daha yeni bir uygulama gerekir.

Hata ayıklayıcı olmayan Performans Profili Oluşturucu ve hata ayıklayıcı ile tümleşik Tanılama Araçları bilgi ve deneyimler sağlar. Debugger ile tümleşik araçlar değişken değerleri gösterir ve kesme noktaları kullanmana izin verir. Hata ayıklayıcı olmayan araçlar, sonuçları son kullanıcı deneyimine daha yakın bir şekilde sunar.

Hangi araçların ve sonuçların kullanılamayacaklarını karara varmanıza yardımcı olmak için aşağıdakilere dikkat edin:

- Hata ayıklayıcıyla tümleşik araç ve hata ayıklayıcı olmayan araç karşılaştırması
  - Dosyanın I/O veya ağ yanıt verme sorunları gibi dış performans sorunları, hata ayıklayıcı veya hata ayıklayıcı olmayan araçlarda çok farklı görünmüyor.
  - Hata ayıklayıcısı, özel durum ve modül yükleme olaylarını kesme gibi gerekli hata ayıklayıcı işlemlerini yaptığı için performans zamanlarını değiştirir.
  - Yayın derlemesi performans numaraları Performans Profili Oluşturucu doğru ve kesindir. Hata ayıklayıcısı ile tümleşik araç sonuçları, hata ayıklamayla ilgili diğer ölçümlerle karşılaştırmak veya hata ayıklayıcı özelliklerini kullanmak için en kullanışlıdır.
  - .NET Nesne Ayırma aracı gibi bazı araçlar yalnızca hata ayıklayıcı olmayan senaryolarda kullanılabilir.
- Hata ayıklama ve yayın derlemesi karşılaştırması
  - YOĞUN CPU kullanımına sahip çağrılardan kaynaklanan sorunlar için sürüm ve hata ayıklama derlemeleri arasında önemli performans farkları olabilir. Sorunun yayın derlemeleri içinde mevcut olup olmadığını kontrol edin.
  - Sorun yalnızca hata ayıklama derlemeleri sırasında oluşuyorsa, büyük olasılıkla hata ayıklayıcı olmayan araçları çalıştırmaya gerek olmaz. Yayın derleme sorunları için hata ayıklayıcıyla tümleşik araçlar tarafından sağlanan özelliklerin sorunu tespit etmeye yardımcı olup olmadığını seçin.
  - Yayın derlemeleri, işlev çağrılarını ve sabitlerini derleme, kullanılmayan kod yollarını ayıklama ve değişkenleri hata ayıklayıcı tarafından kullanılayacak şekilde depolama gibi iyileştirmeler sağlar. Hata ayıklama derlemeleri bu iyileştirmeleri eksik olduğundan, hata ayıklama derlemeleri performans numaraları daha az doğru olur.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Hata ayıklama sırasında profil oluşturma verilerini toplama

hata ayıklamayı hata ayıklamaya Visual Studio Hata Ayıklamayı Başlat 'ı seçerek veya F5 tuşuna basarak Tanılama Araçları  >  penceresi varsayılan olarak görünür.   El ile açmak için Hata **ayıkla'Windows**  >    >  **Show Tanılama Araçları**. Bu **Tanılama Araçları** olaylar, işlem belleği ve CPU kullanımı hakkında bilgiler gösterir.

![Tanılama Araçları ekran görüntüsü](../profiling/media/diagnostictoolswindow.png " Tanılama Araçları Penceresi")

- Araç **çubuğundaki Ayarlar** simgesini kullanarak Bellek **Kullanımı,** **UI** Analizi ve CPU Kullanımı'nın görüntü olup **olmadığını seçin.**

- Diğer **Ayarlar** sayfaları **Ayarlar** açılan listesinden **Tanılama Araçları'yi** seçin.

- IntelliTrace'i Visual Studio Enterprise Araçlar Seçenekleri   >  IntelliTrace'e gidip IntelliTrace'i **etkinleştirebilirsiniz**  >  **veya devre dışı abilirsiniz.**

Hata ayıklamayı durdurarak tanılama oturumu sona erer.

Daha fazla bilgi için bkz.

- [CPU kullanımını analiz ederek uygulama performansını ölçme](../profiling/beginners-guide-to-performance-profiling.md)
- [Visual Studio’da bellek kullanımını ölçme](../profiling/memory-usage.md)

### <a name="the-events-tab"></a>Olaylar sekmesi

Hata ayıklama oturumu sırasında, hata ayıklama penceresinin Olaylar Tanılama Araçları oluşan tanılama olaylarını listeler. Kesme *noktası,* Dosya *ve* diğer kategori ön ekleri, listeyi bir kategori için hızlıca taramanız veya önem vermeyebilirsiniz.

Belirli **olay kategorilerini** seçerek veya temizerek olayları görünüm içinde ve dışında filtrelemek için Filtre açılan listesini kullanın.

![Tanılama Olayı filtresinin ekran görüntüsü](../profiling/media/diagnosticeventfilter.png "Tanılama Olay Filtresi")

Olay listesinde belirli bir dizeyi bulmak için arama kutusunu kullanın. Dört olayla eşan dize adı *için bir* aramanın sonuçları şu şekildedir:

![Tanılama Olayı arama ekran görüntüsü](../profiling/media/diagnosticseventsearch.png "Tanılama Olay Arama")

Daha fazla bilgi için [bkz. Uygulama penceresinin Olaylar sekmesini Tanılama Araçları filtreleme.](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)

## <a name="collect-profiling-data-without-debugging"></a>Hata ayıklama olmadan profil oluşturma verileri toplama

Hata ayıklama olmadan performans verilerini toplamak için aşağıdaki Performans Profili Oluşturucu çalıştırabilirsiniz.

1. Visual Studio'da bir proje açıkken, çözüm yapılandırmasını Sürüm olarak ayarlayın ve dağıtım hedefi **olarak** Yerel Windows Hata Ayıklayıcısı (veya Yerel **Makine)** seçeneğini seçin.

1. Hata **ayıkla'Performans Profili Oluşturucu**  >  veya Alt  + **F2 tuşuna basın.**

1. Tanılama araçları başlatma sayfasında, çalıştıracak bir veya daha fazla araç seçin. Yalnızca proje türü, işletim sistemi ve programlama dili için geçerli olan araçlar gösterilir. Bu **tanılama oturumunda devre** dışı bırakılmış araçları da görmek için Tüm araçları göster'i seçin.

   ![Tanılama araçlarının ekran görüntüsü](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Tanılama oturumunu başlatmak için Başlat'ı **seçin.**

   Oturum çalışırken, bazı araçlar tanılama araçları sayfasında gerçek zamanlı verilerin grafiklerini ve veri toplamayı duraklatma ve sürdürme denetimlerini gösterir.

    ![Performans Profili Oluşturucu'da veri toplamanın ekran görüntüsü](../profiling/media/diaghubcollectdata.png "Hub veri toplama")

1. Tanılama oturumunu durdurmak için Koleksiyonu **Durdur'a seçin.**

   Analiz verileri Rapor **sayfasında** görüntülenir.

Raporları kaydedebilir ve yeni açılan oturumlar **sayfasındaki Son** Açılan Oturumlar listesinden Tanılama Araçları açabilirsiniz.

![En Son Tanılama Araçları Oturumlar listesinin ekran görüntüsü](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

Daha fazla bilgi için bkz.

- [CPU kullanımını analiz etme](../profiling/cpu-usage.md)
- [.NET kodu için bellek kullanımını analiz etme](../profiling/dotnet-alloc-tool.md)
- [Bellek kullanımını analiz etme](../profiling/memory-usage-without-debugging2.md)
- [.NET zaman uyumsuz kodunun performansını analiz etme](../profiling/analyze-async.md)
- [Veritabanı performansını analiz etme](../profiling/analyze-database.md)
- [GPU kullanımını analiz etme](../profiling/gpu-usage.md)

## <a name="collect-profiling-data-from-the-command-line"></a>Komut satırına profil oluşturma verilerini toplama

Komut satırına gelen performans verilerini ölçmek için, VSDiagnostics.exe veya Uzak Araçlar'da bulunan Visual Studio'i kullanabilirsiniz. Bu, yüklü olmayan sistemlerde performans izlemelerini yakalamak Visual Studio veya performans izlemeleri koleksiyonunun betiği için yararlıdır. Ayrıntılı yönergeler için [bkz. Komut satırıyla uygulama performansını ölçme.](../profiling/profile-apps-from-command-line.md)