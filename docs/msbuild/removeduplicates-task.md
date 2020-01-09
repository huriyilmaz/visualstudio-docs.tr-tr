---
title: Removeyinelemeler görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 235f96b3d67b0ad2e3c3bd1c486c5c9f2eeb86c2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596014"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates görevi
Belirtilen öğe koleksiyonundan yinelenen öğeleri kaldırır.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `RemoveDuplicates` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Filtered`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Tüm yinelenen öğeleri kaldırılmış bir öğe koleksiyonu içerir. Giriş öğelerinin sırası, her yinelenen öğenin ilk örneğini koruyarak korunur.|
|`Inputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Yinelenen öğelerin kaldırılacağı öğe koleksiyonu.|

## <a name="remarks"></a>Açıklamalar
 Bu görev, büyük/küçük harfe duyarlıdır ve yinelenenleri belirlerken öğe meta verilerini karşılaştırmaz.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `MyItems` öğesi koleksiyonundan yinelenen öğeleri kaldırmak için `RemoveDuplicates` görevini kullanır. Görev tamamlandığında `FilteredItems` öğesi koleksiyonu bir öğe içerir.

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

 Aşağıdaki örnek, `RemoveDuplicates` görevinin giriş sırasını koruyan gösterir. Görev tamamlandığında `FilteredItems` öğesi koleksiyonu bu sırayla *MyFile2.cs*, *MyFile1.cs*ve *MyFile3.cs* öğelerini içerir.

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
