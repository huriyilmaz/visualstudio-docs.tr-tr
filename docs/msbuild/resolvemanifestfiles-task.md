---
title: ResolveManifestFiles Görev | Microsoft Docs
description: Derleme MSBuild öğeleri bildirim oluşturma dosyalarına çözümlemek için ResolveManifestFiles görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f0306ef70bf7aa2c74875001bbd6f4e1a3bec2c14be65565cda0c56ac13892f8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270373"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles görevi

Derleme sürecindeki aşağıdaki öğeleri bildirim oluşturma dosyalarına çözümler: derleme öğeleri, bağımlılıklar, uydular, içerik, hata ayıklama sembolleri ve belgeler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `ResolveManifestFiles` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DeploymentManifestEntryPoint`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Dağıtım bildiriminin adını belirtir.|
|`EntryPoint`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Yönetilen derlemeyi veya ClickOnce giriş noktası olan bildirim başvurularını belirtir.|
|`ExtraFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Ek dosyaları belirtir.|
|`ManagedAssemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Yönetilen derlemeleri belirtir.|
|`NativeAssemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Yerel derlemeleri belirtir.|
|`OutputAssemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Oluşturulan derlemeleri belirtir.|
|`OutputDeploymentManifestEntryPoint`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı çıkış parametresi.<br /><br /> Çıkış dağıtım bildirimi giriş noktasını belirtir.|
|`OutputEntryPoint`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı çıkış parametresi.<br /><br /> Çıkış giriş noktasını belirtir.|
|`OutputFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Çıkış dosyalarını belirtir.|
|`PublishFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Yayımlama dosyalarını belirtir.|
|`SatelliteAssemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Uydu derlemelerini belirtir.|
|`SigningManifests`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` bildirimleri imzalanmıştır.|
|`TargetCulture`|İsteğe `String` bağlı parametre.<br /><br /> Uydu derlemeleri için hedef kültürü belirtir.|
|`TargetFrameworkVersion`|İsteğe `String` bağlı parametre.<br /><br /> Hedef sürüm .NET Framework belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
