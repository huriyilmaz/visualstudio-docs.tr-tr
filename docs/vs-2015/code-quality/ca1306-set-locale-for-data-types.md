---
title: 'CA1306: veri türleri için yerel ayar ayarla | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: edd1d6a7623f96f03403883ee2585d245414bb3b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539028"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Veri türleri için yereli ayarlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir yöntem veya Oluşturucu bir veya daha fazla <xref:System.Data.DataTable?displayProperty=fullName> veya <xref:System.Data.DataSet?displayProperty=fullName> örnek oluşturdu ve yerel ayar özelliğini (veya) açıkça ayarlamadı <xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 Yerel ayar, sayısal değerler, para birimi sembolleri ve sıralama düzeni için kullanılan biçimlendirme gibi veriler için kültüre özgü sunum öğelerini belirler. Bir <xref:System.Data.DataTable> veya oluşturduğunuzda <xref:System.Data.DataSet> yerel ayarı açıkça ayarlamanız gerekir. Varsayılan olarak, bu türlerin yerel ayarı geçerli kültürdür. Bir veritabanında veya dosyada depolanan ve global olarak paylaşılan veriler için, yerel ayar normalde sabit kültür () olarak ayarlanmalıdır <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> . Veriler kültürler arasında paylaşıldığında, varsayılan yerel ayarı kullanmak <xref:System.Data.DataTable> veya içeriğinin <xref:System.Data.DataSet> yanlış olarak sunulmasına veya yorumlanmasına neden olabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, veya için yerel ayarı açıkça ayarlayın <xref:System.Data.DataTable> <xref:System.Data.DataSet> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kitaplık veya uygulama sınırlı bir yerel hedef kitle için olduğunda, bu kuraldan gelen bir uyarıyı gizlemek güvenlidir, veriler paylaşılmaz veya varsayılan ayar, tüm desteklenen senaryolarda istenen davranışı verir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek iki örnek oluşturur <xref:System.Data.DataTable> .

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
