---
title: '&lt;appAddin &gt; öğesi (Office geliştirme Visual Studio)'
description: vstov4 ad alanının appAddin öğesinin, eklenti eklemeler için özelleştirmeye VSTO depolay olduğunu öğrenin.
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
ms.openlocfilehash: 3ccde6860ac1ef0935346669b20c07e8c434549bc0b878a1b801b3153fe38168
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440896"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin &gt; öğesi (Office geliştirme Visual Studio)
  Ad **alanının appAddin** `vstov4` öğesi, uygulama eklentileri için özelleştirmeye VSTO bilgileri depolar.

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
 **appAddin** öğesi gereklidir ve ad alanı `vstov4` içindedir. Uygulama bildiriminde **tanımlanan yalnızca bir appAddin** öğesi vardır.

 **appAddin öğesi** aşağıdaki özniteliklere sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|**uygulama**|Gereklidir. Uygulamanın Microsoft Office tanımlar. Değer şu değerlerden biri olabilir: Excel, InfoPath, Outlook, PowerPoint, Project, Visio veya Word.|
|**Loadbehavior**|İsteğe bağlı. **LoadBehavior varsayılan olarak** bu değer olarak ayarlanmadan etkinleştirilir. Hata ayıklama için VSTO değeri iki olarak ayar tarafından devre dışı bırakılabilir. Daha fazla bilgi için, uygulama eklentileri için Kayıt Defteri girdilerinde LoadBehavior [Values VSTO bakın.](../vsto/registry-entries-for-vsto-add-ins.md)|
|**Keyname**|Gereklidir. Bu değer, uygulama tarafından eklentiyi yüklemek için kullanılacak kayıt defteri VSTO adıdır. Daha fazla bilgi için [bkz. Eklentilerini VSTO kayıt defteri girdileri.](../vsto/registry-entries-for-vsto-add-ins.md)|

 **appAddin öğesi** aşağıdaki alt öğelere sahiptir.

### <a name="friendlyname"></a>Friendlyname
 İsteğe bağlı. **friendlyName öğesi,** öğesinde [&#60;geliştirme&#62; friendlyName &#40;Office öğesinde Visual Studio&#41;.](../vsto/friendlyname-element-office-development-in-visual-studio.md)

### <a name="description"></a>açıklama
 İsteğe bağlı. Description **öğesi,** öğesinde [&#60;geliştirme&#62; için &#40;Office açıklamasında Visual Studio&#41;.](../vsto/description-element-office-development-in-visual-studio.md)

### <a name="formregions"></a>Formregions
 Yalnızca form Outlook VSTO ek eklentiler için gereklidir. **formRegions öğesi,** [formRegions&#60;geliştirme&#62; için formRegions &#40;Office öğesinde Visual Studio&#41;.](../vsto/formregions-element-office-development-in-visual-studio.md)

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, kullanılarak dağıtılan bir Outlook **appAddin** öğelerini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] göstermektedir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir Office içerir.](../vsto/application-manifests-for-office-solutions.md)

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

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)