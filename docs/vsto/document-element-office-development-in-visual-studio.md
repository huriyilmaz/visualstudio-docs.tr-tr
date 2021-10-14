---
description: vstov4 ad alanının belge öğesi, belge düzeyinde özelleştirmeler için özelleştirmeye özgü bilgileri depolar.
title: '&lt;document &gt; öğesi (Office geliştirme Visual Studio)'
titleSuffix: ''
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
ms.openlocfilehash: 66506aeb6b65050738c4d7a4a37ac0e4caf0ed1e
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971068"
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
 Aşağıdaki kod örneği, kullanılarak `document` dağıtılan belge düzeyinde bir Office çözümünde öğesini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir örneğin Office yer almaktadır.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
