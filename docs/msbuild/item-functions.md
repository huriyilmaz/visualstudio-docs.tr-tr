---
title: Öğe İşlevleri | Microsoft Docs
description: Projedeki MSBuild almak için görevlerdeki ve hedeflerde yer alan kodun öğe işlevlerini nasıl çağırası hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 3f4685674ed963484111832df3c052a737527754
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133977451"
---
# <a name="item-functions"></a>Öğe işlevleri

Görev ve hedeflerde kod, projedeki öğeler hakkında bilgi almak için öğe işlevlerini çağırabilir (MSBuild 4.0 ve sonraki bir sonraki bir yıl içinde). Bu işlevler ayrı öğeleri alma sürecini basitleştirir ve öğelerde döngüye almaya göre daha hızlıdır.

## <a name="string-item-functions"></a>Dize öğesi işlevleri

Herhangi bir öğe değeri üzerinde çalıştırmak için .NET Framework dize yöntemlerini ve özelliklerini kullanabilirsiniz. Yöntemler <xref:System.String> için yöntem adını belirtin. Özellikler <xref:System.String> için özellik adını "get_" olarak belirtin.

Birden çok dizeye sahip öğeler için dize yöntemi veya özelliği her dizede çalışır.

Aşağıdaki örnek, bu dize öğesi işlevlerinin nasıl kullanılagelmektedir.

```xml
<ItemGroup>
    <theItem Include="andromeda;tadpole;cartwheel" />
</ItemGroup>

<Target Name = "go">
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />
    <Message Text="Length   @(theItem->get_Length())" />
    <Message Text="Chars    @(theItem->get_Chars(2))" />
</Target>

  <!--
  Output:
    IndexOf  3;-1;2
    Replace  andromeda;pinwheel;cartwheel
    Length   9;7;9
    Chars    d;d;r
  -->
```

## <a name="intrinsic-item-functions"></a>Iç öğe işlevleri

Aşağıdaki tabloda öğeler için kullanılabilen iç işlevler listelenmiştir.

:::moniker range="vs-2017"

|İşlev|Örnek|Description|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Öğelerin sayısını döndürür.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|Her öğe için `Path.DirectoryName` eşdeğerini döndürür.|
|`Distinct`|`@(MyItem->Distinct())`|Farklı değerlere sahip öğeleri `Include` döndürür. Meta veriler yoksayılır. Karşılaştırma büyük/büyük/büyük harfe duyarlı değildir.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Farklı değerlere sahip öğeleri `itemspec` döndürür. Meta veriler yoksayılır. Karşılaştırma büyük/büyük/büyük harfe duyarlıdır.|
|`Reverse`|`@(MyItem->Reverse())`|Öğeleri ters sırada döndürür.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Herhangi bir `boolean` öğenin verilen meta veri adına ve değerine sahip olup olmadığını belirtmek için bir döndürür. Karşılaştırma büyük/büyük/büyük harfe duyarlı değildir.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Meta verileri temiz olan öğeleri döndürür. Yalnızca `itemspec` korunur.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Verilen meta veri adına sahip öğeleri döndürür. Karşılaştırma büyük/büyük/büyük harfe duyarlı değildir.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Meta veri adına sahip meta verilerin değerlerini döndürür.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Verilen meta veri adına ve değerine sahip öğeleri döndürür. Karşılaştırma büyük/büyük/büyük harfe duyarlı değildir.|

:::moniker-end
:::moniker range=">=vs-2019"

