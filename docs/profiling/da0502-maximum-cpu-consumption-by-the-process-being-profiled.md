---
title: DA0502-profili oluşturulan Işlem tarafından en fazla CPU kullanımı | Microsoft Docs
description: Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin en uzun yüzdesini bildirir.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1d7d0ef9e592d5b8f3c1197a115b8df01aec2c60
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635758"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: işlem tarafından profili oluşturulan en yüksek CPU tüketimi

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0502|
|Kategori|Kaynak Izleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu kural yalnızca bilgi içindir. Işlem () \\ % Işlemci zamanı sayacı, profil oluşturduğunuz IŞLEMIN CPU tüketimini ölçer. Bildirilen değer tüm ölçüm aralıklarında gözlemlenen en yüksek değerdir.|
|Kural türü|Bilgilendirici|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin en uzun yüzdesini bildirir. Bildirilen değer, işlem yapılan işlemin etkin olduğu tüm ölçüm aralıkları arasında raporlanan en büyük değerdir. Yüzde 100 ' den fazla işlemciye sahip bir makinede yüzde ' den büyük olabilir.

## <a name="how-to-use-the-rule-data"></a>Kural verilerini kullanma
 Programın farklı sürümlerinin veya derlemelerin performansını karşılaştırmak veya farklı profil oluşturma senaryolarında uygulamanın performansını anlamak için kural değerini kullanın.
