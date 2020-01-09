---
title: Sıkıştırılmış görev | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3b02108e2ee47a31ced196643bf917b3b63c1c6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594909"
---
# <a name="unzip-task"></a>Sıkıştırılmış görev
Belirtilen konuma bir *. zip* arşivi olarak UnZIP.

>[!NOTE]
>`Unzip` görevi yalnızca MSBuild 15,8 ve üzeri sürümlerde kullanılabilir.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `Unzip` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFolder`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi<br /><br /> Dosyanın sıkıştırmasını açmak için hedef klasörü belirtir.|
|`OverwriteReadOnlyFiles`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, salt yazılır dosyaların üzerine yazar. `false` değerini varsayılan olarak alır.|
|`SkipUnchangedFiles`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, değiştirilmemiş dosyaları yok edin. `true` değerini varsayılan olarak alır. `Unzip` görevi, dosyalar aynı boyuta ve aynı son değiştirme tarihine sahipse bu dosyaları değişmemiş kabul eder.|
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Sıkıştırmayı açmak için bir veya daha fazla dosyayı belirtir. Birden çok dosya belirtirken aynı klasöre göre sıkıştırıldı.|

## <a name="remarks"></a>Açıklamalar
 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

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
