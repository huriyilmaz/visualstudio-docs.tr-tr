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
ms.openlocfilehash: 4e485375c12564b5416c79bd3a41dedb1da76dc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533451"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listeler kesin türdedir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı tür uygular, <xref:System.Collections.IList?displayProperty=fullName> ancak aşağıdakilerden biri veya birkaçı için kesin olarak belirlenmiş bir yöntem sağlamaz:

- IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Kural Tanımı
 Bu kural <xref:System.Collections.IList> <xref:System.Object?displayProperty=fullName> , kullanıcıların, arabirim tarafından sunulan işlevleri kullanırken bağımsız değişkenleri türüne dönüştürmeleri gerekmeden, kesin olarak belirlenmiş Üyeler sağlaması için uygulamalar gerektirir. <xref:System.Collections.IList>Arabirim, dizin tarafından erişilebilen nesne koleksiyonları tarafından uygulanır. Bu kural, uygulayan türün, daha <xref:System.Collections.IList> güçlü bir türün örnek koleksiyonunu yönetmek için bunu uyguladığı varsayılır <xref:System.Object> .

 <xref:System.Collections.IList><xref:System.Collections.ICollection?displayProperty=fullName>ve arabirimlerini uygular <xref:System.Collections.IEnumerable?displayProperty=fullName> . Uygulamasını uygularsanız <xref:System.Collections.IList> , için gerekli kesin olarak belirlenmiş üyeleri sağlamanız gerekir <xref:System.Collections.ICollection> . Koleksiyondaki nesneler <xref:System.ValueType?displayProperty=fullName> genişlemişlerse, <xref:System.Collections.IEnumerable.GetEnumerator%2A> kutulamayı neden olan performansın azalmasını önlemek için, için kesin olarak belirlenmiş bir üye sağlamalısınız; koleksiyonun nesneleri bir başvuru türü olduğunda bu gerekli değildir.

 Bu kuralla uyum sağlamak için, ve gibi InterfaceName. InterfaceMemberName biçimindeki adları kullanarak arabirim üyelerini açıkça uygulayın <xref:System.Collections.IList.Add%2A> . Açık arabirim üyeleri, arabirimi tarafından belirtilen veri türlerini kullanır. Arabirim üye adını (gibi) kullanarak türü kesin belirlenmiş üyeleri uygulayın `Add` . Kesin olarak belirlenmiş üyeleri ortak olarak bildirin ve koleksiyon tarafından yönetilen güçlü türde parametreleri ve dönüş değerlerini bildirin. Güçlü türler, ve gibi daha zayıf türler <xref:System.Object> yerine <xref:System.Array> arabirim tarafından bildirilmiştir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, üyeleri açık olarak uygulayın <xref:System.Collections.IList> ve daha önce belirtilen Üyeler için kesin olarak belirlenmiş alternatifler sağlayın. Arabirimi doğru şekilde uygulayan <xref:System.Collections.IList> ve gerekli kesin türü belirtilmiş üyeleri sağlayan kod için aşağıdaki örneğe bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bağlantılı liste gibi yeni bir nesne tabanlı koleksiyon uygularken bu kuraldan bir uyarı göstermez, bu, yeni koleksiyonu genişleten türlerin güçlü türü belirlemesine neden olacak. Bu türler bu kurala uymalıdır ve türü kesin belirlenmiş üyeleri kullanıma sunmalıdır.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, türü `YourType` <xref:System.Collections.CollectionBase?displayProperty=fullName> , kesin olarak belirlenmiş tüm koleksiyonlar olacak şekilde genişletilir. <xref:System.Collections.CollectionBase>Uygulamasının sizin için açık olan arabirimini sağladığını unutmayın <xref:System.Collections.IList> . Bu nedenle, ve için kesin olarak belirlenmiş üyeleri sağlamanız gerekir <xref:System.Collections.IList> <xref:System.Collections.ICollection> .

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1035: ICollection uygulamalarının kesin türde üyeleri vardır](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Numaralandırıcıların kesin türü belirtilmiş olmalıdır](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
