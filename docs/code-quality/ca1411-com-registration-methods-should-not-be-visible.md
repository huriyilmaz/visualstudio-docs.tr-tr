---
title: 'CA1411: COM kayıt yöntemleri görünebilir olmamalıdır'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b39e16b2a94a22582b9f369e647676541fa4220d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440178"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: COM kayıt yöntemleri görünebilir olmamalıdır

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategori|Microsoft. çalışabilirliği|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

@No__t-0 veya <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> özniteliğiyle işaretlenmiş bir yöntem dışarıdan görünür.

## <a name="rule-description"></a>Kural açıklaması
Bir derleme bileşen nesne modeli (COM) ile kaydettirilirse, derleme içindeki her bir COM görünebilir türü için kayıt defterine giriş eklenir. @No__t-0 ve <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> öznitelikleri ile işaretlenen Yöntemler sırasıyla, bu türlerin kaydına/kaydının kaydedilmesine özgü Kullanıcı kodu çalıştırmak için, kayıt ve kayıt silme işlemlerinde çağrılır. Bu kod bu işlemlerin dışında çağrılmamalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için, yönteminin erişilebilirliğini `private` veya `internal` (`Friend` [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) olarak değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
Aşağıdaki örnek, kuralı ihlal eden iki yöntemi gösterir.

[!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>İlgili kurallar
[CA1410: COM kayıt yöntemleri eşleşmelidir](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Bütünleştirilmiş Kodları COM ile Kaydetme](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (Derleme Kayıt Aracı)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)
