---
title: 'CA1059: Üyeler belirli somut türleri kullanıma sunmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4c105a1224c405d0be9d74ac6500c875df28604d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604040"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Üyeler belli somut türleri göstermemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünür bir üye belirli bir somut türdür veya parametrelerinden biri veya dönüş değeri aracılığıyla belirli somut türleri gösterir. Şu anda, bu kural aşağıdaki somut türlerin görünürlüğünü raporlar:

- @No__t_0 türetilmiş bir tür.

## <a name="rule-description"></a>Kural Tanımı
 Somut tür tam bir uygulamaya sahiptir ve bu nedenle oluşturulabilecek bir türdür. Üyenin yaygın olarak kullanımına izin vermek için somut türü önerilen arabirimle değiştirin. Bu, üyenin arabirimini uygulayan veya arabirimi uygulayan bir türün beklendiği her türlü türü kabul etmesine izin verir.

 Aşağıdaki tabloda hedeflenen somut türler ve bunların önerilen değiştirmeleri listelenmektedir.

|Somut tür|Başka|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Arabirimini kullanmak, üyeyi bir XML veri kaynağının belirli bir uygulamasından ayırır.|

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için somut türü önerilen arabirimle değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Somut tür tarafından sunulan belirli işlevler gerekliyse, bu kuraldan gelen bir iletiyi gizlemek güvenlidir.

## <a name="related-rules"></a>İlgili kurallar
 [CA1011: Temel türleri parametre olarak geçirmeyi düşünün](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
