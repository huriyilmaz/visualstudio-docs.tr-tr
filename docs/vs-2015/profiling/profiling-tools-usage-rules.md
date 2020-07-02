---
title: Kullanım kuralları Profil Oluşturma Araçları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4158a6a393ed6e64dedddfca10c1ae04a95e3d3a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535557"
---
# <a name="profiling-tools-usage-rules"></a>Profil Araçları Kullanım Kuralları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil Oluşturma Araçları Kullanım kategorisindeki performans kuralları, verileri en etkili şekilde toplamak için profil oluşturucunun kullanılmasına yönelik rehberlik sağlar.  
  
|Kural|Açıklama|  
|-|-|  
|[DA0002: VSPerfCorProf.dll eksik](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|Komut satırı profili oluşturma, ikili dosyalar için tamamlanmamış veriler içerebilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Bu durum doğru ortam değişkenlerini ayarlamamasından kaynaklanıyor olabilir.|  
|[DA0003: Pek çok çekirdek örneği](../profiling/da0003-many-kernel-samples.md)|Hedef ikilinin yürütülmesi dışında oluşan birçok profil oluşturma örneği kaydedildi. Daha doğru veri toplamak için, izleme yöntemini kullanmayı düşünün.|  
|[DA0004: Yüksek işlemci kullanımı](../profiling/da0004-high-processor-usage.md)|Profil oluşturma verileri, işlemclerinizin profil oluşturma çalışması sırasında sürekli olarak meşgul olmasını önerir. Daha doğru veri toplamak için örnekleme yöntemini kullanmayı düşünün.|  
|[DA0008: Az sayıda örnek toplandı](../profiling/da0008-few-samples-collected.md)|Profil oluşturma çalıştırmasında toplanan örneklerin sayısı, istatistiksel olarak önemli ölçüde yeterince yüksek değildi. Profil oluşturmayı yeniden deneyin ve uygulamayı daha uzun bir süre boyunca çalıştırın. Ayrıca veri toplamak için izleme yöntemini kullanmayı da düşünebilirsiniz.|  
|[DA0026: Aşırı çekirdek CPU süresi işlemesi](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|Profil oluşturma çalıştırmasında, işlemci çekirdeği modunda önemli bir süre oluştu. Ölçüm olarak zaman kullanmak yerine, sistem çağrılarını ölçüm olarak kullanarak örneklemeyi düşünün.|  
|[DA0029: Desteklenmeyen CLR Sürümü](../profiling/da0029-unsupported-clr-version.md)|Profili oluşturulmuş ikili dosyası, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Profil Oluşturucu tarafından desteklenmeyen bir sürümünü kullanıyor. Profil Oluşturucu raporları sembol adlarını çözümleyemiyor.|  
|[DA0030: Veritabanı projeleri için Katman Etkileşimi ölçüleri toplayın](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Ad alanındaki yöntemlere yapılan önemli sayıda çağrı <xref:System.Data?displayProperty=fullName> toplandı. Veritabanı çağrıları hakkında veri eklemek için, profil çalışmalarınızın katman etkileşimi verilerini toplamayı göz önünde bulundurun.|
