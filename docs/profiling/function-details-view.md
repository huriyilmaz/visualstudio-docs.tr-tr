---
title: İşlev Ayrıntıları görünümü | Microsoft Docs
description: Performans Gezgini, Işlev Ayrıntıları görünümü penceresi, maliyet dağıtım çubuğu grafiği, Işlev performansı Ayrıntıları tablosu ve Işlev kodu görünümü penceresi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 98771014f903b88ad57ec8713fd2867094c483b2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033804"
---
# <a name="function-details-view"></a>İşlev Ayrıntıları Görünümü
**Işlev Ayrıntıları görünümü** penceresi aşağıdaki bilgileri görüntüler:

- **Maliyet dağıtım** çubuğu grafiği, seçtiğiniz bir işlev ile seçili işlevi yürüten çağırma işlevleri arasındaki ilişkiyi ve seçilen işlev ile onun tarafından çağrılan işlevleri arasındaki ilişkileri temsil eder.

- Belirttiğiniz işlev için Özet profil oluşturma verilerinin gösterildiği **Işlev performansı ayrıntıları** tablosu.

- Kod kullanılabilir olduğunda işlev kodunu gösteren **Işlev kodu görünümü** penceresi.

  **Işlev kod görünümü** penceresi ayrı bir bölmesidir. Varsayılan olarak, iki bölme yatay olarak bölünür ve **Işlev kod görünümü** penceresi çerçevenin alt kısmına yerleştirilir.

- İki bölmeyi dikey olarak ayırmak için araç çubuğunda **ekranı dikey olarak Böl** ' e tıklayın.

- Bölmelerin göreli boyutunu değiştirmek için kareler arasında gölgeli kenarlığa tıklayın ve kenarlığı farklı bir konuma sürükleyin.

## <a name="cost-distribution-bar-chart"></a>Maliyet dağıtım çubuğu grafiği

### <a name="performance-metrics"></a>Performans Ölçümleri
 **Performans ölçümü** açılan listesinde, görünümde hangi değerlerin görüneceğini belirtebilirsiniz. Kullanılabilir değerler, profil oluşturma veri dosyasında kullanılan profil oluşturma yöntemine bağlıdır. Parantez içindeki adlar, **Işlev performansı ayrıntıları** tablosundaki satırların adlarıdır.

### <a name="bar-chart"></a>Çubuk Grafiği
 **İşlevleri Çağırma**

 **Çağırma işlevleri** çubuğu, seçilen işlevi çağıran işlevleri gösterir. Çağıran işlevi içeren bloğun boyutu, çağıran işlevin seçili işlev için performans ölçümünün toplam değerine kadar olan katkısıyla orantılı olur.

 Bir arama işlevinin adına tıklayarak, görünümün seçili işlevi olmasını sağlayabilirsiniz.

- Listelemek için çok fazla çağırma işlevi varsa, en küçük katkılara sahip işlevler **diğer** bir blokta toplanır. **Çağıran/çağrılan görünümü** penceresinde seçili işlevin tüm çağırma ve çağrılan işlevlerini görüntülemek için **diğer** ' e tıklayın. Daha fazla bilgi için bkz. [arayan/çağrılan görünümü](../profiling/caller-callee-view.md).

- Çağırma işlevleri yoksa veya işlev bir iş parçacığının veya işlemin giriş işlevleridir, **yığın bloğunun en üstü** görüntülenir.

  **Seçili Işlev**

  Seçilen işlev çubuğu, seçilen işlevin toplam performans ölçüsüne, seçili işlevdeki işlev ve kod olarak adlandırılan katkılarını gösterir. Çağrılan bir işlevi veya işlev gövdesini içeren bloğun boyutu, seçilen işlevin performans ölçümünün toplam değerine olan katkısına göre orandır.

  Görünümdeki seçili işlevi yapmak için çağrılan bir işlevin adına tıklayabilirsiniz.

- **Toplam** değer, seçilen işlevin performans ölçümdür.

- **Işlev gövdesi** bloğu, işlevin gövdesinde doğrudan kod yürütmesinde gerçekleşen performans ölçümünün toplam değerinin miktarını temsil eder.

- Seçili işlev tarafından çağrılan işlevler bloklar bölümünde listelenmiştir. Seçili işlevlerin boyutu bloğu, çağrılan işlevde gerçekleşen seçili işlevin toplam performans ölçümünün miktarını temsil eder.

