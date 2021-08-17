---
title: Yük Analizi Test Sonuçları Hataları
description: Zaman içinde grafik veya ayrıntılı tablolar gibi yük testi çalıştırmalarının sonuçlarını analiz etmek için size farklı yollar sağlayan bölmeleri görüntülemeyi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 8d95b85aaffe7af6e674ab2e049c594b9db570a24e0fb85f6bfcbe47b3be5fee
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425103"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Yük Testi Çözümleyicisi'nin Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz etme

Bir yük testi çalıştırması sonuçlarını görüntüleyebilirsiniz. Bu bölmeleri görüntüleyebilirsiniz. Bu bölmeler size verileri çözümlemek için farklı yollar sağlar. Verileri graf olarak, zaman içinde nasıl değiştiklerini görmek için veya verileri ayrıntılı tablolar olarak görüntüebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Tablo görünümüne geçmek için yük testi **araç** çubuğunda **Tablolar'ı** seçin. Farklı tablolar arasında geçiş yapmak için tablo **kılavuzu üzerindeki** araç çubuğundaki Tablo açılan listesini kullanın. Tablo görünümünde aynı anda en fazla dört tablo görüntüebilirsiniz. Daha fazla bilgi için bu [konudaki Kutucuk yük testi](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) tablolarına bakın.

Performans sayaçları için bir tabloda görüntülenen sayısal değerlerin çoğu yük testi çalıştırması üzerinde birikmelidir. Last adlı **sütunlar** bir özel durumdur ve en son örnekleme aralığındaki değeri temsil eder.

> [!NOTE]
> Last adlı **sütunlar** yalnızca yük testi yürütücü olarak kullanılabilir. Yük testi tamamlandıktan sonra bu sütunlar kullanılamaz.

Sıralamak istediğiniz sütunun başlığını seçerek tabloların çoğunu sıraabilirsiniz. Varsayılan olarak, bazı tablolar kullanılabilir tüm sütunları görüntülemez. Sütunlar varsa tablolara sütun ekleyebilirsiniz. Sütun eklemek için tabloya sağ tıklayın ve Ardından Sütun **Ekle/Kaldır'ı seçin.**

> [!NOTE]
> Bir tablodaki verileri ek analiz için tablo gibi Excel kopyaabilirsiniz.

## <a name="the-load-test-tables"></a>Yük testi tabloları

Aşağıdaki tabloda yük testi çalıştırmalarını analiz etmek için kullanılabilen tablolar listelendi.

