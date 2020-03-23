---
title: Fonksiyon Ayrıntıları Görüntüle | Microsoft Dokümanlar
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6e5bd33d9924784220addafca85a63f550df02c7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779265"
---
# <a name="function-details-view"></a>İşlev Ayrıntıları Görünümü
**İşlev Ayrıntıları Görünümü** penceresi aşağıdaki bilgileri görüntüler:

- **Maliyet Dağılımı** çubuğu grafiği, seçtiğiniz bir işlev ile seçili işlevi çalıştıran çağrı işlevleri ile seçili işlev ve onun tarafından çağrılan işlevler arasındaki ilişkileri temsil eder.

- Belirttiğiniz işlevin özet profil oluşturma verilerini gösteren **İşlev Performans Ayrıntıları** tablosu.

- Kod kullanılabilir olduğunda işlev kodunu gösteren **İşlev Kodu Görünümü** penceresi.

  **İşlev Kodu Görünümü** penceresi ayrı bir bölmedir. Varsayılan olarak, iki bölme yatay olarak bölünür ve **İşlev Kodu Görünümü** penceresi çerçevenin alt kısmında konumlandırılır.

- İki bölmeyi dikey olarak bölmek için, araç çubuğunda **Ekranı Dikey Olarak Böl'e** tıklayın.

- Bölmelerin göreli boyutunu değiştirmek için, çerçeveler arasındaki gölgeli kenarlığı tıklatın ve kenarlığı farklı bir konuma sürükleyin.

## <a name="cost-distribution-bar-chart"></a>Maliyet Dağıtım Çubuğu Grafiği

### <a name="performance-metrics"></a>Performans Ölçümleri
 Performans **metrik** açılır listesinde, görünümde hangi değerlerin görünacağını belirtebilirsiniz. Kullanılabilir değerler, profil oluşturma veri dosyasında kullanılan profil oluşturma yöntemine bağlıdır. Parantez içinde adları **İşlev Performans Ayrıntıları** tablosunda satır adlarıdır.

### <a name="bar-chart"></a>Çubuk Grafiği
 **İşlevleri Çağırma**

 **Arama İşlevleri** çubuğu, seçili işlevi çağıran işlevleri gösterir. Çağrı işlevini içeren bloğun boyutu, çağrı işlevinin seçili işlev için performans ölçütünün toplam değerine katkısıyla orantılıdır.

 Görünümdeki seçili işlevi yapmak için bir arama işlevinin adını tıklatabilirsiniz.

- Listelemek için çok fazla çağrı işlevi varsa, en küçük katkıları olan işlevler **Başka** bir blokta toplanır. **Arayan/Callee Görünümü** penceresinde seçili işlevin tüm arama ve çağrı işlevlerini görüntülemek için **Diğer'i** tıklatın. Daha fazla bilgi için [Bkz. Arayan/Callee Görünümü.](../profiling/caller-callee-view.md)

- Arama işlevi yoksa veya işlev bir iş parçacığının veya işlemin giriş işleviyse, **Yığın Üst** bloğu görüntülenir.

  **Seçili Fonksiyon**

  Seçili işlev çubuğu, çağrılan işlevlerin ve seçilen işlevdeki kodun, seçili işlevin toplam performans ölçüsüne olan katkılarını gösterir. Çağrılan işlev veya işlev gövdesini içeren bloğun boyutu, seçili işlev için performans ölçüsünün toplam değerine olan katkısıyla orantılıdır.

  Görünümde seçili işlevi yapmak için çağrılan işlevin adını tıklatabilirsiniz.

- **Toplam** değer, seçili işlevin performans ölçüsüdür.

- **İşlev Gövdesi** bloğu, işlevin gövdesinde kodun doğrudan yürütülmesinde oluşan performans ölçüsünün toplam değerinin miktarını temsil eder.

- Seçili işlev tarafından çağrılan işlevler bloklar halinde listelenir. Seçili işlevbloğu boyutu, çağrılan işlevde oluşan seçili işlev için toplam performans ölçüsü miktarını temsil eder.

