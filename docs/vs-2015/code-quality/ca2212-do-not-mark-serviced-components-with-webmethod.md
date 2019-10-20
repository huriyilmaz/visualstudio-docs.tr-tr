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
ms.openlocfilehash: 2ee166f8bbc14e66968cd4f7c265331854905ac9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662941"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Servis verilen bileşenleri WebMethod ile işaretlemeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 @No__t_0 devralan bir tür yöntemi <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> ile işaretlenir.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Web.Services.WebMethodAttribute>, ASP.NET kullanılarak oluşturulmuş bir XML Web hizmeti içindeki yöntemlere uygulanır; yöntemi, uzak Web istemcilerinden çağrılabilir hale getirir. Yöntem ve sınıf ortak olmalıdır ve bir ASP.NET Web uygulamasında yürütmelidir. <xref:System.EnterpriseServices.ServicedComponent> türleri COM+ uygulamaları tarafından barındırılır ve COM+ hizmetlerini kullanabilir. <xref:System.Web.Services.WebMethodAttribute> <xref:System.EnterpriseServices.ServicedComponent> türlerine uygulanmaz çünkü bunlar aynı senaryolara yöneliktir. Özellikle, <xref:System.EnterpriseServices.ServicedComponent> metoduna özniteliği eklemek, yöntemi uzak Web istemcilerinden çağrılabilir hale getirir. @No__t_0 ve bir <xref:System.EnterpriseServices.ServicedComponent> yönteminde içerik ve işlem akışı için çakışan davranışlar ve gereksinimler olduğundan, metodun davranışı bazı senaryolarda yanlış olacaktır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.EnterpriseServices.ServicedComponent> yönteminden özniteliği kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Bu öğelerin birleştirilmesinin doğru olduğu bir senaryo yoktur.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName><xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
