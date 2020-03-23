---
title: RequiresFramework35SP1Assembly Görev | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632777"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly görevi

Uygulamanın .NET Framework 3.5 SP1 gerekip gerekmediğini belirler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `RequiresFramework35SP1Assembly` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Uygulamada başvurulan derlemeleri belirtir.|
|`CreateDesktopShortcut`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`yükleme sırasında masaüstünde bir kısayol simgesi oluşturur.|
|`DeploymentManifestEntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Uygulama için bildirim dosya adını belirtir.|
|`EntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Uygulama çalıştırıldığında yürütülmesi gereken derlemeyi belirtir.|
|`ErrorReportUrl`|İsteğe bağlı `String` parametre.<br /><br /> ClickOnce yüklemeleri sırasında karşılaşılan iletişim kutularında görüntülenen Web sitesini belirtir.|
|`Files`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Uygulama yayımlandığında dağıtılacak dosyaların listesini belirtir.|
|`ReferencedAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Projede başvurulan derlemeleri belirtir.|
|`RequiresMinimumFramework35SP1`|İsteğe bağlı `Boolean` çıktı parametresi.<br /><br /> Eğer `true`, uygulama gerektirir .NET Framework 3.5 SP1.|
|`SigningManifests`|İsteğe bağlı `Boolean` çıktı parametresi.<br /><br /> `true`, ClickOnce bildirimleri imzalanırsa.|
|`SuiteName`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın yüklendiği **Başlat** menüsündeki klasörün adını belirtir.|
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametre.<br /><br /> .NET Framework sürümünü belirtir, bu uygulama nın hedeflemesi.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere sahip olmanın yanı sıra, bu görev <xref:Microsoft.Build.Tasks.TaskExtension> sınıftan devralınan parametreleri de devralır. <xref:Microsoft.Build.Utilities.Task> Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)