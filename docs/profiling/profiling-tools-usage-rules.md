---
title: Kullanım kuralları Profil Oluşturma Araçları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1aeeb7e0a9061d72a07b718acde70b00dfcbba89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88144681"
---
# <a name="profiling-tools-usage-rules"></a>Profil Araçları Kullanım Kuralları
Profil Oluşturma Araçları Kullanım kategorisindeki performans kuralları, verileri en etkili şekilde toplamak için profil oluşturucunun kullanılmasına yönelik rehberlik sağlar.

| Kural | Description |
| - | - |
| [DA0002: VSPerfCorProf.dll eksik](../profiling/da0002-vsperfcorprof-dll-is-missing.md) | Komut satırı profili oluşturma, .NET Framework ikililer için tamamlanmamış veriler içerebilir. Bu durum doğru ortam değişkenlerini ayarlamamasından kaynaklanıyor olabilir. |
| [DA0003: Pek çok çekirdek örneği](../profiling/da0003-many-kernel-samples.md) | Hedef ikilinin yürütülmesi dışında oluşan birçok profil oluşturma örneği kaydedildi. Daha doğru veri toplamak için, izleme yöntemini kullanmayı düşünün. |
| [DA0004: Yüksek işlemci kullanımı](../profiling/da0004-high-processor-usage.md) | Profil oluşturma verileri, işlemclerinizin profil oluşturma çalışması sırasında sürekli olarak meşgul olmasını önerir. Daha doğru veri toplamak için örnekleme yöntemini kullanmayı düşünün. |
| [DA0008: Az sayıda örnek toplandı](../profiling/da0008-few-samples-collected.md) | Profil oluşturma çalıştırmasında toplanan örneklerin sayısı, istatistiksel olarak önemli ölçüde yeterince yüksek değildi. Profil oluşturmayı yeniden deneyin ve uygulamayı daha uzun bir süre boyunca çalıştırın. Ayrıca veri toplamak için izleme yöntemini kullanmayı da düşünebilirsiniz. |
| [DA0026: Aşırı çekirdek CPU süresi işlemesi](../profiling/da0026-excessive-kernel-cpu-time-processing.md) | Profil oluşturma çalıştırmasında, işlemci çekirdeği modunda önemli bir süre oluştu. Ölçüm olarak zaman kullanmak yerine, sistem çağrılarını ölçüm olarak kullanarak örneklemeyi düşünün. |
| [DA0029: Desteklenmeyen CLR Sürümü](../profiling/da0029-unsupported-clr-version.md) | Profili oluşturulmuş ikili dosya, profil oluşturucu tarafından desteklenmeyen bir .NET Framework sürümünü kullanıyor. Profil Oluşturucu raporları sembol adlarını çözümleyemiyor. |
| [DA0030: Veritabanı projeleri için Katman Etkileşimi ölçüleri toplayın](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md) | Ad alanındaki yöntemlere yapılan önemli sayıda çağrı <xref:System.Data?displayProperty=fullName> toplandı. Veritabanı çağrıları hakkında veri eklemek için, profil çalışmalarınızın katman etkileşimi verilerini toplamayı göz önünde bulundurun. |
