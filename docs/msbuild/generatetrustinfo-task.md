---
title: GenerateTrustInfo görevi | Microsoft Docs
description: Temel bildirim ve TargetZone ve ExcludedPermissions parametrelerinden uygulama güvenini oluşturmak için MSBuild GenerateTrustInfo görevini kullanın.
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
ms.workload:
- multiple
ms.openlocfilehash: 831f6fa76ba3d6cfdebbb6b850862155ad280641
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914723"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo görevi

Temel bildirimden ve ve parametrelerinden uygulama güvenini oluşturur `TargetZone` `ExcludedPermissions` .

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `GenerateTrustInfo` .

|Parametre|Açıklama|
|---------------|-----------------|
|`ApplicationDependencies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bağımlı derlemeleri belirtir.|
|`BaseManifest`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Uygulama güvenini oluşturmak için temel bildirimi belirtir.|
|`ExcludedPermissions`|İsteğe bağlı `String` parametre.<br /><br /> Bölge varsayılan izin kümesinden dışlanacak bir veya daha fazla noktalı virgülle ayrılmış izin kimliği değeri belirtir.|
|`TargetZone`|İsteğe bağlı `String` parametre.<br /><br /> Makine ilkesinden alınan bölge varsayılan izin kümesini belirtir.|
|`TrustInfoFile`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Uygulama güvenlik güveni bilgilerini içeren dosyayı belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)