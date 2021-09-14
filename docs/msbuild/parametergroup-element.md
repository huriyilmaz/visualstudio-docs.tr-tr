---
title: ParameterGroup Öğesi | Microsoft Docs
description: UsingTask TaskFactory tarafından oluşturulan görevdeki parametrelerin isteğe bağlı bir listesini içeren MSBuild ParameterGroup öğesini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c56eb3b3bfb79bd7896657719157fc6a4bd8e99c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628406"
---
# <a name="parametergroup-element"></a>ParameterGroup öğesi

bir tarafından oluşturulan görev üzerinde mevcut olacak parametrelerin isteğe bağlı bir listesini `UsingTask` `TaskFactory` içerir. Daha fazla bilgi için [bkz. UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>

## <a name="syntax"></a>Syntax

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Parametre](../msbuild/parameter-element.md)|bir tarafından oluşturulan bir görev için belirli bir parametre hakkında bilgi `UsingTask` `TaskFactory` içerir. Öğenin adı parametrenin adıdır.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Usingtask](../msbuild/usingtask-element-msbuild.md) | Görevleri MSBuild'a kaydetmenin bir yolunu sağlar. Projede sıfır veya daha `UsingTask` fazla öğe olabilir. |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğesinin nasıl kullanılalı olduğunu `ParameterGroup` gösterir.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
