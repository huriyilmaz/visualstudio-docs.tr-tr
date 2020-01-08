---
title: CombinePath görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a52e0d770a535b0fa7d29a379a7f6aba63e62d78
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593349"
---
# <a name="combinepath-task"></a>CombinePath görevi
Belirtilen yolları tek bir yol olarak birleştirir.

## <a name="task-parameters"></a>Görev parametreleri
 Aşağıdaki tabloda [CombinePath görevinin](../msbuild/combinepath-task.md)parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`BasePath`|Gerekli `String` parametresi.<br /><br /> Diğer yollarla birleştirilecek temel yol. Göreli yol, mutlak yol veya boş olabilir.|
|`Paths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Birleşik yolu oluşturmak için BasePath ile birleştirilecek bağımsız yolların listesi. Yollar göreli veya mutlak olabilir.|
|`CombinedPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Bu görev tarafından oluşturulan Birleşik yol.|

## <a name="remarks"></a>Açıklamalar
 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
