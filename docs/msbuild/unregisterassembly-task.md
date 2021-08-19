---
title: UnregisterAssembly Görev | Microsoft Docs
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
ms.openlocfilehash: 79b9b607de3a8b4d8eafe46817612c62995d3a51
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142786"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly görevi

Belirtilen derlemeleri COM birlikte çalışma amaçlarıyla geri alma. [RegisterAssembly görevinin tersini gerçekleştirir.](../msbuild/registerassembly-task.md)

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `UnregisterAssembly` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Kaydı silinen derlemeleri belirtir.|
|`AssemblyListFile`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Görev ile görev arasındaki durum `RegisterAssembly` hakkında bilgi `UnregisterAssembly` içerir. Bu, görevin göreve kaydedileemeyen bir derlemenin kaydını silenleri denemesini `RegisterAssembly` önler.<br /><br /> Bu parametre belirtilirse ve `Assemblies` `TypeLibFiles` parametreleri yoksayılır.|
|`TypeLibFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Belirtilen tür kitaplığını belirtilen derlemeden kurtarıyor. **Not:**  Bu parametre yalnızca tür kitaplığı dosya adı derleme adı farklı ise gereklidir.|

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