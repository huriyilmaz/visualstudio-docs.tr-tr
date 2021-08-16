---
description: vstav3 ad alanının her entryPoint öğesi, bu ClickOnce uygulaması yüklendiğinde çalıştırılması gereken bir özelleştirme derlemesini tanımlar.
title: '&lt;entryPoint &gt; öğesi (Visual Studio Office geliştirme)'
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ff0f3313da0479c7ec6a8dda0c2bc609e6f7b4a357821b9acf988e7ff599112a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424352"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;entryPoint &gt; öğesi (Visual Studio Office geliştirme)
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

 `assemblyIdentity`ve özniteliklerinin rolü [&#60;assemblyıdentity&#62; öğesi &#40;ClickOnce uygulama&#41;](../deployment/assemblyidentity-element-clickonce-application.md)tanımlanmıştır.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="description"></a>Açıklama
 aşağıdaki kod örneği, `entryPoint` kullanılarak dağıtılan bir belge düzeyi Office çözümü için uygulama bildiriminde bulunan öğeleri gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

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

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Açıklama
 aşağıdaki kod örneği, `entryPoint` kullanılarak dağıtılan uygulama düzeyi Office çözümü için uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

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
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)
