---
title: RemoveDuplicates Task | Microsoft Docs
description: Belirtilen öğe MSBuild yinelenen öğeleri kaldırmak için RemoveDuplicates görevini nasıl kullandığını öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068754"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates görevi

Belirtilen öğe koleksiyonundan yinelenen öğeleri kaldırır.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `RemoveDuplicates` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Filtered`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Tüm yinelenen öğelerin kaldırıldığı bir öğe koleksiyonu içerir. Giriş öğelerinin sırası korunur ve her yinelenen öğenin ilk örneği korunur.|
|`Inputs`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Yinelenen öğeleri kaldıran öğe koleksiyonu.|

## <a name="remarks"></a>Açıklamalar

 Bu görev büyük/büyük/büyük harfe duyarlı değildir ve yinelenenleri belirlerken öğe meta verilerini karşılaştırmaz.

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğe `RemoveDuplicates` koleksiyonundan yinelenen öğeleri kaldırmak için `MyItems` görevini kullanır. Görev tamamlandığında, öğe koleksiyonu `FilteredItems` bir öğe içerir.

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

 Aşağıdaki örnek, görevin giriş `RemoveDuplicates` sıralamasını korumasını gösterir. Görev tamamlandığında, öğe koleksiyonu bu sırayla `FilteredItems` *MyFile2.cs*, *MyFile1.cs* ve *MyFile3.cs* öğelerini içerir.

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
