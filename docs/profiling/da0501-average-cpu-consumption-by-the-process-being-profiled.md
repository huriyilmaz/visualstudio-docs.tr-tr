---
title: 'DA0501: İşlemin ortalama CPU kullanımının profili oluşturuluyor. | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777469"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: işlem tarafından ortalama CPU kullanımı profili oluşturuldu.

|||
|-|-|
|Kural Kimliği|DA501|
|Kategori|Kaynak Izleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Profili oluşturulan İşlemin Ortalama CPU kullanımı.|
|Kural türü|Bilgisi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin yüzdesini bildirir. Bildirilen değer, işlem yapılan işlemin etkin olduğu tüm ölçüm aralıklarının ortalaması olarak belirlenir. Değerin değeri, birden fazla işlemciye sahip bir makinede %100 değerinden büyük olabilir.

## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma
 Programın farklı sürümlerinin veya derlemelerin performansını karşılaştırmak veya farklı test senaryoları altında uygulamanın performansını anlamak için kural değerini kullanın.
