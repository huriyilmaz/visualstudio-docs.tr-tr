---
description: vstav3 ad alanının addin öğesi, Microsoft Office VSTO ile geliştirilen belge düzeyi özelleştirmelere özgü Visual Studio.
title: '&lt;addin &gt; öğesi (Office geliştirme Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <addIn> element
- addin element
- <addin> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 63d5adb7d4fab31d7f4d24f40948d8e4acd26f10
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725612"
---
# <a name="ltaddingt-element-office-development-in-visual-studio"></a>&lt;addin &gt; öğesi (Office geliştirme Visual Studio)
  Ad **alanının addin** öğesi, eklentilerle geliştirilen Microsoft Office VSTO ve belge düzeyi özelleştirmelere özgü `vstav3` Visual Studio.

## <a name="syntax"></a>Syntax

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customization>
    </customization>
  </application
</addIn>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 Ad **alanının addin** `vstav3` öğesi, Office çözümü ve Microsoft Office içerir. Bu öğe aşağıdaki ad alanı içinde yer alalır: `vstav3=urn:schemas-microsoft-com:vsta.v3` . Alt öğelerin de bu ad alanı içinde olması gerekir.

 öğesinin `addin` özniteliği yoktur.

 öğesi `addin` aşağıdaki alt öğelere sahiptir.

### <a name="entrypoints"></a>Entrypoints
 Gereklidir. **entryPoints öğesi,** öğesinde [&#60;geliştirme&#62; entryPoints &#40;Office öğesinde Visual Studio&#41;.](../vsto/entrypoints-element-office-development-in-visual-studio.md)

### <a name="update"></a>update
 Gereklidir. Update **öğesi,** 'de [&#60;geliştirme&#62; için &#40;Office güncelleştirme öğesinde Visual Studio&#41;.](../vsto/update-element-office-development-in-visual-studio.md)

### <a name="postactions"></a>Postactions
 İsteğe bağlı. **postActions öğesi,**&#62; [geliştirme&#60;postActions &#40;Office öğesinde Visual Studio&#41;.](../vsto/postactions-element-office-development-in-visual-studio.md)

### <a name="application"></a>uygulama
 Gereklidir. Uygulama **öğesi,** uygulama&#60;[geliştirme&#62; uygulama &#40;Office öğesinde Visual Studio&#41;.](../vsto/application-element-office-development-in-visual-studio.md)

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirme örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, kullanılarak dağıtılan bir belge düzeyi Office **addin** öğesini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama [bildirimleri'ne sağlanan daha büyük bir Office bölümüdur.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstav3:addIn
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">
  <vstav3:entryPointsCollection>
    <vstav3:entryPoints>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.ThisWorkbook">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet1">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet2">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet3">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
  <vstav3:update
    enabled="true">
    <vstav3:expiration
      maximumAge="7"
      unit="days" />
  </vstav3:update>
  <vstav3:application>
    <vstov4:customizations
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
      <vstov4:customization>
        <vstov4:document
          solutionId="73e" />
      </vstov4:customization>
    </vstov4:customizations>
  </vstav3:application>
</vstav3:addIn>
```

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, kullanılarak dağıtılan bir uygulama düzeyi Office **addin** öğesini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] göstermektedir. Bu kod örneği, uygulama çözümleri için Uygulama [bildirimleri'ne sağlanan daha büyük bir Office bölümüdur.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstav3:addIn
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">
  <vstav3:entryPointsCollection>
    <vstav3:entryPoints>
      <vstav3:entryPoint
        class="ContosoOutlookAddIn.ThisAddIn">
        <assemblyIdentity
          name="ContosoOutlookAddIn"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
  <vstav3:update
    enabled="true">
    <vstav3:expiration
      maximumAge="7"
      unit="days" />
  </vstav3:update>
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
</vstav3:addIn>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
