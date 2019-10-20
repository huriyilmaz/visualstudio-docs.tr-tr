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
ms.openlocfilehash: bb9574eb6e9f907d4b1fcc74f50fca0e7db85253
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668401"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Değer türlerinde eşittir ve işleç eşitliklerinin üzerine yaz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Ortak değer türü <xref:System.Object.Equals%2A?displayProperty=fullName> geçersiz kılmaz veya eşitlik işlecini uygulamaz (= =). Bu kural numaralandırmalar denetlemez.

## <a name="rule-description"></a>Kural Tanımı
 Değer türleri için, <xref:System.Object.Equals%2A> devralınmış uygulama yansıma kitaplığını kullanır ve tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıların örnekleri karşılaştırmasını veya sıralamasını veya onları karma tablo anahtarları olarak kullanmasını bekleliyorsanız, değer türü <xref:System.Object.Equals%2A> uygulamalıdır. Programlama diliniz işleç aşırı yüklemesini destekliyorsa eşitlik ve eşitsizlik işleçleri de bir uygulama sağlamalısınız.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Object.Equals%2A> bir uygulama sağlayın. Mümkünse eşitlik işlecini uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Değer türünün örnekleri birbirleriyle karşılaştırılmayacak şekilde bu kuraldan bir uyarı bastırılmak güvenlidir.

## <a name="example-of-a-violation"></a>Ihlalin örneği

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, bu kuralı ihlal eden bir yapıyı (değer türü) gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Nasıl düzeltileceğini gösteren örnek

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, <xref:System.ValueType.Equals%2A?displayProperty=fullName> geçersiz kılarak ve eşitlik işleçleri (= =,! =) uygulayarak önceki ihlalin düzeltir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2224: Eşittir işlecini aşırı yükleyerek eşittiri geçersiz kılın](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: ValueType.Equals değerini geçersiz kılmada eşittir işlecini aşırı yükle](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Object.Equals%2A?displayProperty=fullName>
