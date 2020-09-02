---
title: GetFrameworkPath Görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b528d0a4971d1d070c69d12cdb9a693d9a30f20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149490"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Derlemelerin yolunu alır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Aşağıdaki tablo, görevin parametrelerini açıklar `GetFrameworkPath` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 1,1 derlemelerinin yolunu içerir. Aksi halde döndürür `null` .|  
|`FrameworkVersion20Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 2,0 derlemelerinin yolunu içerir. Aksi halde döndürür `null` .|  
|`FrameworkVersion30Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 3,0 derlemelerinin yolunu içerir. Aksi halde döndürür `null` .|  
|`FrameworkVersion35Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 3,5 derlemelerinin yolunu içerir. Aksi halde döndürür `null` .|  
|`FrameworkVersion40Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa Framework sürüm 4,0 derlemelerinin yolunu içerir. Aksi halde döndürür `null` .|  
|`Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Varsa, en son çerçeve derlemelerinin yolunu içerir. Aksi halde döndürür `null` .|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulamasının birkaç sürümü [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] yüklüyse, bu görev [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] üzerinde çalışmak üzere tasarlanan sürümü döndürür.  
  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesini `GetFrameworkPath` özelliğindeki öğesine yolunu depolamak için kullanır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `FrameworkPath` .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
