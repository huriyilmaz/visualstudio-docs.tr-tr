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
ms.openlocfilehash: 6e16fff154b5c0df660b06e5bf9e9e838762adff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661483"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Yerel özel dizeleri doğrudan programın içine gömmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir yöntem, belirli sistem klasörlerinin yolunun bir bölümünü temsil eden bir dize sabiti kullanır.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 numaralandırması özel sistem klasörlerine başvuran Üyeler içerir. Bu klasörlerin konumları farklı işletim sistemlerinde farklı değerlere sahip olabilir, Kullanıcı konumların bazılarını değiştirebilir ve konumlar yerelleştirilir. Özel bir klasöre örnek olarak, [!INCLUDE[winxp](../includes/winxp-md.md)] "C:\WINDOWS\system32" olan ve [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] üzerinde "C:\WINNT\system32" olan sistem klasörüdür. @No__t_0 yöntemi <xref:System.Environment.SpecialFolder> numaralandırmasında ilişkilendirilen konumları döndürür. @No__t_0 tarafından döndürülen konumlar yerelleşmiş ve çalışmakta olan bilgisayar için uygundur.

 Bu kural, <xref:System.Environment.GetFolderPath%2A> yöntemi kullanılarak alınan klasör yollarını ayrı dizin düzeylerinde simgeleştirir. Her dize sabit değeri belirteçlerle karşılaştırılır. Bir eşleşme bulunursa, yöntemin belirteçle ilişkili sistem konumuna başvuran bir dize oluşturmakta olduğu varsayılır. Taşınabilirlik ve Yerelleştirilebilirlik için, dize sabit değerlerini kullanmak yerine özel sistem klasörlerinin konumlarını almak üzere <xref:System.Environment.GetFolderPath%2A> yöntemini kullanın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Environment.GetFolderPath%2A> yöntemini kullanarak konumu alın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Dize sabit değeri <xref:System.Environment.SpecialFolder> numaralandırmasıyla ilişkili sistem konumlarından birine başvurmak için kullanılmıyorsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuraldan üç uyarı üreten ortak uygulama verileri klasörünün yolunu oluşturur. Sonra örnek, <xref:System.Environment.GetFolderPath%2A> yöntemini kullanarak yolu alır.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
