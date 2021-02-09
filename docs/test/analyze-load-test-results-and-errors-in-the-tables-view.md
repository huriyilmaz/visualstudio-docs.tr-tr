---
title: Yükleme Test Sonuçları ve hatalarını çözümleme
description: Bir yük testi çalıştırmasının sonuçlarını çözümlemek için zaman veya ayrıntılı tablolar gibi farklı yollar sağlayan bölmeleri nasıl görüntüleyeceğinizi öğrenin.
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
ms.openlocfilehash: 5b501cef5360be08f1b283e9064617b649a33da9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878025"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Yük Testi Çözümleyicisinin Tablo görünümündeki yük testi sonuçlarını ve hatalarını çözümleme

Bir yük testi çalıştırmasının sonuçlarını görüntülediğinizde, verileri çözümlemek için farklı yollar sağlayan farklı bölmeleri görüntüleyebilirsiniz. Verileri bir grafik olarak görüntüleyebilir, zaman içinde nasıl değişiklik yapıldığını görebilir veya verileri ayrıntılı tablolar olarak görüntüleyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Tablo görünümüne geçiş yapmak için, **Yük testi** araç çubuğundan **Tablolar** ' ı seçin. Farklı tablolar arasında geçiş yapmak için tablo kılavuzunun üzerindeki araç çubuğundan **tablo** açılan listesini kullanın. Tablo görünümünde, bir seferde en fazla dört tablo görüntüleyebilirsiniz. Daha fazla bilgi için bu konudaki [kutucuk yük testi tabloları](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) bölümüne bakın.

Performans sayaçları için bir tabloda görüntülenen en büyük sayısal değerler, yük testi çalıştırmasının tamamına göre birikimlidir. **Last** adlı sütunlar özel bir durumdur ve en son örnekleme aralığından değeri temsil eder.

> [!NOTE]
> **Last** adlı sütunlar yalnızca bir yük testi yürütülürken kullanılabilir. Bir yük testi tamamlandıktan sonra, bu sütunlar kullanılamaz.

Sıralamak istediğiniz sütunun başlığını seçerek çoğu tabloyu sıralayabilirsiniz. Varsayılan olarak, bazı tablolar tüm kullanılabilir sütunları görüntülemez. Sütunlar kullanılabiliyorsa tablolara sütun ekleyebilirsiniz. Sütun eklemek için tabloya sağ tıklayıp **sütun Ekle/Kaldır**' ı seçin.

> [!NOTE]
> Bir tablodaki verileri daha fazla analiz için Excel gibi başka uygulamalara kopyalayabilirsiniz.

## <a name="the-load-test-tables"></a>Yük testi tabloları

Aşağıdaki tabloda, yük testi çalıştırmalarını çözümlemek için kullanılabilen tablolar listelenmektedir.

