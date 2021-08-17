---
title: ItemGroup öğesi (MSBuild) | Microsoft Docs
description: kullanıcı tanımlı öğe öğeleri kümesi içeren MSBuild ıtemgroup öğesi hakkında bilgi edinin. Her öğe bir ItemGroup 'un alt öğesi olmalıdır.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 69fc6afd5a6dc7c5c9d51ae5c57afdbfd2c6847f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077263"
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup öğesi (MSBuild)

Kullanıcı tanımlı [öğe](../msbuild/item-element-msbuild.md) öğeleri kümesi içerir. bir MSBuild projesinde kullanılan her öğe, bir öğesinin alt öğesi olarak belirtilmelidir `ItemGroup` .

\<Project>
\<ItemGroup>

## <a name="syntax"></a>Syntax

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
|`Label`|İsteğe bağlı öznitelik. Öğesini tanımlar `ItemGroup` . |

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğe](../msbuild/item-element-msbuild.md)|Yapı işlemi için girişleri tanımlar. İçinde sıfır veya daha fazla `Item` öğe olabilir `ItemGroup` .|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |
| [Hedef](../msbuild/target-element-msbuild.md) | .NET Framework 3,5 ' den başlayarak, `ItemGroup` öğe bir öğe içinde görünebilir `Target` . Daha fazla bilgi için bkz. [hedefler](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, Kullanıcı tanımlı öğe koleksiyonlarını gösterir `Res` ve `CodeFiles` bir öğesi içinde bildirilmiştir `ItemGroup` . Öğe koleksiyonundaki öğelerin her biri `Res` Kullanıcı tanımlı bir alt [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) öğesi içerir.

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

Basit bir proje dosyasında, normalde tek bir `ItemGroup` öğesi kullanırsınız, ancak birden çok öğe de kullanabilirsiniz `ItemGroup` . Birden çok `ItemGroup` öğe kullanıldığında, öğeler tek bir halinde birleştirilir `ItemGroup` . Örneğin, bazı öğeler `ItemGroup` içeri aktarılan bir dosyada tanımlanan ayrı bir öğe tarafından bulunabilir.

ItemGroups özniteliği kullanılarak uygulanmış koşullara sahip olabilir `Condition` . Bu durumda, öğeler yalnızca koşul karşılandığında öğe listesine eklenir. [MSBuild koşullara](msbuild-conditions.md) bakın

`Label`Özniteliği, derleme davranışlarını denetlemek için bir yöntem olarak bazı yapı sistemlerinde kullanılır. bunu yalnızca bildirimlerinde, daha fazla anlaşılır MSBuild betikler oluşturmanın bir yolu olarak veya derleme eylemlerini etkilemek için bir denetim ayarı olarak kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Project dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Öğeler](../msbuild/msbuild-items.md)
- [Yaygın MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
