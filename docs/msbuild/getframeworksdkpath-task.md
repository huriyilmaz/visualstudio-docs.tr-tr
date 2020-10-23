---
title: GetFrameworkSdkPath görevi | Microsoft Docs
description: Windows SDK yolunu almak için MSBuild GetFrameworkSdkPath görevinin nasıl kullanılacağı hakkında bilgi edinin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4061dbe96c84648aacf136c0d59b92a2af037e2
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436807"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath görevi

Windows yazılım geliştirme seti (SDK) yolunu alır.
## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tablo, görevin parametrelerini açıklar `GetFrameworkSdkPath` .
Aşağıdaki tablo, görevin parametrelerini açıklar `GetFrameworkSdkPath` .

|Parametre|Açıklama|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|İsteğe bağlı `String` salt okunurdur çıkış parametresi.<br /><br /> Varsa .NET SDK sürüm 2,0 'nin yolunu döndürür. Aksi takdirde `String.Empty` döndürür.|
|`FrameworkSdkVersion35Path`|İsteğe bağlı `String` salt okunurdur çıkış parametresi.<br /><br /> Varsa .NET SDK sürüm 3,5 'nin yolunu döndürür. Aksi takdirde `String.Empty` döndürür.|
|`FrameworkSdkVersion40Path`|İsteğe bağlı `String` salt okunurdur çıkış parametresi.<br /><br /> Varsa .NET SDK sürüm 4,0 'nin yolunu döndürür. Aksi takdirde `String.Empty` döndürür.|
|`Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Herhangi bir sürüm varsa, en son .NET SDK 'nın yolunu içerir. Aksi takdirde `String.Empty` döndürür.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `GetFrameworkSdkPath` özelliğindeki Windows SDK yolu depolamak için görevini kullanır `SdkPath` .

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
