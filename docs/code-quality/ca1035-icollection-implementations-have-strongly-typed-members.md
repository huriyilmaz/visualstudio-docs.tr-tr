---
title: 'CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0eb96957048a91685049349bf0c796c4eebab196
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446661"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategori|Microsoft. Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Ortak veya korumalı bir tür @no__t uygular, ancak <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> için kesin olarak belirlenmiş bir yöntem sağlamaz. @No__t-0 ' nın kesin türü belirtilmiş sürümü iki parametreyi kabul etmeli ve ilk parametresi olarak bir <xref:System.Array?displayProperty=fullName> veya <xref:System.Object?displayProperty=fullName> dizisine sahip olamaz.

## <a name="rule-description"></a>Kural açıklaması
Bu kural, kullanıcıların arabirim tarafından sunulan işlevleri kullandıklarında, bağımsız değişkenleri <xref:System.Object> türüne dönüştürmeleri gerekmeden, türü kesin belirlenmiş Üyeler sağlamak için <xref:System.Collections.ICollection> uygulamaları gerektirir. Bu kural <xref:System.Collections.ICollection> uygulayan türün, <xref:System.Object> ' den daha güçlü bir türün örnek koleksiyonunu yönetmesini kabul eder.

 <xref:System.Collections.ICollection> <xref:System.Collections.IEnumerable?displayProperty=fullName> arabirimini uygular. Koleksiyondaki nesneler <xref:System.ValueType?displayProperty=fullName> ' ı genişleyorsa, kutulamaktan kaynaklanan performansın azalmasını önlemek için <xref:System.Collections.IEnumerable.GetEnumerator%2A> için kesin olarak belirlenmiş bir üye sağlamalısınız. Koleksiyonun nesneleri bir başvuru türü olduğunda bu gerekli değildir.

Bir arabirim üyesinin türü kesin belirlenmiş bir sürümünü uygulamak için, <xref:System.Collections.ICollection.CopyTo%2A> gibi `InterfaceName.InterfaceMemberName` biçimindeki adları kullanarak arabirim üyelerini açıkça uygulayın. Açık arabirim üyeleri, arabirimi tarafından belirtilen veri türlerini kullanır. @No__t-0 gibi arabirim üye adını kullanarak türü kesin belirlenmiş üyeleri uygulayın. Kesin olarak belirlenmiş üyeleri ortak olarak bildirin ve koleksiyon tarafından yönetilen güçlü türde parametreleri ve dönüş değerlerini bildirin. Güçlü türler, arabirim tarafından belirtilen <xref:System.Object> ve <xref:System.Array> gibi daha zayıf türlerin yerini alır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için arabirim üyesini açıkça uygulayın (<xref:System.Collections.ICollection.CopyTo%2A> olarak bildirin). @No__t-0 olarak belirtilen public türü kesin belirlenmiş üyeyi ekleyin ve ilk parametresi olarak türü kesin belirlenmiş bir diziyi alın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Yeni koleksiyonu genişleten türlerin güçlü türü belirlemesi için bir ikili ağaç gibi yeni bir nesne tabanlı koleksiyon uygularsanız, bu kuraldan bir uyarı gizleyin. Bu türler bu kurala uymalıdır ve türü kesin belirlenmiş üyeleri kullanıma sunmalıdır.

## <a name="example"></a>Örnek
Aşağıdaki örnek <xref:System.Collections.ICollection> ' i uygulamak için doğru yolu gösterir.

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>İlgili kurallar
[CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039: Listelerin türü kesin olarak belirlenmiştir](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
