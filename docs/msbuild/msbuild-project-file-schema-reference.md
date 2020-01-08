---
title: MSBuild proje dosyası şema başvurusu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: def9edb232a37bc58a56ffd1ec9a16bcb1b75092
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590325"
---
# <a name="msbuild-project-file-schema-reference"></a>MSBuild proje dosyası şema başvurusu
Tüm [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML şema öğelerinin kullanılabilir özniteliklerini ve alt öğelerini içeren bir tablo sağlar.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], derleme altyapısına ne tür derlemeyi ve nasıl oluşturulacağını bildirmek için proje dosyalarını kullanır. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyaları, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML şemasına bağlı olan XML dosyalarıdır. Bu bölüm [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]için XML şema tanımı ( *. xsd*) dosyasını belgeler.

## <a name="msbuild-xml-schema-elements"></a>MSBuild XML şema öğeleri
 Aşağıdaki tabloda, tüm [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML şema öğeleri alt öğeleri ve öznitelikleriyle birlikte listelenmektedir.

|Öğe|Alt öğeleri|{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}|
|-------------|--------------------|----------------|
|[Öğe seç (MSBuild)](../msbuild/choose-element-msbuild.md)|Güvenmiyorsanız<br /><br /> Microsoft|--|
|[İçeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)|--|Koşul<br /><br /> {1&gt;Proje (Project)&lt;1}|
|[ImportGroup öğesi](../msbuild/importgroup-element.md)|Al|Koşul|
|[Item öğesi (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetadata*|Koşul<br /><br /> Dışla<br /><br /> Şunları Dahil Et:<br /><br /> Kaldır|
|[ItemDefinitionGroup öğesi (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Öğesi*|Koşul|
|[ItemGroup öğesi (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Öğesi*|Koşul|
|[ItemMetadata öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Öğesi*|Koşul|
|[HataDurumunda öğesi (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Koşul<br /><br /> ExecuteTargets|
|[Otherwise öğesi (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Yerel koruma uygulamak isterseniz<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output öğesi (MSBuild)](../msbuild/output-element-msbuild.md)|--|Koşul<br /><br /> ItemName<br /><br /> ÖzellikAdı<br /><br /> TaskParameter|
|[Parameter öğesi](../msbuild/parameter-element.md)|--|Çıkış<br /><br /> ParameterType<br /><br /> Gerekli|
|[ParameterGroup Öğesi](../msbuild/parametergroup-element.md)|*Parametre*|--|
|[Proje öğesi (MSBuild)](../msbuild/project-element-msbuild.md)|Yerel koruma uygulamak isterseniz<br /><br /> Al<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Hedef<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> özniteliði|
|[Projecısions öğesi (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property öğesi (MSBuild)](../msbuild/property-element-msbuild.md)|--|Koşul|
|[PropertyGroup öğesi (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Özellik*|Koşul|
|[SDK öğesi (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Name<br /><br /> Sürüm|
|[Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Görev*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Koşul<br /><br /> Bağımlıdsonhedefleri<br /><br /> Girdiler<br /><br /> "Pduperepteçıkışları<br /><br /> Name<br /><br /> Çıktılar<br /><br /> {1&gt;&lt;1} döndürür|
|[Task öğesi (MSBuild)](../msbuild/task-element-msbuild.md)|Çıkış|Koşul<br /><br /> ContinueOnError<br /><br /> *Parametre*|
|[TaskBody öğesi (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Veri*|'i Değerlendirme|
|[UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile & lt<br /><br /> AssemblyName<br /><br /> Koşul<br /><br /> TaskFactory<br /><br /> TaskName|
|[Ne zaman öğesi (MSBuild)](../msbuild/when-element-msbuild.md)|Yerel koruma uygulamak isterseniz<br /><br /> ItemGroup<br /><br /> PropertyGroup|Koşul|

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Koşullar](../msbuild/msbuild-conditions.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
