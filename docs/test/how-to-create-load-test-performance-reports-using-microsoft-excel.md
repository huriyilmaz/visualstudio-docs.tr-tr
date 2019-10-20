---
title: Microsoft Excel kullanarak yük testi performans raporları oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, creating Excel reports
- load tests, reporting
ms.assetid: b87fb196-9973-4512-a924-088788def4ea
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: af0afc61fcf7cb251836414ca474eb63da3bf2e9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653557"
---
# <a name="how-to-create-load-test-performance-reports-using-microsoft-excel"></a>Nasıl yapılır: Microsoft Excel kullanarak yük testi performans raporları oluşturma

İki veya daha fazla test sonucunu temel alan Microsoft Excel yük testi raporları oluşturabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

İki tür yük testi raporu kullanılabilir:

- **Karşılaştırma Çalıştır** Bu, tabloları ve çubuk grafiklerini kullanarak iki yük testi sonuçlarındaki verileri karşılaştıran bir rapor kümesi oluşturur.

- **Eğilimi** İki veya daha fazla yük testi sonucu üzerinde eğilim analizi oluşturabilirsiniz. Sonuçlar çizgi grafikler kullanılarak görüntülenir, ancak veriler Pivot tablolarında kullanılabilir.

> [!TIP]
> Ayrıca, Özet görünümü, Grafikler görünümü ve tablolar görünümünden verileri kopyalayarak ve yapıştırarak Microsoft Word raporlarını el ile oluşturabilirsiniz. Bkz. [nasıl yapılır: Microsoft Word kullanarak yük testi performans raporu el ile oluşturma](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md).

Rapor, performans verilerini paydaşlarla paylaşmak ve sistemin genel performansının ve sistem durumunun daha iyi veya daha kötüleştiğini iletmek için kullanılabilir.

Rapor tanımları yük testi veritabanında depolanır. Bir rapor kaydedildiğinde, raporun tanımı veritabanına kaydedilir ve daha sonra yeniden kullanılabilir.

Ayrıca, Excel çalışma kitabı, paydaşlarla paylaşılabilir, böylece hissedarlar raporu görmek için veritabanına bağlanmak zorunda değildir.

> [!NOTE]
> Excel çalışma kitabını paylaşabilirsiniz; Ancak, yalnızca kendi makinesinde Visual Studio yüklü olan kullanıcılar herhangi bir elektronik tabloda değişiklik yapabilecektir. Diğer kullanıcılar **Office** şeridinde **Yük testi raporu** seçeneğini görmez, ancak çalışma kitabını görüntüleyebilecektir.

Aşağıdaki çizim, işlem içindeki reddetme (güncelleştirme sepeti) hızı ve (% Işlemci) sayacının çıkarılması arasındaki bağıntıyı gösteren bir rapor örneğidir. Bu, veritabanı veya ağ yerine uygulama kodundaki olası bir soruna işaret eder ve ASP.NET profil oluşturucuyu kullanarak tanılamaya yönelik iyi bir adaydır.

![Uygulama kodundaki olası sorun](../test/media/lt_excel.png)

Excel raporları, **Yük Testi Çözümleyicisi**'nde, araç çubuğundaki **Excel raporu oluştur** düğmesi kullanılarak veya Excel 'Den **Office** şeridinin **Yük testi** sekmesindeki **Yük testi raporu** kullanılarak oluşturulabilir.

> [!NOTE]
> Bir yük testine yorum eklerseniz, Excel raporunda görünürler.

## <a name="to-generate-load-test-comparison-reports-using-excel"></a>Excel kullanarak yük testi karşılaştırma raporları oluşturmak için

1. Bir rapor oluşturmadan önce, önce bir yük testi çalıştırmanız gerekir.

