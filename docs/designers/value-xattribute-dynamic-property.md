---
title: Değer (XAttribute dinamik özelliği)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fefa3d13f1a38b5d1c329fa9df9220e13e769b1c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634527"
---
# <a name="value-xattribute-dynamic-property"></a>Değer (XAttribute dinamik özelliği)

XML özniteliğinin değerini alır veya ayarlar.

## <a name="syntax"></a>Sözdizimi

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri

Bu özniteliğin değerini içeren bir <xref:System.String>.

## <a name="exceptions"></a>Özel Durumlar

|Özel durum türü|Koşul|
| - |---------------|
|<xref:System.ArgumentNullException>|Ayarlanırken, `value` `null`.|

## <a name="remarks"></a>Açıklamalar

Bu özellik, <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> sınıfının <xref:System.Xml.Linq.XAttribute.Value%2A> özelliğine eşdeğerdir, ancak bu dinamik özellik değişiklik bildirimlerini de destekler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [XAttribute sınıfı dinamik özellikleri](../designers/value-xattribute-dynamic-property.md)
- [Öznitelik](../designers/attribute-xelement-dynamic-property.md)