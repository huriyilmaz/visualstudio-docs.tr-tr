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
ms.openlocfilehash: 81eaf2735869668b86ca8879478e3d76d77a2811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662304"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Birkaç türü olan ad alanlarından kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Genel ad alanı dışındaki bir ad alanı beşten az tür içerir.

## <a name="rule-description"></a>Kural Tanımı
 Ad alanlarınızın her birinin mantıksal bir kuruluşa sahip olduğundan ve türleri çok seyrek doldurulmuş bir ad alanına koymak için geçerli bir nedenin bulunduğundan emin olun. Ad alanları Çoğu senaryoda birlikte kullanılan türleri içermelidir. Uygulamaları birbirini dışlıyor olduğunda türler ayrı ad alanlarında bulunmalıdır. Örneğin, <xref:System.Web.UI> ad alanı Web uygulamalarında kullanılan türleri içerir ve <xref:System.Windows.Forms> ad alanı [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] tabanlı uygulamalarda kullanılan türleri içerir. Her iki ad alanı da Kullanıcı arabiriminin yönlerini denetleyen türlere sahip olsa da, bu türler aynı uygulamada kullanılmak üzere tasarlanmamıştır. Bu nedenle, ayrı ad alanlarında bulunur. Bir özelliğin bulunabilirliği arttığı için dikkatli bir ad alanı organizasyonu da yararlı olabilir. Ad alanı hiyerarşisini inceleyerek, kitaplık tüketicileri bir özelliği uygulayan türleri bulabilmelidir.

> [!NOTE]
> Tasarım zamanı türleri ve izinleri, bu kılavuza uyum sağlamak için diğer ad alanlarıyla birleştirilmemelidir. Bu türler, ana ad alanlarınızın altındaki kendi ad alanlarına aittir ve ad alanları sırasıyla `.Design` ve `.Permissions` ile bitmelidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, yalnızca birkaç tür içeren ad alanlarını tek bir ad alanında birleştirmeyi deneyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Ad alanı diğer ad boşluklarınızın türleriyle kullanılan türler içermiyorsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.
