---
title: 'CA2242: NaN için doğru test edin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8433ac081a45e3dbab80ffcd6f96e6d1db914337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672017"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: NaN için doğru sınayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir ifade değeri <xref:System.Single.NaN?displayProperty=fullName> veya <xref:System.Double.NaN?displayProperty=fullName> ile sınar.

## <a name="rule-description"></a>Kural Tanımı
 sayı değil, bir aritmetik işlem tanımsız olduğunda sonuçları temsil eder <xref:System.Double.NaN?displayProperty=fullName>. Bir değer ve <xref:System.Double.NaN?displayProperty=fullName> arasındaki eşitliği test eden herhangi bir ifade her zaman `false` döndürür. Bir değer ve <xref:System.Double.NaN?displayProperty=fullName> arasındaki eşitsizlik test eden herhangi bir ifade her zaman `true` döndürür.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak ve değerin <xref:System.Double.NaN?displayProperty=fullName> temsil edip etmediğini doğru şekilde belirlemesi için, değeri sınamak üzere <xref:System.Single.IsNaN%2A?displayProperty=fullName> veya <xref:System.Double.IsNaN%2A?displayProperty=fullName> kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.Double.NaN?displayProperty=fullName> karşı bir değeri yanlış test eden iki ifadeyi ve değeri sınamak için <xref:System.Double.IsNaN%2A?displayProperty=fullName> doğru şekilde kullanılan bir ifadeyi gösterir.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
