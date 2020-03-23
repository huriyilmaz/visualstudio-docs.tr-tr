---
title: CustomBuild Görev | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595351"
---
# <a name="custombuild-task"></a>CustomBuild görevi

Microsoft C++ derleyici aracıcmd.exe'yi sarar. Bu sınıf [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)türetilmiştir, ancak dosya bağımlılıklarını keşfetmek için dosya izleme kullanmaz. Tüm bağımlılıklar, artımlı yapının düzgün çalışması için Ek Bağımlılıklar olarak açıkça belirtilmelidir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **CustomBuild** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**BuildSuffix**|İsteğe bağlı **dize** parametresi.|
|**Kaynak**|Gerekli **ITaskItem[]** parametresi.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
