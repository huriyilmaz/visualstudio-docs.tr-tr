---
title: 'CA1302: Yerel özel dizeleri doğrudan programın içine gömmeyin'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 727acfa5497f2d7f0d09349ff2f5f6648c9d1ca6
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444417"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Yerel özel dizeleri doğrudan programın içine gömmeyin

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategori|Microsoft. Globalization|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
Bir yöntem, belirli sistem klasörlerinin yolunun bir bölümünü temsil eden bir dize sabiti kullanır.

## <a name="rule-description"></a>Kural açıklaması
@No__t-0 numaralandırması özel sistem klasörlerine başvuran Üyeler içerir. Bu klasörlerin konumları farklı işletim sistemlerinde farklı değerlere sahip olabilir, Kullanıcı konumların bazılarını değiştirebilir ve konumlar yerelleştirilir. Özel bir klasöre örnek olarak, [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] ' da "C:\WINDOWS\system32", [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)] üzerinde "C:\WINNT\system32" olan sistem klasörüdür. @No__t-0 yöntemi, <xref:System.Environment.SpecialFolder> numaralandırmasıyla ilişkili konumları döndürür. @No__t-0 tarafından döndürülen konumlar yereldir ve çalışmakta olan bilgisayar için uygundur.

Bu kural, <xref:System.Environment.GetFolderPath%2A> yöntemi kullanılarak alınan klasör yollarını ayrı dizin düzeylerinde simgeleştirir. Her dize sabit değeri belirteçlerle karşılaştırılır. Bir eşleşme bulunursa, yöntemin belirteçle ilişkili sistem konumuna başvuran bir dize oluşturmakta olduğu varsayılır. Taşınabilirlik ve Yerelleştirilebilirlik için, dize sabit değerlerini kullanmak yerine özel sistem klasörlerinin konumlarını almak üzere <xref:System.Environment.GetFolderPath%2A> yöntemini kullanın.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için <xref:System.Environment.GetFolderPath%2A> yöntemini kullanarak konumu alın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Dize sabit değeri <xref:System.Environment.SpecialFolder> numaralandırmasıyla ilişkili sistem konumlarından birine başvurmak için kullanılmıyorsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, bu kuraldan üç uyarı üreten ortak uygulama verileri klasörünün yolunu oluşturur. Ardından örnek, <xref:System.Environment.GetFolderPath%2A> yöntemini kullanarak yolu alır.

[!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
[!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>İlgili kurallar
[CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
