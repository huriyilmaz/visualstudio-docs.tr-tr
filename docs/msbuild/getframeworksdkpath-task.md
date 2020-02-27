---
title: GetFrameworkSdkPath görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d021bdb485846749ea2c7e9dfe483e09738fda46
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633999"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath görevi

Windows yazılım geliştirme seti (SDK) yolunu alır.
## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda `GetFrameworkSdkPath` görevinin parametreleri açıklanmaktadır.
Aşağıdaki tabloda `GetFrameworkSdkPath` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|İsteğe bağlı `String` salt okuma çıkış parametresi.<br /><br /> Varsa .NET SDK sürüm 2,0 'nin yolunu döndürür. Aksi takdirde `String.Empty`döndürür.|
|`FrameworkSdkVersion35Path`|İsteğe bağlı `String` salt okuma çıkış parametresi.<br /><br /> Varsa .NET SDK sürüm 3,5 'nin yolunu döndürür. Aksi takdirde `String.Empty`döndürür.|
|`FrameworkSdkVersion40Path`|İsteğe bağlı `String` salt okuma çıkış parametresi.<br /><br /> Varsa .NET SDK sürüm 4,0 'nin yolunu döndürür. Aksi takdirde `String.Empty`döndürür.|
|`Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Herhangi bir sürüm varsa, en son .NET SDK 'nın yolunu içerir. Aksi takdirde `String.Empty`döndürür.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `SdkPath` özelliğindeki Windows SDK yolunu depolamak için `GetFrameworkSdkPath` görevini kullanır.

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
