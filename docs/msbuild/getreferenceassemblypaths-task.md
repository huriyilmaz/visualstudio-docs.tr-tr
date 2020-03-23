---
title: GetReferenceAssemblyPaths Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: d2ca532e37fa2f70800416539a7de2ff5e9978e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633986"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths görev

Çeşitli çerçevelerin başvuru derleme yollarını döndürür.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `GetReferenceAssemblyPaths` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|İsteğe bağlı `String[]` çıktı parametresi.<br /><br /> `TargetFrameworkMoniker` Parametreye göre yolu döndürür. Null `TargetFrameworkMoniker` veya boş ise, bu `String.Empty`yol .|
|`FullFrameworkReferenceAssemblyPaths`|İsteğe bağlı `String[]` çıktı parametresi.<br /><br /> Takma aparatın `TargetFrameworkMoniker` profil kısmını dikkate almadan, parametreye dayalı yolu döndürür. Null `TargetFrameworkMoniker` veya boş ise, bu `String.Empty`yol .|
|`TargetFrameworkMoniker`|İsteğe bağlı `String` parametre.<br /><br /> Başvuru derleme yolları ile ilişkili hedef çerçeve takma belirtir.|
|`RootPath`|İsteğe bağlı `String` parametre.<br /><br /> Başvuru derleme yolunu oluşturmak için kullanılacak kök yolu belirtir.|
|`BypassFrameworkInstallChecks`|İsteğe bağlı <xref:System.Boolean> parametre.<br /><br /> Hedef `true`çerçeveye bağlı olarak `GetReferenceAssemblyPaths` belirli çalışma zamanı çerçevelerinin yüklendiğinden emin olmak için varsayılan olarak gerçekleştiren temel denetimleri atlarsa.|
|`TargetFrameworkMonikerDisplayName`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Hedef çerçeve takma adının görüntüadını belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere sahip olmanın yanı sıra, bu görev <xref:Microsoft.Build.Tasks.TaskExtension> sınıftan devralınan parametreleri de devralır. <xref:Microsoft.Build.Utilities.Task> Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)