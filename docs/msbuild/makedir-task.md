---
title: MakeDir görevi | Microsoft Docs
description: MSBuild, dizin oluşturmak için makedir görevini ve gerekirse herhangi bir üst dizini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 60f50e6e6ce41c87bae812dcda47534426181eb9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625646"
---
# <a name="makedir-task"></a>MakeDir görevi

Dizinler ve gerekirse herhangi bir üst dizin oluşturur.

## <a name="parameters"></a>Parametreler

Aşağıdaki tablo, görevin parametrelerini açıklar `MakeDir` .

|Parametre|Açıklama|
|---------------|-----------------|
|`Directories`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Oluşturulacak Dizin kümesi.|
|`DirectoriesCreated`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Bu görev tarafından oluşturulan dizinler. Bazı dizinler oluşturulamayabilir, bu, parametreye iletilen tüm öğeleri içermeyebilir `Directories` .|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `MakeDir` özelliği tarafından belirtilen dizini oluşturmak için görevini kullanır `OutputDirectory` .

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
