---
title: ZipDirectory Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: 5ceb23d34fab92fe0056f9bd82b9d9c63967dc4c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094568"
---
# <a name="zipdirectory-task"></a>ZipDirectory görev

Bir dizinin içeriğinden *bir .zip* arşivi oluşturur.

>[!NOTE]
>Görev `ZipDirectory` yalnızca MSBuild 15.8 ve üzeri kullanılabilir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `ZipDirectory` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFile`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre<br /><br /> Oluşturmak için *.zip* dosyasına tam yol.|
|`Overwrite`|İsteğe bağlı `Boolean` parametre.<br /><br /> Atlarsa, `true`hedef dosya varsa üzerine yazılır. Varsayılan `false`değer.|
|`SourceDirectory`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Bir *.zip* arşivi oluşturmak için dizin belirtir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnek (içe *aktarılırsa .hedef dosyası* olarak kullanılırsa), proje oluşturduktan sonra çıktı dizininden *bir .zip* arşivi oluşturur. Özellik `$(OutputPath)` normalde bir MSBuild proje dosyasında tanımlanır, bu nedenle aşağıdaki dosyayı içeri `output.zip`aktaran bir proje dosyası zip arşivi oluşturur:

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
