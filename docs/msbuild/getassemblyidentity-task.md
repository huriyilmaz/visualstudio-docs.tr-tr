---
title: GetAssemblyIdentity Görev | Microsoft Docs
description: Belirtilen MSBuild derleme kimliklerini almak ve kimlik bilgilerini çıkarmak için GetAssemblyIdentity görevini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 28b26047a0893cc9e0ab783e83988b5c7ea1fb08
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143384"
---
# <a name="getassemblyidentity-task"></a>GetAssemblyIdentity görevi

Belirtilen dosyalardan derleme kimliklerini alın ve kimlik bilgilerini çıktı olarak alın.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda görevin parametreleri açık `GetAssemblyIdentity` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Alınan derleme kimliklerini içerir.|
|`AssemblyFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Kimlikleri almak için dosyaları belirtir.|

## <a name="remarks"></a>Açıklamalar

parametresinin çıktısı `Assemblies` , ve adlı öğe meta veri `Version` `PublicKeyToken` girdilerini `Culture` içerir.

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğede belirtilen dosyaların kimliğini `MyAssemblies` alın ve bunları öğeye çıkış olarak `MyAssemblyIdentities` görüntüler.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyAssemblies Include="File1.dll;File2.dll" />
    </ItemGroup>
    <Target Name="RetrieveIdentities">
        <GetAssemblyIdentity AssemblyFiles="@(MyAssemblies)">
            <Output TaskParameter="Assemblies" ItemName="MyAssemblyIdentities" />
        </GetAssemblyIdentity>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
