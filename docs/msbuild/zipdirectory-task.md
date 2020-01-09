---
title: ZipDirectory görevi | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd4bf72509610e9d397e4b208294112fcc0975b4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588336"
---
# <a name="zipdirectory-task"></a>ZipDirectory görevi
Bir dizinin içeriğinden bir *. zip* arşivi oluşturur.

>[!NOTE]
>`ZipDirectory` görevi yalnızca MSBuild 15,8 ve üzeri sürümlerde kullanılabilir.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `ZipDirectory` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFile`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi<br /><br /> Oluşturulacak *. zip* dosyasının tam yolu.|
|`Overwrite`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, varsa, hedef dosyanın atlandığını atlar. `false` değerini varsayılan olarak alır.|
|`SourceDirectory`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> İçinden bir *. zip* Arşivi oluşturulacak dizini belirtir.|

## <a name="remarks"></a>Açıklamalar
 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir proje derlemeden sonra çıkış dizininden bir *. zip* arşivi oluşturur.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
