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
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476929"
---
# <a name="project-element-msbuild"></a>Proje Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyasının gerekli kök öğesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
|    `DefaultTargets`    |                                                                                                                                                                                                                                                                                                 İsteğe bağlı öznitelik.<br /><br /> Hedef belirtilmemişse, varsayılan hedef veya hedefler, yapı giriş noktası olarak kullanılır. Birden çok hedef noktalı virgül (;) Ted.<br /><br /> `DefaultTargets` özniteliğinde veya [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] komut satırında hiçbir varsayılan hedef belirtilmemişse, [Içe aktarma](../msbuild/import-element-msbuild.md) öğeleri değerlendirildikten sonra motor proje dosyasındaki ilk hedefi yürütür.                                                                                                                                                                                                                                                                                                  |
|    `InitialTargets`    |                                                                                                                                                                                                                                                                                                                                                                                                                                             İsteğe bağlı öznitelik.<br /><br /> `DefaultTargets` özniteliğinde veya komut satırında belirtilen hedeflerden önce çalıştırılacak başlangıç hedefi veya hedefleri. Birden çok hedef noktalı virgül (;) Ted.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|     `ToolsVersion`     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             İsteğe bağlı öznitelik.<br /><br /> Araç kümesi MSBuild 'in sürümü, $ (MSBuildBinPath) ve $ (Msbuildaraçları yolu) değerlerini belirlemede kullanır.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TreatAsLocalProperty` | İsteğe bağlı öznitelik.<br /><br /> Genel olarak değerlendirilmeyecek Özellik adları. Bu öznitelik, belirli komut satırı özelliklerinin bir proje veya hedefler dosyasında ve sonraki tüm içeri aktarmalarda ayarlanan özellik değerlerini geçersiz kılmasını önler. Birden çok özellik noktalı virgül (;) Ted.<br /><br /> Normal olarak, genel özellikler proje veya hedefler dosyasında ayarlanan özellik değerlerini geçersiz kılar. Özellik `TreatAsLocalProperty` değerinde listeleniyorsa, genel özellik değeri bu dosyada ve sonraki tüm içeri aktarmalarda ayarlanan özellik değerlerini geçersiz kılmaz. Daha fazla bilgi için bkz. [nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları oluşturma](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Note:**  Genel özellikleri bir komut isteminde, **/Property** (veya **/p**) anahtarını kullanarak ayarlarsınız. Ayrıca, MSBuild görevinin `Properties` özniteliğini kullanarak, çok projeli bir derlemede alt projeler için genel özellikleri ayarlayabilir veya değiştirebilirsiniz. Daha fazla bilgi için bkz. [MSBuild görevi](../msbuild/msbuild-task.md). |
|        `Xmlns`         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Gerekli öznitelik (MSBuild 15. x ve önceki sürümlerde).<br /><br /> `xmlns` özniteliği `http://schemas.microsoft.com/developer/msbuild/2003`değerine sahip olmalıdır.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|['Yu](../msbuild/choose-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> , Değerlendirmek için bir `ItemGroup` öğe ve/veya `PropertyGroup` öğeleri kümesi seçmek üzere alt öğeleri değerlendirir.|  
|[İçeri Aktarma](../msbuild/import-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Proje dosyasının başka bir proje dosyasını içeri aktarmasını sağlar. Bir projede sıfır veya daha fazla öğe `Import` olabilir.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Ayrı öğeler için bir gruplandırma öğesi. Öğeler [Item](../msbuild/item-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla öğe `ItemGroup` olabilir.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyasında[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] olmayan bilgilerin kalıcı hale getirilmesi için bir yol sağlar. Bir projede sıfır veya bir `ProjectExtensions` öğe olabilir.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Ayrı özellikler için bir gruplandırma öğesi. Özellikler, [özellik](../msbuild/property-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla öğe `PropertyGroup` olabilir.|  
|[Hedef](../msbuild/target-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sırayla yürütülecek bir görev kümesi içerir. Görevler, [görev](../msbuild/task-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla öğe `Target` olabilir.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]görevleri kaydetmek için bir yol sağlar. Bir projede sıfır veya daha fazla öğe `UsingTask` olabilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
 Yok.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ilk  hangi hedefin oluşturulacağını belirtme](../msbuild/how-to-specify-which-target-to-build-first.md)  
 [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)   
 [Proje dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](msbuild.md)
