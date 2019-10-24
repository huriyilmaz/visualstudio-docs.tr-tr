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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 678068d1b6acc055fa65e6d0305b07152ed28695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748106"
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
