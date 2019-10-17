---
title: 'CA1057: Dize URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 92990533b77d27f38296f8519c00840ff1f8c8b1
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449094"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Dize URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategori|Microsoft. Design|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep

Bir tür, yalnızca bir dize parametresinin <xref:System.Uri?displayProperty=fullName> parametresiyle değiştirilmesine göre farklılık gösteren ve dize parametresini alan aşırı yükleme <xref:System.Uri> parametresini alan aşırı yüklemeyi çağırmayan Yöntem yüklerini bildirir.

## <a name="rule-description"></a>Kural açıklaması
Aşırı yüklemeler yalnızca dize veya <xref:System.Uri> parametresiyle farklı olduğundan, dize bir Tekdüzen Kaynak tanımlayıcısını (URI) temsil eder. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. @No__t-0 sınıfı bu hizmetleri güvenli ve güvenli bir şekilde sağlar. @No__t-0 sınıfının avantajlarından yararlanmak için, dize aşırı yüklemesi dize bağımsız değişkenini kullanarak <xref:System.Uri> aşırı yüklemeyi çağırmalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Dize bağımsız değişkenini kullanarak <xref:System.Uri> sınıfının bir örneğini oluşturacak ve sonra <xref:System.Uri> nesnesini <xref:System.Uri> parametresine sahip olan aşırı yüklemeye geçireceğini, URI 'nin dize gösterimini kullanan yöntemi yeniden uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Dize parametresi bir URI 'yi temsil etmediği takdirde bu kuraldan bir uyarının bastırmasının güvenli hale gelir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, doğru şekilde uygulanan bir dize aşırı yüklemesini göstermektedir.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>İlgili kurallar
[CA2234: Dizeler yerine System.Uri nesneleri gönderin](../code-quality/ca2234.md)

[CA1056: URI özellikleri dize olmamalıdır](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054: URI parametreleri dizeler olmamalıdır](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055: URI dönüş değerleri dizeler olmamalıdır](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