2. Excel yük testi raporlarını iki şekilde oluşturabilirsiniz:

   - Yük testini tamamladıktan sonra, **yükleme test sonuçları** sayfasında, araç çubuğundaki **Excel raporu oluştur** düğmesini seçin.

      > [!NOTE]
      > **Web performansı test sonuçları Görüntüleyicisi** araç çubuğunda **Excel raporu oluştur** düğmesi devre dışıysa, etkinleştirilmeden önce Microsoft Excel 'i bir kez çalıştırmanız gerekebilir. Visual Studio Enterprise yüklendiğinde, Visual Studio Enterprise yük testi eklentisi Microsoft Excel için bilgisayarınıza kopyalanır; Ancak, eklentinin yükleme işlemini tamamlaması için Microsoft Excel 'nin çalıştırılması gerekir.

      Microsoft Excel, **Yük testi raporu oluşturma Sihirbazı**ile açılır.

   **VEYA**

   1. Microsoft Excel 'i açın, **Office** şeridinde **Yük testi** sekmesini seçin ve ardından **Yük testi raporu**' nu seçin.

       **Yük testi raporu oluşturma Sihirbazı** görünür.

   2. **Yük testlerini içeren veritabanını seçin** sayfasında, **sunucu adı**altında, yük testi sonuçlarını içeren sunucunun adını yazın.

   3. **Veritabanı adı** açılır listesinde, yük testi sonuçlarını içeren veritabanını seçin.

3. **Raporunuzu nasıl oluşturmak** istiyorsunuz sayfasında, **rapor oluştur** ' un seçili olduğunu doğrulayın ve **İleri**' yi seçin.

4. **Ne tür bir rapor oluşturmak** istiyorsunuz sayfasında, **karşılaştırmayı Çalıştır** ' ın seçili olduğunu doğrulayın ve **İleri**' yi seçin.

5. **Yük testi rapor ayrıntılarını girin** sayfasında, **rapor adı**' na raporunuz için bir ad yazın.

6. Raporu oluşturmak istediğiniz yük testini seçin ve **İleri ' yi**seçin.

7. **Raporunuzun çalıştırmalarını seçin** sayfasında, **rapora eklemek için bir veya daha fazla çalıştırma seçin**' in altında, raporda karşılaştırmak istediğiniz iki yük testi sonucunu seçin ve **İleri**' yi seçin.

   > [!NOTE]
   > Yalnızca iki yük testi sonucu üzerinde bir karşılaştırma raporu oluşturabilirsiniz. Bir yük testi sonucu veya ikiden fazla yük testi sonucu seçerseniz, bir uyarı iletisi görüntülenir.

8. **Raporunuzun sayaçlarını seçin** sayfasında, rapora **eklemek için bir veya daha fazla sayaç seçin altında, raporunuzu özelleştirmek için bir veya daha fazla sayaç seçin** altında sayaçların genişletilebilir bir listesi bulunur. Rapordaki iki seçili test çalıştırmasından karşılaştırmak istediğiniz sayaçları seçin ve **son**' u seçin.

9. Excel çalışma kitabı raporu, aşağıdaki elektronik tablo sekmeleri ile oluşturulur:

   - **Içindekiler tablosu** -yük testi rapor adını görüntüler ve rapordaki çeşitli sekmelerin bağlantılarıyla bir içindekiler tablosu sağlar.

   - **Çalıştırmalar-** Raporda iki çalıştırmanın karşılaştırıldığı ayrıntıları sağlar.

   - **Test karşılaştırması-** Karşılaştırılan iki çalıştırma arasındaki performans gerilemeleri ve geliştirmeleri hakkında çubuk grafik ayrıntıları sağlar.

   - **Sayfa karşılaştırması-** Test çalıştırmalarının çeşitli sayfalarındaki iki çalıştırma arasında çubuk grafik ve yüzde performans karşılaştırma verileri sağlar.

   - **Makine karşılaştırması-** Kullanılan makinelere göre iki çalıştırma arasında karşılaştırma verileri sağlar.

   - **Hata karşılaştırması-** İki çalıştırma ve oluşum sayısı arasında karşılaşılan hata türlerini karşılaştırır.

     > [!TIP]
     > Daha iyi raporlar için, daha zengin raporları etkinleştiren yük testlerinde ve Web performans testlerinde bazı özellikler mevcuttur. Sayfa isteği raporlarda sunulan iki özelliğe sahiptir: hedef ve raporlama adı. Sayfa yanıt süreleri hedefe göre bildirilecek ve raporlardaki URL yerine raporlama adı kullanılacaktır. Yük testi çalıştırma ayarlarındaki Sayaç Kümelerini Yönet altında, bilgisayar etiketleri özelliği rapor makinesi adlarında sunulur. Bu, rapordaki belirli bir makinenin rolünü açıklamaya yarar.

## <a name="to-generate-load-test-trend-reports-using-excel"></a>Excel kullanarak yük testi eğilimi raporları oluşturmak için

1. Bir rapor oluşturmadan önce, bir yük testi çalıştırmanız gerekir.

