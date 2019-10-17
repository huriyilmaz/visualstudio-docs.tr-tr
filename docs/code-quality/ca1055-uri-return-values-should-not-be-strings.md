---
title: 'CA1055: URI dönüş değerleri dizeler olmamalıdır'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 41099f0803d6432736e051a1a6ef61c7a6e85160
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446588"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: URI dönüş değerleri dizeler olmamalıdır

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Kategori|Microsoft. Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bir yöntemin adı "Uri", "Uri", "urn", "urn", "URL" veya "URL" içerir ve yöntem bir dize döndürür.

Varsayılan olarak, bu kural yalnızca ortak yöntemlere bakar, ancak bu [yapılandırılabilir](#configurability).

## <a name="rule-description"></a>Kural açıklaması

Bu kural, yöntem adını, Pascal büyük harf kuralına göre belirteçlere böler ve her belirtecin "Uri", "Uri", "urn", "urn", "URL" veya "URL" olarak eşit olup olmadığını denetler. Bir eşleşme varsa kural, yöntemin bir Tekdüzen Kaynak tanımlayıcısı (URI) döndürdüğünü varsayar. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. @No__t-0 sınıfı bu hizmetleri güvenli ve güvenli bir şekilde sağlar.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için, dönüş türünü <xref:System.Uri> olarak değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Dönüş değeri bir URI 'yi temsil etmediği takdirde bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="configurability"></a>Yapılandırılabilirlik

Bu kuralı [FxCop çözümleyicilerinin](install-fxcop-analyzers.md) (eski analizler olmadan) çalıştırıyorsanız, kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz. Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir. editorconfig dosyasına ekleyin:

```ini
dotnet_code_quality.ca1055.api_surface = private, internal
```

Bu seçeneği yalnızca bu kural için, tüm kurallar için veya bu kategorideki tüm kurallar (tasarım) için yapılandırabilirsiniz. Daha fazla bilgi için bkz. [FxCop çözümleyicileri yapılandırma](configure-fxcop-analyzers.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bu kuralı ihlal eden bir tür, `ErrorProne`, ve kuralı karşılayan `SaferWay` ' i gösterir.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>İlgili kurallar

- [CA1056: URI özellikleri dize olmamalıdır](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: URI parametreleri dizeler olmamalıdır](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA2234: Dizeler yerine System.Uri nesneleri gönderin](../code-quality/ca2234.md)
- [CA1057: Dize URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
