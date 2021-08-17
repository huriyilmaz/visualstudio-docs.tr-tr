---
title: ParallelCustomBuild görevi | Microsoft Docs
description: MSBuild, custombuild görevinin paralel örneklerini çalıştırmak için parallelcustombuild görevini nasıl kullandığını öğrenin.
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
ms.openlocfilehash: 921a79c78dbec3df58a78d7dd41011a60d825fd1961ee7a3233e28c5bafec122
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443172"
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
|**Kaynaklar**|Gerekli **ıtaskitem []** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)