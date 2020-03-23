---
title: Test Çalıştır Ayarlarını Yükle
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8898a474888ce9efbf4c91a5251bf8fe7036fe5f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584471"
---
# <a name="load-test-run-settings-properties"></a>Test çalıştırma ayarları özelliklerini yükleyin

Yük testinin çalışma ayarları, testin süresi, sonuç toplama ayrıntı düzeyi ve test çalıştığında toplanan sayaç kümeleri dahil olmak üzere çeşitli diğer ayarları belirler. Her yük testi için birden çok çalıştırma ayarı oluşturabilir ve depolayabilir ve testi çalıştırdığınızda kullanmak üzere belirli bir ayar seçebilirsiniz. Yeni Yük Testi Sihirbazı'nı kullanarak yük testinizi **New Load Test Wizard**oluşturduğunuzda yük testinize ilk çalıştırma ayarı eklenir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki tablolar, yük testi çalıştırma ayarları için çeşitli özellikleri açıklar. Bu özellikleri, özel yük testi gereksinimlerinizi karşılayacak şekilde değiştirebilirsiniz.

Daha fazla bilgi için [bkz.](../test/configure-load-test-run-settings.md)

## <a name="general-properties"></a>Genel özellikler

|Özellik|Tanım|
|-|----------------|
|**Açıklama**|Çalıştır Ayarları'nın açıklaması.|
|**Tür Başına Maksimum Hata**|Yük testi için kaydetmek için tür başına maksimum hata sayısı.<br /><br /> Gerekirse bu sayıyı artırabilirsiniz, ancak bunu yapmak yük testi sonucunun boyutunu ve işlem süresini de artırır.|
|**Bildirilen Maksimum İstek URL'leri**|Bu yük testinde sonuçları raporlamak için en fazla benzersiz web performans testi isteği URL'si sayısı.<br /><br /> Gerekirse bu sayıyı artırabilirsiniz, ancak bunu yapmak yük testi sonucunun boyutunu ve işlem süresini de artırır.|
|**Maksimum Eşik ihlalleri**|Bu yük testi için kaydacak maksimum eşik ihlali sayısı.<br /><br /> Gerekirse bu sayıyı artırabilirsiniz, ancak bunu yapmak yük testi sonucunun boyutunu ve işlem süresini de artırır.|
|**Uygulama etki alanında birim testleri çalıştırma**|Yük testi birim testleri içeriyorsa, her birim test derlemesinin ayrı bir uygulama etki alanında çalışıp çalışmayacağını belirleyen boolean değeri. Varsayılan ayar True'dur.<br /><br /> Birim testleridoğru çalışması için ayrı bir uygulama etki alanı veya app.config dosyası gerektirmiyorsa, birim `False`testleri bu özelliğin değerini 'ye ayarlayarak daha hızlı çalışabilir.|
|**Adı**|Yük Testi Düzenleyicisi'nin Çalışma **Ayarları** düğümünde göründüğü **Load Test Editor**gibi Çalıştır Ayarı'nın adı.|
|**Doğrulama Düzeyi**|Bu, bir yük testinde çalışacak en yüksek doğrulama kuralı düzeyini tanımlar. Doğrulama kuralları web performans testi istekleriyle ilişkilidir. Her doğrulama kuralının ilişkili bir doğrulama düzeyi vardır: **Yüksek**, **Orta**veya **Düşük**. Bu yük testi çalıştırma ayarı, yük testinde web performans testi çalıştırılırken hangi doğrulama kurallarının çalıştırılacağını belirtir. Örneğin, bu çalıştırma ayarı **Orta**olarak ayarlanmışsa, **Orta**veya **Düşük** olarak işaretlenmiş tüm doğrulama kuralları çalıştırılır.|

## <a name="logging-properties"></a>Günlüğe kaydetme özellikleri

