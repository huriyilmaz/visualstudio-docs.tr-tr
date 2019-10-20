---
title: 'CA1027: Numaralandırmaları FlagsAttribute ile Işaretle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6f2dc7dcd79fbcaf47a2db3cf49f22f3467a06ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661928"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Numaralandırmaları FlagsAttribute ile işaretle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Genel numaralandırmanın değerleri iki veya numaralandırmadır ve <xref:System.FlagsAttribute?displayProperty=fullName> özniteliği mevcut değil, diğer değerlerin birleşimleridir. Hatalı pozitif sonuçları azaltmak için, bu kural bitişik değerleri olan Numaralandırmalar için bir ihlal raporlamaz.

## <a name="rule-description"></a>Kural Tanımı
 Bir numaralandırma ilişkili adlandırılmış sabitler kümesini tanımlayan değer türüdür. Adlandırılmış sabitleri anlamlı bir şekilde birleştirilebilecek bir numaralandırmaya <xref:System.FlagsAttribute> uygulayın. Örneğin, bir uygulamadaki haftanın günleri, hangi gün kaynakların kullanılabilir olduğunu izleyen bir sabit listesini göz önünde bulundurun. Her bir kaynağın kullanılabilirliği, <xref:System.FlagsAttribute> olan sabit listesi kullanılarak kodlanmışsa, tüm gün bileşimleri temsil edilebilir. Özniteliği olmadan haftanın yalnızca bir günü temsil edilebilir.

 Combinable numaralandırmaları depolayan alanlar için, tek tek numaralandırma değerleri alanındaki bit grupları olarak değerlendirilir. Bu nedenle, bu tür alanlar bazen *bit alanları*olarak adlandırılır. Bir bit alanındaki depolama için numaralandırma değerlerini birleştirmek için, Boole koşullu işleçlerini kullanın. Belirli bir numaralandırma değerinin var olup olmadığını anlamak üzere bir bit alanını test etmek için, Boole mantıksal işleçlerini kullanın. Bir bit alanının birleştirilmiş numaralandırma değerlerini doğru bir şekilde depolaması ve alması için, numaralandırmada tanımlanan her bir değer ikisinin bir üssü olmalıdır. Bu nedenle, Boolean mantıksal işleçler alanda depolanan bireysel numaralandırma değerlerini ayıklayamayacak.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, numaralandırmaya <xref:System.FlagsAttribute> ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Numaralandırma değerlerinin combinable olmasını istemiyorsanız bu kuraldan bir uyarı gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte `DaysEnumNeedsFlags`, <xref:System.FlagsAttribute> kullanma gereksinimlerini karşılayan ancak sahip olmadığı bir numaralandırmadır. @No__t_0 numaralandırması ikinin üsleri olan değerleri içermez, ancak yanlış <xref:System.FlagsAttribute> belirtir. Bu kural CA2217 ihlal ediyor [: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.FlagsAttribute?displayProperty=fullName>
