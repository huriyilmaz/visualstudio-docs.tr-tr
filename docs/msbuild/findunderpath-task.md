---
title: FindUnderPath Görev | Microsoft Docs
description: Belirtilen MSBuild veya altındaki yollarla belirtilen öğe koleksiyonunda öğeleri bulmak için FindUnderPath görevini kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: dda0aafa554220d5b506479dac843e2b538ace1fb6fb3ae912430ff49339e2d5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427931"
---
# <a name="findunderpath-task"></a>FindUnderPath görevi

Belirtilen öğe koleksiyonunda hangi öğelerin belirtilen klasörde veya altında yollar olduğunu belirler.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevin parametreleri açık `FindUnderPath` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Files`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Yolları parametresi tarafından belirtilen yol ile karşılaştıran dosyaları `Path` belirtir.|
|`InPath`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Belirtilen yolun altında bulunan öğeleri içerir.|
|`OutOfPath`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Belirtilen yol altında bulunamadı öğeleri içerir.|
|`Path`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Başvuru olarak kullanmak üzere klasör yolunu belirtir.|
|`UpdateToAbsolutePaths`|İsteğe `Boolean` bağlı parametre.<br /><br /> True ise, çıkış öğelerinin yolları mutlak yollar olacak şekilde güncelleştirilir.|

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğede yer alan dosyaların özelliği tarafından belirtilen yolun altında var olan yollara sahip olup `FindUnderPath` olmadığını belirlemek için görevini `MyFiles` `SearchPath` kullanır. Görev tamamlandıktan sonra, `FilesNotFoundInPath` öğe File1.txtdosyasını, öğe iseFile2.txt`FilesFoundInPath` içerir. 

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
