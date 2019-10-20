---
title: Öğeler (XElement dinamik özelliği)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d92e9ebd1e5be9f3535dcac136bb46ba33975f0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637316"
---
# <a name="elements-xelement-dynamic-property"></a>Öğeler (XElement dinamik özelliği)

Belirtilen genişletilmiş adla eşleşen geçerli öğenin alt öğelerini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Sözdizimi

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri

@No__t_0 türünde bir Dizin Oluşturucu. Bu Dizin Oluşturucu, istenen alt öğelerin genişletilmiş adını alır ve bir <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` koleksiyonundaki eşleşen alt öğeleri döndürür.

## <a name="remarks"></a>Açıklamalar

Bu özellik <xref:System.Xml.Linq.XContainer> sınıfının <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> yöntemi ile eşdeğerdir.

Döndürülen koleksiyondaki öğeler XML kaynak belgesi sıratümcesinde.

Bu özellik ertelenmiş yürütmeyi kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [XElement sınıfı dinamik özellikleri](../designers/attribute-xelement-dynamic-property.md)
- [Öğe](../designers/element-xelement-dynamic-property.md)
- [Alt Öğeler](../designers/descendants-xelement-dynamic-property.md)