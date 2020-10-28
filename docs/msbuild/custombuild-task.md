---
title: CustomBuild görevi | Microsoft Docs
description: Bu makalede, C++ derleme işlemini özelleştirmeyi desteklemek için MSBuild tarafından kullanılan MSBuild CustomBuild görevi açıklanır.
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
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796556"
---
# <a name="custombuild-task"></a>CustomBuild görevi

Microsoft C++ derleyici aracı 'nı sarmalayan cmd.exe. Bu sınıf, [Trackedvctooltask](../msbuild/trackedvctooltask-base-class.md)'dan türetilir, ancak dosya bağımlılıklarını saptamak için dosya izlemeyi kullanmaz. Artımlı derleme düzgün şekilde çalışması için tüm bağımlılıklar doğrudan bir AdditionalDependencies olarak belirtilmelidir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda, **CustomBuild** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**BuildSuffix**|İsteğe bağlı **dize** parametresi.|
|**Ğına**|Gerekli **ıtaskitem []** parametresi.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
