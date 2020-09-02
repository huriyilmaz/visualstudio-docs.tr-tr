---
title: 'CA1043: Dizin oluşturucular için integral veya dize bağımsız değişkeni kullanın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03d21a824d2d3a9151dad139575f32e3417cbd39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546841"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Dizin oluşturucular için tam sayı veya dize bağımsız değişken kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir tür,,, veya dışında bir dizin türü kullanan ortak veya korumalı bir Dizin Oluşturucu içerir <xref:System.Int32?displayProperty=fullName> <xref:System.Int64?displayProperty=fullName> <xref:System.Object?displayProperty=fullName> <xref:System.String?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 Dizin oluşturucular, diğer bir deyişle dizinli özellikler, dizin için tamsayı veya dize türleri kullanmalıdır. Bu türler genellikle veri yapılarını dizinleme için kullanılır ve kitaplığın kullanılabilirliğini artırır. <xref:System.Object>Bu tür kullanımı, belirli bir tamsayı veya dize türünün tasarım zamanında belirtilebileceği durumlar ile sınırlandırılmalıdır. Tasarım, dizin için başka türler gerektiriyorsa, türün bir mantıksal veri deposunu temsil edip etmediğini yeniden düşünün. Bir mantıksal veri deposunu temsil ediyorsa, bir yöntemi kullanın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, dizini bir tamsayı veya dize türü olarak değiştirin ya da Dizin Oluşturucu yerine bir yöntem kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı yalnızca standart olmayan Dizin Oluşturucu gereksinimini dikkatle ele aldıktan sonra gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, dizin kullanan bir dizin oluşturucuyu gösterir <xref:System.Int32> .

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1023: Dizin oluşturucular çok boyutlu olmamalıdır](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Uygun yerlerde özellikleri kullanın](../code-quality/ca1024-use-properties-where-appropriate.md)
