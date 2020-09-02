---
title: Atama ProjectConfiguration görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e2091fad7e527990e8ed89ea8622cf41c1ae1ac4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187027"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu görev bir liste yapılandırma dizelerini kabul eder ve bunları belirtilen projelere atar.  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Aşağıdaki tablo, görevin parametrelerini açıklar `AssignProjectConfiguration` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|İsteğe bağlı `string` çıkış parametresi.<br /><br /> Her proje için bir proje yapılandırması içeren bir XML dizesi içerir. Yapılandırma, adlandırılmış projelere atanır.|  
|`DefaultToVcxPlatformMapping`|İsteğe bağlı `string` çıkış parametresi.<br /><br /> Kullanılan platform adlarından noktalı virgülle ayrılmış bir eşleme listesi içerir<br /><br /> . vcxproj dosyaları tarafından kullanılan çoğu türden.<br /><br /> Örneğin:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|İsteğe Bağlı<br /><br /> `string` çıkış parametresi.<br /><br /> . Vcxproj platform adlarından, çoğu tür tarafından kullanılan platform adlarına yapılan eşlemelerin noktalı virgülle ayrılmış bir listesini içerir.<br /><br /> Örneğin:<br /><br /> `"Win32=AnyCPU;X64=X64"`|  
|`CurrentProjectConfiguration`|İsteğe bağlı `string` çıkış parametresi.<br /><br /> Geçerli projenin yapılandırmasını içerir.|  
|`CurrentProjectPlatform`|İsteğe bağlı `string` çıkış parametresi.<br /><br /> Geçerli projenin platformunu içerir.|  
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|İsteğe bağlı `bool` çıkış parametresi.<br /><br /> Başvuruların proje yapılandırmasında devre dışı bırakılmış olsa bile oluşturulması gerektiğini belirten bir bayrak içerir.|  
|`ShouldUnsetParentConfigurationAndPlatform`|İsteğe bağlı `bool` çıkış parametresi.<br /><br /> Üst yapılandırmanın ve platformun atlanacağını belirten bir bayrak içerir.|  
|`OutputType`|İsteğe bağlı `string` çıkış parametresi.<br /><br /> Projenin çıkış türünü içerir.|  
|`ResolveConfigurationPlatformUsingMappings`|İsteğe bağlı `bool` çıkış parametresi.<br /><br /> Derleme, geçirilen proje başvurularının yapılandırma ve platformunu çözümlemek için varsayılan eşlemeleri kullanması gerekip gerekmediğini belirten bir bayrak içerir.|  
|`AssignedProjects`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Çözümlenen başvuru yollarının listesini içerir.|  
|`UnassignedProjects`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Önceden çözümlenmiş çıkış listesi kullanılarak çözülemeyen proje başvuru öğelerinin listesini içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
