---
description: vstov4 ad alanının formregion öğesi, bir VSTO eklentisi ile ilişkili Microsoft Office Outlook form bölgelerini içerir.
title: '&lt;formregion &gt; öğesi (Visual Studio Office geliştirme)'
titleSuffix: ''
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a8cbd2956f8cdfe48d8c7a523f996ae7a6e741da
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970366"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formregion &gt; öğesi (Visual Studio Office geliştirme)
  `formRegions`ad alanı öğesi, `vstov4` bir VSTO eklentisi ile ilişkili Microsoft Office Outlook form bölgelerini içerir.

## <a name="syntax"></a>Syntax

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `formRegions`ad alanı öğesi, `vstov4` `formRegion` bir Outlook VSTO eklentisinin tüm öğelerini içerir. yalnızca form bölgelerini içeren Outlook VSTO eklentileri için gereklidir.

 `formRegions`Uygulama bildiriminde tanımlı yalnızca bir öğe olabilir.

 `formRegions`Öğesinde hiç öznitelik yok.

 `formRegions`Öğesi aşağıdaki öğeye sahiptir.

### <a name="formregion"></a>Bağımsız
 form bölgelerini içeren Outlook VSTO eklentileri için gereklidir. `formRegion`öğesi, [Visual Studio&#41;'de geliştirme Office&#60;formRegion&#62; öğesi &#40;](../vsto/formregion-element-office-development-in-visual-studio.md)tanımlanmıştır.

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Description
 aşağıdaki kod örneği, `formRegions` kullanılarak dağıtılan uygulama düzeyi Office çözümü için uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

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
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)
