---
title: Yönetilen kod için Genelleştirme Kuralları kural kümesi
ms.date: 11/04/2016
description: Visual Studio 'da, diller, yerel ayarlar ve kültürler ile ilgili sorunlara odaklanan Genelleştirme kuralları kural kümesi hakkında bilgi edinin. Bkz. kural açıklamaları.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0bf96c8e4140e5b491624d6750b498a26726761c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348885"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genelleştirme Kuralları kural kümesi

Uygulamanızdaki verilerin farklı dillerde, yerel ayarlarda ve kültürlerde doğru görünmesini engelleyebilecek sorunlara odaklanmak için Microsoft Genelleştirme kuralları kural kümesini kullanın. Uygulamanız yerelleştirilmiş, Genelleştirilmiş veya her ikisi de varsa, bu kural kümesini eklemeniz gerekir.

|Kural|Description|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Harfleri yerelleştirilmiş parametreler olarak göndermeyin|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|CultureInfo belirt|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|IFormatProvider belirt|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|Açıklık için StringComparison belirtin|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Dizeleri büyük harfe normalleştirin|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Sıralı StringComparison kullanın|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|Doğruluk için StringComparison belirtin|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|
