---
title: UnregisterAssembly Task | Microsoft Docs
description: Com birlikte MSBuild için belirtilen derlemelerin kaydını silen UnregisterAssembly görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7111c6628193f1574597e20b00fef63746de3174e24cafa29f4f6cfb930c1cd5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369650"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly görevi

Com birlikte çalışma amacıyla belirtilen derlemeleri geri alma. [RegisterAssembly görevinin tersini gerçekleştirir.](../msbuild/registerassembly-task.md)

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `UnregisterAssembly` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Kaydı silinen derlemeleri belirtir.|
|`AssemblyListFile`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Görev ile görev arasındaki durum `RegisterAssembly` hakkında bilgi `UnregisterAssembly` içerir. Bu, görevin göreve kaydedileemeyen bir derlemenin kaydını silenleri denemesini `RegisterAssembly` önler.<br /><br /> Bu parametre belirtilirse ve `Assemblies` `TypeLibFiles` parametreleri yoksayılır.|
|`TypeLibFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Belirtilen tür kitaplığını belirtilen derlemeden geri alan. **Not:**  Bu parametre yalnızca tür kitaplığı dosya adı derleme adı farklı ise gereklidir.|

## <a name="remarks"></a>Açıklamalar

 Bu görevin başarılı olması için derlemenin mevcut olması gerekmez. Mevcut olmayan bir derlemenin kaydını silen bir görev bir uyarıyla başarılı olur. Bunun nedeni, bu görevin kayıt defterinden derleme kaydını kaldırmak olduğu için oluşur. Derleme yoksa kayıt defterinde değildir ve bu nedenle görev başarılı olur.

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> sınıfından <xref:System.MarshalByRefObject> devralınır. `MarshalByRefObject`sınıfı, sınıfıyla aynı işlevselliği sağlar, ancak kendi uygulama etki alanında <xref:Microsoft.Build.Utilities.Task> örnek olabilir.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, eğer varsa ve özellikleri tarafından `UnregisterAssembly` belirtilen yolda derlemenin kaydını `OutputPath` `FileName` silen görevi kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <OutputPath>\Output\</OutputPath>
        <FileName>MyFile.dll</FileName>
    </PropertyGroup>
    <Target Name="UnregisterAssemblies">
        <UnregisterAssembly
            Condition="Exists('$(OutputPath)$(FileName)')"
            Assemblies="$(OutputPath)$(FileName)" />
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [RegisterAssembly görevi](../msbuild/registerassembly-task.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)