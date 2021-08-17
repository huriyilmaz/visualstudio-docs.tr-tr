---
title: yük testi çalıştırma Ayarlar
description: Her yük testi için birden fazla çalışma ayarı oluşturmayı ve depolamayı öğrenin ve ardından testi çalıştırdığınızda kullanılacak belirli bir ayarı seçin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: f0b7dd6f8e228e0ff16d10976c64ecfacc85a73a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032933"
---
# <a name="load-test-run-settings-properties"></a>Yük testi çalıştırma ayarları özellikleri

Yük testinin çalışma ayarları, testin süresi, sonuç koleksiyonu ayrıntı düzeyi ve test çalışırken toplanan sayaç kümeleri dahil olmak üzere çeşitli diğer ayarları belirler. Her bir yük testi için birden fazla çalışma ayarı oluşturup depolayabilmeniz ve sonra testi çalıştırdığınızda kullanılacak belirli bir ayarı seçmeniz gerekir. **Yeni Yük Testi Sihirbazı** kullanarak yük testinizi oluşturduğunuzda, yük testinize bir başlangıç çalıştırması ayarı eklenir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki tablolarda yük testi çalıştırma ayarları için çeşitli özellikler açıklanır. Bu özellikleri, belirli yük testi gereksinimlerinizi karşılayacak şekilde değiştirebilirsiniz.

