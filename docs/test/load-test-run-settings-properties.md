---
title: Yük testi çalıştırma ayarları
description: Her yük testi için birden fazla çalışma ayarı oluşturmayı ve depolamayı öğrenin ve ardından testi çalıştırdığınızda kullanılacak belirli bir ayarı seçin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 651d3937e51be4ec1deeb748f2e4f32cfd08ee81
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329256"
---
# <a name="load-test-run-settings-properties"></a>Yük testi çalıştırma ayarları özellikleri

Yük testinin çalışma ayarları, testin süresi, sonuç koleksiyonu ayrıntı düzeyi ve test çalışırken toplanan sayaç kümeleri dahil olmak üzere çeşitli diğer ayarları belirler. Her bir yük testi için birden fazla çalışma ayarı oluşturup depolayabilmeniz ve sonra testi çalıştırdığınızda kullanılacak belirli bir ayarı seçmeniz gerekir. **Yeni Yük Testi Sihirbazı** kullanarak yük testinizi oluşturduğunuzda, yük testinize bir başlangıç çalıştırması ayarı eklenir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki tablolarda yük testi çalıştırma ayarları için çeşitli özellikler açıklanır. Bu özellikleri, belirli yük testi gereksinimlerinizi karşılayacak şekilde değiştirebilirsiniz.

