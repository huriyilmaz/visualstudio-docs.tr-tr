---
title: '&lt;postActionData &gt; öğesi (Office geliştirme)'
description: Vstav3 ad alanının postActionData öğesi, Office çözümleri yüklendikten sonra çalışan dağıtım sonrası eylemleriyle ilişkili verileri belirtir.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a75f61c6d1f80a127f49d96c4e3f4910c66dd8aa
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470072"
---
# <a name="ltpostactiondatagt-element-office-development"></a>&lt;postActionData &gt; öğesi (Office geliştirme)
  `postActionData`Ad alanı öğesi, `vstav3` Office çözümleri yüklendikten sonra çalışan dağıtım sonrası eylemleriyle ilişkili verileri belirtir.

## <a name="syntax"></a>Syntax

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `postActionData`Öğesi isteğe bağlıdır ve `vstav3` ad alanıdır. `postActionData`Her dağıtım sonrası eylemi için uygulama bildiriminde tanımlanan bir öğe vardır.

 `postActions`Öğesinde hiç öznitelik yok.

 `postActions` alt öğesi yok.

## <a name="post-deployment-action-example"></a>Dağıtım sonrası eylem örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, `postAction` kullanılarak dağıtılan bir Office çözümünün uygulama bildiriminde bulunan öğesini göstermektedir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
