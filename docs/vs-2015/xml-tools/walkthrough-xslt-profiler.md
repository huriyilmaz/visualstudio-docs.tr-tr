---
title: 'İzlenecek yol: XSLT Profiler | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7ee6665aea98edf7cb701f5fdfe07d293887bac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669534"
---
# <a name="walkthrough-xslt-profiler"></a>İzlenecek Yol: XSLT Profil Oluşturucusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XSLT Profiler, XSLT kodundaki performansla ilgili sorunları ölçmenize, değerlendirmenize ve hedefleyecek ayrıntılı XSLT performans raporları oluşturur. XSLT Profiler, XSL ve XSLT stil sayfası iyileştirmeleri için yararlı ipuçları içerir. En yüksek performansı talep eden XSLT uygulamaları için bu araç gerekli olabilir.

## <a name="prerequisites"></a>Önkoşullar
 Aşağıdaki izlenecek yol için Visual Studio 2010 and.NET Framework sürüm 4,0 gerekir. XSLT Profiler yalnızca Profil Oluşturma Araçları yüklü Microsoft Visual Studio Team System ile kullanılabilir.

### <a name="create-the-performance-report"></a>Performans raporu oluşturma

1. Visual Studio 'da bir XSLT belgesi açın.

2. XML menüsünde bulunan **PROFILE XSLT** seçeneğine tıklayın.

3. Bir giriş XML belgesi sağlayın. Bir XML belgesi zaten açık değilse sizden dosya istenir.

4. Analiz başlar ve ilerleme çubuğu düzenleyicide ilerleme durumunu görüntüler.

5. XSLT çıktısı çıkış bölmesinde görünür.

6. Bir performans oturumu bittikten sonra performans raporunu kontrol edin. Bir performans raporuna kaydedilen veriler XSLT performansını görüntülemenizi ve analiz etmenizi sağlar.

### <a name="get-all-the-available-views"></a>Tüm kullanılabilir görünümleri Al

1. Tüm kullanılabilir görünümleri almak için **geçerli görünüm** aşağı açılan listesine tıklayın.

2. **Geçerli görünüm** açılır listesinden **Özet görünümü** seçeneğini belirleyin. Varsayılan olarak, **Özet görünümünde**bir performans raporu görüntülenir. Bu görünüm, XSLT belgeleriyle ilgili performans sorunlarını tespit eden bir başlangıç noktasıdır. **Özet görünümü** aşağıdaki veri noktalarını listeler:

    - En çok çağrılan işlevler

    - En bireysel iş olan işlevler

    - En uzun yürütme zamanı alan işlevler

3. Varsayılan olarak, her bir veri noktası için üç sütun vardır: işlevin adı, mutlak değer içindeki çağrı sayısı ve toplam işlev çağrılarının adlandırılmış işlevinin yüzde değeri. **Özet görünümündeki**her bir veri noktasından, işlev veri noktalarına sağ tıklayarak daha ayrıntılı görünümlere gidebilirsiniz.

4. **Geçerli görünüm** açılır listesinden **işlev görünümü** seçeneğini belirleyin. **Işlev görünümü** profil oluşturma sırasında çağrılan işlevleri listeler. Bir sütun adına tıklayarak verileri sıralayabilirsiniz. Varsayılan olarak görüntülenen sütunlar şunlardır:

    - **İşlev adı**

    - **Geçen kapsamlı süre**

    - **Geçen dışlamalı süre**

    - **Uygulama kapsamlı süresi**

    - **Dışlamalı uygulama süresi**

    - **Çağrı Sayısı**

5. Tüm zaman sütunları mutlak değerlerde ve yüzdede görüntülenir. **Dışlamalı** terim, bu işlevin yürütülmesi sırasında çağrılan diğer işlevler tarafından harcanan sürenin dışlayarak yürütülmesi için harcanan toplam süreyi ifade eder.

6. **Dahil** edilen terim, çağrılan işlevlerin yürütme süresi ve diğer işlevleri olarak adlandırılan işlevlerden herhangi biri dahil olmak üzere yürütülen bir işlevin toplam süresini ifade eder.

