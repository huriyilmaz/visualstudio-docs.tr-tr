---
title: ResolveNonMSBuildProjectOutput görevi | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632582"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput görevi

MSBuild olmayan proje başvuruları için çıkış dosyalarını belirler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `ResolveNonMSBuildProjectOutput` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|İsteğe bağlı `String` parametresi.<br /><br /> Çözümlenen proje çıkışlarını içeren bir XML dizesi belirtir.|
|`ProjectReferences`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Proje başvurularını belirtir.|
|`ResolvedOutputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Çözümlenen başvuru yollarının listesini içerir (ve özgün proje başvuru özniteliklerini korur).|
|`UnresolvedProjectReferences`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Geri alınan çıkış listesi kullanılarak çözülemeyen proje başvuru öğelerinin listesini içerir.<br /><br /> Visual Studio yalnızca MSBuild olmayan projeler ön eki olduğundan, bu listedeki proje başvurularının MSBuild biçiminde olduğu anlamına gelir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)