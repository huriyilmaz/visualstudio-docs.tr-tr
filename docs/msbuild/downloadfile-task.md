---
title: DownloadFile Görev | Microsoft Docs
description: Http kullanarak belirtilen dosyaları indiren MSBuild downloadFile görevinin parametreleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 44f1f59b30cca2cd547766350285491c348d3513
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077627"
---
# <a name="downloadfile-task"></a>DownloadFile görevi

Hyper-Text Aktarım Protokolü'Hyper-Text belirtilen dosyaları indirir.

>[!NOTE]
>DownloadFile görevi yalnızca 15.8 MSBuild'da kullanılabilir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevin parametreleri açık `DownloadFile` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFileName`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre<br /><br /> İndirilen dosya için kullanmak üzere ad.  Varsayılan olarak, dosya adı veya uzak `SourceUrl` sunucusundan türetilen.|
|`DestinationFolder`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Dosyayı indirilecek hedef klasörü belirtir.  Klasör yoksa oluşturulursa.|
|`DownloadedFile`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı çıkış parametresi.<br /><br /> İndirilen dosyayı belirtir.|
|`Retries`|İsteğe `Int32` bağlı parametre.<br /><br /> Önceki tüm denemeler başarısız olursa, kaç kez indirme girişiminin başarısız olduğunu belirtir. Varsayılan olarak sıfırdır.|
|`RetryDelayMilliseconds`|İsteğe `Int32` bağlı parametre.<br /><br /> Gerekli yeniden denemeler arasındaki gecikmeyi milisaniye cinsinden belirtir. Varsayılan değer 5000'tir.|
|`SkipUnchangedFiles`|İsteğe `Boolean` bağlı parametre.<br /><br /> `true`ise, değişmeyen dosyaların indirilma adımlarını atlar. Varsayılan olarak `true` kullanılır. Görev, uzak sunucuya göre aynı boyuta ve aynı son değiştirme zamana sahipse `DownloadFile` dosyaların değişmediğini kabul ediyor. <br /><br />**Not:**  Tüm HTTP sunucuları dosyaların son değiştirme tarihini belirtenin dosyanın yeniden indirilse bile neden olacağını belirtmmektedir.|
|`SourceUrl`|Gerekli `String` parametre.<br /><br /> İndirilen URL'yi belirtir.|

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek bir dosyayı indirir ve projeyi inşa etmek `Content` için önce öğelere içerir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
