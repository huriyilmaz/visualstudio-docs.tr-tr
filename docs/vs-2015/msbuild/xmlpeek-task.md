---
title: XmlPeek görevi | Microsoft Docs
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
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d82deb9c363c1a1bd587cc9a6e48c5d6bf2138bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62584055"
---
# <a name="xmlpeek-task"></a>XmlPeek Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML dosyasından XPath sorgusuyla belirtilen değerleri döndürür.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `XmlPeek` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Namespaces`|İsteğe bağlı `String` parametre.<br /><br /> XPath sorgu önekleri için ad alanlarını belirtir.|  
|`Query`|İsteğe bağlı `String` parametre.<br /><br /> XPath sorgusunu belirtir.|  
|`Result`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Bu görev tarafından döndürülen sonuçları içerir.|  
|`XmlContent`|İsteğe bağlı `String` parametre.<br /><br /> XML girişini bir dize olarak belirtir.|  
|`XmlInputPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> XML girişini dosya yolu olarak belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
