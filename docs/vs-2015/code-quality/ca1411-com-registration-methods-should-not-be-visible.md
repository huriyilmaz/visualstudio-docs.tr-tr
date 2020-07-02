---
title: 'CA1411: COM kayıt yöntemleri görünür olmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f001a2bb4920ebfb3f5cff3745639bd346a0a920
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540147"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: COM kayıt metotları görünebilir olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ya da özniteliğiyle işaretlenmiş bir yöntem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> dışarıdan görünür.

## <a name="rule-description"></a>Kural Tanımı
 Bir derleme bileşen nesne modeli (COM) ile kaydettirilirse, derleme içindeki her bir COM görünebilir türü için kayıt defterine giriş eklenir. Ve öznitelikleri ile işaretlenen Yöntemler, <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> sırasıyla kayıt/kayıt silme <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> işlemlerine özgü Kullanıcı kodunu çalıştırmak için, kayıt ve kayıt silme işlemi sırasında çağrılır. Bu kod bu işlemlerin dışında çağrılmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, yönteminin erişilebilirliğini `private` veya `internal` ( `Friend` içinde) olarak değiştirin [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden iki yöntemi gösterir.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1410: COM kayıt metotları eşleşmelidir](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[DERLEMELERI COMRegasm.exe kaydetme](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [(derleme kayıt aracı)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
