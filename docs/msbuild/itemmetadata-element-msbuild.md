---
title: ItemMetadata öğesi (MSBuild) | Microsoft Docs
description: Meta veri değerine sahip kullanıcı tanımlı bir öğe meta veri anahtarı içeren MSBuild ItemMetadata öğesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aba274068d8cba4f22526fdefac36d6c75f9f1e2
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903597"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata öğesi (MSBuild)

Öğe meta veri değerini içeren Kullanıcı tanımlı bir öğe meta veri anahtarı içerir. Bir öğe herhangi bir sayıda meta veri anahtar-değer çifti içerebilir.

 \<Project> \<ItemGroup>
 \<Item>

## <a name="syntax"></a>Syntax

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
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
|[Öğe](../msbuild/item-element-msbuild.md)|Yapı işlemi için girişleri tanımlayan Kullanıcı tanımlı bir öğe.|

## <a name="text-value"></a>Metin değeri

 Metin değeri isteğe bağlıdır.

 Bu metin, metin veya XML olabilen öğe meta veri değerini belirtir.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, `Culture` öğeye değerine sahip meta verilerin nasıl ekleneceğini gösterir `fr` `CSFile` .

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Öğeler](../msbuild/msbuild-items.md)
