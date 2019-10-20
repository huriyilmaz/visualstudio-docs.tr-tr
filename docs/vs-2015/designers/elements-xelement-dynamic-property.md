---
title: Öğeler (XElement dinamik özelliği) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 383101679827f19b9a85d36f0f5a39eb772c68ec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664687"
---
# <a name="elements-xelement-dynamic-property"></a>Öğeler (XElement dinamik özelliği)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen genişletilmiş adla eşleşen geçerli öğenin alt öğelerini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Sözdizimi

```
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri
 @No__t_0 türünde bir Dizin Oluşturucu. Bu Dizin Oluşturucu, istenen alt öğelerin genişletilmiş adını alır ve bir <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` koleksiyonundaki eşleşen alt öğeleri döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu özellik <xref:System.Xml.Linq.XContainer> sınıfının <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> yöntemi ile eşdeğerdir.

 Döndürülen koleksiyondaki öğeler XML kaynak belgesi sıratümcesinde.

 Bu özellik ertelenmiş yürütmeyi kullanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [XElement sınıfı dinamik özellikler](../designers/xelement-class-dynamic-properties.md) [öğesi](../designers/element-xelement-dynamic-property.md) alt [öğeleri](../designers/descendants-xelement-dynamic-property.md)
