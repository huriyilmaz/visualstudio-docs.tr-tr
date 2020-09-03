---
title: ParameterGroup Öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f4faa9038a5931dec376903f166301f27f00b37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154795"
---
# <a name="parametergroup-element"></a>ParameterGroup Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tarafından oluşturulan görevde mevcut olacak parametrelerin isteğe bağlı bir listesini içerir `UsingTask``TaskFactory` . Daha fazla bilgi için bkz. [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ParameterGroup />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Parametre](../msbuild/parameter-element.md)|Tarafından oluşturulan bir görev için belirli bir parametre hakkında bilgi içerir `UsingTask``TaskFactory` . Öğesinin adı parametrenin adıdır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|İçindeki görevleri kaydetmek için bir yol sağlar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Bir projede sıfır veya daha fazla `UsingTask` öğe olabilir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesinin nasıl kullanılacağını gösterir `ParameterGroup` .  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