- Listelemek için çok fazla çağrı işlevi varsa, en küçük katkıları olan işlevler **Başka** bir blokta toplanır. **Arayan/Callee Görünümü** penceresinde seçili işlevin tüm arama ve çağrı işlevlerini görüntülemek için **Diğer'i** tıklatın. Daha fazla bilgi için [Bkz. Arayan/Callee Görünümü.](../profiling/caller-callee-view.md)

- Çağrı işlevi yoksa, **Yığın Bloğunun Alt** kısmı görüntülenir.

## <a name="function-performance-details"></a>Fonksiyon Performans Ayrıntıları
 İşlev Performans Ayrıntıları tablosu, seçili işlevin performans ölçümleri için özet veri sağlar. Hem değer hem de yüzde görüntülenir. Grafikte görünen profil oluşturma verilerini ve **Performans metrik** listesindeki ayrıntılar tablosunu belirtirsiniz.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel**|- İşlev gövdesinin yürütülmesinde oluşan performans ölçümü miktarı.|
|**Aramalarda**|- Seçili işlevin çağırdığı işlevlerde oluşan performans ölçümü miktarı.|
|**Toplam Dahil**|- **Özel** ve **Aramalar'daki** değerlerin toplamı.|

## <a name="function-code-view"></a>İşlev Kodu Görünümü
 **İşlev Kodu Görünümü** penceresi kullanılabilir olduğunda kaynak kodun listesini görüntüler. Diğer işlevleri çağıran kaynak kod satırlarının yanında, gölgeli sütun çağrılan işlevin performans ölçüt değerlerini içerir. Kaynak kodu ni yeniden sağlamak için kaynak kodu dosyasının bağlantısını tıklatın.

## <a name="cost-distribution-bar-chart-values"></a>Maliyet Dağıtım Çubuğu Grafik Değerleri

### <a name="sampling"></a>Örnekleme
 Aşağıdaki tablo, örnekleme yöntemi kullanılarak toplanan verilerin profilini çıkarmak için Performans Ölçümü listesindeki değerleri açıklar.

|||
|-|-|
|**Dahil Örnekler (Toplanan Numuneler)**|- Bir arama işlevi için, seçili işlev bu arama işlevi tarafından çağrıldığında toplanan örnek sayısı.<br />- İşlev Gövdesi için, seçili işlev kendi kodunu yürütürken toplanan örnek sayısı.<br />- Çağrılan işlev için, seçili işlevden gelen bir çağrı nedeniyle çağrılan işlev yürütüldüğünde toplanan örnek sayısı.|

### <a name="instrumentation"></a>İzleme
 Aşağıdaki tablo, enstrümantasyon yöntemi kullanılarak toplanan verilerin profilini çıkarmak için Performans Ölçümü listesindeki değerleri açıklar.

|||
|-|-|
|**Geçen Kapsayıcı Süre (Geçen Süre)**|Geçen süre, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içerir.<br /><br /> - Bir **Arama İşlevi**için, işlev tarafından çağrılan seçili işlevin örneklerini yürütmek için harcanan geçen süre miktarı. Seçili işlev tarafından çağrılan işlevlerde harcanan zaman dahildir.<br />- **İşlev Gövdesi**için, seçili işlevin kodunu yürütmek için harcanan geçen sürenin toplam miktarı. Çağrılan işlevlerde harcanan süre dahil edilmez.<br />- Çağrılan işlev için, seçili işlev tarafından çağrılan işlevin örneklerini yürütmek için harcanan tutar. Toplam, işlevin çağırdığı işlevlerde harcanan zamanı içerir. Seçili işlev tarafından çağrılan işlevlerde harcanan zaman dahildir.|
|**Uygulama Dahil Süresi (Uygulama Süresi)**|Uygulama süresi, bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemine yapılan aramalarda harcanan zamanı içermez.<br /><br /> - Bir **Arama İşlevi**için, işlev tarafından çağrılan seçili işlevin örneklerini yürütmek için harcanan uygulama süresi miktarı. Seçili işlev tarafından çağrılan işlevlerde harcanan zaman dahildir.<br />- **İşlev Gövdesi**için, seçilen işlevin kodunu yürütmek için harcanan toplam uygulama süresi miktarı. Çağrılan işlevlerde harcanan süre dahil edilmez.<br />- Çağrılan işlev için, seçili işlev tarafından çağrılan işlevin örneklerini yürütmek için harcanan tutar uygulama süresi. Toplam, işlevin çağırdığı işlevlerde harcanan zamanı içerir.|

