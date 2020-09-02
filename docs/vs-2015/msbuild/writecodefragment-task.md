---
title: Writecobirleştirme görevi | Microsoft Docs
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
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa9882d30a8483937f77da21bb4700d4899a68a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555484"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen oluşturulmuş kod parçasındaki geçici bir kod dosyası oluşturur. Dosyayı silmez.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `WriteCodeFragment` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AssemblyAttributes`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Yazılacak özniteliklerin açıklaması. Öğe `Include` değeri, özniteliğin tam tür adıdır, örneğin, "System. AssemblyVersionAttribute".<br /><br /> Her meta veri, türünde olması gereken bir parametrenin ad-değer çiftidir `String` . Bazı öznitelikler yalnızca konumsal Oluşturucu bağımsız değişkenlerine izin veriyor. Ancak, herhangi bir öznitelikte bu tür bağımsız değişkenleri kullanabilirsiniz. Konumsal Oluşturucu özniteliklerini ayarlamak için, "_Parameter1", "_Parameter2" vb. gibi meta veri adlarını kullanın.<br /><br /> Bir parametre dizini atlanamaz.|  
|`Language`|Gerekli `String` parametre.<br /><br /> Oluşturulacak kodun dilini belirtir.<br /><br /> `Language` , CodeDom sağlayıcısının kullanılabildiği herhangi bir dil olabilir, örneğin, "C#" veya "VisualBasic". Yayınlanan dosya, bu dil için varsayılan dosya adı uzantısına sahip olacaktır.|  
|`OutputDirectory`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Oluşturulan kodun hedef klasörünü, genellikle ara klasörünü belirtir.|  
|`OutputFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Oluşturulan dosyanın yolunu belirtir. Bu parametre bir dosya adı kullanılarak ayarlandıysa, hedef klasör dosya adına eklenir. Bir kök kullanılarak ayarlandıysa, hedef klasör yok sayılır.<br /><br /> Bu parametre ayarlanmamışsa, çıkış dosyası adı hedef klasörüdür, rastgele bir dosya adı ve belirtilen dilin varsayılan dosya adı uzantısıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
