---
title: XML (XElement dinamik özelliği)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c93aaf3b43a930fe88020738460ec131972a205a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633517"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (XElement dinamik özelliği)

Öğenin biçimlendirilmemiş XML içeriğini alır.

## <a name="syntax"></a>Sözdizimi

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri

Öğenin biçimlendirilmemiş XML içeriğini temsil eden bir <xref:System.String>.

## <a name="remarks"></a>Açıklamalar

Bu özellik, `SaveOptions` parametresi <xref:System.Xml.Linq.SaveOptions> olarak ayarlanan <xref:System.Xml.Linq.XNode?displayProperty=fullName> sınıfının <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> yöntemi ile eşdeğerdir.

## <a name="see-also"></a>Ayrıca bkz.

- [XElement sınıfı dinamik özellikleri](../designers/attribute-xelement-dynamic-property.md)
- [Değer](../designers/value-xelement-dynamic-property.md)