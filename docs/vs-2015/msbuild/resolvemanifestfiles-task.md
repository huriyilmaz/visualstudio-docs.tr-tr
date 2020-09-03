---
title: ResolveManifestFiles görevi | Microsoft Docs
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
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ba088b91496c633afe34c20e40c12ded7d2279b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161359"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Derleme işlemindeki aşağıdaki öğeleri bildirim oluşturma için dosyalara çözümler: oluşturulan öğeler, bağımlılıklar, uydu, içerik, hata ayıklama sembolleri ve belgeler.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `ResolveManifestFiles` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Dağıtım bildiriminin adını belirtir.|  
|`EntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Bildirime giriş noktası olan yönetilen derlemeyi veya ClickOnce bildirim başvurusunu belirtir.|  
|`ExtraFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Ek dosyaları belirtir.|  
|`ManagedAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Yönetilen derlemeleri belirtir.|  
|`NativeAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Yerel derlemeleri belirtir.|  
|`OutputAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Oluşturulan derlemeleri belirtir.|  
|`OutputDeploymentManifestEntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Çıkış dağıtım bildirimi giriş noktasını belirtir.|  
|`OutputEntryPoint`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Çıkış giriş noktasını belirtir.|  
|`OutputFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Çıkış dosyalarını belirtir.|  
|`PublishFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Yayımlama dosyalarını belirtir.|  
|`SatelliteAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Uydu derlemelerini belirtir.|  
|`SigningManifests`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , bildirimler imzalanır.|  
|`TargetCulture`|İsteğe bağlı `String` parametre.<br /><br /> Uydu derlemeleri için hedef kültürü belirtir.|  
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametre.<br /><br /> Hedef .NET Framework sürümünü belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
