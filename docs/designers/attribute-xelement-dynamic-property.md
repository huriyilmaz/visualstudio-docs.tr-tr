---
title: Öznitelik (XElement dinamik özelliği)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d7fc1aa0419863e933bdc0a828455fcda8671fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637394"
---
# <a name="attribute-xelement-dynamic-property"></a>Öznitelik (XElement dinamik özelliği)

Belirtilen genişletilmiş ada karşılık gelen öznitelik örneğini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Sözdizimi

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri

@No__t_0 türünde bir Dizin Oluşturucu. Bu Dizin Oluşturucu belirtilen özniteliğin genişletilmiş adını alır ve karşılık gelen <xref:System.Xml.Linq.XAttribute> döndürür ya da belirtilen ada sahip bir öznitelik yoksa `null`.

## <a name="remarks"></a>Açıklamalar

Bu özellik <xref:System.Xml.Linq.XElement?displayProperty=fullName> sınıfının <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi ile eşdeğerdir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [XElement Sınıfı Dinamik Özellikleri](../designers/attribute-xelement-dynamic-property.md)
- [Değer](../designers/value-xattribute-dynamic-property.md)