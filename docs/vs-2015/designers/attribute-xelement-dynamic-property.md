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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657975"
---
# <a name="attribute-xelement-dynamic-property"></a>Öznitelik (XElement dinamik özelliği)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen genişletilmiş ada karşılık gelen öznitelik örneğini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Sözdizimi

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri
 @No__t_0 türünde bir Dizin Oluşturucu. Bu Dizin Oluşturucu belirtilen özniteliğin genişletilmiş adını alır ve karşılık gelen <xref:System.Xml.Linq.XAttribute> döndürür ya da belirtilen ada sahip bir öznitelik yoksa `null`.

## <a name="remarks"></a>Açıklamalar
 Bu özellik <xref:System.Xml.Linq.XElement?displayProperty=fullName> sınıfının <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi ile eşdeğerdir.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName> [XElement sınıfı dinamik özellikleri](../designers/xelement-class-dynamic-properties.md) [değeri](../designers/value-xattribute-dynamic-property.md)
