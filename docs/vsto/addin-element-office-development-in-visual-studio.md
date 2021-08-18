---
description: vstav3 ad alanının addın öğesi, Visual Studio ile geliştirilen Microsoft Office VSTO eklentileri ve belge düzeyi özelleştirmelerine özgü bilgiler içerir.
title: '&lt;addın &gt; öğesi (Visual Studio Office geliştirme)'
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100328"
---
# <a name="ltaddingt-element-office-development-in-visual-studio"></a>&lt;addın &gt; öğesi (Visual Studio Office geliştirme)
  ad alanının **addin** öğesi, `vstav3` Visual Studio ile geliştirilen Microsoft Office VSTO eklentileri ve belge düzeyi özelleştirmelerine özgü bilgiler içerir.

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
 ad alanının **addin** öğesi `vstav3` Office çözümü ve Microsoft Office uygulaması hakkında bilgi içerir. Bu öğe şu ad alanında olmalıdır: `vstav3=urn:schemas-microsoft-com:vsta.v3` . Alt öğeler de bu ad alanında olmalıdır.

 `addin`Öğesinde hiç öznitelik yok.

 `addin`Öğesi aşağıdaki alt öğeleri içerir.

### <a name="entrypoints"></a>entryPoints
 Gereklidir. **entrypoints** öğesi [&#60;entrypoints&#62; öğesi &#40;Visual Studio&#41;geliştirme Office](../vsto/entrypoints-element-office-development-in-visual-studio.md)açıklanmaktadır.

### <a name="update"></a>update
 Gereklidir. **update** öğesi, [Visual Studio&#41;Office geliştirme&#62;&#60;güncelleştirme &#40;öğesi](../vsto/update-element-office-development-in-visual-studio.md)açıklanmaktadır.

### <a name="postactions"></a>Postalamalar
 İsteğe bağlı. **postalamalar** öğesi, [Visual Studio&#41;Office geliştirme&#62; öğe &#40;&#60;](../vsto/postactions-element-office-development-in-visual-studio.md)postalamaları açıklanmaktadır.

### <a name="application"></a>uygulama
 Gereklidir. **uygulama** öğesi, [Visual Studio&#41;Office geliştirme &#40;uygulama&#62; öğesi&#60;](../vsto/application-element-office-development-in-visual-studio.md)açıklanmaktadır.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="description"></a>Açıklama
 aşağıdaki kod örneği, kullanılarak dağıtılan bir belge düzeyi Office çözümünde **eklenti** öğesini gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

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

### <a name="description"></a>Açıklama
 aşağıdaki kod örneği, kullanılarak dağıtılan bir uygulama düzeyi Office çözümünde **eklenti** öğesini gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

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

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)
