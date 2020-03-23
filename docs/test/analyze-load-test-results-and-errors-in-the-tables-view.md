---
title: Yük Testi Sonuçlarının ve Hatalarının Analizi
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.pageresult
- vs.test.load.dialog.column
- vs.test.load.monitor.requestresult
- vs.test.load.monitor.testresult
- vs.test.load.monitor.table.view
- vs.test.load.monitor.agentresult
- vs.test.load.monitor.transactionresult
helpviewer_keywords:
- tables, Load Test Viewer options
- load test results, tables
- load tests, Load Test Viewer
- data [Visual Studio ALM], load test tables
- Load Test Viewer, tables
- load tests, results tables
ms.assetid: 0a84bda3-6051-45eb-9c7f-d57419e1f97d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5e337c30a4b6a08f123ef7ee33dee704e9412de
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565181"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Yük Testi Çözümleyicisinin Tablo görünümünde yük testi sonuçlarını ve hatalarını analiz etme

Bir yük testi çalışmasının sonuçlarını görüntülediğinizde, verileri çözümlemeniz için farklı yollar sağlayan farklı bölmeleri görüntüleyebilirsiniz. Zaman içinde nasıl değiştiğini görmek için verileri grafik olarak görüntüleyebilir veya verileri ayrıntılı tablolar olarak görüntüleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Tablo görünümüne geçmek **için, yük testi** araç çubuğundaki **Tablolar'ı** seçin. Farklı tablolar arasında geçiş yapmak için, tablo ızgarasının üzerindeki araç çubuğundaki **Tablo** açılır listesini kullanın. Tablo görünümünde, aynı anda en fazla dört tablo görüntüleyebilirsiniz. Daha fazla bilgi için bu [konudaki Döşeme yük test tablolarına](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) bakın.

Performans sayaçları için bir tabloda görüntülenen çoğu sayısal değer, tüm yük testi çalışması boyunca birikmelidir. **Son** adlı sütunlar bir özel durumdur ve en son örnekleme aralığındaki değeri temsil eder.

> [!NOTE]
> **Son** adlı sütunlar yalnızca yük testi yürütülerken kullanılabilir. Yükleme testi tamamlandıktan sonra bu sütunlar kullanılamaz.

Sıralamak istediğiniz sütunun başlığını seçerek çoğu tabloyu sıralayabilirsiniz. Varsayılan olarak, bazı tablolar kullanılabilir tüm sütunları görüntülemez. Sütunlar varsa tablolara sütun ekleyebilirsiniz. Sütun eklemek için tabloyu sağ tıklatın ve ardından **Sütun Ekle/Kaldır'ı**seçin.

> [!NOTE]
> Ek çözümleme için verileri tablodaki diğer uygulamalara kopyalayabilirsiniz.

## <a name="the-load-test-tables"></a>Yük test tabloları

Aşağıdaki tabloda yük testi çalışır çözümlemek için kullanılabilir tablolar listeler.

