---
title: 'CA2145: Saydam yöntemler SuppressUnmanagedCodeSecurityAttribute ile birlikte tasarlanmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6bffa680fa39014ffa96feec997b5eca63ee08ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610218"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Saydam yöntemler SuppressUnmanagedCodeSecurityAttribute ile donatılmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Saydam bir yöntem, <xref:System.Security.SecuritySafeCriticalAttribute> yöntemiyle işaretlenmiş bir yöntem ya da bir yöntemi içeren bir tür <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliğiyle işaretlenir.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 özniteliğiyle donatılmış Yöntemler, onu çağıran herhangi bir yönteme yerleştirilmiş bir örtülü LinkDemand 'a sahiptir. Bu LinkDemand, çağıran kodun kritik güvenlikli olmasını gerektirir. SuppressUnmanagedCodeSecurity kullanan yöntemi <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretlemek, bu gereksinimi, metodun çağıranları için daha belirgin hale getirir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için yöntemi veya türü <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Açıklamalar
