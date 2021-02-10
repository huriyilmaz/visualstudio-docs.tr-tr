---
title: "&lt;appAddin &gt; öğesi (Visual Studio 'Da Office geliştirme)"
description: Vstov4 ad alanının appAddin öğesinin, VSTO eklentileri için özelleştirmeye özgü bilgileri nasıl depoladığını öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 427d7bc0ec59b98394b292745985be7fdf69b904
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950516"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin &gt; öğesi (Visual Studio 'Da Office geliştirme)
  Ad alanının **appAddin** Öğesı, `vstov4` VSTO eklentileri için özelleştirmeden özel bilgileri depolar.

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
|**uygulama**|Gereklidir. Microsoft Office uygulamasını tanımlar. Değer aşağıdakilerden biri olabilir: Excel, InfoPath, Outlook, PowerPoint, Project, Visio veya Word.|
|**loadBehavior**|İsteğe bağlı. Varsayılan olarak, **LoadBehavior** bu değerin olarak ayarlanarak etkinleştirilir. Hata ayıklama için, VSTO eklentisi değeri iki olarak ayarlanarak devre dışı bırakılabilir. Daha fazla bilgi için, [VSTO eklentileri Için kayıt defteri girişlerinde](../vsto/registry-entries-for-vsto-add-ins.md)LoadBehavior değerlerini başlıklı tabloya bakın.|
|**Işareti**|Gereklidir. Bu değer, VSTO eklentisini yüklemek için uygulama tarafından kullanılacak kayıt defteri anahtarı adıdır. Daha fazla bilgi için bkz. [VSTO eklentileri Için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).|

 **AppAddin** öğesi aşağıdaki alt öğeleri içerir.

### <a name="friendlyname"></a>friendlyName
 İsteğe bağlı. **FriendlyName** öğesi [&#60;FriendlyName&#62; öğesi Visual&#41;Studio 'da Office geliştirme &#40;](../vsto/friendlyname-element-office-development-in-visual-studio.md)açıklanmaktadır.

### <a name="description"></a>açıklama
 İsteğe bağlı. **Description** öğesi [&#60;Description&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/description-element-office-development-in-visual-studio.md)açıklanmaktadır.

### <a name="formregions"></a>formRegions
 Yalnızca form bölgelerini içeren Outlook VSTO eklentileri için gereklidir. **FormRegion** öğesi, [Visual&#41;Studio 'da Office geliştirme &#40;&#60;FormRegion&#62; öğesi](../vsto/formregions-element-office-development-in-visual-studio.md)açıklanmaktadır.

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, kullanılarak dağıtılan bir Outlook çözümünde **appAddin** öğelerini gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

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
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)