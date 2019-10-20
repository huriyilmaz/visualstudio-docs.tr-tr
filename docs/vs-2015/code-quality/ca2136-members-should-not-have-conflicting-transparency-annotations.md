---
title: 'CA2136: Üyeler çakışan saydamlık ek açıklamalarını içermemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f2fbb856ff53552ab99dabd4f650e9fd7f62a088
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602975"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Üyeler çakışan saydamlık ek açıklamalarına sahip olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bu kural, bir tür üyesi üyenin kapsayıcısının güvenlik özniteliğiyle farklı bir saydamlığa sahip <xref:System.Security> güvenlik özniteliğiyle işaretlendiğinde ateşlenir.

## <a name="rule-description"></a>Kural Tanımı
 Saydamlık nitelikleri, geniş kapsam kodlu öğelerden daha küçük kapsamlı öğelere uygulanır. Geniş kapsamı ile kod öğelerinin saydamlık öznitelikleri ilk öğeden kapsayan kod öğelerinin saydam öznitelikleri önceliklidir. Örneğin, <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretlenmiş bir sınıf, <xref:System.Security.SecuritySafeCriticalAttribute> özniteliğiyle işaretlenmiş bir yöntemi içeremez.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu ihlalin giderilmesi için, alt kapsamına sahip kod öğesinden güvenlik özniteliğini kaldırın veya özniteliğini kapsayan kod öğesiyle aynı olacak şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan gelen uyarıları göstermez.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, bir yöntem <xref:System.Security.SecuritySafeCriticalAttribute> özniteliğiyle işaretlenir ve <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretlenmiş bir sınıfın üyesidir. Güvenlik güvenli özniteliği kaldırılmalıdır.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
