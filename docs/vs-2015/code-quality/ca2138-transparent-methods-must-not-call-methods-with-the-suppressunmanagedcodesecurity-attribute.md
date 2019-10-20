---
title: 'CA2138: Saydam yöntemler SuppressUnmanagedCodeSecurity özniteliğine sahip yöntemleri çağırmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 65e00d319bff3bbfd3c441c6b60ed8a703e69251
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654810"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Saydam yöntemler SuppressUnmanagedCodeSecurity özniteliğine sahip yöntemleri çağırmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir güvenlik saydam yöntemi, <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliğiyle işaretlenmiş bir yöntemi çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, örneğin, bir P/Invoke (Platform Invoke) çağrısını kullanarak, yerel koda doğrudan çağıran herhangi bir saydam yöntemde ateşlenir. @No__t_0 özniteliğiyle işaretlenen P/Invoke ve COM birlikte çalışma yöntemleri, çağırma yöntemine karşı gerçekleştirilen bir LinkDemand ile sonuçlanır. Güvenlik saydam kodu Linktaleplerini karşılayamadığından, kod aynı zamanda SuppressUnmanagedCodeSecurity özniteliğiyle işaretlenmiş yöntemleri veya SuppressUnmanagedCodeSecurity özniteliğiyle işaretlenmiş sınıf yöntemlerini çağıramaz. Yöntem başarısız olur veya talep tam talebe dönüştürülür.

 Bu kuralın ihlalleri, düzey 2 güvenlik saydamlığı modelindeki bir <xref:System.MethodAccessException> ve düzey 1 saydamlık modelinde <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> için bir tam talebe yol açabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliğini kaldırın ve yöntemi <xref:System.Security.SecurityCriticalAttribute> veya <xref:System.Security.SecuritySafeCriticalAttribute> özniteliğiyle işaretleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
