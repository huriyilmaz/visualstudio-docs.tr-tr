---
title: 'CA2141: Saydam yöntemler bağlantı taleplerini karşılamamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5e8e88401a6fbe3ab7dc635dadee9215b049b2d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602840"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:Transparent yöntemleri LinkDemands'i karşılamamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir güvenlik saydam yöntemi, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) özniteliğiyle işaretlenmemiş bir derlemede bir yöntemi çağırır veya bir güvenlik saydam yöntemi bir tür ya da yöntem için <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` karşılar.

## <a name="rule-description"></a>Kural Tanımı
 LinkDemand 'in yerine bir güvenlik duyarlı işlem, yanlışlıkla ayrıcalık yükselmesine neden olabilir. Güvenliği saydam kod, güvenlik açısından kritik kod ile aynı güvenlik denetimi gereksinimlerine tabi olmadığından, bağlantı taleplerini karşılamamalıdır. Güvenlik kuralı kümesi düzey 1 derlemelerindeki saydam Yöntemler, tüm bağlantı taleplerinin çalışma zamanında tam taleplerine dönüştürülmesini sağlar ve bu da performans sorunlarına neden olabilir. Güvenlik kuralı set Level 2 derlemeleri içinde, bir LinkDemand ile yararlanmaya çalıştıklarında, saydam Yöntemler tam zamanında (JıT) derleyicide derlenmeyecektir.

 2\. düzey güvenliği güvenlik düzeyine sahip olan derlemelerde, bir bağlantı talebini karşılamak için bir güvenlik saydam yöntemi veya APTCA olmayan bir derlemede bir yöntemi çağırmak, bir <xref:System.MethodAccessException> oluşturur; Düzey 1 derlemelerde LinkDemand tam talep haline gelir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, erişim yöntemini <xref:System.Security.SecurityCriticalAttribute> veya <xref:System.Security.SecuritySafeCriticalAttribute> özniteliğiyle işaretleyin ya da bağlantı talebini erişilen yöntemden kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Bu örnekte, saydam bir yöntem LinkDemand içeren bir yöntemi çağırmaya çalışır. Bu kural, bu kodda harekete geçmeyecektir.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
