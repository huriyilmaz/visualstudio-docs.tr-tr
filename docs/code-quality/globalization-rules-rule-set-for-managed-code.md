---
title: Yönetilen kod için Genelleştirme Kuralları kural kümesi
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4a4aa987c58ace1bb2fa8c0a2dfac3c0aecd87d7
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535870"
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
