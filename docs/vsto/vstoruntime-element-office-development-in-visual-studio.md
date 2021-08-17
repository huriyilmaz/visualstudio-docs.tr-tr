---
title: '&lt;vstoruntime &gt; öğesi (Visual Studio Office geliştirme)'
titleSuffix: ''
description: vstav3 ad alanının vstoruntime öğesi, belirli bir Office çözümü için Office için Visual Studio Araçları çalışma zamanının desteklenen bir sürümünü içerir.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1ce97744f8b7fc93317c80755b01ede222df2a4b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025647"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoruntime &gt; öğesi (Visual Studio Office geliştirme)
  `vstoRuntime`ad alanı öğesi, `vstav3` belirli bir Office çözümü için Office için Visual Studio Araçları çalışma zamanının desteklenen bir sürümünü içerir.

## <a name="syntax"></a>Syntax

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `vstoRuntime`Öğesi gereklidir ve `vstav3` ad alanında bulunur. bir Office çözümü Office için Visual Studio Araçları çalışma zamanının iki sürümünü destekliyorsa, `vstoRuntime` uygulama bildiriminde iki öğe vardır.

 `vstoRuntime`Öğesi aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`release`|Gereklidir. Office için Visual Studio Araçları çalışma zamanının yayın sürümü.|
|`version`|Gereklidir. Office için Visual Studio Araçları çalışma zamanının sürüm numarası.|
|`supportUrl`|İsteğe bağlı. Office için Visual Studio Araçları çalışma zamanının yükleme konumuna bağlantı.|

 `vstoRuntime` öğesi yok.

## <a name="example"></a>Örnek
 aşağıdaki kod örneği, `vstoRuntime` kullanılarak dağıtılan bir Office çözümü için uygulama bildiriminde bulunan öğeyi gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)
