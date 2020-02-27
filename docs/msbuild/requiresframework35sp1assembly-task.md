---
title: RequiresFramework35SP1Assembly görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: caefe0887ca23cd4cee60c3a4ba2a6133e9893df
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632777"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly görevi

Uygulamanın .NET Framework 3,5 SP1 gerektirip gerektirmediğini belirler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `RequiresFramework35SP1Assembly` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Uygulamada başvurulan derlemeleri belirtir.|
|`CreateDesktopShortcut`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, yükleme sırasında masaüstünde bir kısayol simgesi oluşturur.|
|`DeploymentManifestEntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Uygulamanın bildirim dosyası adını belirtir.|
|`EntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Uygulama çalıştırıldığında yürütülmesi gereken derlemeyi belirtir.|
|`ErrorReportUrl`|İsteğe bağlı `String` parametresi.<br /><br /> ClickOnce yüklemeleri sırasında karşılaşılan iletişim kutularında görüntülenen Web sitesini belirtir.|
|`Files`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Uygulama yayımlandığında dağıtılacak dosyaların listesini belirtir.|
|`ReferencedAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Projede başvurulan derlemeleri belirtir.|
|`RequiresMinimumFramework35SP1`|İsteğe bağlı `Boolean` çıkış parametresi.<br /><br /> `true`, uygulama .NET Framework 3,5 SP1 gerektirir.|
|`SigningManifests`|İsteğe bağlı `Boolean` çıkış parametresi.<br /><br /> `true`, ClickOnce bildirimleri imzalanır.|
|`SuiteName`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın yükleneceği **Başlangıç** menüsünde klasörün adını belirtir.|
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametresi.<br /><br /> Bu uygulamanın hedeflediği .NET Framework sürümünü belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)