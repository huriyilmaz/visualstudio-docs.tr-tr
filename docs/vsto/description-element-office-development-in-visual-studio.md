---
title: "&lt;Description &gt; öğesi (Visual Studio 'Da Office geliştirme)"
description: Vstov4 ad alanının açıklama öğesinin, COM eklentileri iletişim kutusunda görüntülenen Office çözümünün açıklamasını depoladığını öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 377599e770a93faca9e283ec543091508b773bc7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846239"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Description &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `description`Ad alanı öğesi, `vstov4` MICROSOFT OFFICE uygulamaların com eklentileri iletişim kutusunda görüntülenen Office çözümünün açıklamasını depolar.

## <a name="syntax"></a>Syntax

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 İsteğe bağlı. `description`Öğesi `vstov4` ad alanıdır. Microsoft Office uygulamaların COM eklentileri iletişim kutusunda görüntülenen eklentinin açıklamasını içerir.

 `description`Öğesinde hiç öznitelik veya öğe yok.

## <a name="vsto-add-in-example"></a>VSTO eklentisi örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, `description` kullanılarak dağıtılan bir uygulama düzeyi çözümünün öğesini göstermektedir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

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
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)