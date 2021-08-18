---
title: Excel kullanarak yük testi perf raporu oluşturma
description: İki veya daha Microsoft Excel test sonuçlarını temel alan yük testi raporları oluşturma hakkında bilgi edinin. Çalıştırma karşılaştırması ve eğilim raporları oluşturabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: f40d477122bbf3fe0057fa1010b9847fa5a7cae0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075859"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Nasıl Microsoft Excel kullanarak yük testi performans raporları oluşturma

İki veya Microsoft Excel test sonuçlarını temel alan bir yük testi raporu da oluştur.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

İki tür yük testi raporu mevcuttur:

- **Çalıştırma karşılaştırması** Bu, tabloları ve çubuk grafikleri kullanarak iki yük testi sonuçlarından verileri karşılaştıran bir rapor kümesi oluşturur.

- **Eğilim** İki veya daha fazla yük testi sonucu üzerinde eğilim analizi oluştur. Sonuçlar çizgi grafikler kullanılarak görüntülenir, ancak veriler özet tablolarda kullanılabilir.

> [!TIP]
> Özet görünümü, graflar Microsoft Word tablo görünümünden verileri kopyalayıp yapıştırarak da el ile rapor oluşturabilirsiniz. Bkz. [Nasıl yapılır: yük testi performans raporunu kullanarak el ile Microsoft Word.](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md)

Her iki rapor da performans verilerini paydaşlarla paylaşmak ve sistemin genel performansının ve durumunun iyiye mi yoksa daha kötüye mi olduğunu iletmek için kullanılabilir.

Rapor tanımları yük testi veritabanında depolanır. Bir rapor kaydedilebilir, raporun tanımı veritabanına kaydedilir ve daha sonra yeniden kullanılabilir.

Ayrıca, Excel çalışma kitabı paydaşlarla paylaşarak paydaşların raporu görmek için veritabanına bağlanmasına gerek olmaz.

> [!NOTE]
> Çalışma kitabını Excel; ancak, yalnızca Visual Studio yüklü olan kullanıcılar elektronik tablolardan herhangi birini değiştirebilir. Diğer kullanıcılar çalışma kitabı **şeridinde** Yük  Testi Raporu Office ancak çalışma kitabını görüntülemeye devam ediyor.

Aşağıdaki çizimde, işlem (Güncelleştirme Sepeti) hızındaki düşüş ile (% İşlemci) sayacının degenerasyonu arasındaki bağıntıyı gösteren bir rapor örneği gösterilmiştir. Bu, veritabanı veya ağ yerine uygulama kodundaki olası bir sorunu gösterir ve ASP.NET Profiler'ı kullanarak tanılama için iyi bir adaydır.

![Uygulama kodunda olası sorun](../test/media/lt_excel.png)

Excel, araç çubuğundaki **Excel** Raporu Oluştur düğmesi kullanılarak Yük Testi Çözümleyicisi'nda veya Excel şeridinin Yük Testi sekmesindeki Yük  Testi Raporu seçeneği kullanılarak **Office** oluşturabilir. 

> [!NOTE]
> Bir yük testine açıklama eklersiniz, bunlar Excel görüntülenir.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Yük testi karşılaştırma raporları oluşturmak için Excel

1. Rapor oluşturmadan önce bir yük testi çalıştırmalısiniz.

2. Yük testi Excel iki şekilde oluşturabilirsiniz:

   - Bir yük testi tamamlandıktan sonra, Yükleme **Test Sonuçları** araç çubuğundaki **Excel Rapor Oluştur** düğmesini seçin.

      > [!NOTE]
      > Web **Performansı Excel** Görüntüleyici araç çubuğunda Rapor Oluştur **Test Sonuçları** devre dışı bırakılırsa, etkinleştirilmeden önce Microsoft Excel bir kez çalıştırmanız gerekir. Yükleme Visual Studio Enterprise, Visual Studio Enterprise testi eklentisi, yükleme testi için bilgisayarınıza Microsoft Excel; ancak, Microsoft Excel yükleme işlemini tamamlamak için aşağıdakiler çalıştır gerekir.

      Microsoft Excel Yük Testi **Raporu Oluşturma Sihirbazı ile açılır.**

   **OR**

   1. Test Microsoft Excel açın, test **şeridinde** Yük Testi sekmesini **Office** sonra Yük Testi **Raporu'Office'yi seçin.**

       Yük **Testi Raporu Oluşturma Sihirbazı** görüntülenir.

   2. Yük **testleri içeren veritabanını seçin sayfasının** Sunucu **adı'nın** altına yük testi sonuçlarını içeren sunucunun adını yazın.

   3. Veritabanı **adı açılan** listesinde yük testi sonuçlarını içeren veritabanını seçin.

