---
title: Uyarı görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adbddc2fb36e5036e535dfc1049945187fe14ed0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62558495"
---
# <a name="warning-task"></a>Uyarı Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Değerlendirilen bir koşullu ifadeye dayanan bir derleme sırasında bir uyarı kaydeder.  
  
## <a name="parameters"></a>Parametreler  
 Katlama tablosu, görevin parametrelerini açıklar `Warning` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Code`|İsteğe bağlı `String` parametre.<br /><br /> Uyarıyla ilişkilendirilecek uyarı kodu.|  
|`File`|İsteğe bağlı `String` parametre.<br /><br /> Varsa ilgili dosyayı belirtir. Dosya sağlanmazsa, uyarı görevini içeren dosya kullanılır.|  
|`HelpKeyword`|İsteğe bağlı `String` parametre.<br /><br /> Uyarıyla ilişkilendirilecek Yardım anahtar sözcüğü.|  
|`Text`|İsteğe bağlı `String` parametre.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Parametresi olarak değerlendirilirse günlüğe kaydeden uyarı metni `Condition` `true` .|  
  
## <a name="remarks"></a>Açıklamalar  
 `Warning`Görev, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bir sonraki derleme adımına geçmeden önce, projelerin gerekli bir yapılandırma veya özellik varlığını denetlemesini sağlar.  
  
 `Condition` `Warning` Görevin parametresi olarak değerlendirilirse `true` , `Text` parametrenin değeri günlüğe kaydedilir ve derleme yürütülmeye devam eder. Bir `Condition` parametre mevcut değilse, uyarı metni günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, komut satırında ayarlanan özellikleri denetler. Hiçbir özellik ayarlanmamışsa, proje bir uyarı olayı oluşturur ve görevin parametresinin değerini günlüğe kaydeder `Text` `Warning` .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
