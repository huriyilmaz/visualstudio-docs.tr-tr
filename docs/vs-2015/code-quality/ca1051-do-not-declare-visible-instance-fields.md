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
ms.openlocfilehash: 076ce3858774d44e2d6c4c25205ced74b7a41bf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539769"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Görünür örnek alanlarını bildirmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Dışarıdan görünen bir türün dışarıdan görünür bir örnek alanı vardır.

## <a name="rule-description"></a>Kural Tanımı
 Bir alanın birincil kullanım alanının uygulama ayrıntısı olması gerekir. Alanlar `private` `internal` , veya özellikleri kullanılarak sunulmalıdır. Bir alana erişmek için bir özelliğe erişmek kolaydır ve bir özelliğin erişimcilerinin kodu, önemli değişikliklere bildirmeden tür özellikleri genişleyebilir. Yalnızca bir özel veya iç alanın değerini döndüren Özellikler bir alana erişim için en iyi duruma getirilir; çok az performans kazancı, Özellikler üzerinde dışarıdan görünür alanların kullanımıyla ilişkilendirilmiştir.

 Dışarıdan görünür,, `public` , `protected` ve `protected internal` ( `Public` `Protected` `Protected Friend` Visual Basic) erişilebilirlik düzeylerine başvurur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, alanı oluşturun `private` veya `internal` dışarıdan görünebilir bir özellik kullanarak sunun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Dışarıdan görünen alanlar, özelliklerde kullanılamayan avantajlar sağlamaz. Ayrıca, ortak alanlar [bağlantı taleplerine](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)karşı korunamaz. Bkz. [CA2112: güvenli türler alanları kullanıma sunmamalıdır](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `BadPublicInstanceFields` Bu kuralı ihlal eden bir türü () gösterir. `GoodPublicInstanceFields` düzeltilen kodu gösterir.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2112: Güvenli türler alanları açığa çıkarmamalıdır](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Bağlantı Talepleri](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
