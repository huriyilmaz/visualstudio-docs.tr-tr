---
title: 'DA0008: Birkaç örnek toplandı | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 15f8eeb370a3f1e61981e0e936704d33f6b44bbd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779447"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Toplanan örnek az

|||
|-|-|
|Kural Id|DA0008|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemi|Örnekleme|
|İleti|Sadece birkaç örnek toplandı. Daha önemli sonuçlar için daha uzun bir çalışma veya daha hızlı örnekleme oranı düşünün.|
|Kural türü|Bilgi|

## <a name="cause"></a>Nedeni
 Profil oluşturma çalışmasında sadece birkaç örnek toplandı.

## <a name="rule-description"></a>Kural açıklaması
 Örnekleme yöntemi kullanıldığında, verilerin gerçek program davranışını temsil ettiğinden emin olmak için istatistiksel olarak önemli sayıda örnek toplamanız gerekir. Örnekleme hatalarını en aza indirmek için, program yönergesi yürütme davranışının en az 1000 örneğini toplamaya çalışmalısınız. Yeterli örnek toplamazsanız, profil oluşturma verilerini çözümlediğinizde yanıltılabilirsiniz.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Uygulamanın daha uzun bir profil oluşturma veya istatistiksel olarak anlamlı sonuçlar elde etmek için daha hızlı bir örnekleme oranı kullanarak düşünün. Visual Studio IDE'deki örnekleme hızının nasıl değiştirilenhakkında bilgi için [bkz.](../profiling/how-to-choose-sampling-events.md) Profil Oluşturma Araçları komut satırını kullandığınızda örnekleme hızını nasıl değiştireceğiniz hakkında daha fazla bilgi için [VSPerfCmd](../profiling/vsperfcmd.md) başvurusunda [Timer'a](../profiling/timer.md) bakın.
