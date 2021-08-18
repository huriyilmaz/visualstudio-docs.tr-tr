---
title: Output Öğesi (MSBuild) | Microsoft Docs
description: Özniteliklere, öğelere ve görev çıkış değerlerini öğelerde ve özelliklerde depolar MSBuild çıkış öğesinin bir örneğine bakın.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: a9192de1f2d56017be3bf3036170cd183a191ed8393dac8d3a912091c0fe14f0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121356016"
---
# <a name="output-element-msbuild"></a>Çıkış öğesi (MSBuild)

Görev çıkış değerlerini öğelerde ve özelliklerde depolar.

 \<Project> \<Target>
 \<Task>
 \<Output>

## <a name="syntax"></a>Syntax

```xml
<Output TaskParameter="Parameter"
    PropertyName="PropertyName"
    Condition = "'String A' == 'String B'" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`TaskParameter`|Gerekli öznitelik.<br /><br /> Görevin çıkış parametresinin adı.|
|`PropertyName`|veya `PropertyName` özniteliği `ItemName` gereklidir.<br /><br /> Görevin çıkış parametresi değerini alan özellik. Projeniz daha sonra $( ) söz dizimi ile \<PropertyName> özelliğine başvurabilirsiniz. Bu özellik adı yeni bir özellik adı veya projede zaten tanımlanmış bir ad olabilir.<br /><br /> Bu öznitelik de `ItemName` kullanılıyorsa kullanılamaz.|
|`ItemName`|veya `PropertyName` özniteliği `ItemName` gereklidir.<br /><br /> Görevin çıkış parametresi değerini alan öğe. Projeniz daha sonra öğeye @( ) söz dizimi \<ItemName> ile başvurabilirsiniz. Öğe adı yeni bir öğe adı veya projede zaten tanımlanmış bir ad olabilir. Öğe adı mevcut bir öğe olduğunda, çıkış parametresi değerleri var olan öğeye eklenir. <br /><br /> Bu öznitelik de `PropertyName` kullanılıyorsa kullanılamaz.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Görev](../msbuild/task-element-msbuild.md) | Bir görev örneği oluşturur ve MSBuild yürütür. |

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, `Csc` bir öğenin içinde yürütülen görevi `Target` gösterir. Görev parametrelerine geçirilen öğeler ve özellikler, bu örneğin kapsamı dışında bildirildi. Çıkış parametresinden gelen değer öğede depolanır ve çıkış `OutputAssembly` `FinalAssemblyName` parametresinden gelen değer `BuildSucceeded` özelliğinde `BuildWorked` depolanır. Daha fazla bilgi için bkz. [Görevler.](../msbuild/msbuild-tasks.md)

```xml
<Target Name="Compile" DependsOnTargets="Resources">
    <Csc  Sources="@(CSFile)"
            TargetType="library"
            Resources="@(CompiledResources)"
            EmitDebugInformation="$(includeDebugInformation)"
            References="@(Reference)"
            DebugType="$(debuggingType)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
        <Output TaskParameter="BuildSucceeded"
                  PropertyName="BuildWorked" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
