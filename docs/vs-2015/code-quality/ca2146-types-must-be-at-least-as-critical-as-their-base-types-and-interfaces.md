---
title: 'CA2146: türler en az temel türleri ve arabirimleri kadar kritik olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ab621ade120a257508eddbf9527f674b5fda8748
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610183"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Türler en az kendi taban türleri ve arabirimleri kadar kritik olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Typesmusbeatliastakaralama Ticalasbasetypes|
|CheckId|CA2146|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Saydam bir tür, <xref:System.Security.SecuritySafeCriticalAttribute> veya <xref:System.Security.SecurityCriticalAttribute> ile işaretlenmiş bir türden türetilir veya <xref:System.Security.SecuritySafeCriticalAttribute> özniteliğiyle işaretlenmiş bir tür <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretlenmiş bir türden türetilir.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, kendi temel türü kadar kritik olmayan saydam güvenlik özniteliğine sahip bir tür türetildiğinde veya arabirim uygulandığında tetiklenir. Yalnızca kritik türler, kritik temel türlerden veya kritik arabirimleri uygulayanlardan türeyebilir ve sadece kritik ya da kritik güvenli türler, kritik güvenli temel türler veya kritik güvenli arabirim uygulamalarından türeyebilir. Düzey 2 saydamlığının içindeki bu kuralın ihlalleri, türetilmiş tür için bir <xref:System.TypeLoadException> ile sonuçlanır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu ihlalin giderilmesi için, türetilmiş veya uygulama türünü, en az temel tür veya arabirim olarak kritik olan bir saydamlık özniteliğiyle işaretleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]
