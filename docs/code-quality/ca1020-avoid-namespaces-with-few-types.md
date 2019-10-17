---
title: 'CA1020: Birkaç türü olan ad alanlarından kaçının'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d13f4e9308e77cc723703394a4295273b5facef1
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441634"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Birkaç türü olan ad alanlarından kaçının

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategori|Microsoft. Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Genel ad alanı dışındaki bir ad alanı beşten az tür içerir.

## <a name="rule-description"></a>Kural açıklaması

Ad alanlarınızın her birinin mantıksal bir kuruluşa sahip olduğundan ve türleri çok seyrek doldurulmuş bir ad alanına koymak için geçerli bir nedenin bulunduğundan emin olun. Ad alanları Çoğu senaryoda birlikte kullanılan türleri içermelidir. Uygulamaları birbirini dışlıyor olduğunda türler ayrı ad alanlarında bulunmalıdır. Örneğin, <xref:System.Web.UI> ad alanı Web uygulamalarında kullanılan türleri içerir ve <xref:System.Windows.Forms> ad alanı @no__t -2 tabanlı uygulamalarda kullanılan türleri içerir. Her iki ad alanı da Kullanıcı arabiriminin yönlerini denetleyen türlere sahip olsa da, bu türler aynı uygulamada kullanılmak üzere tasarlanmamıştır. Bu nedenle, ayrı ad alanlarında bulunur. Bir özelliğin bulunabilirliği arttığı için dikkatli bir ad alanı organizasyonu da yararlı olabilir. Ad alanı hiyerarşisini inceleyerek, kitaplık tüketicileri bir özelliği uygulayan türleri bulabilmelidir.

> [!NOTE]
> Tasarım zamanı türleri ve izinleri, bu kılavuza uyum sağlamak için diğer ad alanlarıyla birleştirilmemelidir. Bu türler, ana ad alanlarınızın altındaki kendi ad alanlarına aittir ve ad alanları sırasıyla `.Design` ve `.Permissions` ile bitmelidir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kuralın ihlalini onarmak için, yalnızca birkaç tür içeren ad alanlarını tek bir ad alanında birleştirmeyi deneyin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Ad alanı diğer ad boşluklarınızın türleriyle kullanılan türler içermiyorsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.
