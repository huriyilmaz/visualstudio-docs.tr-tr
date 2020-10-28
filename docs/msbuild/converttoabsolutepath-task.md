---
title: ConvertToAbsolutePath görevi | Microsoft Docs
description: Göreli bir yolu veya başvuruyu mutlak bir yola dönüştürmek için MSBuild ConvertToAbsolutePath görevini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ConvertToAbsolutePath task [MSBuild]
- MSBuild, ConvertToAbsolutePath task
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ecf9695b36f341fa350abf53062e70095c03c374
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796166"
---
# <a name="converttoabsolutepath-task"></a>ConvertToAbsolutePath görevi

Göreli yolu veya başvuruyu mutlak bir yola dönüştürür.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tablo, görevin parametrelerini açıklar `ConvertToAbsolutePath` .

|Parametre|Açıklama|
|---------------|-----------------|
|`Paths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Mutlak yollara dönüştürülecek göreli yolların listesi.|
|`AbsolutePaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Geçirilen öğeler için mutlak yolların listesi.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
