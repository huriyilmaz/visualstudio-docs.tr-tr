---
title: ItemDefinitionGroup öğesi (MSBuild) | Microsoft Docs
description: MSBuild 'in, projedeki tüm öğelere uygulanan bir dizi öğe tanımı, meta veri değeri tanımlamak için ItemDefinitionGroup öğesini nasıl kullandığını öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 466c753f986eeda233a7ff32bd51fa3e42b3f796
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913891"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup öğesi (MSBuild)

`ItemDefinitionGroup`Öğesi, varsayılan olarak, projedeki tüm öğelere uygulanan meta veri değerleri olan öğe tanımları kümesini tanımlamanızı sağlar. ItemDefinitionGroup, [CreateItem görevi](../msbuild/createitem-task.md) ve [CreateProperty görevini](../msbuild/createproperty-task.md)kullanma ihtiyacını ortadan ortadan alır. Daha fazla bilgi için bkz. [öğe tanımları](../msbuild/item-definitions.md).

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
|`Condition`|İsteğe bağlı öznitelik. Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğe](../msbuild/item-element-msbuild.md)|Yapı işlemi için girişleri tanımlar. İçinde sıfır veya daha fazla `Item` öğe olabilir `ItemDefinitionGroup` .|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir ItemDefinitionGroup içinde, k ve n olmak üzere iki meta veri öğesi tanımlar. Bu örnekte, "m" meta verileri "i" öğesi tarafından açıkça tanımlanmadığından "m" varsayılan meta verileri "i" öğesine uygulanır. Ancak, "n" meta verileri "i" öğesi tarafından zaten tanımlandığından "i" varsayılan meta verileri "i" öğesine uygulanmıyor.

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

- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Öğeler](../msbuild/msbuild-items.md)
