---
title: 'CA2135: düzey 2 derlemeleri Linktaleplerini içermemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1248ac41a757ba2fc26ef0659c0f93ee325bc605
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602941"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Düzey 2 derlemeler LinkDemands içermemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir sınıf veya sınıf üyesi, düzey 2 güvenliği kullanan bir uygulamada <xref:System.Security.Permissions.SecurityAction> kullanıyor.

## <a name="rule-description"></a>Kural Tanımı
 LinkDemands, düzey 2 güvenlik kural kümesinden kaldırılmıştır. Tam zamanında (JıT) derleme zamanında güvenliği zorlamak için Linktaleplerini kullanmak yerine, yöntemleri, türleri ve alanları <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretleyin.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Security.Permissions.SecurityAction> ' ı kaldırın ve türü veya üyeyi <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte <xref:System.Security.Permissions.SecurityAction> ' ın kaldırılması ve yönteminin <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretlenmiş olması gerekir.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]
