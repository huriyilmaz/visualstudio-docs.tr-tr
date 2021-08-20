---
title: AssignProjectConfiguration Görev | Microsoft Docs
description: Yapılandırma dizelerinin MSBuild ve bunları belirtilen projelere atamak için AssignProjectConfiguration görevini kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7d0f6adb8bd03225bffe7efe885c0d295b65f7e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150501"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration görevi

Bu görev bir liste yapılandırma dizelerini kabul eder ve bunları belirtilen projelere atar.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevin parametreleri açık `AssignProjectConfiguration` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`ProjectReferences`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> `[]` giriş parametresi.<br /><br /> Yapılandırılan projeler.|
|`SolutionConfigurationContents`|İsteğe `string` bağlı çıkış parametresi.<br /><br /> Her proje için proje yapılandırmasını içeren bir XML dizesi içerir. Yapılandırmalar adlandırılmış projelere atanır.|
|`DefaultToVcxPlatformMapping`|İsteğe `string` bağlı çıkış parametresi.<br /><br /> Çoğu tür tarafından kullanılan platform adlarından *.vcxproj* dosyaları tarafından kullanılanlara eşlemelerin noktalı virgülle ayrılmış listesini içerir.<br /><br /> Örnek:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|İsteğe Bağlı<br /><br /> `string` output parametresi.<br /><br /> *.vcxproj* platform adlarından çoğu tür tarafından kullanılan platform adlarından eşlemelerin noktalı virgülle ayrılmış listesini içerir.<br /><br /> Örnek:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|İsteğe `string` bağlı çıkış parametresi.<br /><br /> Geçerli projenin yapılandırmasını içerir.|
|`CurrentProjectPlatform`|İsteğe `string` bağlı çıkış parametresi.<br /><br /> Geçerli projenin platformunu içerir.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|İsteğe `bool` bağlı çıkış parametresi.<br /><br /> Proje yapılandırmasında devre dışı bırakılmış olsalar bile başvuruların nasıl inşa edileceklerini belirten bir bayrak içerir.|
|`ShouldUnsetParentConfigurationAndPlatform`|İsteğe `bool` bağlı çıkış parametresi.<br /><br /> Üst yapılandırmanın ve platformun kümeden silinip silinip siline olmadığını belirten bir bayrak içerir.|
|`OutputType`|İsteğe `string` bağlı çıkış parametresi.<br /><br /> Projenin çıkış türünü içerir.|
|`ResolveConfigurationPlatformUsingMappings`|İsteğe `bool` bağlı çıkış parametresi.<br /><br /> Derlemenin geçirilen proje başvurularının yapılandırmasını ve platformunu çözümlemek için varsayılan eşlemeleri kullanip kullanmay gerektiğini belirten bir bayrak içerir.|
|`AssignedProjects`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Çözümlenen başvuru yollarının listesini içerir.|
|`UnassignedProjects`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Çıkışların önceden çözümlenmiş listesi kullanılarak çözümlenemedi proje başvuru öğelerinin listesini içerir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
