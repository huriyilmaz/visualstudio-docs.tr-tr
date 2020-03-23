---
title: GetFrameworkSdkPath Görev | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633999"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath görevi

Windows Yazılım Geliştirme Kiti'ne (SDK) giden yolu alır.
## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda görevparametreleri `GetFrameworkSdkPath` açıklanmaktadır.
Aşağıdaki tabloda görevparametreleri `GetFrameworkSdkPath` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|İsteğe bağlı `String` salt okunur çıktı parametresi.<br /><br /> Varsa .NET SDK sürüm 2.0'a giden yolu döndürür. Aksi `String.Empty`takdirde döner.|
|`FrameworkSdkVersion35Path`|İsteğe bağlı `String` salt okunur çıktı parametresi.<br /><br /> Varsa .NET SDK sürüm 3.5'e giden yolu döndürür. Aksi `String.Empty`takdirde döner.|
|`FrameworkSdkVersion40Path`|İsteğe bağlı `String` salt okunur çıktı parametresi.<br /><br /> Varsa .NET SDK sürüm 4.0'a giden yolu döndürür. Aksi `String.Empty`takdirde döner.|
|`Path`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Herhangi bir sürüm varsa, en son .NET SDK'ya giden yolu içerir. Aksi `String.Empty`takdirde döner.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `GetFrameworkSdkPath` `SdkPath` windows SDK'ya giden yolu özellikte depolamak için görev kullanır.

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
