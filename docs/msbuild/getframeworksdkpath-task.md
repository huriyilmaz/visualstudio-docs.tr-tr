---
title: GetFrameworkSdkPath Görev | Microsoft Docs
description: MSBuild SDK'sı yolunu almak için GetFrameworkSdkPath görevinin nasıl Windows öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c785e7d7e12a77650f607fc58798f6b80b73f0f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093820"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath görevi

Windows Software Development Kit(SDK) yolunu alır.
## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda görevin parametreleri açık `GetFrameworkSdkPath` almaktadır.
Aşağıdaki tabloda görevin parametreleri açık `GetFrameworkSdkPath` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|İsteğe `String` bağlı salt okunur çıkış parametresi.<br /><br /> Varsa , .NET SDK sürüm 2.0'ın yolunu döndürür. Aksi takdirde `String.Empty` döndürür.|
|`FrameworkSdkVersion35Path`|İsteğe `String` bağlı salt okunur çıkış parametresi.<br /><br /> Varsa , .NET SDK sürüm 3.5'in yolunu döndürür. Aksi takdirde `String.Empty` döndürür.|
|`FrameworkSdkVersion40Path`|İsteğe `String` bağlı salt okunur çıkış parametresi.<br /><br /> Varsa , .NET SDK sürüm 4.0'ın yolunu döndürür. Aksi takdirde `String.Empty` döndürür.|
|`Path`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Herhangi bir sürüm varsa, en son .NET SDK'sı yolunu içerir. Aksi takdirde `String.Empty` döndürür.|

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, Windows `GetFrameworkSdkPath` SDK'sı yolunu özelliğinde depolamak için görevini `SdkPath` kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkSdkPath>
            <Output
                TaskParameter="Path"
                PropertyName="SdkPath" />
        </GetFrameworkSdkPath>
        <Message Text="$(SdkPath)"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
