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
ms.openlocfilehash: 905f3323f4ede33ba8a7e1547bed7a81c43be96d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449039"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genelleştirme Kuralları kural kümesi

Uygulamanızdaki verilerin farklı dillerde, yerel ayarlarda ve kültürlerde doğru görünmesini engelleyebilecek sorunlara odaklanmak için Microsoft Genelleştirme kuralları kural kümesini kullanın. Uygulamanız yerelleştirilmiş, Genelleştirilmiş veya her ikisi de varsa, bu kural kümesini eklemeniz gerekir.

|Kural|Açıklama|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|MessageBoxOptions belirt|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Yinelenen hızlandırıcılardan kaçının|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Yerel ayara özgü dizeler vermeyin|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Harfleri yerelleştirilmiş parametreler olarak göndermeyin|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|CultureInfo belirt|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|IFormatProvider belirt|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Veri türleri için yereli ayarlayın|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison belirt|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Dizeleri büyük harfe normalleştirin|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Sıralı StringComparison kullanın|
|[CA2101](../code-quality/ca2101.md)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|
