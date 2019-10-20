---
title: 'CA2224: override işleci eşittir üzerine yaz eşittir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d35052bb2a1efb1a466ffc67c95c83e5b3a76533
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671885"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Eşittir işlecini aşırı yükleyerek eşittiri geçersiz kılın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Ortak tür eşitlik işlecini uygular, ancak <xref:System.Object.Equals%2A?displayProperty=fullName> geçersiz kılmaz.

## <a name="rule-description"></a>Kural Tanımı
 Eşitlik işlecinin, <xref:System.Object.Equals%2A> yönteminin işlevlerine erişmek için sözdizimsel olarak uygun bir yol olması amaçlanmıştır. Eşitlik işlecini uygularsanız, mantığı <xref:System.Object.Equals%2A> özdeş olmalıdır.

 Kodunuz C# bu kuralı ihlal ederse derleyici bir uyarı verir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için eşitlik işlecinin uygulamasını kaldırmanız veya <xref:System.Object.Equals%2A> geçersiz kılmalı ve iki yöntemin aynı değerleri döndürmesini sağlayabilirsiniz. Eşitlik işleci tutarsız bir davranış içermiyorsa, Taban sınıfında <xref:System.Object.Equals%2A> yöntemini çağıran bir <xref:System.Object.Equals%2A> uygulamasını sağlayarak ihlalin düzelmesi yapabilirsiniz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Eşitlik operatörü <xref:System.Object.Equals%2A> devralınan uygulamasıyla aynı değeri döndürürse, bu kuraldan bir uyarının görüntülenmesini güvenli hale getirmektir. Örnek bölüm, bu kuraldan bir uyarıyı güvenle gizedebilen bir tür içerir.

## <a name="examples-of-inconsistent-equality-definitions"></a>Tutarsız eşitlik tanımlarının örnekleri

### <a name="description"></a>Açıklama
 Aşağıdaki örnekte, tutarsız bir eşitlik tanımları içeren bir tür gösterilmektedir. `BadPoint` eşitlik işlecinin özel bir uygulamasını sağlayarak eşitlik anlamını değiştirir, ancak aynı şekilde davranması için <xref:System.Object.Equals%2A> geçersiz kılmaz.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki kod `BadPoint` ' ın davranışını sınar.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **a = ([0] 1, 1) ve b = ([1] 2, 2) eşittir mi? Hayır** **a 
 a = = b? @No__t_3** **a1 ve a eşit değildir mi? Evet** 
**a1 = = a? Evet** 
**b ve bCopy eşittir mi? Hayır** 
**b = = bCopy? Evet**
## <a name="example"></a>Örnek
 Aşağıdaki örnek, teknik olarak bu kuralı ihlal eden, ancak tutarsız bir şekilde davranmayan bir türü gösterir.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki kod `GoodPoint` ' ın davranışını sınar.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **a = (1, 1) ve b = (2, 2) eşittir mi? Hayır** **a 
 a = = b? @No__t_3** **a1 ve a eşit değildir mi? Evet** 
**a1 = = a? Evet** 
**b ve bCopy eşittir mi? Evet** 
**b = = bCopy? Evet**
## <a name="class-example"></a>Sınıf örneği

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, bu kuralı ihlal eden bir sınıfı (başvuru türü) gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.Object.Equals%2A?displayProperty=fullName> geçersiz kılarak ihlalin düzeltir.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Yapı örneği

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, bu kuralı ihlal eden bir yapıyı (değer türü) gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.ValueType.Equals%2A?displayProperty=fullName> geçersiz kılarak ihlalin düzeltir.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1046: Başvuru türlerinde eşittir işleçlerini aşırı yüklemeyin](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: ValueType.Equals değerini geçersiz kılmada eşittir işlecini aşırı yükle](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
