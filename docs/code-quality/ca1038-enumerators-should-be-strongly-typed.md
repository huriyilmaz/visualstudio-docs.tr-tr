---
title: 'CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22d3ebbbce2a2495e32e55dca85f9db35b09a06d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449249"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategori|Microsoft. Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Ortak veya korumalı bir tür @no__t uygular, ancak <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> özelliğinin kesin türü belirtilmiş bir sürümünü sağlamaz. Aşağıdaki türlerden türetilmiş türler bu kuraldan muaf tutulur:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Kural açıklaması
Bu kural <xref:System.Collections.IEnumerator> uygulamalarının, bir <xref:System.Collections.IEnumerator.Current%2A> özelliğinin kesin türü belirtilmiş bir sürümünü sağlaması gerekir, böylece kullanıcıların, arabirim tarafından sunulan işlevleri kullandıklarında döndürülen değeri güçlü türe saçılması gerekmez. Bu kural <xref:System.Collections.IEnumerator> uygulayan türün <xref:System.Object> ' den daha güçlü bir tür örnek koleksiyonu içerdiğini varsayar.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için Interface özelliğini açıkça uygulayın (`IEnumerator.Current` olarak bildirin). Özelliğinin, `Current` olarak bildirildiği ve kesin tür belirtilmiş bir nesne döndürmesini sağlamak için, özelliğin kesin türü belirtilmiş bir sürümünü ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bir ikili ağaç gibi nesne tabanlı bir koleksiyonla birlikte kullanmak üzere nesne tabanlı bir Numaralandırıcı uyguladığınızda bu kuraldan bir uyarı gizleyin. Yeni koleksiyonu genişleten türler kesin türü belirtilmiş Numaralandırıcı tanımlar ve kesin türü belirtilmiş özelliği sunar.

## <a name="example"></a>Örnek
Aşağıdaki örnek, türü kesin belirlenmiş <xref:System.Collections.IEnumerator> türünü uygulamak için doğru yolu gösterir.

[!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>İlgili kurallar
[CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1039: Listelerin türü kesin olarak belirlenmiştir](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
