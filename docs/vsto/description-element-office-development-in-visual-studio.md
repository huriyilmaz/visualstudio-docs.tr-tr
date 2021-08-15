---
title: '&lt;description &gt; öğesi (Visual Studio Office geliştirme)'
description: vstov4 ad alanının açıklama öğesinin, COM eklentileri iletişim kutusunda görünen Office çözümü için açıklama depoladığını öğrenin.
titleSuffix: ''
ms.custom: secdec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 24377ea58285a87372a590b267ad3301e5bd4d284879cfb44337e0beaaa3cb2c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268410"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;description &gt; öğesi (Visual Studio Office geliştirme)
  `description`ad alanı öğesi, `vstov4` Microsoft Office uygulamalarının COM eklentileri iletişim kutusunda görünen Office çözümünün açıklamasını depolar.

## <a name="syntax"></a>Syntax

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 İsteğe bağlı. `description`Öğesi `vstov4` ad alanıdır. Microsoft Office uygulamaların COM eklentileri iletişim kutusunda görüntülenen eklentinin açıklamasını içerir.

 `description`Öğesinde hiç öznitelik veya öğe yok.

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, `description` kullanılarak dağıtılan bir uygulama düzeyi çözümünün öğesini göstermektedir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . bu kod örneği, [Office çözümleri için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)