---
title: CombinePath Görevi | Microsoft Dokümanlar
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
ms.openlocfilehash: 533f87eba9032efa7dc60ac682bbe400cb640727
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634441"
---
# <a name="combinepath-task"></a>CombinePath görevi

Belirtilen yolları tek bir yolda birleştirir.
## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki [tabloda CombinePath görevinin](../msbuild/combinepath-task.md)parametreleri açıklanmaktadır.


|Parametre|Açıklama|
|---------------|-----------------|
|`BasePath`|Gerekli `String` parametre.<br /><br /> Diğer yollar ile birleştirmek için temel yol. Göreceli bir yol, mutlak yol veya boş olabilir.|
|`Paths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Birleştirilmiş yolu oluşturmak için BasePath ile birleşimecek tek tek yolların listesi. Yollar göreceli veya mutlak olabilir.|
|`CombinedPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Bu görev tarafından oluşturulan birleşik yol.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
