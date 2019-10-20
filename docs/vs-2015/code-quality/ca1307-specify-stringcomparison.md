---
title: 'CA1307: StringComparison belirtin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 111f0b85a601d931ac17bde46f7170fa81e71815
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661403"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Dize karşılaştırma işlemi, <xref:System.StringComparison> parametresi ayarlanmamış bir yöntem aşırı yüklemesi kullanır.

## <a name="rule-description"></a>Kural Tanımı
 Çoğu dize işlemi, <xref:System.String.Compare%2A> ve <xref:System.String.Equals%2A> yöntemlerinin en önemlileri, bir <xref:System.StringComparison> numaralandırma değerini parametre olarak kabul eden bir aşırı yükleme sağlar.

 Bir <xref:System.StringComparison> parametresi alan aşırı yükleme yapıldığında, bu parametreyi almayan aşırı yükleme yerine kullanılmalıdır. Bu parametreyi açıkça ayarlayarak, kodunuz genellikle daha net ve bakım daha kolay hale getirilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, dize karşılaştırma yöntemlerini parametre olarak <xref:System.StringComparison> numaralandırmayı kabul eden aşırı yüklerden değiştirin. Örneğin: `String.Compare(str1, str2)` ' i `String.Compare(str1, str2, StringComparison.Ordinal)` ' e değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kitaplık veya uygulama sınırlı bir yerel hedef kitle için tasarlanıyorsa ve bu nedenle yerelleştirilmez, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Genelleştirme Uyarıları](../code-quality/globalization-warnings.md) [CA1309: sıralı StringComparison kullanın](../code-quality/ca1309-use-ordinal-stringcomparison.md)
