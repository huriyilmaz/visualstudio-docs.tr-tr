---
title: XmlPoke Görevi | Microsoft Docs
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
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ba57c1578bd69d71ed0abdac45907d937b89ecb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198963"
---
# <a name="xmlpoke-task"></a>XmlPoke Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir XPath sorgusu tarafından belirtilen değerleri bir XML dosyasına ayarlar.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `XmlPoke` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Namespaces`|İsteğe bağlı `String` parametre.<br /><br /> XPath sorgu ön ekleri için ad alanlarını belirtir.|  
|`Query`|İsteğe bağlı `String` parametre.<br /><br /> XPath sorgusunu belirtir.|  
|`Value`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Çıkış dosyasını belirtir.|  
|`XmlInputPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> XML girişini dosya yolu olarak belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
