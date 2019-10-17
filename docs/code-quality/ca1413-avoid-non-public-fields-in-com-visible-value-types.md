---
title: 'CA1413: COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d47a7ff2633b94de73435168136060e741080de7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444186"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Kategori|Microsoft. çalışabilirliği|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Özellikle bileşen nesne modeli (COM) tarafından görünür olarak işaretlenen bir değer türü, ortak bir örnek alanı bildirir.

## <a name="rule-description"></a>Kural açıklaması
COM-görünür değer türlerinin ortak olmayan örnek alanları COM istemcilerine görünürdür. Açığa çıkmamalıdır veya istenmeyen bir tasarım ya da güvenlik etkisine sahip olacak bilgiler için alanın içeriğini gözden geçirin.

Varsayılan olarak, tüm ortak değer türleri COM olarak görünür. Ancak, hatalı pozitif sonuçları azaltmak için bu kural, türün COM görünürlüğünü açık bir şekilde ifade etmek için gereklidir. İçeren derleme <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ' ı `false` ' e ayarlanmış olarak işaretlenmelidir ve tür `true` ' e ayarlanmış @no__t şekilde işaretlenmelidir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kuralın ihlalini onarmak ve alanı gizli tutmaya devam etmek için, değer türünü bir başvuru türü olarak değiştirin veya <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliğini türden kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Alanın genel pozlaması kabul edilebilir ise, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir.

[!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
[!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>İlgili kurallar
[CA1407: COM görünebilir türler içinde statik üyelerden kaçının](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Derlemeleri ComVisibleAttribute ile işaretleyin](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kod ile Birlikte Çalışma](/dotnet/framework/interop/index)
- [Birlikte Çalışma için .NET Türlerini Niteleme](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
