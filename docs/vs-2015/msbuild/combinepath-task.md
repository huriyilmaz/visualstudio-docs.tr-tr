---
title: CombinePath görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b97714fc707d8f9174a01dcc1fe7b3b59176de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160390"
---
# <a name="combinepath-task"></a>CombinePath Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen yolları tek bir yol olarak birleştirir.  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Aşağıdaki tabloda [CombinePath görevinin](../msbuild/combinepath-task.md)parametreleri açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BasePath`|Gerekli `String` parametre.<br /><br /> Diğer yollarla birleştirilecek temel yol. Göreli yol, mutlak yol veya boş olabilir.|  
|`Paths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Birleşik yolu oluşturmak için BasePath ile birleştirilecek bağımsız yolların listesi. Yollar göreli veya mutlak olabilir.|  
|`CombinedPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Bu görev tarafından oluşturulan Birleşik yol.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
