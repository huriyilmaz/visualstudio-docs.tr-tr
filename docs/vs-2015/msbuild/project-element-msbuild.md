---
title: Proje öğesi (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b11449626050c4da75b09f2d348a4b1b0190ec4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476929"
---
# <a name="project-element-msbuild"></a>Proje Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje dosyasının gerekli kök öğesi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
## <a name="syntax"></a>Syntax  
  
```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|       Öznitelik        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              Açıklama                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `DefaultTargets`    |                                                                                                                                                                                                                                                                                                 İsteğe bağlı öznitelik.<br /><br /> Hedef belirtilmemişse, varsayılan hedef veya hedefler, yapı giriş noktası olarak kullanılır. Birden çok hedef noktalı virgül (;) Ted.<br /><br /> `DefaultTargets`Öznitelikte veya komut satırında hiçbir varsayılan hedef belirtilmemişse [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , [içeri aktarma](../msbuild/import-element-msbuild.md) öğeleri değerlendirildikten sonra motor proje dosyasındaki ilk hedefi yürütür.                                                                                                                                                                                                                                                                                                  |
|    `InitialTargets`    |                                                                                                                                                                                                                                                                                                                                                                                                                                             İsteğe bağlı öznitelik.<br /><br /> Öznitelikte veya komut satırında belirtilen hedeflerden önce çalıştırılacak başlangıç hedefi veya hedefleri `DefaultTargets` . Birden çok hedef noktalı virgül (;) Ted.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|     `ToolsVersion`     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             İsteğe bağlı öznitelik.<br /><br /> Araç kümesi MSBuild 'in sürümü, $ (MSBuildBinPath) ve $ (Msbuildaraçları yolu) değerlerini belirlemede kullanır.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TreatAsLocalProperty` | İsteğe bağlı öznitelik.<br /><br /> Genel olarak değerlendirilmeyecek Özellik adları. Bu öznitelik, belirli komut satırı özelliklerinin bir proje veya hedefler dosyasında ve sonraki tüm içeri aktarmalarda ayarlanan özellik değerlerini geçersiz kılmasını önler. Birden çok özellik noktalı virgül (;) Ted.<br /><br /> Normal olarak, genel özellikler proje veya hedefler dosyasında ayarlanan özellik değerlerini geçersiz kılar. Özellik `TreatAsLocalProperty` değerde listeleniyorsa, genel özellik değeri bu dosyada ve sonraki tüm içeri aktarmalarda ayarlanan özellik değerlerini geçersiz kılmaz. Daha fazla bilgi için bkz. [nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları oluşturma](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Note:**  Genel özellikleri bir komut isteminde, **/Property** (veya **/p**) anahtarını kullanarak ayarlarsınız. Ayrıca, MSBuild görevinin özniteliğini kullanarak çok projeli bir derlemede alt projeler için genel özellikler ayarlayabilir veya değiştirebilirsiniz `Properties` . Daha fazla bilgi için bkz. [MSBuild görevi](../msbuild/msbuild-task.md). |
|        `Xmlns`         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Gerekli öznitelik (MSBuild 15. x ve önceki sürümlerde).<br /><br /> `xmlns`Özniteliğinin değeri olmalıdır `http://schemas.microsoft.com/developer/msbuild/2003` .                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Seçin:](../msbuild/choose-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> , `ItemGroup` Değerlendirilecek öğe ve/veya öğe kümesi seçmek için alt öğeleri değerlendirir `PropertyGroup` .|  
|[İçeri Aktar](../msbuild/import-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Proje dosyasının başka bir proje dosyasını içeri aktarmasını sağlar. Bir projede sıfır veya daha fazla `Import` öğe olabilir.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Ayrı öğeler için bir gruplandırma öğesi. Öğeler [Item](../msbuild/item-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla `ItemGroup` öğe olabilir.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> , [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Bir proje dosyasında bilgilerin kalıcı hale getirilmesi için bir yol sağlar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Bir projede sıfır veya bir `ProjectExtensions` öğe olabilir.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Ayrı özellikler için bir gruplandırma öğesi. Özellikler, [özellik](../msbuild/property-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla `PropertyGroup` öğe olabilir.|  
|[Hedef](../msbuild/target-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Sıralı olarak yürütülmesi için bir görevler kümesi içerir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Görevler, [görev](../msbuild/task-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla `Target` öğe olabilir.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> İçindeki görevleri kaydetmek için bir yol sağlar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Bir projede sıfır veya daha fazla `UsingTask` öğe olabilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
 Yok.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)   
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBUILD](msbuild.md)
