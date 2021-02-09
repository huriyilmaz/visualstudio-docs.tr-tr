---
title: "&lt;Application &gt; öğesi (Visual Studio 'Da Office geliştirme)"
description: Vstav3 ad alanının uygulama öğesinin Office çözümlerinin açıklamasını nasıl sarılacağını öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <application> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 895a695f1de56c3041ad1723f1b6b30356c839df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900922"
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;Application &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `application` `vstav3` Ad alanı öğesi Office çözümlerinin açıklamalarını sarmalar. Alt öğeler, belge düzeyi özelleştirmeleri ve VSTO eklentileri için farklıdır.

## <a name="syntax-for-document-level-customizations"></a>Belge düzeyi özelleştirmeleri sözdizimi

```xml
<application>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</application>
```

## <a name="syntax-for-application-level-add-ins"></a>Uygulama düzeyi eklentileri sözdizimi

```xml
<application>
  <customization
    id
    <appAddin
      application
      loadBehavior
      keyName>
    <friendlyName></friendlyName>
    <description></description>
    <formRegions></formRegions>
  </customization>
</application>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `application`Ad alanı öğesi, `vstav3` ad alanında bulunan özelleştirmeye özgü tüm bilgileri sarmalayan düğümdür `vstov4` .

 `application`Öğesinde hiç öznitelik yok.

 `application`Öğesi aşağıdaki öğeye sahiptir.

### <a name="customization"></a>Özelleştirme
 `customization` `vstov3` Ad alanındaki öğesinin rolü [&#60;özelleştirme&#62; öğesi Visual Studio 'da Office geliştirme&#41;&#40;](../vsto/customization-element-office-development-in-visual-studio.md)tanımlanmıştır.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `application` kullanılarak dağıtılan belge düzeyi Office çözümünde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
    <vstov4:customization>
      <vstov4:document
        solutionId="73e" />
    </vstov4:customization>
  </vstov4:customizations>
</vstav3:application>
```

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `application` kullanılarak dağıtılan uygulama düzeyi Office çözümünde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
    <vstov4:customization>
      <vstov4:appAddIn
        application="Outlook"
        loadBehavior="3"
        keyName="ContosoOutlookAddIn">
        <vstov4:friendlyName>
          ContosoOutlookAddIn
        </vstov4:friendlyName>
        <vstov4:description>
          ContosoOutlookAddIn - Outlook VSTO Add-in
          created with Visual Studio Tools for Office
        </vstov4:description>
        <vstov4:formRegions>
          <vstov4:formRegion
              name="OutlookAddIn1.FormRegion1">
            <vstov4:messageClass name="IPM.Note" />
            <vstov4:messageClass name="IPM.Contact" />
            <vstov4:messageClass name="IPM.Appointment" />
          </vstov4:formRegion>
        </vstov4:formRegions>
      </vstov4:appAddIn>
    </vstov4:customization>
  </vstov4:customizations>
</vstav3:application>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)