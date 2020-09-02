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
ms.openlocfilehash: 033d8f0e22ec040ffb10821993a5a9c647ee401e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538924"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison belirt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Dize karşılaştırma işlemi, parametre ayarlanmamış bir yöntem aşırı yüklemesi kullanır <xref:System.StringComparison> .

## <a name="rule-description"></a>Kural Tanımı
 Çoğu dize işlemi, <xref:System.String.Compare%2A> ve <xref:System.String.Equals%2A> yöntemleri, bir <xref:System.StringComparison> sabit listesi değerini parametre olarak kabul eden bir aşırı yükleme sağlar.

 Bir parametre alan aşırı yükleme olduğunda <xref:System.StringComparison> , bu parametreyi almayan aşırı yükleme yerine kullanılmalıdır. Bu parametreyi açıkça ayarlayarak, kodunuz genellikle daha net ve bakım daha kolay hale getirilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için dize karşılaştırma yöntemlerini <xref:System.StringComparison> bir parametre olarak numaralandırmayı kabul eden aşırı yüklemeleri değiştirin. Örneğin: olarak değiştirin `String.Compare(str1, str2)` `String.Compare(str1, str2, StringComparison.Ordinal)` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kitaplık veya uygulama sınırlı bir yerel hedef kitle için tasarlanıyorsa ve bu nedenle yerelleştirilmez, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Genelleştirme Uyarıları](../code-quality/globalization-warnings.md) [CA1309: sıralı StringComparison kullanın](../code-quality/ca1309-use-ordinal-stringcomparison.md)
