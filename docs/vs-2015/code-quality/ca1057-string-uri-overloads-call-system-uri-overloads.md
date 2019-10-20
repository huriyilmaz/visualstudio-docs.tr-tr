---
title: 'CA1057: dize URI aşırı yüklemeleri System. Uri aşırı yüklerini çağırır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba7e7de4f3ef6336ed3d82dc1e1da03ec0bf2575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603071"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Dize URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir tür, yalnızca bir dize parametresinin <xref:System.Uri?displayProperty=fullName> parametresiyle değiştirilmesine göre farklılık gösteren ve dize parametresini alan aşırı yükleme <xref:System.Uri> parametresini alan aşırı yüklemeyi çağırmayan Yöntem yüklerini bildirir.

## <a name="rule-description"></a>Kural Tanımı
 Aşırı yüklemeler yalnızca dize/<xref:System.Uri> parametresi tarafından farklı olduğundan, dize bir Tekdüzen Kaynak tanımlayıcısını (URI) temsil eder. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. @No__t_0 sınıfı bu hizmetleri güvenli ve güvenli bir şekilde sağlar. @No__t_0 sınıfının avantajlarından yararlanmak için, dize aşırı yüklemesi dize bağımsız değişkenini kullanarak <xref:System.Uri> aşırı yüklemeyi çağırmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 URI 'nin dize gösterimini kullanan yöntemi yeniden uygulayın, böylece dize bağımsız değişkenini kullanarak <xref:System.Uri> sınıfının bir örneğini oluşturur ve sonra <xref:System.Uri> nesnesini <xref:System.Uri> parametresine sahip olan aşırı yüklemeye geçirir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Dize parametresi bir URI 'yi temsil etmediği takdirde bu kuraldan bir uyarının bastırmasının güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, doğru şekilde uygulanan bir dize aşırı yüklemesini göstermektedir.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2234: Dizeler yerine System.Uri nesneleri gönderin](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: URI özellikleri dize olmamalıdır](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI parametreleri dizeler olmamalıdır](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI dönüş değerleri dizeler olmamalıdır](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
