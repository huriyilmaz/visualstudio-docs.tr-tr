---
title: 'CA1007: Uygun yerlerde genel türler kullanın'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d2c9416d1cdc655df110c7230b9f0e29290221a7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441694"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Uygun yerlerde genel türler kullanın

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Kategori|Microsoft. Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Dışarıdan görünen bir yöntem <xref:System.Object?displayProperty=fullName> türünde bir başvuru parametresi içerir ve içeren derleme .NET Framework 2,0 ' i hedefler.

## <a name="rule-description"></a>Kural açıklaması
Başvuru parametresi, `ref` @no__t ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) anahtar sözcüğü kullanılarak değiştirilen bir parametredir. Başvuru parametresi için sağlanan bağımsız değişken türü, başvuru parametre türü ile tam olarak eşleşmelidir. Başvuru parametre türünden türetilmiş bir türü kullanmak için, öncelikle tür cast ve başvuru parametre türündeki bir değişkene atanmalıdır. Genel bir yöntemin kullanımı, tüm türlerin ve öncelikle türü başvuru parametre türüne dönüştürmeksizin yönteme geçirilmesini sağlar.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için, yöntemi genel yapın ve <xref:System.Object> parametresini bir tür parametresi kullanarak değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
Aşağıdaki örnek, hem genel olmayan hem de genel yöntemler olarak uygulanan genel amaçlı bir değiştirme yordamını göstermektedir. Dizelerin, genel yöntemi kullanılarak genel olmayan yönteme kıyasla ne kadar verimli bir şekilde yer aldığı unutulmamalıdır.

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>İlgili kurallar
[CA1005: Genel türlerde aşırı parametrelerden kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Koleksiyonlar genel arabirim uygulamalıdır](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Genel türlerde statik üyeleri belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Üye imzalarında genel türleri iç içe kullanmayın](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Genel olay işleyici örnekleri kullan](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Ayrıca bkz.
[Genel Türler](/dotnet/csharp/programming-guide/generics/index)
