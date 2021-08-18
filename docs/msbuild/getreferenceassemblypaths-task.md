---
title: GetReferenceAssemblyPaths Görev | Microsoft Docs
description: Çeşitli MSBuild başvuru derleme yollarını geri almak için GetReferenceAssemblyPaths görevini kullanın.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0909253f87a6eb1e65463d84fb0ff07a2d9cb781
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077341"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths görevi

Çeşitli çerçevelerin başvuru derleme yollarını döndürür.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `GetReferenceAssemblyPaths` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|İsteğe `String[]` bağlı çıkış parametresi.<br /><br /> parametresine göre yolu `TargetFrameworkMoniker` döndürür. null `TargetFrameworkMoniker` veya boşsa, bu yol `String.Empty` olur.|
|`FullFrameworkReferenceAssemblyPaths`|İsteğe `String[]` bağlı çıkış parametresi.<br /><br /> Bilinen adın profil bölümünü `TargetFrameworkMoniker` dikkate almadan parametresine göre yolu döndürür. null `TargetFrameworkMoniker` veya boşsa, bu yol `String.Empty` olur.|
|`TargetFrameworkMoniker`|İsteğe `String` bağlı parametre.<br /><br /> Başvuru derleme yolları ile ilişkili hedef çerçeve bilinen adı belirtir.|
|`RootPath`|İsteğe `String` bağlı parametre.<br /><br /> Başvuru derleme yolunu oluşturmak için kullanmak üzere kök yolu belirtir.|
|`BypassFrameworkInstallChecks`|İsteğe <xref:System.Boolean> bağlı parametre.<br /><br /> ise, hedef çerçeveye bağlı olarak belirli çalışma zamanı çerçevelerinin yüklü olduğundan emin olmak için varsayılan `true` `GetReferenceAssemblyPaths` olarak gerçekleştirdiği temel denetimleri atlar.|
|`TargetFrameworkMonikerDisplayName`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Hedef çerçeve bilinen adı için görünen adı belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)