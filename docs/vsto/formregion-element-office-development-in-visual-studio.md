---
description: vstov4 ad alanının formRegion öğesi, Microsoft Office Outlook eklenti ile ilişkili bir form VSTO tanımlar.
title: '&lt;formRegion &gt; öğesi (Office geliştirme Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d3eaadeba609b13e801421031f2e54546b5a353e
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970353"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion &gt; öğesi (Office geliştirme Visual Studio)
  ad alanının öğesi, bir Microsoft Office Outlook ile ilişkili bir form `formRegion` bölgesi VSTO `vstov4` tanımlar.

## <a name="syntax"></a>Syntax

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 ad `formRegion` alanının `vstov4` öğesi, bir form bölgesiyle ilişkili form Outlook VSTO tanımlar. Yalnızca form bölgelerini Outlook VSTO eklentileri oluşturmak için gereklidir.

 Bir öğe içinde `formRegion` tek bir eklenti için birden çok öğe VSTO `formRegions` olabilir.

 öğesi `formRegion` aşağıdaki özniteliğine sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Form bölgesi adını tanımlar.|

 öğesi `formRegion` aşağıdaki alt öğelere sahiptir.

### <a name="messageclass"></a>messageClass
 `messageClass`öğesi, Outlook bölgeyle ilişkili bir form tanımlar.

 öğesi `messageClass` aşağıdaki özniteliğine sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Form bölgesiyle ilişkili formu tanımlar.|

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, kullanılarak `formRegion` dağıtılan bir uygulama Outlook VSTO öğesi [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu tek form bölgesiyle ilişkili üç ileti sınıfı vardır. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
