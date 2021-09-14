---
title: DA0003 - Birçok çekirdek örneği | Microsoft Docs
description: Uygulama için toplanan çağrı yığını örneklerinin önemli bir oranı çekirdek modunda yürütülmektedir.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c181aa99ce1005bf3909cf7f5c9a59a409b15990
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627002"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Pek çok çekirdek örneği

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0003|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemleri|Örnekleme|
|İleti|Çekirdek Modunda örneklerin büyük bir oranına sahipsiniz. Bu, yüksek hacimli bir I/O etkinliği veya yüksek oranda bağlam değiştirme olduğunu gösteriyor olabilir. Ölçüm modunu kullanarak uygulamanın profilini oluşturmayı yeniden düşünün.|
|Kural türü|Bilgi|

## <a name="cause"></a>Nedeni
 Uygulama için toplanan çağrı yığını örneklerinin önemli bir oranı çekirdek modunda yürütülmektedir. Farklı bir profil oluşturma yöntemi kullanarak uygulamanın profilini oluşturmayı göz önünde bulundurabilirsiniz.

## <a name="rule-description"></a>Kural açıklaması
 Bu Windows, kod çekirdek modunda veya kullanıcı modunda yürütülebilirsiniz. (Çekirdek modu ayrıcalıklı mod olarak da adlandırılan bir moddur.) Yalnızca cihaz sürücüsü gibi alt düzey sistem kodu çekirdek modunda çalışır. Kullanıcı modu uygulaması, I/O işlemlerini gerçekleştirmek, iş parçacığı veya işlem eşitleme temellerini beklemek veya sistem çağrıları yapmak için çekirdek moduna geçiş yapar.

 Örnekleme, zamanlarının çoğunu kullanıcı modunda iş yaparak harcayan uygulamaların profilini oluşturmada en etkilidir. Uygulama çekirdek modunda yürütücürken toplanan örnek sayısı, sık sık yapılan I/O işlemlerini veya bağlam anahtarlarının oluştuğunu gösteriyor olabilir. Bu işlemlerin hiçbiri örnekleme yöntemi kullanılarak araştırılaamaz. Çok fazla çekirdek modu örneği alınırsa, örnekleme verileri istatistiksel olarak anlamlı olacak kadar kullanıcı modu örneği içeremiyor olabilir.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Aşağıdaki seçeneklerden birini kullanarak uygulamanın profilini oluşturmayı yeniden düşünün:

- Ölçümleme yöntemini kullanarak profil oluşturun.

- Kullanıcı modunda daha fazla örnek toplamayı denemek için örnekleme oranını artırabilirsiniz.
