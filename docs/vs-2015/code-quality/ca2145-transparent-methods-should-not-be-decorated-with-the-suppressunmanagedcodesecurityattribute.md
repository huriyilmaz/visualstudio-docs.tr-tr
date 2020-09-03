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
ms.openlocfilehash: d5eb16130aef42abcf9fddf533d0253864a75114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546412"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Saydam metotlar SuppressUnmanagedCodeSecurityAttribute ile donatılmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Saydam bir yöntem, yöntemiyle işaretlenmiş bir yöntem <xref:System.Security.SecuritySafeCriticalAttribute> veya bir yöntemi içeren bir tür, <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliğiyle işaretlenir.

## <a name="rule-description"></a>Kural Tanımı
 Özniteliği ile donatılmış Yöntemler, <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> onu çağıran herhangi bir yönteme yerleştirilmiş bir örtülü LinkDemand 'a sahiptir. Bu LinkDemand, çağıran kodun kritik güvenlikli olmasını gerektirir. SuppressUnmanagedCodeSecurity kullanan yöntemi <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretlemek, bu gereksinimi metodun çağıranları için daha belirgin hale getirir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için yöntemini veya türünü <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Yorumlar
