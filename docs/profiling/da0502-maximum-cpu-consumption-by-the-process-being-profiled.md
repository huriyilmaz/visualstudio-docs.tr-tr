---
title: 'DA0502: Profilleme Süreci ile maksimum CPU tüketimi | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5c3cb5169d078ba1242bf898ba93e31a7a488bb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779343"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Profilden alınan işlemle maksimum CPU tüketimi

|||
|-|-|
|Kural Id|DA0502|
|Kategori|Kaynak İzleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu kural yalnızca bilgi içindir. İşlem()\\% İşlemci Zamanı karşı, profil oluşturma yaptığınız işlemin CPU tüketimini ölçer. Bildirilen değer, tüm ölçüm aralıklarında gözlenen maksimum değerdir.|
|Kural türü|Bilgilendirici|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, bir işlemcinin uygulamadan gelen yönergeleri yürütmekle meşgul olduğu maksimum süre yüzdesini bildirir. Bildirilen değer, profillenen işlemin etkin olduğu tüm ölçüm aralıkları arasında bildirilen maksimum değerdir. Bu oran, birden fazla işlemcisi olan bir makinede %100'den büyük olabilir.

## <a name="how-to-use-the-rule-data"></a>Kural verileri nasıl kullanılır?
 Farklı sürümlerin veya programın yapılarının performansını karşılaştırmak veya farklı profil oluşturma senaryoları altında uygulamanın performansını anlamak için kural değerini kullanın.
