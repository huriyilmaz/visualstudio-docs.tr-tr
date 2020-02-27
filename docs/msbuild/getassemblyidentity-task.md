---
title: GetAssemblyIdentity görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a09bd4955cee6e50368f7155fb2e03c2c1758bf
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634025"
---
# <a name="getassemblyidentity-task"></a>GetAssemblyIdentity görevi

Belirtilen dosyalardaki derleme kimliklerini alır ve kimlik bilgilerini çıkarır.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda `GetAssemblyIdentity` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Alınan derleme kimliklerini içerir.|
|`AssemblyFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Kimlikleri alınacak dosyaları belirtir.|

## <a name="remarks"></a>Açıklamalar

`Assemblies` parametresine göre çıkış öğeleri `Version`, `PublicKeyToken`ve `Culture`adlı öğe meta veri girdilerini içerir.

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `MyAssemblies` öğesinde belirtilen dosyaların kimliğini alır ve bunları `MyAssemblyIdentities` öğesine verir.

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
