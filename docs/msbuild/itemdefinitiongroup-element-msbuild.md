---
title: ItemDefinitionGroup Öğesi (MSBuild) | Microsoft Docs
description: Bir MSBuild tanımları, projedeki tüm öğelere uygulanan meta veri değerleri tanımlamak için ItemDefinitionGroup öğesini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 3eeea6faf2456dadb1083658d8403a7d2501aa0e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093768"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup öğesi (MSBuild)

öğesi, varsayılan olarak projedeki tüm öğelere uygulanan meta veri değerleri olan `ItemDefinitionGroup` bir Öğe Tanımları kümesi tanımlamanıza olanak sağlar. ItemDefinitionGroup, [CreateItem](../msbuild/createitem-task.md) görevinin ve [CreateProperty](../msbuild/createproperty-task.md)görevinin yerine kullanılır. Daha fazla bilgi için [bkz. Öğe tanımları.](../msbuild/item-definitions.md)

\<Project>
\<ItemDefinitionGroup>

## <a name="syntax"></a>Syntax

```xml
<ItemDefinitionGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemDefinitionGroup>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Condition`|İsteğe bağlı öznitelik. Değerlendirilecek koşul. Daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğe](../msbuild/item-element-msbuild.md)|Derleme işleminin girişlerini tanımlar. içinde sıfır veya daha `Item` fazla öğe `ItemDefinitionGroup` olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Bir proje dosyasının gerekli MSBuild öğesi. |

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir ItemDefinitionGroup içinde m ve n olmak için iki meta veri öğesini tanımlar. "m" meta verileri "i" Öğesi tarafından açıkça tanımlanmamış olduğundan, bu örnekte varsayılan "m" meta verileri Item "i" değerine uygulanır. Ancak"n" meta verileri "i" Öğesi tarafından zaten tanımlandığı için varsayılan "n" meta verileri "i" öğesine uygulanmaz.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemDefinitionGroup>
        <i>
            <m>m1</m>
            <n>n1</n>
        </i>
    </ItemDefinitionGroup>
    <ItemGroup>
        <i Include="a">
            <o>o1</o>
            <n>n2</n>
        </i>
    </ItemGroup>
    ...
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Öğeler](../msbuild/msbuild-items.md)
