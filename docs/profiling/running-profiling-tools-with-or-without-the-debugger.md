---
title: Hata ayıklayıcılı veya hata ayıklayıcıolmadan profil oluşturma araçlarını çalıştırın | Microsoft Dokümanlar
ms.date: 04/02/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf544b3bec9b492f1d1669549ba5501a52f7d5f2
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638795"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçları çalıştırma

Visual Studio performans ölçümü ve profil oluşturma araçları sunar. **CPU Kullanımı** ve **Bellek Kullanımı**gibi bazı araçlar hata ayıklayıcıyla veya hata ayıklayıcı olmadan ve Release veya Hata Ayıklama yapılandırmalarında çalıştırılabilir. **Uygulama Zaman Çizelgesi** gibi Performans **Profiler** araçları Hata Ayıklama veya Sürüm yapılarında çalıştırılabilir. **Tanılama Araçları** penceresi ve **Olaylar** sekmesi gibi hata ayıklama tümleşik araçları yalnızca hata ayıklama oturumları sırasında çalışır.

>[!NOTE]
>Hata ayıklama olmayan performans araçlarını Windows 7 ve sonraki araçlarla kullanabilirsiniz. Hata ayıklama tümleşik profil oluşturma araçlarını çalıştırmak için Windows 8 veya daha sonra olması gerekir.

Hata ayıklayıcı olmayan **Performans Profilcisi** ve hata ayıklayıcı tümleşik **Tanı Araçları** farklı bilgi ve deneyimler sağlar. Hata ayıklama tümleşik araçları, kesme noktalarını ve değişken değerleri gösterir. Hata ayıklama olmayan araçlar, sonuçları son kullanıcı deneyimine daha yakın sağlar.

Hangi araçların ve sonuçların kullanılacağına karar vermenize yardımcı olmak için aşağıdaki noktaları göz önünde bulundurun:

- Dosya G/Ç veya ağ yanıt verme sorunları gibi dış performans sorunları, hata ayıklayıcı veya hata ayıklayıcı olmayan araçlarda çok farklı gözükmez.
- CPU yoğun aramaların neden olduğu sorunlar için, Sürüm ve Hata Ayıklama yapıları arasında önemli performans farklılıkları olabilir. Sorunun Sürüm oluştururda var olup olmadığını denetleyin.
- Sorun yalnızca Hata Ayıklama oluşturursırasında oluşursa, büyük olasılıkla hata ayıklama olmayan araçları çalıştırmanız gerekmez. Sürüm oluşturma sorunları için hata ayıklama araçlarının daha fazla araştırma için yardımcı olup olmayacağına karar verin.
- Sürüm yapıları, işlev çağrıları ve sabitleri oluşturma, kullanılmayan kod yollarını budama ve değişkenleri hata ayıklayıcı tarafından kullanılamayacak şekilde depolama gibi optimizasyonlar sağlar. Hata ayıklama tümleşik araçlardaki performans sayıları daha az doğrudur, çünkü Hata Ayıklama oluşturur bu optimizasyonlar eksikliği.
- Hata ayıklama, özel durum ve modül yük olaylarını engelleme gibi gerekli hata ayıklama işlemlerini yaptığı için performans sürelerini değiştirir.
- **Performans Profiler** araçlarında sürüm oluşturma performans numaraları en kesin ve doğrudur. Hata ayıklama ile tümleşik araç sonuçları, hata ayıklamayla ilgili diğer ölçümlerle karşılaştırmak için en yararlıdır.

CPU Kullanımı için, komut satırı araçlarını kullanarak aracı uzak bir makinede çalıştırabilirsiniz.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a>Hata ayıklama sırasında profil oluşturma verilerini toplama

**Hata** > Ayıklama**Başlat Hata Ayıklama'yı** seçerek veya **F5**tuşuna basarak Visual Studio'da hata ayıklamaya başladığınızda, **Tanılama Araçları** penceresi varsayılan olarak görüntülenir. El ile açmak için **Hata Ayıklama** > **Windows** > **Show TanıLama Araçları'nı**seçin. **Tanılama Araçları** penceresi olaylar, işlem belleği ve CPU kullanımı hakkındaki bilgileri gösterir.

![Tanı Araçları](../profiling/media/diagnostictools-update1.png "Tanı Araçları")

