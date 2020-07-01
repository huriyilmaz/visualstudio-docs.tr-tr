---
title: DA0003-birçok çekirdek örneği | Microsoft Docs
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0523f9a21dbdb655a02fb6263a6eb644458ab6d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548232"
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
 Windows 'da, kod çekirdek modunda veya Kullanıcı modunda yürütülebilir. (Çekirdek modu ayrıcalıklı mod olarak da adlandırılır.) Çekirdek modunda, yalnızca bir cihaz sürücüsü gibi alt düzey sistem kodu çalışır. Kullanıcı modu uygulaması g/ç işlemlerini gerçekleştirmek, iş parçacığı veya işlem eşitleme temelleri için beklemek veya sistem çağrıları yapmak için çekirdek moduna geçirebilir.

 Örnekleme en çok, kullanıcı modunda çalışma zamanının çoğunu harcayabileceğiniz uygulamalar için profil oluştururken etkilidir. Uygulama çekirdek modunda yürütüldüğü zaman toplanan örneklerin sayısı, sık kullanılan g/ç işlemlerini gösterebilir veya bağlam anahtarlarının gerçekleştiğini gösterebilir. Bu işlemlerden hiçbiri örnekleme yöntemi kullanılarak araştırılmaz. Çok fazla sayıda çekirdek modu örneği alınmıyorsa, örnekleme verileri istatistiksel olarak önemli olacak şekilde yeterli sayıda kullanıcı modu örneği içermeyebilir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 Aşağıdaki seçeneklerden birini kullanarak uygulamanızın profilini oluşturmayı düşünün:

- İzleme yöntemini kullanarak profil.

- Kullanıcı modunda daha fazla örnek toplamayı denemek için örnekleme hızını artırın.
