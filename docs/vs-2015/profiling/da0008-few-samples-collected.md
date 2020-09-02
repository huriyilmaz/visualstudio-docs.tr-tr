---
title: 'DA0008: toplanan birkaç örnek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03fd9b6fd794320faf76119616900b79d5bf4333
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187853"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Az sayıda örnek toplandı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0008 |  
| Kategori | Profil Oluşturma Araçları kullanımı |  
| Profil oluşturma yöntemi | Örnekleme |  
| İleti | Yalnızca birkaç örnek toplandı. Daha önemli sonuçlar için daha uzun bir çalıştırma veya daha hızlı örnekleme oranı düşünün. |  
| Kural türü | Bilgi |  
  
## <a name="cause"></a>Nedeni  
 Profil oluşturma çalıştırmasında yalnızca birkaç örnek toplandı.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Örnekleme yöntemi kullanıldığında, verilerin gerçek program davranışını temsil ettiğinden emin olmak için istatistiksel olarak önemli sayıda örnek toplamanız gerekir. Örnekleme hatalarını en aza indirmek için, program yönergesi yürütme davranışının en az 1000 örneğini toplamaya çalışırsınız. Yeterli örnek toplamazsınız, profil oluşturma verilerini çözümlediğinizde yanlış olabilir.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Uygulamanın daha uzun bir şekilde çalıştırılmasını veya istatistiksel olarak önemli sonuçlar elde etmek için daha hızlı örnekleme hızı kullanmayı düşünün. Visual Studio IDE 'de örnekleme hızının nasıl değiştirileceği hakkında bilgi için bkz. [nasıl yapılır: örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md). Profil Oluşturma Araçları komut satırını kullanırken örnekleme hızının nasıl değiştirileceği hakkında daha fazla bilgi için bkz. [VSPerfCmd](../profiling/vsperfcmd.md) Reference içindeki [Timer](../profiling/timer.md) .
