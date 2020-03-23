---
title: GetFrameworkPath Görevi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634012"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath görevi

.NET Framework derlemelerine giden yolu alır.
.NET Framework derlemelerine giden yolu alır.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda görevparametreleri `GetFrameworkPath` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`FrameworkVersion11Path`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Varsa, çerçeve sürümü 1.1 derlemelerine giden yolu içerir. Aksi `null`takdirde döner.|
|`FrameworkVersion20Path`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Varsa, çerçeve sürümü 2.0 derlemelerine giden yolu içerir. Aksi `null`takdirde döner.|
|`FrameworkVersion30Path`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Varsa, çerçeve sürümü 3.0 derlemelerine giden yolu içerir. Aksi `null`takdirde döner.|
|`FrameworkVersion35Path`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Varsa, çerçeve sürümü 3.5 derlemelerine giden yolu içerir. Aksi `null`takdirde döner.|
|`FrameworkVersion40Path`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Varsa, çerçeve sürümü 4.0 derlemelerine giden yolu içerir. Aksi `null`takdirde döner.|
|`Path`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Varsa, en son çerçeve derlemelerine giden yolu içerir. Aksi `null`takdirde döner.|

## <a name="remarks"></a>Açıklamalar

.NET Framework'ün birkaç sürümü yüklenirse, bu görev MSBuild'in çalıştırmak üzere tasarladığı sürümü döndürür.

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki `GetFrameworkPath` örnekte, `FrameworkPath` .NET Framework'e giden yolu özellikte depolamak için görev kullanılmıştır.

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