- Listelemek için çok fazla çağırma işlevi varsa, en küçük katkılara sahip işlevler **diğer** bir blokta toplanır. **Çağıran/çağrılan görünümü** penceresinde seçili işlevin tüm çağırma ve çağrılan işlevlerini görüntülemek için **diğer** ' e tıklayın. Daha fazla bilgi için bkz. [arayan/çağrılan görünümü](../profiling/caller-callee-view.md).

- Çağrılan işlev yoksa, **yığın bloğunun alt kısmı** görüntülenir.

## <a name="function-performance-details"></a>İşlev performansı ayrıntıları
 Işlev performansı Ayrıntıları tablosu, seçili işlevin performans ölçümleri için özet veriler sağlar. Hem değer hem de yüzde görüntülenir. Grafik ve **performans ölçümü** listesindeki ayrıntılar tablosunda görüntülenen profil oluşturma verilerini belirtin.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel**|-İşlev gövdesinin yürütülmesi sırasında gerçekleşen performans ölçümünün miktarı.|
|**Çağrılarında**|-Seçili işlevin çağrıldığı işlevlerde gerçekleşen performans ölçümü miktarı.|
|**Kapsamlı toplam**|- **Dışlamalı** ve **içindeki çağrı** değerlerinin toplamı.|

## <a name="function-code-view"></a>İşlev kod görünümü
 **Işlev kod görünümü** penceresi, kullanılabilir olduğunda kaynak kodun bir listesini görüntüler. Diğer işlevleri çağıran kaynak kodu satırlarının yanında, gölgeli bir sütun çağrılan işlev için performans ölçümü değerlerini içerir. Kaynak kodu düzenlemek için kaynak kodu dosyasının bağlantısına tıklayın.

## <a name="cost-distribution-bar-chart-values"></a>Maliyet dağıtım Çubuğu grafik değerleri

### <a name="sampling"></a>Örnekleme
 Aşağıdaki tabloda, örnekleme yöntemi kullanılarak toplanan profil oluşturma verileri için performans ölçümü listesindeki değerler açıklanmaktadır.

|Değer|Açıklama|
|-|-|
|**Kapsamlı örnekler (toplanan örnekler)**|-Çağıran bir işlev için, seçilen işlev bu çağıran işlev tarafından çağrıldığında toplanan örnek sayısı.<br />-Işlev gövdesi için, seçilen işlev kendi kodunu yürütürken toplanan örnek sayısı.<br />-Çağrılan bir işlev için, seçilen işlevden gelen bir çağrı nedeniyle çağrılan işlev yürütülerek toplanan örneklerin sayısı.|

### <a name="instrumentation"></a>İzleme
 Aşağıdaki tabloda, izleme yöntemi kullanılarak toplanan profil oluşturma verileri için performans ölçümü listesindeki değerler açıklanmaktadır.

|Değer|Açıklama|
|-|-|
|**Geçen kapsamlı süre (geçen süre)**|Geçen süre, işletim sistemine yapılan çağrılarında bağlam anahtarları ve giriş/çıkış işlemleri gibi harcanan süreyi içerir.<br /><br /> - **Çağırma işlevi** için, işlev tarafından çağrılan seçili işlevin örneklerinin yürütülmesi için harcanan geçen süre miktarı. Seçilen işlev tarafından çağrılan işlevlerde harcanan süre dahildir.<br />- **Işlev gövdesi** için, seçilen işlevin kodunu yürütmek için harcanan geçen sürenin toplam miktarı. Çağrılan işlevlerde harcanan süre dahil değildir.<br />-Çağrılan bir işlev için, seçilen işlev tarafından çağrılan işlevin örneklerini yürütmek için harcanan süre. Toplam, işlevin çağrıldığı işlevlerde harcanan süreyi içerir. Seçilen işlev tarafından çağrılan işlevlerde harcanan süre dahildir.|
|**Uygulama kapsamlı süresi (uygulama saati)**|Uygulama saati, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan çağrılarda harcanan zamanı içermez.<br /><br /> - **Çağırma işlevi** için, işlev tarafından çağrılan seçili işlevin örneklerini yürütmek için harcanan uygulama zamanı miktarı. Seçilen işlev tarafından çağrılan işlevlerde harcanan süre dahildir.<br />- **Işlev gövdesi** için, seçilen işlevin kodunu yürütmek için harcanan toplam uygulama zamanı miktarı. Çağrılan işlevlerde harcanan süre dahil değildir.<br />-Çağrılan bir işlev için, seçilen işlev tarafından çağrılan işlevin örneklerini yürütmek için harcanan tutar. Toplam, işlevin çağrıldığı işlevlerde harcanan süreyi içerir.|