3. Raporlarınızı **nasıl oluşturmak istediğiniz sayfasında Rapor oluştur'ın** seçili olduğunu doğrulayın ve **Sonraki'yi** **seçin.**

4. Hangi **rapor türünü oluşturmak istediğiniz sayfasında Karşılaştırma çalıştır'ın** seçili olduğunu doğrulayın ve **Sonraki'yi** **seçin.**

5. Yük **testi raporu ayrıntılarını girin sayfasında** Rapor Adı alanına raporunuz için bir ad **yazın.**

6. Raporu oluşturmak istediğiniz yük testini seçin ve ardından Sonraki'yi **seçin.**

7. Rapor **için çalıştırmaları** seçin sayfasının Rapora eklemek istediğiniz bir veya daha fazla çalıştırmayı seçin **altında,** raporda karşılaştırmak istediğiniz iki yük testi sonuçlarını seçin ve ardından Sonraki'yi **seçin.**

   > [!NOTE]
   > Yalnızca iki yük testi sonucu üzerinde karşılaştırma raporu oluşturabilirsiniz. Bir yük testi sonucu veya ikiden fazla yük testi sonucu seçersiniz, bir uyarı iletisi görüntülenir.

8. Rapor **için sayaçları** seçin sayfasının Bir  veya daha fazla sayaç seçin altında rapora eklemek istediğiniz sayaçları genişletilebilir bir listeyle özelleştirebilirsiniz. Raporda seçilen iki test çalıştırması arasında karşılaştırmak istediğiniz sayaçları seçin ve Son'a **seçin.**

9. Çalışma Excel raporu aşağıdaki elektronik tablo sekmeleriyle oluşturulur:

   - **İçindekiler -** Yük testi rapor adını görüntüler ve rapordaki çeşitli sekmelere bağlantılar içeren bir içindekiler tablosu sağlar.

   - **Çalıştırmalar -** Raporda hangi iki çalıştırmanın karşılaştırıldıkları hakkında ayrıntılar sağlar.

   - **Test Karşılaştırması -** Karşılaştıran iki çalıştırma arasındaki performans gerilemeleri ve geliştirmeler hakkında çubuk grafik ayrıntıları sağlar.

   - **Sayfa Karşılaştırması -** Test çalıştırmalarının çeşitli sayfalarındaki iki çalıştırma arasında çubuk grafik ve yüzde performans karşılaştırma verileri sağlar.

   - **Makine Karşılaştırması -** Kullanılan makinelere göre iki çalıştırma arasında karşılaştırma verileri sağlar.

   - **Hata Karşılaştırması -** İki çalıştırma ve oluşum sayısı arasında karşılaşılan hata türlerini karşılar.

     > [!TIP]
     > Daha iyi raporlar için yük testlerinde ve daha zengin raporlara olanak sağlayan web performansı testlerinde çeşitli özellikler mevcuttur. Sayfa isteğinin raporlarda sunulan iki özelliği vardır: Hedef ve Raporlama Adı. Sayfa yanıt süreleri hedefe göre rapor olur ve raporlarda URL yerine raporlama adı kullanılır. Bir yük testi Çalıştırma Ayarlar, Sayaç Kümelerini Yönet altında, Bilgisayar Etiketleri özelliği rapor makinesi adlarında sunulmuştur. Bu, raporda belirli bir makinenin rolünü açıklamak için çok kullanışlıdır.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Yük testi eğilim raporları oluşturmak için Excel

1. Rapor oluşturmadan önce bir yük testi çalıştırmalısiniz.

