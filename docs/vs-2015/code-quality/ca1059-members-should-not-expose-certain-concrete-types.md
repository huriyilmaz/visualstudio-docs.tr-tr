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
ms.openlocfilehash: 792426615dd78241ade1d38a24ec1f4d5702cede
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545385"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Üyeler belirli somut türleri kullanıma sunmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Dışarıdan görünür bir üye belirli bir somut türdür veya parametrelerinden biri veya dönüş değeri aracılığıyla belirli somut türleri gösterir. Şu anda, bu kural aşağıdaki somut türlerin görünürlüğünü raporlar:

- Öğesinden türetilmiş bir tür <xref:System.Xml.XmlNode?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 Somut tür tam bir uygulamaya sahiptir ve bu nedenle oluşturulabilecek bir türdür. Üyenin yaygın olarak kullanımına izin vermek için somut türü önerilen arabirimle değiştirin. Bu, üyenin arabirimini uygulayan veya arabirimi uygulayan bir türün beklendiği her türlü türü kabul etmesine izin verir.

 Aşağıdaki tabloda hedeflenen somut türler ve bunların önerilen değiştirmeleri listelenmektedir.

|Somut tür|Değiştirme|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Arabirimini kullanmak, üyeyi bir XML veri kaynağının belirli bir uygulamasından ayırır.|

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için somut türü önerilen arabirimle değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Somut tür tarafından sunulan belirli işlevler gerekliyse, bu kuraldan gelen bir iletiyi gizlemek güvenlidir.

## <a name="related-rules"></a>İlgili kurallar
 [CA1011: Parametre olarak temel türleri geçmeyi düşünün](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
