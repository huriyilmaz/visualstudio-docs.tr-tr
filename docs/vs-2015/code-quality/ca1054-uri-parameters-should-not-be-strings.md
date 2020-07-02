---
title: 'CA1054: URI parametreleri dize olmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: babef652bbfa55d6549cf0e43ddae0920b3ff302
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539496"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: URI parametreleri dize olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir tür, adı "Uri", "Uri", "urn", "urn", "URL" veya "URL" içeren bir dize parametresine sahip bir yöntem bildirir ve tür, bir parametreyi alan karşılık gelen bir aşırı yükleme bildirmiyor <xref:System.Uri?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, parametre adını ortası kuralı kuralına göre belirteçlere böler ve her belirtecin "Uri", "Uri", "urn", "urn", "URL" veya "URL" olarak eşit olup olmadığını denetler. Bir eşleşme varsa, kural parametrenin bir Tekdüzen Kaynak tanımlayıcısını (URI) temsil ettiğini varsayar. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. Bir yöntem bir URI 'nin dize gösterimini alırsa, <xref:System.Uri> Bu hizmetleri güvenli ve güvenli bir şekilde sağlayan sınıfının bir örneğini alan karşılık gelen bir aşırı yükleme sağlanmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için parametreyi bir tür olarak değiştirin <xref:System.Uri> ; Bu bir son değişiklik değildir. Alternatif olarak, bir parametresi alan ve <xref:System.Uri> Bu bölünemez bir değişiklik olan yöntemin aşırı yüklemesini sağlar.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Parametresi bir URI 'yi temsil etmediği takdirde bu kuraldan bir uyarının bastırmasının güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `ErrorProne` Bu kuralı ihlal eden bir türü ve kuralını karşılayan bir türü gösterir `SaferWay` .

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1056: URI özellikleri dize olmamalıdır](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: URI dönüş değerleri dize olmamalıdır](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Dizeler yerine System.Uri nesneleri gönderin](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: String URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
