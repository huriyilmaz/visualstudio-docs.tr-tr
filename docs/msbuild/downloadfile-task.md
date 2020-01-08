---
title: DownloadFile görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06171f3a1543f6fa827c1b6fd477b992d099fff6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590481"
---
# <a name="downloadfile-task"></a>DownloadFile görevi
, Hyper-metin Aktarım Protokolü 'Nü (HTTP) kullanarak belirtilen dosyaları indirir.

>[!NOTE]
>DownloadFile görevi yalnızca MSBuild 15,8 ve üzeri sürümlerde kullanılabilir.

## <a name="parameters"></a>Parametreler
Aşağıdaki tabloda `DownloadFile` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFileName`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi<br /><br /> İndirilen dosya için kullanılacak ad.  Varsayılan olarak, dosya adı `SourceUrl` veya uzak sunucudan türetilir.|
|`DestinationFolder`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Dosyanın indirileceği hedef klasörü belirtir.  Yoksa, klasör oluşturulmadıysa.|
|`DownloadedFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> İndirilen dosyayı belirtir.|
|`Retries`|İsteğe bağlı `Int32` parametresi.<br /><br /> Önceki tüm denemeler başarısız olursa kaç kez indirilmek gerektiğini belirtir. Varsayılan olarak sıfırdır.|
|`RetryDelayMilliseconds`|İsteğe bağlı `Int32` parametresi.<br /><br /> Gerekli yeniden denemeler arasındaki gecikme süresi (milisaniye olarak) belirtir. Varsayılan olarak 5000 ' dir.|
|`SkipUnchangedFiles`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, değiştirilmemiş dosyaların indirilmesini atlar. `true` değerini varsayılan olarak alır. `DownloadFile` görevi, uzak sunucuya göre aynı boyutta ve en son değiştirme zamanına sahip olmaları durumunda dosyaları değişmeden kabul eder. <br /><br />**Note:**  Tüm HTTP sunucularının dosyaların son değiştirilme tarihini belirtmesi, dosyanın yeniden indirilmesine neden olur.|
|`SourceUrl`|Gerekli `String` parametresi.<br /><br /> İndirilecek URL 'YI belirtir.|

## <a name="remarks"></a>Açıklamalar
Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek
Aşağıdaki örnek bir dosyayı indirir ve projeyi oluşturmadan önce `Content` öğelerine ekler.

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
