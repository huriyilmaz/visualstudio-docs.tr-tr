---
title: PaletliVCToolTask Sınıf | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594935"
---
# <a name="trackedvctooltask-base-class"></a>Paletli VCToolTask taban sınıfı

Birçok görev sonuçta sınıf <xref:Microsoft.Build.Utilities.Task> ve [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) sınıfından devralınır. Bu sınıf [VCToolTask](../msbuild/vctooltask-base-class.md)türetilen görevlere çeşitli parametreler ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **TrackedVCToolTask** taban sınıfının parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**DeleteOutputOnExecute**|İsteğe bağlı **bool** parametresi.|
|**EnableExecuteTool**|İsteğe bağlı **bool** parametresi.|
|**DışlanmışInputPaths**|İsteğe bağlı **ITaskItem[]** parametresi.|
|**MinimalRebuildFromTracking**|İsteğe bağlı **bool** parametresi.|
|**PathOverride**|İsteğe bağlı **dize** parametresi.|
|**PostBuildTrackingTemizlik**|İsteğe bağlı **bool** parametresi.|
|**RootSource**|İsteğe bağlı **dize** parametresi.|
|**Atlanan Yürütme**|İsteğe bağlı **bool** çıkış parametresi.|
|**KaynaklarDerlenmiş**|İsteğe bağlı **ITaskItem[]** çıktı parametresi.|
|**TlogCommandFile**|İsteğe bağlı **ITaskItem** parametresi.|
|**TLogreadFiles**|İsteğe bağlı **ITaskItem[]** parametresi.|
|**TLogWriteFiles**|İsteğe bağlı **ITaskItem[]** parametresi.|
|**Araç Mimarisi**|İsteğe bağlı **dize** parametresi.|
|**TrackCommandLines**|İsteğe bağlı **bool** parametresi.|
|**TrackFileAccess**|İsteğe bağlı **bool** parametresi.|
|**TrackedInputFilesToIgnore**|İsteğe bağlı **ITaskItem[]** parametresi.|
|**İzlenenOutputFilesToIgnore**|İsteğe bağlı **ITaskItem[]** parametresi.|
|**İzleyiciÇerçeve Yolu**|İsteğe bağlı **dize** parametresi.|
|**TrackerSdkPath**|İsteğe bağlı **dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)<br/>
[Görevler](../msbuild/msbuild-tasks.md)
