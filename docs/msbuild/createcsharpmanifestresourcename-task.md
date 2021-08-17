---
title: CreateCSharpManifestResourceName Görev | Microsoft Docs
description: CreateCSharpManifestResourceName MSBuild kullanarak belirli bir .resx dosya adı veya başka bir kaynaktan C# stilinde bir bildirim adı oluşturun.
ms.custom: SEO-VS-2020
ms.date: 11/15/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 900665ce4ea91c83559aa470344c3d0b4cd60c6fd7590b3a2bbc376f6f069940
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370352"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName görevi

Belirli bir *.resx* dosya adı veya başka bir kaynaktan C# stili bir bildirim adı oluşturur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda [CreateCSharpManifestResourceName görevinin parametreleri açık almaktadır.](../msbuild/createcsharpmanifestresourcename-task.md)

| Parametre | Açıklama |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`salt okunur parametresi çıktısı.<br /><br /> Sonuçta elde edilen bildirim adları. |
| `ResourceFiles` | Gerekli `String` parametre.<br /><br /> C# bildirim adının oluşturularak kaynak dosyasının adı. |
| `RootNamespace` | İsteğe `String` bağlı parametre.<br /><br /> Genellikle proje dosyasından alınan kaynak dosyasının kök ad alanı. olabilir. `null` |
| `PrependCultureAsDirectory` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` kültür adı bildirim kaynağı adının hemen öncesinde bir dizin adı olarak eklenir. Varsayılan değer `true` olarak belirlenmiştir. |
| `ResourceFilesWithManifestResourceNames` | İsteğe bağlı salt `String` okunur çıkış parametresi.<br /><br /> Artık bildirim kaynağı adını içeren kaynak dosyasının adını döndürür. |

## <a name="remarks"></a>Açıklamalar

 [CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md) görevi, belirli bir *.resx* dosyasına veya başka bir kaynak dosyasına atanacak uygun bildirim kaynak adını belirler. Görev, bir kaynak dosyasına mantıksal bir ad sağlar ve sonra bunu meta veri olarak bir çıkış parametresine iliştirer.

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
