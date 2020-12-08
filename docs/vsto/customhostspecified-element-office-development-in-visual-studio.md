---
title: "&lt;Customhostbelirtilen &gt; öğesi (Visual Studio 'Da Office geliştirme)"
description: Customhostbelirtilen öğesinin, bu çözümün tek başına bir uygulama olmadığını nasıl gösterir olduğunu öğrenin.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8327c6e154f051f5ce79d41ceaa696e330c794f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848137"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;Customhostbelirtilen &gt; öğesi (Visual Studio 'Da Office geliştirme)
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
 Aşağıdaki kod örneği, `customHostSpecified` bir Office çözümünün uygulama bildiriminde öğesini gösterir. Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)