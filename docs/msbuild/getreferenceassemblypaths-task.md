---
title: GetReferenceAssemblyPaths görevi | Microsoft Docs
description: Çeşitli çerçevelerin başvuru derleme yollarını döndürmek için MSBuild GetReferenceAssemblyPaths görevini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bbe9366e9b4b2c795b21ba46bd8320599c9e572
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436803"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths görevi

Çeşitli çerçevelerin başvuru derleme yollarını döndürür.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `GetReferenceAssemblyPaths` .

|Parametre|Açıklama|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|İsteğe bağlı `String[]` çıkış parametresi.<br /><br /> Parametreye göre yolu döndürür `TargetFrameworkMoniker` . `TargetFrameworkMoniker`Null veya boş ise, bu yol olur `String.Empty` .|
|`FullFrameworkReferenceAssemblyPaths`|İsteğe bağlı `String[]` çıkış parametresi.<br /><br /> `TargetFrameworkMoniker`Adın profil bölümünü düşünmeksizin parametreye göre yolu döndürür. `TargetFrameworkMoniker`Null veya boş ise, bu yol olur `String.Empty` .|
|`TargetFrameworkMoniker`|İsteğe bağlı `String` parametre.<br /><br /> Başvuru derleme yollarıyla ilişkili hedef Framework bilinen adını belirtir.|
|`RootPath`|İsteğe bağlı `String` parametre.<br /><br /> Başvuru derleme yolunu oluşturmak için kullanılacak kök yolu belirtir.|
|`BypassFrameworkInstallChecks`|İsteğe bağlı <xref:System.Boolean> parametre.<br /><br /> `true`, `GetReferenceAssemblyPaths` Hedef çerçeveye bağlı olarak, belirli çalışma zamanı çerçevelerinin yüklü olduğundan emin olmak için varsayılan olarak gerçekleştirilen temel denetimleri atlar.|
|`TargetFrameworkMonikerDisplayName`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Hedef çerçeve adının görünen adını belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)