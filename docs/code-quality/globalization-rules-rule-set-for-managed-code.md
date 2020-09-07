---
title: Yönetilen kod için Genelleştirme Kuralları kural kümesi
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2af6126c751d03968dc7ecd87693e3546376c12a
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509867"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genelleştirme Kuralları kural kümesi

Uygulamanızdaki verilerin farklı dillerde, yerel ayarlarda ve kültürlerde doğru görünmesini engelleyebilecek sorunlara odaklanmak için Microsoft Genelleştirme kuralları kural kümesini kullanın. Uygulamanız yerelleştirilmiş, Genelleştirilmiş veya her ikisi de varsa, bu kural kümesini eklemeniz gerekir.

|Kural|Açıklama|
|----------|-----------------|
|[CA1303](../code-quality/ca1303.md)|Harfleri yerelleştirilmiş parametreler olarak göndermeyin|
|[CA1304](../code-quality/ca1304.md)|CultureInfo belirt|
|[CA1305](../code-quality/ca1305.md)|IFormatProvider belirt|
|[CA1307](../code-quality/ca1307.md)|Açıklık için StringComparison belirtin|
|[CA1308](../code-quality/ca1308.md)|Dizeleri büyük harfe normalleştirin|
|[CA1309](../code-quality/ca1309.md)|Sıralı StringComparison kullanın|
|[CA1310](../code-quality/ca1310.md)|Doğruluk için StringComparison belirtin|
|[CA2101](../code-quality/ca2101.md)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|
