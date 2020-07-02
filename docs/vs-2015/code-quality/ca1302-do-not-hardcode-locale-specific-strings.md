---
title: 'CA1302: yerel koda özel dizeler vermeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18da0471b1ac62f0e61b303c60b46c15cdc2e428
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539015"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Yerel özel dizeleri doğrudan programın içine gömmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir yöntem, belirli sistem klasörlerinin yolunun bir bölümünü temsil eden bir dize sabiti kullanır.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Environment.SpecialFolder?displayProperty=fullName>Sabit Listesi özel sistem klasörlerine başvuran Üyeler içerir. Bu klasörlerin konumları farklı işletim sistemlerinde farklı değerlere sahip olabilir, Kullanıcı konumların bazılarını değiştirebilir ve konumlar yerelleştirilir. Özel bir klasöre örnek olarak "C:\WINDOWS\system32" ve üzerinde "C:\WINNT\system32" olan sistem klasörü bulunur [!INCLUDE[winxp](../includes/winxp-md.md)] [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] . <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>Yöntemi, numaralandırmada ilişkili konumları döndürür <xref:System.Environment.SpecialFolder> . Tarafından döndürülen konumlar <xref:System.Environment.GetFolderPath%2A> yerelleştirilmiştir ve çalışmakta olan bilgisayar için uygundur.

 Bu kural, <xref:System.Environment.GetFolderPath%2A> metodu ayrı Dizin düzeylerine kullanarak alınan klasör yollarını simgeleştirir. Her dize sabit değeri belirteçlerle karşılaştırılır. Bir eşleşme bulunursa, yöntemin belirteçle ilişkili sistem konumuna başvuran bir dize oluşturmakta olduğu varsayılır. Taşınabilirlik ve Yerelleştirilebilirlik için, <xref:System.Environment.GetFolderPath%2A> dize sabit değerlerini kullanmak yerine özel sistem klasörlerinin konumlarını almak için yöntemini kullanın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, yöntemini kullanarak konumu alın <xref:System.Environment.GetFolderPath%2A> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Dize sabit değeri, numaralandırmada ilişkili sistem konumlarından birine başvurmak için kullanılmıyorsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir <xref:System.Environment.SpecialFolder> .

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuraldan üç uyarı üreten ortak uygulama verileri klasörünün yolunu oluşturur. Daha sonra örnek, yöntemini kullanarak yolunu alır <xref:System.Environment.GetFolderPath%2A> .

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
