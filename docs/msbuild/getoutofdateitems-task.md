---
title: GetOutOfDateItems görevi | Microsoft Docs
description: İşlem günlüklerini (TLOGs) okumak ve yazmak için MSBuild GetOutOfDateItems yardımcı görevini kullanın ve güncel olmayan öğe kümelerini geri döndürün.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6cc80d4e1aa3580e0185460d19f78e9737b73220
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436829"
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