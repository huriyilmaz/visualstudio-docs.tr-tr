---
title: Findinlist Görev | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 915265a775f572467ad1296499bdd3201adc1f8b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634155"
---
# <a name="findinlist-task"></a>FindInList görevi

Belirtilen bir listede, eşleşen madde spec olan bir öğe bulur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda [FindInList görevin](../msbuild/findinlist-task.md)parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`CaseSensitive`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`arama büyük/küçük harf duyarlıise; aksi takdirde, öyle değildir. Varsayılan değer. `true`|
|`FindLastMatch`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, son maç dönmek; aksi takdirde, ilk eşleşmeyi geri dönün. Varsayılan değer. `false`|
|`ItemFound`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıktı parametresi.<br /><br /> Listede bulunan ilk eşleşen öğe varsa.|
|`ItemSpecToFind`|Gerekli `String` parametre.<br /><br /> Aranacak öğe spec.|
|`List`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Öğe spec için arama yapmak için liste.|
|`MatchFileNameOnly`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`itemspec sadece dosya adı bölümü ne eşleşirse; aksi takdirde, tüm itemspec karşı maç. Varsayılan değer. `true`|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
