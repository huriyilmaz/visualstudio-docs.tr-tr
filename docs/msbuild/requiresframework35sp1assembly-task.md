---
title: RequiresFramework35SP1Assembly Görev | Microsoft Docs
description: Uygulamanın MSBuild 3.5 SP1'e gerekip gerek olmadığını belirlemek için RequiresFramework35SP1Assembly görevini nasıl .NET Framework öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 77f57eb4b36fb4bf12088dd46dc457127b576098
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625605"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly görevi

Uygulamanın 3.5 SP1 .NET Framework gerekip gerek olmadığını belirler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `RequiresFramework35SP1Assembly` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Uygulamada başvurulan derlemeleri belirtir.|
|`CreateDesktopShortcut`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` yükleme sırasında masaüstünde bir kısayol simgesi oluşturur.|
|`DeploymentManifestEntryPoint`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Uygulamanın bildirim dosyası adını belirtir.|
|`EntryPoint`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Uygulama çalıştırıldıkları zaman yürütülecek derlemeyi belirtir.|
|`ErrorReportUrl`|İsteğe `String` bağlı parametre.<br /><br /> Yükleme sırasında karşılaşılan iletişim kutularında görüntülenen Web sitesini ClickOnce belirtir.|
|`Files`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Uygulama yayımıldığında dağıtılacak dosyaların listesini belirtir.|
|`ReferencedAssemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Projede başvurulan derlemeleri belirtir.|
|`RequiresMinimumFramework35SP1`|İsteğe `Boolean` bağlı çıkış parametresi.<br /><br /> ise, `true` uygulama 3.5 SP1 .NET Framework gerektirir.|
|`SigningManifests`|İsteğe `Boolean` bağlı çıkış parametresi.<br /><br /> ise, `true` ClickOnce bildirimleri imzalanmıştır.|
|`SuiteName`|İsteğe `String` bağlı parametre.<br /><br /> Uygulamanın yük kurulacak **Başlat** menüsündeki klasörün adını belirtir.|
|`TargetFrameworkVersion`|İsteğe `String` bağlı parametre.<br /><br /> Bu uygulamanın hedefle .NET Framework sürümünü belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra, sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)