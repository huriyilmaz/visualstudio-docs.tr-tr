---
title: 'DA0003: birçok çekirdek örneği | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad9a0671595d4628932ff4f2db41a137e060c4d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158717"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Pek çok çekirdek örneği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0003 |  
| Kategori | Profil Oluşturma Araçları kullanımı |  
| Profil oluşturma yöntemleri | Örnekleme |  
| İleti | Çekirdek modunda daha yüksek bir örnek oranı vardır. Bu, yüksek hacimli g/ç etkinliğinin veya yüksek oranda bağlam geçişinin olduğunu gösterebilir. Izleme modunu kullanarak uygulamanızın profilini oluşturmayı deneyin. |  
| Kural türü | Bilgi |  
  
## <a name="cause"></a>Nedeni  
 Uygulama için toplanan çağrı yığını örneklerinin önemli bir oranı çekirdek modunda yürütülüyor. Farklı bir profil oluşturma yöntemi kullanarak uygulamanızın profilini oluşturmayı düşünün.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Windows 'da, kod çekirdek modunda veya Kullanıcı modunda yürütülebilir. (Çekirdek modu ayrıcalıklı mod olarak da adlandırılır.) Çekirdek modunda, yalnızca bir cihaz sürücüleri gibi alt düzey sistem kodu çalışır. Kullanıcı modu uygulaması g/ç işlemlerini gerçekleştirmek, iş parçacığı veya işlem eşitleme temelleri için beklemek veya sistem çağrıları yapmak için çekirdek moduna geçirebilir.  
  
 Örnekleme en çok, kullanıcı modunda çalışma zamanının çoğunu harcayabileceğiniz uygulamalar için profil oluştururken etkilidir. Uygulama çekirdek modunda yürütüldüğü zaman toplanan örneklerin sayısı, sık kullanılan g/ç işlemlerini gösterebilir veya bağlam anahtarlarının gerçekleştiğini gösterebilir. Bu işlemlerden hiçbiri örnekleme yöntemi kullanılarak araştırılmaz. Çok fazla sayıda çekirdek modu örneği alınmıyorsa, örnekleme verileri istatistiksel olarak önemli olacak şekilde yeterli sayıda kullanıcı modu örneği içermeyebilir.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Aşağıdaki seçeneklerden birini kullanarak uygulamanızın profilini oluşturmayı düşünün:  
  
- İzleme yöntemini kullanarak profil.  
  
- Kullanıcı modunda daha fazla örnek toplamayı denemek için örnekleme hızını artırın.
