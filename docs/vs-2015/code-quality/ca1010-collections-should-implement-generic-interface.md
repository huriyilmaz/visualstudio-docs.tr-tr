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
ms.openlocfilehash: b141d755c717ad6650d2a49c98c2b26547066b7a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545528"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Koleksiyonlar genel arabirimi uygulamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Dışarıdan görünen bir tür arabirimini uygular <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> , ancak arabirimini uygulamaz ve kapsayan bütünleştirilmiş kod hedefler [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] . Bu kural, uygulayan türleri yoksayar <xref:System.Collections.IDictionary?displayProperty=fullName> .

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
 Aşağıdaki örnek, bu kuralı ihlal eden genel olmayan sınıftan türetilen bir sınıfı (başvuru türü) gösterir `CollectionBase` .

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>Yorumlar
 Bu ihlalin ihlalini onarmak için, genel arabirimleri uygulamanız veya temel sınıfı, sınıf gibi genel ve genel olmayan arabirimleri önceden uygulayan bir türe değiştirmelisiniz `Collection<T>` .

## <a name="fix-by-base-class-change"></a>Temel sınıf değişikliğine göre düzeltir

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, koleksiyonun Taban sınıfını genel olmayan `CollectionBase` sınıftan genel `Collection<T>` ( `Collection(Of T)` ın [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) sınıfına değiştirerek ihlalini düzeltir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>Yorumlar
 Zaten yayınlanmış bir sınıfın temel sınıfını değiştirmek, mevcut tüketicilerle bir son değişiklik olarak kabul edilir.

## <a name="fix-by-interface-implementation"></a>Arabirim uygulamasına göre onarma

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, bu genel arabirimleri uygulayarak ihlalini düzeltir: `IEnumerable<T>` , `ICollection<T>` , ve `IList<T>` ( `IEnumerable(Of T)` , `ICollection(Of T)` , ve `IList(Of T)` içinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1005: Genel türlerde aşırı parametre kullanmaktan kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Genel türlerde statik üyeler belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Üye imzalarında genel türleri iç içe kullanma](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Genel olay işleyicisi örnekleri kullan](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Uygun yerlerde genel türleri kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel Türler](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