- **Bellek Kullanımı** veya CPU **Kullanımı**görüntülemek için olup olmadığını seçmek için araç çubuğunda **Ayarlar** simgesini kullanın.

- **Tanılama Araçları Özellik Sayfalarını** daha fazla seçenekle açmak için **Ayarlar** açılır **bölümündeayarlar'ı** seçin.

- Visual Studio Enterprise'ı çalıştırıyorsanız, Visual Studio **Tools** > **Options** > **IntelliTrace**altında IntelliTrace'i etkinleştirebilir veya devre dışı kullanabilirsiniz.

Hata ayıklamayı durdurduğunuzda tanılama oturumu sona erer.

### <a name="the-events-tab"></a>Etkinlikler sekmesi

Hata ayıklama oturumu sırasında, **Tanılama Araçları** penceresinin **Olaylar** sekmesi, oluşan tanılama olaylarını listeler. Kategori önekleri: **Breakpoint,** **Dosya**ve diğerleri, listeyi bir kategori için hızla taramanıza veya önemsin olmayan kategorileri atlamanıza izin verin.

Belirli etkinlik kategorilerini seçerek veya seçerek görüntüdeki ve olmayan olayları filtrelemek için **Filtre** açılır düşüşünü kullanın.

![Tanılama Olay Filtresi](../profiling/media/diagnosticeventfilter.png "Tanılama Olay Filtresi")

Olay listesinde belirli bir dize bulmak için arama kutusunu kullanın. Dört olayla eşleşen "ad" dizesi için yapılan aramanın sonuçları aşağıda veda edilmiştir:

![Tanılama Olay Arama](../profiling/media/diagnosticseventsearch.png "Tanılama Olay Arama")

Daha fazla bilgi için [Tanılama Araçları penceresinin Olaylar sekmesini arama ve filtreleme bölümüne](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)bakın.

## <a name="collect-profiling-data-without-debugging"></a>Hata ayıklama olmadan profil oluşturma verilerini toplama

Hata ayıklama olmadan performans verileri toplamak için **Performans Profilleyici** araçlarını çalıştırabilirsiniz. Profil oluşturma araçlarından bazılarıçalıştırmak için yönetici ayrıcalıkları gerektirir. Visual Studio'yu yönetici olarak açabilir veya tanılama oturumunu başlattığınızda araçları yönetici olarak çalıştırabilirsiniz.

1. Visual Studio'da açık olan bir projeyle, çözüm yapılandırmasını **Release** olarak ayarlayın ve dağıtım hedefi olarak **Yerel Windows Hata Ayıklayıcı'yı** (veya **Yerel Makineyi)** seçin.

1. **Hata Ayıklama** > **Performans Profilleyicisi'ni**seçin veya **Alt**+**F2 tuşuna**basın.

