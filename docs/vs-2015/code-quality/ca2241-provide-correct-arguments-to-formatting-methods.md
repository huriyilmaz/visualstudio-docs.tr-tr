---
title: 'CA2241: biçimlendirme yöntemlerine doğru bağımsız değişkenleri sağlayın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 112065b2a8b9a88241ce62dda7b32a2f2c22fc75
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672022"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Biçimlendirme yöntemlerine doğru bağımsız değişkenleri sağlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 @No__t_1, <xref:System.Console.Write%2A> veya <xref:System.String.Format%2A?displayProperty=fullName> gibi bir yönteme geçirilen `format` dize bağımsız değişkeni, her bir nesne bağımsız değişkenine karşılık gelen bir biçim öğesi içermez ya da tam tersi.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0, <xref:System.Console.Write%2A> ve <xref:System.String.Format%2A> gibi yöntemlere yönelik bağımsız değişkenler, birkaç <xref:System.Object?displayProperty=fullName> örneği tarafından izlenen bir biçim dizesinden oluşur. Biçim dizesi, {index [, hizalama] [: formatString]} biçiminde metin ve katıştırılmış biçim öğelerinden oluşur. ' index ', hangi nesnelerden biçimlendirileceğini gösteren sıfır tabanlı bir tamsayıdır. Bir nesne, biçim dizesinde karşılık gelen bir dizin içermiyorsa, nesne yok sayılır. ' İndex ' tarafından belirtilen nesne yoksa, çalışma zamanında bir <xref:System.FormatException?displayProperty=fullName> oluşturulur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için her bir nesne bağımsız değişkeni için bir biçim öğesi sağlayın ve her biçim öğesi için bir nesne bağımsız değişkeni sağlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralın iki ihlalini gösterir.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
