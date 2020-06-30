---
title: 'CA1030: uygun yerlerde olayları kullanın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1313c5ee79a7a13d3eb937a3431b13ea393857d1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544527"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Uygun yerlerde olayları kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Ortak, korumalı veya özel bir yöntem adı aşağıdakilerden biriyle başlar:

- Eklenti

- RemoveOn

- Ateş

- Yükseltmek

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, normalde olaylar için kullanılan adlara sahip yöntemleri algılar. Olaylar gözlemci veya yayımla-abone ol tasarım modelini izler; bir nesnedeki durum değişikliği diğer nesnelere iletilmesi gerektiğinde kullanılırlar. Bir yöntem açıkça tanımlanmış bir durum değişikliğine yanıt olarak çağrılırsa, yöntemi bir olay işleyicisi tarafından çağrılmalıdır. Yöntemi direkt olarak çağırmak yerine olayları yükselterek çağıran nesneler.

 Bazı yaygın olay örnekleri, bir düğmeye tıklanması gibi bir kullanıcı eyleminin bir kod segmentinin yürütülmesine neden olduğu kullanıcı arabirimi uygulamalarında bulunur. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Olay modeli Kullanıcı arabirimleriyle sınırlı değildir; bir veya daha fazla nesnede durum değişikliklerini iletmelisiniz her yerde kullanılmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bir nesnenin durumu değiştiğinde yöntemi çağrılırsa, olay modelini kullanmak için tasarımı değiştirmeyi göz önünde bulundurmanız gerekir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yöntem olay modeliyle çalışmazsa bu kuraldan bir uyarı gizleyin [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .
