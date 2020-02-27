---
title: FindAppConfigFile Görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c54f3c222588cd13711c832d12f7598f0cc5e223
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634181"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile görevi

Varsa, belirtilen listelerdeki *app. config* dosyasını bulur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `FindAppConfigFile` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AppConfigFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Varsa, listede bulunan ilk eşleşen öğeyi belirtir.|
|`PrimaryList`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Arama yapılacak birincil listeyi belirtir.|
|`SecondaryList`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Arama yapılacak ikincil listeyi belirtir.|
|`TargetPath`|Gerekli `String` parametresi.<br /><br /> Meta veri olarak eklenecek değeri belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
