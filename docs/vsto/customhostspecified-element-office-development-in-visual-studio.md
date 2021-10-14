---
title: '&lt;customhostbelirtilen &gt; öğesi (Visual Studio Office geliştirme)'
description: Customhostbelirtilen öğesinin, bu çözümün tek başına bir uygulama olmadığını nasıl gösterir olduğunu öğrenin.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 37d9d81fefe29f9830c4fd0581c3df77aeca28ee
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969235"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customhostbelirtilen &gt; öğesi (Visual Studio Office geliştirme)
  `customHostSpecified`Öğesi bu çözümün tek başına bir uygulama olmadığını gösterir. Office çözümleri, Microsoft Office uygulamalar içinde barındırılan bileşenleri içerir.

## <a name="syntax"></a>Syntax

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `customHostSpecified`Office çözümleri için öğesi gereklidir. Bu öğe `co.v1` ad alanında bulunur ve bu dağıtımın özel bir ana bilgisayar içinde dağıtılacak bir bileşen içerdiğini ve tek başına bir uygulama oluşturmadığını belirtir.

 Bu öğe, uygulama bildirimindeki ilk öğenin bir alt öğesidir `<entrypoint>` . Bu öğede başka alt öğe yok `<entrypoint>` veya [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] yükleme sırasında doğrulama hatası oluşturacak.

 Bu öğenin hiç özniteliği yok ve alt öğesi yok.

## <a name="example"></a>Örnek
 aşağıdaki kod örneği, `customHostSpecified` bir Office çözümü için uygulama bildiriminde bulunan öğeyi gösterir. bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)