---
title: Özellik öğesi (MSBuild) | Microsoft Docs
description: bir propertygroup öğesinin alt öğesi olarak belirtilmesi gereken kullanıcı tanımlı bir özellik adı ve değeri içeren MSBuild özellik öğesi hakkında bilgi edinin.
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
ms.openlocfilehash: 4203d177c4d4289f26ba445538005951a11792887acc9ec16ef35e5398b6acad
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270424"
---
# <a name="property-element-msbuild"></a>Özellik öğesi (MSBuild)

Kullanıcı tanımlı özellik adı ve değeri içerir. bir MSBuild projesinde kullanılan her özellik, bir öğesinin alt öğesi olarak belirtilmelidir `PropertyGroup` .

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
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Özellikler için gruplandırma öğesi.|

## <a name="text-value"></a>Metin değeri

 Metin değeri isteğe bağlıdır.

 Bu metin, özellik değerini belirtir ve XML içerebilir.

## <a name="remarks"></a>Açıklamalar

 Özellik adları yalnızca ASCII karakterleri ile sınırlıdır. Özellik değerleri, " `$(` " ve "" arasında özellik adı girilerek projede başvurulur `)` . Örneğin, `$(builddir)\classes` *build\classes* olarak çözümleniyordu `builddir` `build` . özellikler hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="example"></a>Örnek

 Aşağıdaki kod, özelliği `Optimization` boş ise özelliğini `false` ve özelliğini `DefaultVersion` olarak ayarlar `1.0` `Version` .

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
- [Project dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