### <a name="net-memory"></a>.NET Bellek
 Aşağıdaki tabloda,.NET bellek profil oluşturma yöntemi kullanılarak toplanan verilerin profilini çıkarmak için Performans Ölçümü listesindeki değerler açıklanmaktadır.

|||
|-|-|
|**Kapsayıcı Tahsisatlar (Tahsisler)**|- Bir **Çağrı İşlevi**için, seçili işlevin örnekleri tarafından ayrılan nesne sayısı denir. Sayı, seçili işlevin çağırdığı işlevler tarafından ayrılan nesneleri içerir.<br />- **İşlev Gövdesi**için, kendi kodunu yürütürken seçilen işlev tarafından ayrılan nesnelerin sayısı. Seçili işlev tarafından çağrılan işlevlerde ayrılan nesneler dahil edilmez.<br />- Çağrılan işlev için, seçili işlev tarafından çağrılan işlev örnekleri tarafından ayrılan nesne sayısı. Sayı, işlevin çağırdığı işlevler tarafından ayrılan nesneleri içerir.|
|**Dahil Baytlar (Bayt)**|- Bir **Çağrı İşlevi**için, seçili işlevin örnekleri tarafından ayrılan bayt sayısı denir. Sayı, seçili işlevin çağırdığı işlevler tarafından ayrılan baytları içerir.<br />- **İşlev Gövdesi**için, kendi kodunu yürütürken seçili işlev tarafından ayrılan baytların toplam sayısı. Seçili işlev tarafından çağrılan işlevlere ayrılan baytlar dahil edilmez.<br />- Çağrılan işlev için, seçili işlev tarafından çağrılan işlev örnekleri tarafından ayrılan bayt sayısı. Sayı, işlevin çağırdığı işlevler tarafından ayrılan baytları içerir.|

### <a name="concurrency"></a>Eşzamanlılık
 Aşağıdaki tablo, eşzamanlılık yöntemi kullanılarak toplanan verilerin profilini çıkarmak için Performans Ölçümü listesindeki değerleri açıklar.

|||
|-|-|
|**Kapsayıcı Çekişmeler (Çekişmeler)**|- Bir **Arama İşlevi**için, seçili işlev örneklerinde meydana gelen kaynak çekişme olaylarının sayısı, işlevin çağırdığı. Sayı, seçili işlevin çağırdığı işlevlerde çekişme olaylarını içerir.<br />- **İşlev Gövdesi**için, işlev kendi kodunu yürütürken oluşan çekişme olaylarının toplam sayısı. Seçili işlev tarafından çağrılan işlevlerde oluşan çekişmeler dahil edilmez.<br />- Çağrılan işlev için, seçili işlev tarafından çağrılan işlev örneklerinde oluşan çekişme olaylarının sayısı. Sayı, çağrılan işlevlerde oluşan çekişme olaylarını içerir.|
|**Kapsayıcı Engellenen Süre (Engellenen Süre)**|- Bir arama işlevi için, seçili işlevin çağrıldığı örnekler için kaynak çekişme olaylarında harcanan süre. Zaman, seçili işlevin çağrıldığı işlevlerde engellenen zamanı içerir.<br />- **İşlev Gövdesi**için, işlev kendi kodunu yürüterken oluşan çekişme olaylarında harcanan toplam süre. Seçili işlev in çağrıldığı işlevlerde oluşan çekişmeler dahil edilmez.<br />- Çağrılan işlev için, seçili işlevin çağırdığı işlev örnekleri için kaynak çekişme olaylarında harcanan süre. Zaman, işlevin çağırdığı işlevlerde oluşan engellenmiş zamanı içerir.|
