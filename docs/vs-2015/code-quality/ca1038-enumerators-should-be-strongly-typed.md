---
title: 'CA1038: Numaralandırıcılar kesin belirlenmiş olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3a08f4987fe57a94aaee8f3df6129782fd6448c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661759"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir tür <xref:System.Collections.IEnumerator?displayProperty=fullName> uygular, ancak <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> özelliğinin kesin türü belirtilmiş bir sürümünü sağlamaz. Aşağıdaki türlerden türetilmiş türler bu kuraldan muaf tutulur:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, kullanıcıların, arabirim tarafından sunulan işlevleri kullandıklarında döndürülen değeri güçlü türe dönüştürmek için gerekli olmaması için <xref:System.Collections.IEnumerator.Current%2A> özelliğinin kesin belirlenmiş bir sürümünü sağlaması için <xref:System.Collections.IEnumerator> uygulamalar gerektirir. Bu kural <xref:System.Collections.IEnumerator> uygulayan türün <xref:System.Object> ' den daha güçlü bir tür örnek koleksiyonu içerdiğini varsayar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için Interface özelliğini açıkça uygulayın (`IEnumerator.Current` olarak bildirin). Özelliğinin, `Current` olarak bildirildiği ve kesin tür belirtilmiş bir nesne döndürmesini sağlamak için, özelliğin kesin türü belirtilmiş bir sürümünü ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bir ikili ağaç gibi nesne tabanlı bir koleksiyonla birlikte kullanmak üzere nesne tabanlı bir Numaralandırıcı uyguladığınızda bu kuraldan bir uyarı gizleyin. Yeni koleksiyonu genişleten türler kesin türü belirtilmiş Numaralandırıcı tanımlar ve kesin türü belirtilmiş özelliği sunar.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, türü kesin belirlenmiş <xref:System.Collections.IEnumerator> türünü uygulamak için doğru yolu gösterir.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Listelerin türü kesin olarak belirlenmiştir](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Collections.IEnumerator?displayProperty=fullName><xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
