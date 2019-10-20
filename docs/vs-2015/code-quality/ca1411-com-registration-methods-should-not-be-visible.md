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
ms.openlocfilehash: f3ddd2c90d23884bd08a90560dcc5ed0fe700aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652722"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: COM kayıt yöntemleri görünebilir olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 @No__t_0 veya <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> özniteliğiyle işaretlenmiş bir yöntem dışarıdan görünür.

## <a name="rule-description"></a>Kural Tanımı
 Bir derleme bileşen nesne modeli (COM) ile kaydettirilirse, derleme içindeki her bir COM görünebilir türü için kayıt defterine giriş eklenir. @No__t_0 ve <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> öznitelikleriyle işaretlenen Yöntemler sırasıyla, bu türlerin kaydına/kayıt kaydına özgü Kullanıcı kodu çalıştırmak için, kayıt ve kayıt silme işlemlerinde çağrılır. Bu kod bu işlemlerin dışında çağrılmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, yönteminin erişilebilirliğini `private` veya `internal` ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] içinde `Friend`) olarak değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden iki yöntemi gösterir.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1410: COM kayıt yöntemleri eşleşmelidir](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Ayrıca Bkz.
 COM [Regasm. exe (derleme kayıt aracı)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb) [ile derlemeleri kaydetme](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
