---
title: İleti görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48e867cd0993106247f7105c1102f4e1407a4fed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190900"
---
# <a name="message-task"></a>İleti Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Derleme sırasında bir iletiyi günlüğe kaydeder.  
  
## <a name="parameters"></a>Parametreler  
 Katlama tablosu, görevin parametrelerini açıklar `Message` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Importance`|İsteğe bağlı `String` parametre.<br /><br /> İletinin önemini belirtir. Bu parametre, veya değerine sahip olabilir `high` `normal` `low` . Varsayılan değer: `normal`.|  
|`Text`|İsteğe bağlı `String` parametre.<br /><br /> Günlüğe kaydedilecek hata metni.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu `Message` görev, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projelerin, derleme işlemindeki farklı adımlarda oturum cihazlarına ileti vermesini sağlar.  
  
 `Condition`Parametresi olarak değerlendirilirse `true` , `Text` parametrenin değeri günlüğe kaydedilir ve derleme yürütülmeye devam eder. Bir `Condition` parametre yoksa, ileti metni günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Varsayılan olarak, ileti MSBuild konsol günlükçüsü öğesine gönderilir. Bu, parametresi ayarlanarak değiştirilebilir <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> . Günlükçü, parametreyi Yorumlar `Importance` .  
  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, tüm kayıtlı Günlükçüler için iletileri günlüğe kaydeder.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Derleme Günlüklerini Alma](../msbuild/obtaining-build-logs-with-msbuild.md)
