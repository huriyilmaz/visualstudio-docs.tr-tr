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
ms.openlocfilehash: 2e679fb3cc62ba80cfb7b56dfd7fa6590375565e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546620"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection uygulamalarının kesin türde üyeleri vardır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir tür uygular <xref:System.Collections.ICollection?displayProperty=fullName> , ancak için kesin olarak belirlenmiş bir yöntem sağlamaz <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> . Türü kesin belirlenmiş olan sürümü <xref:System.Collections.ICollection.CopyTo%2A> iki parametreyi kabul etmelidir ve <xref:System.Array?displayProperty=fullName> ilk parametresi olarak bir veya dizisine sahip olamaz <xref:System.Object?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 Bu kural <xref:System.Collections.ICollection> <xref:System.Object> , kullanıcıların, arabirim tarafından sunulan işlevleri kullanırken bağımsız değişkenleri türüne dönüştürmeleri gerekmeden, kesin olarak belirlenmiş Üyeler sağlaması için uygulamalar gerektirir. Bu kural, uygulayan türün, daha <xref:System.Collections.ICollection> güçlü bir tür örnek koleksiyonunu yönetmek için bunu uyguladığı varsayılır <xref:System.Object> .

 <xref:System.Collections.ICollection>arabirimini uygular <xref:System.Collections.IEnumerable?displayProperty=fullName> . Koleksiyondaki nesneler <xref:System.ValueType?displayProperty=fullName> genişlemişlerse, <xref:System.Collections.IEnumerable.GetEnumerator%2A> kutulamaktan kaynaklanan performansı azaltmaktan kaçınmak için, için kesin olarak belirlenmiş bir üye sağlamalısınız. Koleksiyonun nesneleri bir başvuru türü olduğunda bu gerekli değildir.

 Bir arabirim üyesinin kesin türü belirtilmiş bir sürümünü uygulamak için, formdaki adları kullanarak arabirim üyelerini açıkça uygulayın `InterfaceName.InterfaceMemberName` <xref:System.Collections.ICollection.CopyTo%2A> . Açık arabirim üyeleri, arabirimi tarafından belirtilen veri türlerini kullanır. Arabirim üye adını (gibi) kullanarak türü kesin belirlenmiş üyeleri uygulayın <xref:System.Collections.ICollection.CopyTo%2A> . Kesin olarak belirlenmiş üyeleri ortak olarak bildirin ve koleksiyon tarafından yönetilen güçlü türde parametreleri ve dönüş değerlerini bildirin. Güçlü türler, ve gibi daha zayıf türler <xref:System.Object> yerine <xref:System.Array> arabirim tarafından bildirilmiştir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için arabirim üyesini açıkça uygulayın (olarak bildirin <xref:System.Collections.ICollection.CopyTo%2A> ). Olarak belirtilen public türü kesin belirlenmiş üyeyi ekleyin `CopyTo` ve ilk parametresi olarak türü kesin belirlenmiş bir diziyi alır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yeni koleksiyonu genişleten türlerin güçlü türü belirlemesi için bir ikili ağaç gibi yeni bir nesne tabanlı koleksiyon uygularsanız, bu kuraldan bir uyarı gizleyin. Bu türler bu kurala uymalıdır ve türü kesin belirlenmiş üyeleri kullanıma sunmalıdır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, uygulamak için doğru yolu gösterir <xref:System.Collections.ICollection> .

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1038: Numaralandırıcıların kesin türü belirtilmiş olmalıdır](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Listeler kesin türdedir](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
