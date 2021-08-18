---
title: DA0501 - Profili yapılan İşlem tarafından ortalama CPU tüketimi. | Microsoft Belgeleri
description: Bu ileti, bir işlemcinin uygulama yönergelerini yürütmekle meşgul olduğu süre yüzdesini raporlar.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 75d9f0006d72e00a88ed434d6530cdc0a81db15f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142162"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Profili yapılan işlem tarafından ortalama CPU tüketimi.

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA501|
|Kategori|Kaynak İzleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Profili oluşturulan İşlemin Ortalama CPU kullanımı.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 10 örnek toplayan bu kuralı tetiklemeniz gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, bir işlemcinin uygulama yönergelerini yürütmekle meşgul olduğu süre yüzdesini raporlar. Bildirilen değer, profili yapılan sürecin etkin olduğu tüm ölçüm aralıklarının ortalamasıdır. Değerin değeri, birden fazla işlemciye sahip bir makinede %100'den büyük olabilir.

## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma
 Programın farklı sürümlerinin veya derlemelerinin performansını karşılaştırmak veya farklı test senaryolarında uygulamanın performansını anlamak için kural değerini kullanın.
