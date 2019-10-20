---
title: 'CA2231: ValueType. Equals geçersiz kılınırken aşırı yükleme işleci eşittir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 308c970eb21faa7e725559d0451706899b62fd19
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662813"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: ValueType.Equals değerini geçersiz kılmada eşittir işlecini aşırı yükle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Değer türü <xref:System.Object.Equals%2A?displayProperty=fullName> geçersiz kılar, ancak eşitlik işlecini uygulamaz.

## <a name="rule-description"></a>Kural Tanımı
 Çoğu programlama dilinde, değer türleri için eşitlik işlecinin (= =) varsayılan bir uygulamasý yoktur. Programlama diliniz operatör aşırı yüklerini destekliyorsa, eşitlik işlecini uygulamayı düşünmelisiniz. Davranışı <xref:System.Object.Equals%2A> özdeş olmalıdır.

 Eşitlik işlecinin aşırı yüklenmiş bir uygulamasında varsayılan eşitlik işlecini kullanamazsınız. Bunun yapılması, yığın taşmasına neden olur. Eşitlik işlecini uygulamak için uygulamanızdaki Object. Equals yöntemini kullanın. Örneğin:

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için eşitlik işlecini uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir; Ancak, mümkünse eşitlik operatörünü sağlamanızı öneririz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü tanımlar.

 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode/cs/FxCop.Usage.EqualsGetHashCode.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1046: Başvuru türlerinde eşittir işleçlerini aşırı yüklemeyin](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Eşittir işlecini aşırı yükleyerek eşittiri geçersiz kılın](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Object.Equals%2A?displayProperty=fullName>
