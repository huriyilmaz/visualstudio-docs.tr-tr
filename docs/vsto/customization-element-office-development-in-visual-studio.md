---
title: '&lt;özelleştirme &gt; öğesi (Office geliştirme Visual Studio)'
description: vstov4 ad alanının özelleştirme öğesinin belirli bir Office öğrenin.
titleSuffix: ''
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9405b25f5bf354a39a2aa2d9b920e3da0cd144b1
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972147"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;özelleştirme &gt; öğesi (Office geliştirme Visual Studio)
  Ad `customization` alanının `vstov4` öğesi, belirli bir Office açıklar. Alt öğeler, belge düzeyi özelleştirmeler ve VSTO farklıdır.

## <a name="syntax-for-document-level-customizations"></a>Belge düzeyi özelleştirmeler için söz dizimi

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>VSTO Eklentileri için Söz Dizimi

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
 öğesi `customization` özelleştirmeye özgü bilgiler içerir. Bu öğe aşağıdaki ad alanı içinde yer alalır: `vstov4=urn:schemas-microsoft-com:vsto.v4` . Her bir çözüm `customization` için bir Office vardır. Örneğin, çok projeli bir Office dağıtımda üç farklı çözüm dağıtırsanız, uygulama `customization` bildiriminde üç öğe vardır.

 Derlemenin alt öğeleri de bu ad alanına sahip olması gerekir.

 öğesi `customization` aşağıdaki özniteliğine sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`id`|Çok projeli dağıtım için gereklidir. öğesi, `id` bir uygulama çözümünü Office tanımlar.|

### <a name="document-level-customizations"></a>Document-Level özelleştirmeleri
 öğesi `customization` aşağıdaki alt öğeye sahip.

#### <a name="document"></a>belge
 ad `document` alanı `vstov4` öğesi, öğesinde geliştirme [&#60;için&#62; belge &#40;Office öğesinde Visual Studio&#41;. ](../vsto/document-element-office-development-in-visual-studio.md)

### <a name="vsto-add-ins"></a>VSTO Eklentiler
 öğesi `customization` aşağıdaki alt öğeye sahip.

#### <a name="appaddin"></a>Appaddin
 ad `appAddin` alanı öğesi `vstov4` [appAddin&#60;öğesinde tanımlanır&#62; geliştirme &#40;Office öğesi Visual Studio&#41;. ](../vsto/appaddin-element-office-development-in-visual-studio.md)

## <a name="example-of-a-document-level-customization"></a>Belge düzeyinde özelleştirme örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, belge `customization` düzeyinde özelleştirme için öğesini gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>VSTO Örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, bir `customization` eklentinin VSTO göstermektedir. Bu, form Outlook VSTO içeren bir eklentidir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

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

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)