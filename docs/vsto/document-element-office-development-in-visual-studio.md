---
description: Vstov4 ad alanının belge öğesi, belge düzeyi özelleştirmeleri için özelleştirmeye özgü bilgileri depolar.
title: "&lt;Document &gt; öğesi (Visual Studio 'Da Office geliştirme)"
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3563169bd9b567cd974248bf4185cb9bc8a7b022
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221047"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;Document &gt; öğesi (Visual Studio 'Da Office geliştirme)
  `document`Ad alanının öğesi, `vstov4` belge düzeyi özelleştirmeleri için özelleştirmeye özgü bilgileri depolar.

## <a name="syntax"></a>Syntax

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 Yalnızca belge düzeyi özelleştirmeleri için gereklidir. `document`Öğesi `vstov4` ad alanıdır. `document`Öğesi aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`solutionId`|Gereklidir. Office çalışma zamanı için Visual Studio Araçları tarafından, belge düzeyinde bir çözümü benzersiz şekilde tanımlamak için kullanılan GUID. Bu değer, _AssemblyLocation özel belge özelliği olarak depolanır. Daha fazla bilgi için bkz. [özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md).|

 `document` alt öğesi yok.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirmesi örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, `document` kullanılarak dağıtılan bir belge düzeyi Office çözümünde öğesini göstermektedir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Bu kod örneği, [Office çözümleri Için uygulama bildirimlerinde](../vsto/application-manifests-for-office-solutions.md)sunulan daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
