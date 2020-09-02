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
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77272399"
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
|**Kaynaklar**|İsteğe bağlı **ıtaskitem []** parametresi.|
|**TLogDirectory**|Gerekli **dize** parametresi.|
|**TLogNamePrefix**|Gerekli **dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)