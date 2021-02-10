---
title: "&lt;FormRegion &gt; öğesi (Visual Studio 'Da Office geliştirme)"
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a1a718c6a247528788d91e9c1f30ad636acb7ab9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970341"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;FormRegion &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `formRegions`Ad alanı öğesi, `vstov4` bir VSTO eklentisi ile Ilişkili Microsoft Office Outlook form bölgelerini içerir.

## <a name="syntax"></a>Syntax

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `formRegions`Ad alanı öğesi, `vstov4` `formRegion` bir Outlook VSTO eklentisi için tüm öğeleri içerir. Yalnızca form bölgelerini içeren Outlook VSTO eklentileri için gereklidir.

 `formRegions`Uygulama bildiriminde tanımlı yalnızca bir öğe olabilir.

 `formRegions`Öğesinde hiç öznitelik yok.

 `formRegions`Öğesi aşağıdaki öğeye sahiptir.

### <a name="formregion"></a>Bağımsız
 Form bölgelerini içeren Outlook VSTO eklentileri için gereklidir. `formRegion`Öğesi, [Visual&#41;Studio 'da Office geliştirme &#40;&#60;FormRegion&#62; öğesinde ](../vsto/formregion-element-office-development-in-visual-studio.md)tanımlanmıştır.

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `formRegions` kullanılarak dağıtılan uygulama düzeyi Office çözümü için uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)