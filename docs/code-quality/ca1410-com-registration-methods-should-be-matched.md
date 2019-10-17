---
title: 'CA1410: COM kayıt yöntemleri eşleşmelidir'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c7c7c20ece08bc5167887727e423a3f7cdf7ee19
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440196"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: COM kayıt yöntemleri eşleşmelidir

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategori|Microsoft. çalışabilirliği|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep

Bir tür, <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> özniteliğiyle işaretlenmiş ancak <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> özniteliğiyle işaretlenmiş bir yöntemi bildirmeyen veya tam tersi bir yöntem bildirir.

## <a name="rule-description"></a>Kural açıklaması

Bileşen nesne modeli (COM) istemcilerinin bir .NET türü oluşturması için öncelikle türün kaydedilmesi gerekir. Varsa, Kullanıcı tarafından belirtilen kodu çalıştırmak için kayıt işlemi sırasında <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> özniteliğiyle işaretlenmiş bir yöntem çağrılır. Kayıt yönteminin işlemlerini tersine çevirmek için, <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> özniteliğiyle işaretlenen karşılık gelen bir yöntem, kayıt silme işlemi sırasında çağrılır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için ilgili kayıt veya kayıt silme yöntemini ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir. Açıklamalı kod, ihlalin düzeltmesini gösterir.

[!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>İlgili kurallar

[CA1411: COM kayıt yöntemleri görünebilir olmamalıdır](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Derlemeleri COM ile kaydetme](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Derleme Kayıt Aracı)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)
