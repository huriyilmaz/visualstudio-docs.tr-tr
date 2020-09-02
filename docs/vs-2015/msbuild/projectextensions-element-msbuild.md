---
title: Projecısions öğesi (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0afc4f73ed287f753acf87bd0b112e6f5303e996
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551262"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Proje dosyalarının bilgi olmayan bilgiler içermesini sağlar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Bir öğenin içindeki her şey `ProjectExtensions` tarafından yok sayılacak [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
 \<Project>  
 \<ProjectExtensions>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectExtensions>  
    Non-MSBuild information to include in file.  
</ProjectExtensions>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Hiçbiri  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Proje dosyasının gerekli kök öğesi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectExtensions`Bir projede yalnızca bir öğe kullanılabilir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir öğesinde depolanan tümleşik geliştirme ortamının bilgilerini gösterir `ProjectExtensions` .  
  
```  
<ProjectExtensions>  
    <VSIDE>  
        <External>  
            <!--  
            Raw XML passed to the IDE by an external source  
            -->  
        </External>  
    </VSIDE>  
</ProjectExtensions>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBUILD](msbuild.md)
