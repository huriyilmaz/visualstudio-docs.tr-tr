---
title: XSLT performansı
description: XSLT kodunuzun performansını iyileştirmenize Visual Studio ayrıntılı XSLT performans raporları oluşturan XSLT Profiler hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/11/2020
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 4e4c15f9185a967f2c200a00ad2312343600c73e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147498"
---
# <a name="the-xslt-profiler"></a>XSLT Profil Oluşturma

XSLT Profiler, XSLT kodundaki performansla ilgili sorunları ölçmeye, değerlendirmeye ve hedeflemeye yardımcı olan ayrıntılı XSLT performans raporları oluşturur. XSLT Profiler, XSL ve XSLT stil sayfası iyileştirmeleri için yararlı ipuçları içerir. En yüksek performansa talepte olan XSLT uygulamaları için bu araç temel olabilir.

XSLT Profiler, Visual Studio xml menüsünde **kullanılabilir.**

![XSLT Profiler](../xml-tools/media/profile-xslt-menu.png "Visual Studio 2017'de XML menü öğelerinin ekran görüntüsü")

> [!NOTE]
> XSLT Profiler yalnızca Enterprise 2017'nin Visual Studio kullanılabilir.

## <a name="create-a-performance-report"></a>Performans raporu oluşturma

1. Visual Studio 2017'de bir XSLT belgesi açın.

2. Menü çubuğunda **XML** Profili  >  **XSLT'yi seçin.**

3. Giriş XML belgesi sağlama. Bir XML belgesi henüz açık değilse, dosya istenir.

   Analiz başlatılır ve ilerleme çubuğu düzenleyicide ilerlemeyi görüntüler. XSLT çıkışı da görünür durumdadır.

4. Performans oturumu sona erdikten sonra XSLT performansını analiz etmek için performans raporunu kontrol edin.

## <a name="get-all-available-views"></a>Kullanılabilir tüm görünümleri al

1. Kullanılabilir tüm **görünümleri almak** için Geçerli Görünüm açılan listesine tıklayın.

2. Geçerli **Görünüm açılan** listesinde **Özet Görünümü** seçeneğini belirleyin. Varsayılan olarak, Özet Görünümünde bir performans **raporu görüntülenir.** Bu görünüm, XSLT belgeleriyle ilgili performans sorunlarını belirlemek için başlangıç noktasıdır. Özet **Görünümü aşağıdaki** veri noktalarını listeler:

   - En çok çağrı yapılan işlevler

   - En bireysel çalışmaya sahip işlevler

   - Yürütmesi en uzun süren işlevler

   Varsayılan olarak, her veri noktası için üç sütun vardır: işlevin adı, mutlak değerde çağrı sayısı ve adlandırılmış işlevin toplam işlev çağrılarının yüzdesi. Özet Görünümündeki her veri **noktasından,** işlev veri noktalarına sağ tıklayarak daha ayrıntılı görünümlere ulaşabilirsiniz.

3. Geçerli **Görünüm açılan** listesinde **İşlev Görünümü** seçeneğini belirleyin. İşlev **Görünümü,** profil oluşturma sırasında çağrılır işlevleri listeler. Bir sütun adına tıklayarak verileri sıraabilirsiniz. Varsayılan olarak görüntülenen sütunlar:

    - **İşlev Adı**

    - **Geçen Kapsayıcı Süre**

    - **Geçen Özel Süre**

    - **Uygulama Dahil Saati**

    - **Uygulamaya Özel Zaman**

    - **Çağrı Sayısı**

   Tüm zaman sütunları hem mutlak değerlerde hem de yüzdelerde görüntülenir. Dışlama **terimi,** bir işlevin bu işlevin yürütülmesi sırasında çağrılduğu diğer işlevler tarafından harcanan zaman dışında harcanan toplam zamanı ifade eder.

   Kapsayıcı **terimi,** çağrılduğu tüm işlevlerin yürütme süresi ve bu işlevlerden herhangi biri diğer işlevler olarak adlandırılan işlevlerden herhangi biri olup olmadığı da dahil olmak üzere bir işlevin yürütülmesi için harcanan toplam zamanı ifade eder.

