---
title: Öznitelik (XElement dinamik özelliği) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 551e072b05e7a88ff9624c5d16e4aa199a6afd66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657975"
---
# <a name="attribute-xelement-dynamic-property"></a>Öznitelik (XElement dinamik özelliği)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen genişletilmiş ada karşılık gelen öznitelik örneğini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Syntax

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri
 Türün Dizin Oluşturucusu `XAttribute Item(String expandedName)` . Bu Dizin Oluşturucu belirtilen özniteliğin genişletilmiş adını alır ve buna karşılık gelen <xref:System.Xml.Linq.XAttribute> veya `null` belirtilen ada sahip bir öznitelik yoksa.

## <a name="remarks"></a>Açıklamalar
 Bu özellik, <xref:System.Xml.Linq.XElement.Attribute%2A> sınıfının yöntemine eşdeğerdir <xref:System.Xml.Linq.XElement?displayProperty=fullName> .

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>[XElement sınıfı dinamik özellikleri](../designers/xelement-class-dynamic-properties.md) [değeri](../designers/value-xattribute-dynamic-property.md)
