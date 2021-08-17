---
title: '&lt;uygulama &gt; öğesi (Visual Studio Office geliştirme)'
description: vstav3 ad alanının uygulama öğesinin Office çözümlerin açıklamasını nasıl sarılacağını öğrenin.
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
ms.openlocfilehash: 8389cc3ed162c4d1717810fa6d95037ce4db1595
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047250"
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;uygulama &gt; öğesi (Visual Studio Office geliştirme)
  `application` `vstav3` ad alanı öğesi Office çözümlerin açıklamasını sarmalar. alt öğeler, belge düzeyi özelleştirmeleri ve VSTO eklentileri için farklıdır.

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
 `customization`ad alanındaki öğesinin rolü, Visual Studio&#41;`vstov3` [Office geliştirmesi &#40;&#60;özelleştirme&#62; öğesi ](../vsto/customization-element-office-development-in-visual-studio.md)tanımlanmıştır.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="description"></a>Açıklama
 aşağıdaki kod örneği, `application` kullanılarak dağıtılan bir belge düzeyi Office çözümünde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

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
 aşağıdaki kod örneği, `application` kullanılarak dağıtılan bir uygulama düzeyi Office çözümünde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

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
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)