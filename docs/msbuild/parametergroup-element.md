---
title: ParameterGroup Öğesi | Microsoft Docs
description: Bir UsingTask TaskFactory tarafından oluşturulan görevde bulunan isteğe bağlı parametrelerin bir listesini içeren MSBuild ParameterGroup öğesi hakkında bilgi edinin.
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
ms.workload:
- multiple
ms.openlocfilehash: 56ff9c63de40f6a352c10f92b937a397c683fc65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905299"
---
# <a name="parametergroup-element"></a>ParameterGroup öğesi

Tarafından oluşturulan görevde mevcut olacak parametrelerin isteğe bağlı bir listesini içerir `UsingTask` `TaskFactory` . Daha fazla bilgi için bkz. [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

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
|[Parametre](../msbuild/parameter-element.md)|Tarafından oluşturulan bir görev için belirli bir parametre hakkında bilgi içerir `UsingTask` `TaskFactory` . Öğesinin adı parametrenin adıdır.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | MSBuild 'e görevleri kaydetmek için bir yol sağlar. Bir projede sıfır veya daha fazla `UsingTask` öğe olabilir. |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğesinin nasıl kullanılacağını gösterir `ParameterGroup` .

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
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
