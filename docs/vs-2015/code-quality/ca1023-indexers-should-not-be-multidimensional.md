---
title: 'CA1023: Dizin oluşturucular çok boyutlu olmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30eee67d54e4fc3c73b265240fff82b0729e1cfc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546659"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Dizin oluşturucular çok boyutlu olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir tür, birden fazla dizin kullanan ortak veya korumalı bir Dizin Oluşturucu içerir.

## <a name="rule-description"></a>Kural Tanımı
 Dizin oluşturucular, yani dizinli özellikler tek bir dizin kullanmalıdır. Çok boyutlu Dizin oluşturucular kitaplığın kullanılabilirliğini önemli ölçüde azaltabilir. Tasarımda birden çok dizin gerekiyorsa, türün bir mantıksal veri deposunu temsil edip etmediğini yeniden düşünün. Aksi takdirde, bir yöntemi kullanın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, tasarımı bir tek tamsayı veya dize dizini kullanacak şekilde değiştirin ya da Dizin Oluşturucu yerine bir yöntem kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı yalnızca standart olmayan Dizin Oluşturucu gereksinimini dikkatle ele aldıktan sonra gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `DayOfWeek03` kuralını ihlal eden çok boyutlu bir Dizin Oluşturucu ile bir türü gösterir. Dizin Oluşturucu bir dönüştürme türü olarak görülebilir ve bu nedenle bir yöntem olarak daha uygun şekilde kullanıma sunulabilir. Türü, kuralı karşılamak için ' de yeniden tasarlanmıştır `RedesignedDayOfWeek03` .

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1043: Dizin oluşturucular için tam sayı veya dize bağımsız değişken kullanın](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Uygun yerlerde özellikleri kullanın](../code-quality/ca1024-use-properties-where-appropriate.md)
