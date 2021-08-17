---
title: MSBuild Project dosya şeması başvurusu | Microsoft Docs
description: tüm MSBuild XML şeması öğelerini kullanılabilir öznitelikleri ve alt öğeleriyle birlikte listeleyerek bir tabloya bakın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 49e2b4196ce6ac08177aa9a4b3c7b484de8194c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068884"
---
# <a name="msbuild-project-file-schema-reference"></a>MSBuild proje dosyası şema başvurusu

tüm MSBuild XML şema öğelerinin kullanılabilir özniteliklerini ve alt öğelerini içeren bir tablo sağlar.

 MSBuild, derleme altyapısına ne tür derlemeyi ve nasıl oluşturulacağını bildirmek için proje dosyalarını kullanır. MSBuild proje dosyaları, MSBuild xml şemasına bağlı olan xml dosyalarıdır. Bu bölüm MSBuild için XML şema tanımı (*. xsd*) dosyasını belgeler.

MSBuild proje dosyasındaki şema bağlantısı Visual Studio 2017 ve sonrasında gerekli değildir. Varsa, ` http://schemas.microsoft.com/developer/msbuild/2003` Visual Studio sürümünden bağımsız olarak olmalıdır.

## <a name="msbuild-xml-schema-elements"></a>MSBuild XML şema öğeleri

 aşağıdaki tabloda, tüm MSBuild XML şema öğeleri alt öğeleri ve öznitelikleriyle birlikte listelenmektedir.

|Öğe|Alt öğeleri|Öznitelikler|
|-------------|--------------------|----------------|
|[Öğe seçin (MSBuild)](../msbuild/choose-element-msbuild.md)|Güvenmiyorsanız<br /><br /> Ne zaman|--|
|[İçeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)|--|Koşul<br /><br /> Project|
|[ImportGroup öğesi](../msbuild/importgroup-element.md)|İçeri Aktar|Koşul|
|[Öğe öğesi (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetadata*|Koşul<br /><br /> Exclude<br /><br /> Şunları Dahil Et:<br /><br /> Kaldır|
|[ItemDefinitionGroup öğesi (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Öğe*|Koşul|
|[ItemGroup öğesi (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Öğe*|Koşul|
|[ItemMetadata öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Öğe*|Koşul|
|[HataDurumunda öğe (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Koşul<br /><br /> ExecuteTargets|
|[Otherwise öğesi (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Seçin:<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output öğesi (MSBuild)](../msbuild/output-element-msbuild.md)|--|Koşul<br /><br /> ItemName<br /><br /> ÖzellikAdı<br /><br /> TaskParameter|
|[Parameter öğesi](../msbuild/parameter-element.md)|--|Çıktı<br /><br /> ParameterType<br /><br /> Gerekli|
|[ParameterGroup öğesi](../msbuild/parametergroup-element.md)|*Parametre*|--|
|[Project öğesi (MSBuild)](../msbuild/project-element-msbuild.md)|Seçin:<br /><br /> İçeri Aktar<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Hedef<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> 'Sının<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> özniteliði|
|[Projecısions öğesi (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Özellik öğesi (MSBuild)](../msbuild/property-element-msbuild.md)|--|Koşul|
|[PropertyGroup öğesi (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Özellik*|Koşul|
|[SDK öğesi (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Name<br /><br /> Sürüm|
|[Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Görev*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Koşul<br /><br /> Bağımlıdsonhedefleri<br /><br /> Girişler<br /><br /> "Pduperepteçıkışları<br /><br /> Name<br /><br /> Çıkışlar<br /><br /> Döndürülenler|
|[Hedefin görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md)|Çıktı|Koşul<br /><br /> ContinueOnError<br /><br /> *Parametre*|
|[UsingTask görev öğesi (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Veriler*|Değerlendir|
|[UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Görev|AssemblyFile & lt<br /><br /> AssemblyName<br /><br /> Koşul<br /><br /> TaskFactory<br /><br /> Silinecek|
|[Ne zaman öğesi (MSBuild)](../msbuild/when-element-msbuild.md)|Seçin:<br /><br /> ItemGroup<br /><br /> PropertyGroup|Koşul|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Koşullar](../msbuild/msbuild-conditions.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
