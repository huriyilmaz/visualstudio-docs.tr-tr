---
title: 'CA1044: özellikler salt yazılır olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa2d07337ec48e41a9d8ad82602a387159192f92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668270"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Özellikler salt yazılır olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Public veya protected özelliği bir set erişimcisine sahiptir ancak get erişimcisine sahip değildir.

## <a name="rule-description"></a>Kural Tanımı
 Get erişimcileri bir özelliğe okuma erişimi sağlar ve set erişimcileri yazma erişimi sağlar. Salt okunur özelliğe sahip olmasına karşın kabul edilebilir ve genellikle gereklidir, tasarıma ilişkin yönergeler salt yazılır özellik kullanılmasını engeller. Bunun nedeni, bir kullanıcının bir değer ayarlayabilmesini ve sonra kullanıcının değeri görüntülemesini önlemediğini bir güvenlik sağlamaz. Ayrıca, okuma erişimi olmadan, yararsız olduklarını sınırlayan paylaşılan nesnelerin durumu görüntülenemez.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için özelliğe bir get erişimcisi ekleyin. Alternatif olarak, salt yazılır bir özelliğin davranışı gerekliyse, bu özelliği bir yönteme dönüştürmeyi düşünün.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı bastırmamanızı önemle tavsiye edilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `BadClassWithWriteOnlyProperty`, salt yazılır özelliği olan bir türdür. `GoodClassWithReadWriteProperty` düzeltilen kodu içerir.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
