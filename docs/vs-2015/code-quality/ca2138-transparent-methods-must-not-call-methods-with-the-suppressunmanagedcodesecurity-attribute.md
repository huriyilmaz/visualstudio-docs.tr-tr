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
ms.openlocfilehash: 35cc152998b15a2fd4c4ff02e4730cdfae5366cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546503"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Saydam metotlar SuppressUnmanagedCodeSecurity özniteliğine sahip metotları çağırmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir güvenlik saydam yöntemi, özniteliğiyle işaretlenmiş bir yöntemi çağırır <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> .

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, örneğin, bir P/Invoke (Platform Invoke) çağrısını kullanarak, yerel koda doğrudan çağıran herhangi bir saydam yöntemde ateşlenir. Özniteliği ile işaretlenen P/Invoke ve COM birlikte çalışma yöntemleri, <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> çağırma yöntemine karşı gerçekleştirilen bir LinkDemand ile sonuçlanır. Güvenlik saydam kodu Linktaleplerini karşılayamadığından, kod aynı zamanda SuppressUnmanagedCodeSecurity özniteliğiyle işaretlenmiş yöntemleri veya SuppressUnmanagedCodeSecurity özniteliğiyle işaretlenmiş sınıf yöntemlerini çağıramaz. Yöntem başarısız olur veya talep tam talebe dönüştürülür.

 Bu kuralın ihlalleri <xref:System.MethodAccessException> , düzey 2 güvenlik saydamlığı modelinde bir öğesine ve <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> düzey 1 saydamlık modelinde için tam talebe yol açabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliğini kaldırın ve yöntemi <xref:System.Security.SecurityCriticalAttribute> veya özniteliğiyle işaretleyin <xref:System.Security.SecuritySafeCriticalAttribute> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
