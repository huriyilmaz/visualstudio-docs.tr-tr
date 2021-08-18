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
ms.openlocfilehash: e22e4831d92bc17d1a0c6ac4463a94f85ead2f00
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141642"
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
|[Profil Oluşturma Araçları Kullanım Kuralları](../profiling/profiling-tools-usage-rules.md)|Veri kaynaklarını verimli bir şekilde Profil Oluşturma Araçları kurallar.|
|[Kaynak İzleme Performans Kuralları](../profiling/resource-monitoring-performance-rules.md)|Profil oluşturma çalıştırması içinde işlemci ve bellek kullanımı hakkında bilgi iletileri.|
