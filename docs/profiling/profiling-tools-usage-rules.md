---
title: Profil Oluşturma Araçları Kullanım Kuralları | Microsoft Docs
description: Profil Oluşturma Araçları Usage kategorisindeki Performans kurallarının, verileri en verimli şekilde toplamak için profilleyiciyi kullanmaya yönelik nasıl rehberlik sağlaycı olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 858a49a02e335f169bda60182d5388971cc6f29b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054554"
---
# <a name="profiling-tools-usage-rules"></a>Profil Araçları Kullanım Kuralları
Profil Oluşturma Araçları Kullanım kategorisindeki performans kuralları, verileri en verimli şekilde toplamak için profil oluşturmanın kullanımına yönelik rehberlik sağlar.

| Kural | Açıklama |
| - | - |
| [DA0002: VSPerfCorProf.dll eksik](../profiling/da0002-vsperfcorprof-dll-is-missing.md) | Komut satırı profili oluşturma, ikili dosyalar için .NET Framework içerebilir. Bunun nedeni doğru ortam değişkenlerini ayarlamama olabilir. |
| [DA0003: Pek çok çekirdek örneği](../profiling/da0003-many-kernel-samples.md) | Hedef ikili dosyanın yürütülmesi dışında meydana gelen birçok profil oluşturma örneği kaydedildi. Daha doğru veriler toplamak için ölçümleme yöntemini kullanmayı göz önünde bulundurabilirsiniz. |
| [DA0004: Yüksek işlemci kullanımı](../profiling/da0004-high-processor-usage.md) | Profil oluşturma verileri, profil oluşturma çalıştırması sırasında işlemcilerin sürekli meşgul olduğunu gösteriyor. Daha doğru veriler toplamak için örnekleme yöntemini kullanmayı göz önünde bulundurabilirsiniz. |
| [DA0008: Az sayıda örnek toplandı](../profiling/da0008-few-samples-collected.md) | Profil oluşturma çalıştırması içinde toplanan örnek sayısı istatistiksel olarak anlamlı olacak kadar yüksek değildi. Yeniden profil oluşturmayı ve uygulamayı daha uzun süre çalıştırmayı göz önünde bulundurabilirsiniz. Veri toplamak için ölçüm ölçüm yöntemini de kullanabilirsiniz. |
| [DA0026: Aşırı çekirdek CPU süresi işlemesi](../profiling/da0026-excessive-kernel-cpu-time-processing.md) | Profil oluşturma çalıştırması sırasında işlemci çekirdeği modunda önemli bir süre oluştu. Ölçüm olarak zaman kullanmak yerine ölçüm olarak sistem çağrılarını kullanarak örneklemeyi göz önünde bulundurabilirsiniz. |
| [DA0029: Desteklenmeyen CLR Sürümü](../profiling/da0029-unsupported-clr-version.md) | Profili yapılan ikili dosya, profil .NET Framework bir sürüm kullanıyor. Profil oluşturma raporları sembol adlarını çözümleyemzdire. |
| [DA0030: Veritabanı projeleri için Katman Etkileşimi ölçüleri toplayın](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md) | Ad alanı içinde yöntemlere yapılan önemli sayıda <xref:System.Data?displayProperty=fullName> çağrı toplanmış. Veritabanı çağrıları hakkında veri eklemek için profil çalıştırmalarınıza katman etkileşim verileri toplamayı göz önünde bulundurabilirsiniz. |
