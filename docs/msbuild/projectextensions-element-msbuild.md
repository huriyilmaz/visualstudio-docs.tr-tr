---
title: Projecısions öğesi (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1057743732c8dfc7ebb05bc9cbc108d61b2e234c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597418"
---
# <a name="projectextensions-element-msbuild"></a>Projecısions öğesi (MSBuild)
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyalarının[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] olmayan bilgiler içermesini sağlar. `ProjectExtensions` öğesinin içindeki her şey [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]tarafından yok sayılır.

 \<Proje > \<Projecbir >

## <a name="syntax"></a>Sözdizimi

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}
 Yok.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyasının gerekli kök öğesi. |

## <a name="remarks"></a>Açıklamalar
 Bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projesinde yalnızca bir `ProjectExtensions` öğesi kullanılabilir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, bir `ProjectExtensions` öğesinde depolanan tümleşik geliştirme ortamının bilgilerini gösterir.

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
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
