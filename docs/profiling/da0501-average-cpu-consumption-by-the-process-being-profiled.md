---
title: DA0501-profili oluşturulan Işlem tarafından ortalama CPU kullanımı. | Microsoft Belgeleri
description: Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin yüzdesini bildirir.
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
ms.openlocfilehash: d503321cf877a1132795c14d7705cbce356cba6304d94b7adaad9d58eee2d358
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396688"
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
