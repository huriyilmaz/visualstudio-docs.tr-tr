---
description: vstav3 ad alanının her entryPoint öğesi, bu uygulama yüklenirken ClickOnce özelleştirme derlemesini tanımlar.
title: '&lt;entryPoint &gt; öğesi (Office geliştirme Visual Studio)'
titleSuffix: ''
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
ms.openlocfilehash: 1a61d79e7028cc4b691e072f113241d79fd1b885
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970977"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;entryPoint &gt; öğesi (Office geliştirme Visual Studio)
  Ad `entryPoint` alanının her `vstav3` öğesi, bu uygulama yüklenirken çalıştıracak bir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] özelleştirme derlemesi tanımlar.

## <a name="syntax"></a>Syntax

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 öğesi `entryPoint` gereklidir ve ad alanı `vstav3` içindedir.

 Her `entryPoint` öğe yalnızca bir özelleştirme derlemesi içerebilir. Bir uygulama `entryPoint` bildiriminde tanımlanmış birden çok öğe olabilir.

 öğesi `entryPoint` aşağıdaki özniteliklere sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`class`|Gereklidir. Yürütülecek bir özelleştirme derlemesi tanımlar. Bu özniteliğin söz dizimi *NamespaceName.ClassName'tir.*|

 `entryPoint` aşağıdaki öğeye sahip.

### <a name="assemblyidentity"></a>Assemblyıdentity
 Gereklidir. Ad `assemblyIdentity` alanı `vstav3` öğesi, uygulama bildiriminde var `assemblyIdentity` olan bir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] öğeye başvurur.

 ve öznitelikleri,&#41;uygulama `assemblyIdentity` [öğesi&#60;assemblyIdentity&#62; öğesinde &#40;ClickOnce tanımlanır. ](../deployment/assemblyidentity-element-clickonce-application.md)

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirme örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, kullanılarak `entryPoint` dağıtılan belge düzeyi bir çözüme Office uygulama bildiriminde öğeleri [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

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

### <a name="description"></a>Description
 Aşağıdaki kod örneği, kullanılarak `entryPoint` dağıtılan bir uygulama düzeyi uygulama Office öğesi [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

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

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
