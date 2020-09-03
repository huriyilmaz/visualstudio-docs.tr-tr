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
ms.openlocfilehash: a0c832b7eb4a94506c5e15dfa5858bb9f6753912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546269"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: NaN için doğru test edin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir ifade, veya ile karşılaştırarak bir değeri sınar <xref:System.Single.NaN?displayProperty=fullName> <xref:System.Double.NaN?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Double.NaN?displayProperty=fullName>, bir sayı değil, bir aritmetik işlem tanımsız olduğunda sonuçları gösterir. Bir değer ile <xref:System.Double.NaN?displayProperty=fullName> her zaman geri dönüş arasındaki eşitliği test eden herhangi bir ifade `false` . Bir değer ile her zaman arasında eşitsizlik test eden herhangi bir ifade <xref:System.Double.NaN?displayProperty=fullName> `true` .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak ve değerin temsil edilip edilmeyeceğini doğru bir şekilde tespit etmek için <xref:System.Double.NaN?displayProperty=fullName> , <xref:System.Single.IsNaN%2A?displayProperty=fullName> değerini kullanın veya <xref:System.Double.IsNaN%2A?displayProperty=fullName> test edin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir değeri yanlış test eden iki <xref:System.Double.NaN?displayProperty=fullName> ifadeyi ve <xref:System.Double.IsNaN%2A?displayProperty=fullName> değeri sınamak için doğru şekilde kullanılan bir ifadeyi gösterir.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
