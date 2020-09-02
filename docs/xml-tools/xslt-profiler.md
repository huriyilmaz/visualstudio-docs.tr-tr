---
title: XSLT performansı
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79d865a426af2c089bfcc6bd1e733b4ecc185077
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592288"
---
# <a name="the-xslt-profiler"></a>XSLT Profiler

XSLT Profiler, XSLT kodundaki performansla ilgili sorunları ölçmenize, değerlendirmenize ve hedefleyecek ayrıntılı XSLT performans raporları oluşturur. XSLT Profiler, XSL ve XSLT stil sayfası iyileştirmeleri için yararlı ipuçları içerir. En yüksek performansı talep eden XSLT uygulamaları için bu araç gerekli olabilir.

XSLT Profiler, Visual Studio 'nun bir parçasıdır ve **XML** menüsünde kullanılabilir.

![XSLT Profil Oluşturucusu](../xml-tools/media/profile-xslt-menu.png)

> [!NOTE]
> XSLT Profiler yalnızca Visual Studio Enterprise sürümünde kullanılabilir.

## <a name="create-a-performance-report"></a>Performans raporu oluşturma

1. Visual Studio 'da bir XSLT belgesi açın.

2. Menü çubuğunda, **XML**  >  **profili XSLT**' yi seçin.

3. Bir giriş XML belgesi sağlayın. Bir XML belgesi zaten açık değilse sizden dosya istenir.

   Analiz başlar ve ilerleme çubuğu düzenleyicide ilerleme durumunu görüntüler. XSLT çıktısı da görünür.

4. Performans oturumu bittikten sonra XSLT performansını çözümlemek için performans raporunu kontrol edin.

## <a name="get-all-available-views"></a>Tüm kullanılabilir görünümleri Al

1. Tüm kullanılabilir görünümleri almak için **geçerli görünüm** aşağı açılan listesine tıklayın.

2. **Geçerli görünüm** açılır listesinden **Özet görünümü** seçeneğini belirleyin. Varsayılan olarak, **Özet görünümünde**bir performans raporu görüntülenir. Bu görünüm, XSLT belgeleriyle ilgili performans sorunlarını tespit eden bir başlangıç noktasıdır. **Özet görünümü** aşağıdaki veri noktalarını listeler:

   - En çok çağrılan işlevler

   - En bireysel iş olan işlevler

   - En uzun yürütme zamanı alan işlevler

   Varsayılan olarak, her bir veri noktası için üç sütun vardır: işlevin adı, mutlak değer içindeki çağrı sayısı ve toplam işlev çağrılarının adlandırılmış işlevinin yüzde değeri. **Özet görünümündeki**her bir veri noktasından, işlev veri noktalarına sağ tıklayarak daha ayrıntılı görünümlere gidebilirsiniz.

3. **Geçerli görünüm** açılır listesinden **işlev görünümü** seçeneğini belirleyin. **Işlev görünümü** profil oluşturma sırasında çağrılan işlevleri listeler. Bir sütun adına tıklayarak verileri sıralayabilirsiniz. Varsayılan olarak görüntülenen sütunlar şunlardır:

    - **İşlev adı**

    - **Geçen kapsamlı süre**

    - **Geçen dışlamalı süre**

    - **Uygulama kapsamlı süresi**

    - **Dışlamalı uygulama süresi**

    - **Çağrı Sayısı**

   Tüm zaman sütunları mutlak değerlerde ve yüzdede görüntülenir. **Dışlamalı** terim, bu işlevin yürütülmesi sırasında çağrılan diğer işlevler tarafından harcanan sürenin dışlayarak yürütülmesi için harcanan toplam süreyi ifade eder.

   **Dahil** edilen terim, çağrılan işlevlerin yürütme süresi ve diğer işlevleri olarak adlandırılan işlevlerden herhangi biri dahil olmak üzere yürütülen bir işlevin toplam süresini ifade eder.

## <a name="select-callercallee-view"></a>Arayan/çağrılan görünümünü seçin

