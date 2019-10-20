---
title: 'CA1820: dize uzunluğunu kullanarak boş dizeler için test edin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6711dac907de2777cf892b20269fec7e99d3bd6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657499"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Dize uzunluğunu kullanarak boş dizeler için sınayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Dize, <xref:System.Object.Equals%2A?displayProperty=fullName> kullanılarak boş dizeyle karşılaştırılır.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 özelliğini kullanarak dizeleri karşılaştırma veya <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> yöntemi <xref:System.Object.Equals%2A> kullanmaktan çok daha hızlıdır. Bunun nedeni, <xref:System.Object.Equals%2A> <xref:System.String.IsNullOrEmpty%2A> veya <xref:System.String.Length%2A> özellik değerini almak için yürütülen yönergelerin sayısını ya da değeri sıfıra karşılaştırmak için çok daha fazla MSIL yönergesi yürütür.

 @No__t_0 ve <xref:System.String.Length%2A> = = 0 ' ın null dizeler için farklı davrandığını bilmelisiniz. @No__t_0 özelliğinin değerini null bir dizeye almaya çalışırsanız, ortak dil çalışma zamanı bir <xref:System.NullReferenceException?displayProperty=fullName> oluşturur. Null dize ve boş dize arasında bir karşılaştırma gerçekleştirirseniz, ortak dil çalışma zamanı bir özel durum oluşturmaz; Karşılaştırma `false` döndürür. Null testi, bu iki yaklaşımın göreli performansını önemli ölçüde etkilemez. @No__t_0 hedeflenirken <xref:System.String.IsNullOrEmpty%2A> yöntemini kullanın. Aksi takdirde, mümkün olduğunda <xref:System.String.Length%2A> = = karşılaştırma kullanın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için karşılaştırmayı <xref:System.String.Length%2A> özelliğini kullanacak şekilde değiştirin ve null dize için test edin. @No__t_0 hedefliyorsanız <xref:System.String.IsNullOrEmpty%2A> yöntemini kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Performans bir sorun değilse, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, boş bir dizeyi aramak için kullanılan farklı teknikleri gösterir.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
