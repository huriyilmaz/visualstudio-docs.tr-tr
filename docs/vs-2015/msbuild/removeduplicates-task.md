---
title: Removeyinelemeler görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73ad829c86305ff4d9a54025467e262d56e24dbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159250"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen öğe koleksiyonundan yinelenen öğeleri kaldırır.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `RemoveDuplicates` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Filtered`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Tüm yinelenen öğeleri kaldırılmış bir öğe koleksiyonu içerir.|  
|`Inputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Yinelenen öğelerin kaldırılacağı öğe koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görev, büyük/küçük harfe duyarlıdır ve yinelenenleri belirlerken öğe meta verilerini karşılaştırmaz.  
  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `RemoveDuplicates` öğe koleksiyonundan yinelenen öğeleri kaldırmak için görevini kullanır `MyItems` . Görev tamamlandığında, `FilteredItems` öğe koleksiyonu bir öğe içerir.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [Görevler](../msbuild/msbuild-tasks.md)
