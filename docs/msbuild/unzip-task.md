---
title: Görev Sıkıştırması | Microsoft Docs
description: Bir dosya arşivini belirtilen bir konuma MSBuild sıkıştırmayı açmak için .zip ve kullanımı hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 30120b45a26fe46e80f6dca1eb6f68e1f4ce7e93
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142748"
---
# <a name="unzip-task"></a>Unzip görevi

Belirtilen konuma *.zip* arşivini açar.

>[!NOTE]
>Görev `Unzip` yalnızca 15.8 MSBuild ve üzerinde kullanılabilir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `Unzip` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFolder`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre<br /><br /> Dosyanın sıkıştırması açmak için hedef klasörü belirtir.|
|`OverwriteReadOnlyFiles`|İsteğe `Boolean` bağlı parametre.<br /><br /> , `true` salt okunur dosyaların üzerine yazıyorsa. Varsayılan olarak `false` kullanılır.|
|`SkipUnchangedFiles`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` değişmeyen dosyaları atlar. Varsayılan olarak `true` kullanılır. `Unzip` görevi, dosyalar aynı boyuta ve aynı son değiştirme tarihine sahipse bu dosyaları değişmemiş kabul eder.|
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Sıkıştırmayı açmak için bir veya daha fazla dosya belirtir. Birden çok dosya belirtirken, aynı klasöre doğru sıkıştırmaları çıkarılır.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki örnek bir arşivin sıkıştırmalarını açar ve tüm salt okunur dosyaların üzerine yazılır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
