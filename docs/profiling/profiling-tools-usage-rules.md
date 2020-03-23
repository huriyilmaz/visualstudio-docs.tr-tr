---
title: Profil Oluşturma Araçları Kullanım Kuralları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 51c4f1384a58b19ad9a6a4f46ad0131158cc967c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778355"
---
# <a name="profiling-tools-usage-rules"></a>Profil Araçları Kullanım Kuralları
Profil Oluşturma Araçları Kullanımı kategorisindeki performans kuralları, verileri en etkili şekilde toplamak için profil oluşturucuyu kullanmak için kılavuz sağlar.

| | |
| - | - |
| [DA0002: VSPerfCorProf.dll eksik](../profiling/da0002-vsperfcorprof-dll-is-missing.md) | Komut satırı profil oluşturma .NET Framework ikilileri için eksik veri içerebilir. Bunun nedeni doğru ortam değişkenlerinin ayarlanmaması olabilir. |
| [DA0003: Pek çok çekirdek örneği](../profiling/da0003-many-kernel-samples.md) | Hedef ikiliyürütme dışında meydana gelen birçok profil örnekleri kaydedildi. Daha doğru veri toplamak için enstrümantasyon yöntemini kullanmayı düşünün. |
| [DA0004: Yüksek işlemci kullanımı](../profiling/da0004-high-processor-usage.md) | Profil oluşturma verileri, işlemcilerinizin profil oluşturma sırasında sürekli olarak meşgul olduğunu gösterir. Daha doğru veri toplamak için örnekleme yöntemini kullanmayı düşünün. |
| [DA0008: Toplanan örnek az](../profiling/da0008-few-samples-collected.md) | Profil oluşturma çalışmasında toplanan örnek sayısı istatistiksel olarak anlamlı olacak kadar yüksek değildi. Yeniden profil oluşturmayı ve uygulamayı daha uzun süre çalıştırmayı düşünün. Ayrıca veri toplamak için enstrümantasyon yöntemini kullanmayı da düşünebilirsiniz. |
| [DA0026: Aşırı çekirdek CPU süresi işleme](../profiling/da0026-excessive-kernel-cpu-time-processing.md) | Profil oluşturma çalışmasında önemli miktarda zaman işlemci çekirdeği modunda oluştu. Zamanı metrik olarak kullanmak yerine sistem çağrılarını metrik olarak kullanarak örneklemeyi göz önünde bulundurun. |
| [DA0029: Desteklenmeyen CLR Sürümü](../profiling/da0029-unsupported-clr-version.md) | Profilli ikili, .NET Framework'ün profil oluşturucu tarafından desteklenmeyen bir sürümünü kullanıyor. Profil oluşturucu raporları sembol adlarını çözemez. |
| [DA0030: Veritabanı projeleri için Katman Etkileşim ölçümlerini topla](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md) | <xref:System.Data?displayProperty=fullName> Ad alanındaki yöntemlere yapılan önemli sayıda çağrı toplandı. Veritabanı çağrılarıyla ilgili verileri eklemek için, profil çalışırnızda katman etkileşim verileri toplamayı düşünün. |
