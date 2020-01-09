---
title: FindUnderPath görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33912df490b148c91c2a0d152f979bd6149d8ae3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566078"
---
# <a name="findunderpath-task"></a>FindUnderPath görevi
Belirtilen öğe koleksiyonundaki hangi öğelerin belirtilen klasörün içinde veya altında olan yollara sahip olduğunu belirler.

## <a name="parameters"></a>Parametreler
Aşağıdaki tabloda `FindUnderPath` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Files`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Yolları `Path` parametresi tarafından belirtilen yol ile karşılaştırılacak olan dosyaları belirtir.|
|`InPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Belirtilen yolun altında bulunan öğeleri içerir.|
|`OutOfPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Belirtilen yolda bulunmayan öğeleri içerir.|
|`Path`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Başvuru olarak kullanılacak klasör yolunu belirtir.|
|`UpdateToAbsolutePaths`|İsteğe bağlı `Boolean` parametresi.<br /><br /> True ise, çıkış öğelerinin yolları mutlak yollar olacak şekilde güncelleştirilir.|

## <a name="remarks"></a>Açıklamalar
Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek
Aşağıdaki örnek, `MyFiles` öğesinde yer alan dosyaların `SearchPath` özelliği tarafından belirtilen yolun altında bulunan yollara sahip olup olmadığını anlamak için `FindUnderPath` görevini kullanır. Görev tamamlandıktan sonra, `FilesNotFoundInPath` öğesi *FILE1. txt* dosyasını içerir ve `FilesFoundInPath` öğesi *dosya2. txt* dosyasını içerir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyFiles Include="C:\File1.txt" />
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />
    </ItemGroup>

    <PropertyGroup>
        <SearchPath>C:\Projects\MyProject</SearchPath>
    </PropertyGroup>

    <Target Name="FindFiles">
        <FindUnderPath
            Files="@(MyFiles)"
            Path="$(SearchPath)">
            <Output
                TaskParameter="InPath"
                ItemName="FilesFoundInPath" />
            <Output
                TaskParameter="OutOfPath"
                ItemName="FilesNotFoundInPath" />
        </FindUnderPath>
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
