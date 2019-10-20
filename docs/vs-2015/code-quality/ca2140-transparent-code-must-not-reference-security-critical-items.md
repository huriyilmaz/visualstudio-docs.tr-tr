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
ms.openlocfilehash: 5c3e624e4210e59406fd1d5955cd37c2e83ed79a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602861"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Saydam kod güvenlik kritik nesnelerine başvurmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
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
 @No__t_0 özniteliğiyle işaretlenmiş bir kod öğesi güvenlik açısından kritiktir. Saydam bir yöntem, kritik güvenlik öğesini kullanamaz. Saydam bir tür, <xref:System.TypeAccessException>, <xref:System.MethodAccessException> veya <xref:System.FieldAccessException> olan güvenlik açısından kritik bir tür kullanmayı denerse.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için aşağıdakilerden birini yapın:

- Güvenlik kritik kodunu kullanan kod öğesini <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretleyin

     \- veya-

- @No__t_0 özniteliğini güvenlik açısından kritik olarak işaretlenen kod öğelerinden kaldırın ve bunun yerine bunları <xref:System.Security.SecuritySafeCriticalAttribute> veya <xref:System.Security.SecurityTransparentAttribute> özniteliğiyle işaretleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örneklerde, saydam bir yöntem güvenlik açısından kritik Genel koleksiyona, güvenlik açısından kritik alana ve güvenlik açısından kritik bir yönteme başvurmasına çalışır.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Security.SecurityTransparentAttribute><xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
