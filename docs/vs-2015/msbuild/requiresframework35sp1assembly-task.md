---
title: RequiresFramework35SP1Assembly görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ada207a619021922b999d0e821ecf27ba48dbb38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158737"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanın .NET Framework 3,5 SP1 gerektirip gerektirmediğini belirler.  
  
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
|`RequiresMinimumFramework35SP1`|İsteğe bağlı `Boolean` çıkış parametresi.<br /><br /> `true`Uygulama için .NET Framework 3,5 SP1 gerekir.|  
|`SigningManifests`|İsteğe bağlı `Boolean` çıkış parametresi.<br /><br /> Varsa `true` , ClickOnce bildirimleri imzalanır.|  
|`SuiteName`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın yükleneceği **Başlangıç** menüsünde klasörün adını belirtir.|  
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametre.<br /><br /> Bu uygulamanın hedeflediği .NET Framework sürümünü belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
