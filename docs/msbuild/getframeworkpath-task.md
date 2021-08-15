---
title: GetFrameworkPath Görevi | Microsoft Docs
description: .NET Framework derlemelerinin yolunu almak için MSBuild getframeworkpath görevinin nasıl kullanılacağını öğrenin.
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
ms.openlocfilehash: 30585cba87e24449ef3e95a43dd97b9bbe9dbceca397e2238ba45883b8a1f05d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397689"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath görevi

.NET Framework derlemelerinin yolunu alır.
.NET Framework derlemelerinin yolunu alır.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tablo, görevin parametrelerini açıklar `GetFrameworkPath` .

|Parametre|Açıklama|
|---------------|-----------------|
|`FrameworkVersion11Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 1,1 derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|
|`FrameworkVersion20Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 2,0 derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|
|`FrameworkVersion30Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 3,0 derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|
|`FrameworkVersion35Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 3,5 derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|
|`FrameworkVersion40Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 4,0 derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|
|`Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa, en son çerçeve derlemelerinin yolunu içerir. Aksi takdirde `null` döndürür.|

## <a name="remarks"></a>Açıklamalar

.NET Framework birden çok sürümü yüklüyse, bu görev MSBuild üzerinde çalışmak üzere tasarlanan sürümü döndürür.

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

aşağıdaki örnek, `GetFrameworkPath` özelliğindeki .NET Framework yolu depolamak için görevini kullanır `FrameworkPath` .

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