Daha fazla bilgi için bkz. [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Genel Özellikler

|Özellik|Tanım|
|-|----------------|
|**Açıklama**|Çalışma ayarlarının açıklaması.|
|**Tür başına en yüksek hata**|Yük testi için kaydedilecek tür başına en yüksek hata sayısı.<br /><br /> Gerekirse bu sayıyı artırabilirsiniz, ancak bunu yapmak yük testi sonucunun boyut ve işlem süresini de artırır.|
|**Raporlanan en yüksek Istek URL 'Leri**|Bu yük testinde sonuçların raporlanmasına yönelik en fazla benzersiz Web performansı test isteği URL sayısı.<br /><br /> Gerekirse bu sayıyı artırabilirsiniz, ancak bunu yapmak yük testi sonucunun boyut ve işlem süresini de artırır.|
|**En fazla eşik ihlalleri**|Bu yük testi için kaydedilecek en yüksek eşik ihlali sayısı.<br /><br /> Gerekirse bu sayıyı artırabilirsiniz, ancak bunu yapmak yük testi sonucunun boyut ve işlem süresini de artırır.|
|**Uygulama etki alanında birim testlerini Çalıştır**|Yük testi birim testleri içerdiğinde, her birim testi derlemesinin ayrı bir uygulama etki alanında çalışıp çalışmadığını belirleyen bir Boolean değer. Varsayılan ayar true 'dur.<br /><br /> Birim testleriniz ayrı bir uygulama etki alanının veya app.config dosyasının düzgün çalışmasını gerektirmiyorsa, birim testleriniz bu özelliğin değeri olarak ayarlanarak daha hızlı çalışabilir `False` .|
|**Ad**|Çalışma ayarının **Yük Testi Düzenleyicisi** **çalışma ayarları** düğümünde göründüğü şekliyle adı.|
|**Doğrulama düzeyi**|Bu, bir yük testinde çalışacak en yüksek doğrulama kuralı düzeyini tanımlar. Doğrulama kuralları Web performans testi istekleriyle ilişkilendirilir. Her doğrulama kuralının ilişkili bir doğrulama düzeyi vardır: **yüksek**, **Orta** veya **düşük**. Bu yük testi çalıştırma ayarı, Web performans testinin yük testinde çalıştırıldığı sırada hangi doğrulama kurallarının çalıştırılacağını belirler. Örneğin, bu çalıştırma ayarı **Orta** olarak ayarlandıysa, tüm doğrulama kuralları **Orta** olarak işaretlenir veya **düşük** olur.|

## <a name="logging-properties"></a>Günlüğe kaydetme özellikleri

|Özellik|Tanım|
|-|----------------|
|**En yüksek test günlüğü**|Yük testi için kaydedilecek en yüksek test günlüğü sayısını belirtir. En fazla test günlüğü sayısı için girilen değere ulaşıldığında, yük testi günlükleri toplamayı durdurur. Bu nedenle, Günlükler testin başlangıcında toplanacaktır, sonunda değil. Yük testi tamamlanana kadar çalışmaya devam edecektir.|
|**Tamamlanan testler için günlük sıklığını Kaydet**|Test günlüğünün yazılacağı sıklığı belirtir. Bu sayı, her girilen test sayısının bir tanesi test günlüğüne kaydedilecek anlamına gelir. Örneğin, on değerini girerken, onuncu, Twentieth, thtieth ve bu gibi bir test günlüğüne yazılacağını belirtir. Değerin 0 olarak ayarlanması, hiçbir test günlüğünün kaydedileceğini belirtir.|
|**Test hatasında Günlüğü Kaydet**|Yük testinde bir test başarısız olursa test günlüklerinin kaydedilip kaydedilmediğini belirleyen bir Boole değeri. Varsayılan değer: `True`.<br /><br /> Daha fazla bilgi için bkz [. nasıl yapılır: test başarısızlıklarının test günlüklerine kaydedilip kaydedilmediğini belirtme](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

Daha fazla bilgi için bkz. [Yük testi günlük ayarlarını değiştirme](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Sonuçlar özellikleri

|Özellik|Tanım|
|-|----------------|
|**Depolama türü**|Bir yük testinde elde edilen performans sayaçlarını depolamanın yolu. Seçenekler şunlardır:<br /><br /> -   **Veritabanı** - **Load Test sonuçları DEPOSUNA** sahip bir SQL veritabanı gerektirir.<br />-   **Yok**.|
|**Zamanlama Ayrıntıları Depolaması**|Bu, **Load Test sonuçları deposunda** depolanacak ayrıntıları belirlemekte kullanılır. Üç değer mevcuttur:<br /><br /> -   **Allindividualdetails** - **yük test sonuçları deposundaki** yük testi sırasında çalıştırılan veya verilen her test, işlem ve sayfa için bireysel zamanlama değerlerini toplayın ve saklayın. **Yük Testi Çözümleyicisi**'Nde **Sanal Kullanıcı etkinliği grafiğini** kullanmayı düşünüyorsanız, bu gereklidir.<br />     Daha fazla bilgi için bkz. [Ayrıntılar görünümündeki sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Hiçbiri** -hiçbir ayrı zamanlama değeri toplanmaz. Bu, Visual Studio 2013 Güncelleştirme 4 ve sonraki sürümler için varsayılan değerdir.<br />-   **StatisticsOnly** - **yük test sonuçları deposundaki** yük testi sırasında yürütülen veya verilen her test, işlem ve sayfa için bireysel zamanlama değerlerini depolamak yerine yalnızca istatistikleri toplayın ve saklayın.<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: zamanlama ayrıntıları depolama özelliğini belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>SQL izleme özellikleri

|Özellik|Tanım|
|-|----------------|
|**Izlenen SQL Işlemlerinin en düşük süresi**|SQL Izleme tarafından yakalanan, milisaniye cinsinden bir SQL işlemi için en az süre. Örneğin bu, yük altında yavaş olan SQL işlemlerini bulmaya çalışıyorsanız hızlı bir şekilde tamamlanan işlemleri yoksaymanıza olanak sağlar.|
|**SQL Izleme bağlantı dizesi**|İzlenecek veritabanına erişmek için kullanılan bağlantı dizesi.|
|**SQL Izleme dizini**|İzleme bittikten sonra SQL Izleme dosyasının konulacağı konum. Bu dizin, denetleyicinin SQL Server ve okuma izinleri için yazma izinlerine sahip olmalıdır.|
|**SQL Izleme etkin**|Bu, SQL işlemlerinin izlenmesini mümkün bir şekilde sunar. `False` varsayılan değerdir.|

## <a name="test-iterations-properties"></a>Test yinelemeleri özellikleri

|Özellik|Tanım|
|-|----------------|
|**Test yinelemeleri**|Yük testi tamamlanmadan önce çalıştırılacak bireysel testlerin toplam sayısını belirtir. Bu özellik yalnızca "test yinelemeleri kullan" özelliği olduğunda geçerlidir `True` .|
|**Test Yinelemeleri Kullan**|Test Yinelemeleri Kullan ise, yük testi `True` içinde tamamlanan bireysel testlerin sayısı "test yinelemeleri" özelliği tarafından belirtilen sayıya ulaşırsa, yük testi çalışır. Bu durumda, ısınma süresi, çalıştırma süresi ve seyrek erişimli süre olan zaman tabanlı ayarlar yoksayılır. "Test yinelemeleri kullan" ise, `False` Tüm zamanlama ayarları uygulanır ve "test yinelemeleri" yok sayılır.|

Daha fazla bilgi için, bkz. [nasıl yapılır: bir çalışma ayarında test yinelemesi sayısını belirtme](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Zamanlama özellikleri

|Özellik|Tanım|
|-|----------------|
|**Cool-azaltma süresi**|Sınama soğuk-azaltma döneminin süresi hh: mm: ss biçiminde ifade edilir. Yük testi tamamlandığında, yük testi içindeki bireysel testler yine de çalışıyor olabilir. Cool azaltma süresi boyunca, bu testler tamamlanana kadar veya seyrek erişimli dönemin sonuna ulaşılana kadar devam edebilir. Varsayılan olarak, bir soğuk nokta yoktur ve yük testi çalışma süresi ayarına göre tamamlandığında, bireysel testler sonlandırılır.|
|**Çalışma süresi**|Testin uzunluğu ss: DD: ss biçimindedir.|
|**Örnek hız**|Performans sayacı değerlerinin, ss: DD: ss biçiminde yakalanacağı Aralık.<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: örnek hızını belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Isınma Süresi**|Testin başlangıcı ve veri örneklerinin ne zaman kaydedilebildiği, ss: DD: ss biçiminde süresi. Bu, genellikle örnek değerleri kaydetmeden önce belirli bir yük düzeyine ulaşmak üzere sanal kullanıcıları yüklemek için kullanılır. Isınma süresi bitmeden önce yakalanan örnek değerler, **Yük Testi Çözümleyicisi**'nde gösterilir.|

## <a name="webtest-connections-properties"></a>WebTest bağlantıları özellikleri

|Özellik|Tanım|
|-|----------------|
|**WebTest bağlantı modeli**|Bu, yük testi aracısından, yük testi içinde çalışan Web performans testleri için Web sunucusuna bağlantıların kullanımını denetler. Üç Web performans testi bağlantı modeli seçeneği mevcuttur:<br /><br /> - **Kullanıcı modeli başına bağlantı** , gerçek bir tarayıcı kullanan bir kullanıcının davranışına benzetir. Internet Explorer 6 veya Internet Explorer 7 benzetildiğinde, Web performans testini çalıştıran her bir sanal kullanıcı Web sunucusuna bir veya iki adanmış bağlantı kullanır. İlk bağlantı, Web performans testinde ilk istek verildiğinde oluşturulur. Bir sayfa birden fazla bağımlı istek içerdiğinde ikinci bir bağlantı kullanılabilir. Bu istekler, iki bağlantı kullanılarak paralel olarak verilir. Bu bağlantılar, Web performans testinde sonraki istekler için yeniden kullanılır. Web performans testi tamamlandığında bağlantılar kapalıdır. Bu modelin bir dezavantajı, aracı bilgisayar üzerinde açık tutulmuş bağlantı sayısının yüksek (Kullanıcı yükünün iki katına kadar) olmasını sağlar. Sonuç olarak, bu yüksek bağlantı sayısını desteklemesi gereken kaynaklar, tek bir yük testi aracısından yürütülen kullanıcı yükünü sınırlayabilir. Internet Explorer 8 benzetildiğinde, altı eşzamanlı bağlantı desteklenir.<br />- **Bağlantı havuzu** modeli, birden çok sanal Web performans testi kullanıcısı arasında Web sunucusuyla bağlantıları paylaşarak yük testi aracısındaki kaynakları korur. Kullanıcı yükü bağlantı havuzu boyutundan daha büyükse, farklı sanal kullanıcılar tarafından çalıştırılan Web performans testleri bir bağlantıyı paylaşır. Bu, başka bir Web performans testinin bağlantıyı kullanırken bir istek yapmadan önce bir Web performans testinin beklemek zorunda olabileceği anlamına gelir. Bir Web performans testinin bir isteği göndermeden önce beklediği ortalama süre, yük testi performans sayacı ortalama bağlantı bekleme süresi tarafından izlenir. Bu sayı, bir sayfa için Ortalama yanıt süresinden daha az olmalıdır. Aksi takdirde, bağlantı havuzu boyutu büyük olasılıkla çok küçüktür.<br />- **Test yineleme modeli başına bağlantı** , her test yinelemesi için adanmış bağlantıların kullanımını belirtir.|
|**WebTest bağlantı havuzu boyutu**|Bu, yük testi Aracısı ve Web sunucusu arasında yapılacak en fazla bağlantı sayısını belirtir. Bu yalnızca **bağlantı havuzu** modeli için geçerlidir.|

## <a name="change-run-setting-properties"></a>Çalışma ayarı özelliklerini değiştir

Yük testini farklı koşullarda çalıştırabilmeniz için, farklı özellik ayarlarıyla yük testinize daha fazla çalışma ayarı ekleyebilirsiniz. Örneğin, yeni bir test ayarı ekleyebilir ve farklı bir örnek hızı kullanabilir ya da daha uzun çalışma süresi belirtebilirsiniz. Tek seferde yalnızca bir çalıştırma ayarı kullanabilirsiniz ve onu etkin olarak işaretleyerek hangi çalıştırma ayarını kullanacağınızı belirtmeniz gerekir. Bir örnek için bkz. [nasıl yapılır: yük testi için etkin çalıştırma ayarını seçme](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

Çalışma ayarlarını değiştirmek için:

1. Bir yük testi açın.

2. **Çalışma ayarları** klasörünü genişletin.

3. **Çalışma ayarları** düğümünü seçin.

4. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

     **Özellikler penceresi** görüntülenir ve seçilen çalışma ayarının özellikleri görüntülenir.

5. Çalıştırma ayarlarını değiştirmek için **Özellikler penceresini** kullanın. Örneğin, testinizi beş dakikada çalıştırmak için çalıştırma süresini **00:05:00** olarak değiştirin.

    > [!NOTE]
    > Çalışma ayarları özelliklerinin ve açıklamalarının tüm listesi için bkz. [Yük testi çalışma ayarı özellikleri](../test/load-test-run-settings-properties.md).

6. Özellikleri değiştirmeyi tamamladığınızda, yük testinizi kaydedin. **Dosya** menüsünde **Kaydet**' i seçin.

> [!NOTE]
> Sayaç kümesi eşlemeleri aynı zamanda çalıştırma ayarları ' nın bir parçasıdır. Daha fazla bilgi için bkz. [bir yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
