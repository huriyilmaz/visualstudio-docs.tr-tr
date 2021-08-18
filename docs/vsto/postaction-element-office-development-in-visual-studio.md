---
title: '&lt;postAction &gt; öğesi (Office geliştirme Visual Studio)'
description: vstav3 ad alanının postAction öğesi, giriş noktası öğelerini ve dağıtım sonrası eylemlerle ilişkili tüm postActionData öğelerini içerir. Bu öğeler, Office yüklendikten sonra çalıştırıldı.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ec3988628f579023cddf5ff9f49a47d323fa9742
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032296"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction &gt; öğesi (Office geliştirme Visual Studio)
  Ad alanının öğesi, dağıtım sonrası eylemlerle ilişkilendirilmiş olan öğeleri ve tüm öğeleri içerir. Bu `postAction` `vstav3` `entrypoint` `postActionData` öğeler, Office yüklendikten sonra kullanılır.

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
 öğesi `postAction` isteğe bağlıdır ve ad alanı `vstav3` içindedir. Her dağıtım sonrası `postAction` eylem için bir uygulama bildiriminde tanımlanan bir öğe vardır.

 öğesinin `postAction` özniteliği yoktur.

 `postAction` aşağıdaki öğelere sahiptir.

### <a name="entrypoint"></a>entryPoint
 İsteğe bağlı. ad alanı içinde `entryPoint` öğenin `vstav3` rolü, [&#60;'de geliştirme&#62; entryPoints &#40;Office öğesinde Visual Studio&#41;. ](../vsto/entrypoints-element-office-development-in-visual-studio.md)

### <a name="postactiondata"></a>postActionData
 İsteğe bağlı. ad alanı içinde `postActionData` öğenin rolü, Visual Studio&#41;`vstav3` geliştirme&#60;[postActionData&#62; öğesinde &#40;Office tanımlanır. ](../vsto/postactiondata-element-office-development-in-visual-studio.md)

## <a name="post-deployment-action-example"></a>Dağıtım sonrası eylem örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, kullanılarak `postAction` dağıtılan bir uygulama Office uygulama bildiriminde öğesini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir Office içerir.](../vsto/application-manifests-for-office-solutions.md)

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

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
