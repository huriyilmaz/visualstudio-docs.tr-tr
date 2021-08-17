---
title: '&lt;appaddin &gt; öğesi (Visual Studio Office geliştirme)'
description: vstov4 ad alanının appaddin öğesinin VSTO eklentileri için özelleştirmeye özgü bilgileri nasıl depoladığını öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3e8a6ee4a422c156bfb81108c830f917e5ee8020
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047263"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appaddin &gt; öğesi (Visual Studio Office geliştirme)
  ad alanının **appaddin** öğesi, `vstov4` VSTO eklentileri için özelleştirmeye özgü bilgileri depolar.

## <a name="syntax"></a>Syntax

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 **AppAddin** öğesi zorunludur ve `vstov4` ad alanında yer alan. Uygulama bildiriminde tanımlı yalnızca bir **appAddin** öğesi vardır.

 **AppAddin** öğesi aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|**uygulama**|Gereklidir. Microsoft Office uygulamasını tanımlar. değer aşağıdakilerden biri olabilir: Excel, ınfopath, Outlook, PowerPoint, Project, Visio veya Word.|
|**loadBehavior**|İsteğe bağlı. Varsayılan olarak, **LoadBehavior** bu değerin olarak ayarlanarak etkinleştirilir. hata ayıklama için, VSTO eklentisi değeri iki olarak ayarlanarak devre dışı bırakılabilir. daha fazla bilgi için, [VSTO eklentileri için kayıt defteri girişlerinde](../vsto/registry-entries-for-vsto-add-ins.md)LoadBehavior değerlerini başlıklı tabloya bakın.|
|**Işareti**|Gereklidir. bu değer, uygulama tarafından VSTO eklentisini yüklemek için kullanılacak kayıt defteri anahtarı adıdır. daha fazla bilgi için bkz. [VSTO eklentileri için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).|

 **AppAddin** öğesi aşağıdaki alt öğeleri içerir.

### <a name="friendlyname"></a>friendlyName
 İsteğe bağlı. **friendlyname** öğesi [&#60;friendlyname&#62; öğesi &#40;Visual Studio&#41;Office geliştirme](../vsto/friendlyname-element-office-development-in-visual-studio.md)bölümünde açıklanmaktadır.

### <a name="description"></a>açıklama
 İsteğe bağlı. **description** öğesi [&#60;description&#62; öğesi &#40;Visual Studio&#41;Office geliştirme](../vsto/description-element-office-development-in-visual-studio.md)bölümünde açıklanmaktadır.

### <a name="formregions"></a>formRegions
 yalnızca form bölgelerini içeren Outlook VSTO eklentileri için gereklidir. **formregion** öğesi [&#60;formregion&#62; öğesi &#40;Visual Studio&#41;geliştirme Office](../vsto/formregions-element-office-development-in-visual-studio.md)açıklanmıştır.

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Açıklama
 aşağıdaki kod örneği, kullanılarak dağıtılan bir Outlook çözümünde **appaddin** öğelerini gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
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
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)