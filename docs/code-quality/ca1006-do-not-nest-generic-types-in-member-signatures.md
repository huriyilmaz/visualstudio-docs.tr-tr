---
title: 'CA1006: Üye imzalarında genel türleri iç içe kullanmayın'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e69a32e7215e9609d1e1cb2c23572997b11a7fc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446896"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: Üye imzalarında genel türleri iç içe kullanmayın

|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Kategori|Microsoft. Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Dışarıdan görünür bir üyenin, iç içe geçmiş bir tür bağımsız değişkeni içeren bir imzası vardır.

## <a name="rule-description"></a>Kural açıklaması
Bir yuvalanmış bağımsız değişken aynı zamanda genel tip olan bir tip bağımsız değişkendir. Yuvalanmış tip bağımsız değişkeni içeren imzası olan bir üye çağırmak için, kullanıcı bir genel tipi örneklemeli ve bu tipi ikinci bir genel tipin yapıcısına geçirmelidir. Gerekli yordam ve sözdizimi karmaşıktır ve kaçınılmalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için, iç içe geçmiş tür bağımsız değişkenini kaldırmak üzere tasarımı değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan uyarıyı bastırmayın. Anlaşılması kolay ve kullanımı kolay bir sözdiziminde genel türler sağlamak, yeni kitaplıkların benimseme oranını öğrenmek ve artmak için gereken süreyi azaltır.

## <a name="example"></a>Örnek
Aşağıdaki örnek, kuralı ve ihlal eden yöntemi çağırmak için gereken sözdizimini ihlal eden bir yöntemi gösterir.

[!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
[!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>İlgili kurallar
[CA1005: Genel türlerde aşırı parametrelerden kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Koleksiyonlar genel arabirim uygulamalıdır](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Genel türlerde statik üyeleri belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Genel olay işleyici örnekleri kullan](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Uygun yerlerde genel türler kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca bkz.
[Genel Türler](/dotnet/csharp/programming-guide/generics/index)
