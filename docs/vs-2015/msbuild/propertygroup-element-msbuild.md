---
title: PropertyGroup öğesi (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6590464b78d6b5452ce266d701aefc0f739185b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155945"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcı tanımlı [özellik](../msbuild/property-element-msbuild.md) öğeleri kümesi içerir. `Property`Bir projede kullanılan her öğe [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bir `PropertyGroup` öğesinin alt öğesi olmalıdır.  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>Syntax  
  
```  
<PropertyGroup Condition="'String A' == 'String B'">  
    <Property1>...</Property1>  
    <Property2>...</Property2>  
</PropertyGroup>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Koşul|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Özellik](../msbuild/property-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Özellik değerini içeren Kullanıcı tanımlı özellik adı. Bir öğede sıfır veya daha fazla *özellik* öğesi olabilir `PropertyGroup` .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Proje dosyasının gerekli kök öğesi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir koşula bağlı olarak özelliklerin nasıl ayarlanacağını gösterir. Bu örnekte, özelliğinin değeri ise,, `CompileConfig` `DEBUG` `Optimization` `Obfuscate` ve `OutputPath` öğelerinin içindeki Özellikler `PropertyGroup` ayarlanır.  
  
```  
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >  
    <Optimization>false</Optimization>  
    <Obfuscate>false</Obfuscate>  
    <OutputPath>$(OutputPath)\debug</OutputPath>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild özellikleri](msbuild-properties1.md)
