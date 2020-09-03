---
title: GenerateTrustInfo görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84007c9a10618c6d757a36debe58c272302fa3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634038"
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