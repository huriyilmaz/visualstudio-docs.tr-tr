---
description: vstav3 ad alanının entryPointsCollection öğesi, uygulama çözümleriyle ilişkili tüm entryPoints Office içerir.
title: '&lt;entryPointsCollection &gt; öğesi (Office geliştirme Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <entryPointsCollection> element
- application manifests [Office development in Visual Studio], <entryPointsCollection> element
- entryPointsCollection element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d9d76ceb66ef180a90e9e8cdc916ec3175fe2517
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972180"
---
# <a name="ltentrypointscollectiongt-element-office-development-in-visual-studio"></a>&lt;entryPointsCollection &gt; öğesi (Office geliştirme Visual Studio)
  Ad `entryPointsCollection` alanının `vstav3` öğesi, çözümlerle `entryPoints` ilişkili tüm öğeleri Office içerir.

## <a name="syntax"></a>Syntax

```xml
<entryPointsCollection>
  <entryPoints>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
  </entryPoints>
</entryPointsCollection>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 öğesi `entryPointsCollection` gereklidir ve ad alanı `vstav3` içindedir. Alt öğelerin de bu ad alanı içinde olması gerekir. Bir uygulama `entryPointsCollection` bildiriminde tanımlanan yalnızca bir öğe vardır.

 öğesinin `entryPointsCollection` özniteliği yoktur.

 `entryPointsCollection` aşağıdaki öğelere sahiptir.

### <a name="entrypoints"></a>Entrypoints
 Gereklidir. öğesinin ad `entryPoints` alanı içinde `vstav3` rolü, [&#60;'de geliştirme&#62; entryPoints &#40;Office öğesinde Visual Studio&#41;. ](../vsto/entrypoints-element-office-development-in-visual-studio.md)

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirme örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, kullanılarak `entryPointsCollection` dağıtılan belge düzeyi bir çözüm için uygulama bildiriminde öğesini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
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
```

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, kullanılarak `entryPointsCollection` dağıtılan bir uygulama düzeyi çözümü için uygulama bildiriminde bir öğeyi [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
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
```

## <a name="multi-project-deployment-example"></a>Çoklu Project dağıtım örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, iki farklı çözüme sahip çoklu proje dağıtımı için bir `entryPointsCollection` uygulama bildiriminde Office gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstav3:entryPointsCollection>
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
    </vstav3:entryPointsCollection>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
