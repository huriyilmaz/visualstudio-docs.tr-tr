---
title: '&lt;güncelleştirme &gt; öğesi (Visual Studio Office geliştirme)'
description: Update öğesi, çözümün güncelleştirmeleri denet, zaman aralığını belirtir.
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
ms.openlocfilehash: 066d5a29329764fcca8cba0e8faaa936b10292c4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025686"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;güncelleştirme &gt; öğesi (Visual Studio Office geliştirme)
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

### <a name="description"></a>Açıklama
 aşağıdaki kod örneği, `update` Office çözümlerinde güncelleştirmeleri her zaman denetlenecek şekilde ayarlanmış bir öğe gösterir.

### <a name="code"></a>Kod

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Varsayılan güncelleştirme aralığı ayarlama örneği

### <a name="description"></a>Açıklama
 aşağıdaki kod örneği, `update` Office çözümleri için bir uygulama bildiriminde bir öğe gösterir. bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce kullanarak Office çözümünü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)
