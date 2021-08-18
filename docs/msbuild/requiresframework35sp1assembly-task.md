---
title: RequiresFramework35SP1Assembly görevi | Microsoft Docs
description: MSBuild, uygulamanın .NET Framework 3,5 SP1 gerektirip gerektirmediğini öğrenmek için RequiresFramework35SP1Assembly görevini nasıl kullandığını öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093677"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly görevi

uygulamanın .NET Framework 3,5 SP1 gerektirip gerektirmediğini belirler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `RequiresFramework35SP1Assembly` .

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Uygulamada başvurulan derlemeleri belirtir.|
|`CreateDesktopShortcut`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , yükleme sırasında masaüstünde bir kısayol simgesi oluşturur.|
|`DeploymentManifestEntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Uygulamanın bildirim dosyası adını belirtir.|
|`EntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Uygulama çalıştırıldığında yürütülmesi gereken derlemeyi belirtir.|
|`ErrorReportUrl`|İsteğe bağlı `String` parametre.<br /><br /> ClickOnce yüklemeleri sırasında karşılaşılan iletişim kutularında görüntülenen Web sitesini belirtir.|
|`Files`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Uygulama yayımlandığında dağıtılacak dosyaların listesini belirtir.|
|`ReferencedAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Projede başvurulan derlemeleri belirtir.|
|`RequiresMinimumFramework35SP1`|İsteğe bağlı `Boolean` çıkış parametresi.<br /><br /> `true`uygulama için .NET Framework 3,5 SP1 gerekir.|
|`SigningManifests`|İsteğe bağlı `Boolean` çıkış parametresi.<br /><br /> `true`ClickOnce bildirimleri imzalanır.|
|`SuiteName`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın yükleneceği **Başlangıç** menüsünde klasörün adını belirtir.|
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametre.<br /><br /> bu uygulamanın hedeflediği .NET Framework sürümünü belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)