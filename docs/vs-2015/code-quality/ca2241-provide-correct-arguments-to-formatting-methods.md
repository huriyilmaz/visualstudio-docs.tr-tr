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
ms.openlocfilehash: 1dfd770efd4d690930155d2486b8ff1859065272
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543656"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 `format`,, Veya gibi bir yönteme geçirilen dize bağımsız değişkeni, <xref:System.Console.WriteLine%2A> <xref:System.Console.Write%2A> <xref:System.String.Format%2A?displayProperty=fullName> her bir nesne bağımsız değişkenine karşılık gelen bir biçim öğesi içermez veya tam tersi de geçerlidir.

## <a name="rule-description"></a>Kural Tanımı
 , Ve gibi yöntemlere yönelik bağımsız değişkenler, <xref:System.Console.WriteLine%2A> <xref:System.Console.Write%2A> <xref:System.String.Format%2A> ardından birkaç örnek tarafından bir biçim dizesi oluşur <xref:System.Object?displayProperty=fullName> . Biçim dizesi, {index [, hizalama] [: formatString]} biçiminde metin ve katıştırılmış biçim öğelerinden oluşur. ' index ', hangi nesnelerden biçimlendirileceğini gösteren sıfır tabanlı bir tamsayıdır. Bir nesne, biçim dizesinde karşılık gelen bir dizin içermiyorsa, nesne yok sayılır. ' İndex ' tarafından belirtilen nesne yoksa, <xref:System.FormatException?displayProperty=fullName> çalışma zamanında bir oluşturulur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için her bir nesne bağımsız değişkeni için bir biçim öğesi sağlayın ve her biçim öğesi için bir nesne bağımsız değişkeni sağlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralın iki ihlalini gösterir.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
