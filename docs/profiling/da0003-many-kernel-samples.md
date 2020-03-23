---
title: 'DA0003: Birçok çekirdek örnekleri | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 69cd81943641e4e0585a67127c70d35a601a5396
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777744"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Pek çok çekirdek örneği

|||
|-|-|
|Kural Id|DA0003|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemleri|Örnekleme|
|İleti|Çekirdek Modu'nda yüksek oranda örnek var. Bu, yüksek miktarda G/Ç etkinliği veya yüksek oranda bağlam geçişi gösterebilir. Instrumentation Mode'u kullanarak uygulamanızın profilini yeniden çıkarmayı düşünün.|
|Kural türü|Bilgi|

## <a name="cause"></a>Nedeni
 Uygulama için toplanan çağrı yığını örneklerinin önemli bir kısmı çekirdek modunda yürütülüyordu. Farklı bir profil oluşturma yöntemi kullanarak uygulamanızın profilini çıkarmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Windows'da kod çekirdek modunda veya kullanıcı modunda yürütülebilir. (Çekirdek modu ayrıcalıklı mod olarak da adlandırılır.) Yalnızca aygıt sürücüsü gibi düşük düzeyli sistem kodu çekirdek modunda çalışır. Kullanıcı modu uygulaması, G/Ç işlemlerini gerçekleştirmek, iş parçacığı veya işlem senkronizasyonu ilkellerini beklemek veya sistem çağrıları yapmak için çekirdek moduna geçiş yapabilir.

 Örnekleme, zamanlarının çoğunu kullanıcı modunda çalışarak geçiren uygulamaların profilini çıkarırken en etkili olandır. Uygulama çekirdek modunda yürütüldüğünde toplanan örnek sayısı sık G/Ç işlemlerini gösterebilir veya bağlam anahtarlarının oluştuğunu gösterebilir. Bu işlemlerin hiçbiri örnekleme yöntemi kullanılarak araştırılamaz. Çok fazla çekirdek modu örneği alınırsa, örnekleme verileri istatistiksel olarak anlamlı olacak kadar kullanıcı modu örneği içermeyebilir.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Aşağıdaki seçeneklerden birini kullanarak uygulamanızın profilini yeniden oluşturmayı düşünün:

- Enstrümantasyon yöntemini kullanarak profil.

- Kullanıcı modunda daha fazla örnek toplamaya çalışmak için örnekleme oranını artırın.