|Tablo Adı|Açıklama|
|-|-|
|Hatalar|Yük testi çalışması sırasında oluşan hataların listesini görüntüler. Daha fazla bilgi için bu [konudaki Hatalar tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) bakın ve [yük testi sonuçlarını çözümleyin.](../test/analyze-load-test-results-using-the-load-test-analyzer.md)|
|Sayfalar|Yük testi sırasında erişilen sayfaların listesini görüntüler. Bu tablodaki bazı veriler yalnızca bir yük testi tamamlandıktan sonra kullanılabilir. Daha fazla bilgi için [bkz: Web sayfası yanıtını görüntüle.](../test/how-to-view-web-page-response-time-in-a-load-test.md)|
|İstekler|Yük testi sırasında verilen bireysel isteklerin ayrıntılarını görüntüler. Buna tüm HTTP istekleri ve resimler gibi bağımlı istekler dahildir. Daha fazla bilgi için bu [konudaki İstekler tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) bakın.|
|SQL İzi|SQL izleme sonuçlarını görüntüler. Bu tablo yalnızca bir yük testi tamamlandıktan sonra ve yalnızca test sırasında SQL izleme si kullanıldıysa kullanılabilir. Daha fazla bilgi için bu [konudaki SQL İzleme veri tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) bakın.|
|Testler|Yük testi sırasında yapılan tek tek testlerin ayrıntılarını görüntüler. Daha fazla bilgi için bu [konudaki Testler tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) bakın.|
|Eşik|Yük testi çalışması sırasında oluşan eşik kuralı ihlallerinin listesini görüntüler. Daha fazla bilgi için [bkz.](../test/analyze-threshold-rule-violations-in-load-tests.md)|
|İşlemler|Yük testi çalışması sırasında gerçekleşen hareketlerin listesini görüntüler. Daha fazla bilgi için bu [konudaki Hareketler tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) bakın.|
|Aracılar|Yalnızca yük testiniz bir test denetleyicisi ve test aracıları kullanıyorsa görüntüler. Yük testi çalışması sırasında kullanılan aracıların listesini görüntüler. Aracılar tablosu, aracının kaç isteği sınadığını ve bu isteklerin kaç tanebaşarısız olduğunu içerir. Ayrıca, Aracılar tablosu, aracının test ettiği yük testleri test karışımındaki test sayısını ve bunların kaç başarısız olduğunu içerir.|
|Test Detayları|Yük testi için test karışımında yer alan testlerin ayrıntılarını görüntüler. Ayrıntılar, testin adını, testin içinde bulunduğu senaryoyu, testin başladığı zamanı, testin çalıştırılmak için aldığı süreyi ve testin geçip geçemediğini belirten test sonucunu içerir. Test başarısız olduysa, **Ayrıntılar** sütununda bir bağlantı bulunur. Başarısız istek vurgulanmış web performans testi düzenleyicisine götürecek bağlantıyı seçebilirsiniz.|

## <a name="collect-percentile-data"></a>Yüzdelik veritoplama