## <a name="select-callercallee-view"></a>Çağıran/Çağrılı görünümünü seçin

Geçerli **Görünüm açılan listesinde Çağıran/Çağrılı** görünümünü seçin.  **Çağıran/Çağrılı görünümü** aşağıdaki üç ayrı parçaya sahiptir:

- **adlı işlevler:** Belirli bir işlevi çağıran tüm işlevler görünümün üst kısmında listelenir.

- **Geçerli İşlev:** Çağrılan belirli işlev görünümün orta kısmında listelenir.

- **tarafından çağrılan işlevler:** Belirli bir işlev tarafından çağrılan tüm işlevler görünümün alt kısmında listelenir.

adlı bir işlev görünümün orta kısmında görünürse, işlevi çağıran tüm işlevler görünümün üst kısmında ve tarafından çağrılan tüm işlevler görünümün alt `SyncToNavigator` `SyncToNavigator` kısmında `SyncToNavigator` görünür.

- Görünümün diğer iki bölümünde listelenen işlevlerden herhangi birini çift tıklayarak görünümün orta kısmında işlevi değiştirebilirsiniz. Daha sonra görünüm, değişiklikleri otomatik olarak yansıtacak şekilde güncelleştirilir.

- Ayrıca sütun adlara tıklayarak verileri sıraabilirsiniz.

## <a name="select-call-tree-view"></a>Çağrı Ağacı Görünümü'ne tıklayın

- Geçerli **Görünüm açılan listesinde** Çağrı Ağacı **Görünümü'ne** tıklayın. Bu görünüm, program yürütmenin ağaç görünümü.

   Çağrı **Ağacı Görünümü,** işlem adı olarak ağacın kökünü gösterir. İşlevler ağacın düğümleridir. Bu görünüm, belirli çağrı izlemeleri üzerinde detaya gitme ve en büyük performans etkisine sahip izlemeleri analiz etmenize olanak sağlar. Görünüm, hata ayıklama sırasında **kullanılabilen Çağrı Yığını Görünümüne** benzer. İşlev Görünümündeki sütunlara **ek olarak,** Çağrı Ağacı **Görünümünde** Modül Adını görüntülemek için ek bir **sütun vardır.**

- Geçerli **Görünüm** açılan **listesinde İşaretler'i** seçin.

   XSLT Profiler ile, veri toplama akışında ilişkili bir açıklamayla birlikte ortaya çıktı işaretleri vardır. İşaretler, kodda sayaçları olan yerlerdir. XSLT Profiler'a XSLT performans sayaçlarını toplamasını söylerken, bu işaretlerden biri her yürütülürken sayaçlar toplanır. Veriler, Mark ID **,** Mark **Name** (**Start Program**, **End Program**) ve Time Stamp (Zaman Damgası) içeren bir **tabloda görüntülenir.** İşaretler toplanmaz ve performans raporunun İşaretler Görünümünde **kronolojik** sırada görünür.

## <a name="select-modules-in-the-current-view"></a>Geçerli Görünümde Modülleri Seçme

- Geçerli **Görünüm** açılan **listesinde Modüller'i** seçin.

   Modüller görünümü, modül düzeyinde toplanan tüm işlevlerin düz bir listesidir. Modül performans verilerini görüntülemek veya kapatmak için modül adını genişletin veya daraltabilirsiniz. Bir sütun adına tıklayarak verileri sıraabilirsiniz. Varsayılan olarak, Geçen Kapsayıcı Saat **,** Geçen Özel **Saat,** Uygulama Dahil **Saati,** Uygulama Özel Saati ve Çağrı Sayısı için hem mutlak değerler hem de yüzde **sayıları vardır.**

- Geçerli **Görünüm** açılan **listesinde İşlem'i** seçin.

   İşlem görünümünde İşlem Kimliği, **İşlem Adı,** Başlangıç **Zamanı** ve **Bitiş Saati'nin yer** alan bir tablo **görüntülenir.** Veriler sütun adları tıklarak sıralanmış olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: XSLT hiyerarşisini kullanma](../xml-tools/walkthrough-using-xslt-hierarchy.md)
