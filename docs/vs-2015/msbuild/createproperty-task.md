---
title: CreateProperty görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea16950e47760e89204503413fd98811e781d059
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184054"
---
# <a name="createproperty-task"></a>CreateProperty Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özellikleri geçirilen değerlerle doldurur. Bu, değerlerin bir özellikten veya dizeden diğerine kopyalanmasını sağlar.  
  
## <a name="attributes"></a>Öznitelikler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `CreateProperty` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Value`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yeni özelliğe kopyalanacak değeri belirtir.|  
|`ValueSetByTask`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Parametresiyle aynı değeri içerir `Value` . Bu parametreyi yalnızca [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , çıktılar güncel olduğundan, kapsayan hedefi atlayarak çıkış özelliğinin ayarlanmış olmasını önlemek istediğinizde kullanın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `CreateProperty` `NewFile` ve özelliğinin değerlerinin birleşimini kullanarak özelliğini oluşturmak için görevini kullanır `SourceFilename` `SourceFileExtension` .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Projeyi çalıştırdıktan sonra `NewFile` özelliğin değeri `Module1.vb` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevler](../msbuild/msbuild-tasks.md)
