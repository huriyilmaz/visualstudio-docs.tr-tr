---
title: ResolveNonMSBuildProjectOutput Görev | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 604ed91d32140c3b037e6ddef21e996f72ef8439
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632582"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput görevi

MSBuild olmayan proje başvuruları için çıktı dosyalarını belirler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `ResolveNonMSBuildProjectOutput` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|İsteğe bağlı `String` parametre.<br /><br /> Çözülmüş proje çıktılarını içeren bir XML dizesi belirtir.|
|`ProjectReferences`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Proje başvurularını belirtir.|
|`ResolvedOutputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Çözülmüş başvuru yollarının listesini içerir (ve özgün proje başvuru özniteliklerini korur).|
|`UnresolvedProjectReferences`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Önceden çözümlenmiş çıktılar listesini kullanarak çözülemeyen proje başvuru öğelerinin listesini içerir.<br /><br /> Visual Studio yalnızca MSBuild olmayan projeleri önceden çözdüğünden, bu listedeki proje başvurularının MSBuild biçiminde olduğu anlamına gelir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere sahip olmanın yanı sıra, bu görev <xref:Microsoft.Build.Tasks.TaskExtension> sınıftan devralınan parametreleri de devralır. <xref:Microsoft.Build.Utilities.Task> Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)