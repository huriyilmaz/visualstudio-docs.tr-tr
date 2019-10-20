---
title: 'CA1309: sıralı StringComparison kullan | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34054f6f444e503077c1e81da9f08ae2832d635a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661427"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Sıralı StringComparison kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Dil olmayan bir dize karşılaştırma işlemi, <xref:System.StringComparison> parametresini **sıra** veya **OrdinalIgnoreCase**olarak ayarlamayın.

## <a name="rule-description"></a>Kural Tanımı
 Çok sayıda dize işlemi, <xref:System.String.Compare%2A?displayProperty=fullName> ve <xref:System.String.Equals%2A?displayProperty=fullName> yöntemlerinin en önemlileri, artık bir parametre olarak <xref:System.StringComparison?displayProperty=fullName> numaralandırma değeri kabul eden bir aşırı yükleme sağlıyor.

 **StringComparison. Ordinal** ya da **StringComparison. OrdinalIgnoreCase**belirttiğinizde, dize karşılaştırması dil olmayan bir işlem olur. Yani, doğal dile özgü özellikler, karşılaştırma kararları verilirken yok sayılır. Bu, kararların basit bayt karşılaştırmaları temel aldığı ve kültüre göre parametreli büyük/küçük harf veya denklik tablolarının yoksayılmasına yol gösterir. Sonuç olarak, parametresini **StringComparison. Ordinal** ya da **StringComparison. OrdinalIgnoreCase**olarak ayarlayarak, kodunuz genellikle hızlanır, doğruluk artar ve daha güvenilir hale gelir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, dize karşılaştırma yöntemini bir parametre olarak <xref:System.StringComparison?displayProperty=fullName> numaralandırmayı kabul eden bir aşırı yüklemeye değiştirin ve **Ordinal** ya da **OrdinalIgnoreCase**belirtin. Örneğin, `String.Compare(str1, str2)` ' ı `String.Compare(str1, str2, StringComparison.Ordinal)` ' e değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kitaplık veya uygulama sınırlı bir yerel hedef kitle için tasarlanıyorsa veya geçerli kültürün semantiğinin kullanılması gerektiğinde, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Genelleştirme Uyarıları](../code-quality/globalization-warnings.md) [CA1307: StringComparison belirt](../code-quality/ca1307-specify-stringcomparison.md)
