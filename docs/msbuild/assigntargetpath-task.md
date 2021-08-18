---
title: AssignTargetPath Görev | Microsoft Docs
description: Bir dosya MSBuild kabul etmek ve önceden belirtilmemişse TargetPath özniteliklerini eklemek için AssignTargetPath görevini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: a28e6dd3c49796967944a8a9fee0b53b96f5035d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085292"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath görevi

Bu görev dosya listesini kabul eder ve `<TargetPath>` önceden belirtilmemişse öznitelikler ekler.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda görevin parametreleri açık `AssignTargetPath` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`RootFolder`|İsteğe `string` bağlı giriş parametresi.<br /><br /> Hedef bağlantıları içeren klasörün yolunu içerir.|
|`Files`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı giriş parametresi.<br /><br /> Gelen dosya listesini içerir.|
|`AssignedFiles`|İsteğe Bağlı<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]`output parametresi.<br /><br /> Sonuçta elde edilen dosya listesini içerir.|

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir projeyi `AssignTargetPath` yapılandırmak için görevi yürütür.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyProject">
        <AssignTargetPath
RootFolder="Resources"
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
        </AssignTargetPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
