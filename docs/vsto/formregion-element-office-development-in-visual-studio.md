---
description: vstov4 ad alanının formRegion öğesi, bir VSTO eklentisi ile ilişkili bir Microsoft Office Outlook form bölgesini tanımlar.
title: '&lt;formRegion &gt; öğesi (Visual Studio Office geliştirme)'
titleSuffix: ''
ms.custom: seodec18
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
ms.openlocfilehash: f78e6867afd4839dab329a9543fafe4015bf777f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156025"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion &gt; öğesi (Visual Studio Office geliştirme)
  `formRegion`ad alanının öğesi, `vstov4` bir VSTO eklentisi ile ilişkili bir Microsoft Office Outlook form bölgesini tanımlar.

## <a name="syntax"></a>Syntax

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `formRegion`ad alanı öğesi, `vstov4` bir Outlook VSTO eklentisi ile ilişkili bir form bölgesini tanımlar. yalnızca form bölgelerini içeren Outlook VSTO eklentileri için gereklidir.

 `formRegion`tek bir VSTO eklentisi için bir öğe içinde tanımlanmış birden fazla öğe olabilir `formRegions` .

 `formRegion`Öğesi aşağıdaki özniteliğe sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Form bölgesinin adını tanımlar.|

 `formRegion`Öğesi aşağıdaki alt öğeleri içerir.

### <a name="messageclass"></a>messageClass
 `messageClass`öğesi, form bölgesiyle ilişkili Outlook formunu tanımlar.

 `messageClass`Öğesi aşağıdaki özniteliğe sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Form bölgesiyle ilişkili formu tanımlar.|

## <a name="example"></a>Örnek
 aşağıdaki kod örneği, `formRegion` kullanılarak dağıtılan bir Outlook VSTO eklentisinin uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu tek form bölgesiyle ilişkili üç ileti sınıfı vardır. bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)