### <a name="select-callercallee-view"></a>Arayan/çağrılan görünümünü seçin

1. **Geçerli görünüm** aşağı açılan listesinden **arayan/çağrılan** görünümü ' nü seçin.

2. **Arayan/çağrılan** görünümü aşağıdaki üç farklı kısma sahiptir:

    - **Çağrılan işlevler**: belirli bir işlevi çağıran tüm işlevler, görünümün en üst kısmında listelenir.

    - **Geçerli işlev**: çağrılan belirli işlev, görünümün orta bölümünde listelenmiştir.

    - **Tarafından çağrılan işlevler** : belirli bir işlev tarafından çağrılan tüm işlevler, görünümün alt bölümünde listelenir.

3. Adında bir işlev, `SyncToNavigator` görünümün orta kısmında görünürse, işlevi çağıran tüm işlevler `SyncToNavigator` görünümün en üst kısmında görünür ve tarafından çağrılan tüm işlevler `SyncToNavigator` görünümün alt bölümünde görünür.

4. Görünümün orta bölümündeki işlevini, görünümün diğer iki bölümünde listelenen işlevlerden herhangi birine çift tıklayarak değiştirebilirsiniz. Daha sonra Görünüm, değişiklikleri otomatik olarak yansıtacak şekilde güncelleştirilir.

5. Ayrıca, sütun adları ' na tıklayarak verileri sıralayabilirsiniz.

### <a name="select-calltree-view"></a>CallTree görünümünü seçin

1. **Geçerli görünüm** açılan listesinde **çağrı ağacı görünümü** ' nü seçin. Bu görünüm program yürütmenin ağaç görünümüdür.

2. **Çağrı ağacı görünümü** , işlem adı olarak ağacın kökünü gösterir. İşlevler ağacın düğümleridir. Bu görünüm, belirli çağrı izlemelerinin detayına gitmeyi ve hangi izlemelerin en yüksek performans etkisi olduğunu analiz etmenizi sağlar. Görünüm, hata ayıklama sırasında kullanılabilen **çağrı yığını görünümüne** benzer. **Işlev görünümündeki**sütunlara ek olarak, **çağrı ağacı görünümünde**, **modül adını**görüntülemek için ek bir sütun vardır.

3. **Geçerli görünüm** açılır listesinde **işaretler** ' i seçin.

4. SLT profil Oluşturucu ile, ilişkili bir yorum ile veri toplama akışında görüntülenen işaretler vardır. İşaretler, sayaçların bulunduğu koda yer koyar. XSLT profil oluşturucuyu XSLT performans sayaçlarını toplayacak şekilde söylemeniz durumunda, bu işaretlerin her biri çalıştırıldığında sayaçlar toplanır. Veriler, **Işaret kimliği**, **işaret adı** (**Başlangıç programı**, **bitiş programı**) ve **zaman damgasını**içeren bir tabloda görüntülenir. İşaretler toplanmaz ve performans raporunun **Işaretler görünümünde** kronolojik sırada görünür.

### <a name="select-modules-in-the-current-view"></a>Geçerli görünümdeki modülleri seçin

1. **Geçerli görünüm** açılan listesinde **modüller** ' i seçin.

2. Modüller görünümü, modül düzeyine toplanmış tüm işlevlerin düz bir listesidir. Modül performans verilerinin görünümünü görüntülemek veya kapatmak için modül adını genişletin veya daraltın. Bir sütun adına tıklayarak verileri sıralayabilirsiniz. Varsayılan olarak, **geçen kapsamlı süre**, **geçen dışlamalı**süre, **uygulama kapsamlı**süre, **uygulama dışlamalı zaman**ve **çağrı sayısı**için mutlak değerler ve yüzde numaraları vardır.

3. **Geçerli görünüm** açılır listesinden **işlem** ' i seçin.

4. İşlem görünümü, işlem **kimliği**, **işlem adı**, **Başlangıç zamanı**ve **bitiş saatini**içeren bir tablo görüntüler. Veriler, sütun adlarına tıklanarak sıralanabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [İzlenecek Yol: XSLT Hiyerarşisi Kullanma](../xml-tools/walkthrough-using-xslt-hierarchy.md)
