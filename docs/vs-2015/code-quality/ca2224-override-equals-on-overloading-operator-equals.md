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
ms.openlocfilehash: 39272790b6ef366c64d45e0aea238606d0b62bf4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538642"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Eşittir işlecini aşırı yüklerken Equals'ı geçersiz kılın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Ortak tür eşitlik işlecini uygular, ancak geçersiz kılmaz <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 Eşitlik işlecinin, yöntemin işlevselliğine erişmek için sözdizimsel olarak uygun bir yol olması amaçlanmıştır <xref:System.Object.Equals%2A> . Eşitlik işlecini uygularsanız, mantığı ile özdeş olmalıdır <xref:System.Object.Equals%2A> .

 C# derleyicisi, kodunuz bu kuralı ihlal ederse bir uyarı verir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için eşitlik işlecinin uygulamasını kaldırmanız veya geçersiz kılmalı <xref:System.Object.Equals%2A> ve iki yöntemin aynı değerleri döndürmesini sağlayabilirsiniz. Eşitlik işleci tutarsız bir davranış oluşturmasa, <xref:System.Object.Equals%2A> yöntemi temel sınıfta Çağıran bir uygulamasını sağlayarak ihlalin düzeltmesini çözebilirsiniz <xref:System.Object.Equals%2A> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Eşitlik operatörü devralınan uygulamasıyla aynı değeri döndürürse, bu kuraldan bir uyarı bastırmayı güvenli hale getirmektir <xref:System.Object.Equals%2A> . Örnek bölüm, bu kuraldan bir uyarıyı güvenle gizedebilen bir tür içerir.

## <a name="examples-of-inconsistent-equality-definitions"></a>Tutarsız eşitlik tanımlarının örnekleri

### <a name="description"></a>Description
 Aşağıdaki örnekte, tutarsız bir eşitlik tanımları içeren bir tür gösterilmektedir. `BadPoint`eşitlik işlecinin özel bir uygulamasını sağlayarak eşitlik anlamını değiştirir, ancak <xref:System.Object.Equals%2A> aynı şekilde davranması için geçersiz kılmaz.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki kod davranışını sınar `BadPoint` .

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **a = ([0] 1, 1) ve b = ([1] 2, 2) eşittir mi? Hayır** 
 **= = b? ** 
 **A1 ve a eşit değil mi? Evet** 
 **a1 = = a? Evet** 
 **b ve bCopy eşittir mi? Hayır** 
 **b = = bCopy? Evet**
## <a name="example"></a>Örnek
 Aşağıdaki örnek, teknik olarak bu kuralı ihlal eden, ancak tutarsız bir şekilde davranmayan bir türü gösterir.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki kod davranışını sınar `GoodPoint` .

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **a = (1, 1) ve b = (2, 2) eşittir mi? Hayır** 
 **= = b? ** 
 **A1 ve a eşit değil mi? Evet** 
 **a1 = = a? Evet** 
 **b ve bCopy eşittir mi? Evet** 
 **b = = bCopy? Evet**
## <a name="class-example"></a>Sınıf örneği

### <a name="description"></a>Description
 Aşağıdaki örnek, bu kuralı ihlal eden bir sınıfı (başvuru türü) gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, geçersiz kılarak ihlalin düzeltir <xref:System.Object.Equals%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Yapı örneği

### <a name="description"></a>Description
 Aşağıdaki örnek, bu kuralı ihlal eden bir yapıyı (değer türü) gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, geçersiz kılarak ihlalin düzeltir <xref:System.ValueType.Equals%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1046: Eşittir işlecini başvuru türlerinde aşırı yüklemeyin](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
