---
title: UnregisterAssembly görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22be291184ebf02ae0455f5b4656b1dec976dc89
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578292"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly görevi
Belirtilen derlemelerin COM birlikte çalışma amacıyla kaydını siler. [RegisterAssembly görevinin](../msbuild/registerassembly-task.md)ters işlemini gerçekleştirir.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `UnregisterAssembly` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Kaydı kaldırılacak derlemeleri belirtir.|
|`AssemblyListFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> `RegisterAssembly` görevi ve `UnregisterAssembly` görevi arasındaki durum hakkında bilgi içerir. Bu, görevin `RegisterAssembly` görevde kaydettirilemedi bir derlemenin kaydını silmeye çalışmasını önler.<br /><br /> Bu parametre belirtilmişse `Assemblies` ve `TypeLibFiles` parametreleri yoksayılır.|
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Belirtilen bütünleştirilmiş koddan belirtilen tür kitaplığının kaydını siler. **Note:**  Bu parametre yalnızca tür kitaplığı dosya adı derleme adından farklıysa gereklidir.|

## <a name="remarks"></a>Açıklamalar
 Bu görevin başarılı olabilmesi için derlemenin mevcut olması gerekmez. Mevcut olmayan bir derlemenin kaydını silmeye çalışırsanız, görev bir uyarıyla başarılı olur. Bu durum, kayıt defterinden derleme kaydını kaldırmak için bu görevin bir işi olduğu için oluşur. Derleme yoksa, kayıt defterinde değildir ve bu nedenle görev başarılı olur.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:System.MarshalByRefObject> sınıfından devralan <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> sınıfından parametreleri devralır. `MarshalByRefObject` sınıfı, <xref:Microsoft.Build.Utilities.Task> sınıfıyla aynı işlevselliği sağlar, ancak kendi uygulama etki alanında oluşturulabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, varsa, `OutputPath` ve `FileName` özellikleriyle belirtilen yoldaki derlemenin kaydını silmek için `UnregisterAssembly` görevini kullanır.

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