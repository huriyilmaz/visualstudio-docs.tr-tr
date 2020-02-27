---
title: Output öğesi (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90fbd517608c9c36db0b1035f296b9d9402abddd
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633037"
---
# <a name="output-element-msbuild"></a>Output öğesi (MSBuild)

Öğe ve özelliklerde görev çıkış değerlerini depolar.

 \<Proje > \<hedef > \<> \<) >

## <a name="syntax"></a>Sözdizimi

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
|`PropertyName`|`PropertyName` ya da `ItemName` özniteliği gereklidir.<br /><br /> Görevin çıkış parametre değerini alan özellik. Projeniz daha sonra $ (\<PropertyName >) söz dizimine sahip özelliğe başvurabilir. Bu özellik adı yeni bir özellik adı veya projede zaten tanımlanmış bir ad olabilir.<br /><br /> `ItemName` de kullanılıyorsa bu öznitelik kullanılamaz.|
|`ItemName`|`PropertyName` ya da `ItemName` özniteliği gereklidir.<br /><br /> Görevin çıkış parametre değerini alan öğe. Projeniz daha sonra @ (\<ItemName >) söz dizimine sahip öğeye başvuru yapabilir. Öğe adı yeni bir öğe adı ya da projede zaten tanımlanmış bir ad olabilir. Öğe adı varolan bir öğe olduğunda, çıkış parametresi değerleri var olan öğeye eklenir. <br /><br /> `PropertyName` de kullanılıyorsa bu öznitelik kullanılamaz.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Görev](../msbuild/task-element-msbuild.md) | MSBuild görevi örneğini oluşturur ve yürütür. |

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, bir `Target` öğesinin içinde yürütülen `Csc` görevi gösterir. Görev parametrelerine geçirilen öğeler ve özellikler bu örneğin kapsamı dışında bildirilmiştir. Çıkış parametresindeki `OutputAssembly` değeri `FinalAssemblyName` öğesinde depolanır ve çıkış parametresindeki `BuildSucceeded` değeri `BuildWorked` özelliğinde depolanır. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

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
