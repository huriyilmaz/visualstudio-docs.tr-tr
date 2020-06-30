---
title: 'CA2143: Saydam yöntemler güvenlik taleplerini kullanmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca8f049da83b99da7d36ebf74e756dd95f738d64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546477"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Saydam metotlar güvenlik taleplerini kullanmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir Tranparent türü ya da yöntemi bildirimli olarak bir talep ile işaretlenir ya da yöntemi <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> yöntemini çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Saydam güvenlik kodu, bir işlemin güvenlik doğrulaması için sorumlu olmamalıdır ve bu nedenle izin talep edilmemelidir. Saydam güvenlik kodu, güvenlik kararını vermek için tüm talepleri kullanmalıdır ve güvenli kritik kod, saydam koda tüm talepleri vermek için güvenmemelidir. Güvenlik istekleri gerçekleştiren tüm kodlar, bunun yerine güvenli kritik öneme sahip olmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Genel olarak, bu kural ihlalini onarmak için yöntemi <xref:System.Security.SecuritySafeCriticalAttribute> özniteliğiyle işaretleyin. Ayrıca talebi de kaldırabilirsiniz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Bir saydam Yöntem bildirime dayalı bir güvenlik talebi yaptığından, aşağıdaki kodda kural dosyaları.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [CA2142: Saydam kod LinkDemands ile korunmamalıdır](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
