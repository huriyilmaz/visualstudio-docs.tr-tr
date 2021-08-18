---
title: DA0008-toplanan birkaç örnek | Microsoft Docs
description: Profil oluşturma çalıştırmasında yalnızca birkaç örnek toplandı.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d00ee39802b5e1cf5b1f449f4a34b511146d95cdd0cda53aa1a53a0285d7cf74
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427164"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Az sayıda örnek toplandı

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0008|
|Kategori|Profil Oluşturma Araçları kullanımı|
|Profil oluşturma yöntemi|Örnekleme|
|İleti|Yalnızca birkaç örnek toplandı. Daha önemli sonuçlar için daha uzun bir çalıştırma veya daha hızlı örnekleme oranı düşünün.|
|Kural türü|Bilgi|

## <a name="cause"></a>Nedeni
 Profil oluşturma çalıştırmasında yalnızca birkaç örnek toplandı.

## <a name="rule-description"></a>Kural açıklaması
 Örnekleme yöntemi kullanıldığında, verilerin gerçek program davranışını temsil ettiğinden emin olmak için istatistiksel olarak önemli sayıda örnek toplamanız gerekir. Örnekleme hatalarını en aza indirmek için, program yönergesi yürütme davranışının en az 1000 örneğini toplamaya çalışırsınız. Yeterli örnek toplamazsınız, profil oluşturma verilerini çözümlediğinizde yanlış olabilir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 Uygulamanın daha uzun bir şekilde çalıştırılmasını veya istatistiksel olarak önemli sonuçlar elde etmek için daha hızlı örnekleme hızı kullanmayı düşünün. Visual Studio ıde 'de örnekleme hızının nasıl değiştirileceği hakkında bilgi için bkz. [nasıl yapılır: örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md). Profil Oluşturma Araçları komut satırını kullanırken örnekleme hızının nasıl değiştirileceği hakkında daha fazla bilgi için bkz. [VSPerfCmd](../profiling/vsperfcmd.md) Reference içindeki [Timer](../profiling/timer.md) .
