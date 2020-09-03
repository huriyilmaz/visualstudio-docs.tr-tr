---
title: Alt öğeler (XElement dinamik özelliği) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b0496a04219c88573b3b555ef879a046d90faa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664778"
---
# <a name="descendants-xelement-dynamic-property"></a>Alt öğeler (XElement dinamik özelliği)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen genişletilmiş adla eşleşen geçerli öğenin tüm alt öğelerini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Syntax

```
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri
 Türün Dizin Oluşturucusu `IEnumerable<XElement> Item(String expandedName)` . Bu Dizin Oluşturucu belirtilen alt öğelerin genişletilmiş adını alır ve bir koleksiyondaki eşleşen alt öğeleri döndürür <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` .

## <a name="remarks"></a>Açıklamalar
 Bu özellik, <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> sınıfının yöntemine eşdeğerdir <xref:System.Xml.Linq.XContainer> .

 Döndürülen koleksiyondaki öğeler XML kaynak belgesi sıratümcesinde.

 Bu özellik ertelenmiş yürütmeyi kullanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [XElement sınıfı dinamik özellikler](../designers/xelement-class-dynamic-properties.md) [öğeleri](../designers/elements-xelement-dynamic-property.md)
