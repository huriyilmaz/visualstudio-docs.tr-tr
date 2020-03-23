---
title: OluşturmaTrustInfo Görev | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634038"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo görevi

Temel bildirimden ve `TargetZone` `ExcludedPermissions` parametrelerden uygulama güvenini oluşturur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `GenerateTrustInfo` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`ApplicationDependencies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bağımlı derlemeleri belirtir.|
|`BaseManifest`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Uygulama güvenini oluşturmak için temel bildirimi belirtir.|
|`ExcludedPermissions`|İsteğe bağlı `String` parametre.<br /><br /> Bölge varsayılan izin kümesinin dışında bırakılacak bir veya daha fazla yarı sütunayrılmış izin kimlik değerlerini belirtir.|
|`TargetZone`|İsteğe bağlı `String` parametre.<br /><br /> Makine ilkesinden elde edilen bir bölge varsayılan izin kümesini belirtir.|
|`TrustInfoFile`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Uygulama güvenlik güven bilgilerini içeren dosyayı belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere sahip olmanın yanı sıra, bu görev <xref:Microsoft.Build.Tasks.TaskExtension> sınıftan devralınan parametreleri de devralır. <xref:Microsoft.Build.Utilities.Task> Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)