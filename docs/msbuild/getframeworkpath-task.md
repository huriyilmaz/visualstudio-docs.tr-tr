---
title: GetFrameworkPath Görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b907194c4818ff6b867e9d15b795506ef3b77476
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634012"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath görevi

.NET Framework derlemelerinin yolunu alır.
.NET Framework derlemelerinin yolunu alır.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda `GetFrameworkPath` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`FrameworkVersion11Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 1,1 derlemelerinin yolunu içerir. Aksi takdirde `null`döndürür.|
|`FrameworkVersion20Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 2,0 derlemelerinin yolunu içerir. Aksi takdirde `null`döndürür.|
|`FrameworkVersion30Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 3,0 derlemelerinin yolunu içerir. Aksi takdirde `null`döndürür.|
|`FrameworkVersion35Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 3,5 derlemelerinin yolunu içerir. Aksi takdirde `null`döndürür.|
|`FrameworkVersion40Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 4,0 derlemelerinin yolunu içerir. Aksi takdirde `null`döndürür.|
|`Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa, en son çerçeve derlemelerinin yolunu içerir. Aksi takdirde `null`döndürür.|

## <a name="remarks"></a>Açıklamalar

.NET Framework birden çok sürümü yüklüyse, bu görev MSBuild 'in üzerinde çalışmak üzere tasarlandığı sürümü döndürür.

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `FrameworkPath` özelliğindeki .NET Framework yolunu depolamak için `GetFrameworkPath` görevini kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkPath>
            <Output
                TaskParameter="Path"
                PropertyName="FrameworkPath" />
        </GetFrameworkPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
