---
title: "&lt;Postatransaction &gt; öğesi (Visual Studio 'Da Office geliştirme)"
description: Vstav3 ad alanının postalandırma öğesi, giriş noktası öğelerini ve Office çözümleri yüklendikten sonra çalıştırılan dağıtım sonrası eylemlerle ilişkili tüm postaverileri öğelerini içerir.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04f8c92c52aeee9f7f1dd5ab67b3dcef3a295474
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470059"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;Postatransaction &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `postAction`Ad alanı öğesi, `vstav3` `entrypoint` `postActionData` Office çözümleri yüklendikten sonra çalıştırılan dağıtım sonrası eylemlerle ilişkili öğeleri ve tüm öğeleri içerir.

## <a name="syntax"></a>Syntax

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `postAction`Öğesi isteğe bağlıdır ve `vstav3` ad alanıdır. `postAction`Her dağıtım sonrası eylemi için uygulama bildiriminde tanımlanan bir öğe vardır.

 `postAction`Öğesinde hiç öznitelik yok.

 `postAction` Aşağıdaki öğelere sahiptir.

### <a name="entrypoint"></a>Noktası
 İsteğe bağlı. `entryPoint` `vstav3` Ad alanındaki öğesinin rolü [&#60;entryPoints&#62; öğesi &#40;Visual Studio 'da Office geliştirme&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)' nde tanımlanmıştır.

### <a name="postactiondata"></a>postActionData
 İsteğe bağlı. `postActionData`Ad alanındaki öğesinin rolü, `vstav3` [Visual Studio&#41;Office geliştirme &#40;&#60;postactiondata&#62; öğesinde ](../vsto/postactiondata-element-office-development-in-visual-studio.md)tanımlanmıştır.

## <a name="post-deployment-action-example"></a>Dağıtım sonrası eylem örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, `postAction` kullanılarak dağıtılan bir Office çözümü için uygulama bildiriminde bulunan öğesini gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
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
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