**Geçerli görünüm** aşağı açılan listesinden **arayan/çağrılan** görünümü ' nü seçin. **Arayan/çağrılan** görünümü aşağıdaki üç farklı kısma sahiptir:

- **Çağrılan işlevler**: belirli bir işlevi çağıran tüm işlevler, görünümün en üst kısmında listelenir.

- **Geçerli işlev**: çağrılan belirli işlev, görünümün orta bölümünde listelenmiştir.

- **Tarafından çağrılan işlevler**: belirli bir işlev tarafından çağrılan tüm işlevler, görünümün alt bölümünde listelenir.

Adında bir işlev, `SyncToNavigator` görünümün orta kısmında görünürse, işlevi çağıran tüm işlevler `SyncToNavigator` görünümün en üst kısmında görünür ve tarafından çağrılan tüm işlevler `SyncToNavigator` görünümün alt bölümünde görünür.

- Görünümün orta bölümündeki işlevini, görünümün diğer iki bölümünde listelenen işlevlerden herhangi birine çift tıklayarak değiştirebilirsiniz. Daha sonra Görünüm, değişiklikleri otomatik olarak yansıtacak şekilde güncelleştirilir.

- Ayrıca, sütun adları ' na tıklayarak verileri sıralayabilirsiniz.

## <a name="select-call-tree-view"></a>Çağrı ağacı görünümünü seçin

- **Geçerli görünüm** açılan listesinde **çağrı ağacı görünümü** ' nü seçin. Bu görünüm program yürütmenin ağaç görünümüdür.

   **Çağrı ağacı görünümü** , işlem adı olarak ağacın kökünü gösterir. İşlevler ağacın düğümleridir. Bu görünüm, belirli çağrı izlemelerinin detayına gitmeyi ve hangi izlemelerin en yüksek performans etkisi olduğunu analiz etmenizi sağlar. Görünüm, hata ayıklama sırasında kullanılabilen **çağrı yığını görünümüne** benzer. **Işlev görünümündeki**sütunlara ek olarak, **çağrı ağacı görünümünde**, **modül adını**görüntülemek için ek bir sütun vardır.

- **Geçerli görünüm** açılır listesinde **işaretler** ' i seçin.

   XSLT Profiler ile, ilişkili bir yoruma sahip veri toplama akışında görüntülenen işaretler vardır. İşaretler, sayaçların bulunduğu koda yer koyar. XSLT profil oluşturucuyu XSLT performans sayaçlarını toplayacak şekilde söylemeniz durumunda, bu işaretlerin her biri çalıştırıldığında sayaçlar toplanır. Veriler, **Işaret kimliği**, **işaret adı** (**Başlangıç programı**, **bitiş programı**) ve **zaman damgasını**içeren bir tabloda görüntülenir. İşaretler toplanmaz ve performans raporunun **Işaretler görünümünde** kronolojik sırada görünür.

## <a name="select-modules-in-the-current-view"></a>Geçerli görünümdeki modülleri seçin

- **Geçerli görünüm** açılan listesinde **modüller** ' i seçin.

   Modüller görünümü, modül düzeyine toplanmış tüm işlevlerin düz bir listesidir. Modül performans verilerinin görünümünü görüntülemek veya kapatmak için modül adını genişletin veya daraltın. Bir sütun adına tıklayarak verileri sıralayabilirsiniz. Varsayılan olarak, **geçen kapsamlı süre**, **geçen dışlamalı**süre, **uygulama kapsamlı**süre, **uygulama dışlamalı zaman**ve **çağrı sayısı**için mutlak değerler ve yüzde numaraları vardır.

- **Geçerli görünüm** açılır listesinden **işlem** ' i seçin.

   İşlem görünümü, işlem **kimliği**, **işlem adı**, **Başlangıç zamanı**ve **bitiş saatini**içeren bir tablo görüntüler. Veriler, sütun adlarına tıklanarak sıralanabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: XSLT hiyerarşisini kullanma](../xml-tools/walkthrough-using-xslt-hierarchy.md)
