---
title: TrackedVCToolTask sınıfı | Microsoft Docs
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
ms.openlocfilehash: 8a4272f7800e0532c0674fe7117e839cb16557d5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594935"
---
# <a name="trackedvctooltask-base-class"></a>TrackedVCToolTask temel sınıfı

Çoğu görev <xref:Microsoft.Build.Utilities.Task> sınıfından ve [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) sınıfından devralınır. Bu sınıf, [Vctooltask](../msbuild/vctooltask-base-class.md)'dan türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda, **Trackedvctooltask** temel sınıfının parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Deleteoutputonexyürütüldüğünde**|İsteğe bağlı **bool** parametresi.|
|**EnableExecuteTool**|İsteğe bağlı **bool** parametresi.|
|**Excludeınputpaths**|İsteğe bağlı **ıtaskitem []** parametresi.|
|**MinimalRebuildFromTracking**|İsteğe bağlı **bool** parametresi.|
|**PathOverride**|İsteğe bağlı **dize** parametresi.|
|**PostBuildTrackingCleanup**|İsteğe bağlı **bool** parametresi.|
|**RootSource**|İsteğe bağlı **dize** parametresi.|
|**SkippedExecution**|İsteğe bağlı **bool** çıkış parametresi.|
|**Sourcesderlenen**|İsteğe bağlı **ıtaskitem []** çıkış parametresi.|
|**TLogCommandFile**|İsteğe bağlı **ıtaskitem** parametresi.|
|**TLogReadFiles**|İsteğe bağlı **ıtaskitem []** parametresi.|
|**TLogWriteFiles**|İsteğe bağlı **ıtaskitem []** parametresi.|
|**ToolArchitecture**|İsteğe bağlı **dize** parametresi.|
|**TrackCommandLines**|İsteğe bağlı **bool** parametresi.|
|**TrackFileAccess**|İsteğe bağlı **bool** parametresi.|
|**Trackedınputfilestoıgnore**|İsteğe bağlı **ıtaskitem []** parametresi.|
|**TrackedOutputFilesToIgnore**|İsteğe bağlı **ıtaskitem []** parametresi.|
|**Trackerframeworkyolu**|İsteğe bağlı **dize** parametresi.|
|**TrackerSdkPath**|İsteğe bağlı **dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)<br/>
[Görevler](../msbuild/msbuild-tasks.md)
