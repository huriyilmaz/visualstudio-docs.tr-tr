---
title: ZipDirectory görevi | Microsoft Docs
description: MSBuild 'in bir dizin içeriğinden bir. zip arşivi oluşturmak için ZipDirectory görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6b897a33dacdbd52beaabdd9289a010df92a85c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847888"
---
# <a name="zipdirectory-task"></a>ZipDirectory görevi

Bir dizinin içeriğinden bir *. zip* arşivi oluşturur.

>[!NOTE]
>`ZipDirectory`Görev yalnızca MSBuild 15,8 ve üzeri sürümlerde kullanılabilir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `ZipDirectory` .

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFile`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre<br /><br /> Oluşturulacak *. zip* dosyasının tam yolu.|
|`Overwrite`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , varsa hedef dosyanın üzerine yazılır. Varsayılan olarak olur `false` .|
|`SourceDirectory`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> İçinden bir *. zip* Arşivi oluşturulacak dizini belirtir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek (içeri aktarılmış bir *. targets* dosyası olarak kullanılırsa), bir proje oluşturulduktan sonra çıkış dizininden bir *. zip* arşivi oluşturur. `$(OutputPath)`Özelliği normalde bir MSBuild proje dosyasında tanımlanır, bu nedenle aşağıdaki dosyayı içeri aktaran bir proje dosyası bir ZIP arşivi üretir `output.zip` :

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
