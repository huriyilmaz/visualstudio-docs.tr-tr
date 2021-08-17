---
title: TrackedVCToolTask Sınıfı | Microsoft Docs
description: TrackedVCToolTask temel sınıfının bu sınıftan devralınan görevlere ekleyen parametreleri öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6cd173bf92fbb5efea20efee3e4a0dc35501d16bf14f17fc4980142148984b0a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443143"
---
# <a name="trackedvctooltask-base-class"></a>TrackedVCToolTask temel sınıfı

Çoğu görev sonuçta sınıfından ve <xref:Microsoft.Build.Utilities.Task> [ToolTask sınıfından](/dotnet/api/microsoft.build.utilities.tooltask) devralınır. Bu sınıf, [VCToolTask'tan](../msbuild/vctooltask-base-class.md)türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **TrackedVCToolTask** temel sınıfının parametreleri açıklandı.

|Parametre|Açıklama|
|---------------|-----------------|
|**DeleteOutputOnExecute**|İsteğe **bağlı bool** parametresi.|
|**EnableExecuteTool**|İsteğe **bağlı bool** parametresi.|
|**ExcludedInputPaths**|İsteğe **bağlı ITaskItem[]** parametresi.|
|**MinimalRebuildFromTracking**|İsteğe **bağlı bool** parametresi.|
|**PathOverride**|İsteğe **bağlı dize** parametresi.|
|**PostBuildTrackingCleanup**|İsteğe **bağlı bool** parametresi.|
|**RootSource**|İsteğe **bağlı dize** parametresi.|
|**SkippedExecution**|İsteğe **bağlı bool** çıkış parametresi.|
|**KaynaklarCompiled**|İsteğe **bağlı ITaskItem[]** çıkış parametresi.|
|**TLogCommandFile**|İsteğe **bağlı ITaskItem** parametresi.|
|**TLogReadFiles**|İsteğe **bağlı ITaskItem[]** parametresi.|
|**TLogWriteFiles**|İsteğe **bağlı ITaskItem[]** parametresi.|
|**ToolArchitecture**|İsteğe **bağlı dize** parametresi.|
|**TrackCommandLines**|İsteğe **bağlı bool** parametresi.|
|**TrackFileAccess**|İsteğe **bağlı bool** parametresi.|
|**TrackedInputFilesToIgnore**|İsteğe **bağlı ITaskItem[]** parametresi.|
|**TrackedOutputFilesToIgnore**|İsteğe **bağlı ITaskItem[]** parametresi.|
|**TrackerFrameworkPath**|İsteğe **bağlı dize** parametresi.|
|**TrackerSdkPath**|İsteğe **bağlı dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)<br/>
[Görevler](../msbuild/msbuild-tasks.md)
