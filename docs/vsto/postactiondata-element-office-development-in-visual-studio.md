---
title: '&lt;postActionData &gt; öğesi (Office geliştirme)'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 85e1a02dbb85094cf84e1bba05e900d0e3f2c641
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583729"
---
# <a name="ltpostactiondatagt-element-office-development"></a>&lt;postActionData &gt; öğesi (Office geliştirme)
  `postActionData`Ad alanı öğesi, `vstav3` Office çözümleri yüklendikten sonra çalışan dağıtım sonrası eylemleriyle ilişkili verileri belirtir.

## <a name="syntax"></a>Sözdizimi

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
