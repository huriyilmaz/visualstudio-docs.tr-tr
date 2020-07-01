---
title: 'CA2104: salt okuma kesilebilir başvuru türlerini bildirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ff42cc2b8543fe8e1cf980a3574ae15922febf9b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521049"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Salt okunur kesilebilir başvuru türleri bildirmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Dışarıdan görünen bir tür, kesilebilir başvuru türü olan dışarıdan görünen bir salt okunur alan içerir.

## <a name="rule-description"></a>Kural Tanımı
 Kesilebilir tür, örnek verileri değiştirilebilen bir türdür. <xref:System.Text.StringBuilder?displayProperty=fullName>Sınıfı kesilebilir başvuru türüne bir örnektir. Bu, sınıfının bir örneğinin değerini değiştirecek üyeleri içerir. Değişmez bir başvuru türü örneği <xref:System.String?displayProperty=fullName> sınıf olur. Örneği oluşturulduktan sonra, değeri hiçbir şekilde değişiklik yapabilir.

 Bir başvuru türü alanında salt okunur değiştirici (C# ' ta[ReadOnly](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) , [ReadOnly](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ve [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) ) (c++ ' da işaretçi), alanın farklı bir başvuru türü örneğiyle değiştirilmesini önler. Ancak, değiştirici alanın örnek verilerinin başvuru türü aracılığıyla değiştirilmesini engellemez.

 Salt okuma dizisi alanları bu kuraldan muaf tutulur, bunun yerine [CA2105: Array alanları](../code-quality/ca2105-array-fields-should-not-be-read-only.md) ihlaline neden olan salt okuma kuralı olmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, salt okunurdur değiştiricisini kaldırın veya bir son değişiklik kabul edilebilir ise, alanı değişmez bir türle değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Alan türü sabit ise, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralın ihlaline neden olan bir alan bildirimi gösterir.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