|Özellik|Tanım|
|-|----------------|
|**Maksimum Test Günlükleri**|Yük testi için kaydetmek için maksimum test günlükleri sayısını belirtir. Maksimum test günlüğü sayısı için girilen değere ulaşıldığında, yükleme testi günlükleri toplamayı durdurur. Bu nedenle, günlükleri testin başında değil, sonunda toplanır. Yük testi tamamlanana kadar çalışmaya devam edecektir.|
|**Tamamlanan Testler için Günlük Sıklığını Kaydet**|Test günlüğünün yazılma sıklığını belirtir. Numara, girilen her test sayısından birinin test günlüğüne kaydedileceğini gösterir. Örneğin, on değerini girerek onuncu, yirminci, otuzuncu ve benzeri test günlüğüne yazılacak belirtir. Değeri 0 olarak ayarlamak, hiçbir test günlüğünün kaydedilmeyeceğini belirtir.|
|**Test Hatasında Günlük Kaydetme**|Bir test bir yük testinde başarısız olursa test günlüklerinin kaydedilip kaydedilemeyeceğini belirleyen Boolean değeri. Varsayılan değer: `True`.<br /><br /> Daha fazla bilgi için [bkz: Test hatalarının test günlükleri için kaydedilip kaydedilenolmadığını belirtin](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

Daha fazla bilgi için bkz: [Yük testi günlüğe kaydetme ayarlarını değiştir.](../test/modify-load-test-logging-settings.md)

## <a name="results-properties"></a>Sonuç özellikleri

|Özellik|Tanım|
|-|----------------|
|**Depolama Türü**|Yük testinde elde edilen performans sayaçlarını depolamanın yolu. Seçenekler şunlardır:<br /><br /> -   **Veritabanı** - **Yük Testi Sonuçları Deposu**olan bir SQL veritabanı gerektirir.<br />-   **Hiç yok.**|
|**Zamanlama Ayrıntıları Depolama**|Bu, **Yük Testi Sonuçları Deposu'nda**hangi ayrıntıların depolanacağını belirlemek için kullanılır. Üç değer mevcuttur:<br /><br /> -   **AllIndividualDetails** - **Yük Testi Sonuçları Deposu'nda**yük testi sırasında çalıştırılabilen veya verilen her test, işlem ve sayfa için tek tek zamanlama değerlerini toplayın ve depolayın. Yük Testi Çözümleyicisi'nde Sanal Kullanıcı **Load Test Analyzer** **Etkinlik Grafiği'ni** kullanmak istiyorsanız gereklidir.<br />     Daha fazla bilgi için ayrıntılar [görünümünde sanal kullanıcı etkinliğini analiz et'](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)e bakın.<br />-   **Yok** - Bireysel zamanlama değerlerini toplamayın. Bu Visual Studio 2013 Güncelleştirme 4 ve daha sonraki sürümleri için varsayılan değerdir.<br />-   **StatisticsOnly** - **Yük Testi Sonuçları Deposu'nda**yük testi sırasında gerçekleştirilen veya verilen her test, işlem ve sayfa için tek tek zamanlama değerlerini depolamak yerine yalnızca istatistikleri toplayın ve depolayın.<br /><br /> Daha fazla bilgi için [bkz: Zamanlama ayrıntıları depolama özelliğini belirtin.](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|

## <a name="sql-tracing-properties"></a>SQL izleme özellikleri

|Özellik|Tanım|
|-|----------------|
|**İzlenmiş SQL İşlemlerinin Minimum Süresi**|Sql Trace tarafından milisaniye cinsinden yakalanacak bir SQL işleminin minimum süresi. Örneğin, bu, yük altında yavaş olan SQL işlemlerini bulmaya çalışıyorsanız, hızla tamamlanan işlemleri yoksaymanızı sağlar.|
|**SQL İzleme Bağlantı Dizesi**|İzlenecek veritabanına erişmek için kullanılan bağlantı dizesi.|
|**SQL İzleme Dizini**|İzleme sona erdikten sonra SQL Trace dosyasının konulduğu konum. Bu dizin, SQL Server için yazma izinlerine ve denetleyici için izinleri okumalıdır.|
|**SQL İzleme Etkin**|Bu, SQL işlemlerinin izlenmesini sağlar. Varsayılan değer: `False`.|

## <a name="test-iterations-properties"></a>Yineleme özelliklerini test edin

|Özellik|Tanım|
|-|----------------|
|**Test Yinelemeleri**|Yük testi tamamlanmadan önce çalışacak tek tek testlerin toplam sayısını belirtir. Bu özellik yalnızca "Test Yinelemelerini Kullan" özelliği. `True`|
|**Test Yinelemelerini Kullanma**|Test Yinelemeleri'ni `True`Kullan ise, yük testi, yük testi içinde tamamlanan tek tek test sayısı "Test Yinelemeleri" özelliğinde belirtilen sayıya ulaşana kadar çalışır. Bu durumda, Süre, Çalışma Süresi ve Soğuma Süresi Olan Zaman Tabanlı ayarlar yoksayılır. "Test Yinelemelerini Kullan" `False`ise, tüm zamanlama ayarları uygulanır ve "Test Yinelemeleri" yoksayılır.|

Daha fazla bilgi için [bkz: Çalışma ortamındatest yinelemelerinin sayısını belirtin.](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)

## <a name="timing-properties"></a>Zamanlama özellikleri

|Özellik|Tanım|
|-|----------------|
|**Soğuma Süresi**|Test soğuma süresi, hh:mm:ss formatında ifade edilir. Yük testi bittiğinde, yük testi içindeki tek tek testler çalışmaya devam ediyor olabilir. Soğuma süresi boyunca, bu testler tamamlanana veya soğuma süresinin sonuna ulaşılına kadar devam edebilir. Varsayılan olarak, bekleme süresi yoktur ve yük testi Çalışma Süresi ayarını temel alarak bittiğinde tek tek testler sonlandırılır.|
|**Çalışma Süresi**|Testin uzunluğu, hh:mm:ss formatında.|
|**Örnek Oranı**|Hh:mm:ss formatında performans sayacı değerlerini yakalama aralığı.<br /><br /> Daha fazla bilgi için [bkz: Örnek oranını belirtin.](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Isınma Süresi**|Testin başlangıcı ile veri örneklerinin kayda başlandığı dönem, hh:mm:ss biçiminde. Bu, örnek değerleri kaydetmeden önce belirli bir yük düzeyine ulaşmak için sanal kullanıcıları yüklemek için sıklıkla kullanılır. Isınma dönemi sona ermeden önce yakalanan örnek değerler **Yük Testi Çözümleyicisi'nde**gösterilir.|

## <a name="webtest-connections-properties"></a>WebTest bağlantı özellikleri

|Özellik|Tanım|
|-|----------------|
|**WebTest Bağlantı Modeli**|Bu, yük testi aracısından web sunucusuna, yük testi içinde çalışan web performans testleri için bağlantıların kullanımını denetler. Üç web performans testi bağlantı modeli seçeneği mevcuttur:<br /><br /> - **Kullanıcı Başına Bağlantı** modeli, gerçek bir tarayıcı kullanan bir kullanıcının davranışını simüle eder. Internet Explorer 6 veya Internet Explorer 7 simüle edildiğinde, web performans testi çalıştıran her sanal kullanıcı web sunucusuna bir veya iki özel bağlantı kullanır. Web performans testindeki ilk istek yayımlandığında ilk bağlantı kurulur. Bir sayfa birden fazla bağımlı istek içeriyorsa ikinci bir bağlantı kullanılabilir. Bu istekler iki bağlantı kullanılarak paralel olarak verilir. Bu bağlantılar, web performans testinde sonraki istekler için yeniden kullanılır. Web performans testi bittiğinde bağlantılar kapatılır. Bu modelin bir dezavantajı, aracı bilgisayarda açık tutulan bağlantı sayısının yüksek olmasıdır (kullanıcı yükünün en fazla iki katı). Sonuç olarak, bu yüksek bağlantı sayısını desteklemek için gereken kaynaklar, tek bir yük testi aracısından sürülebilen kullanıcı yükünü sınırlayabilir. Internet Explorer 8 simüle edildiğinde, altı eşzamanlı bağlantı desteklenir.<br />- **Bağlantı Havuzu** modeli, birden çok sanal web performans testi kullanıcısı arasında web sunucusuna bağlantı paylaşarak yük testi aracısı üzerindeki kaynakları korur. Kullanıcı yükü bağlantı havuzu boyutundan daha büyükse, farklı sanal kullanıcılar tarafından çalıştırılabilen web performans testleri bir bağlantıyı paylaşır. Bu, başka bir web performans testi bağlantıyı kullanırken bir web performans testinin istekte bulunmadan önce beklemesi gerekebileceği anlamına gelebilir. Bir web performans testinin bir isteği göndermeden önce beklediği ortalama süre, yük testi performans sayacı Ortalama Bağlantı Bekleme Süresi tarafından izlenir. Bu sayı, bir sayfanın ortalama yanıt süresinden daha az olmalıdır. Değilse, bağlantı havuzu boyutu büyük olasılıkla çok küçüktür.<br />- **Test Başına Bağlantı Yineleme** modeli, her test yinelemesi için özel bağlantıların kullanımını belirtir.|
|**WebTest Bağlantı Havuzu Boyutu**|Bu, yük testi aracısı ile Web sunucusu arasında yapmak için gereken maksimum bağlantı sayısını belirtir. Bu yalnızca Bağlantı **Havuzu** modeli için geçerlidir.|

## <a name="change-run-setting-properties"></a>Çalıştırma ayar özelliklerini değiştirme

Farklı koşullar altında yük testini çalıştırabilmeniz için farklı özellik ayarlarıyla yük testinize daha fazla çalıştırma ayarı ekleyebilirsiniz. Örneğin, yeni bir test ayarı ekleyebilir ve farklı bir örnek hızı kullanabilir veya daha uzun bir çalışma süresi belirtebilirsiniz. Aynı anda yalnızca bir çalıştırma ayarı kullanabilirsiniz ve etkin olarak işaretleyerek hangi çalışma ayarını kullanacağınızı belirtmeniz gerekir. Örneğin, [bkz.](../test/how-to-select-the-active-run-setting-for-a-load-test.md)

Çalışma ayarlarını değiştirmek için:

1. Bir yük testi açın.

2. Çalışma **Ayarları** klasörünü genişletin.

3. Bir **Çalıştır Ayarları** düğümü seçin.

4. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     **Özellikler Penceresi** görüntülenir ve seçili çalıştırma ayarı için özellikler görüntülenir.

5. Çalışma ayarlarını değiştirmek için **Özellikler Penceresini** kullanın. Örneğin, testinizi beş dakika çalıştırmak için çalışma süresini **00:05:00** olarak değiştirin.

    > [!NOTE]
    > Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi için [bkz.](../test/load-test-run-settings-properties.md)

6. Özellikleri değiştirmeyi bitirdiğinizde, yük testinizi kaydedin. **Dosya** menüsünde **Kaydet'i**seçin.

> [!NOTE]
> Sayaç kümesi eşlemeleri de çalışma ayarlarının bir parçasıdır. Daha fazla bilgi için [bkz.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