2. Yük testi Excel iki şekilde oluşturabilirsiniz:

   - Bir yük testi tamamlandıktan sonra, Yükleme **Test Sonuçları** araç çubuğundaki **Excel Rapor Oluştur** düğmesini seçin.

      > [!NOTE]
      > Web **Performansı Excel** Görüntüleyici araç çubuğunda Rapor Oluştur **Test Sonuçları** devre dışı bırakılırsa, etkinleştirilmeden önce Microsoft Excel bir kez çalıştırmanız gerekir. Yükleme Visual Studio Enterprise, Visual Studio Enterprise testi eklentisi, yükleme testi için bilgisayarınıza Microsoft Excel; ancak, Microsoft Excel yükleme işlemini tamamlamak için aşağıdakiler çalıştır gerekir.

      Microsoft Excel Yük Testi **Raporu Oluşturma Sihirbazı ile açılır.**

   **OR**

   1. Test Microsoft Excel açın, test **şeridinde** Yük Testi sekmesini **Office** sonra Yük Testi **Raporu'Office'yi seçin.**

       Yük **Testi Raporu Oluşturma Sihirbazı** görüntülenir.

   2. Yük **testleri içeren veritabanını seçin sayfasının** Sunucu **adı'nın** altına yük testi sonuçlarını içeren sunucunun adını yazın.

   3. Veritabanı **adı açılan** listesinde yük testi sonuçlarını içeren veritabanını seçin.

3. Raporlarınızı **nasıl oluşturmak istediğiniz sayfasında Rapor oluştur'ın** seçili olduğunu doğrulayın ve **Sonraki'yi** **seçin.**

4. Hangi **rapor türünü oluşturmak istediğiniz sayfasında Eğilim'in** seçili olduğunu doğrulayın **ve Sonraki'yi** **seçin.**

5. Yük **testi raporu ayrıntılarını girin sayfasında** Rapor Adı alanına raporunuz için bir ad **yazın.**

6. Raporu oluşturmak istediğiniz yük testini seçin ve ardından Sonraki'yi **seçin.**

7. Rapor **için çalıştırmaları** seçin sayfasının Rapora eklemek istediğiniz bir veya daha fazla çalıştırmayı seçin **altında,** raporda karşılaştırmak istediğiniz yük testi sonuçlarını seçin ve ardından Sonraki'yi **seçin.**

8. Rapor **için sayaçları** seçin sayfasının Rapora eklemek istediğiniz bir veya daha fazla sayacı seçin altında **raporlarınızı** özelleştirmek için genişletilebilir sayaç listesi kullanılabilir. Eğilim analizi için karşılaştırmak istediğiniz sayaçları seçin ve Son'a **seçin.**

9. Rapor, raporda oluşturulan çeşitli çalışma kitabı sekmelerine Excel içeren bir içindekiler tablosuyla oluşturulur. Bağlantılar, eğilim raporu için seçilen sayaçları temel almaktadır. Örneğin, 7. adımda varsayılan sayaçları seçili bıraktıysanız rapor, 7. adımda listelenen her sayaç için ayrı sekmelerde Excel veriler üretir. Her sayaç için oluşturulan veriler eğilim stilinde grafiklerde gösterilir.

   > [!TIP]
   > Daha iyi raporlar için yük testlerinde ve daha zengin raporlara olanak sağlayan web performansı testlerinde çeşitli özellikler mevcuttur. Sayfa isteğinin raporlarda sunulan iki özelliği vardır: Hedef ve Raporlama Adı. Sayfa yanıt süreleri hedefe göre rapor olur ve raporlarda URL yerine raporlama adı kullanılır. Bir yük testi Çalıştırma Ayarlar, Sayaç Kümelerini Yönet altında, Bilgisayar Etiketleri özelliği rapor makinesi adlarında sunulmuştur. Bu, raporda belirli bir makinenin rolünü açıklamak için çok kullanışlıdır.

## <a name="net-security"></a>.NET Framework güvenliği

Yük testi sonuçları ve raporları, bilgisayarınıza veya ağınıza karşı bir saldırı oluşturmak için kullanılmaktadır. Yük testi sonuçları ve raporları bilgisayar adlarını ve bağlantı dizelerini içerir. Yük testi raporlarını diğer kişilerle paylaşırken bunun farkında olmak gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test karşılaştırmaları veya eğilim analizi için yük testleri sonuçlarını bildirme](../test/compare-load-test-results.md)
