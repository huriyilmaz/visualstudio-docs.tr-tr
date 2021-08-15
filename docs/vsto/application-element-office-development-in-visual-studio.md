---
title: '&lt;application &gt; öğesi (Office geliştirme Visual Studio)'
description: vstav3 ad alanının uygulama öğesinin, uygulama çözümlerinin açıklamasını nasıl Office öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 111d993082464409f7a6689779292b1b27dbf349e20f373baec3290f68566b44
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440883"
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;application &gt; öğesi (Office geliştirme Visual Studio)
  Ad `application` alanının `vstav3` öğesi, Office çözümlerinin açıklamasını sarmalar. Alt öğeler, belge düzeyi özelleştirmeler ve VSTO farklıdır.

## <a name="syntax-for-document-level-customizations"></a>Belge düzeyi özelleştirmeler için söz dizimi

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

## <a name="syntax-for-application-level-add-ins"></a>Uygulama düzeyi eklentilerin söz dizimi

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
 Ad `application` alanının `vstav3` öğesi, ad alanında yer alan özelleştirmeye özgü tüm bilgileri sarmalar. `vstov4`

 öğesinin `application` özniteliği yoktur.

 öğesi `application` aşağıdaki öğeye sahip.

### <a name="customization"></a>Özelleştirme
 öğenin ad `customization` alanında `vstov3` rolü, [&#62;'de&#60;&#40;Office Geliştirme&#62; özelleştirmesinde Visual Studio&#41;. ](../vsto/customization-element-office-development-in-visual-studio.md)

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirme örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, kullanılarak `application` dağıtılan belge düzeyi bir Office bir öğeyi [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, Office Solutions için Uygulama Bildirimleri [bölümünde sağlanan daha büyük bir Office örneğidir.](../vsto/application-manifests-for-office-solutions.md)

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

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, kullanılarak `application` dağıtılan bir uygulama düzeyinde Office bir öğeyi [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] göstermektedir. Bu kod örneği, Office Solutions için Uygulama Bildirimleri [bölümünde sağlanan daha büyük bir Office örneğidir.](../vsto/application-manifests-for-office-solutions.md)

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

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)