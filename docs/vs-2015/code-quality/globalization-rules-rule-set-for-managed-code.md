---
title: Yönetilen kod için Genelleştirme kuralları kural kümesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1630769b5150d9cef7b00e575ac9c555f5bc5be1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667611"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genelleştirme Kuralları kural kümesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızdaki verilerin farklı dillerde, yerel ayarlarda ve kültürlerde doğru görünmesini engelleyebilecek sorunlara odaklanmak için Microsoft Genelleştirme kuralları kural kümesini kullanabilirsiniz. Uygulamanız yerelleştirilmiş, Genelleştirilmiş veya her ikisi de varsa, bu kural kümesini eklemeniz gerekir.

|Kural|Açıklama|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|MessageBoxOptions belirt|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Yinelenen hızlandırıcılardan kaçının|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Yerel özel dizeleri doğrudan programın içine gömmeyin|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Harfleri yerelleştirilmiş parametreler olarak göndermeyin|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|CultureInfo belirt|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|IFormatProvider belirt|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Veri türleri için yereli ayarlayın|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison belirt|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Dizeleri büyük harfe normalleştirin|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Sıralı StringComparison kullanın|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|
