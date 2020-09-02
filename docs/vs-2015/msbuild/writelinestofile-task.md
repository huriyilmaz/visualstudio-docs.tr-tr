---
title: WriteLinesToFile Görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f530648c7dd772fb60148f4d755d4a4ffb420cbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62419965"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen öğelerin yollarını belirtilen metin dosyasına yazar.  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Aşağıdaki tablo, görevin parametrelerini açıklar `WriteLinestoFile` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`File`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Öğelerin yazılacağı dosyayı belirtir.|  
|`Lines`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Dosyaya yazılacak öğeleri belirtir.|  
|`Overwrite`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , görev dosyadaki varolan içeriğin üzerine yazar.|  
|`Encoding`|İsteğe bağlı `String` parametre.<br /><br /> Karakter kodlamasını seçer, örneğin, "UNICODE".  Ayrıca bkz <xref:System.Text.Encoding> ..|  
  
## <a name="remarks"></a>Açıklamalar  
 `Overwrite`İse, `true` Yeni bir dosya oluşturur, içeriği dosyaya yazın ve sonra dosyayı kapatır. Hedef dosya zaten varsa, üzerine yazılır. `Overwrite`İse, `false` içeriği dosyaya ekler, zaten mevcut değilse hedef dosyayı oluşturur.  
  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğe koleksiyonundaki `WriteLinesToFile` öğelerin yollarını öğe `MyItems` koleksiyonu tarafından belirtilen dosyaya yazmak için görevini kullanır `MyTextFile` .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
