---
title: 'CA1046: Başvuru türlerinde eşittir işlecini aşırı yüklemeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 519faf2d49cb74d60d342d6bcf449f211076b0b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661093"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Başvuru türlerinde eşittir işleçlerini aşırı yüklemeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya iç içe ortak başvuru türü eşitlik işlecini aşırı yükler.

## <a name="rule-description"></a>Kural Tanımı
 Başvuru türleri için, varsayılan eşitlik işleci neredeyse her zaman doğrudur. Varsayılan olarak, yalnızca aynı nesneye gelirseniz iki başvuru eşit olur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için eşitlik işlecinin uygulamasını kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Başvuru türü yerleşik bir değer türü gibi davrandığı zaman, bu kuraldan bir uyarının bastırması güvenlidir. Türün örneklerine ekleme veya çıkarma yapmak için anlamlı ise, eşitlik işlecinin uygulanması ve ihlalin görünmemesi için büyük olasılıkla doğrudur.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, iki başvuruyu karşılaştırırken varsayılan davranışı gösterir.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama bazı başvuruları karşılaştırır.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **a = yeni (2, 2) ve b = yeni (2, 2) eşittir mi? @No__t_1** **c ve a eşit değildir mi? Evet** 
**b ve a = =? **@No__t_5**c ve a yok = =? Evet**
## <a name="related-rules"></a>İlgili kurallar
 [CA1013: Eşittir işlecini ekleme ve çıkarmayı aşırı yükleyerek aşırı yükleyin](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Object.Equals%2A?displayProperty=fullName> [eşitlik işleçleri](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
