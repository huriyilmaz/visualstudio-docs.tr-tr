---
title: Aynı anda birden çok profil Oluşturucu aracını kullanma | Microsoft Docs
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: f72757d46496c3990c0a0d4205753d185078eac7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85332037"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Aynı anda birden çok profil oluşturucu aracını kullanma

Performans profili Oluşturucu, performans sorunlarının anlaşılmasına yardımcı olmak için aynı oturumda birden çok araçların kullanılabileceği fikrle tasarlanmıştır. Performans Profiler 'daki çoğu araç, [CPU kullanımı](../profiling/cpu-usage.md), [.net Async aracı](../profiling/analyze-async.md)ve [veritabanı](../profiling/analyze-database.md) aracı gibi eşzamanlı olarak çalışmayı destekler. Aynı tanılama oturumunda araçları aynı anda çalıştırmak için, yanındaki onay kutusuna tıklayın ve ardından tanılama oturumunu başlatın.

![DIAG hub tüm araçları seçili](../profiling/media/diaghuballtoolsselected.png "DIAG hub tüm araçları seçili")

>[!NOTE]
>[.NET nesne ayırma](../profiling/dotnet-alloc-tool.md) aracı gibi bazı araçlar, yüksek yüklerine veya diğer teknik sınırlamalara bağlı olarak diğer araçlarla çalıştırılamaz.

## <a name="time-filtering"></a>Zaman filtreleme 

Çözümleme sırasında, zaman filtreleme işlemleri araçlar arasında uygulanır, böylece bir zaman aralığını daraltmak ve başka bir araçtaki verileri filtrelemek için bir araçtaki bilgileri kullanabilirsiniz. Bu özellik, bir izlemede belirli noktalara kılavuzluk eder ve uygulamanın durumunu anlamanıza yardımcı olur.

![Diag merkezi zaman filtreleme](../profiling/media/diaghubtimefiltering.png "Diag merkezi zaman filtreleme")

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturucu ayarlarını iyileştirme](../profiling/optimize-profiler-settings.md)
- [Hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Performans bilgilerini toplama metotlarını anlama](../profiling/understanding-performance-collection-methods-perf-profiler.md)
