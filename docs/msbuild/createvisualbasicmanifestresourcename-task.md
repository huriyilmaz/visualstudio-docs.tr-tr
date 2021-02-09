---
title: CreateVisualBasicManifestResourceName görevi | Microsoft Docs
description: Verilen bir. resx dosya adından veya başka bir kaynaktan Visual Basic stili bir bildirim adı oluşturmak için MSBuild CreateVisualBasicManifestResourceName görevini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8e9f0868cb774ee82c79ba190acddebf63193cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901378"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName görevi

Verilen bir *. resx* dosya adından veya başka bir kaynaktan Visual Basic stili bir bildirim adı oluşturur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda [CreateVisualBasicManifestResourceName görevinin](../msbuild/createvisualbasicmanifestresourcename-task.md)parametreleri açıklanmaktadır.

| Parametre | Açıklama |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`salt okuma parametresi çıktı.<br /><br /> Elde edilen bildirim adları. |
| `ResourceFiles` | Gerekli `String` parametre.<br /><br /> Visual Basic bildirim adının oluşturulacağı kaynak dosyasının adı. |
| `RootNamespace` | İsteğe bağlı `String` parametre.<br /><br /> Kaynak dosyasının genellikle proje dosyasından alınan kök ad alanı. Olabilir `null` . |
| `PrependCultureAsDirectory` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , kültür adı bildirim kaynağı adından hemen önce bir dizin adı olarak eklenir. Varsayılan değer `true` olarak belirlenmiştir. |
| `ResourceFilesWithManifestResourceNames` | İsteğe bağlı salt okunurdur `String` çıkış parametresi.<br /><br /> Artık bildirim kaynağı adını içeren kaynak dosyasının adını döndürür. |

## <a name="remarks"></a>Açıklamalar

 [CreateVisualBasicManifestResourceName görevi](../msbuild/createvisualbasicmanifestresourcename-task.md) , belirli bir *. resx* veya diğer kaynak dosyasına atanacak uygun bildirim kaynağı adını belirler. Görev, bir kaynak dosyasına mantıksal bir ad sağlar ve ardından bunu meta veriler olarak bir çıkış parametresine ekler.

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
