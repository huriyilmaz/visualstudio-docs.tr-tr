---
title: 'DA0004: Yüksek işlemci kullanımı | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b324d26d21920bae9f03f909b2eab0c1ce7ab419
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777731"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Yüksek işlemci kullanımı

|||
|-|-|
|Kural Id|DA0004|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemleri|İzleme<br /><br /> Örnekleme|
|İleti|İşlemci kullanımınız sürekli olarak %75'in üzerindedir. CPU'ya bağlı uygulamalar için Örnekleme modunu kullanmayı düşünün.|
|Kural türü|Bilgi|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 İşlemci (CPU) kullanımı, enstrümantasyon yöntemi kullanılarak toplanan verilerin profil oluşturmasında yüksekti. CPU'ya bağlı bir uygulamanın profilini çıkarırken örnekleme profil oluşturma yöntemini kullanmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Bu profil oluşturma çalışması sırasında işlemci (veya işlemciler) sürekli olarak meşguldü. Yüksek CPU kullanımı CPU'ya bağlı bir uygulamayı gösterebilir. Enstrümantine profilleri CPU kullanım senaryoları araştırmak için en etkili yolu değildir. Örnekleme, zamanlarının çoğunu işlemci üzerindeki yönergeleri uygulayarak geçiren uygulamaların profilini çıkarırken daha etkilidir.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 İşlev zamanlamaları gerektirmedikçe veya işlemci darboğazlarından çok giriş/çıktıyı anlamakla ilgilenmiyorsanız, uygulamanızı enstrümantasyon yöntemi yerine örnekleme yöntemini kullanarak yeniden profil oluşturmayı düşünün.
