---
title: ItemGroup öğesi (MSBuild) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8064ce4c13419238ca5877893a731d2ac53afb25
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633648"
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup öğesi (MSBuild)

Kullanıcı tanımlı [öğe](../msbuild/item-element-msbuild.md) öğeleri kümesi içerir. Bir MSBuild projesinde kullanılan her öğe, bir `ItemGroup` öğesinin alt öğesi olarak belirtilmelidir.

\<Proje > \<ItemGroup >

## <a name="syntax"></a>Sözdizimi

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Condition`|İsteğe bağlı öznitelik. Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|
|`Label`|İsteğe bağlı öznitelik. `ItemGroup`tanımlar.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğe](../msbuild/item-element-msbuild.md)|Yapı işlemi için girişleri tanımlar. Bir `ItemGroup`sıfır veya daha fazla `Item` öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Proje](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |
| [Hedef](../msbuild/target-element-msbuild.md) | .NET Framework 3,5 ' den başlayarak, `ItemGroup` öğesi bir `Target` öğesi içinde bulunabilir. Daha fazla bilgi için bkz. [hedefler](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, Kullanıcı tanımlı öğe koleksiyonlarını `Res` ve bir `ItemGroup` öğesinin içinde bildirildiği `CodeFiles` gösterir. `Res` öğesi koleksiyonundaki öğelerin her biri Kullanıcı tanımlı bir alt [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) öğesi içerir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Öğeler](../msbuild/msbuild-items.md)
- [Ortak MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
