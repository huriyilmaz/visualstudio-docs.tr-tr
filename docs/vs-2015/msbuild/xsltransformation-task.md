---
title: XslTransformation görevi | Microsoft Docs
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
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1705fd2b79f8b5044aa4ffa0b65801d6db6c7f33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198951"
---
# <a name="xsltransformation-task"></a>XslTransformation Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir XSLT veya derlenmiş XSLT kullanarak bir XML girişini dönüştürür ve çıkış cihazına veya bir dosyaya çıktılar verir.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `XslTransformation` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`OutputPaths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> XML dönüştürmesi için çıkış dosyalarını belirtir.|  
|`Parameters`|İsteğe bağlı `String` parametre.<br /><br /> XSLT giriş belgesi için parametreleri belirtir.|  
|`XmlContent`|İsteğe bağlı `String` parametre.<br /><br /> XML girişini bir dize olarak belirtir.|  
|`XmlInputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> XML giriş dosyalarını belirtir.|  
|`XslCompiledDllPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Derlenen XSLT 'yi belirtir.|  
|`XslContent`|İsteğe bağlı `String` parametre.<br /><br /> XSLT girişini bir dize olarak belirtir.|  
|`XslInputPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> XSLT giriş dosyasını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