Bazı yük test tabloları, ağ öykünmesine dayalı olarak gruplara ayrılmış yüzdelik verileri ve yanıt sürelerini içeren ek sütunlar içerebilir. Varsayılan olarak, bu veriler toplanmaz. Yüzdelik veri, sonuçları yalnızca yerel olarak kaydettiğinizde değil, bir veritabanına kaydettiğinizde kullanılabilir. Daha fazla bilgi için bkz: [Yük Testi Sonuçları Deposu'nda yük testi sonuçlarını yönetme.](../test/manage-load-test-results-in-the-load-test-results-repository.md) Ayrıca, bu verileri toplamak **için, Yük Testi**Düzenleyicisi'nde , **Çalıştır Ayarları** düğümünün altında, değiştirmek için belirli çalıştır ayar düğümünü seçin. **Özellikler** penceresinde, Zamanlama **Ayrıntıları Depolama** özelliği için **StatisticsOnly** veya **AllIndividualDetails'ı**seçin. Daha fazla bilgi için [bkz: Web sayfası yanıtını görüntüle.](../test/how-to-view-web-page-response-time-in-a-load-test.md)

## <a name="the-requests-table"></a>İstekler tablosu

**İstekler** tablosu, yükleme testi sırasında verilen tek tek isteklerin ayrıntılarını görüntüler. Buna tüm HTTP istekleri ve resimler gibi bağımlı istekler dahildir. Bir istek birçok test ve senaryoya dahil edilebildiği için tablo isteklerini test ve senaryoya göre listeler.

Aşağıdaki **tabloda İstekler** tablosundaki sütunlar listelenebilmiştir:

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|**İstek**|İsteğin URL'si. Örneğin, *home.html*veya *turuncu-ok.gif*.|Evet|
|**Senaryo**|Senaryonun adı.|Evet|
|**Test**|Testin adı.|Evet|
|**Toplam**|Yük testi çalışması sırasında verilen bu web performans testi isteğinin toplam sayısı. Toplam, geçirilen ve başarısız olan istekleri içerir, ancak önbelleğe alınmış istekleri içermez, çünkü bunlar web sunucusuna verilmez.|Evet|
|**Geçirilen**|İsteğin kaç kez verildiği ve geçirildiği.|Hayır|
|**Başarısız**|İsteğin kaç kez verildiği ve başarısız olduğu. Bu sütundaki girişler köprüler olarak görünür. **Yük Testi Hataları** iletişim kutusundaki tek tek hataların listesini görüntülemek için herhangi bir köprü seçebilirsiniz. Daha fazla bilgi için [bkz.](../test/analyze-load-test-results-using-the-load-test-analyzer.md)|Evet|
|**Önbelleğe alınmış**|İsteğin zaten önbelleğe alınmış toplam sayısı.|Hayır|
|**İstekler/Sn**|Yük testi çalışması sırasında isteğin saniye başına oranı.|Hayır|
|**Geçti/Sn**|Bu istek, geçen bu istek örnekleri için, yük testi çalışması sırasında bu isteğin saniye başına oranı.|Hayır|
|**Başarısız/Sn**|Bu istek başarısız örnekleri için, yük testi çalışması sırasında bu isteğin saniye başına oranı.|Hayır|
|**İlk Bayt Zamanı**|Yanıtın ilk baytını almak için gereken ortalama süre, isteğin web sunucusuna gönderildiği andan itibaren ölçülür. Birimler saniyeler.|Hayır|
|**Yanıt Süresi**|İsteğin web sunucusuna gönderildiği andan itibaren ölçülen bir isteğe yanıtın tamamını almak için gereken ortalama süre. Birimler saniyeler.|Evet|
|**İçerik Uzunluğu**|İsteğe yanıtın içeriğinin ortalama uzunluğu. Birimler bayt.|Evet|

## <a name="the-tests-table"></a>Testler tablosu

**Testler** tablosu, yük testi sırasında çalıştırılanan tek tek testlerin ayrıntılarını görüntüler. Bir test birçok senaryoya dahil edilebildiği için tablo testleri test ve senaryoya göre listeler.

Aşağıdaki tabloda **Testler** tablosundaki sütunlar listelenebilmiştir.

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|**Test**|Testin adı.|Evet|
|**Senaryo**|Senaryonun adı.|Evet|
|**Toplam**|Testin senaryoda toplam kaç kez çalıştırıldığını. Bu, testin kaç kez geçtiğini ve başarısız olduğunu içerir.|Evet|
|**Geçirilen**|Testin senaryoda çalıştırılıp geçirildiği sayı.|Evet|
|**Başarısız**|Testin senaryoda kaç kez çalıştırıldı ve başarısız oldu. Bu sütundaki girişler köprüler olarak görünür. **Yük Testi Hataları** iletişim kutusundaki tek tek hataların listesini görüntülemek için herhangi bir köprü seçebilirsiniz. Daha fazla bilgi için [bkz.](../test/analyze-load-test-results-using-the-load-test-analyzer.md)|Evet|
|**Testler/Sn**|Yük testi çalışması sırasında testin saniye başına oranı.|Evet|
|**Geçti/Sn**|Bu testin geçen örnekleri için, yük testi çalışması sırasında bu testin saniye başına oranı.|Hayır|
|**Başarısız/Sn**|Bu testin başarısız olan örnekleri için, yük testi çalışması sırasında bu testin saniye başına oranı.|Hayır|
|**Test Süresi**|Yük testi çalışması sırasında testi yürütmek için ortalama süre. Birimler saniyeler.|Evet|
|**%90 Test Süresi**|Test Süresi için 90.|Hayır|
|**%95 Test Süresi**|Test Süresi için 95.|Evet|
|**İstekler/Test**|Bir web performans testi yse, testteki ortalama istek sayısı.|Hayır|

## <a name="the-transactions-table"></a>İşlemler tablosu

**Hareketler** tablosu, yük testi çalışması sırasında gerçekleşen hareketlerin listesini görüntüler. Hareketler, web performans testinde tanımlanan hareketlere veya birim testinde tanımlanan zamanlayıcılara başvurur. Hareket veritabanı hareketlerine başvurmaz.

Aşağıdaki tabloda **Hareketler** tablosundaki sütunlar listelenebilmiştir.

> [!NOTE]
> Tüm sütunları görüntülemek için, etkin çalıştırma ayarı ile ilişkili Zamanlama Ayrıntıları Depolama özelliğini etkinleştirmeniz gerekir. Daha fazla bilgi için [bkz: Zamanlama Ayrıntıları Depolama özelliğini belirtin.](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)

|Sütun|Açıklama|Zamanlama ayrıntıları olmadan görünür|
|-|-|-|
|**Işlem**|İşlemin adı.|Evet|
|**Senaryo**|Senaryonun adı.|Evet|
|**Test**|Testin adı.|Evet|
|**Toplam**|Yük testi çalışması sırasında verilen toplam hareket sayısı.|Evet|
|**İşlem Süresi**|Yük testi çalışması sırasında hareketi yürütme zamanı. Web performans testleri için, zaman hesaplamaya dahil olduğunu düşünüyorum. Birimler saniyeler.|Hayır|
|**Yanıt Süresi**|Yük testi çalışmasındaki web performans testi hareketinin yanıt süresi. Yanıt Süresi, bu Yanıt Süresi'ndeki İşlem Süresi'nden farklıdır ve hareket sırasında gerçekleşen düşünme süresini içermez. Birimler saniyeler.|Hayır|
|**Ave. İşlem Süresi**|Ortalama işlem süresi. Bu süre düşünme sürelerini içerir. Örneğin, üç isteğiniz varsa ve her birinin düşünme süresi varsa, bu süre bu düşünme sürelerini ve istekleri yürütmek için gereken fiili zamanı içerir.|Hayır|
|**Ave. Yanıt Süresi**|Yük testi çalışmasındaki web performans testi hareketinin ortalama yanıt süresi. Yanıt Süresi, bu Yanıt Süresi'ndeki İşlem Süresi'nden farklıdır ve hareket sırasında gerçekleşen düşünme süresini içermez. Birimler saniyeler.|Hayır|
|**Min Yanıt Süresi**|Bu düşünme sürelerini içermez.|Hayır|
|**Max Yanıt Süresi**|Bu düşünme sürelerini içermez.|Hayır|
|**Ortanca Yanıt Süresi**|Bu düşünme sürelerini içermez.|Hayır|
|**%90 Yanıt Süresi**|İşlem Süresi için 90. Bu düşünme sürelerini içermez. **Not:**  Bu, **%90 İşlem Süresi** değerini kullanan Visual Studio Team System 2008 Test Load Agent'dan farklıdır.|Hayır|
|**%95 Yanıt Süresi**|İşlem Süresi için 95. Bu düşünme sürelerini içermez. **Not:**  Bu, **%95 İşlem Süresi** değerini kullanan Visual Studio Team System 2008 Test Load Agent'dan farklıdır.|Hayır|
|**%99 Yanıt Süresi**|İşlem Süresi için 99. Bu düşünme sürelerini içermez.|Hayır|
|**Std Dev Yanıt Süresi**|Bu düşünme sürelerini içermez.|Hayır|

## <a name="the-errors-table"></a>Hatalar tablosu

Bir yük testi çalıştırdığınızda, oluşan hataları çözümleyebilirsiniz. Hataları çözümleme ve testlerinizi ayarlama, yük testi sürecinin önemli bir parçasıdır. Herhangi bir hata oluştuysa, yük testi durum çubuğunda bir **hata** köprü görünür ve oluşan hata sayısını belirtir. Hatalar tablosunu görüntülemek için köprüseçin.

Hatalar tablosu, bir yük testi sırasında oluşan hataları hatanın türüne ve alt türüne göre gruplandırılır. Ayrıca tabloda oluşan tüm hataların toplam sayısını belirten bir **toplam** satır vardır.

Hatalar tablosu aşağıdaki sütunları içerir:

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|Tür|Hata türü. Örneğin, httpError.|Evet|
|SubType|Hatanın alt türü. Örneğin, LoadTestException.|Evet|
|Sayı|Yük testi sırasında oluşan bu tür hata sayısı. Bu sütundaki girişler köprüler olarak görünür. Tek tek hataların listesini görüntülemek için herhangi bir köprü seçebilirsiniz.|Evet|
|Son İleti|Hatayı açıklayan bir ileti. Örneğin, 404 - NotFound.|Evet|

Daha fazla bilgi için [bkz: Yük test tabloları ile çalışma.](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

### <a name="drill-down-to-the-error-list"></a>Hata listesine ayrıntısına kadar inme

Hatalar tablosu hataları hatanın türüne ve alt türüne göre gruplatır. Tek tek hatalar tablosunu görüntülemek **için, Yükle Testi Hataları** iletişim kutusunu görüntülersiniz. İletişim kutusunu görüntülemek için, hatalar tablosunun **Count** sütunundaki bir köprü seçin. Ayrıca, doldurulan hatalar tablosunda bir satırı sağ tıklatarak ve **Hatalar'ı**seçerek iletişim kutusunu görüntüleyebilirsiniz.

> [!NOTE]
> Herhangi bir hata türü ve alt tür kombinasyonunun yalnızca ilk 1.000 örneği toplanır. Yük Testi **Hataları** iletişim kutusunu görüntülediğinizde, en fazla ilk 1.000 örneği görürsünüz.

**Yük Testi Hataları** tablosu aşağıdaki sütunları içerir:

|Sütun|Açıklama|
|-|-|
|**Zaman**|Hatanın oluştuğu yük testi sırasındaki süre.|
|**Aracı**|Hatanın oluştuğu aracı bilgisayarın adı. Bu, test denetleyicileri ve test aracıları kullanarak yük testleri çalıştırdığınızda önemlidir. Daha fazla bilgi için [bkz.](../test/lab-management/install-configure-test-agents.md)|
|**Test**|Hatanın oluştuğu web performans testinin adı.|
|**Senaryo**|Hatanın oluştuğu senaryonun adı.|
|**İstek**|Hatanın oluştuğu isteğin URL'si.|
|**Tür**|Hata türü. Örneğin, httpError.|
|**Alt**|Hatanın alt türü. Örneğin, LoadTestException.|
|**Metin**|Hata iletisinin metni. Örneğin, 404 - NotFound.|
|**Yığın**|Bu sütundaki girişler boş veya **Yığın** sözcüğü köprü olarak biçimlendirilir. Hatayığının izini görüntülemek için köprüseçebilirsiniz.|
|**Şey**|Bu sütundaki girişler boş veya **TestLog** sözcüğü köprü olarak biçimlendirilir. Bu bağlantı, yük testindeki hataları yalıtmanıza yardımcı olabilir. Örneğin, bir web performans testi isteği hatasındaki **TestLog** bağlantısını seçmek, Web Performans Testi Sonuçları Görüntüleyici'deki web performans testinin sonuçlarını açar ve istek hatasını vurgular.|

> [!NOTE]
> Sütun üstbilgisini seçerek tabloyu sıralayabilirsiniz.

## <a name="the-sql-trace-data-table"></a>SQL Trace veri tablosu

Daha sonra çözümlemek için bir yük testi çalışması sırasında SQL izleme verileri toplayabilirsiniz. İzleme verileri toplamak, test edilen SQL Server veritabanında en yavaş çalışan sorguları ve depolanan yordamları belirlemenize olanak tanır.

SQL izleme etkinse, izleme verilerini içeren yük testi çalışması sırasında bir dosya oluşturulur. Bu veriler, test çalışmasının sonundaki Yük Testi Sonuçları Deposu'na otomatik olarak kaydedilir ve izleme dosyası silinir. Yükleme testiniz tamamlandıktan sonra **SQL İzleme** tablosundaki izleme verilerini çözümlersiniz.

### <a name="to-view-sql-trace-data"></a>SQL izleme verilerini görüntülemek için

1. Yük Testi Çözümleyicisi'nde, tablo ızgarasının görüntülendiğinden emin olmak için araç çubuğundaki **Tablolar'ı** seçin.

2. **Tablo** açılır liste kutusunda SQL **İzleme'yi**seçin.

3. Çalışma sırasında toplanan izleme verileri ızgarada görüntülenir. Tablo, süreye göre sıralanmış en yavaş çalışan SQL işlemlerini listeler ve en üstte en yavaş olan dır. Genellikle, **Süre** sütunu incelenen ilk sütundur. Veriler milisaniye cinsinden görüntülenir.

   Görüntülenen sütunlar aşağıdaki gibidir:

    - **Etkinlik Sınıfı**

    - **Süre**

    - **CPU**

    - **Okur**

    - **Yazar**

    - **TextData**

    - **Starttime**

    - **Endtime**

   Bu sütunlarda tanımlanan veriler dışındaki SQL olaylarını izlemek istiyorsanız, Visual Studio'dan ayrı olan SQL Profiler aracını kullanarak kendi özel SQL izlemenizi ayarlayabilirsiniz.

## <a name="tile-load-test-tables"></a>Fayans yük test tabloları

Bir yük testi çalışmasının sonuçlarını görüntülediğinizde, verileri ayrıntılı tablolar olarak görüntüleyebilirsiniz. Tablo görünümüne geçmek **için, yük testi** araç çubuğundaki **Tablolar'ı** seçin. Kullanılabilir tablolar **Hatalar,** **Sayfalar**, **İstekler**, **SQL İzleme**, **Testler**, Eşikler ve **İşlemler**. **Transactions** Daha fazla bilgi için [bkz: Yük test tabloları ile çalışma.](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

Tablo görünümünde, tablolar çakışmadan aynı anda en fazla dört tablo görüntüleyebilirsiniz.

### <a name="to-tile-tables"></a>Döşeme tablolarına

1. Yük **Testi Çözümleyici** araç çubuğunda **Tablolar'ı**seçin.

     Tablo görünümü açılır. Varsayılan düzen iki yatay paneldir.

2. Yük **Testi Çözümleyici** araç çubuğunda **düzen** düğmesini seçin ve ardından aşağıdaki seçeneklerden birini seçin:

    - **Tek Panel**

    - **İki Yatay Panel**

    - **Üç Yatay Panel**

    - **Dört Yatay Panel**

3. Farklı tablolar arasında geçiş yapmak için, her paneldeki tablo ızgarasının üzerindeki açılır listeyi kullanın.

    > [!NOTE]
    > Aynı tabloyu birden fazla panelde görüntüleyemezsiniz. Bir panelde görüntülenen tabloyu başka bir panelde zaten görüntülenen bir tabloyla değiştirirseniz, tablolar panelleri değiştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılı: Analiz için yük testi sonuçlarına erişin](../test/how-to-access-load-test-results-for-analysis.md)
- [Grafikler görünümünde yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Eşik kuralı ihlallerini analiz edin](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Yük Testi Sonuçları Deposu'nda yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Yük testi sonuçları özetine genel bakış](../test/load-test-results-summary-overview.md)
