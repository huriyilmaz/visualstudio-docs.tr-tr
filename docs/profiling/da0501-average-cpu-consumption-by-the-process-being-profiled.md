---
title: 'DA0501: İşlemin ortalama CPU kullanımının profili oluşturuluyor. | Microsoft Belgeleri'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d9835ad1965d1fd9a31113117eeb07ed62fd8ec4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777469"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Profilden alınan işlemle ortalama CPU tüketimi.

|||
|-|-|
|Kural Id|DA501|
|Kategori|Kaynak İzleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Profili oluşturulan İşlemin Ortalama CPU kullanımı.|
|Kural türü|Bilgi|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlemcinin uygulamadan gelen yönergeleri yürütmekle meşgul olduğu süre yüzdesini bildirir. Bildirilen değer, profillenen işlemin etkin olduğu tüm ölçüm aralıklarının ortalamasıdır. Birden fazla işlemcisi olan bir makinede değer değeri %100'den büyük olabilir.

## <a name="how-to-use-rule-data"></a>Kural verileri nasıl kullanılır?
 Farklı sürümlerin veya programın yapılarının performansını karşılaştırmak veya farklı test senaryoları altında uygulamanın performansını anlamak için kural değerini kullanın.
