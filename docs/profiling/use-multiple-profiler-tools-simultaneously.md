---
title: Birden çok profil oluşturma aracı aynı anda | Microsoft Docs
description: Performans sorunlarının Performans Profili Oluşturucu yardımcı olması için aynı oturumda birden çok araç kullanıla bir fikirle nasıl tasarlanmış olduğunu öğrenin.
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 5a4c4658282f15b6b34562e51be94d9f2be195a8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725672"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Aynı anda birden çok profil oluşturucu aracını kullanma

Bu Performans Profili Oluşturucu, performans sorunlarının anlaşılmasına yardımcı olmak için aynı oturumda birden çok araç kullanılası fikriyle tasarlanmıştır. Hizmet hizmet hizmet Performans Profili Oluşturucu [CPU](../profiling/cpu-usage.md)Kullanımı, .NET Async Aracı ve Veritabanı [aracı gibi eşzamanlı](../profiling/analyze-async.md)olarak [çalıştırmayı](../profiling/analyze-database.md) destekler. Araçları aynı tanılama oturumunda aynı anda çalıştırmak için, bu araçların yanındaki onay kutusuna tıklayın ve ardından tanılama oturumunu çalıştırın.

![Diag Hub Tüm Araçlar Seçildi](../profiling/media/diaghuballtoolsselected.png "Diag Hub Tüm Araçlar Seçildi")

>[!NOTE]
>[.NET](../profiling/dotnet-alloc-tool.md) Nesne Ayırma aracı gibi bazı araçlar, yüksek ek yüklerinden veya diğer teknik sınırlamalar nedeniyle başka araçlarla çalıştıramaz.

## <a name="time-filtering"></a>Zaman filtreleme 

Analiz sırasında, zaman filtreleme işlemleri araçlar arasında uygulanır, bu nedenle bir zaman aralığını daraltmak ve başka bir araçta verileri filtrelemek için bilgileri bir araçta kullanabilirsiniz. Bu özellik, bir izlemede belirli noktalara analiz için yol ve uygulamanın durumunu anlamanıza yardımcı olur.

![Tanılama Hub'ı Zaman Filtreleme](../profiling/media/diaghubtimefiltering.png "Tanılama Hub'ı Zaman Filtreleme")

## <a name="see-also"></a>Ayrıca bkz.

- [Profil oluşturma ayarlarını iyileştirme](../profiling/optimize-profiler-settings.md)
- [Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Performans bilgilerini toplama metotlarını anlama](../profiling/understanding-performance-collection-methods-perf-profiler.md)
