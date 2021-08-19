---
title: '&lt;postActions &gt; öğesi (Office geliştirme)'
description: vstav3 ad alanının postActions öğesi, dağıtım sonrası eylemleri açıklayan tüm postAction öğelerini içerir. Bu öğeler, Office yüklendikten sonra ürkür.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9051d2a4947057eed815b234880702c198426949
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147784"
---
# <a name="ltpostactionsgt-element-office-development"></a>&lt;postActions &gt; öğesi (Office geliştirme)
  Ad alanının öğesi, dağıtım sonrası eylemleri açıklayan tüm öğeleri içerir ve bu öğeler, `postActions` `vstav3` Office `postAction` yüklendikten sonra çalıştırıldı.

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
 öğesi `postActions` isteğe bağlıdır ve ad alanı `vstav3` içindedir. Bir uygulama `postActions` bildiriminde tanımlanan yalnızca bir öğe vardır.

 öğesinin `postActions` özniteliği yoktur.

 `postActions` aşağıdaki öğeye sahip.

### <a name="postaction"></a>Postaction
 İsteğe bağlı. ad alanı içinde `postAction` öğenin rolü,&#60;`vstav3` geliştirme&#62; [postAction &#40;Office öğesinde Visual Studio&#41;. ](../vsto/postaction-element-office-development-in-visual-studio.md)

## <a name="post-deployment-action-example"></a>Dağıtım sonrası eylem örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, kullanılarak `postActions` dağıtılan bir uygulama çözümü için uygulama Office öğesini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir Office içerir.](../vsto/application-manifests-for-office-solutions.md)

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

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
