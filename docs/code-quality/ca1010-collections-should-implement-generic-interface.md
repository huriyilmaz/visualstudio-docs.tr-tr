---
title: 'CA1010: Koleksiyonlar genel arabirim uygulamalıdır'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3e50fb93e8cdfe6f65fe1b2de1da54b58a6a8c9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449314"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Koleksiyonlar genel arabirim uygulamalıdır

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategori|Microsoft. Design|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep

Bir tür <xref:System.Collections.IEnumerable?displayProperty=fullName> arabirimini uygular, ancak <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> arabirimini uygulamaz ve içeren derleme .NET ' i hedefliyor. Bu kural <xref:System.Collections.IDictionary?displayProperty=fullName> uygulayan türleri yoksayar.

Bu kural varsayılan olarak yalnızca dışarıdan görünür türlere bakar, ancak bu [yapılandırılabilir](#configurability).

## <a name="rule-description"></a>Kural açıklaması

Bir koleksiyon kullanılabilirliğini genişletmek için genel koleksiyon arabirimlerinden birini uygulayın. Daha sonra koleksiyon, aşağıdakiler gibi genel koleksiyon türlerini doldurmak için kullanılabilir:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kuralın ihlalini onarmak için aşağıdaki genel koleksiyon arabirimlerinden birini uygulayın:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Bu kuraldan bir uyarıyı gizlemek güvenlidir; Ancak, koleksiyonun kullanımı daha sınırlı olacaktır.

## <a name="configurability"></a>Yapılandırılabilirlik

Bu kuralı [FxCop çözümleyicilerinin](install-fxcop-analyzers.md) (eski analizler olmadan) çalıştırıyorsanız, kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz. Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir. editorconfig dosyasına ekleyin:

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

Bu seçeneği yalnızca bu kural için, tüm kurallar için veya bu kategorideki tüm kurallar (tasarım) için yapılandırabilirsiniz. Daha fazla bilgi için bkz. [FxCop çözümleyicileri yapılandırma](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Örnek ihlali

Aşağıdaki örnek, bu kuralı ihlal eden genel olmayan `CollectionBase` sınıfından türetilen bir sınıfı (başvuru türü) gösterir.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Bu kuralın ihlalini onarmak için aşağıdakilerden birini yapın:

- Genel arabirimleri uygulayın.
- Temel sınıfı, `Collection<T>` sınıfı gibi hem genel hem de genel olmayan arabirimleri zaten uygulayan bir türle değiştirin.

## <a name="fix-by-base-class-change"></a>Temel sınıf değişikliğine göre düzeltir

Aşağıdaki örnek, koleksiyonun temel sınıfını genel olmayan `CollectionBase` sınıfından genel `Collection<T>` (`Collection(Of T)` Visual Basic) sınıfında değiştirerek ihlalin düzeltir.

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Zaten yayınlanmış bir sınıfın temel sınıfını değiştirmek, mevcut tüketicilerle bir son değişiklik olarak kabul edilir.

## <a name="fix-by-interface-implementation"></a>Arabirim uygulamasına göre onarma

Aşağıdaki örnek şu genel arabirimleri uygulayarak ihlalin düzeltir: `IEnumerable<T>`, `ICollection<T>` ve `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)` ve `IList(Of T)` Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>İlgili kurallar

- [CA1005: Genel türlerde aşırı parametrelerden kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: Genel türlerde statik üyeleri belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Üye imzalarında genel türleri iç içe kullanmayın](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Genel olay işleyici örnekleri kullan](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Uygun yerlerde genel türler kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Türler](/dotnet/csharp/programming-guide/generics/index)
