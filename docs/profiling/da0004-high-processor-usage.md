---
title: DA0004 - Yüksek işlemci kullanımı | Microsoft Docs
description: Ölçümleme yöntemi kullanılarak toplanan profil oluşturma verilerinde işlemci (CPU) kullanımı yüksekti.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f5f4dfccfdc8814992ecdac095408efabdd3f2d8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076678"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Yüksek işlemci kullanımı

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0004|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemleri|İzleme<br /><br /> Örnekleme|
|İleti|İşlemci kullanımınız tutarlı olarak %75'in üzerinde. CPU'ya bağlı uygulamalar için Örnekleme modunu kullanmayı göz önünde bulundurabilirsiniz.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 10 örnek toplayan bu kuralı tetiklemeniz gerekir.

## <a name="cause"></a>Nedeni
 Ölçümleme yöntemi kullanılarak toplanan profil oluşturma verilerinde işlemci (CPU) kullanımı yüksekti. CPU'ya bağlı bir uygulamanın profilini oluşturmada örnekleme profil oluşturma yöntemini kullanmayı göz önünde bulundurabilirsiniz.

## <a name="rule-description"></a>Kural açıklaması
 Bu profil oluşturma çalıştırması sırasında işlemci (veya işlemciler) sürekli olarak meşguldu. Yüksek CPU kullanımı, CPU'ya bağlı bir uygulama olduğunu gösteriyor olabilir. Cpu kullanımı senaryolarını araştırmanın en etkili yolu, takip edilen profiller değildir. Örnekleme, zamanlarının çoğunu işlemcide yönergeleri yürütmek için harcayan uygulamaların profilini oluşturma konusunda daha etkilidir.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 İşlev zamanlamalarına gerek yoksa veya giriş/çıkış sorunlarını işlemci performans sorunlarını anlamaktan daha çok ilgileniyorsanız, ölçüm yöntemi yerine örnekleme yöntemini kullanarak uygulamanın profilini oluşturmayı yeniden göz önünde bulundurabilirsiniz.