1. Tanılama başlatma sayfasında, çalıştırmak için bir veya daha fazla araç seçin. Yalnızca proje türü, işletim sistemi ve programlama dili için geçerli olan araçlar görüntülenir. Bu tanılama oturumu için devre dışı bırakılan araçları da görmek için **tüm araçları göster'i** seçin. Seçenekleriniz bir C# UWP uygulaması için şu şekilde görünebilir:

   ![Tanılama araçlarını seçin](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. Tanılama oturumunu başlatmak için **Başlat'ı**seçin.

   Oturum çalışırken, bazı araçlar tanılama araçları sayfasında gerçek zamanlı verilerin grafiklerini görüntüler.

    ![Performans ve Tanılama Hub'ı hakkında veri toplama](../profiling/media/pdhub_collectdata.png "Hub veri toplama")

1. Tanılama oturumunu sona erdirmek için **Koleksiyonu Durdur'u**seçin.

   Analiz edilen veriler **Rapor** sayfasında görüntülenir.

Raporları kaydedebilir ve tanılama araçları başlatma **sayfasındaki Son Açılan Oturumlar** listesinden açabilirsiniz.

![Kaydedilmiş tanı oturum dosyası açma](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>Profil oluşturma raporu
 ![Tanılama araçları raporu](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![1. Adım](../profiling/media/procguid_1.png "ProcGuid_1")|Zaman çizelgesi profil oluşturma oturumunun uzunluğunu, uygulama yaşam döngüsü etkinleştirme olaylarını ve kullanıcı işaretlerini gösterir.|
|![2. Adım](../profiling/media/procguid_2.png "ProcGuid_2")|Mavi çubukları sürükleyip zaman çizelgesinde bir bölgeyi seçerek, raporu zaman çizelgesinin bir bölümüyle sınırlandırabilirsiniz.|
|![3. Adım](../profiling/media/procguid_3.png "ProcGuid_3")|Her tanılama aracı bir veya daha fazla ana grafik görüntüler. Tanılama oturumunuzda birden fazla araç varsa, tüm ana grafikler görüntülenir.|
|![Adım 4](../profiling/media/procguid_4.png "ProcGuid_4")|Her aracın ayrı grafiklerini daraltabilir ve genişletebilirsiniz.|
|![5. Adım](../profiling/media/procguid_6.png "ProcGuid_6")|Veriler birden fazla araç içeriyorsa, araç ayrıntıları sekmeler altında toplanır.|
|![6. Adım](../profiling/media/procguid_6a.png "ProcGuid_6a")|Raporun alt yarısında her araç için bir veya daha fazla ayrıntı görünümü gösterilir. Zaman çizelgesinin bölgelerini seçerek görünümü filtreleyebilirsiniz.|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Yüklü veya çalıştırılan uygulamalarda tanılama oturumları çalıştırma

Uygulamanızı Visual Studio projesinden başlatmanın yanı sıra, alternatif hedefler üzerinde tanılama oturumları da çalıştırabilirsiniz. Örneğin, Windows App Mağazası'ndan yüklenen bir uygulamadaki performans sorunlarını tanılamak isteyebilirsiniz. Performans Profilcisi'nde, **Hedef Değiştir'in**altındaki açılır listeden seçin.

![Tanılama araçları analiz hedefini seçin](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

Zaten yüklü olan uygulamaları başlatabilir veya tanılama araçlarını zaten çalışmakta olan uygulamalara ve işlemlere ekleyebilirsiniz.

Çözümleme hedefiniz olarak **Yürütülebilir'i** seçerseniz, yerel veya uzak bir makinede *bir .exe'ye* giden yolu girebilirsiniz. Her iki durumda *da,.exe* yerel olarak çalışır. Ancak Visual Studio'da çözümü açarak uygulamanızın profilini oluşturmanızı öneririz.

Bir UWP uygulaması **için, Çalışan Uygulama** veya **Yüklü Uygulama'yı**seçtiğinizde, uygulamayı belirtilen dağıtım hedefindeki uygulamaları bulan bir listeden seçersiniz. Bu hedef yerel veya uzak bir makine olabilir. Uzak bir makinede bir UWP uygulamasının profilini çıkarmak için **Uzak Bağlantılar** iletişim kutusunda **Evrensel (Şifrelenmemiş Protokol)** seçeneğini seçmeniz gerekir.

![Tanı için çalışan veya yüklü bir uygulama seçin](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

> [!NOTE]
> Profil oluşturma araçlarının uzaktan kullanılmasını gerektiren diğer senaryolar için [bkz.](../profiling/profile-apps-from-command-line.md) CPU Kullanımı ve .NET Nesne Ayırma aracı ile komut satırı araçlarını kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

Tanılama geliştirme ekibinin blog gönderileri ve MSDN makaleleri şunlardır:
- [MSDN Dergisi: Visual Studio 2015'te Hata Ayıklarken Performansı Analiz Edin](https://msdn.microsoft.com/magazine/dn973013.aspx)

- [MSDN Dergisi: Sorunları Daha Hızlı Teşhis Etmek Için IntelliTrace'i Kullanın](https://msdn.microsoft.com/magazine/dn973014.aspx)

- [Blog yazısı: Visual Studio 2015 Bellek Kullanım Aracı ile Olay Handler Sızıntıları Tanılama](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)

- [Video: Microsoft Visual Studio Ultimate 2015'te IntelliTrace ile Tarihsel Hata Ayıklama](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)

- [Video: Visual Studio 2015 Kullanarak Performans Sorunlarını Ayıklama](https://channel9.msdn.com/Events/Build/2015/3-731)

- [PerfTips: Visual Studio ile Hata Ayıklama sırasında bir bakışta Performans Bilgileri](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

- [Visual Studio 2015'te Tanılama Araçları hata ayıklama penceresi](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)

- [IntelliTrace in Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
