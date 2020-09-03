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
ms.openlocfilehash: e660b1af58dca8d0d69ce2844076382c4a5a1f12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548271"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Numaralandırıcıların kesin türü belirtilmiş olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir tür <xref:System.Collections.IEnumerator?displayProperty=fullName> , özelliğinin kesin türü belirtilmiş bir sürümünü uygular ancak sağlamaz <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> . Aşağıdaki türlerden türetilmiş türler bu kuraldan muaf tutulur:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, <xref:System.Collections.IEnumerator> <xref:System.Collections.IEnumerator.Current%2A> kullanıcıların, arabirim tarafından sunulan işlevleri kullandıklarında döndürülen değeri güçlü türe dönüştürmek için gerekli olmaması için, uygulamaların kesin türü belirtilmiş bir sürümünü de sağlaması gerekir. Bu kural, uygulayan türün, daha <xref:System.Collections.IEnumerator> güçlü olan bir türün örnek koleksiyonunu içerdiğini varsayar <xref:System.Object> .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için Interface özelliğini açıkça uygulayın (olarak bildirin `IEnumerator.Current` ). Özelliğin kesin türü belirtilmiş bir sürümünü ekleyin, olarak `Current` ve türü kesin belirlenmiş bir nesne döndürmesini sağlayabilirsiniz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bir ikili ağaç gibi nesne tabanlı bir koleksiyonla birlikte kullanmak üzere nesne tabanlı bir Numaralandırıcı uyguladığınızda bu kuraldan bir uyarı gizleyin. Yeni koleksiyonu genişleten türler kesin türü belirtilmiş Numaralandırıcı tanımlar ve kesin türü belirtilmiş özelliği sunar.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, türü kesin belirlenmiş bir tür uygulamak için doğru yolu gösterir <xref:System.Collections.IEnumerator> .

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1035: ICollection uygulamalarının kesin türde üyeleri vardır](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Listeler kesin türdedir](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
