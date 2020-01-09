---
title: ItemMetadata öğesi (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 66c19dbd74176babbf9e26030a68a6095992b660
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589376"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata öğesi (MSBuild)
Öğe meta veri değerini içeren Kullanıcı tanımlı bir öğe meta veri anahtarı içerir. Bir öğe herhangi bir sayıda meta veri anahtar-değer çifti içerebilir.

 \<Proje > \<ItemGroup > \<öğesi >

## <a name="syntax"></a>Sözdizimi

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
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
|[Öğesi](../msbuild/item-element-msbuild.md)|Yapı işlemi için girişleri tanımlayan Kullanıcı tanımlı bir öğe.|

## <a name="text-value"></a>Metin değeri
 Metin değeri isteğe bağlıdır.

 Bu metin, metin veya XML olabilen öğe meta veri değerini belirtir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, öğe `CSFile``fr` değer ile `Culture` meta verilerin nasıl ekleneceğini gösterir.

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
