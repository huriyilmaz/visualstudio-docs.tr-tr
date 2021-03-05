---
description: Vstav3 ad alanının AddIn öğesi, Visual Studio ile geliştirilen Microsoft Office VSTO eklentileri ve belge düzeyi özelleştirmelerine özgü bilgiler içerir.
title: "&lt;AddIn &gt; öğesi (Visual Studio 'Da Office geliştirme)"
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
ms.workload:
- office
ms.openlocfilehash: 4cfc59475b01fbf42c387b4a7a5ca533b313a322
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227391"
---
# <a name="ltaddingt-element-office-development-in-visual-studio"></a>&lt;AddIn &gt; öğesi (Visual Studio 'Da Office geliştirme)
  Ad alanının **addin** öğesi, `vstav3` Visual Studio Ile geliştirilen Microsoft Office VSTO eklentileri ve belge düzeyi özelleştirmelerine özgü bilgiler içerir.

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
 Ad alanının **addin** öğesi `vstav3` Office çözümü ve Microsoft Office uygulaması hakkında bilgi içerir. Bu öğe şu ad alanında olmalıdır: `vstav3=urn:schemas-microsoft-com:vsta.v3` . Alt öğeler de bu ad alanında olmalıdır.

 `addin`Öğesinde hiç öznitelik yok.

 `addin`Öğesi aşağıdaki alt öğeleri içerir.

### <a name="entrypoints"></a>entryPoints
 Gereklidir. **EntryPoints** öğesi, [Visual&#41;Studio 'da Office geliştirme &#40;&#62;&#60;entryPoints](../vsto/entrypoints-element-office-development-in-visual-studio.md)öğesinde açıklanmıştır.

### <a name="update"></a>update
 Gereklidir. **Update** öğesi, [Visual&#41;Studio 'da Office geliştirme &#40;&#60;Update&#62; öğesi](../vsto/update-element-office-development-in-visual-studio.md)açıklanmaktadır.

### <a name="postactions"></a>Postalamalar
 İsteğe bağlı. **Postalamalar** öğesi, [Visual&#41;Studio 'da Office geliştirme &#40;&#60;postalamalar&#62; öğesi](../vsto/postactions-element-office-development-in-visual-studio.md)içinde açıklanmıştır.

### <a name="application"></a>uygulama
 Gereklidir. **Uygulama** öğesi, [Visual Studio 'da Office geliştirme &#40;&#41;uygulama&#62; öğesi&#60;](../vsto/application-element-office-development-in-visual-studio.md)açıklanmaktadır.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, kullanılarak dağıtılan belge düzeyi Office çözümünde **eklenti öğesini gösterir** [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

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

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, kullanılarak dağıtılan uygulama düzeyi Office çözümünde **eklenti öğesini gösterir** [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

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
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
