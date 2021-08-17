---
title: CreateCSharpManifestResourceName görevi | Microsoft Docs
description: verilen bir. resx dosya adından veya başka bir kaynaktan C# stili bildirim adı oluşturmak için createcsharpmanifestresourcename görevi MSBuild kullanın.
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
ms.openlocfilehash: 2c8633972152cb1d8c08b21a2f6dd44bb20e77bd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054918"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName görevi

Verilen *. resx* dosya adından veya diğer kaynaklardan C# stili bir bildirim adı oluşturur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda [CreateCSharpManifestResourceName görevinin](../msbuild/createcsharpmanifestresourcename-task.md)parametreleri açıklanmaktadır.

| Parametre | Açıklama |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`salt okuma parametresi çıktı.<br /><br /> Elde edilen bildirim adları. |
| `ResourceFiles` | Gerekli `String` parametre.<br /><br /> C# bildirim adının oluşturulacağı kaynak dosyasının adı. |
| `RootNamespace` | İsteğe bağlı `String` parametre.<br /><br /> Kaynak dosyasının genellikle proje dosyasından alınan kök ad alanı. Olabilir `null` . |
| `PrependCultureAsDirectory` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , kültür adı bildirim kaynağı adından hemen önce bir dizin adı olarak eklenir. Varsayılan değer `true` olarak belirlenmiştir. |
| `ResourceFilesWithManifestResourceNames` | İsteğe bağlı salt okunurdur `String` çıkış parametresi.<br /><br /> Artık bildirim kaynağı adını içeren kaynak dosyasının adını döndürür. |

## <a name="remarks"></a>Açıklamalar

 [CreateCSharpManifestResourceName görevi](../msbuild/createcsharpmanifestresourcename-task.md) , belirli bir *. resx* veya diğer kaynak dosyasına atanacak uygun bildirim kaynağı adını belirler. Görev, bir kaynak dosyasına mantıksal bir ad sağlar ve ardından bunu meta veriler olarak bir çıkış parametresine ekler.

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
