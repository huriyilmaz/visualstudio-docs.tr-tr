---
title: PropertyGroup öğesi (MSBuild) | Microsoft Docs
description: kullanıcı tanımlı özellik öğeleri kümesi içeren MSBuild propertygroup öğesi hakkında bilgi edinin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084889"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup öğesi (MSBuild)

Kullanıcı tanımlı [özellik](../msbuild/property-element-msbuild.md) öğeleri kümesi içerir. `Property`bir MSBuild projesinde kullanılan her öğe bir `PropertyGroup` öğesinin alt öğesi olmalıdır.

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
|Koşul|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Özellik](../msbuild/property-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Özellik değerini içeren Kullanıcı tanımlı özellik adı. Bir öğede sıfır veya daha fazla *özellik* öğesi olabilir `PropertyGroup` .|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, bir koşula bağlı olarak özelliklerin nasıl ayarlanacağını gösterir. Bu örnekte, özelliğinin değeri ise,, `CompileConfig` `DEBUG` `Optimization` `Obfuscate` ve `OutputPath` öğelerinin içindeki Özellikler `PropertyGroup` ayarlanır.

```xml
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >
    <Optimization>false</Optimization>
    <Obfuscate>false</Obfuscate>
    <OutputPath>$(OutputPath)\debug</OutputPath>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Project dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
