---
title: AtamaTargetPath Görevi | Microsoft Dokümanlar
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
ms.openlocfilehash: e2d825c0c08ffeba1449954ed310644dd4437840
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634545"
---
# <a name="assigntargetpath-task"></a>TargetPath görevini atayın

Bu görev dosyaların listesini kabul `<TargetPath>` eder ve zaten belirtilmemişse öznitelikler ekler.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda görevparametreleri `AssignTargetPath` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`RootFolder`|İsteğe bağlı `string` giriş parametresi.<br /><br /> Hedef bağlantıları içeren klasöre giden yolu içerir.|
|`Files`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` giriş parametresi.<br /><br /> Gelen dosya listesini içerir.|
|`AssignedFiles`|İsteğe bağlı<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Ortaya çıkan dosya listesini içerir.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir `AssignTargetPath` projeyi yapılandırma görevini yürütür.

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
