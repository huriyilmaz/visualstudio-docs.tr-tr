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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634038"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo görevi

Temel bildirimden ve `TargetZone` ve `ExcludedPermissions` parametrelerinden uygulama güvenini oluşturur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `GenerateTrustInfo` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`ApplicationDependencies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bağımlı derlemeleri belirtir.|
|`BaseManifest`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Uygulama güvenini oluşturmak için temel bildirimi belirtir.|
|`ExcludedPermissions`|İsteğe bağlı `String` parametresi.<br /><br /> Bölge varsayılan izin kümesinden dışlanacak bir veya daha fazla noktalı virgülle ayrılmış izin kimliği değeri belirtir.|
|`TargetZone`|İsteğe bağlı `String` parametresi.<br /><br /> Makine ilkesinden alınan bölge varsayılan izin kümesini belirtir.|
|`TrustInfoFile`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> çıktı parametresi.<br /><br /> Uygulama güvenlik güveni bilgilerini içeren dosyayı belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)