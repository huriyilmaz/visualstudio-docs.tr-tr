---
title: MakeDir görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cc2e97a3024d768861a1967705137415a0d3aa2
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633544"
---
# <a name="makedir-task"></a>MakeDir görevi

Dizinler ve gerekirse herhangi bir üst dizin oluşturur.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda `MakeDir` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Directories`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Oluşturulacak Dizin kümesi.|
|`DirectoriesCreated`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Bu görev tarafından oluşturulan dizinler. Bazı dizinler oluşturulamayabilir, bu, `Directories` parametresine iletilen tüm öğeleri içermeyebilir.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `OutputDirectory` özelliği tarafından belirtilen dizini oluşturmak için `MakeDir` görevini kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
    </PropertyGroup>

    <Target Name="CreateDirectories">
        <MakeDir
            Directories="$(OutputDirectory)"/>
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
