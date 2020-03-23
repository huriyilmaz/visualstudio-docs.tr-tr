---
title: Performans Veri Dosyalarını Karşılaştırma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 64842c5b4f622a1f76aa528360f79403ec92cb42
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777863"
---
# <a name="compare-performance-data-files"></a>Performans veri dosyalarını karşılaştırma

Profil Oluşturma Araçları veri dosyaları karşılaştırma işlevi iki rapor dosyası seçmenize olanak tanır (.* vsp* /veya . *vsps*) bir profil oluşturma oturumundan diğerine gerçekleşen farklılıkları, performans gerilemelerini ve iyileştirmeleri gösteren bir rapor oluşturun.

Profil Oluşturma Araçları'ndaki [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veri dosyalarının karşılaştırma raporu, bir profil oluşturma veri dosyasındaki bir analizin sonuçlarını başka bir veri dosyasındaki temel çözümleme nin sonuçlarıyla karşılaştırır. Her iki veri dosyası da aynı profil oluşturma yöntemi kullanılarak oluşturulmuş olmalıdır. Çözümlenen karşılaştırmaların raporu bir . *vsps* dosyası.

Karşılaştırma raporu görünümü, değiştirilen verilerin tablo görünümünü sunar. Tablo delta yı veya taban çizgisinden değişiklik sunar. Delta, eski değer, temel değer ve yeni çözümlemeden elde edilen sonuç değeri arasındaki fark belirlenerek hesaplanır.

Profil oluşturucu verilerinin karşılaştırılması, koddaki işlevlere, uygulamadaki modüllere, çizgilere, talimat işaretçilerine (IP) ve türlerine dayalı olabilir.

Karşılaştırma için kullanılabilir profil oluşturma verileri sütunlarda görüntülenen bilgileri içerir. Bu sütun adlarının tanımları için [Bkz. Performans raporu görünümleri.](../profiling/performance-report-views.md)

Gürültüyü azaltmak ve belirli bir miktar değişmemiş satırların karşılaştırma tablosu görünümündeki verileri filtrelemek için bir eşik ayarlanabilir.

## <a name="in-this-section"></a>Bu bölümde

[Nasıl yapılır: Performans veri dosyalarını karşılaştırma](../profiling/how-to-compare-performance-data-files.md)
