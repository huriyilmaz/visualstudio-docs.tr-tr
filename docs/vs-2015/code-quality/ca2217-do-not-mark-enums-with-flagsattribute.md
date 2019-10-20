---
title: 'CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 73f94c45568a55cc098dd223deca9dab404f44ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651642"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Dışarıdan görünür bir numaralandırma, <xref:System.FlagsAttribute> ile işaretlenir ve Numaralandırmadaki veya diğer tanımlı değerlerin bir birleşimi olmayan bir ya da daha fazla değere sahiptir.

## <a name="rule-description"></a>Kural Tanımı
 Sabit listesi yalnızca numaralandırmada tanımlanan her bir değer iki veya bir tanımlı Değerler birleşimi olduğunda <xref:System.FlagsAttribute> bulunmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, Numaralandırmadaki <xref:System.FlagsAttribute> kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, 2 ' nin üssü olan 3 değerini, ya da tanımlı değerlerden herhangi birinin birleşimini içeren bir numaralandırma, renk gösterir. Renk numaralandırması <xref:System.FlagsAttribute> olarak işaretlenmemelidir.

 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cpp/FxCop.Usage.EnumNoFlags.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cs/FxCop.Usage.EnumNoFlags.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/vb/FxCop.Usage.EnumNoFlags.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnekte System. FlagsAttribute ile işaretlenme gereksinimlerini karşılayan bir numaralandırma, günler gösterilmektedir.

 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cpp/FxCop.Usage.EnumNoFlags2.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cs/FxCop.Usage.EnumNoFlags2.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/vb/FxCop.Usage.EnumNoFlags2.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.FlagsAttribute?displayProperty=fullName>
