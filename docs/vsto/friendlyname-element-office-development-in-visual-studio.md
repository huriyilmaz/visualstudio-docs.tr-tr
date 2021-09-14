---
description: Vstov4 ad alanının friendlyName öğesi, yüklü programlar listesinde görüntülenen adı depolar.
title: '&lt;friendlyName &gt; öğesi (Visual Studio Office geliştirme)'
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 887c28cdd81f4f3176dcf29804fa9f6ec4b27123
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634081"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName &gt; öğesi (Visual Studio Office geliştirme)
  `friendlyName`Ad alanı öğesi, `vstov4` yüklü programlar listesinde görünen adı depolar.

## <a name="syntax"></a>Syntax

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `friendlyName`Öğesi `vstov4` ad alanıdır. değer, bilgisayardaki yüklü programlar listesinde ve Microsoft Office uygulamaların COM VSTO eklentileri iletişim kutusunda görünür.

 `friendlyName`Öğesinde hiç öznitelik veya alt öğe yok.

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, `friendlyName` kullanılarak dağıtılan bir uygulama düzeyi çözümünde öğesini gösterir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)
