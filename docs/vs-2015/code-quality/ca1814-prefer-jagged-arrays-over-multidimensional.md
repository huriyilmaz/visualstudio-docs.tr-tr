---
title: 'CA1814: çok boyutlu pürüzlü dizileri tercih etme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f0ac183321bd2a3070b1f1ddc54402b74c8fb823
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668411"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Basit dizileri çok boyutlu dizilere tercih edin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir üye çok boyutlu bir dizi olarak bildirilmiştir.

## <a name="rule-description"></a>Kural Tanımı
 Basit bir dizi, öğeleri dizi olan bir dizidir. Öğeleri olan diziler bazı veri kümeler için daha az harcanmış önde gelen farklı boyutlarda olabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, çok boyutlu diziyi pürüzlü bir dizi olarak değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Çok boyutlu dizi alanı atık olarak içermiyorsa, bu kuraldan bir uyarı gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, pürüzlü ve çok boyutlu diziler için bildirimleri gösterir.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]
