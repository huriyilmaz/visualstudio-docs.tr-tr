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
ms.openlocfilehash: 774279dd05bd14c34df7f1d450f00599812d6a5b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544514"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Sabit listelerini FlagsAttribute ile işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Ortak numaralandırmanın değerleri iki veya sabit listesi içinde tanımlanan diğer değerlerin birleşimleridir ve <xref:System.FlagsAttribute?displayProperty=fullName> öznitelik mevcut değildir. Hatalı pozitif sonuçları azaltmak için, bu kural bitişik değerleri olan Numaralandırmalar için bir ihlal raporlamaz.

## <a name="rule-description"></a>Kural Tanımı
 Bir numaralandırma ilişkili adlandırılmış sabitler kümesini tanımlayan değer türüdür. <xref:System.FlagsAttribute>Adlandırılmış sabitleri anlamlı bir şekilde birleştirilebilecek bir numaralandırmaya Uygula. Örneğin, bir uygulamadaki haftanın günleri, hangi gün kaynakların kullanılabilir olduğunu izleyen bir sabit listesini göz önünde bulundurun. Her bir kaynağın kullanılabilirliği, mevcut olan numaralandırma kullanılarak kodlanmışsa <xref:System.FlagsAttribute> , tüm gün bileşimleri temsil edilebilir. Özniteliği olmadan haftanın yalnızca bir günü temsil edilebilir.

 Combinable numaralandırmaları depolayan alanlar için, tek tek numaralandırma değerleri alanındaki bit grupları olarak değerlendirilir. Bu nedenle, bu tür alanlar bazen *bit alanları*olarak adlandırılır. Bir bit alanındaki depolama için numaralandırma değerlerini birleştirmek için, Boole koşullu işleçlerini kullanın. Belirli bir numaralandırma değerinin var olup olmadığını anlamak üzere bir bit alanını test etmek için, Boole mantıksal işleçlerini kullanın. Bir bit alanının birleştirilmiş numaralandırma değerlerini doğru bir şekilde depolaması ve alması için, numaralandırmada tanımlanan her bir değer ikisinin bir üssü olmalıdır. Bu nedenle, Boolean mantıksal işleçler alanda depolanan bireysel numaralandırma değerlerini ayıklayamayacak.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, numaralandırmaya ekleyin <xref:System.FlagsAttribute> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Numaralandırma değerlerinin combinable olmasını istemiyorsanız bu kuraldan bir uyarı gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `DaysEnumNeedsFlags` kullanma gereksinimlerini karşılayan ancak içermeyen bir numaralandırmadır <xref:System.FlagsAttribute> . `ColorEnumShouldNotHaveFlag`Sabit listesinin iki üsleri olan değerleri yoktur, ancak yanlış şekilde belirtir <xref:System.FlagsAttribute> . Bu kural CA2217 ihlal ediyor [: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2217: Sabit listelerini FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.FlagsAttribute?displayProperty=fullName>
