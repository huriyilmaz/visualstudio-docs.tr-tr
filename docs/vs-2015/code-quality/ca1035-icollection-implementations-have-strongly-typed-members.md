---
title: 'CA1035: ICollection uygulamalarında kesin olarak belirlenmiş Üyeler var | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d112e2dfb704a785db6bbc5becd2b369d90605b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661840"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir tür <xref:System.Collections.ICollection?displayProperty=fullName> uygular, ancak <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> için türü kesin belirlenmiş bir yöntem sağlamaz. @No__t_0 türü kesin belirlenmiş olan sürümü iki parametre kabul etmelidir ve ilk parametresi olarak bir <xref:System.Array?displayProperty=fullName> veya <xref:System.Object?displayProperty=fullName> dizisine sahip olamaz.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, kullanıcıların arabirim tarafından sunulan işlevleri kullandıklarında, bağımsız değişkenleri <xref:System.Object> türüne dönüştürmeleri gerekmeden, türü kesin belirlenmiş Üyeler sağlamak için <xref:System.Collections.ICollection> uygulamaları gerektirir. Bu kural <xref:System.Collections.ICollection> uygulayan türün, <xref:System.Object> ' den daha güçlü bir türün örnek koleksiyonunu yönetmesini kabul eder.

 <xref:System.Collections.ICollection> <xref:System.Collections.IEnumerable?displayProperty=fullName> arabirimini uygular. Koleksiyondaki nesneler <xref:System.ValueType?displayProperty=fullName> genişleyorsa, kutulamaktan kaynaklanan performansı azaltmaktan kaçınmak için, <xref:System.Collections.IEnumerable.GetEnumerator%2A> için kesin olarak belirlenmiş bir üye sağlamalısınız. Koleksiyonun nesneleri bir başvuru türü olduğunda bu gerekli değildir.

 Bir arabirim üyesinin türü kesin belirlenmiş bir sürümünü uygulamak için, <xref:System.Collections.ICollection.CopyTo%2A> gibi `InterfaceName.InterfaceMemberName` biçimindeki adları kullanarak arabirim üyelerini açıkça uygulayın. Açık arabirim üyeleri, arabirimi tarafından belirtilen veri türlerini kullanır. @No__t_0 gibi arabirim üye adını kullanarak türü kesin belirlenmiş üyeleri uygulayın. Kesin olarak belirlenmiş üyeleri ortak olarak bildirin ve koleksiyon tarafından yönetilen güçlü türde parametreleri ve dönüş değerlerini bildirin. Güçlü türler, arabirim tarafından belirtilen <xref:System.Object> ve <xref:System.Array> gibi daha zayıf türlerin yerini alır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için arabirim üyesini açıkça uygulayın (<xref:System.Collections.ICollection.CopyTo%2A> olarak bildirin). @No__t_0 olarak belirtilen herkese açık türü belirlenmiş üyeyi ekleyin ve ilk parametresi olarak türü kesin belirlenmiş bir diziyi alın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yeni koleksiyonu genişleten türlerin güçlü türü belirlemesi için bir ikili ağaç gibi yeni bir nesne tabanlı koleksiyon uygularsanız, bu kuraldan bir uyarı gizleyin. Bu türler bu kurala uymalıdır ve türü kesin belirlenmiş üyeleri kullanıma sunmalıdır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek <xref:System.Collections.ICollection> ' i uygulamak için doğru yolu gösterir.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Listelerin türü kesin olarak belirlenmiştir](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Array?displayProperty=fullName><xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
