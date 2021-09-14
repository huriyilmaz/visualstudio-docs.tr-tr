---
title: ProjectExtensions Öğesi (MSBuild) | Microsoft Docs
description: Proje dosyalarının belirli bir MSBuild içermesini sağlayan MSBuildProjectExtensions öğesini MSBuild öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0fbf7760af7275172bc57ce0aac097e70182b4f5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625622"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions öğesi (MSBuild)

Proje MSBuild olmayan bilgileri içermesini MSBuild sağlar. Bir öğenin içindeki `ProjectExtensions` her şey, bir öğenin MSBuild.

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>Syntax

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

 Hiçbiri

### <a name="child-elements"></a>Alt öğeleri

 Hiçbiri

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Bir proje dosyasının gerekli MSBuild öğesi. |

## <a name="remarks"></a>Açıklamalar

 Bir `ProjectExtensions` MSBuild projesinde yalnızca bir öğe kullanılabilir.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, bir öğesinde depolanan tümleşik geliştirme ortamındaki bilgileri `ProjectExtensions` gösterir.

```xml
<ProjectExtensions>
    <VSIDE>
        <External>
            <!--
            Raw XML passed to the IDE by an external source
            -->
        </External>
    </VSIDE>
</ProjectExtensions>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
