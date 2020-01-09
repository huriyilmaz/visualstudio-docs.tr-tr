---
title: Property öğesi (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99970bfbc955fe972d5e3c9a4e38ae6f57e0e0bf
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597431"
---
# <a name="property-element-msbuild"></a>Property öğesi (MSBuild)
Kullanıcı tanımlı özellik adı ve değeri içerir. Bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projesinde kullanılan her özellik, bir `PropertyGroup` öğesinin alt öğesi olarak belirtilmelidir.

 \<Proje > \<PropertyGroup >

## <a name="syntax"></a>Sözdizimi

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

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
 Özellik adları yalnızca ASCII karakterleri ile sınırlıdır. Özellik değerleri, "`$(`" ve "`)`" arasında özellik adı girilerek projede başvurulur. Örneğin, `builddir` özelliğinde `build`değeri varsa `$(builddir)\classes`, *build\classes*olarak çözümlenir. Özellikler hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="example"></a>Örnek
 Aşağıdaki kod, `Version` özelliği boşsa `Optimization` özelliğini `false` ve `DefaultVersion` özelliğini `1.0` olarak ayarlar.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
