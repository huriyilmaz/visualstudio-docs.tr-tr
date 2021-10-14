---
title: '&lt;customizations &gt; öğesi (Office geliştirme Visual Studio)'
description: vstov4 ad alanının özelleştirmeler öğesinin her bir çözümü yükleme ve yükleme hakkında tüm Office öğrenin.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: bc059992ca0f704125feb9e01c4f46f441ed145d
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129967853"
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;customizations &gt; öğesi (Office geliştirme Visual Studio)
  Ad `customizations` alanının `vstov4` öğesi, her bir çözüm için yükleme ve yükleme Office içerir.

## <a name="syntax-for-document-level-customizations"></a>Belge düzeyi özelleştirmeler için söz dizimi

```xml
<customizations>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</customizations>
```

## <a name="syntax-for-vsto-add-ins"></a>VSTO Eklentileri için Söz Dizimi

```xml
<customizations>
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
</customizations>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 öğesi, `customizations` her bir çözümle ilgili Office içerir. Bu öğe aşağıdaki ad alanı içinde yer alalır: `vstov4=urn:schemas-microsoft-com:vsto.v4` . Derlemenin alt öğeleri de bu ad alanına sahip olması gerekir.

 öğesinin `customizations` özniteliği yoktur.

 öğesi `customizations` aşağıdaki alt öğeye sahip.

### <a name="customization"></a>Özelleştirme
 Gereklidir. ad `customization` alanında `vstov4` öğesi, 'de geliştirme [&#60;için&#62; özelleştirme &#40;Office öğesinde Visual Studio&#41;. ](../vsto/customization-element-office-development-in-visual-studio.md)

## <a name="example-of-a-document-level-customization"></a>Belge düzeyinde özelleştirme örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, belge `customizations` düzeyinde özelleştirme için öğesini gösterir.

> [!NOTE]
> Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
  <vstov4:customization>
    <vstov4:document
      solutionId="73e" />
  </vstov4:customization>
</vstov4:customizations>
```

## <a name="example-of-a-vsto-add-in"></a>VSTO Örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, bir `customizations` eklentinin VSTO göstermektedir. Bu, form Outlook VSTO içeren bir eklentidir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
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
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)