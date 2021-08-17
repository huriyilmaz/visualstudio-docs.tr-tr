---
title: GenerateTrustInfo Görev | Microsoft Docs
description: Temel bildirimden MSBuild TargetZone ve ExcludedPermissions parametrelerinden uygulama güvenini oluşturmak için generateTrustInfo görevini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d2f31a8726f81ba98f32b6f98ca8bd76b3537cd0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077393"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo görevi

Uygulama güvenini temel bildirimden ve ve `TargetZone` parametrelerinden `ExcludedPermissions` üretir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `GenerateTrustInfo` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`ApplicationDependencies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bağımlı derlemeleri belirtir.|
|`BaseManifest`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Uygulama güveni oluşturmak için temel bildirimi belirtir.|
|`ExcludedPermissions`|İsteğe `String` bağlı parametre.<br /><br /> Bölge varsayılan izin kümesinden hariç tutulacak bir veya daha fazla noktalı virgülle ayrılmış izin kimliği değeri belirtir.|
|`TargetZone`|İsteğe `String` bağlı parametre.<br /><br /> Makine ilkesinden alınan bir bölge varsayılan izin kümesi belirtir.|
|`TrustInfoFile`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Uygulama güvenliği güven bilgilerini içeren dosyayı belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)