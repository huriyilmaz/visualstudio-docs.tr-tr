---
title: DA0003-birçok çekirdek örneği | Microsoft Docs
description: Uygulama için toplanan çağrı yığını örneklerinin önemli bir oranı çekirdek modunda yürütülüyor.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076717"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Pek çok çekirdek örneği

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0003|
|Kategori|Profil Oluşturma Araçları kullanımı|
|Profil oluşturma yöntemleri|Örnekleme|
|İleti|Çekirdek modunda daha yüksek bir örnek oranı vardır. Bu, yüksek hacimli g/ç etkinliğinin veya yüksek oranda bağlam geçişinin olduğunu gösterebilir. Izleme modunu kullanarak uygulamanızın profilini oluşturmayı düşünün.|
|Kural türü|Bilgi|

## <a name="cause"></a>Nedeni
 Uygulama için toplanan çağrı yığını örneklerinin önemli bir oranı çekirdek modunda yürütülüyor. Farklı bir profil oluşturma yöntemi kullanarak uygulamanızın profilini oluşturmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Windows, kod çekirdek modunda veya kullanıcı modunda yürütülebilir. (Çekirdek modu ayrıcalıklı mod olarak da adlandırılır.) Çekirdek modunda, yalnızca bir cihaz sürücüsü gibi alt düzey sistem kodu çalışır. Kullanıcı modu uygulaması g/ç işlemlerini gerçekleştirmek, iş parçacığı veya işlem eşitleme temelleri için beklemek veya sistem çağrıları yapmak için çekirdek moduna geçirebilir.

 Örnekleme en çok, kullanıcı modunda çalışma zamanının çoğunu harcayabileceğiniz uygulamalar için profil oluştururken etkilidir. Uygulama çekirdek modunda yürütüldüğü zaman toplanan örneklerin sayısı, sık kullanılan g/ç işlemlerini gösterebilir veya bağlam anahtarlarının gerçekleştiğini gösterebilir. Bu işlemlerden hiçbiri örnekleme yöntemi kullanılarak araştırılmaz. Çok fazla sayıda çekirdek modu örneği alınmıyorsa, örnekleme verileri istatistiksel olarak önemli olacak şekilde yeterli sayıda kullanıcı modu örneği içermeyebilir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 Aşağıdaki seçeneklerden birini kullanarak uygulamanızın profilini oluşturmayı düşünün:

- İzleme yöntemini kullanarak profil.

- Kullanıcı modunda daha fazla örnek toplamayı denemek için örnekleme hızını artırın.
