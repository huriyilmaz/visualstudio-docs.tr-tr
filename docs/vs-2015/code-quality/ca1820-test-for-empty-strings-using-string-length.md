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
ms.openlocfilehash: 296eb6407e3ce63b0eb28ff86c215c12ec724ce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545320"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Dize uzunluğunu kullanarak boş dizeleri test edin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Dize, kullanılarak boş dizeyle karşılaştırılır <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.String.Length%2A?displayProperty=fullName>Özelliği veya yöntemi kullanarak dizeleri karşılaştırmak, <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> kullanmaktan çok daha hızlı bir şekilde daha hızlıdır <xref:System.Object.Equals%2A> . Bunun nedeni, <xref:System.Object.Equals%2A> <xref:System.String.IsNullOrEmpty%2A> <xref:System.String.Length%2A> özellik değerini almak ve değeri sıfıra karşılaştırmak için yürütülen yönergelerin sayısından ya da daha fazla MSIL yönergesi yürütür.

 <xref:System.Object.Equals%2A>Ve <xref:System.String.Length%2A> = = 0 ' ın null dizeler için farklı davrandığını unutmayın. <xref:System.String.Length%2A>Özelliğin değerini null bir dizeye almaya çalışırsanız, ortak dil çalışma zamanı bir oluşturur <xref:System.NullReferenceException?displayProperty=fullName> . Null dize ve boş dize arasında bir karşılaştırma gerçekleştirirseniz, ortak dil çalışma zamanı bir özel durum oluşturmaz; Karşılaştırma döndürülür `false` . Null testi, bu iki yaklaşımın göreli performansını önemli ölçüde etkilemez. Hedefleme sırasında [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] <xref:System.String.IsNullOrEmpty%2A> yöntemini kullanın. Aksi takdirde, <xref:System.String.Length%2A> mümkün olduğunda = = karşılaştırmayı kullanın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için karşılaştırmayı, özelliğini kullanacak şekilde değiştirin <xref:System.String.Length%2A> ve null dize için test edin. Hedefleniyorsa [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] <xref:System.String.IsNullOrEmpty%2A> yöntemini kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Performans bir sorun değilse, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, boş bir dizeyi aramak için kullanılan farklı teknikleri gösterir.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
