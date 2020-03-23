---
title: ParallelCustomBuild Görevi | Microsoft Dokümanlar
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279256"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild görevi

[CustomBuild görevinin](../msbuild/custombuild-task.md)paralel örneklerini çalıştırın.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **ParallelCustomBuild** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**BreakOnFirstFailure**|İsteğe bağlı **bool** parametresi.|
|**MaxItemsinBatch**|İsteğe bağlı **int** parametresi.|
|**Maxprocesses**|İsteğe bağlı **int** parametresi.|
|**Kaynak**|Gerekli **ITaskItem[]** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)