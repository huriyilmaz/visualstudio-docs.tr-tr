---
title: 'CA1010: Koleksiyonlar genel arabirimi uygulamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 20238a844b45221207ca952d90d172ac720136ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655247"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Koleksiyonlar genel arabirim uygulamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir tür <xref:System.Collections.IEnumerable?displayProperty=fullName> arabirimini uygular, ancak <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> arabirimini uygulamaz ve içeren derleme [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] hedefler. Bu kural <xref:System.Collections.IDictionary?displayProperty=fullName> uygulayan türleri yoksayar.

## <a name="rule-description"></a>Kural Tanımı
 Bir koleksiyon kullanılabilirliğini genişletmek için genel koleksiyon arabirimlerinden birini uygulayın. Daha sonra koleksiyon, aşağıdakiler gibi genel koleksiyon türlerini doldurmak için kullanılabilir:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için aşağıdaki genel koleksiyon arabirimlerinden birini uygulayın:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir; Ancak, koleksiyon daha sınırlı bir kullanıma sahip olacaktır.

## <a name="example-violation"></a>Örnek Ihlali

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, bu kuralı ihlal eden genel olmayan `CollectionBase` sınıfından türetilen bir sınıfı (başvuru türü) gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>Açıklamalar
 Bu ihlalin ihlalini onarmak için, genel arabirimleri uygulamanız veya temel sınıfı, `Collection<T>` sınıfı gibi genel ve genel olmayan arabirimleri önceden uygulayan bir türe değiştirmelisiniz.

## <a name="fix-by-base-class-change"></a>Temel sınıf değişikliğine göre düzeltir

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, koleksiyonun temel sınıfını genel olmayan `CollectionBase` sınıfından genel `Collection<T>` ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Collection(Of T)`) sınıfında değiştirerek ihlalin düzeltir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>Açıklamalar
 Zaten yayınlanmış bir sınıfın temel sınıfını değiştirmek, mevcut tüketicilerle bir son değişiklik olarak kabul edilir.

## <a name="fix-by-interface-implementation"></a>Arabirim uygulamasına göre onarma

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, bu genel arabirimleri uygulayarak ihlali düzeltir: `IEnumerable<T>`, `ICollection<T>` ve `IList<T>` (`ICollection(Of T)` `IEnumerable(Of T)`, `IList(Of T)` ve [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1005: Genel türlerde aşırı parametrelerden kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Genel türlerde statik üyeleri belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Üye imzalarında genel türleri iç içe kullanmayın](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Genel olay işleyici örnekleri kullan](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Uygun yerlerde genel türler kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel Türler](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
