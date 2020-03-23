---
title: DownloadFile Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: 81a9c3b1c22277261276ced1940f1f2e83d11882
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634259"
---
# <a name="downloadfile-task"></a>DownloadFile görevi

Hyper-Text Transfer Protocol (HTTP) kullanarak belirtilen dosyaları karşıdan yükler.

>[!NOTE]
>DownloadFile görevi yalnızca MSBuild 15.8 ve üzeri olarak kullanılabilir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevparametreleri `DownloadFile` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFileName`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre<br /><br /> İndirilen dosya için kullanılacak ad.  Varsayılan olarak, dosya adı veya `SourceUrl` uzak sunucudan türetilmiştir.|
|`DestinationFolder`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Dosyayı karşıdan yüklemek için hedef klasörü belirtir.  Klasör yoksa oluşturulursa.|
|`DownloadedFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıktı parametresi.<br /><br /> İndirilen dosyayı belirtir.|
|`Retries`|İsteğe bağlı `Int32` parametre.<br /><br /> Önceki tüm denemeler başarısız olduysa, kaç kez karşıdan yükleme girişiminde bulununcaya çalışılır. Varsayılan olarak sıfırdır.|
|`RetryDelayMilliseconds`|İsteğe bağlı `Int32` parametre.<br /><br /> Gerekli yeniden denemeler arasındaki gecikmeyi milisaniye cinsinden belirtir. Varsayılan olarak 5000'e kadar.|
|`SkipUnchangedFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`değişmeden dosyaların karşıdan yüklenir. Varsayılan `true`değer. Görev, `DownloadFile` dosyaların uzak sunucuya göre aynı boyuta ve aynı son değiştirilen süreye sahipse değişmediğini düşünür. <br /><br />**Not:**  Tüm HTTP sunucuları dosyaların son değiştirilmiş tarihini gösterir dosyanın yeniden indirilmesine neden olur.|
|`SourceUrl`|Gerekli `String` parametre.<br /><br /> İndirmek için URL'yi belirtir.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek bir dosyaindirir ve projeyi oluşturmadan önce `Content` öğelere içerir.

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
