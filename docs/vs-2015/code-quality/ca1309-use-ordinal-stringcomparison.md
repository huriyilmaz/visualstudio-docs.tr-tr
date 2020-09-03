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
ms.openlocfilehash: be60d2a1dcb769a0b7a8574984de3d288bf57af4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538885"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Sıralı StringComparison kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Dilsel olmayan bir dize karşılaştırma işlemi, <xref:System.StringComparison> parametreyi **Ordinal** veya **OrdinalIgnoreCase**olarak ayarlamayın.

## <a name="rule-description"></a>Kural Tanımı
 Çok sayıda dize işlemi, <xref:System.String.Compare%2A?displayProperty=fullName> ve <xref:System.String.Equals%2A?displayProperty=fullName> yöntemleri, artık bir <xref:System.StringComparison?displayProperty=fullName> sabit listesi değerini parametre olarak kabul eden bir aşırı yükleme sağlar.

 **StringComparison. Ordinal** ya da **StringComparison. OrdinalIgnoreCase**belirttiğinizde, dize karşılaştırması dil olmayan bir işlem olur. Yani, doğal dile özgü özellikler, karşılaştırma kararları verilirken yok sayılır. Bu, kararların basit bayt karşılaştırmaları temel aldığı ve kültüre göre parametreli büyük/küçük harf veya denklik tablolarının yoksayılmasına yol gösterir. Sonuç olarak, parametresini **StringComparison. Ordinal** ya da **StringComparison. OrdinalIgnoreCase**olarak ayarlayarak, kodunuz genellikle hızlanır, doğruluk artar ve daha güvenilir hale gelir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, dize karşılaştırma yöntemini bir parametre olarak numaralandırmayı kabul eden bir aşırı yükleme olarak değiştirin <xref:System.StringComparison?displayProperty=fullName> ve **Ordinal** ya da **OrdinalIgnoreCase**belirtin. Örneğin, olarak değiştirin `String.Compare(str1, str2)` `String.Compare(str1, str2, StringComparison.Ordinal)` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kitaplık veya uygulama sınırlı bir yerel hedef kitle için tasarlanıyorsa veya geçerli kültürün semantiğinin kullanılması gerektiğinde, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Genelleştirme Uyarıları](../code-quality/globalization-warnings.md) [CA1307: StringComparison belirt](../code-quality/ca1307-specify-stringcomparison.md)
