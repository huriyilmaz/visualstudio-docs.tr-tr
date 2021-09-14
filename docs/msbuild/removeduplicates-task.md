---
title: Removeyinelemeler görevi | Microsoft Docs
description: MSBuild, belirtilen öğe koleksiyonundan yinelenen öğeleri kaldırmak için removeyinelenenler görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/01/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 53abd38178770ddff46216dbba2cd1548e204fec
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625611"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates görevi

Belirtilen öğe koleksiyonundan yinelenen öğeleri kaldırır.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `RemoveDuplicates` .

|Parametre|Açıklama|
|---------------|-----------------|
|`Filtered`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Tüm yinelenen öğeleri kaldırılmış bir öğe koleksiyonu içerir. Giriş öğelerinin sırası, her yinelenen öğenin ilk örneğini koruyarak korunur.|
|`Inputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Yinelenen öğelerin kaldırılacağı öğe koleksiyonu.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, büyük/küçük harfe duyarlıdır ve yinelenenleri belirlerken öğe meta verilerini karşılaştırmaz.

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `RemoveDuplicates` öğe koleksiyonundan yinelenen öğeleri kaldırmak için görevini kullanır `MyItems` . Görev tamamlandığında, `FilteredItems` öğe koleksiyonu bir öğe içerir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile.cs"/>
        <MyItems Include="MyFile.cs">
            <Culture>fr</Culture>
        </MyItems>
        <MyItems Include="myfile.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

 Aşağıdaki örnekte, `RemoveDuplicates` görevin giriş sırası korunduğu gösterilmektedir. Görev tamamlandığında, `FilteredItems` öğe koleksiyonu bu sırayla *MyFile2. cs*, *MyFile1. cs* ve *MyFile3. cs* öğelerini içerir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile2.cs"/>
        <MyItems Include="MyFile1.cs" />
        <MyItems Include="MyFile3.cs" />
        <MyItems Include="myfile1.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Görevler](../msbuild/msbuild-tasks.md)
