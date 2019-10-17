---
title: 'CA1712: Numaralandırma değerleri için tür adıyla önek kullanmayın'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9bf4d7d2ee0df2a6c5330fcfb8fe6bd168e318c9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72439399"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Numaralandırma değerleri için tür adıyla önek kullanmayın

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Kategori|Microsoft. Naming|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Sabit listesi, adı numaralandırmanın tür adıyla başlayan bir üye içerir.

## <a name="rule-description"></a>Kural açıklaması
Tür bilgilerinin geliştirme araçları tarafından sağlanması beklendiğinden, numaralandırma üyelerinin adlarına tür adı ön eki uygulanmaz.

Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni bir yazılım kitaplığı öğrenmek için gereken süreyi azaltır ve müşterinin, yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiği müşterilerin güvenini arttırır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kuralın ihlalini onarmak için, tür adı önekini numaralandırma üyesinden kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
Aşağıdaki örnek, düzeltilmiş sürüm tarafından izlenen yanlış adlandırılmış bir numaralandırmayı gösterir.

[!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
[!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
[!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>İlgili kurallar
[CA1711: Tanımlayıcıların sonekleri yanlış olmamalıdır](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

[CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

[CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Enum?displayProperty=fullName>
