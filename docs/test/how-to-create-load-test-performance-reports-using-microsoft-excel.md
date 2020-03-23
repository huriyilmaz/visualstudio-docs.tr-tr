---
title: Microsoft Excel'i kullanarak Yük Testi Performans Raporları Oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8134d2652c1654a65ac303838bd1209a5d061bd0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589077"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Nasıl? Microsoft Excel'i kullanarak yük testi performans raporları oluşturma

İki veya daha fazla test sonucuna dayanan Microsoft Excel yük testi raporları oluşturabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

İki tür yük testi raporu mevcuttur:

- **Karşılaştırmayı çalıştır** Bu, tablolar ve çubuk grafikler kullanarak iki yük testi sonuçlarından elde edilen verileri karşılaştıran bir rapor kümesi oluşturur.

- **Trend** İki veya daha fazla yük testi sonucu üzerinde eğilim çözümlemesi oluşturabilirsiniz. Sonuçlar satır grafikleri kullanılarak görüntülenir, ancak veriler pivot tablolarda kullanılabilir.

> [!TIP]
> Ayrıca, özet görünümünden, grafik görünümünden ve tablo görünümünden verileri kopyalayıp yapıştırarak Microsoft Word raporlarını el ile oluşturabilirsiniz. Bkz. [Nasıl: Microsoft Word'ü kullanarak bir yük testi performans raporu el ile oluşturun.](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md)

Her iki rapor da performans verilerini hissedarlarla paylaşmak ve sistemin genel performansının ve sağlığının iyiye mi yoksa kötüye mi gidiyorsa iletmek için kullanılabilir.

Rapor tanımları yük testi veritabanında depolanır. Bir rapor kaydedildiğinde, raporun tanımı veritabanına kaydedilir ve daha sonra yeniden kullanılabilir.

Ayrıca, Excel çalışma kitabı hissedarlarla paylaşılabilir, böylece hissedarlar raporu görmek için veritabanına bağlanmak zorunda kalmaz.

> [!NOTE]
> Excel çalışma kitabını paylaşabilirsiniz; ancak, yalnızca Görsel Studio'yu makinelerine yükleyen kullanıcılar elektronik tablolardan herhangi birini değiştirebilir. Diğer kullanıcılar **Office** şeridinde **Yük Testi Raporu** seçeneğini görmez, ancak çalışma kitabını görüntüleyebilirler.

Aşağıdaki örnek, işlem (Update Cart) hızındaki düşüş ile (%Processor) sayacının dejenerasyonu arasında bir korelasyon gösteren bir rapor örneğidir. Bu, veritabanı veya ağ yerine uygulama kodundaki olası bir soruna işaret ediyor ve ASP.NET Profiler'ı kullanarak tanıkoymak için iyi bir adaydır.

![Uygulama kodundaki olası sorun](../test/media/lt_excel.png)

Excel raporları, araç çubuğundaki **Excel Raporu Oluştur** düğmesini kullanarak Veya **Office** şeridinin Yük Testi sekmesindeki Yük **Testi** **Raporu** seçeneğini kullanarak Excel'den Yük **Testi Çözümleyicisi'nde**oluşturulabilir.

> [!NOTE]
> Bir yük testine yorum eklerseniz, bunlar Excel raporunda görünür.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Excel'i kullanarak yük testi karşılaştırma raporları oluşturmak için

1. Bir rapor oluşturmadan önce bir yük testi çalıştırmanız gerekir.

2. Excel yük testi raporlarını iki şekilde oluşturabilirsiniz:

   - Bir yük testini tamamladıktan sonra, **Load Test Sonuçları** sayfasında araç çubuğundaki Excel Raporu **Oluştur** düğmesini seçin.

      > [!NOTE]
      > **Web Performans Testi Sonuçları Görüntüleyici** araç çubuğunda Excel Raporu **Oluştur** düğmesi devre dışı bırakılmışsa, etkinleştirilmeden önce Microsoft Excel'i bir kez çalıştırmanız gerekebilir. Visual Studio Enterprise yüklendiğinde, Visual Studio Enterprise yük testi eklentisi Microsoft Excel için bilgisayarınıza kopyalanır; ancak, eklenti için yükleme işlemini tamamlamak için Microsoft Excel çalıştırılması gerekir.

      Microsoft **Excel, Yük Testi Raporu Oluştur Sihirbazı**ile açılır.

   **Veya**

   1. Microsoft Excel'i açın, **Office** şeridindeki **Yük Testi** sekmesini seçin ve ardından Test **Raporunu Yükle'yi**seçin.

       **Yük Testi Raporu Oluştur Sihirbazı** görüntülenir.

   2. Yük **testleri** sayfasını içeren Select veritabanında, **Sunucu adı altında,** yük testi sonuçlarını içeren sunucunun adını yazın.

   3. Veritabanı **adı** açılır listesinde, yük testi sonuçlarını içeren veritabanını seçin.

3. Rapor **sayfanızı nasıl oluşturmak istiyorsunuz,** rapor **oluştur'un** seçildiğini doğrulayın ve **İleri'yi**seçin.

4. Sayfa **oluşturmak istediğiniz rapor türünde,** **Çalıştır karşılaştırmasının** seçildiğini doğrulayın ve **İleri'yi**seçin.

5. Yükle **test raporu ayrıntıları** gir sayfasında, **Rapor Adı'na**raporunuz için bir ad yazın.

6. Raporu oluşturmak istediğiniz yük testini seçin ve **İleri'yi**seçin.

7. Rapor **sayfanızın çalıştırmasını** seç'te, **rapora eklemek için bir veya daha fazla çalıştırma seç'in**altında, raporda karşılaştırmak istediğiniz iki yük testi sonucu seçin ve **İleri'yi**seçin.

   > [!NOTE]
   > Yalnızca iki yükleme testi sonucu yla ilgili bir karşılaştırma raporu oluşturabilirsiniz. Bir yük testi sonucu veya ikiden fazla yükleme testi sonucu seçerseniz, bir uyarı iletisi görüntülenir.

8. Rapor **sayfanızın sayaçlarını** seç'te, **rapora ekleyebileceğiniz** bir veya daha fazla sayaç seç'in altında, raporunuzu özelleştirmek için genişletilebilir bir sayaç listesi kullanılabilir. Raporda seçili iki test çalışmasından karşılaştırmak istediğiniz sayaçları seçin ve **Finish'i**seçin.

9. Excel çalışma kitabı raporu aşağıdaki elektronik tablo sekmeleri ile oluşturulur:

   - **İçerik Tablosu** - Yük testi raporu adını görüntüler ve rapordaki çeşitli sekmelere bağlantılar içeren bir içerik tablosu sağlar.

   - **Çalışır -** Raporda iki çalıştırmanın karşılaştırıldığı ayrıntıları sağlar.

   - **Test Karşılaştırması -** Karşılaştırılan iki çalıştırma arasındaki performans gerilemeleri ve iyileştirmeler hakkında çubuk grafik ayrıntıları sağlar.

   - **Sayfa Karşılaştırması -** Test çalışır çeşitli sayfalarda iki çalışır arasında çubuk grafik ve yüzde performans karşılaştırma verileri sağlar.

   - **Makine Karşılaştırma -** Kullanılan makineleri temel alan iki çalıştırma arasında karşılaştırma verileri sağlar.

   - **Hata Karşılaştırması -** İki çalıştırma ile oluşum sayısı arasında karşılaşılan hata türlerini karşılaştırır.

     > [!TIP]
     > Daha iyi raporlar için yük testlerinde ve daha zengin raporlar sağlayan web performans testlerinde çeşitli özellikler mevcuttur. Sayfa isteğinin raporlarda sunulan iki özelliği vardır: Hedef ve Raporlama Adı. Sayfa yanıt süreleri hedefe karşı bildirilir ve raporlardaki URL yerine raporlama adı kullanılır. Bir yük testi Çalıştır Ayarları'nda, Sayaç Kümelerini Yönet altında, Bilgisayar Etiketleri özelliği rapor makinesi adlarında sunulur. Bu, raporda belirli bir makinenin rolünü açıklamak için çok yararlıdır.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Excel'i kullanarak yük testi eğilim raporları oluşturmak için

1. Bir rapor oluşturmadan önce bir yük testi çalıştırmanız gerekir.

2. Excel yük testi raporlarını iki şekilde oluşturabilirsiniz:

   - Bir yük testini tamamladıktan sonra, **Load Test Sonuçları** sayfasında araç çubuğundaki Excel Raporu **Oluştur** düğmesini seçin.

      > [!NOTE]
      > **Web Performans Testi Sonuçları Görüntüleyici** araç çubuğunda Excel Raporu **Oluştur** düğmesi devre dışı bırakılmışsa, etkinleştirilmeden önce Microsoft Excel'i bir kez çalıştırmanız gerekebilir. Visual Studio Enterprise yüklendiğinde, Visual Studio Enterprise yük testi eklentisi Microsoft Excel için bilgisayarınıza kopyalanır; ancak, eklenti için yükleme işlemini tamamlamak için Microsoft Excel çalıştırılması gerekir.

      Microsoft **Excel, Yük Testi Raporu Oluştur Sihirbazı**ile açılır.

   **Veya**

   1. Microsoft Excel'i açın, **Office** şeridindeki **Yük Testi** sekmesini seçin ve ardından Test **Raporunu Yükle'yi**seçin.

       **Yük Testi Raporu Oluştur Sihirbazı** görüntülenir.

   2. Yük **testleri** sayfasını içeren Select veritabanında, **Sunucu adı altında,** yük testi sonuçlarını içeren sunucunun adını yazın.

   3. Veritabanı **adı** açılır listesinde, yük testi sonuçlarını içeren veritabanını seçin.

3. Rapor **sayfanızı nasıl oluşturmak istiyorsunuz,** rapor **oluştur'un** seçildiğini doğrulayın ve **İleri'yi**seçin.

4. Sayfa **oluşturmak istediğiniz rapor türünde,** **Eğilim'in** seçildiğini doğrulayın ve **İleri'yi**seçin.

5. Yükle **test raporu ayrıntıları** gir sayfasında, **Rapor Adı'na**raporunuz için bir ad yazın.

6. Raporu oluşturmak istediğiniz yük testini seçin ve **İleri'yi**seçin.

7. Rapor **sayfanızın çalıştırmasını** seç'te, **rapora eklemek için bir veya daha fazla çalıştırma seç'in**altında, raporda karşılaştırmak istediğiniz yük testi sonuçlarını seçin ve **İleri'yi**seçin.

8. Rapor **sayfanızın sayaçlarını** seç'te, **rapora eklemek için bir veya daha fazla sayaç seç'in**altında, raporunuzu özelleştirmek için genişletilebilir bir sayaç listesi kullanılabilir. Eğilim analizi için karşılaştırmak istediğiniz sayaçları seçin ve **Finish'i**seçin.

9. Rapor, raporda oluşturulan çeşitli Excel çalışma kitabı sekmelerine bağlantılar içeren bir içerik tablosuyla oluşturulur. Bağlantılar, eğilim raporu için seçilen sayaçları temel adamaktadır. Örneğin, varsayılan sayaçları adım 7'de seçili bıraktıysanız, rapor, 7 adımda listelenen her sayaç için Excel'de ayrı sekmelerde sunulan veriler oluşturur. Her sayaç için oluşturulan veriler eğilim stili grafiklerde sunulur.

   > [!TIP]
   > Daha iyi raporlar için yük testlerinde ve daha zengin raporlar sağlayan web performans testlerinde çeşitli özellikler mevcuttur. Sayfa isteğinin raporlarda sunulan iki özelliği vardır: Hedef ve Raporlama Adı. Sayfa yanıt süreleri hedefe karşı bildirilir ve raporlardaki URL yerine raporlama adı kullanılır. Bir yük testi Çalıştır Ayarları'nda, Sayaç Kümelerini Yönet altında, Bilgisayar Etiketleri özelliği rapor makinesi adlarında sunulur. Bu, raporda belirli bir makinenin rolünü açıklamak için çok yararlıdır.

## <a name="net-security"></a>.NET güvenlik

Yük testi sonuçları ve raporları, bilgisayarınıza veya ağınıza karşı bir saldırı oluşturmak için kullanılabilecek hassas olabilecek bilgiler içerir. Yük testi sonuçları ve raporları bilgisayar adları ve bağlantı dizeleri içerir. Yük testi raporlarını diğer kişilerle paylaştığınızda bunun farkında olmalısınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Test karşılaştırmaları veya eğilim analizi için rapor yükü testleri sonuçları](../test/compare-load-test-results.md)
