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
ms.openlocfilehash: bcdb4d8333b0a4d2d06580d882cf736d4527eca4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539535"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: String URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir tür, yalnızca bir parametre içeren bir dize parametresinin yerine geçen <xref:System.Uri?displayProperty=fullName> ve dize parametresini alan aşırı yükleme, parametreyi alan aşırı yüklemeyi çağırmayan Yöntem yüklerini bildirir <xref:System.Uri> .

## <a name="rule-description"></a>Kural Tanımı
 Aşırı yüklemeler yalnızca dize/parametre tarafından farklı olduğundan <xref:System.Uri> , dize bir Tekdüzen Kaynak tanımlayıcısını (URI) temsil edecek şekilde kabul edilir. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. <xref:System.Uri>Sınıfı bu hizmetleri güvenli ve güvenli bir şekilde sağlar. Sınıfının avantajlarından yararlanmak için <xref:System.Uri> , dize aşırı yüklemesi <xref:System.Uri> dize bağımsız değişkenini kullanarak aşırı yüklemeyi çağırmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 URI 'nin dize gösterimini kullanan yöntemi yeniden uygulayın <xref:System.Uri> , böylece dize bağımsız değişkenini kullanarak sınıfının bir örneğini oluşturur ve sonra <xref:System.Uri> nesneyi parametresi olan aşırı yüklemeye geçirir <xref:System.Uri> .

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

 [CA1054: URI parametreleri dize olmamalıdır](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI dönüş değerleri dize olmamalıdır](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
