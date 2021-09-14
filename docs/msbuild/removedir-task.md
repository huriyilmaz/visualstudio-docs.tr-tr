---
title: RemoveDir Görev | Microsoft Docs
description: Belirtilen MSBuild tüm dosyalarını ve alt dizinlerini kaldırmak için RemoveDir görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 342f1da7d476f95397d474d8edf972f36f49b5c2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625616"
---
# <a name="removedir-task"></a>RemoveDir görevi

Belirtilen dizinleri ve tüm dosyalarını ve alt dizinlerini kaldırır.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `RemoveDir` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Directories`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Silinecek dizinleri belirtir.|
|`RemovedDirectories`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Başarıyla silinen dizinleri içerir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki örnek, ve özellikleri tarafından belirtilen `OutputDirectory` dizinleri `DebugDirectory` kaldırır. Bu yollar proje dizinine göre olarak kabul edilir.

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
