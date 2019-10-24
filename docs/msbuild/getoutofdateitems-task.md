---
title: GetOutOfDateItems görevi | Microsoft Docs
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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: d3dc343c595606faf5bd31d7f087f7ba8d95f69e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747315"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems görevi

Eski tgünlükleri okuyan yardımcı görev, yeni tlogs yazma ve güncel olmayan öğe kümesi döndürür.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **GetOutOfDateItems** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Denetim bağımlılıkları**|İsteğe bağlı **bool** parametresi.|
|**CommandMetadataName**|İsteğe bağlı **dize** parametresi.|
|**Bağımlılıkları Cıesmetadataname**|İsteğe bağlı **dize** parametresi.|
|**Hasınterdependencies**|İsteğe bağlı **bool** çıkış parametresi.|
|**OutOfDateSources**|İsteğe bağlı **ıtaskitem []** çıkış parametresi.|
|**OutputsMetadataName**|Gerekli **dize** parametresi.|
|**Ğına**|İsteğe bağlı **ıtaskitem []** parametresi.|
|**TLogDirectory**|Gerekli **dize** parametresi.|
|**TLogNamePrefix**|Gerekli **dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)