---
title: ParallelCustomBuild Görev | Microsoft Docs
description: CustomBuild MSBuild paralel örneklerini çalıştırmak için ParallelCustomBuild görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f4491d0a5e9c9d3a2554bd32211fd1fa8f7be2d2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628400"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild görevi

CustomBuild görevinin [paralel örneklerini çalıştırın.](../msbuild/custombuild-task.md)

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **ParallelCustomBuild görevinin parametreleri açık** almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**BreakOnFirstFailure**|İsteğe **bağlı bool** parametresi.|
|**MaxItemsInBatch**|İsteğe **bağlı int** parametresi.|
|**Maxprocesses**|İsteğe **bağlı int** parametresi.|
|**Kaynaklar**|Gerekli **ITaskItem[]** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)