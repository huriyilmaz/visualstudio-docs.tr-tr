---
title: Output öğesi (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 52b8ef11e295d60e71a59820a48bca5e477c639d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163596"
---
# <a name="output-element-msbuild"></a>Çıktı Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğe ve özelliklerde görev çıkış değerlerini depolar.  
  
 \<Project>  
 \<Target>  
 \<Task>  
 \<Output>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`TaskParameter`|Gerekli öznitelik.<br /><br /> Görevin çıkış parametresinin adı.|  
|`PropertyName`|Ya da `PropertyName` `ItemName` özniteliği gereklidir.<br /><br /> Görevin çıkış parametre değerini alan özellik. Projeniz daha sonra `$(` *PropertyName* sözdizimi ile özelliğe başvurabilir `)` . Bu özellik adı yeni bir özellik adı veya projede zaten tanımlanmış bir ad olabilir.<br /><br /> Bu öznitelik `ItemName` de kullanılıyorsa kullanılamaz.|  
|`ItemName`|Ya da `PropertyName` `ItemName` özniteliği gereklidir.<br /><br /> Görevin çıkış parametre değerini alan öğe. Projeniz daha sonra `@(` *ItemName* `)` söz dizimine sahip öğeye başvurabilir. Öğe adı yeni bir öğe adı ya da projede zaten tanımlanmış bir ad olabilir.<br /><br /> Bu öznitelik `PropertyName` de kullanılıyorsa kullanılamaz.|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Görev](../msbuild/task-element-msbuild.md)|Bir görevin örneğini oluşturur ve yürütür [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği `Csc` bir öğesi içinde yürütülen görevi gösterir `Target` . Görev parametrelerine geçirilen öğeler ve özellikler bu örneğin kapsamı dışında bildirilmiştir. Çıkış parametresindeki değer `OutputAssembly` `FinalAssemblyName` öğede depolanır ve çıkış parametresindeki değer `BuildSucceeded` `BuildWorked` özelliğinde depolanır. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Görevler](../msbuild/msbuild-tasks.md)
