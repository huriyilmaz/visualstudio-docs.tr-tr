---
title: 'CA1055: URI dönüş değerleri dize olmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 522534d81ef9c87fc93d16a7ee880c7743a3268c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539665"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: URI dönüş değerleri dize olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir yöntemin adı "Uri", "Uri", "urn", "urn", "URL" veya "URL" içerir ve yöntem bir dize döndürür.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, yöntem adını, Pascal büyük harf kuralına göre belirteçlere böler ve her belirtecin "Uri", "Uri", "urn", "urn", "URL" veya "URL" olarak eşit olup olmadığını denetler. Bir eşleşme varsa kural, yöntemin bir Tekdüzen Kaynak tanımlayıcısı (URI) döndürdüğünü varsayar. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. <xref:System.Uri?displayProperty=fullName>Sınıfı bu hizmetleri güvenli ve güvenli bir şekilde sağlar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, dönüş türünü bir olarak değiştirin <xref:System.Uri> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Dönüş değeri bir URI 'yi temsil etmediği takdirde bu kuraldan bir uyarının bastırmasının güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `ErrorProne` Bu kuralı ihlal eden bir türü ve kuralını karşılayan bir türü gösterir `SaferWay` .

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1056: URI özellikleri dize olmamalıdır](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI parametreleri dize olmamalıdır](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA2234: Dizeler yerine System.Uri nesneleri gönderin](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: String URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