Daha fazla bilgi için bkz. [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Genel Özellikler

|Özellik|Tanım|
|-|----------------|
|**Açıklama**|çalıştırma Ayarlar açıklaması.|
|**Tür başına en yüksek hata**|Yük testi için kaydedilecek tür başına en yüksek hata sayısı.<br /><br /> Gerekirse bu sayıyı artırabilirsiniz, ancak bunu yapmak yük testi sonucunun boyut ve işlem süresini de artırır.|
|**Raporlanan en yüksek Istek URL 'Leri**|Bu yük testinde sonuçların raporlanmasına yönelik en fazla benzersiz Web performansı test isteği URL sayısı.<br /><br /> Gerekirse bu sayıyı artırabilirsiniz, ancak bunu yapmak yük testi sonucunun boyut ve işlem süresini de artırır.|
|**En fazla eşik ihlalleri**|Bu yük testi için kaydedilecek en yüksek eşik ihlali sayısı.<br /><br /> Gerekirse bu sayıyı artırabilirsiniz, ancak bunu yapmak yük testi sonucunun boyut ve işlem süresini de artırır.|
|**Uygulama etki alanında birim testlerini Çalıştır**|Yük testi birim testleri içerdiğinde, her birim testi derlemesinin ayrı bir uygulama etki alanında çalışıp çalışmadığını belirleyen bir Boolean değer. Varsayılan ayar true 'dur.<br /><br /> Birim testleriniz ayrı bir uygulama etki alanının veya app.config dosyasının düzgün çalışmasını gerektirmiyorsa, birim testleriniz bu özelliğin değeri olarak ayarlanarak daha hızlı çalışabilir `False` .|
|**Ad**|çalışma ayarının, **Yük Testi Düzenleyicisi** **Ayarlar çalıştır** düğümünde göründüğü şekilde adı.|
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
|**Depolama Türüyle**|Bir yük testinde elde edilen performans sayaçlarını depolamanın yolu. Seçenekler şunlardır:<br /><br /> -   **veritabanı** - **yük Test Sonuçları deposu** olan bir SQL veritabanı gerektirir.<br />-   **Yok**.|
|**zamanlama ayrıntıları Depolama**|Bu, **Load Test sonuçları deposunda** depolanacak ayrıntıları belirlemekte kullanılır. Üç değer mevcuttur:<br /><br /> -   **Allindividualdetails** - **yük test sonuçları deposundaki** yük testi sırasında çalıştırılan veya verilen her test, işlem ve sayfa için bireysel zamanlama değerlerini toplayın ve saklayın. **Yük Testi Çözümleyicisi**'Nde **Sanal Kullanıcı etkinliği grafiğini** kullanmayı düşünüyorsanız, bu gereklidir.<br />     Daha fazla bilgi için bkz. [Ayrıntılar görünümündeki sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Hiçbiri** -hiçbir ayrı zamanlama değeri toplanmaz. bu, Visual Studio 2013 Güncelleştirme 4 ve sonraki sürümler için varsayılan değerdir.<br />-   **StatisticsOnly** - **yük test sonuçları deposundaki** yük testi sırasında yürütülen veya verilen her test, işlem ve sayfa için bireysel zamanlama değerlerini depolamak yerine yalnızca istatistikleri toplayın ve saklayın.<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: zamanlama ayrıntıları depolama özelliğini belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>SQL izleme özellikleri

|Özellik|Tanım|
|-|----------------|
|**izlenen SQL işlemlerinin Minimum süresi**|SQL izleme tarafından yakalanan SQL işleminin en kısa süresi (milisaniye). örneğin, bu, yük altında yavaş olan SQL işlemleri bulmaya çalışıyorsanız hızlı bir şekilde tamamlanan işlemleri yoksaymanıza olanak sağlar.|
|**SQL Bağlan dize izleniyor**|İzlenecek veritabanına erişmek için kullanılan bağlantı dizesi.|
|**SQL İzleme dizini**|izleme sona erdikten sonra SQL izleme dosyasının yer aldığı konum. bu dizin, denetleyicinin SQL Server ve okuma izinleri için yazma izinlerine sahip olmalıdır.|
|**SQL İzleme etkin**|bu, SQL işlemlerinin izlenmesini mümkün bir şekilde sunar. `False` varsayılan değerdir.|

## <a name="test-iterations-properties"></a>Test yinelemeleri özellikleri

|Özellik|Tanım|
|-|----------------|
|**Test yinelemeleri**|Yük testi tamamlanmadan önce çalıştırılacak bireysel testlerin toplam sayısını belirtir. Bu özellik yalnızca "test yinelemeleri kullan" özelliği olduğunda geçerlidir `True` .|
|**Test Yinelemeleri Kullan**|Test Yinelemeleri Kullan ise, yük testi `True` içinde tamamlanan bireysel testlerin sayısı "test yinelemeleri" özelliği tarafından belirtilen sayıya ulaşırsa, yük testi çalışır. Bu durumda, ısınma süresi, çalıştırma süresi ve seyrek erişimli süre olan zaman tabanlı ayarlar yoksayılır. "Test yinelemeleri kullan" ise, `False` Tüm zamanlama ayarları uygulanır ve "test yinelemeleri" yok sayılır.|

Daha fazla bilgi için, bkz. [nasıl yapılır: bir çalışma ayarında test yinelemesi sayısını belirtme](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Zamanlama özellikleri

|Özellik|Tanım|
|-|----------------|
|**Cool-azaltma süresi**|Testin hh:mm:ss biçiminde ifade edildiklerinin süresi. Yük testi tamam olduğunda bir yük testi içindeki tek tek testler hala çalışıyor olabilir. Geri çalışma süresi boyunca, bu testler tamamlayana veya geri soğutma süresi sona erinceye kadar devam eder. Varsayılan olarak, bir geri yükleme süresi yoktur ve yük testi Çalışma Süresi ayarına göre sona erer.|
|**Çalıştırma Süresi**|Testin uzunluğu: ss:mm:ss biçiminde.|
|**Örnek Hızı**|Ss:mm:ss biçiminde performans sayacı değerlerinin yakalanma aralığı.<br /><br /> Daha fazla bilgi için, [bkz. How to: Specify the sample rate](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Isınma Süresi**|Testin başlangıcı ile veri örneklerinin kaydediliyor olması arasındaki süre (ss:mm:ss biçiminde). Bu genellikle örnek değerleri kaydetmeden önce belirli bir yük düzeyine ulaşmak için sanal kullanıcıları yüklemek için kullanılır. Isınma süresi sona ermeden önce yakalanan örnek değerler Yük Testi **Çözümleyicisi'ne gösterilir.**|

## <a name="webtest-connections-properties"></a>WebTest bağlantıları özellikleri

|Özellik|Tanım|
|-|----------------|
|**WebTest Bağlantı Modeli**|Bu, bir yük testi içinde çalıştıran web performans testleri için yük testi aracılarından web sunucusuna bağlantıların kullanımını kontrol eder. Üç web performansı testi bağlantı modeli seçeneği vardır:<br /><br /> - **Kullanıcı Başına Bağlantı** modeli, gerçek bir tarayıcı kullanan kullanıcının davranışının benzetimini sağlar. 6 Internet Explorer 7 Internet Explorer sanal makineniz benzetimli olduğunda, web performans testi çalıştıran her sanal kullanıcı web sunucusuna bir veya iki ayrılmış bağlantı kullanır. İlk bağlantı, web performans testinde ilk istek yayım olduğunda kurulur. Sayfa birden fazla bağımlı istek içerdiğinde ikinci bir bağlantı kullanılabilir. Bu istekler iki bağlantı kullanılarak paralel olarak verilmektedir. Bu bağlantılar, web performans testinde sonraki istekler için yeniden kullanılır. Web performans testi tamam olduğunda bağlantılar kapatılır. Bu modelin bir dezavantajı, aracı bilgisayarda açık durumdaki bağlantı sayısının yüksek olmasıdır (kullanıcı yükünün iki katı kadar). Sonuç olarak, bu yüksek bağlantı sayısını desteklemek için gereken kaynaklar, tek bir yük testi aracısına yönlendirilen kullanıcı yükünü sınırlayıcı olabilir. Sanal Internet Explorer 8 sanal olduğunda, altı eş zamanlı bağlantı de destekler.<br />- **Bağlantı Havuzu modeli,** web sunucusuna bağlantıları birden çok sanal web performansı testi kullanıcısı arasında paylaşarak yük testi aracısı üzerindeki kaynakları korumayı sağlar. Kullanıcı yükü bağlantı havuzu boyutundan büyükse, farklı sanal kullanıcılar tarafından çalıştır alınan web performansı testleri bir bağlantıyı paylaşır. Bu, bağlantıyı kullanan başka bir web performans testi olduğunda bir web performans testinin istekte başlamadan önce beklemesi gerektirebilir. Bir web performans testinin istek göndermeden önce bekleyeceği ortalama süre, yük testi performans sayacı Ortalama Bağlantı Bekleme Süresi tarafından iz olur. Bu sayı, bir sayfanın ortalama yanıt süresinden küçük olması gerekir. Bağlantı havuzu boyutu büyük olasılıkla çok küçüktür.<br />- Test **Başına Bağlantı Yinelemesi** modeli, her test yinelemesi için ayrılmış bağlantıların kullanımını belirtir.|
|**WebTest Bağlantı Havuzu Boyutu**|Bu, yük testi aracısı ile Web sunucusu arasında en fazla bağlantı sayısını belirtir. Bu yalnızca Bağlantı Havuzu **modeli için** geçerlidir.|

## <a name="change-run-setting-properties"></a>Çalıştırma ayarı özelliklerini değiştirme

Yük testini farklı koşullarda çalıştırabilirsiniz, böylece yük testini farklı özellik ayarlarıyla yük teste daha fazla çalıştırma ayarı abilirsiniz. Örneğin, yeni bir test ayarı ekleyebilir ve farklı bir örnek hızı kullanabilir veya daha uzun bir çalışma süresi belirtebilirsiniz. Aynı anda yalnızca bir çalıştırma ayarı kullanabilirsiniz ve etkin olarak işaretleyerek hangi çalıştırma ayarının kullan gerektiğini belirtmeniz gerekir. Bir örnek için, [bkz. Nasıl 2012: Yük testi için etkin çalıştırma ayarını seçme.](../test/how-to-select-the-active-run-setting-for-a-load-test.md)

Çalıştırma ayarlarını değiştirmek için:

1. Yük testi açın.

2. Run **Ayarlar** genişletin.

3. Bir Run **Ayarlar** seçin.

4. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

     Özellikler **Penceresi** görüntülenir ve seçilen çalıştırma ayarının özellikleri görüntülenir.

5. Çalıştırma **ayarlarını değiştirmek için** Özellikler Penceresini kullanın. Örneğin, testini beş dakika boyunca çalıştırmak için çalışma süresini **00:05:00** olarak değiştirebilirsiniz.

    > [!NOTE]
    > Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi için [bkz. Test çalıştırması ayarı özelliklerini yükleme.](../test/load-test-run-settings-properties.md)

6. Özellikleri değiştirmeyi bitirdikten sonra yük testini kaydedin. Dosya menüsünde **Kaydet'i** **seçin.**

> [!NOTE]
> Sayaç kümesi eşlemeleri de çalıştırma ayarlarının bir parçası. Daha fazla bilgi için [bkz. Yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
