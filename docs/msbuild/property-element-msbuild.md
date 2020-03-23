---
title: Özellik Öğesi (MSBuild) | Microsoft Dokümanlar
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
ms.openlocfilehash: e50a6dd66c2dca7fa4159c578ccd334ed1d26cae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632959"
---
# <a name="property-element-msbuild"></a>Özellik öğesi (MSBuild)

Kullanıcı tanımlı bir özellik adı ve değeri içerir. MSBuild projesinde kullanılan her özellik, bir `PropertyGroup` öğenin alt öğesi olarak belirtilmelidir.

 \<Proje \<> PropertyGroup>

## <a name="syntax"></a>Sözdizimi

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
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek durum. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Propertygroup](../msbuild/propertygroup-element-msbuild.md)|Özellikler için gruplandırma öğesi.|

## <a name="text-value"></a>Metin değeri

 Metin değeri isteğe bağlıdır.

 Bu metin özellik değerini belirtir ve XML içerebilir.

## <a name="remarks"></a>Açıklamalar

 Özellik adları yalnızca ASCII chars ile sınırlıdır. Özellik değerleri , " ve "`$(``)`arasına özellik adı yerleştirilerek projeye başvurulmaktadır. Örneğin, `$(builddir)\classes` `builddir` özellik değeri `build` *olsaydı\sınıflar oluşturmak*için çözer. Özellikler hakkında daha fazla bilgi için [MSBuild özelliklerine](../msbuild/msbuild-properties.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki kod, `Optimization` `Version` özelliğin `false` boş `DefaultVersion` `1.0` olup olmadığını ve özelliği ayarlar.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