### <a name="net-memory"></a>.NET belleği
 Aşağıdaki tabloda, .NET bellek profili oluşturma yöntemi kullanılarak toplanan profil oluşturma verileri için performans ölçümü listesindeki değerler açıklanmaktadır.

|Değer|Açıklama|
|-|-|
|**Kapsamlı ayırmalar (ayırmalar)**|-Çağıran bir **işlev** için, işlevin çağrıldığı seçili işlevin örnekleri tarafından ayrılan nesne sayısı. Bu sayı, seçilen işlevin çağırdığı işlevler tarafından ayrılan nesneleri içerir.<br />- **Işlev gövdesi** için, kendi kodunu yürütürken seçili işlev tarafından ayrılan nesne sayısı. Seçili işlev tarafından çağrılan işlevlerde ayrılan nesneler dahil değildir.<br />-Çağrılan bir işlev için, seçilen işlev tarafından çağrılan işlevin örnekleri tarafından ayrılan nesne sayısı. Bu sayı, işlevin çağırdığı işlevler tarafından ayrılan nesneleri içerir.|
|**Kapsamlı baytlar (bayt)**|-Çağıran bir **işlev** için, işlevin çağırdığı seçili işlevin örnekleri tarafından ayrılan bayt sayısı. Bu sayı, seçilen işlevin çağırdığı işlevler tarafından ayrılan baytları içerir.<br />- **Işlev gövdesi** için, seçili işlev tarafından ayrılan ve kendi kodunu yürütürken ayrılan toplam bayt sayısı. Seçilen işlev tarafından çağrılan işlevlerde ayrılan baytlar dahil değildir.<br />-Çağrılan bir işlev için, seçilen işlev tarafından çağrılan işlevin örnekleri tarafından ayrılan bayt sayısı. Sayı, işlevin çağıran işlevleri tarafından ayrılan baytları içerir.|

### <a name="concurrency"></a>Eşzamanlılık
 Aşağıdaki tabloda eşzamanlılık yöntemi kullanılarak toplanan verilerin profilini oluşturma için Performans Ölçümü listesinde yer alan değerler açıklanıyor.

|Değer|Açıklama|
|-|-|
|**Kapsayıcı İçerikler (İçerikler)**|- Bir **Çağırma İşlevi** için, işlevin çağır olduğu seçili işlevin örneklerde meydana gelen kaynak mukkimlik olaylarının sayısı. Sayı, seçilen işlevin çağıran işlevlerde yer alan etkinliklerini içerir.<br />- İşlev **Gövdesi için,** işlev kendi kodunu yürütürken meydana gelen toplam olay sayısı. Seçilen işlev tarafından çağrılan işlevlerde oluşan içerikler dahil değildir.<br />- Çağrılır bir işlev için, seçilen işlev tarafından çağrılan işlevin örneklerde meydana gelen olay sayısıdır. Sayısı, işlevinin çağıran işlevlerinde meydana gelen olaylarını içerir.|
|**Kapsayıcı Engellenen Saat (Engellenen Saat)**|- Çağıran bir işlev için, işlevin çağıran seçili işlevin örnekleri için kaynak musiki olaylarında harcanan süre. Bu süre, seçilen işlevin çağırmış olduğu işlevlerde engellenen zamanı içerir.<br />- İşlev **Gövdesi için,** işlev kendi kodunu yürütürken meydana gelen olaylarda harcanan toplam süre. Seçilen işlevin çağır olduğu işlevlerde oluşan içerikler dahil değildir.<br />- Çağrılır bir işlev için, seçilen işlevin çağır olduğu işlev örnekleri için kaynak musiki olaylarında harcanan süre. Süre, işlevin çağırmış olduğu işlevlerde meydana gelen engellenen zamanı içerir.|
