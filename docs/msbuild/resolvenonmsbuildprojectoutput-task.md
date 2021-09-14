---
title: ResolveNonMSBuildProjectOutput Görev | Microsoft Docs
description: Bu MSBuild olmayan proje başvurularını belirlemek için ResolveNonMSBuildProjectOutput görevini nasıl MSBuild öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: de57cbcd1b1ad59f3edfce47f09bf88a8e9ea94e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625562"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput görevi

Proje başvurularına uygun olmayan MSBuild belirler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `ResolveNonMSBuildProjectOutput` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|İsteğe `String` bağlı parametre.<br /><br /> Çözümlenmiş proje çıkışlarını içeren bir XML dizesi belirtir.|
|`ProjectReferences`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Proje başvurularını belirtir.|
|`ResolvedOutputPaths`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Çözümlenen başvuru yollarının listesini içerir (ve özgün proje başvuru özniteliklerini korur).|
|`UnresolvedProjectReferences`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Önceden çözümlenen çıkış listesi kullanılarak çözümlenemedi proje başvuru öğelerinin listesini içerir.<br /><br /> Yalnızca Visual Studio olmayan MSBuild için bu listede yer alan proje başvuruları, MSBuild biçimindedir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra, sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)