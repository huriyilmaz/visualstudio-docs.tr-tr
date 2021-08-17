---
title: FindInList Görev | Microsoft Docs
description: Belirli bir listede MSBuild itemspec içeren bir öğeyi bulmak için FindInList görevini kullanmayı öğrenin.
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
ms.openlocfilehash: f7682929efd7be1d3ee99e71fa0ace598aa8ee00d7007a391bdf0cb541f3465f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428048"
---
# <a name="findinlist-task"></a>FindInList görevi

Belirtilen bir listede, eşleşen itemspec'e sahip bir öğe bulur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda [FindInList](../msbuild/findinlist-task.md)görevinin parametreleri açık almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`CaseSensitive`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` arama büyük/büyük/büyük harfe duyarlıdır; aksi takdirde değildir. Varsayılan değer `true` olarak belirlenmiştir.|
|`FindLastMatch`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` son eşleşmeyi, aksi takdirde ilk eşleşmeyi geri döner. Varsayılan değer `false` olarak belirlenmiştir.|
|`ItemFound`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Varsa, listede bulunan ilk eşleşen öğe.|
|`ItemSpecToFind`|Gerekli `String` parametre.<br /><br /> Aranan itemspec.|
|`List`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Itemspec'in aranma listesi.|
|`MatchFileNameOnly`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` itemspec'in yalnızca dosya adı bölümüyle eşle; aksi takdirde, tüm itemspec ile eşle. Varsayılan değer `true` olarak belirlenmiştir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
