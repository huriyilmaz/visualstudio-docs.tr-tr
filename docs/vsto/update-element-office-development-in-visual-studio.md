---
title: "&lt;Update &gt; öğesi (Visual Studio 'Da Office geliştirme)"
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241bddb8c79a01bb1ba6921486a4dc46d99940cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537390"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Update &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `update`Öğesi, çözümün güncelleştirmeleri denet, zaman aralığını belirtir.

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
 `update`Öğesi gereklidir ve `vstav3` ad alanında bulunur.

 `update`Öğesi aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gereklidir. Etkinleştirilen değeri aşağıdaki değerlerden birine ayarlayın:<br /><br /> -   güncelleştirmeleri denetlemek için **true** .<br />-   güncelleştirmelerin denetlenmesini engellemek için **false** .|

 `update`Öğesi aşağıdaki alt öğeleri içerir.

### <a name="expiration"></a>dolmadan
 `expiration`Öğesi gereklidir ve `vstav3` ad alanında bulunur. Bu öğe, çözümün güncelleştirmeleri denetlediğinde kullanılacak aralığı belirtir.

 `expiration`Öğesi aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`maximumAge`| Gereklidir. Bunu bir tamsayıya eşit olarak ayarlayın.|
|`unit`|Gereklidir. `unit`Aşağıdaki değerlerden birine ayarlayın:<br /><br /> -   **saatlerinin**<br />-   **miş**<br />-   **hafta**|

## <a name="example-of-always-checking-for-updates"></a>Güncelleştirmelerin her zaman denetlenme örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `update` Office çözümlerinde güncelleştirmeleri her zaman denetlenecek şekilde ayarlanmış bir öğe göstermektedir.

### <a name="code"></a>Kod

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Varsayılan güncelleştirme aralığı ayarlama örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `update` Office çözümleri için bir uygulama bildiriminde bir öğe gösterir. Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
