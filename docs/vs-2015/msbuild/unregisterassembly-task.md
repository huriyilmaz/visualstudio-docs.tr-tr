---
title: UnregisterAssembly görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ef7ef7f4ec930b8aa338a8be33c4009b3009b20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193231"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen derlemelerin COM birlikte çalışma amacıyla kaydını siler. [RegisterAssembly görevinin](../msbuild/registerassembly-task.md)ters işlemini gerçekleştirir.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `UnregisterAssembly` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Kaydı kaldırılacak derlemeleri belirtir.|  
|`AssemblyListFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Görev ve görev arasındaki durum hakkındaki bilgileri içerir `RegisterAssembly` `UnregisterAssembly` . Bu, görevin, görevde kaydettirilemedi bir derlemenin kaydını silmeye çalışmasını önler `RegisterAssembly` .<br /><br /> Bu parametre belirtilmişse, `Assemblies` ve `TypeLibFiles` parametreleri yok sayılır.|  
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Belirtilen bütünleştirilmiş koddan belirtilen tür kitaplığının kaydını siler. **Note:**  Bu parametre yalnızca tür kitaplığı dosya adı derleme adından farklıysa gereklidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görevin başarılı olabilmesi için derlemenin mevcut olması gerekmez. Mevcut olmayan bir derlemenin kaydını silmeye çalışırsanız, görev bir uyarıyla başarılı olur. Bu durum, kayıt defterinden derleme kaydını kaldırmak için bu görevin bir işi olduğu için oluşur. Derleme yoksa, kayıt defterinde değildir ve bu nedenle görev başarılı olur.  
  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> <xref:System.MarshalByRefObject> . `MarshalByRefObject`Sınıfı sınıfla aynı işlevselliği sağlar <xref:Microsoft.Build.Utilities.Task> , ancak kendi uygulama etki alanında oluşturulabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsa, `UnregisterAssembly` ve özellikleri tarafından belirtilen yoldaki derlemenin kaydını silmek için görevini kullanır `OutputPath` `FileName` .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [RegisterAssembly görevi](../msbuild/registerassembly-task.md)   
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
