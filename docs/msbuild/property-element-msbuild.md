---
title: Property Öğesi (MSBuild) | Microsoft Docs
description: Bir PropertyGroup MSBuild alt öğesi olarak belirtilmelidir kullanıcı tanımlı özellik adı ve değeri içeren MSBuild Property öğesi hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 450ac3215b967aced23dcadf99e2f6a049c75cd9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100614"
---
# <a name="property-element-msbuild"></a>Özellik öğesi (MSBuild)

Kullanıcı tanımlı özellik adını ve değerini içerir. Bir projedeki MSBuild bir öğenin alt öğesi olarak `PropertyGroup` belirtilmelidir.

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Syntax

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Propertygroup](../msbuild/propertygroup-element-msbuild.md)|Özellikler için gruplama öğesi.|

## <a name="text-value"></a>Metin değeri

 Metin değeri isteğe bağlıdır.

 Bu metin özellik değerini belirtir ve XML içerebilir.

## <a name="remarks"></a>Açıklamalar

 Özellik adları yalnızca ASCII karakterlerle sınırlıdır. Özellik değerlerine projede, özellik adı " " ve `$(` " " arasına yerleştirerek `)` başvurabilirsiniz. Örneğin, `$(builddir)\classes` özelliği *değerine sahipse build\classes* `builddir` olarak çözümlemektedir. `build` Özellikler hakkında daha fazla bilgi için [bkz. MSBuild.](../msbuild/msbuild-properties.md).

## <a name="example"></a>Örnek

 Aşağıdaki kod özelliği `Optimization` olarak ayarlar ve özelliği `false` `DefaultVersion` `1.0` boşsa özelliğini olarak `Version` ayarlar.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
