---
title: Kayıt DışıMontaj Görevi | Microsoft Dokümanlar
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
ms.openlocfilehash: 2f8cddcf9bf0632914d1a6de1cc904dbf0f173e6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631503"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly görevi

Com interop amaçları için belirtilen derlemeleri kayıt dışı kalır. [RegisterAssembly görevinin](../msbuild/registerassembly-task.md)tersini gerçekleştirir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `UnregisterAssembly` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Derlemelerin kayıtsız olacağını belirtir.|
|`AssemblyListFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> `RegisterAssembly` Görev ve `UnregisterAssembly` görev arasındaki durum hakkında bilgi içerir. Bu, görevin göreve kaydolmayan bir derlemeyi silmeye `RegisterAssembly` çalışmasından engeller.<br /><br /> Bu parametre `Assemblies` belirtilirse, `TypeLibFiles` parametreler ve parametreler yoksayılır.|
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Belirtilen tür kitaplığını belirtilen derlemeden kaydeder. **Not:**  Bu parametre yalnızca tür kitaplığı dosya adı derleme adından farklıysa gereklidir.|

## <a name="remarks"></a>Açıklamalar

 Bu görevin başarılı olaması için derlemenin bulunması gerekmez. Var olmayan bir derlemenin kaydını kaldırmaya çalışırsanız, görev bir uyarıyla başarılı olur. Bu, derleme kaydını kayıt defterinden kaldırmak için bu görevin işi olduğundan oluşur. Derleme yoksa, kayıt defterinde değildir ve bu nedenle, görev başarılı oldu.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> <xref:System.MarshalByRefObject> devralınan sınıftan parametreleri devralır. <xref:Microsoft.Build.Utilities.Task> Sınıf, `MarshalByRefObject` sınıfla aynı işlevselliği sağlar, ancak kendi uygulama etki alanında anında kullanılabilir.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `UnregisterAssembly` varsa, ve `OutputPath` `FileName` özellikleri tarafından belirtilen yolda derleme yi boşaltmak için görevi kullanır.

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