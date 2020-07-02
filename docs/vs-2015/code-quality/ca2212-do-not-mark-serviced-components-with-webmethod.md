---
title: 'CA2212: hizmet verilen bileşenleri WebMethod ile işaretlemeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c707fef5562b932b6232300131f6e6e6efef6a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534569"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Servis verilen bileşenleri WebMethod ile işaretlemeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Öğesinden devralan bir tür yöntemi <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> ile işaretlenir <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Web.Services.WebMethodAttribute>ASP.NET kullanılarak oluşturulmuş bir XML Web hizmeti içindeki yöntemler için geçerlidir; yöntemi, uzak Web istemcilerinden çağrılabilir hale getirir. Yöntem ve sınıf ortak olmalıdır ve bir ASP.NET Web uygulamasında yürütmelidir. <xref:System.EnterpriseServices.ServicedComponent>türler COM+ uygulamaları tarafından barındırılır ve COM+ Hizmetleri kullanılabilir. <xref:System.Web.Services.WebMethodAttribute><xref:System.EnterpriseServices.ServicedComponent>, aynı senaryolar için düşünülmediği için türlere uygulanmaz. Özellikle, özniteliği <xref:System.EnterpriseServices.ServicedComponent> yöntemine eklemek yöntemi uzak Web istemcilerinden çağrılabilir hale getirir. <xref:System.Web.Services.WebMethodAttribute>Ve bir <xref:System.EnterpriseServices.ServicedComponent> yönteminde bağlam ve işlem akışı için çakışan davranışlar ve gereksinimler olduğundan, metodun davranışı bazı senaryolarda yanlış olacaktır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, yönteminden özniteliğini kaldırın <xref:System.EnterpriseServices.ServicedComponent> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Bu öğelerin birleştirilmesinin doğru olduğu bir senaryo yoktur.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
