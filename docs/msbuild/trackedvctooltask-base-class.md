---
title: TrackedVCToolTask sınıfı | Microsoft Docs
description: TrackedVCToolTask temel sınıfının ondan devraldığı görevlere eklediği parametreler hakkında bilgi edinin.
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
ms.openlocfilehash: 01b55e0ad88cb520078479217306bac948e6cd60
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047003"
---
# <a name="trackedvctooltask-base-class"></a>TrackedVCToolTask temel sınıfı

Çoğu görev, sonunda <xref:Microsoft.Build.Utilities.Task> sınıfından ve [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) sınıfından devralınır. Bu sınıf, [Vctooltask](../msbuild/vctooltask-base-class.md)'dan türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

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
