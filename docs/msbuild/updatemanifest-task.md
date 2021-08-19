---
title: UpdateManifest Görev | Microsoft Docs
description: Bir bildirimde MSBuild ve yeniden imzayı güncelleştirmek için UpdateManifest görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 8cde4f2fcc9b226aeda9066da083a1a37979dfe9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142604"
---
# <a name="updatemanifest-task"></a>UpdateManifest görevi

Bir bildirimde seçili özellikleri güncelleştirme ve yeniden atama.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `UpdateManifest` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`ApplicationManifest`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Uygulama bildirimini belirtir.|
|`ApplicationPath`|Gerekli `String` parametre.<br /><br /> Uygulama bildiriminin yolunu belirtir.|
|`InputManifest`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Güncelleştirilen bildirimi belirtir.|
|`OutputManifest`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı çıkış parametresi.<br /><br /> Güncelleştirilmiş özellikleri içeren bildirimi belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından parametreleri <xref:Microsoft.Build.Utilities.Task> devralıyor. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [Görev temel sınıfı.](../msbuild/task-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)