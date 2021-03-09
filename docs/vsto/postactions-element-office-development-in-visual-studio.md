---
title: '&lt;Postalamalar &gt; öğesi (Office geliştirme)'
description: Vstav3 ad alanının Postalamalar öğesi, Office çözümleri yüklendikten sonra çalıştırılan dağıtım sonrası eylemleri açıklayan tüm postaçalıştır öğelerini içerir.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5c4a66e270cd446996884262d380df0f7384f54f
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470046"
---
# <a name="ltpostactionsgt-element-office-development"></a>&lt;Postalamalar &gt; öğesi (Office geliştirme)
  `postActions`Ad alanı öğesi, `vstav3` `postAction` Office çözümleri yüklendikten sonra çalıştırılan dağıtım sonrası eylemleri açıklayan tüm öğeleri içerir.

## <a name="syntax"></a>Syntax

```xml
<postActions>
  <postAction>
    <entryPoint>
    </entryPoint>
    <postActionData>
    </postActionData>
  </postAction>
</postActions>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `postActions`Öğesi isteğe bağlıdır ve `vstav3` ad alanıdır. `postActions`Uygulama bildiriminde tanımlı yalnızca bir öğe vardır.

 `postActions`Öğesinde hiç öznitelik yok.

 `postActions` Aşağıdaki öğeye sahiptir.

### <a name="postaction"></a>Postaeylemi
 İsteğe bağlı. `postAction`Ad alanındaki öğesinin rolü, `vstav3` [Visual&#41;Studio 'da Office geliştirme &#40;&#60;postatransaction&#62; öğesi ](../vsto/postaction-element-office-development-in-visual-studio.md)içinde tanımlanmıştır.

## <a name="post-deployment-action-example"></a>Dağıtım sonrası eylem örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, `postActions` kullanılarak dağıtılan bir Office çözümünün uygulama bildiriminde bulunan öğesini göstermektedir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstav3:postActions>
  <vstav3:postAction>
    <vstav3:entryPoint
      class="PostDeploymentAction.PostDeploymentActionSample">
      <assemblyIdentity
        name="PostDeploymentAction"
        version="1.0.0.0"
        language="neutral"
        processorArchitecture="msil" />
    </vstav3:entryPoint>
    <vstav3:postActionData>
    </vstav3:postActionData>
  </vstav3:postAction>
</vstav3:postActions>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
