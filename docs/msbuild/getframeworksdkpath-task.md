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
ms.openlocfilehash: 8fbe0dbda58a0c57cacd64c40b66cc640b779bca
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593323"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath görevi
[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]yolunu alır.

## <a name="task-parameters"></a>Görev parametreleri
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
Aşağıdaki örnek, `SdkPath` özelliğindeki [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] yolunu depolamak için `GetFrameworkSdkPath` görevini kullanır.

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
