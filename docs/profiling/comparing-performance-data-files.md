---
title: Performans veri dosyalarını karşılaştırma | Microsoft Docs
description: İki rapor dosyasını (. vsp veya. vsps) karşılaştırmak için Profil Oluşturma Araçları kullanın. Karşılaştırma farkları, performans gerilemeleri ve geliştirmeleri gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9d057c691e6f850edecd253ce460795591083b2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039689"
---
# <a name="compare-performance-data-files"></a>Performans veri dosyalarını karşılaştırma

Profil Oluşturma Araçları veri dosyaları karşılaştırma işlevselliği, iki rapor dosyası seçmenizi sağlar (.*VSP* veya. *vsps*) dosyalar ve bir profil oluşturma oturumundan diğerine gerçekleşen farkları, performans gerilemeleri ve geliştirmeleri gösteren bir rapor oluşturur.

Profil Oluşturma Araçları veri dosyalarının karşılaştırma raporu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , bir profil oluşturma veri dosyasındaki analizin sonuçlarını başka bir veri dosyasındaki temel çözümlemenin sonuçlarına karşılaştırır. Her iki veri dosyası aynı profil oluşturma yöntemi kullanılarak oluşturulmuş olmalıdır. Çözümlenen karşılaştırmalar raporu bir olarak kaydedilir. *vsps* dosyası.

Karşılaştırma raporu görünümü değiştirilen verilerin tablo görünümünü sunar. Tablo, Delta veya taban çizgisinden göre değişiklik gösterir. Delta değeri, eski değer, taban çizgisi değeri ve yeni analizin sonucu değeri arasındaki fark saptanarak hesaplanır.

Profiler verilerinin karşılaştırmaları, koddaki işlevlere, uygulamadaki modüllerde, satırlarda, yönerge işaretçilerine (IP) ve türlere göre yapılabilir.

Karşılaştırma için kullanılabilen profil oluşturma verileri sütunlarda görüntülenen bilgileri içerir. Bu sütun adlarının tanımları için bkz. [Performans raporu görünümleri](../profiling/performance-report-views.md).

Bir eşik, paraziti azaltmak ve belirli bir miktarda değişmemiş satırların karşılaştırma tablosu görünümündeki verilerin filtreleneceği şekilde ayarlanabilir.

## <a name="in-this-section"></a>Bu bölümde

[Nasıl yapılır: Performans veri dosyalarını karşılaştırma](../profiling/how-to-compare-performance-data-files.md)
