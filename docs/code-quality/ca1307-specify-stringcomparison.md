---
title: 'CA1307: StringComparison belirtme'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3b3d979910883f6be9f542ec581ecbda0f91deb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444378"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison belirtme

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategori|Microsoft. Globalization|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
Dize karşılaştırma işlemi, <xref:System.StringComparison> parametresi ayarlanmamış bir yöntem aşırı yüklemesi kullanır.

## <a name="rule-description"></a>Kural açıklaması
@No__t-0 ve <xref:System.String.Equals%2A> yöntemlerinin çoğu önemli olan çok sayıda dize işlemi, bir parametre olarak @no__t 2 numaralandırma değeri kabul eden bir aşırı yükleme sağlar.

@No__t-0 parametresini alan aşırı yükleme yapıldığında, bu parametreyi almayan aşırı yükleme yerine kullanılmalıdır. Bu parametreyi açıkça ayarlayarak, kodunuz genellikle daha net ve bakım daha kolay hale getirilir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için, dize karşılaştırma yöntemlerini parametre olarak <xref:System.StringComparison> numaralandırmayı kabul eden aşırı yüklerden değiştirin. Örneğin: `String.Compare(str1, str2)` ' i `String.Compare(str1, str2, StringComparison.Ordinal)` ' e değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Kitaplık veya uygulama sınırlı bir yerel hedef kitle için tasarlanıyorsa ve bu nedenle yerelleştirilmez, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme Uyarıları](../code-quality/globalization-warnings.md)
- [CA1309: Sıralı StringComparison kullanın](../code-quality/ca1309-use-ordinal-stringcomparison.md)
