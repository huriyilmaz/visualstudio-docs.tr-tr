---
description: Vstav3 ad alanının her entryPoint öğesi, bu ClickOnce uygulaması yüklendiğinde çalıştırılması gereken bir özelleştirme derlemesini tanımlar.
title: "&lt;entryPoint &gt; öğesi (Visual Studio 'Da Office geliştirme)"
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 581274ea58dafa8021cb456a0c7cb1e6bf98da32
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223725"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;entryPoint &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `entryPoint`Ad alanındaki her öğe, `vstav3` Bu uygulama yüklendiğinde çalıştırılması gereken bir özelleştirme derlemesini tanımlar [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

## <a name="syntax"></a>Syntax

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `entryPoint`Öğesi gereklidir ve `vstav3` ad alanında bulunur.

 Her `entryPoint` öğe yalnızca bir özelleştirme derlemesi içerebilir. `entryPoint`Uygulama bildiriminde tanımlanmış birden fazla öğe olabilir.

 `entryPoint`Öğesi aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`class`|Gereklidir. Yürütülecek bir özelleştirme derlemesini tanımlar. Bu özniteliğin söz dizimi *NamespaceName. ClassName*' dir.|

 `entryPoint` Aşağıdaki öğeye sahiptir.

### <a name="assemblyidentity"></a>AssemblyIdentity
 Gereklidir. `assemblyIdentity`Ad alanındaki öğesi, `vstav3` uygulama bildiriminde varolan bir öğeyi ifade eder `assemblyIdentity` [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

 `assemblyIdentity`Ve özniteliklerinin rolü, [ClickOnce uygulama&#41;&#40;&#62; öğesi&#60;assemblyIdentity ](../deployment/assemblyidentity-element-clickonce-application.md)içinde tanımlanır.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, `entryPoint` kullanılarak dağıtılan bir belge düzeyi Office çözümü için uygulama bildirimindeki öğeleri gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
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
```

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, `entryPoint` kullanılarak dağıtılan uygulama düzeyi Office çözümü için uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstav3:entryPoint
  class="ContosoOutlookAddIn.ThisAddIn">
  <assemblyIdentity
    name="ContosoOutlookAddIn"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
