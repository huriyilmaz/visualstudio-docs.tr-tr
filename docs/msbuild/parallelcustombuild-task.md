---
title: ParallelCustomBuild görevi | Microsoft Docs
description: MSBuild 'in, CustomBuild görevinin paralel örneklerini çalıştırmak için ParallelCustomBuild görevini nasıl kullandığını öğrenin.
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
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048901"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild görevi

[CustomBuild görevinin](../msbuild/custombuild-task.md)paralel örneklerini çalıştırın.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **Parallelcustombuild** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Breakkonfirstfailure**|İsteğe bağlı **bool** parametresi.|
|**Maxıtemınbatch**|İsteğe bağlı **int** parametresi.|
|**MaxProcesses**|İsteğe bağlı **int** parametresi.|
|**Ğına**|Gerekli **ıtaskitem []** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)