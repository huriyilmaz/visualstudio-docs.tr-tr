---
title: 'CA2234: dizeler yerine System. Uri nesnelerini geçir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ce5c076260886def089118a4d7211d75e0185c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545216"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Dizeler yerine System.Uri nesneleri gönderin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Adı "Uri", "Uri", "urn", "urn", "URL" veya "URL" içeren bir dize parametresine sahip bir yönteme çağrı yapılır. ve yöntemin bildirim türü, parametresine sahip karşılık gelen bir yöntem aşırı yüklemesini içerir <xref:System.Uri?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 Bir parametre adı, ortası büyük/küçük harf kuralına göre belirteçlere bölünür ve ardından "Uri", "Uri", "urn", "urn", "URL" veya "URL" olarak eşit olup olmadığını görmek için her belirteç denetlenir. Bir eşleşme varsa parametre bir Tekdüzen Kaynak tanımlayıcısını (URI) temsil eder. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. <xref:System.Uri>Sınıfı bu hizmetleri güvenli ve güvenli bir şekilde sağlar. Yalnızca bir URI gösterimi ile ilgili olan iki aşırı yükleme arasında seçim yapıldığında, Kullanıcı bir bağımsız değişken alan aşırı yüklemeyi seçmelidir <xref:System.Uri> .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için bağımsız değişkenini alan aşırı yüklemeyi çağırın <xref:System.Uri> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Dize parametresi bir URI 'yi temsil etmediği takdirde bu kuraldan bir uyarının bastırmasının güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, yeniden `ErrorProne` `SaferWay` yüklemeyi doğru şekilde çağıran kuralı ve yöntemi ihlal eden bir yöntemi gösterir <xref:System.Uri> .

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1057: String URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: URI özellikleri dize olmamalıdır](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI parametreleri dize olmamalıdır](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI dönüş değerleri dize olmamalıdır](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
