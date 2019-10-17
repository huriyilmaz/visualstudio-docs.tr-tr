---
title: 'CA1023: Dizin oluşturucular çok boyutlu olmamalıdır'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9b9488d3f28567e3e39f86355b353f6d1d9d84d9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441426"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Dizin oluşturucular çok boyutlu olmamalıdır

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Kategori|Microsoft. Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Ortak veya korumalı bir tür, birden fazla dizin kullanan ortak veya korumalı bir Dizin Oluşturucu içerir.

## <a name="rule-description"></a>Kural açıklaması
Dizin oluşturucular, yani dizinli özellikler tek bir dizin kullanmalıdır. Çok boyutlu Dizin oluşturucular kitaplığın kullanılabilirliğini önemli ölçüde azaltabilir. Tasarımda birden çok dizin gerekiyorsa, türün bir mantıksal veri deposunu temsil edip etmediğini yeniden düşünün. Aksi takdirde, bir yöntemi kullanın.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için, tasarımı bir tek tamsayı veya dize dizini kullanacak şekilde değiştirin ya da Dizin Oluşturucu yerine bir yöntem kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan bir uyarıyı yalnızca standart olmayan Dizin Oluşturucu gereksinimini dikkatle ele aldıktan sonra gizleyin.

## <a name="example"></a>Örnek
Aşağıdaki örnek, kuralı ihlal eden çok boyutlu bir Dizin Oluşturucu ile `DayOfWeek03` türünü gösterir. Dizin Oluşturucu bir dönüştürme türü olarak görülebilir ve bu nedenle bir yöntem olarak daha uygun şekilde kullanıma sunulabilir. Tür, kuralı karşılamak için `RedesignedDayOfWeek03` ' da yeniden tasarlanmıştır.

[!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
[!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
[!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>İlgili kurallar
[CA1043: Dizin oluşturucular için tamsayı veya dize bağımsız değişkeni kullanın](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

[CA1024: Uygun yerlerde özellikler kullanın](../code-quality/ca1024-use-properties-where-appropriate.md)