|Tablo Adı|Açıklama|
|-|-|
|Hatalar|Yük testi çalıştırması sırasında oluşan hataların listesini görüntüler. Daha fazla bilgi için bu [konudaki Hatalar](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) tablosu ve Yük testi sonuçlarını [analiz etme konularına bakın.](../test/analyze-load-test-results-using-the-load-test-analyzer.md)|
|Sayfalar|Yük testi çalıştırması sırasında erişilen sayfaların listesini görüntüler. Bu tablodaki bazı veriler ancak bir yük testi tamamlandıktan sonra kullanılabilir. Daha fazla bilgi için, [bkz. How to: View web page response](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|İstekler|Yük testi sırasında verilen tek tek isteklerin ayrıntılarını görüntüler. Buna tüm HTTP istekleri ve görüntüler gibi bağımlı istekler dahildir. Daha fazla bilgi için bu [konudaki Requests](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) tablosuna bakın.|
|SQL Izleme|Uygulama izlemenin SQL görüntüler. Bu tablo yalnızca bir yük testi tamamlandıktan sonra ve yalnızca test SQL izleme kullanıldıktan sonra kullanılabilir. Daha fazla bilgi için bu [SQL İzleme verileri tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) bakın.|
|Testler|Bir yük testi sırasında çalıştırıla tek tek testlerin ayrıntılarını görüntüler. Daha fazla bilgi için bu [konudaki Testler](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) tablosuna bakın.|
|Eşik|Yük testi çalıştırması sırasında meydana gelen eşik kuralı ihlallerinin listesini görüntüler. Daha fazla bilgi için [bkz. Eşik kuralı ihlallerini analiz etme.](../test/analyze-threshold-rule-violations-in-load-tests.md)|
|İşlemler|Yük testi çalıştırması sırasında meydana gelen işlemlerin listesini görüntüler. Daha fazla bilgi için bu [konudaki İşlemler](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) tablosuna bakın.|
|Aracılar|Yalnızca yük testinde test denetleyicisi ve test aracıları kullanıyorsa görüntülenir. Yük testi çalıştırması sırasında kullanılan aracıların listesini görüntüler. Agents tablosu, aracı tarafından test edilen istek sayısı ve bu isteklerden kaç tane başarısız olduğunu içerir. Ayrıca Agents tablosu, aracı tarafından test edilen yük testleri test karışımında testlerin sayısını ve başarısız olan test sayısını içerir.|
|Test Ayrıntıları|Yük testi için test karışımına dahil edilen testlerin ayrıntılarını görüntüler. Ayrıntılar arasında testin adı, testin içinde olduğu senaryo, testin başladığı süre, testin çalışması için geçen süre ve testin başarılı olup olmadığını gösteren test sonucu yer aldı. Test başarısız olursa Ayrıntılar sütununda bir **bağlantı** mevcuttur. Başarısız istek vurgulanmış şekilde sizi Web Performans Testi Düzenleyicisi bağlantıyı seçebilirsiniz.|

## <a name="collect-percentile-data"></a>Yüzdebirlik verileri toplama

Bazı yük testi tabloları, yüzdebirlik verileri ve ağ öykünmesi temel alınarak gruplara ayrılırken yanıt sürelerini içeren ek sütunlar içerebilir. Varsayılan olarak, bu veriler toplanmaz. Yüzdebirlik verileri yalnızca sonuçları bir veritabanına kaydederek yerel olarak kaydetmeden kullanılabilir. Daha fazla bilgi [için, Load Test Sonuçları Repository](../test/manage-load-test-results-in-the-load-test-results-repository.md)'de yük testi sonuçlarını yönetme. Buna ek olarak, bu verileri **toplamak için Yük Testi Düzenleyicisi** altında, Çalışma Ayarlar altında, değiştirilen belirli bir çalıştırma ayarı düğümünü seçin.  Özellikler **penceresinde,** Timing **Details** Depolama **statisticsOnly** veya **AllIndividualDetails öğesini seçin.** Daha fazla bilgi için, [bkz. How to: View web page response](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>Requests tablosu

Requests **tablosu,** bir yük testi sırasında verilen tek tek isteklerin ayrıntılarını görüntüler. Buna tüm HTTP istekleri ve görüntüler gibi bağımlı istekler dahildir. İsteklerden biri birçok teste ve senaryoya dahil edilebilir olduğundan tablo, istekleri teste ve senaryoya göre listeler.

Aşağıdaki tabloda **Requests** tablosunda yer alan sütunlar liste edilmektedir:

|Sütun|Açıklama|Varsayılan Olarak Görünür|
|-|-|-|
|**İstek**|İsteğin URL'si. Örneğin, *home.html* veya *orange-arrow.gif.*|Yes|
|**Senaryo**|Senaryonun adı.|Yes|
|**Test**|Testin adı.|Yes|
|**Toplam**|Yük testi çalıştırması sırasında verilen bu web performansı test isteğinin toplam sayısı. Toplam, geçirilen ve başarısız istekleri içerir, ancak web sunucusuna alınmama nedeniyle önbelleğe alınmış istekleri dahil değildir.|Yes|
|**Geçirilen**|İsteğin kaç kez ve kaç kez geçirildi?|Hayır|
|**Başarısız**|İsteğin kaç kez verilen ve başarısız olduğu. Bu sütundaki girişler köprü olarak görünür. Yük Testi Hataları iletişim kutusunda tek tek hataların listesini görüntülemek için **herhangi bir köprü** seçebilirsiniz. Daha fazla bilgi için [bkz. Yük testi sonuçlarını analiz etme.](../test/analyze-load-test-results-using-the-load-test-analyzer.md)|Yes|
|**Önbelleğe alınmış**|İsteğin toplam önbelleğe alınma sayısı.|Hayır|
|**İstekler/Sn**|Yük testi çalıştırması sırasında isteğin saniye başına hızı.|Hayır|
|**Geçilen/sn**|Bu isteğin geçirildiği örnekleri için yük testi çalıştırması sırasında bu isteğin saniye oranı.|Hayır|
|**Başarısız/sn**|Bu isteğin başarısız olduğu örnekler için yük testi çalıştırması sırasında bu isteğin saniye oranı.|Hayır|
|**İlk bayt süresi**|İsteğin Web sunucusuna gönderilme zamanından itibaren ölçülen ilk baytın alınacağı ortalama süre. Birimler saniyedir.|Hayır|
|**Yanıt süresi**|İsteğin Web sunucusuna gönderilme zamanından itibaren ölçülen tüm yanıtı almak için geçen ortalama süre. Birimler saniyedir.|Yes|
|**İçerik uzunluğu**|İsteğin yanıt içeriğinin ortalama uzunluğu. Birimler bayttır.|Yes|

## <a name="the-tests-table"></a>Testler tablosu

**Testler** tablosu, bir yük testi sırasında bireysel testlerin ayrıntılarını görüntüler. Bir test birçok senaryoya dahil olabileceğinden, bu tablo testleri test ve senaryoya göre listeler.

Aşağıdaki tabloda, **testler** tablosundaki sütunlar listelenmektedir.

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|**Test**|Testin adı.|Yes|
|**Senaryo**|Senaryonun adı.|Yes|
|**Toplam**|Senaryoda testin toplam kaç kez çalıştırıldığı. Bu, testin kaç kez geçtiğini ve başarısız olduğunu içerir.|Yes|
|**Geçiril**|Testin senaryoda kaç kez çalıştırıldığı ve geçirildiği sayı.|Yes|
|**Başarısız**|Testin senaryoda kaç kez çalıştırıldığını ve başarısız olduğunu. Bu sütundaki girişler köprü olarak görüntülenir. **Yük testi hataları** iletişim kutusunda bireysel hataların bir listesini görüntülemek için herhangi bir köprü seçebilirsiniz. Daha fazla bilgi için bkz. [Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Yes|
|**Test/sn**|Yük testi çalışması sırasında testin saniye başına hızı.|Yes|
|**Geçilen/sn**|Bu testin geçirildiği örnekleri için yük testi çalıştırması sırasında bu testin saniye oranı.|Hayır|
|**Başarısız/sn**|Bu testin başarısız olan örnekleri için yük testi çalıştırması sırasında bu testin saniye oranı.|Hayır|
|**Test zamanı**|Yük testi çalıştırması sırasında testi yürütmek için geçen ortalama süre. Birimler saniyedir.|Yes|
|**%90 test zamanı**|Test süresi için 90. yüzdebirlik değeri.|Hayır|
|**%95 test zamanı**|Test süresi için 95. yüzdebirlik değeri.|Yes|
|**İstek/test**|Web performans testi ise, testteki ortalama istek sayısı.|Hayır|

## <a name="the-transactions-table"></a>Işlem tablosu

**İşlemler** tablosu, yük testi çalıştırması sırasında oluşan işlemlerin listesini görüntüler. İşlemler, bir Web performans testinde tanımlanan işlemlere veya birim testinde tanımlanan zamanlayıcılara başvurur. İşlem veritabanı işlemlerine başvurmuyor.

Aşağıdaki tabloda, **işlemler** tablosundaki sütunlar listelenmektedir.

> [!NOTE]
> tüm sütunları görüntülemek için, etkin çalışma ayarıyla ilişkili olan zamanlama ayrıntıları Depolama özelliğini etkinleştirmeniz gerekir. daha fazla bilgi için bkz. [nasıl yapılır: zamanlama ayrıntıları Depolama özelliği belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Sütun|Açıklama|Zamanlama ayrıntıları olmadan görünür|
|-|-|-|
|**İşlem**|İşlemin adı.|Yes|
|**Senaryo**|Senaryonun adı.|Yes|
|**Test**|Testin adı.|Yes|
|**Toplam**|Yük testi çalışması sırasında verilen toplam işlem sayısı.|Yes|
|**İşlem saati**|Yük testi çalışması sırasında işlemin yürütülmesi için geçen süre. Web performans testlerinde düşünme süresi hesaplamaya dahil edilir. Birimler saniyedir.|Hayır|
|**Yanıt süresi**|Yük testi çalıştırmasında Web performans testi işlemi için yanıt süresi. Yanıt süresi, bu yanıt süresi içinde Işlem zamanından farklıdır ve işlem sırasında oluşan düşünme süresini içermez. Birimler saniyedir.|Hayır|
|**Ave. Işlem zamanı**|Ortalama işlem süresi. Bu zaman, düşünme sürelerini içerir. Örneğin, üç isteğiniz varsa ve her biri bir düşünme süresine sahipse, bu zaman bu düşünme sürelerini ve isteklerin yürütülecek gerçek zamanı içerir.|Hayır|
|**Yanıt Süresi**|Yük testi çalıştırması içinde web performansı test işlemi için ortalama yanıt süresi. Yanıt Süresi, İşlem Zamanından farklıdır ve Yanıt Süresi işlem sırasında meydana gelen herhangi bir düşünme süresi içermez. Birimler saniyedir.|Hayır|
|**En Az Yanıt Süresi**|Buna düşünme süreleri dahil değildir.|Hayır|
|**En Uzun Yanıt Süresi**|Buna düşünme süreleri dahil değildir.|Hayır|
|**Ortan Yanıt Süresi**|Buna düşünme süreleri dahil değildir.|Hayır|
|**%90 Yanıt Süresi**|İşlem Süresi için 90. yüzdebirlik değer. Buna düşünme süreleri dahil değildir. **Not:**  Bu, %90 İşlem Visual Studio kullanılan Visual Studio Team System **2008 Test Yük Aracısı'dan** farklıdır.|Hayır|
|**%95 Yanıt Süresi**|İşlem Süresi için 95. yüzdebirlik değer. Buna düşünme süreleri dahil değildir. **Not:**  Bu, %95 İşlem Süresi değerini Visual Studio Team System 2008 Test Yük **Aracısı'dan farklıdır.**|Hayır|
|**%99 Yanıt Süresi**|İşlem Süresi için 99. yüzdebirlik değer. Buna düşünme süreleri dahil değildir.|Hayır|
|**Std Dev Yanıt Süresi**|Buna düşünme süreleri dahil değildir.|Hayır|

## <a name="the-errors-table"></a>Errors tablosu

Yük testi çalıştırarak oluşan hataları analiz edin. Hataları analiz etmek ve testlerinizi ayarlamak, yük testi işleminin önemli bir kısmıdır. Herhangi bir hata oluştu **ise** yük testi durum çubuğunda bir hata köprüsü görünür ve oluşan hata sayısını belirtir. Hatalar tablosu görüntülemek için köprüyü seçersiniz.

Errors tablosu, yük testi sırasında oluşan hataları hatanın türüne ve alt türüne göre gruplar. Tabloda, **oluşan** tüm hataların toplam sayısını belirten bir toplam satır da vardır.

Errors tablosu aşağıdaki sütunları içerir:

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|Tür|Hatanın türü. Örneğin, HttpError.|Yes|
|SubType|Hatanın alt türü. Örneğin, LoadTestException.|Yes|
|Count|Yük testi sırasında oluşan bu tür hataların sayısı. Bu sütundaki girişler köprü olarak görünür. Tek tek hataların listesini görüntülemek için herhangi bir köprü seçebilirsiniz.|Yes|
|Son İleti|Hatayı açıklayan bir ileti. Örneğin, 404 - NotFound.|Yes|

Daha fazla bilgi için [bkz. Yük testi tabloları ile çalışma.](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

### <a name="drill-down-to-the-error-list"></a>Hata listesinde detaya gitme

errors tablosu hataları hatanın türüne ve alt türüne göre gruplar. Tek tek hataların bir tabloyu görüntülemek için Yük Testi **Hataları iletişim kutusunu** görüntülersiniz. İletişim kutusunu görüntülemek için hatalar tablonun **Sayı sütununda** bir köprü seçin. İletişim kutusunu, doldurulan hatalar tablosunda bir satıra sağ tıklar ve Hatalar'ı seçerek de **görüntüebilirsiniz.**

> [!NOTE]
> Herhangi bir hata türü ve alt tür bileşiminin yalnızca ilk 1.000 örneği toplanır. Yük Testi Hataları **iletişim kutusunu görüntülerken,** bu hatanın en çok ilk 1.000 örneğini görüyorsunuz.

Yük **Testi Hataları tablosu** aşağıdaki sütunları içerir:

|Sütun|Açıklama|
|-|-|
|**Saat**|Yük testi sırasında hatanın meydana geldiği zaman.|
|**Aracı**|Hatanın meydana geldiği aracı bilgisayarın adı. Bu, test denetleyicilerini ve test aracılarını kullanarak yük testleri çalıştırsanız önemlidir. Daha fazla bilgi için [bkz. Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)|
|**Test**|Hatanın meydana geldiği web performans testinin adı.|
|**Senaryo**|Hatanın meydana geldiği senaryonun adı.|
|**İstek**|Hatanın meydana geldiği isteğin URL'si.|
|**Tür**|Hatanın türü. Örneğin, HttpError.|
|**Alt**|Hatanın alt türü. Örneğin, LoadTestException.|
|**Metin**|Hata iletisinin metni. Örneğin, 404 - NotFound.|
|**Yığın**|Bu sütundaki girişler boş veya **Stack** sözcüğü köprü olarak biçimlendirildi. Hatanın yığın izlemesini görüntülemek için köprüyü seçebilirsiniz.|
|**Ayrıntılar**|Bu sütundaki girişler boş veya **TestLog** sözcüğü köprü olarak biçimlendirildi. Bu bağlantı, hataları Yük testinde yalıtmanıza yardımcı olabilir. Örneğin, bir Web performans testi isteği hatası üzerinde **TestLog** bağlantısını seçmek Web performans testi Için sonuçları web performans test sonuçları görüntüleyicisinde açar ve istek hatasını vurgulayacaktır.|

> [!NOTE]
> Sütun üstbilgilerini seçerek tabloyu sıralayabilirsiniz.

## <a name="the-sql-trace-data-table"></a>SQL izleme verileri tablosu

daha sonra analiz etmek üzere bir yük testi çalıştırması sırasında SQL izleme verileri toplayabilirsiniz. izleme verilerini toplamak, sınanan SQL Server veritabanında en yavaş çalışan sorguları ve saklı yordamları belirlemenize olanak sağlar.

SQL izleme etkinse, izleme verilerini içeren yük testi çalıştırması sırasında bir dosya oluşturulur. Bu veriler, Test çalıştırmasının sonundaki Load Test Sonuçları deposuna otomatik olarak kaydedilir ve izleme dosyası silinir. yük testiniz tamamlandıktan sonra, **SQL izleme** tablosundaki izleme verilerini çözümleyebilirsiniz.

### <a name="to-view-sql-trace-data"></a>SQL izleme verilerini görüntülemek için

1. Yük Testi Çözümleyicisi 'nde tablo kılavuzunun görüntülendiğinden emin olmak için araç çubuğunda **Tablolar** ' ı seçin.

2. **tablo** aşağı açılan liste kutusunda **SQL Trace**' i seçin.

3. Çalıştırma sırasında toplanan izleme verileri kılavuzda görüntülenir. tabloda, en yavaş en üst kısımdaki şekilde, süreye göre sıralanan en yavaş çalışan SQL işlemleri listelenir. Genellikle, **Duration** sütunu incelenecek ilk sütundur. Veriler milisaniye cinsinden görüntülenir.

   Görüntülenen sütunlar aşağıdaki gibidir:

    - **Event sınıfı**

    - **Süre**

    - **CPU**

    - **Okumalar**

    - **Yazmalar**

    - **TextData**

    - **StartTime**

    - **EndTime**

   bu sütunlarda tanımlanan verilerden farklı SQL olaylarını izlemek isterseniz, SQL profil oluşturucu aracını kullanarak kendi özel SQL izlemeyi Visual Studio 'den ayrı olarak ayarlayabilirsiniz.

## <a name="tile-load-test-tables"></a>Kutucuk yük testi tabloları

Bir yük testi çalıştırmasının sonuçlarını görüntülediğinizde, verileri ayrıntılı tablolar olarak görebilirsiniz. Tablo görünümüne geçiş yapmak için, **Yük testi** araç çubuğundan **Tablolar** ' ı seçin. kullanılabilir tablolar **hatalar**, **sayfalar**, **istekler**, **SQL Trace**, **testler**, **eşikler** ve **işlemlerdir**. Daha fazla bilgi için bkz. [Yük testi tablolarıyla çalışma](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Tablo görünümünde, çakışan tablolar olmadan tek seferde en fazla dört tablo görüntüleyebilirsiniz.

### <a name="to-tile-tables"></a>Tabloları döşeme

1. **Yük Testi Çözümleyicisi** araç çubuğunda **Tablolar**' ı seçin.

     Tablo görünümü açılır. Varsayılan düzen iki yatay paneldir.

2. **Yük Testi Çözümleyicisi** araç çubuğunda, **Düzen** düğmesini seçin ve ardından aşağıdaki seçeneklerden birini belirleyin:

    - **Bir panel**

    - **İki yatay panel**

    - **Üç yatay panel**

    - **Dört yatay panel**

3. Farklı tablolar arasında geçiş yapmak için, her panelde tablo kılavuzunun üstündeki açılan listeyi kullanın.

    > [!NOTE]
    > Aynı tabloyu birden fazla panelde görüntüleyemezsiniz. Bir panelde görüntülenecek tabloyu başka bir panelde zaten görüntülenmiş bir tabloya değiştirirseniz, tablolar geçiş yapar.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Nasıl yapılır: analiz için yük testi sonuçlarına erişme](../test/how-to-access-load-test-results-for-analysis.md)
- [Grafik görünümünde Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Eşik Kuralı İhlallerini Çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Yük Test Sonuçları deposundaki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Yük testi sonuçları özetine genel bakış](../test/load-test-results-summary-overview.md)
