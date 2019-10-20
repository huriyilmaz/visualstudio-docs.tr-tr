---
title: Alt öğeler (XElement dinamik özelliği)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fab6b90489624955ddd567492d12f54d8de2686f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637340"
---
# <a name="descendants-xelement-dynamic-property"></a>Alt öğeler (XElement dinamik özelliği)

Belirtilen genişletilmiş adla eşleşen geçerli öğenin tüm alt öğelerini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Sözdizimi

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri

@No__t_0 türünde bir Dizin Oluşturucu. Bu Dizin Oluşturucu belirtilen alt öğelerin genişletilmiş adını alır ve bir <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` koleksiyonundaki eşleşen alt öğeleri döndürür.

## <a name="remarks"></a>Açıklamalar

Bu özellik <xref:System.Xml.Linq.XContainer> sınıfının <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> yöntemi ile eşdeğerdir.

Döndürülen koleksiyondaki öğeler XML kaynak belgesi sıratümcesinde.

Bu özellik ertelenmiş yürütmeyi kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [XElement sınıfı dinamik özellikleri](../designers/attribute-xelement-dynamic-property.md)
- [Elements](../designers/elements-xelement-dynamic-property.md)