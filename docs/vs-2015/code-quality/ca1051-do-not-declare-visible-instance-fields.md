---
title: 'CA1051: görünür örnek alanlarını bildirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 41332ab7d729f7b2187ccace6b05fe2d17763a0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672514"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Görünür örnek alanlarını bildirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir türün dışarıdan görünür bir örnek alanı vardır.

## <a name="rule-description"></a>Kural Tanımı
 Bir alanın birincil kullanım alanının uygulama ayrıntısı olması gerekir. Alanlar `private` veya `internal` olmalı ve özellikler kullanılarak gösterilmelidir. Bir alana erişmek için bir özelliğe erişmek kolaydır ve bir özelliğin erişimcilerinin kodu, önemli değişikliklere bildirmeden tür özellikleri genişleyebilir. Yalnızca bir özel veya iç alanın değerini döndüren Özellikler bir alana erişim için en iyi duruma getirilir; çok az performans kazancı, Özellikler üzerinde dışarıdan görünür alanların kullanımıyla ilişkilendirilmiştir.

 Dışarıdan görünür, `public`, `protected` ve `protected internal` (`Public`, `Protected` ve `Protected Friend`) erişilebilirlik düzeylerinde anlamına gelir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, alanı `private` veya `internal` yapın ve dışarıdan görünür bir özellik kullanarak sunun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Dışarıdan görünen alanlar, özelliklerde kullanılamayan avantajlar sağlamaz. Ayrıca, ortak alanlar [bağlantı taleplerine](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)karşı korunamaz. Bkz. [CA2112: güvenli türler alanları kullanıma sunmamalıdır](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü (`BadPublicInstanceFields`) gösterir. `GoodPublicInstanceFields` düzeltilen kodu gösterir.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2112: Güvenli türler alanları açığa çıkarmamalıdır](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Bağlantı talepleri](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
