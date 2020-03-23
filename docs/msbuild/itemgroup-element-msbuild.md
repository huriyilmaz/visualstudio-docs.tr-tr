---
title: ItemGroup Öğesi (MSBuild) | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633648"
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup öğesi (MSBuild)

Kullanıcı tanımlı [Öğe](../msbuild/item-element-msbuild.md) öğeleri kümesi içerir. MSBuild projesinde kullanılan her öğe, bir `ItemGroup` öğenin alt öğesi olarak belirtilmelidir.

\<Proje \<> ItemGroup>

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
|`Condition`|İsteğe bağlı öznitelik. Değerlendirilecek durum. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|
|`Label`|İsteğe bağlı öznitelik. `ItemGroup`Tanımlar.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğe](../msbuild/item-element-msbuild.md)|Yapı işleminin girdilerini tanımlar. Bir 'de sıfır `Item` veya `ItemGroup`daha fazla öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Proje](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |
| [Hedef](../msbuild/target-element-msbuild.md) | .NET Framework 3.5 ile `ItemGroup` başlayarak, `Target` öğe bir öğenin içinde görünebilir. Daha fazla bilgi için [Bkz. Hedefler.](../msbuild/msbuild-targets.md) |

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, kullanıcı tanımlı `Res` madde `CodeFiles` koleksiyonlarını `ItemGroup` gösterir ve bir öğenin içinde bildirilir. Madde koleksiyonundaki `Res` öğelerin her biri kullanıcı tanımlı alt [ÖğeMetadata](../msbuild/itemmetadata-element-msbuild.md) öğesi içerir.

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
