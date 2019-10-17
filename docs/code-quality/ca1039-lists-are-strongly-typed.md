---
title: 'CA1039: Listelerin türü kesin olarak belirlenmiştir'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87c4e960b313e92efbdf418c1646a81183e75f81
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446651"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listelerin türü kesin olarak belirlenmiştir

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategori|Microsoft. Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Ortak veya korumalı tür <xref:System.Collections.IList?displayProperty=fullName> uygular, ancak aşağıdakilerden biri veya birkaçı için kesin olarak belirlenmiş bir yöntem sağlamaz:

- IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Kural açıklaması

Bu kural, kullanıcıların, arabirim tarafından sunulan işlevleri kullandıklarında, bağımsız değişkenleri <xref:System.Object?displayProperty=fullName> türüne atama gerektirmemesi için, türü kesin belirlenmiş Üyeler sağlamak üzere <xref:System.Collections.IList> uygulamaları gerektirir. @No__t-0 arabirimi, dizin tarafından erişilebilen nesne koleksiyonları tarafından uygulanır. Bu kural <xref:System.Collections.IList> uygulayan türün, <xref:System.Object> ' den daha güçlü bir türdeki örneklerin toplanmasını yönettiğini varsayar.

<xref:System.Collections.IList> <xref:System.Collections.ICollection?displayProperty=fullName> ve <xref:System.Collections.IEnumerable?displayProperty=fullName> arabirimlerini uygular. @No__t-0 ' ı uygularsanız, <xref:System.Collections.ICollection> için gerekli kesin tür olan üyeleri sağlamanız gerekir. Koleksiyondaki nesneler <xref:System.ValueType?displayProperty=fullName> ' ı genişleyorsa, kutulamaktan kaynaklanan performansı azaltmaktan kaçınmak için <xref:System.Collections.IEnumerable.GetEnumerator%2A> için kesin olarak belirlenmiş bir üye sağlamalısınız; koleksiyonun nesneleri bir başvuru türü olduğunda bu gerekli değildir.

Bu kurala uymak için, <xref:System.Collections.IList.Add%2A> gibi InterfaceName. InterfaceMemberName biçimindeki adları kullanarak arabirim üyelerini açıkça uygulayın. Açık arabirim üyeleri, arabirimi tarafından belirtilen veri türlerini kullanır. @No__t-0 gibi arabirim üye adını kullanarak türü kesin belirlenmiş üyeleri uygulayın. Kesin olarak belirlenmiş üyeleri ortak olarak bildirin ve koleksiyon tarafından yönetilen güçlü türde parametreleri ve dönüş değerlerini bildirin. Güçlü türler, arabirim tarafından belirtilen <xref:System.Object> ve <xref:System.Array> gibi daha zayıf türlerin yerini alır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kuralın ihlalini onarmak için, <xref:System.Collections.IList> üyelerini açık bir şekilde uygulayın ve daha önce belirtilen Üyeler için kesin olarak belirlenmiş alternatifler sağlayın. @No__t-0 arabirimini doğru bir şekilde uygulayan ve gerekli türü kesin belirlenmiş üyeleri sağlayan kod için aşağıdaki örneğe bakın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bağlantılı liste gibi yeni bir nesne tabanlı koleksiyon uygularken bu kuraldan bir uyarı göstermez, bu, yeni koleksiyonu genişleten türlerin güçlü türü belirlemesine neden olacak. Bu türler bu kurala uymalıdır ve türü kesin belirlenmiş üyeleri kullanıma sunmalıdır.

## <a name="example"></a>Örnek
Aşağıdaki örnekte, türü kesin belirlenmiş tüm koleksiyonlar olması gerektiği için `YourType` <xref:System.Collections.CollectionBase?displayProperty=fullName> ' i genişletiyor. <xref:System.Collections.CollectionBase>, sizin için <xref:System.Collections.IList> arabiriminin açık uygulamasını sağlar. Bu nedenle, yalnızca <xref:System.Collections.IList> ve <xref:System.Collections.ICollection> için kesin olarak belirlenmiş üyeleri sağlamanız gerekir.

[!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>İlgili kurallar
[CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
