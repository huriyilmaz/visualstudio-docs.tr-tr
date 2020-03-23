---
title: KaldırmaYinelenen Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: 90366bab14eefd1be4edac81d6b09b3f57aa3332
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632790"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates görevi

Yinelenen öğeleri belirtilen madde koleksiyonundan kaldırır.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `RemoveDuplicates` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Filtered`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Tüm yinelenen öğeleri kaldırılmış bir madde koleksiyonu içerir. Her yinelenen öğenin ilk örneği tutarak giriş maddelerinin sırası korunur.|
|`Inputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Yinelenen öğeleri kaldırmak için öğe koleksiyonu.|

## <a name="remarks"></a>Açıklamalar

 Bu görev büyük/küçük harf duyarsızdır ve yinelenenleri belirlerken madde meta verilerini karşılaştırmaz.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, `RemoveDuplicates` yinelenen öğeleri `MyItems` madde koleksiyonundan kaldırmak için görev kullanır. Görev tamamlandığında, `FilteredItems` madde koleksiyonu nda bir öğe yer alır.

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

 Aşağıdaki örnek, görevin giriş sırasını koruduğunu `RemoveDuplicates` gösterir. Görev `FilteredItems` tamamlandığında, madde koleksiyonu MyFile2.cs, *MyFile2.cs* *MyFile1.cs*ve bu sırada *MyFile3.cs* öğeleri içerir.

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
