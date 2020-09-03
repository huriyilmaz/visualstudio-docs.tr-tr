---
title: Öğe (XElement dinamik özelliği) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c6171a5dedfd6985a6f54e748011bf86e03f4d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664647"
---
# <a name="element-xelement-dynamic-property"></a>Öğe (XElement dinamik özelliği)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen genişletilmiş ada karşılık gelen alt öğe örneğini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Syntax

```
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri
 Türün Dizin Oluşturucusu `XElement Item(String expandedName)` . Bu dizin oluşturucu genişletilmiş bir ad parametresi alır ve buna karşılık gelen <xref:System.Xml.Linq.XElement> veya `null` belirtilen ada sahip hiçbir öğe yoksa.

## <a name="remarks"></a>Açıklamalar
 Bu özellik, <xref:System.Xml.Linq.XContainer.Element%2A> sınıfının yöntemine eşdeğerdir <xref:System.Xml.Linq.XContainer?displayProperty=fullName> .

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>[XElement sınıfı dinamik özellikler](../designers/xelement-class-dynamic-properties.md) [öğeleri](../designers/elements-xelement-dynamic-property.md)