|Tablo Adı|Description|
|-|-|
|Hatalar|Yük testi çalıştırması sırasında oluşan hataların listesini görüntüler. Daha fazla bilgi için bu konudaki [hatalar tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) bakın ve [Yük testi sonuçlarını çözümleyin](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Sayfalar|Yük testi çalıştırması sırasında erişilen sayfaların listesini görüntüler. Bu tablodaki bazı veriler yalnızca bir yük testi tamamlandıktan sonra kullanılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: Web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|İstekler|Bir yük testi sırasında verilen bireysel isteklerin ayrıntılarını görüntüler. Bu, tüm HTTP isteklerini ve görüntüler gibi bağımlı istekleri içerir. Daha fazla bilgi için bu konudaki [istekler tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) bakın.|
|SQL Izleme|SQL izlemenin sonuçlarını görüntüler. Bu tablo yalnızca bir yük testi tamamlandıktan sonra ve test sırasında SQL izleme kullanılmışsa kullanılabilir. Daha fazla bilgi için bu konudaki [SQL izleme verileri tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) bakın.|
|Testler|Bir yük testi sırasında bireysel testlerin ayrıntılarını görüntüler. Daha fazla bilgi için bu konudaki [testler tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) bakın.|
|Leriyle|Yük testi çalıştırması sırasında oluşan eşik kuralı ihlallerinin bir listesini görüntüler. Daha fazla bilgi için bkz. [eşik kuralı Ihlallerini çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|İşlemler|Yük testi çalıştırması sırasında oluşan işlemlerin listesini görüntüler. Daha fazla bilgi için bu konudaki [işlemler tablosuna](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) bakın.|
|Aracılar|Yalnızca yük testiniz bir test denetleyicisi ve test aracıları kullanıyorsa görüntülenir. Yük testi çalıştırması sırasında kullanılan aracıların listesini görüntüler. Aracılar tablosu, aracının kaç istek ve bu isteklerden test edildiğini, kaç tane başarısız olduğunu içerir. Ayrıca, aracılar tablosu, aracının test ettiği Test karışımındaki testlerin sayısını ve bunların kaç tane başarısız olduğunu içerir.|
|Test ayrıntıları|Yük testi için test karışımına dahil edilen testlerin ayrıntılarını görüntüler. Ayrıntılar arasında testin adı, testin içinde bulunduğu senaryo, testin başladığı zaman uzunluğu ve testin başarılı veya başarısız olduğunu belirten test sonucu yer alır... Test başarısız olursa, **Ayrıntılar** sütununda bir bağlantı bulunur. Sizi başarısız istek vurgulandığı Web Performans Testi Düzenleyicisi sizi alacak bağlantıyı seçebilirsiniz.|

## <a name="collect-percentile-data"></a>Yüzdelik veri topla

Bazı yük testi tabloları, ağ öykünmesine göre gruplara bölünen yüzdelik verileri ve yanıt sürelerini içeren ek sütunlar içerebilir. Varsayılan olarak, bu veriler toplanmaz. Yüzdelik veri yalnızca sonuçları bir veritabanına kaydettiğinizde ve yerel olarak kaydettiğinizde kullanılabilir. Daha fazla bilgi için bkz. [load test sonuçları deposunda yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md). Ayrıca, bu verileri toplamak için **Yük Testi Düzenleyicisi**, **çalışma ayarları** düğümü altında, değiştirilecek belirli çalışma ayarı düğümünü seçin. **Özellikler** penceresinde, **Zamanlama Ayrıntıları Deposu** özelliği için, **StatisticsOnly** veya **allindividualdetails**' i seçin. Daha fazla bilgi için bkz. [nasıl yapılır: Web sayfası yanıtını görüntüleme](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>Istekler tablosu

**İstekler** tablosu, bir yük testi sırasında verilen bireysel isteklerin ayrıntılarını görüntüler. Bu, tüm HTTP isteklerini ve görüntüler gibi bağımlı istekleri içerir. Bir istek birçok teste ve senaryoya dahil olabileceğinden, bu tablo, test ve senaryoya göre istekleri listeler.

Aşağıdaki tabloda **istekler** tablosundaki sütunlar listelenmektedir:

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|**İstek**|İsteğin URL 'SI. Örneğin, *home.html* veya *orange-arrow.gif*.|Yes|
|**Senaryo**|Senaryonun adı.|Yes|
|**Test**|Testin adı.|Yes|
|**Toplam**|Yük testi çalıştırması sırasında verilen bu Web performans testi isteğinin toplam sayısı. Toplam geçen ve başarısız istekleri içerir, ancak Web sunucusuna verilmediğinden önbelleğe alınmış istekleri içermez.|Yes|
|**Geçiril**|İsteğin kaç kez verildiğini ve geçtiğini.|Hayır|
|**Başarısız**|İsteğin kaç kez verildiğini ve başarısız olduğunu. Bu sütundaki girişler köprü olarak görüntülenir. **Yük testi hataları** iletişim kutusunda bireysel hataların bir listesini görüntülemek için herhangi bir köprü seçebilirsiniz. Daha fazla bilgi için bkz. [Yük testi sonuçlarını çözümleme](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Yes|
|**Önbelleğe alınmış**|İsteğin önceden önbelleğe alınma toplam sayısı.|Hayır|
|**İstek/sn**|Yük testi çalışması sırasında isteğin saniye başına oranı.|Hayır|
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
> Tüm sütunları görüntülemek için, etkin çalışma ayarıyla ilişkili zamanlama ayrıntıları depolama özelliğini etkinleştirmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: zamanlama ayrıntıları depolama özelliğini belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Sütun|Açıklama|Zamanlama ayrıntıları olmadan görünür|
|-|-|-|
|**İşlem**|İşlemin adı.|Yes|
|**Senaryo**|Senaryonun adı.|Yes|
|**Test**|Testin adı.|Yes|
|**Toplam**|Yük testi çalışması sırasında verilen toplam işlem sayısı.|Yes|
|**İşlem saati**|Yük testi çalışması sırasında işlemin yürütülmesi için geçen süre. Web performans testlerinde düşünme süresi hesaplamaya dahil edilir. Birimler saniyedir.|Hayır|
|**Yanıt süresi**|Yük testi çalıştırmasında Web performans testi işlemi için yanıt süresi. Yanıt süresi, bu yanıt süresi içinde Işlem zamanından farklıdır ve işlem sırasında oluşan düşünme süresini içermez. Birimler saniyedir.|Hayır|
|**Ave. Işlem zamanı**|Ortalama işlem süresi. Bu kez düşünme süreleri de dahildir. Örneğin, üç isteğiniz varsa ve her birinin bir düşünme zamanı varsa, bu kez isteklerin yürütülmesi için bu düşünme süreleri ve gerçek zaman dahil edilir.|Hayır|
|**Ort. yanıt süresi**|Bir yük testi çalıştırmasında bir Web performans testi işlemi için Ortalama yanıt süresi. Yanıt süresi, bu yanıt süresi içinde Işlem zamanından farklıdır ve işlem sırasında oluşan düşünme süresini içermez. Birimler saniyedir.|Hayır|
|**En az yanıt süresi**|Bu, düşünme süreleri içermez.|Hayır|
|**En fazla yanıt süresi**|Bu, düşünme süreleri içermez.|Hayır|
|**Ortanca yanıt süresi**|Bu, düşünme süreleri içermez.|Hayır|
|**%90 yanıt süresi**|Işlem zamanı için 90. yüzdebirlik değeri. Bu, düşünme süreleri içermez. **Note:**  Bu, **%90 Işlem süresi** değerini kullanan Visual Studio Team System 2008 test yük aracısından farklıdır.|Hayır|
|**%95 yanıt süresi**|Işlem zamanı için 95. yüzdebirlik değeri. Bu, düşünme süreleri içermez. **Note:**  Bu, **%95 Işlem süresi** değerini kullanan Visual Studio Team System 2008 test yük aracısından farklıdır.|Hayır|
|**%99 yanıt süresi**|Işlem zamanı için 99. yüzdebirlik değeri. Bu, düşünme süreleri içermez.|Hayır|
|**STD dev yanıt süresi**|Bu, düşünme süreleri içermez.|Hayır|

## <a name="the-errors-table"></a>Hatalar tablosu

Bir yük testi çalıştırdığınızda oluşan hataları çözümleyebilirsiniz. Hataları çözümleme ve testlerinizi ayarlama, yük testi sürecinin önemli bir parçasıdır. Herhangi bir hata oluştuysa, yük testi durum çubuğunda bir **hata** Köprüsü görüntülenir ve oluşan hata sayısını belirtir. Hatalar tablosunu göstermek için köprüyü seçersiniz.

Hatalar tablosu, hatanın türü ve alt türü tarafından bir yük testi sırasında oluşan hataları gruplandırır. Ayrıca, tabloda gerçekleşen tüm hataların toplam sayısını belirten **Toplam** bir satır vardır.

Hatalar tablosu şu sütunları içerir:

|Sütun|Açıklama|Varsayılan olarak görünür|
|-|-|-|
|Tür|Hatanın türü. Örneğin, HttpError.|Yes|
|SubType|Hatanın alt türü. Örneğin, LoadTestException.|Yes|
|Count|Bu türün yük testi sırasında oluşan hata sayısı. Bu sütundaki girişler köprü olarak görüntülenir. Bireysel hataların bir listesini görüntülemek için herhangi bir köprü seçebilirsiniz.|Yes|
|Son Ileti|Hatayı açıklayan bir ileti. Örneğin, 404-NotFound.|Yes|

Daha fazla bilgi için bkz. [Yük testi tablolarıyla çalışma](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Hata listesinin detayına gitme

Hatalar tablosu hatanın türüne ve alt türüne göre hataları gruplandırır. Bireysel hataların bir tablosunu görüntülemek için **Yük testi hataları** iletişim kutusunu görüntüleyin. İletişim kutusunu göstermek için, hatalar tablosunun **say** sütununda bir köprü seçin. Ayrıca, doldurulmuş hatalar tablosundaki bir satıra sağ tıklayıp **hatalar**' ı seçerek iletişim kutusunu da görüntüleyebilirsiniz.

> [!NOTE]
> Herhangi bir hata türü ve alt tür birleşiminin yalnızca ilk 1.000 örneği toplanır. **Yük testi hataları** iletişim kutusunu görüntülediğinizde, hata oluşan en fazla ilk 1.000 örneği görürsünüz.

**Yük testi hataları** tablosu şu sütunları içerir:

|Sütun|Açıklama|
|-|-|
|**Saat**|Hatanın gerçekleştiği yük testi sırasında geçen süre.|
|**Aracısı**|Hatanın gerçekleştiği aracı bilgisayarın adı. Test denetleyicileri ve test aracıları kullanarak yük testlerini çalıştırdığınızda bu önemlidir. Daha fazla bilgi için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Hatanın oluştuğu Web performans testinin adı.|
|**Senaryo**|Hatanın oluştuğu senaryonun adı.|
|**İstek**|Hatanın gerçekleştiği isteğin URL 'SI.|
|**Tür**|Hatanın türü. Örneğin, HttpError.|
|**SubType**|Hatanın alt türü. Örneğin, LoadTestException.|
|**Metin**|Hata iletisinin metni. Örneğin, 404-NotFound.|
|**Yığın**|Bu sütundaki girişler boştur ya da Word **yığını** bir köprü olarak biçimlendirilir. Hatanın yığın izlemesini görüntülemek için köprüyü seçebilirsiniz.|
|**Ayrıntılar**|Bu sütundaki girişler boş ya da **TestLog** sözcüğü köprü olarak biçimlendirilir. Bu bağlantı, hataları Yük testinde yalıtmanıza yardımcı olabilir. Örneğin, bir Web performans testi isteği hatası üzerinde **TestLog** bağlantısını seçmek Web performans testi Için sonuçları web performans test sonuçları görüntüleyicisinde açar ve istek hatasını vurgulayacaktır.|

> [!NOTE]
> Sütun üstbilgilerini seçerek tabloyu sıralayabilirsiniz.

## <a name="the-sql-trace-data-table"></a>SQL Izleme verileri tablosu

Daha sonra analiz etmek üzere bir yük testi çalıştırması sırasında SQL izleme verileri toplayabilirsiniz. İzleme verilerini toplamak, sınanan SQL Server veritabanında en yavaş çalışan sorguları ve saklı yordamları belirlemenize olanak sağlar.

SQL izleme etkinse, izleme verilerini içeren yük testi çalıştırması sırasında bir dosya oluşturulur. Bu veriler, Test çalıştırmasının sonundaki Load Test Sonuçları deposuna otomatik olarak kaydedilir ve izleme dosyası silinir. Yük testiniz tamamlandıktan sonra **SQL izleme** tablosundaki izleme verilerini çözümleyebilirsiniz.

### <a name="to-view-sql-trace-data"></a>SQL izleme verilerini görüntülemek için

1. Yük Testi Çözümleyicisi 'nde tablo kılavuzunun görüntülendiğinden emin olmak için araç çubuğunda **Tablolar** ' ı seçin.

2. **Tablo** aşağı açılan liste kutusunda **SQL Trace**' i seçin.

3. Çalıştırma sırasında toplanan izleme verileri kılavuzda görüntülenir. Tabloda, en yavaş en üst kısımdaki şekilde, süreye göre sıralanan en yavaş çalışan SQL işlemleri listelenir. Genellikle, **Duration** sütunu incelenecek ilk sütundur. Veriler milisaniye cinsinden görüntülenir.

   Görüntülenen sütunlar aşağıdaki gibidir:

    - **Event sınıfı**

    - **Süre**

    - **CPU**

    - **Okumalar**

    - **Yazmalar**

    - **TextData**

    - **StartTime**

    - **EndTime**

   Bu sütunlarda tanımlanan verilerden farklı SQL olaylarını izlemek isterseniz, Visual Studio 'dan ayrı olarak SQL Profiler aracını kullanarak kendi özel SQL izlemenizi ayarlayabilirsiniz.

## <a name="tile-load-test-tables"></a>Kutucuk yük testi tabloları

Bir yük testi çalıştırmasının sonuçlarını görüntülediğinizde, verileri ayrıntılı tablolar olarak görebilirsiniz. Tablo görünümüne geçiş yapmak için, **Yük testi** araç çubuğundan **Tablolar** ' ı seçin. Kullanılabilen tablolar **hatalar**, **Sayfalar**, **istekler**, **SQL izleme**, **testler**, **eşikler** ve **işlemlerdir**. Daha fazla bilgi için bkz. [Yük testi tablolarıyla çalışma](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

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
