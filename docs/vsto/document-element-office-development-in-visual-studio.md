---
description: vstov4 ad alanının belge öğesi, belge düzeyinde özelleştirmeler için özelleştirmeye özgü bilgileri depolar.
title: '&lt;document &gt; öğesi (Office geliştirme Visual Studio)'
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 66ef774db63c01a1b622c6ea937bd29444bc3d71
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634142"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;document &gt; öğesi (Office geliştirme Visual Studio)
  Ad `document` alanının `vstov4` öğesi, belge düzeyinde özelleştirmeler için özelleştirmeye özgü bilgileri depolar.

## <a name="syntax"></a>Syntax

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 Yalnızca belge düzeyinde özelleştirmeler için gereklidir. öğesi `document` ad alanı `vstov4` içindedir. öğesi `document` aşağıdaki özniteliklere sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`solutionId`|Gereklidir. Belge düzeyi bir çözümü Office için Visual Studio Araçları için çalışma zamanı tarafından kullanılan GUID. Bu değer, özel belge _AssemblyLocation olarak depolanır. Daha fazla bilgi için [bkz. Özel belge özelliklerine genel bakış.](../vsto/custom-document-properties-overview.md)|

 `document` alt öğeye sahip değil.

## <a name="document-level-customization-example"></a>Belge düzeyi özelleştirme örneği

### <a name="description"></a>Description
 Aşağıdaki kod örneği, kullanılarak `document` dağıtılan bir belge düzeyi Office çözümünde öğesini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir Office içerir.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
