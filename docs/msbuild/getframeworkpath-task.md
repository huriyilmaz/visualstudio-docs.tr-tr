---
title: GetFrameworkPath Görev | Microsoft Docs
description: MSBuild derlemelerinin yolunu almak için GetFrameworkPath .NET Framework öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 80c4feb8c0b1ba92df467a634e748c177341bb8e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077367"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath görevi

Uygulama derlemelerinin yolunu .NET Framework.
Uygulama derlemelerinin yolunu .NET Framework.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda görevin parametreleri açık `GetFrameworkPath` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`FrameworkVersion11Path`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Varsa, çerçeve sürümü 1.1 derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|
|`FrameworkVersion20Path`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Varsa, çerçeve sürümü 2.0 derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|
|`FrameworkVersion30Path`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Varsa, çerçeve sürümü 3.0 derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|
|`FrameworkVersion35Path`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Varsa, çerçeve sürümü 3.5 derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|
|`FrameworkVersion40Path`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Varsa, çerçeve sürümü 4.0 derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|
|`Path`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Varsa, en son çerçeve derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|

## <a name="remarks"></a>Açıklamalar

Bu görev, .NET Framework sürümü yüklüyse, bu görev MSBuild için tasarlanmış olan sürümü döndürür.

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, `GetFrameworkPath` özelliğinin yolunu depolamak için .NET Framework `FrameworkPath` kullanır.

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
