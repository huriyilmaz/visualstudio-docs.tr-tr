---
title: CustomBuild Görev | Microsoft Docs
description: Bu makalede, MSBuild C++ derleme işlemini özelleştirmeyi desteklemek için MSBuild custombuild görevi açıklanmıştır.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 03c8c41aa50651354a490f31f4bfe71e2dae7cdef4d066fd8d45edb8e742e757
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397949"
---
# <a name="custombuild-task"></a>CustomBuild görevi

Microsoft C++ derleyici aracını sarmalar ve cmd.exe. Bu sınıf [TrackedVCToolTask'tan](../msbuild/trackedvctooltask-base-class.md)türetilen, ancak dosya bağımlılıklarını bulmak için dosya izleme kullanmaz. Artımlı derlemenin düzgün çalışması için tüm bağımlılıklar açıkça AdditionalDependencies olarak belirtilmelidir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda CustomBuild görevinin **parametreleri açık** almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**BuildSuffix**|İsteğe **bağlı dize** parametresi.|
|**Kaynaklar**|Gerekli **ITaskItem[]** parametresi.|
|**TrackerLogDirectory**|İsteğe **bağlı dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
