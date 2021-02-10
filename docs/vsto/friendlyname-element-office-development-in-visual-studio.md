---
title: "&lt;friendlyName &gt; öğesi (Visual Studio 'Da Office geliştirme)"
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c04a7a90f32051cc211fece4f27f1f46f8fb92f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939272"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `friendlyName`Ad alanı öğesi, `vstov4` yüklü programlar listesinde görünen adı depolar.

## <a name="syntax"></a>Syntax

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `friendlyName`Öğesi `vstov4` ad alanıdır. Değer, bilgisayardaki yüklü programlar listesinde ve Microsoft Office uygulamaların COM VSTO eklentileri iletişim kutusunda görünür.

 `friendlyName`Öğesinde hiç öznitelik veya alt öğe yok.

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `friendlyName` kullanılarak dağıtılan bir uygulama düzeyi çözümünde öğesini gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)