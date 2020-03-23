---
title: AtamaProjectConfiguration Görev | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5159b73058c73c925cae644c2e3ddd2bc84ac41
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634558"
---
# <a name="assignprojectconfiguration-task"></a>AtamaProjectConfiguration görev

Bu görev, bir liste yapılandırma dizeleri kabul eder ve bunları belirtilen projelere atar.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevparametreleri `AssignProjectConfiguration` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`SolutionConfigurationContents`|İsteğe bağlı `string` çıktı parametresi.<br /><br /> Her proje için proje yapılandırması içeren bir XML dizesi içerir. Yapılandırmalar adlandırılmış projelere atanır.|
|`DefaultToVcxPlatformMapping`|İsteğe bağlı `string` çıktı parametresi.<br /><br /> *.vcxproj* dosyaları tarafından kullanılançoğu türtarafından kullanılan platform adlarından yarı sütunlu sınırlı eşlemeler listesi içerir.<br /><br /> Örnek:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|İsteğe bağlı<br /><br /> `string`çıkış parametresi.<br /><br /> *.vcxproj* platform adlarından çoğu türde kullanılan platform adlarına kadar eşlemelerin yarı sütunlu sınırlı bir listesini içerir.<br /><br /> Örnek:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|İsteğe bağlı `string` çıktı parametresi.<br /><br /> Geçerli proje yapılandırmasını içerir.|
|`CurrentProjectPlatform`|İsteğe bağlı `string` çıktı parametresi.<br /><br /> Geçerli proje için platformu içerir.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|İsteğe bağlı `bool` çıktı parametresi.<br /><br /> Proje yapılandırmasında devre dışı bırakılmış olsalar bile başvuruların oluşturulması gerektiğini belirten bir bayrak içerir.|
|`ShouldUnsetParentConfigurationAndPlatform`|İsteğe bağlı `bool` çıktı parametresi.<br /><br /> Üst yapılandırma ve platformun ayarsız bırakılmaması gerektiğini belirten bir bayrak içerir.|
|`OutputType`|İsteğe bağlı `string` çıktı parametresi.<br /><br /> Projenin çıktı türünü içerir.|
|`ResolveConfigurationPlatformUsingMappings`|İsteğe bağlı `bool` çıktı parametresi.<br /><br /> Yapının proje başvurularında geçirilen yapılandırmayı ve platformu çözmek için varsayılan eşlemeleri kullanıp kullanmaması gerektiğini belirten bir bayrak içerir.|
|`AssignedProjects`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Çözülen başvuru yollarının listesini içerir.|
|`UnassignedProjects`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Önceden çözülmüş çıktılar listesini kullanarak çözülmeyen proje başvuru öğelerinin listesini içerir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
