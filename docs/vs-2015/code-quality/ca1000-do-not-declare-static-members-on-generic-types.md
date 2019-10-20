---
title: 'CA1000: genel türlerde statik üye bildirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ef6c98c2808e639570b51d485df90bbdab72c43
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646362"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: Genel türlerde statik üyeleri belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görülebilen genel bir tür, `static` (Visual Basic `Shared`) üyesine sahiptir.

## <a name="rule-description"></a>Kural Tanımı
 Genel bir türün `static` üyesi çağrıldığında, tür için tür bağımsız değişkeni belirtilmelidir. Destek çıkarımı desteklenmeyen genel örnek üyesi çağrıldığında tür bağımsız değişkeni üye için belirlenmelidir. Aşağıdaki çağrılar gösterildiği gibi, bu iki durumda tür bağımsız değişkenini belirtmenin sözdizimi farklı ve kolayca karıştırılır:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

 Genellikle, tür bağımsız değişkeninin üye çağrıldığında belirtilmesi gerekmez, ancak önceki bildirimlerin her ikisi de kaçınılmalıdır. Bu, genel türler için sözdiziminden farklı olmayan genel türlerde üyeleri çağırmaya yönelik bir söz dizimine neden olur. Daha fazla bilgi için bkz. [CA1004: genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için statik üyeyi kaldırın veya bir örnek üyesine değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Anlaşılması kolay ve kullanımı kolay bir sözdiziminde genel türler sağlamak, yeni kitaplıkların benimseme oranını öğrenmek ve artmak için gereken süreyi azaltır.

## <a name="related-rules"></a>İlgili kurallar
 [CA1005: Genel türlerde aşırı parametrelerden kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Koleksiyonlar genel arabirim uygulamalıdır](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Üye imzalarında genel türleri iç içe kullanmayın](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Genel olay işleyici örnekleri kullan](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Uygun yerlerde genel türler kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel Türler](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