2. Excel yük testi raporlarını iki şekilde oluşturabilirsiniz:

   - Yük testini tamamladıktan sonra, **yükleme test sonuçları** sayfasında, araç çubuğundaki **Excel raporu oluştur** düğmesini seçin.

      > [!NOTE]
      > **Web performansı test sonuçları Görüntüleyicisi** araç çubuğunda **Excel raporu oluştur** düğmesi devre dışıysa, etkinleştirilmeden önce Microsoft Excel 'i bir kez çalıştırmanız gerekebilir. Visual Studio Enterprise yüklendiğinde, Visual Studio Enterprise yük testi eklentisi Microsoft Excel için bilgisayarınıza kopyalanır; Ancak, eklentinin yükleme işlemini tamamlaması için Microsoft Excel 'nin çalıştırılması gerekir.

      Microsoft Excel, **Yük testi raporu oluşturma Sihirbazı**ile açılır.

   **VEYA**

   1. Microsoft Excel 'i açın, **Office** şeridinde **Yük testi** sekmesini seçin ve ardından **Yük testi raporu**' nu seçin.

       **Yük testi raporu oluşturma Sihirbazı** görünür.

   2. **Yük testlerini içeren veritabanını seçin** sayfasında, **sunucu adı**altında, yük testi sonuçlarını içeren sunucunun adını yazın.

   3. **Veritabanı adı** açılır listesinde, yük testi sonuçlarını içeren veritabanını seçin.

3. **Raporunuzu nasıl oluşturmak** istiyorsunuz sayfasında, **rapor oluştur** ' un seçili olduğunu doğrulayın ve **İleri**' yi seçin.

4. **Ne tür bir rapor oluşturmak** istiyorsunuz sayfasında, **eğilimi** seçili olduğunu doğrulayın ve **İleri**' yi seçin.

5. **Yük testi rapor ayrıntılarını girin** sayfasında, **rapor adı**' na raporunuz için bir ad yazın.

6. Raporu oluşturmak istediğiniz yük testini seçin ve **İleri ' yi**seçin.

7. **Raporunuzun çalıştırmalarını seçin** sayfasında, **rapora eklemek için bir veya daha fazla çalıştırma seçin**altında, raporda karşılaştırmak istediğiniz yük testi sonuçlarını seçin ve **İleri**' yi seçin.

8. **Raporunuzun sayaçlarını seçin** sayfasında, rapora **eklemek için bir veya daha fazla sayaç seçin**altında, raporunuzu özelleştirmek için sayaçların genişletilebilir bir listesi mevcuttur. Eğilim analizi için karşılaştırmak istediğiniz sayaçları seçin ve **son**' u seçin.

9. Rapor, raporda oluşturulan çeşitli Excel çalışma kitabı sekmelerine bağlantılar içeren bir içindekiler tablosu ile oluşturulur. Bağlantılar, eğilim raporu için seçilen sayaçları temel alır. Örneğin, adım 7 ' de varsayılan sayaçları seçtiyseniz, rapor 7. adımda listelenen her sayaç için Excel 'de ayrı sekmelerde sunulan veriler oluşturacaktır. Her sayaç için oluşturulan veriler, eğilim stili grafiklerde sunulur.

   > [!TIP]
   > Daha iyi raporlar için, daha zengin raporları etkinleştiren yük testlerinde ve Web performans testlerinde bazı özellikler mevcuttur. Sayfa isteği raporlarda sunulan iki özelliğe sahiptir: hedef ve raporlama adı. Sayfa yanıt süreleri hedefe göre bildirilecek ve raporlardaki URL yerine raporlama adı kullanılacaktır. Yük testi çalıştırma ayarlarındaki Sayaç Kümelerini Yönet altında, bilgisayar etiketleri özelliği rapor makinesi adlarında sunulur. Bu, rapordaki belirli bir makinenin rolünü açıklamaya yarar.

## <a name="net-security"></a>.NET güvenliği

Yük testi sonuçları ve raporları, bilgisayarınıza veya ağınıza karşı bir saldırı oluşturmak için kullanılabilecek potansiyel olarak hassas bilgiler içerir. Yükleme testi sonuçları ve raporları, bilgisayar adlarını ve bağlantı dizelerini içerir. Yük testi raporlarını diğer kişilerle paylaştığınızda bunun farkında olmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test karşılaştırmaları veya eğilim analizi için yük testi sonuçlarını raporla](../test/compare-load-test-results.md)