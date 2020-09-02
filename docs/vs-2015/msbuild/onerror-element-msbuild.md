---
title: HataDurumunda öğe (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46f6907bea5954cffae92b41398717a8247350e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195669"
---
# <a name="onerror-element-msbuild"></a>OnError Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`ContinueOnError`Öznitelik `false` başarısız bir görev için ise, bir veya daha fazla hedefin yürütülmesine neden olur.  
  
 \<Project>  
 \<Target>  
 \<OnError>  
  
## <a name="syntax"></a>Syntax  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Gerekli öznitelik.<br /><br /> Bir görev başarısız olursa yürütülecek hedefler. Birden çok hedefi noktalı virgülle ayırın. Birden çok hedef belirtilen sırada yürütülür.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Hedef](../msbuild/target-element-msbuild.md)|Görevler için kapsayıcı öğesi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] öğe öğesinin `OnError` `Target` görevlerden biri `ContinueOnError` `ErrorAndStop` (veya) olarak ayarlanan öznitelik ile başarısız `false` olursa, öğesini yürütür. Görev başarısız olduğunda, özniteliğinde belirtilen hedefler `ExecuteTargets` yürütülür. Hedefte birden fazla `OnError` öğe varsa, `OnError` görev başarısız olduğunda öğeler sırayla yürütülür.  
  
 Özniteliği hakkında daha fazla bilgi için `ContinueOnError` , bkz. [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md). Hedefler hakkında daha fazla bilgi için bkz. [targets](../msbuild/msbuild-targets.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `TaskOne` ve `TaskTwo` görevlerini yürütür. `TaskOne`Başarısız olursa, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] öğesini değerlendirir `OnError` ve `OtherTarget` hedefi yürütür.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Targets](../msbuild/msbuild-targets.md)
