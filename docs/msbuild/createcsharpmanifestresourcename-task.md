---
title: CreateCSharpManifestResourceName Görev | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634363"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName görevi

Belirli bir *.resx* dosya adından veya başka bir kaynaktan C# stili bir bildirim adı oluşturur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda [CreateCSharpManifestResourceName görevparametreleri](../msbuild/createcsharpmanifestresourcename-task.md)açıklanmaktadır.

| Parametre | Açıklama |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıktı salt okunur parametresi.<br /><br /> Ortaya çıkan bildirim adları. |
| `ResourceFiles` | Gerekli `String` parametre.<br /><br /> C# manifesto adını oluşturmak için kaynak dosyasının adı. |
| `RootNamespace` | İsteğe bağlı `String` parametre.<br /><br /> Genellikle proje dosyasından alınan kaynak dosyasının kök ad alanı. `null`Olabilir. |
| `PrependCultureAsDirectory` | İsteğe bağlı `Boolean` parametre.<br /><br /> Kültür `true`adı, bildirim kaynağı adından hemen önce dizin adı olarak eklenirse. Varsayılan değer. `true` |
| `ResourceFilesWithManifestResourceNames` | İsteğe bağlı `String` salt okunur çıktı parametresi.<br /><br /> Şimdi manifest kaynak adını içeren kaynak dosyasının adını döndürür. |

## <a name="remarks"></a>Açıklamalar

 [CreateVisualBasicManifestResourceName görevi,](../msbuild/createvisualbasicmanifestresourcename-task.md) belirli bir *.resx* veya başka bir kaynak dosyasına atamak için uygun bildirim kaynak adını belirler. Görev, kaynak dosyasına mantıksal bir ad sağlar ve sonra bunu meta veri olarak çıktı parametresine bağlar.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
