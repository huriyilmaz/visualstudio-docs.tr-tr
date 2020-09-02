---
title: FormatVersion görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee6e163bd6587d93c970a56ac1c08383084ddc0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149620"
---
# <a name="formatversion-task"></a>FormatVersion Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sürüm numarasına Düzeltme numarasını ekler.  
  
- Örnek #1: giriş: sürüm = \<undefined> ;  Düzeltme = \<don't care> ;   Çıkış: OutputVersion = "1.0.0.0"  
  
- Case #2: Input: Version = "1.0.0. *" Revision = "5" çıkış: OutputVersion = "1.0.0.5"  
  
- Case #3: Input: Version = "1.0.0.0" Düzeltme = \<don't care> ;  Çıkış: OutputVersion = "1.0.0.0"  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `FormatVersion` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`FormatType`|İsteğe bağlı `String` parametre.<br /><br /> Biçim türünü belirtir.<br /><br /> -"Sürüm" = sürüm.<br />-"Path" = "." yerine "_";|  
|`OutputVersion`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Düzeltme numarasını içeren çıkış sürümünü belirtir.|  
|`Revision`|İsteğe bağlı `Int32` parametre.<br /><br /> Sürüme eklenecek düzeltmeyi belirtir.|  
|`Version`|İsteğe bağlı `String` parametre.<br /><br /> Biçimlendirilecek sürüm numarası dizesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
