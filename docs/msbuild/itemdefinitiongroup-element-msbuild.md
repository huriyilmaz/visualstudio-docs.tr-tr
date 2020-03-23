---
title: ItemDefinitionGroup Öğesi (MSBuild) | Microsoft Dokümanlar
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
ms.openlocfilehash: 21e3b6554a9d6e0024cc21fd898962177acfffa7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633635"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup öğesi (MSBuild)

Öğe, `ItemDefinitionGroup` varsayılan olarak projedeki tüm öğelere uygulanan meta veri değerleri olan madde tanımları kümesini tanımlamanızı sağlar. ItemDefinitionGroup [CreateItem görev](../msbuild/createitem-task.md) ve [CreateProperty görev](../msbuild/createproperty-task.md)kullanma gereksinimi yerini alır. Daha fazla bilgi için [Madde tanımlarına](../msbuild/item-definitions.md)bakın.

\<Proje \<> ItemDefinitionGroup>

## <a name="syntax"></a>Sözdizimi

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
|`Condition`|İsteğe bağlı öznitelik. Değerlendirilecek durum. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğe](../msbuild/item-element-msbuild.md)|Yapı işleminin girdilerini tanımlar. Bir 'de sıfır `Item` veya `ItemDefinitionGroup`daha fazla öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Proje](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir ItemDefinitionGroup'ta m ve n olmak üzere iki meta veri öğesi tanımlar. Bu örnekte, "m" meta verileri Madde "i" olarak uygulanır, çünkü meta veri "m" Madde "i" tarafından açıkça tanımlanmamıştır. Ancak, varsayılan meta veri "n" Madde "i" uygulanmaz, çünkü meta veri "n" zaten Madde "i" tarafından tanımlanır.

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
