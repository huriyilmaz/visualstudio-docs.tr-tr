---
title: 'CA2140: saydam kod güvenlik kritik öğelerine başvurulmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6f11125f43fd06b0442d1c40cbd4da41e346fd1d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546464"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Saydam kod güvenlik kritik nesnelerine başvurmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Saydam bir yöntem:

- Güvenlik açısından kritik güvenlik özel durum türünü işler

- , güvenlik açısından kritik tür olarak işaretlenmiş bir parametreye sahiptir

- kritik güvenlik kısıtlamalarına sahip genel bir parametreye sahiptir

- , güvenlik açısından kritik bir tür yerel değişkenine sahiptir

- Güvenlik açısından kritik olarak işaretlenmiş bir türe başvurur

- Güvenlik açısından kritik olarak işaretlenen bir yöntemi çağırır

- Güvenlik açısından kritik olarak işaretlenmiş bir alana başvurur

- Güvenlik açısından kritik olarak işaretlenen bir tür döndürür

## <a name="rule-description"></a>Kural Tanımı
 Özniteliğiyle işaretlenmiş bir kod öğesi <xref:System.Security.SecurityCriticalAttribute> güvenlik açısından kritik ' dir. Saydam bir yöntem, kritik güvenlik öğesini kullanamaz. Saydam bir tür, bir güvenlik kritik türünü kullanmayı denerse, <xref:System.TypeAccessException> <xref:System.MethodAccessException> veya <xref:System.FieldAccessException> oluşturulur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için aşağıdakilerden birini yapın:

- Güvenlik açısından kritik kodu kullanan kod öğesini <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretle

     \-veya

- <xref:System.Security.SecurityCriticalAttribute>Özniteliği güvenlik açısından kritik olarak işaretlenen kod öğelerinden kaldırın ve bunun yerine bunları <xref:System.Security.SecuritySafeCriticalAttribute> veya <xref:System.Security.SecurityTransparentAttribute> özniteliğiyle işaretleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örneklerde, saydam bir yöntem güvenlik açısından kritik Genel koleksiyona, güvenlik açısından kritik alana ve güvenlik açısından kritik bir yönteme başvurmasına çalışır.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
