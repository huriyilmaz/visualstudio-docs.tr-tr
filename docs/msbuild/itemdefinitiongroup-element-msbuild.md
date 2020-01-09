---
title: ItemDefinitionGroup öğesi (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5bfe09fec169495afa5b58a41f7c9f1b9bacfad
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573475"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup öğesi (MSBuild)
`ItemDefinitionGroup` öğesi, varsayılan olarak, projedeki tüm öğelere uygulanan meta veri değerleri olan öğe tanımları kümesini tanımlamanızı sağlar. ItemDefinitionGroup, [CreateItem görevi](../msbuild/createitem-task.md) ve [CreateProperty görevini](../msbuild/createproperty-task.md)kullanma ihtiyacını ortadan ortadan alır. Daha fazla bilgi için bkz. [öğe tanımları](../msbuild/item-definitions.md).

\<Proje > \<ItemDefinitionGroup >

## <a name="syntax"></a>Sözdizimi

```xml
<ItemDefinitionGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemDefinitionGroup>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Condition`|İsteğe bağlı öznitelik. Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğesi](../msbuild/item-element-msbuild.md)|Yapı işlemi için girişleri tanımlar. Bir `ItemDefinitionGroup`sıfır veya daha fazla `Item` öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyasının gerekli kök öğesi. |

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
