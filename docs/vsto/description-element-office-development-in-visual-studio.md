---
title: '&lt;description &gt; öğesi (Office geliştirme Visual Studio)'
description: vstov4 ad alanının açıklama öğesinin COM eklentileri iletişim kutusunda görünen Office çözümü için açıklamayı depolar.
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
ms.openlocfilehash: 8c20ccff5941fc03bec7aac314f680912b45da7d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038064"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;description &gt; öğesi (Office geliştirme Visual Studio)
  Ad alanının öğesi, Office uygulamalarının COM eklentileri iletişim kutusunda görünen Microsoft Office `description` `vstov4` depolar.

## <a name="syntax"></a>Syntax

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 İsteğe bağlı. öğesi `description` ad alanı `vstov4` içindedir. Uygulama uygulamalarının COM eklentileri iletişim kutusunda görünen eklentinin açıklamasını Microsoft Office içerir.

 öğesinin `description` özniteliği veya öğesi yok.

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği kullanılarak `description` dağıtılan bir uygulama düzeyi çözümü için öğesini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] göstermektedir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir Office içerir.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)