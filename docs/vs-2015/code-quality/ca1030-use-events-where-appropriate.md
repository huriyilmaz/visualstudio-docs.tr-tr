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
ms.openlocfilehash: 7ab3a576b5014799e470260567a4942b5c3ef9de
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661916"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Uygun yerlerde olaylar kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Ortak, korumalı veya özel bir yöntem adı aşağıdakilerden biriyle başlar:

- Eklenti

- RemoveOn

- Ateş

- Yükseltmek

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, normalde olaylar için kullanılan adlara sahip yöntemleri algılar. Olaylar gözlemci veya yayımla-abone ol tasarım modelini izler; bir nesnedeki durum değişikliği diğer nesnelere iletilmesi gerektiğinde kullanılırlar. Bir yöntem açıkça tanımlanmış bir durum değişikliğine yanıt olarak çağrılırsa, yöntemi bir olay işleyicisi tarafından çağrılmalıdır. Yöntemi direkt olarak çağırmak yerine olayları yükselterek çağıran nesneler.

 Bazı yaygın olay örnekleri, bir düğmeye tıklanması gibi bir kullanıcı eyleminin bir kod segmentinin yürütülmesine neden olduğu kullanıcı arabirimi uygulamalarında bulunur. @No__t_0 olay modeli Kullanıcı arabirimleriyle sınırlı değildir; durum değişikliklerini bir veya daha fazla nesnede iletmelisiniz her yerde kullanılmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bir nesnenin durumu değiştiğinde yöntemi çağrılırsa, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] olay modelini kullanmak için tasarımı değiştirmeyi göz önünde bulundurmanız gerekir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yöntem [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] olay modeliyle çalışmazsa bu kuraldan bir uyarı gizleyin.
