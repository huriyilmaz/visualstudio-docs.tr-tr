---
title: Atamatargetpath görevi | Microsoft Docs
description: Bir dosya listesini kabul etmek ve henüz belirtilmemişse, TargetPath özniteliklerini eklemek için MSBuild Atamayolu görevini kullanın.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e56bb8817551e24d1b5aceef2f571e35f1db43e
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353336"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath görevi

Bu görev, bir dosya listesi kabul eder ve `<TargetPath>` henüz belirtilmemişse öznitelikleri ekler.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tablo, görevin parametrelerini açıklar `AssignTargetPath` .

|Parametre|Açıklama|
|---------------|-----------------|
|`RootFolder`|İsteğe bağlı `string` giriş parametresi.<br /><br /> Hedef bağlantıları içeren klasörün yolunu içerir.|
|`Files`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` giriş parametresi.<br /><br /> Gelen dosya listesini içerir.|
|`AssignedFiles`|İsteğe Bağlı<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]`çıkış parametresi.<br /><br /> Dosyaların elde edilen listesini içerir.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `AssignTargetPath` bir projeyi yapılandırmak için görevini yürütür.

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
