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
ms.openlocfilehash: cbb68855832e84150b81c8a8a6fde47bf9433edc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547712"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Düzey 2 derlemeler LinkDemands içermemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Sınıf veya sınıf üyesi, <xref:System.Security.Permissions.SecurityAction> düzey 2 güvenliği kullanan bir uygulamada bir kullanıyor.

## <a name="rule-description"></a>Kural Tanımı
 LinkDemands, düzey 2 güvenlik kural kümesinden kaldırılmıştır. Tam zamanında (JıT) derleme zamanında güvenliği zorlamak için Linktaleplerini kullanmak yerine, yöntemleri, türleri ve alanları <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretleyin.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için öğesini kaldırın <xref:System.Security.Permissions.SecurityAction> ve özniteliği ile türü veya üyeyi işaretleyin <xref:System.Security.SecurityCriticalAttribute> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, öğesinin <xref:System.Security.Permissions.SecurityAction> kaldırılması ve özniteliği ile işaretlenmiş yöntemi olması gerekir <xref:System.Security.SecurityCriticalAttribute> .

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]
