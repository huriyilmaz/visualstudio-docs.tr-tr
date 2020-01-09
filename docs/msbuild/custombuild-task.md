---
title: CustomBuild görevi | Microsoft Docs
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
ms.openlocfilehash: d95b6e7d4197487adc13050572ac31310701c759
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595351"
---
# <a name="custombuild-task"></a>CustomBuild görevi

, Cmd. C++ exe Microsoft derleyici aracını sarmalanmış. Bu sınıf, [Trackedvctooltask](../msbuild/trackedvctooltask-base-class.md)'dan türetilir, ancak dosya bağımlılıklarını saptamak için dosya izlemeyi kullanmaz. Artımlı derleme düzgün şekilde çalışması için tüm bağımlılıklar doğrudan bir AdditionalDependencies olarak belirtilmelidir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda, **CustomBuild** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**BuildSuffix**|İsteğe bağlı **dize** parametresi.|
|**Ğına**|Gerekli **ıtaskitem []** parametresi.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
