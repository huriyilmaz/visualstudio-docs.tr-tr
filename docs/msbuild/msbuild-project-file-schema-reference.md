---
title: MSBuild Proje Dosyası Şema Başvuru | Microsoft Dokümanlar
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
ms.openlocfilehash: 824a6f562638edb04854431c437289f2741c46d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263115"
---
# <a name="msbuild-project-file-schema-reference"></a>MSBuild proje dosyası şema başvurusu

Tüm MSBuild XML Şema öğelerinin kullanılabilir öznitelikleri ve alt öğeleriyle bir tablo sağlar.

 MSBuild, yapı motoruna ne inşa edilip nasıl inşa edilebildiğini öğretmek için proje dosyalarını kullanır. MSBuild proje dosyaları, MSBuild XML şemasına uyan XML dosyalarıdır. Bu bölüm, MSBuild için XML şema tanımını (*.xsd*) dosyasını belgeler.

Bir MSBuild proje dosyasındaki şema bağlantısı Visual Studio 2017 ve sonraki yıllarda gerekli değildir. Varsa, ne olursa ` http://schemas.microsoft.com/developer/msbuild/2003` olsun Visual Studio sürümü olmalıdır.

## <a name="msbuild-xml-schema-elements"></a>MSBuild XML şema elemanları

 Aşağıdaki tabloda, tüm MSBuild XML şema öğelerinin alt öğeleri ve öznitelikleri listeleneb.rıa yer ait.

|Öğe|Alt öğeleri|Öznitelikler|
|-------------|--------------------|----------------|
|[Öğeyi seçin (MSBuild)](../msbuild/choose-element-msbuild.md)|Aksi takdir -de<br /><br /> Tesis|--|
|[Alma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)|--|Koşul<br /><br /> Project|
|[ImportGroup öğesi](../msbuild/importgroup-element.md)|İçeri Aktarma|Koşul|
|[Öğe öğesi (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Koşul<br /><br /> Exclude<br /><br /> Şunları Dahil Et:<br /><br /> Kaldır|
|[ItemDefinitionGroup öğesi (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Öğe*|Koşul|
|[ItemGroup öğesi (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Öğe*|Koşul|
|[ItemMetaveri öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Öğe*|Koşul|
|[OnError öğesi (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Koşul<br /><br /> Executetargets|
|[Aksi takdirde eleman (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Seçin:<br /><br /> ıtemgroup<br /><br /> Propertygroup|--|
|[Çıkış elemanı (MSBuild)](../msbuild/output-element-msbuild.md)|--|Koşul<br /><br /> ItemName<br /><br /> ÖzellikAdı<br /><br /> Taskparameter|
|[Parametre elemanı](../msbuild/parameter-element.md)|--|Çıktı<br /><br /> ParametreTürü<br /><br /> Gerekli|
|[ParametreGrup öğesi](../msbuild/parametergroup-element.md)|*Parametre*|--|
|[Proje öğesi (MSBuild)](../msbuild/project-element-msbuild.md)|Seçin:<br /><br /> İçeri Aktarma<br /><br /> ıtemgroup<br /><br /> Proje Uzantıları<br /><br /> Propertygroup<br /><br /> Hedef<br /><br /> Usingtask|Defaulttargets<br /><br /> ınitialtargets<br /><br /> Toolsversion<br /><br /> TreatasLocalProperty<br /><br /> Xmlns|
|[ProjectExtensions öğesi (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Özellik öğesi (MSBuild)](../msbuild/property-element-msbuild.md)|--|Koşul|
|[PropertyGroup öğesi (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Özellik*|Koşul|
|[Sdk elemanı (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Adı<br /><br /> Sürüm|
|[Hedef eleman (MSBuild)](../msbuild/target-element-msbuild.md)|Onerror<br /><br /> *Görev*|Aftertargets<br /><br /> Beforetargets<br /><br /> Koşul<br /><br /> Bağımlı Hedefler<br /><br /> Girişler<br /><br /> KeepDuplicateOutputs<br /><br /> Adı<br /><br /> Çıkışlar<br /><br /> Döndürür|
|[Hedefin Görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md)|Çıktı|Koşul<br /><br /> ContinueOnError<br /><br /> *Parametre*|
|[UsingTask (MSBuild) görev öğesi](../msbuild/taskbody-element-msbuild.md)|*Veri*|Değerlendir|
|[UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParametreGrubu<br /><br /> Görev|Assemblyfile<br /><br /> Assemblyname<br /><br /> Koşul<br /><br /> Taskfactory<br /><br /> Görevadı|
|[Eleman (MSBuild)](../msbuild/when-element-msbuild.md)|Seçin:<br /><br /> ıtemgroup<br /><br /> Propertygroup|Koşul|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Koşullar](../msbuild/msbuild-conditions.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
