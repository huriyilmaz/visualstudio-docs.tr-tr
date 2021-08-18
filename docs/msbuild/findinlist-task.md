---
title: FindInList görevi | Microsoft Docs
description: belirtilen listede eşleşen itemspec içeren bir öğe bulmak için MSBuild findınlist görevini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f50c3a96b3d2b7ff4d18e28b74ace5f9cd31f522
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069323"
---
# <a name="findinlist-task"></a>FindInList görevi

Belirtilen listede, eşleşen itemspec 'e sahip bir öğe bulur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda, [Findinlist görevinin](../msbuild/findinlist-task.md)parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`CaseSensitive`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Arama büyük/küçük harfe duyarlıdır; Aksi takdirde, değildir. Varsayılan değer `true` olarak belirlenmiştir.|
|`FindLastMatch`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true` , son eşleşmeyi döndürür; Aksi takdirde, ilk eşleşmeyi döndürün. Varsayılan değer `false` olarak belirlenmiştir.|
|`ItemFound`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> Listede bulunan ilk eşleşen öğe (varsa).|
|`ItemSpecToFind`|Gerekli `String` parametre.<br /><br /> Arama yapılacak itemspec.|
|`List`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> İtemspec 'in aranacağı liste.|
|`MatchFileNameOnly`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true` , itemspec 'in yalnızca dosya adı bölümüyle eşleşir; Aksi takdirde, tüm itemspec ile eşleştirin. Varsayılan değer `true` olarak belirlenmiştir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
