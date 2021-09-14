---
title: Performans Veri Dosyalarını Karşılaştırma | Microsoft Docs
description: İki Profil Oluşturma Araçları (.vsp veya .vsps) karşılaştırmak için bir dosya kullanın. Karşılaştırma farkları, performans regresyonlarını ve geliştirmeleri gösterir.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628377"
---
# <a name="compare-performance-data-files"></a>Performans veri dosyalarını karşılaştırma

Profil Oluşturma Araçları dosyaları karşılaştırma işlevi, iki rapor dosyası () seçmenize olanak sağlar.*vsp* veya . *vsps*) dosyaları ve bir profil oluşturma oturumundan diğerine yapılan farkları, performans regresyonlarını ve geliştirmeleri gösteren bir rapor oluşturma.

Profil Oluşturma Araçları veri dosyalarının karşılaştırma raporu, bir profil oluşturma veri dosyasındaki bir analizin sonuçlarını başka bir veri dosyasındaki temel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] analizin sonuçlarıyla karşılaştırılmasıdır. Her iki veri dosyası da aynı profil oluşturma yöntemi kullanılarak oluşturulmuş olması gerekir. Analiz karşılaştırmalarının raporu olarak kaydedilir. *vsps* dosyası.

Karşılaştırma raporu görünümü, değiştirilen verilerin tablo görünümünü sunar. Tablo deltayı gösterir veya temelden değiştirir. Delta, eski değer, temel değer ve yeni analizden elde edilen sonuç değeri arasındaki fark belirlenerek hesaplanır.

Profil oluşturma verileri karşılaştırmaları kod, uygulama modülleri, satırlar, yönerge işaretçileri (PS) ve türler gibi işlevlere dayalı olabilir.

Karşılaştırma için kullanılabilen verilerin profilini oluşturma, sütunlarda görüntülenen bilgileri içerir. Bu sütun adlarının tanımları için [bkz. Performans raporu görünümleri.](../profiling/performance-report-views.md)

Gürültüyü azaltmak ve belirtilen miktarda değişmemiş satırların karşılaştırma tablosu görünümündeki verileri filtrelemek için bir eşik belirlenilebilir.

## <a name="in-this-section"></a>Bu bölümde

[Nasıl yapılır: Performans veri dosyalarını karşılaştırma](../profiling/how-to-compare-performance-data-files.md)
