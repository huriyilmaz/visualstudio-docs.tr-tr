---
title: DA0501-profili oluşturulan Işlem tarafından ortalama CPU kullanımı. | Microsoft Belgeleri
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 7f03a65842664ec5d0ed2841f791dd168d82860e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544579"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: işlem tarafından ortalama CPU kullanımı profili oluşturuldu.

|Öğe|Değer|
|-|-|
|Kural kimliği|DA501|
|Kategori|Kaynak Izleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Profili oluşturulan İşlemin Ortalama CPU kullanımı.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin yüzdesini bildirir. Bildirilen değer, işlem yapılan işlemin etkin olduğu tüm ölçüm aralıklarının ortalaması olarak belirlenir. Değerin değeri, birden fazla işlemciye sahip bir makinede %100 değerinden büyük olabilir.

## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma
 Programın farklı sürümlerinin veya derlemelerin performansını karşılaştırmak veya farklı test senaryoları altında uygulamanın performansını anlamak için kural değerini kullanın.
