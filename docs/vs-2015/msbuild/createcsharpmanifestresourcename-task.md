---
title: CreateCSharpManifestResourceName görevi | Microsoft Docs
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
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9308f94e865bfe54384719d8f57f3ad1819c79fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184038"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verilen bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] . resx dosya adından veya başka bir kaynaktan bir-Style bildirim adı oluşturur.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda [CreateCSharpManifestResourceName görevinin](../msbuild/createcsharpmanifestresourcename-task.md)parametreleri açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem>`[]`salt okuma parametresi çıktı.<br /><br /> Elde edilen bildirim adları.|  
|`ResourceFiles`|Gerekli `String` parametre.<br /><br /> Bildirim adının oluşturulacağı kaynak dosyasının adı [!INCLUDE[csprcs](../includes/csprcs-md.md)] .|  
|`RootNamespace`|İsteğe bağlı `String` parametre.<br /><br /> Kaynak dosyasının genellikle proje dosyasından alınan kök ad alanı. Olabilir `null` .|  
|`PrependCultureAsDirectory`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , kültür adı bildirim kaynağı adından hemen önce bir dizin adı olarak eklenir. Varsayılan değer `true` .|  
|`ResourceFilesWithManifestResourceNames`|İsteğe bağlı salt okunurdur `String` çıkış parametresi.<br /><br /> Artık bildirim kaynağı adını içeren kaynak dosyasının adını döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 [CreateVisualBasicManifestResourceName görevi](../msbuild/createvisualbasicmanifestresourcename-task.md) , belirli bir. resx veya diğer kaynak dosyasına atanacak uygun bildirim kaynağı adını belirler. Görev, bir kaynak dosyasına mantıksal bir ad sağlar ve ardından bunu meta veriler olarak bir çıkış parametresine ekler.  
  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
