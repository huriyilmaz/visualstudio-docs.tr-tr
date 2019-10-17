---
title: 'CA1714: Bayrak numaralandırmalarında çoğul adlar olmalıdır'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865ed4feb0e95d7fbe1f2d7894a1c6bb3bcb8c6f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72439241"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Bayrak numaralandırmalarında çoğul adlar olmalıdır

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategori|Microsoft. Naming|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Sabit Listesi <xref:System.FlagsAttribute?displayProperty=fullName> ' dır ve adı ' ın ' de bitmez.

Bu kural varsayılan olarak yalnızca dışarıdan görünür numaralandırmalara bakar, ancak bu [yapılandırılabilir](#configurability).

## <a name="rule-description"></a>Kural açıklaması

@No__t-0 ile işaretlenen türler, öznitelik birden fazla değerin belirtidiğini gösterdiği için çoğul olan adlara sahiptir. Örneğin, haftanın günlerini tanımlayan bir numaralandırma, birden çok gün belirtebileceğiniz bir uygulamada kullanılmak üzere tasarlanmış olabilir. Bu numaralandırma <xref:System.FlagsAttribute> olmalıdır ve ' Days ' olarak çağrılabilir. Yalnızca tek bir günün belirtilmesini sağlayan benzer bir numaralandırma özniteliğe sahip değildir ve ' Day ' olarak çağrılabilir.

Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Sabit listesinin bir çoğul kelime olmasını veya birden çok numaralandırma değerinin aynı anda belirtilmemelidir <xref:System.FlagsAttribute> özniteliğini kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Ad bir plural sözcükse ancak ' ın içinde bitmezse ihlalin görünmemesi güvenli bir hale gelir. Örneğin, daha önce açıklanan birden çok günlük numaralandırması ' DaysOfTheWeek ' olarak adlandırılmışsa, bu kural mantığını ihlal etmez ancak amacını ihlal etmez. Bu ihlallerin gizlenmesi gerekir.

## <a name="configurability"></a>Yapılandırılabilirlik

Bu kuralı [FxCop çözümleyicilerinin](install-fxcop-analyzers.md) (eski analizler olmadan) çalıştırıyorsanız, kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz. Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir. editorconfig dosyasına ekleyin:

```ini
dotnet_code_quality.ca1714.api_surface = private, internal
```

Bu seçeneği yalnızca bu kural için, tüm kurallar için veya bu kategorideki tüm kurallar (adlandırma) için yapılandırabilirsiniz. Daha fazla bilgi için bkz. [FxCop çözümleyicileri yapılandırma](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>İlgili kurallar

- [CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Numaralandırma tasarımı](/dotnet/standard/design-guidelines/enum)
