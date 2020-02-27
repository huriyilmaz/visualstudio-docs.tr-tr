---
title: UpdateManifest görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25e410ba3122e0065f92186195ee5a82d6a55c2f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631348"
---
# <a name="updatemanifest-task"></a>UpdateManifest görevi

Bir bildirimde seçili özellikleri güncelleştirir ve yeniden imzalar.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `UpdateManifest` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`ApplicationManifest`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Uygulama bildirimini belirtir.|
|`ApplicationPath`|Gerekli `String` parametresi.<br /><br /> Uygulama bildiriminin yolunu belirtir.|
|`InputManifest`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Güncelleştirilecek bildirimi belirtir.|
|`OutputManifest`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Güncelleştirilmiş özellikleri içeren bildirimi belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere ek olarak, bu görev <xref:Microsoft.Build.Utilities.Task> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)