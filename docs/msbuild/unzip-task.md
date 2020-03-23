---
title: Unzip Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: d331fda05e8655be0536a1e83d8309ae8c060b1f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631516"
---
# <a name="unzip-task"></a>Zip'i açma görevi

Bir *.zip* arşivini belirtilen konuma ait olarak unzips.

>[!NOTE]
>Görev `Unzip` yalnızca MSBuild 15.8 ve üzeri kullanılabilir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `Unzip` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFolder`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre<br /><br /> Dosyanın zip'ini açmak için hedef klasörü belirtir.|
|`OverwriteReadOnlyFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> Yalnızca `true`okunan dosyaların üzerine yazarsa. Varsayılan `false`değer.|
|`SkipUnchangedFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> Değiştirilirse, `true`gün dönümlerini atlar. Varsayılan `true`değer. `Unzip` görevi, dosyalar aynı boyuta ve aynı son değiştirme tarihine sahipse bu dosyaları değişmemiş kabul eder.|
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir veya daha fazla dosyanın zip'i açmayı belirtir. Birden çok dosya belirtirken, aynı klasöre sırayla fermuarsız.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir arşivin fermuarını alır ve salt okunur dosyaların üzerine yazar.

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
