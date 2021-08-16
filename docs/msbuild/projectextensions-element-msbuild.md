---
title: Projecısions öğesi (MSBuild) | Microsoft Docs
description: MSBuild proje dosyalarının MSBuild olmayan bilgileri içermesini sağlayan msbuildprojecısions öğesi hakkında bilgi edinin.
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
ms.openlocfilehash: 850bef50c5e381c4e15aa1967ca49382362bcf027eabd5330015f06da9d95373
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270425"
---
# <a name="projectextensions-element-msbuild"></a>Projecısions öğesi (MSBuild)

MSBuild proje dosyalarının MSBuild olmayan bilgiler içermesini sağlar. Bir öğenin içindeki her şey `ProjectExtensions` MSBuild yok sayılır.

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
| [Project](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="remarks"></a>Açıklamalar

 `ProjectExtensions`MSBuild projesinde yalnızca bir öğe kullanılabilir.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, bir öğesinde depolanan tümleşik geliştirme ortamının bilgilerini gösterir `ProjectExtensions` .

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

- [Project dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
