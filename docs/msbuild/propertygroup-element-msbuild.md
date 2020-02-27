---
title: PropertyGroup öğesi (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b94cf266be81b81aca9c83fe8d29b9777ee9114b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632933"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup öğesi (MSBuild)

Kullanıcı tanımlı [özellik](../msbuild/property-element-msbuild.md) öğeleri kümesi içerir. MSBuild projesinde kullanılan her `Property` öğesi bir `PropertyGroup` öğesinin alt öğesi olmalıdır.

 \<Proje > \<PropertyGroup >

## <a name="syntax"></a>Sözdizimi

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
|[Özellik](../msbuild/property-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Özellik değerini içeren Kullanıcı tanımlı özellik adı. Bir `PropertyGroup` öğesinde sıfır veya daha fazla *özellik* öğesi olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Proje](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, bir koşula bağlı olarak özelliklerin nasıl ayarlanacağını gösterir. Bu örnekte, `CompileConfig` özelliğinin değeri `DEBUG`, `OutputPath` öğesinin içindeki `Optimization`, `Obfuscate`ve `PropertyGroup` özellikleri ayarlanır.

```xml
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >
    <Optimization>false</Optimization>
    <Obfuscate>false</Obfuscate>
    <OutputPath>$(OutputPath)\debug</OutputPath>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
