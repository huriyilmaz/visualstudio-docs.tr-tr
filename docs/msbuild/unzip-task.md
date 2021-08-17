---
title: Sıkıştırılmış görev | Microsoft Docs
description: MSBuild Unzip görevinin, belirli bir konuma bir .zip arşivlemesini içeren parametreler ve kullanımları hakkında bilgi edinin.
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
ms.openlocfilehash: dc0fe999e6a86f405208c0da3b0b9008a3214db2afb70e5307375d998e7f6b3e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369559"
---
# <a name="unzip-task"></a>Unzip görevi

Belirtilen konuma bir *.zip* Arşivi kaldırır.

>[!NOTE]
>`Unzip`görev yalnızca MSBuild 15,8 ve üzeri sürümlerde kullanılabilir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `Unzip` .

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFolder`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre<br /><br /> Dosyanın sıkıştırmasını açmak için hedef klasörü belirtir.|
|`OverwriteReadOnlyFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , salt yazılır dosyaların üzerine yazar. Varsayılan olarak olur `false` .|
|`SkipUnchangedFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , değiştirilmemiş dosyaları yok etmek için atlar. Varsayılan olarak olur `true` . `Unzip` görevi, dosyalar aynı boyuta ve aynı son değiştirme tarihine sahipse bu dosyaları değişmemiş kabul eder.|
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Sıkıştırmayı açmak için bir veya daha fazla dosyayı belirtir. Birden çok dosya belirtirken aynı klasöre göre sıkıştırıldı.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir arşivi kaldırır ve salt okunurdur dosyanın üzerine yazar.

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
