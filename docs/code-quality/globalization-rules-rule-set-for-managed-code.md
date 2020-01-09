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
ms.openlocfilehash: 5502989e3866cb28d05e36d4c88e38574e5987c9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587608"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genelleştirme Kuralları kural kümesi

Uygulamanızdaki verilerin farklı dillerde, yerel ayarlarda ve kültürlerde doğru görünmesini engelleyebilecek sorunlara odaklanmak için Microsoft Genelleştirme kuralları kural kümesini kullanın. Uygulamanız yerelleştirilmiş, Genelleştirilmiş veya her ikisi de varsa, bu kural kümesini eklemeniz gerekir.

|Kural|Açıklama|
|----------|-----------------|
|[CA1300](../code-quality/ca1300.md)|MessageBoxOptions belirt|
|[CA1301](../code-quality/ca1301.md)|Yinelenen hızlandırıcılardan kaçının|
|[CA1302](../code-quality/ca1302.md)|Yerel ayara özgü dizeler vermeyin|
|[CA1303](../code-quality/ca1303.md)|Harfleri yerelleştirilmiş parametreler olarak göndermeyin|
|[CA1304](../code-quality/ca1304.md)|CultureInfo belirt|
|[CA1305](../code-quality/ca1305.md)|IFormatProvider belirt|
|[CA1306](../code-quality/ca1306.md)|Veri türleri için yereli ayarlayın|
|[CA1307](../code-quality/ca1307.md)|StringComparison belirt|
|[CA1308](../code-quality/ca1308.md)|Dizeleri büyük harfe normalleştirin|
|[CA1309](../code-quality/ca1309.md)|Sıralı StringComparison kullanın|
|[CA2101](../code-quality/ca2101.md)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|
