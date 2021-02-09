---
title: Output öğesi (MSBuild) | Microsoft Docs
description: Öğe ve özelliklerde görev çıkış değerlerini depolayan, bkz. öznitelikler, öğeler ve MSBuild output öğesi örneği.
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
ms.workload:
- multiple
ms.openlocfilehash: d69f1e4960ad2f9e11b8ac0248033e5ff425262d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905317"
---
# <a name="output-element-msbuild"></a>Output öğesi (MSBuild)

Öğe ve özelliklerde görev çıkış değerlerini depolar.

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
|`PropertyName`|Ya da `PropertyName` `ItemName` özniteliği gereklidir.<br /><br /> Görevin çıkış parametre değerini alan özellik. Projeniz daha sonra $ ( \<PropertyName> ) sözdizimiyle özelliğe başvurabilir. Bu özellik adı yeni bir özellik adı veya projede zaten tanımlanmış bir ad olabilir.<br /><br /> Bu öznitelik `ItemName` de kullanılıyorsa kullanılamaz.|
|`ItemName`|Ya da `PropertyName` `ItemName` özniteliği gereklidir.<br /><br /> Görevin çıkış parametre değerini alan öğe. Projeniz daha sonra @ ( \<ItemName> ) söz dizimine sahip öğeye başvurabilir. Öğe adı yeni bir öğe adı ya da projede zaten tanımlanmış bir ad olabilir. Öğe adı varolan bir öğe olduğunda, çıkış parametresi değerleri var olan öğeye eklenir. <br /><br /> Bu öznitelik `PropertyName` de kullanılıyorsa kullanılamaz.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Görev](../msbuild/task-element-msbuild.md) | MSBuild görevi örneğini oluşturur ve yürütür. |

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği `Csc` bir öğesi içinde yürütülen görevi gösterir `Target` . Görev parametrelerine geçirilen öğeler ve özellikler bu örneğin kapsamı dışında bildirilmiştir. Çıkış parametresindeki değer `OutputAssembly` `FinalAssemblyName` öğede depolanır ve çıkış parametresindeki değer `BuildSucceeded` `BuildWorked` özelliğinde depolanır. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

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

- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
