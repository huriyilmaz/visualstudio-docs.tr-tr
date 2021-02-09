---
title: "&lt;özelleştirme &gt; öğesi (Visual Studio 'Da Office geliştirme)"
description: Vstov4 ad alanının özelleştirme öğesinin belirli bir Office çözümünü nasıl açıklar olduğunu öğrenin.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e63b93728f41dcff360da8ee9d14e2830d216be5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849950"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;özelleştirme &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `customization`Ad alanının öğesi, `vstov4` belirli bir Office çözümünü tanımlar. Alt öğeler, belge düzeyi özelleştirmeleri ve VSTO eklentileri için farklıdır.

## <a name="syntax-for-document-level-customizations"></a>Belge düzeyi özelleştirmeleri sözdizimi

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>VSTO eklentileri sözdizimi

```xml
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
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `customization`Öğesi, özelleştirmeye özgü bilgiler içerir. Bu öğe şu ad alanında olmalıdır: `vstov4=urn:schemas-microsoft-com:vsto.v4` . `customization`Her bir Office çözümü için bir öğe vardır. Örneğin, çok projeli bir dağıtımda üç Office çözümü dağıtırsanız, `customization` uygulama bildiriminde üç öğe vardır.

 Derlemenin alt öğeleri de bu ad alanında olmalıdır.

 `customization`Öğesi aşağıdaki özniteliğe sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`id`|Çoklu proje dağıtımı için gereklidir. `id`Öğesi bir Office çözümünü benzersiz bir şekilde tanımlar.|

### <a name="document-level-customizations"></a>Document-Level özelleştirmeler
 `customization`Öğesi aşağıdaki alt öğeye sahiptir.

#### <a name="document"></a>belge
 `document` `vstov4` Ad alanındaki öğesi [&#60;belge&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/document-element-office-development-in-visual-studio.md)tanımlanmıştır.

### <a name="vsto-add-ins"></a>VSTO eklentileri
 `customization`Öğesi aşağıdaki alt öğeye sahiptir.

#### <a name="appaddin"></a>appAddin
 `appAddin`Ad alanındaki öğesi, `vstov4` [Visual Studio&#41;Office geliştirme &#40;&#60;appAddin&#62; öğesi ](../vsto/appaddin-element-office-development-in-visual-studio.md)içinde tanımlanmıştır.

## <a name="example-of-a-document-level-customization"></a>Belge düzeyi özelleştirmesi örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `customization` belge düzeyi özelleştirmesi için öğesini gösterir. Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>VSTO eklentisi örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `customization` VSTO eklentisinin öğesini gösterir. Bu, form bölgelerini içeren bir Outlook VSTO eklentisi. Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
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
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)