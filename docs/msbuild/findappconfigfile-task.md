---
title: FindAppConfigFile Task | Microsoft Docs
description: Sağlanan listelerde MSBuild dosyanın (varsa) bulun app.config FindAppConfigFile görevini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5f078b3110fa7888c59f6a5aaf374f5a714db9dc70341a3bb2550e64cabcd29b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428061"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile görevi

Sağlanan *app.config* varsa, bir dosya bulur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `FindAppConfigFile` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AppConfigFile`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Varsa, listede bulunan ilk eşleşen öğeyi belirtir.|
|`PrimaryList`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Aranan birincil listeyi belirtir.|
|`SecondaryList`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Aranan ikincil listeyi belirtir.|
|`TargetPath`|Gerekli `String` parametre.<br /><br /> Meta veri olarak eklenecek değeri belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
