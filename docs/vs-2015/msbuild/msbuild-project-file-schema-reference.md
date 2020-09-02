---
title: MSBuild proje dosyası şema başvurusu | Microsoft Docs
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
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 847fa53acad63cec151222521ed8f85090c52080
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158860"
---
# <a name="msbuild-project-file-schema-reference"></a>MSBuild Proje Dosyası Şema Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tüm [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] XML şema öğelerinin kullanılabilir özniteliklerini ve alt öğelerini içeren bir tablo sağlar.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] derleme altyapısına ne tür derlemeyi ve nasıl oluşturulacağını bildirmek için proje dosyalarını kullanır. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje dosyaları, XML şemasına bağlı XML dosyalarıdır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Bu bölüm için XML şema tanımı (. xsd) dosyasını belgeler [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
## <a name="msbuild-xml-schema-elements"></a>MSBuild XML şema öğeleri  
 Aşağıdaki tabloda, tüm [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] XML şema öğeleri alt öğeleri ve öznitelikleriyle birlikte listelenmektedir.  
  
|Öğe|Alt Öğeler|Öznitelikler|  
|-------------|--------------------|----------------|  
|[Öğe Seç (MSBuild)](../msbuild/choose-element-msbuild.md)|Güvenmiyorsanız<br /><br /> Ne zaman|--|  
|[İçeri Aktarma Öğesi (MSBuild)](../msbuild/import-element-msbuild.md)|--|Koşul<br /><br /> Project|  
|[ImportGroup öğesi](../msbuild/importgroup-element.md)|İçeri Aktar|Koşul|  
|[Öğe Unsuru (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetadata*|Koşul<br /><br /> Exclude<br /><br /> Şunları Dahil Et:<br /><br /> Kaldır|  
|[ItemDefinitionGroup Öğesi (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Öğe*|Koşul|  
|[ItemGroup Öğesi (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Öğe*|Koşul|  
|[ItemMetadata Öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Öğe*|Koşul|  
|[OnError Öğesi (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Koşul<br /><br /> ExecuteTargets|  
|[Otherwise Öğesi (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Seçin:<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Çıktı Öğesi (MSBuild)](../msbuild/output-element-msbuild.md)|--|Koşul<br /><br /> ItemName<br /><br /> ÖzellikAdı<br /><br /> TaskParameter|  
|[Parameter öğesi](../msbuild/parameter-element.md)|--|Çıktı<br /><br /> ParameterType<br /><br /> Gerekli|  
|[ParameterGroup Öğesi](../msbuild/parametergroup-element.md)|*Parametre*|--|  
|[Proje Öğesi (MSBuild)](../msbuild/project-element-msbuild.md)|Seçin:<br /><br /> İçeri Aktar<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Hedef<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> özniteliði|  
|[ProjectExtensions Öğesi (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Özellik Öğesi (MSBuild)](../msbuild/property-element-msbuild.md)|--|Koşul|  
|[PropertyGroup Öğesi (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Özellik*|Koşul|  
|[Hedef Öğe (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Görev*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Koşul<br /><br /> Bağımlıdsonhedefleri<br /><br /> Girişler<br /><br /> "Pduperepteçıkışları<br /><br /> Name<br /><br /> Çıkışlar<br /><br /> Döndürülenler|  
|[Görev Öğesi (MSBuild)](../msbuild/task-element-msbuild.md)|Çıktı|Koşul<br /><br /> ContinueOnError<br /><br /> *Parametre*|  
|[TaskBody Öğesi (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Veriler*|Değerlendir|  
|[UsingTask Öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile & lt<br /><br /> AssemblyName<br /><br /> Koşul<br /><br /> TaskFactory<br /><br /> Silinecek|  
|[When Öğesi (MSBuild)](../msbuild/when-element-msbuild.md)|Seçin:<br /><br /> ItemGroup<br /><br /> PropertyGroup|Koşul|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Durumunda](../msbuild/msbuild-conditions.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)  
 [MSBUILD](msbuild.md)
