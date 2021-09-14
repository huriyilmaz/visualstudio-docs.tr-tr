---
title: PropertyGroup Öğesi (MSBuild) | Microsoft Docs
description: Kullanıcı tanımlı MSBuild kümesi içeren PropertyGroup öğesi hakkında bilgi edinmek için bkz.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7ca05a0f96a159d354c09d9542327cfa73ff76e8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726854"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup öğesi (MSBuild)

Kullanıcı tanımlı Özellik öğeleri [kümesi](../msbuild/property-element-msbuild.md) içerir. MSBuild `Property` projesinde kullanılan her öğe bir öğenin alt öğesi `PropertyGroup` olması gerekir.

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Syntax

```xml
<PropertyGroup Condition="'String A' == 'String B'">
    <Property1>...</Property1>
    <Property2>...</Property2>
</PropertyGroup>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Koşul|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Özellik](../msbuild/property-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Özellik değerini içeren kullanıcı tanımlı özellik adı. Bir öğede sıfır veya *daha fazla* Özellik öğesi `PropertyGroup` olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Bir proje dosyasının gerekli MSBuild öğesi. |

## <a name="example"></a>Örnek

 Aşağıdaki kod örneğinde, özellikleri bir koşula göre ayarlama adımları ve ardından aşağıdaki kodlar yer ayaları. Bu örnekte, özelliğinin değeri `CompileConfig` `DEBUG` ise, `Optimization` öğesinin `Obfuscate` içindeki , ve özellikleri `OutputPath` `PropertyGroup` ayarlanır.

```xml
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >
    <Optimization>false</Optimization>
    <Obfuscate>false</Obfuscate>
    <OutputPath>$(OutputPath)\debug</OutputPath>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
