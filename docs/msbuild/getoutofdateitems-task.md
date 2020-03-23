---
title: GetOutOfDateItems Görev | Microsoft Dokümanlar
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272399"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems görevi

Eski tlogları okuyan, yeni tloglar yazan ve güncel olmayan öğeler kümesini döndüren yardımcı görev.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **GetOutOfDateItems** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**CheckForInterdependencies**|İsteğe bağlı **bool** parametresi.|
|**CommandMetadataName**|İsteğe bağlı **dize** parametresi.|
|**BağımlılıklarMetadataName**|İsteğe bağlı **dize** parametresi.|
|**HasInterdependencies**|İsteğe bağlı **bool** çıkış parametresi.|
|**OutofdateSources**|İsteğe bağlı **ITaskItem[]** çıktı parametresi.|
|**ÇıktılarMetadataName**|Gerekli **dize** parametresi.|
|**Kaynak**|İsteğe bağlı **ITaskItem[]** parametresi.|
|**TLogDirectory**|Gerekli **dize** parametresi.|
|**TLogNameÖnek**|Gerekli **dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)