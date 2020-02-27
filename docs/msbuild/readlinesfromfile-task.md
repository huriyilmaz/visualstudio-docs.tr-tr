---
title: ReadLinesFromFile Görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ReadLinesFromFile task
- ReadLinesFromFile task [MSBuild]
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c926c131fab101563841bea3362e88e27674226
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632907"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile görevi

Bir metin dosyasından öğelerin listesini okur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `ReadLinesFromFile` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`File`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Okunacak dosyayı belirtir. Dosya her satırda bir öğe içermelidir.|
|`Lines`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Dosyadan okunan satırları içerir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir metin dosyasındaki listeden öğe oluşturmak için `ReadLinesFromFile` görevini kullanır. Dosyadan okunan öğeler `ItemsFromFile` öğesi koleksiyonunda depolanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
    </ItemGroup>

    <Target Name="ReadFromFile">
        <ReadLinesFromFile
            File="@(MyTextFile)" >
            <Output
                TaskParameter="Lines"
                ItemName="ItemsFromFile"/>
        </ReadLinesFromFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Görevler](../msbuild/msbuild-tasks.md)
