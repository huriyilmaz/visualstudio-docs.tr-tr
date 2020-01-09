---
title: RemoveDir Görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RemoveDir task [MSBuild]
- MSBuild, RemoveDir task
ms.assetid: 7ab214be-26b2-4bcd-9de8-c1b2091c0b74
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0827e05b2c295df2922c5f58d6a47d52e9a50e3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596001"
---
# <a name="removedir-task"></a>RemoveDir görevi
Belirtilen dizinleri ve tüm dosyalarını ve alt dizinlerini kaldırır.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `RemoveDir` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Directories`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Silinecek dizinleri belirtir.|
|`RemovedDirectories`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Başarıyla silinen dizinleri içerir.|

## <a name="remarks"></a>Açıklamalar
 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `OutputDirectory` ve `DebugDirectory` özellikleri tarafından belirtilen dizinleri kaldırır. Bu yollar proje dizinine göreli olarak değerlendirilir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2005">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
        <DebugDirectory>\Debug\</DebugDirectory>
    </PropertyGroup>

    <Target Name="RemoveDirectories">
        <RemoveDir
            Directories="$(OutputDirectory);$(DebugDirectory)" />
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
