---
title: CreateCSharpManifestResourceName görevi | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8e72ef282911ecb36fb9a16838f6cc311e253e1
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634363"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName görevi

Verilen bir C# *. resx* dosya adından veya başka bir kaynaktan bir-Style bildirim adı oluşturur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda [CreateCSharpManifestResourceName görevinin](../msbuild/createcsharpmanifestresourcename-task.md)parametreleri açıklanmaktadır.

| Parametre | Açıklama |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkışı salt okunurdur parametresi.<br /><br /> Elde edilen bildirim adları. |
| `ResourceFiles` | Gerekli `String` parametresi.<br /><br /> C# Bildirim adının oluşturulacağı kaynak dosyasının adı. |
| `RootNamespace` | İsteğe bağlı `String` parametresi.<br /><br /> Kaynak dosyasının genellikle proje dosyasından alınan kök ad alanı. `null`olabilir. |
| `PrependCultureAsDirectory` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, kültür adı bildirim kaynağı adından hemen önce bir dizin adı olarak eklenir. Varsayılan değer `true`. |
| `ResourceFilesWithManifestResourceNames` | İsteğe bağlı salt okunurdur `String` output parametresi.<br /><br /> Artık bildirim kaynağı adını içeren kaynak dosyasının adını döndürür. |

## <a name="remarks"></a>Açıklamalar

 [CreateVisualBasicManifestResourceName görevi](../msbuild/createvisualbasicmanifestresourcename-task.md) , belirli bir *. resx* veya diğer kaynak dosyasına atanacak uygun bildirim kaynağı adını belirler. Görev, bir kaynak dosyasına mantıksal bir ad sağlar ve ardından bunu meta veriler olarak bir çıkış parametresine ekler.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