|İşlev|Örnek|Description|
|--------------|-------------|-----------------|
|`Combine`|`@(MyItems->Combine('path'))`|Tüm giriş öğelerine belirli bir göreli yol ekli yeni bir öğe kümesi döndürür.|
|`Count`|`@(MyItems->Count())`|Öğelerin sayısını döndürür.|
|`DirectoryName`|`@(MyItems->DirectoryName())`|Her öğe için `Path.DirectoryName` eşdeğerini döndürür.|
|`Distinct`|`@(MyItems->Distinct())`|Farklı değerlere sahip öğeleri `Include` döndürür. Meta veriler yoksayılır. Karşılaştırma büyük/büyük/büyük harfe duyarlı değildir.|
|`DistinctWithCase`|`@(MyItems->DistinctWithCase())`|Farklı değerlere sahip öğeleri `itemspec` döndürür. Meta veriler yoksayılır. Karşılaştırma büyük/büyük/büyük harfe duyarlıdır.|
|`Exists`|`@(MyItems->Exists())`|Bir öğe kümesine, diskte gerçekten var olan öğeleri filtreler.|
|`GetPathsOfAllDirectoriesAbove`| `@(MyItems->GetPathsOfAllFilesAbove())`|Bir öğe kümesi verildi, tüm üst dizinleri temsil eden öğeleri döndürür. Hiçbir sipariş garanti edilemez.|
|`Reverse`|`@(MyItems->Reverse())`|Öğeleri ters sırada döndürür.|
|`AnyHaveMetadataValue`|`@(MyItems->AnyHaveMetadataValue("MetadataName", "MetadataValue"))` | Herhangi bir `boolean` öğenin verilen meta veri adına ve değerine sahip olup olmadığını belirtmek için bir döndürür. Karşılaştırma büyük/büyük/büyük harfe duyarlı değildir. |
|`ClearMetadata`|`@(MyItems->ClearMetadata())` |Meta verileri temiz olan öğeleri döndürür. Yalnızca `itemspec` korunur.|
|`HasMetadata`|`@(MyItems->HasMetadata("MetadataName"))`|Verilen meta veri adına sahip öğeleri döndürür. Karşılaştırma büyük/büyük/büyük harfe duyarlı değildir.|
|`Metadata`|`@(MyItems->Metadata("MetadataName"))`|Meta veri adına sahip meta verilerin değerlerini döndürür.|
|`WithMetadataValue`|`@(MyItems->WithMetadataValue("MetadataName", "MetadataValue"))`|Verilen meta veri adına ve değerine sahip öğeleri döndürür. Karşılaştırma büyük/büyük/büyük harfe duyarlı değildir.|

> [!NOTE]
> `Exists`diğer bağlamlarda da kullanılabilir; içinde [MSBuild ,](msbuild-conditions.md)örneğin ; veya Statik özellik `Condition="Exists('path')"` [işlevlerinde](property-functions.md), örneğin `$([System.IO.File]::Exists("path"))` .
:::moniker-end

Aşağıdaki örnek, iç öğe işlevlerinin nasıl kullanılagelmektedir.

```xml
<ItemGroup>
    <TheItem Include="first">
        <Plant>geranium</Plant>
    </TheItem>
    <TheItem Include="second">
        <Plant>algae</Plant>
    </TheItem>
    <TheItem Include="third">
        <Plant>geranium</Plant>
    </TheItem>
</ItemGroup>

<Target Name="go">
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />
    <Message Text=" " />
    <Message Text="Count:   @(theItem->Count())" />
    <Message Text="Reverse: @(theItem->Reverse())" />
</Target>

  <!--
  Output:
    MetaData:    geranium;algae;geranium
    HasMetadata: first;second;third
    WithMetadataValue: first;third

    Count:   3
    Reverse: third;second;first
  -->
```

## <a name="msbuild-condition-functions"></a>MSBuild koşulu işlevleri

İşlev `HasTrailingSlash` bir öğe işlevi değildir. özniteliğiyle birlikte `Condition` kullanılabilir. Bkz. [MSBuild koşulları.](msbuild-conditions.md)

## <a name="see-also"></a>Ayrıca bkz.

Öğe meta verilerini filtreleme gibi öğe listelerinde işlem gerçekleştirmek için öznitelikleri de kullanabilirsiniz; Bkz. [Öğeler.](../msbuild/msbuild-items.md)
