---
title: Performans Kuralları Başvuru | Microsoft Docs
description: Uygulamanın performans kurallarının Profil Oluşturma Araçları uyarıları ve uygulama performansı hakkında bilgi sağlamayı öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7dd51299756ead4593afb95a374e23edce25f47f45489af573b2ba3ab924f181
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410404"
---
# <a name="performance-rules-reference"></a>Performans Kuralları Başvurusu
Uygulamanın performans kuralları Profil Oluşturma Araçları ek uyarılar ve uygulama performansı hakkında bilgi sağlar. Performans kuralları, veri kaynağı ve işlemci performans sayaçları gibi kaynaklardan toplanan bir profil oluşturma Windows verileri analiz eder. Kural iletileri, tümleşik geliştirme ortamının Hata [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Çıkışı penceresinde görüntülenir. İletiler aşağıdaki kural düzeylerinden biri ile listelenir:

|Kategori|Açıklama|
|-|-|
|**Hata**|Performans sorunlarının çoğu doğru hata değildir, çünkü birkaç kural Hata iletileri üretir. Hata iletisi, profil oluşturma verilerini toplama hatası olduğunu gösteriyor olabilir.|
|**Uyarı**|Uyarılar, uygulamanın performans sorunlarının kaynağı olabilecek veya iyileştirmelerden yararlanabilecek bir alanı gösterir.|
|**Bilgi**|Bilgi iletileri, bir kural koşulu analizinin Hata iletisi oluşturmak için eşiğe ulaşmadığını veya iletide yer alan bilgilerin yararlı olduğunu ancak bir performans sorununu yansıtmadığını gösterir.|

## <a name="in-this-section"></a>Bu Bölümde

[Id'ye göre Performans Kuralları](../profiling/performance-rules-by-id.md)

Performans Profil Oluşturma Araçları kuralları dört kategoride düzenlenmiştir:

|Kategori|Açıklama|
|-|-|
|[.NET Framework Kullanım Performansı Kuralları](../profiling/dotnet-framework-usage-performance-rules.md)|Veri kaynaklarını verimli bir şekilde .NET Framework kurallar.|
|[Bellek ve Disk Belleği Performans Kuralları](../profiling/memory-and-paging-performance-rules.md)|Uygulamanın yönetilen belleğini ve disk belleği davranışını analiz etme kuralları.|
|[Profil Oluşturma Araçları Kuralları](../profiling/profiling-tools-usage-rules.md)|Veri kaynaklarını verimli bir şekilde Profil Oluşturma Araçları kurallar.|
|[Kaynak İzleme Performans Kuralları](../profiling/resource-monitoring-performance-rules.md)|Profil oluşturma çalıştırması içinde işlemci ve bellek kullanımı hakkında bilgi iletileri.|
