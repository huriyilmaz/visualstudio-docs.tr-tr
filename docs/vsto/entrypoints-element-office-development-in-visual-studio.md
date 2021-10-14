---
description: vstav3 ad alanının entrypoints öğesi, bir Office çözümüyle ilişkili tüm entryPoint öğelerini içerir.
title: '&lt;entrypoints &gt; öğesi (Visual Studio Office geliştirme)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoints> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c18bf0e107e9e068157bf124123f8b971d8eaf43
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972177"
---
# <a name="ltentrypointsgt-element-office-development-in-visual-studio"></a>&lt;entrypoints &gt; öğesi (Visual Studio Office geliştirme)
  `entryPoints`ad alanı öğesi, `vstav3` `entryPoint` bir Office çözümüyle ilişkili tüm öğeleri içerir.

## <a name="syntax"></a>Syntax

```xml
<entryPoints>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
</entryPoints>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `entryPoints`Öğesi gereklidir ve `vstav3` ad alanında bulunur. `entryPoints`her bir Office çözümü için uygulama bildiriminde tanımlanan bir öğe vardır. örneğin, çok projeli bir dağıtımda üç Office çözümü dağıtırsanız, `entryPoints` uygulama bildiriminde üç öğe vardır.

 `entryPoints`Öğesi aşağıdaki özniteliğe sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|kimlik|Çoklu proje dağıtımı için gereklidir. Office çözümünün adı. Kimlik, eşittir (=) sembolünü içeremez.|

 `entryPoints` Aşağıdaki öğelere sahiptir.

### <a name="entrypoint"></a>Noktası
 Gereklidir. `entryPoint`ad alanındaki öğesinin rolü, Visual Studio&#41;`vstav3` [Office geliştirme &#40;&#60;giriş noktası&#62; öğesi ](../vsto/entrypoint-element-office-development-in-visual-studio.md)içinde tanımlanmıştır.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `entryPoints` kullanılarak dağıtılan bir belge düzeyi çözümü için uygulama bildiriminde bulunan öğeyi gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
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
```

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `entryPoints` kullanılarak dağıtılan uygulama düzeyi çözüm için uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
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
```

## <a name="multi-project-deployment-example"></a>Çoklu proje dağıtım örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `entryPoints` Çoklu proje dağıtımı için bir uygulama bildiriminde öğesini gösterir. bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstav3:entryPoints
  id="ContosoExcel">
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
<vstav3:entryPoints
  id="ContosoOutlook">
  <vstav3:entryPoint
    class="ContosoOutlookAddIn.ThisAddIn">
    <assemblyIdentity
      name="ContosoOutlookAddIn"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
</vstav3:entryPoints>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)
