---
title: Değer (XAttribute dinamik özelliği) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9a31b4c4182ed67a3e67d3c25c2c5ccf50e083f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664058"
---
# <a name="value-xattribute-dynamic-property"></a>Değer (XAttribute dinamik özelliği)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML özniteliğinin değerini alır veya ayarlar.

## <a name="syntax"></a>Syntax

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri
 <xref:System.String>Bu özniteliğin değerini içeren bir.

## <a name="exceptions"></a>Özel durumlar

|Özel durum türü|Koşul|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|Ayarlanırken,, `value` olur `null` .|

## <a name="remarks"></a>Açıklamalar
 Bu özellik, <xref:System.Xml.Linq.XAttribute.Value%2A> sınıfının özelliğine eşdeğerdir <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> , ancak bu dinamik özellik değişiklik bildirimlerini de destekler.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>[XAttribute sınıfı dinamik özellikler](../designers/xattribute-class-dynamic-properties.md) [özniteliği](../designers/attribute-xelement-dynamic-property.md)
