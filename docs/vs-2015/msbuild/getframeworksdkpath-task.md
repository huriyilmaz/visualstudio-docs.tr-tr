---
title: GetFrameworkSdkPath görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6d527b00e8cbfe6a6f4ad5d112a23e46d4edb8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149549"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yolunu alır [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] .  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Aşağıdaki tablo, görevin parametrelerini açıklar `GetFrameworkSdkPath` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|İsteğe bağlı `String` salt okunurdur çıkış parametresi.<br /><br /> Varsa .NET SDK sürüm 2,0 'nin yolunu döndürür. Aksi halde döndürür `String.Empty` .|  
|`FrameworkSdkVersion35Path`|İsteğe bağlı `String` salt okunurdur çıkış parametresi.<br /><br /> Varsa .NET SDK sürüm 3,5 'nin yolunu döndürür. Aksi halde döndürür `String.Empty` .|  
|`FrameworkSdkVersion40Path`|İsteğe bağlı `String` salt okunurdur çıkış parametresi.<br /><br /> Varsa .NET SDK sürüm 4,0 'nin yolunu döndürür. Aksi halde döndürür `String.Empty` .|  
|`Path`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Herhangi bir sürüm varsa, en son .NET SDK 'nın yolunu içerir. Aksi halde döndürür `String.Empty` .|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesini `GetFrameworkSdkPath` özelliğindeki öğesine yolunu depolamak için kullanır [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] `SdkPath` .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
