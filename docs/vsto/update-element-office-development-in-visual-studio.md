---
title: '&lt;update &gt; öğesi (Office geliştirme Visual Studio)'
description: Update öğesi, çözümün güncelleştirmeleri denetleme aralığını belirtir.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 35f082a176c958ea40539fac594f1119405de819b7ab054f4c51010aff2044a3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121365932"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;update &gt; öğesi (Office geliştirme Visual Studio)
  `update`öğesi, çözümün güncelleştirmeleri denetleme aralığını belirtir.

## <a name="syntax"></a>Syntax

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 öğesi `update` gereklidir ve ad alanı `vstav3` içindedir.

 öğesi `update` aşağıdaki özniteliklere sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gereklidir. Etkin olarak aşağıdaki değerlerden birini ayarlayın:<br /><br /> -   **güncelleştirmeleri** kontrol etmek için true.<br />-   **güncelleştirmeleri** denetlemeyi önlemek için false.|

 öğesi `update` aşağıdaki alt öğelere sahiptir.

### <a name="expiration"></a>Sona erme
 öğesi `expiration` gereklidir ve ad alanı `vstav3` içindedir. Bu öğe, çözümün güncelleştirmeleri kontrol aralığı belirtir.

 öğesi `expiration` aşağıdaki özniteliklere sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`maximumAge`| Gereklidir. Bunu bir tamsayıya eşit olarak ayarlayın.|
|`unit`|Gereklidir. Aşağıdaki `unit` değerlerden biri olarak ayarlayın:<br /><br /> -   **Saat**<br />-   **Gün**<br />-   **Hafta**|

## <a name="example-of-always-checking-for-updates"></a>Her zaman güncelleştirmeleri denetleme örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, çözümlerde `update` her zaman güncelleştirmeleri denetlemesi için ayarlanmış bir Office göstermektedir.

### <a name="code"></a>Kod

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Varsayılan güncelleştirme aralığı ayarlama örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, uygulama çözümleri `update` için uygulama bildiriminde bir Office gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir Office içerir.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office kullanarak bir Office çözümü ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
