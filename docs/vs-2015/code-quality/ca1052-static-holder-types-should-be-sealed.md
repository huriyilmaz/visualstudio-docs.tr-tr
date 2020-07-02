---
title: 'CA1052: Statik tutucu türleri Sealed olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 14231cc4dcde5aed5cabc2d8a6172a002c0ba6bf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539756"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Static tutucu türler sealed olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı tür yalnızca statik Üyeler içeriyor ve [Sealed](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) değiştiricisi ile bildirilmemiş.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, türü türetilmiş bir türde geçersiz kılınabilen bir işlev sağlamadığından, yalnızca statik üyeleri içeren bir türün devralınabilmesi için tasarlanmadığını varsayar. Devralınmayan bir tür, `sealed` bir temel tür olarak kullanımını yasaklamak için değiştiriciyle işaretlenmelidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için türü olarak işaretleyin `sealed` . [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]2,0 veya daha önceki bir sürümü hedefliyorsanız, türü olarak işaretlemek daha iyi bir yaklaşımdır `static` . Bu şekilde, sınıfın oluşturulmasını önlemek için özel bir Oluşturucu bildirmek zorunda kalmaktan kaçının.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yalnızca tür devralınacak şekilde tasarlandıysa, bu kuraldan bir uyarı gizleyin. Değiştiricinin yokluğu, `sealed` türün temel tür olarak yararlı olmasını önerir.

## <a name="example-of-a-violation"></a>Ihlalin örneği

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir.

### <a name="code"></a>Kod
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Statik değiştiriciyle onarma

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, türü değiştiriciyle işaretleyerek bu kural ihlalinin nasıl düzeltileceğini gösterir `static` .

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1053: Static tutucu türlerin oluşturucuları olmamalıdır](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
