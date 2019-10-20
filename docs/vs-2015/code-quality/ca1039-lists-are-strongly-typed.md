---
title: 'CA1039: listelerin türü kesin olarak belirlenmiş | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8845fb8bcd08f076ddc3c509a37948cf008e0623
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661808"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listelerin türü kesin olarak belirlenmiştir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı tür <xref:System.Collections.IList?displayProperty=fullName> uygular, ancak aşağıdakilerden biri veya birkaçı için kesin olarak belirlenmiş bir yöntem sağlamaz:

- IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, kullanıcıların, arabirim tarafından sunulan işlevleri kullandıklarında, bağımsız değişkenleri <xref:System.Object?displayProperty=fullName> türüne atama gerektirmemesi için <xref:System.Collections.IList> uygulamaların kesin olarak belirlenmiş Üyeler sağlamasını gerektirir. @No__t_0 arabirimi, dizin tarafından erişilebilen nesne koleksiyonları tarafından uygulanır. Bu kural <xref:System.Collections.IList> uygulayan türün, <xref:System.Object> daha güçlü bir tür örnek koleksiyonunu yönetmek için bunu uyguladığı varsayılır.

 <xref:System.Collections.IList> <xref:System.Collections.ICollection?displayProperty=fullName> ve <xref:System.Collections.IEnumerable?displayProperty=fullName> arabirimlerini uygular. @No__t_0 uygularsanız, <xref:System.Collections.ICollection> için gerekli kesin belirlenmiş üyeleri sağlamanız gerekir. Koleksiyondaki nesneler <xref:System.ValueType?displayProperty=fullName> genişleyorsa, kutulamaktan kaynaklanan performansın azalmasını önlemek için <xref:System.Collections.IEnumerable.GetEnumerator%2A> için kesin olarak belirlenmiş bir üye sağlamalısınız; koleksiyonun nesneleri bir başvuru türü olduğunda bu gerekli değildir.

 Bu kurala uymak için, <xref:System.Collections.IList.Add%2A> gibi InterfaceName. InterfaceMemberName biçimindeki adları kullanarak arabirim üyelerini açıkça uygulayın. Açık arabirim üyeleri, arabirimi tarafından belirtilen veri türlerini kullanır. @No__t_0 gibi arabirim üye adını kullanarak türü kesin belirlenmiş üyeleri uygulayın. Kesin olarak belirlenmiş üyeleri ortak olarak bildirin ve koleksiyon tarafından yönetilen güçlü türde parametreleri ve dönüş değerlerini bildirin. Güçlü türler, arabirim tarafından belirtilen <xref:System.Object> ve <xref:System.Array> gibi daha zayıf türlerin yerini alır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, <xref:System.Collections.IList> üyelerini açık bir şekilde uygulayın ve daha önce belirtilen Üyeler için kesin olarak belirlenmiş alternatifler sağlayın. @No__t_0 arabirimini doğru bir şekilde uygulayan ve gerekli kesin türü belirtilmiş üyeleri sağlayan kod için aşağıdaki örneğe bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bağlantılı liste gibi yeni bir nesne tabanlı koleksiyon uygularken bu kuraldan bir uyarı göstermez, bu, yeni koleksiyonu genişleten türlerin güçlü türü belirlemesine neden olacak. Bu türler bu kurala uymalıdır ve türü kesin belirlenmiş üyeleri kullanıma sunmalıdır.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte tür `YourType`, kesin olarak belirlenmiş tüm koleksiyonlar gibi <xref:System.Collections.CollectionBase?displayProperty=fullName> genişletir. @No__t_0, sizin için <xref:System.Collections.IList> arabiriminin açık uygulamasını sağladığını unutmayın. Bu nedenle, yalnızca <xref:System.Collections.IList> ve <xref:System.Collections.ICollection> için kesin olarak belirlenmiş üyeleri sağlamanız gerekir.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1035: ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Numaralandırıcıların türü kesin olarak belirtilmelidir](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Collections.CollectionBase?displayProperty=fullName><xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
