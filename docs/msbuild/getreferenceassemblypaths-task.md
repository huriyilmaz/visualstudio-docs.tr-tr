---
title: GetReferenceAssemblyPaths görevi | Microsoft Docs
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
ms.openlocfilehash: 56e3526f130a8717dec2dafeef794375ceffc37c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579612"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths görevi
Çeşitli çerçevelerin başvuru derleme yollarını döndürür.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `GetReferenceAssemblyPaths` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|İsteğe bağlı `String[]` çıkış parametresi.<br /><br /> `TargetFrameworkMoniker` parametresine göre yolu döndürür. `TargetFrameworkMoniker` null veya boşsa, bu yol `String.Empty`olur.|
|`FullFrameworkReferenceAssemblyPaths`|İsteğe bağlı `String[]` çıkış parametresi.<br /><br /> Adın profil bölümünü düşünmeksizin `TargetFrameworkMoniker` parametresine göre yolu döndürür. `TargetFrameworkMoniker` null veya boşsa, bu yol `String.Empty`olur.|
|`TargetFrameworkMoniker`|İsteğe bağlı `String` parametresi.<br /><br /> Başvuru derleme yollarıyla ilişkili hedef Framework bilinen adını belirtir.|
|`RootPath`|İsteğe bağlı `String` parametresi.<br /><br /> Başvuru derleme yolunu oluşturmak için kullanılacak kök yolu belirtir.|
|`BypassFrameworkInstallChecks`|İsteğe bağlı <xref:System.Boolean> parametresi.<br /><br /> `true`, hedef çerçeveye bağlı olarak, belirli çalışma zamanı çerçevelerinin yüklü olduğundan emin olmak için `GetReferenceAssemblyPaths` varsayılan olarak gerçekleştirdiği temel denetimleri atlar.|
|`TargetFrameworkMonikerDisplayName`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Hedef çerçeve adının görünen adını belirtir.|

## <a name="remarks"></a>Açıklamalar
 Tabloda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)