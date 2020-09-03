---
title: 'CA1020: birkaç türde ad alanlarını önleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ddd69c62eb4d6b818410a588967c1e23f164f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546737"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Az tür içeren ad alanlarından kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Genel ad alanı dışındaki bir ad alanı beşten az tür içerir.

## <a name="rule-description"></a>Kural Tanımı
 Ad alanlarınızın her birinin mantıksal bir kuruluşa sahip olduğundan ve türleri çok seyrek doldurulmuş bir ad alanına koymak için geçerli bir nedenin bulunduğundan emin olun. Ad alanları Çoğu senaryoda birlikte kullanılan türleri içermelidir. Uygulamaları birbirini dışlıyor olduğunda türler ayrı ad alanlarında bulunmalıdır. Örneğin, <xref:System.Web.UI> ad alanı Web uygulamalarında kullanılan türleri içerir ve <xref:System.Windows.Forms> ad alanı, tabanlı uygulamalarda kullanılan türleri içerir [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] . Her iki ad alanı da Kullanıcı arabiriminin yönlerini denetleyen türlere sahip olsa da, bu türler aynı uygulamada kullanılmak üzere tasarlanmamıştır. Bu nedenle, ayrı ad alanlarında bulunur. Bir özelliğin bulunabilirliği arttığı için dikkatli bir ad alanı organizasyonu da yararlı olabilir. Ad alanı hiyerarşisini inceleyerek, kitaplık tüketicileri bir özelliği uygulayan türleri bulabilmelidir.

> [!NOTE]
> Tasarım zamanı türleri ve izinleri, bu kılavuza uyum sağlamak için diğer ad alanlarıyla birleştirilmemelidir. Bu türler, ana ad alanlarınızın altındaki kendi ad alanlarına aittir ve ad alanları `.Design` sırasıyla ve ile bitmelidir `.Permissions` .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, yalnızca birkaç tür içeren ad alanlarını tek bir ad alanında birleştirmeyi deneyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Ad alanı diğer ad boşluklarınızın türleriyle kullanılan türler içermiyorsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.
