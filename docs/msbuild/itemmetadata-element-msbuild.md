---
title: ItemMetadata Öğesi (MSBuild) | Microsoft Docs
description: Meta veri MSBuild kullanıcı tanımlı öğe meta veri anahtarını içeren ItemMetadata öğesinin nasıl tanımlandığı hakkında bilgi öğrenin.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: aca05e3711d23e8346770fb45523f98c0c72da38
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143189"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata öğesi (MSBuild)

Öğe meta veri değerini içeren kullanıcı tanımlı bir öğe meta veri anahtarı içerir. Bir öğede herhangi bir sayıda meta veri anahtar-değer çifti olabilir.

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
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğe](../msbuild/item-element-msbuild.md)|Derleme işleminin girişlerini tanımlayan kullanıcı tanımlı bir öğe.|

## <a name="text-value"></a>Metin değeri

 Metin değeri isteğe bağlıdır.

 Bu metin, metin veya XML olan öğe meta veri değerini belirtir.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, değerine sahip `Culture` meta verilerin öğeye nasıl `fr` ekli olduğunu `CSFile` gösterir.

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Öğeler](../msbuild/msbuild-items.md)
