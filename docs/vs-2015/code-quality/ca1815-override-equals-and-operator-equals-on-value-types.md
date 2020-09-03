---
title: 'CA1815: değer türlerinde Equals ve işleç eşittir geçersiz kıl | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc5dc311fd85af2b6a0eb3e29e9932614ca55193
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543916"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Değer türlerinde eşittir ve işleç eşittiri geçersiz kılın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Ortak değer türü geçersiz kılmaz <xref:System.Object.Equals%2A?displayProperty=fullName> veya eşitlik işlecini uygulamıyor (= =). Bu kural numaralandırmalar denetlemez.

## <a name="rule-description"></a>Kural Tanımı
 Değer türlerinde, devralınan uygulama <xref:System.Object.Equals%2A> yansıma kitaplığını kullanır ve tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıların örnekleri karşılaştırmasını veya sıralamasını veya bunları karma tablo anahtarları olarak kullanmasını bekleliyorsanız, değer türü uygulanmalıdır <xref:System.Object.Equals%2A> . Programlama diliniz işleç aşırı yüklemesini destekliyorsa eşitlik ve eşitsizlik işleçleri de bir uygulama sağlamalısınız.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için uygulamasının bir uygulamasını sağlayın <xref:System.Object.Equals%2A> . Mümkünse eşitlik işlecini uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Değer türünün örnekleri birbirleriyle karşılaştırılmayacak şekilde bu kuraldan bir uyarı bastırılmak güvenlidir.

## <a name="example-of-a-violation"></a>Ihlalin örneği

### <a name="description"></a>Description
 Aşağıdaki örnek, bu kuralı ihlal eden bir yapıyı (değer türü) gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Nasıl düzeltileceğini gösteren örnek

### <a name="description"></a>Description
 Aşağıdaki örnek, <xref:System.ValueType.Equals%2A?displayProperty=fullName> eşitlik işleçlerini (= =,! =) geçersiz kılarak ve uygulayarak önceki ihlalin düzeltir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2224: Eşittir işlecini aşırı yüklerken Equals'ı geçersiz kılın](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Object.Equals%2A?displayProperty=fullName>
