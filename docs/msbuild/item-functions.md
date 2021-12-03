---
title: Öğe Işlevleri | Microsoft Docs
description: görev ve hedeflerdeki MSBuild kodun, projedeki öğeler hakkında bilgi almak için nasıl öğe işlevleri çağırabileceğinizi öğrenin.
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
ms.openlocfilehash: 8150231e6ecf6c2b2f789da68fd4aae8d334854f
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133514512"
---
# <a name="item-functions"></a>Öğe işlevleri

görev ve hedeflerdeki kod, projedeki öğeler hakkında bilgi almak için (MSBuild 4,0 ve üzeri) öğe işlevlerini çağırabilir. Bu işlevler ayrı öğeler almayı basitleştirir ve öğeler aracılığıyla döngüden daha hızlıdır.

## <a name="string-item-functions"></a>Dize öğesi işlevleri

herhangi bir öğe değerinde çalıştırmak için .NET Framework dize yöntemleri ve özellikleri kullanabilirsiniz. <xref:System.String>Yöntemler için yöntem adını belirtin. <xref:System.String>Özellikler için, "get_" öğesinden sonra özellik adını belirtin.

Birden çok dizeye sahip öğeler için, dize yöntemi veya özelliği her bir dizede çalışır.

Aşağıdaki örnekte, bu dize öğesi işlevlerinin nasıl kullanılacağı gösterilmektedir.

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

## <a name="intrinsic-item-functions"></a>İç öğe işlevleri

Aşağıdaki tabloda, öğeler için kullanılabilen iç işlevler listelenmiştir.

:::moniker range="vs-2017"

|İşlev|Örnek|Description|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Öğelerin sayısını döndürür.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|`Path.DirectoryName`Her öğe için eşdeğerini döndürür.|
|`Distinct`|`@(MyItem->Distinct())`|Farklı değerlere sahip öğeleri döndürür `Include` . Meta veriler yoksayıldı. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Farklı değerlere sahip öğeleri döndürür `itemspec` . Meta veriler yoksayıldı. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`Reverse`|`@(MyItem->Reverse())`|Öğeleri ters sırada döndürür.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Herhangi bir `boolean` öğenin belirtilen meta veri adı ve değerine sahip olup olmadığını belirtmek için öğesini döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Meta verileri işaretsiz öğeleri döndürür. Yalnızca, `itemspec` tutulur.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Verilen meta veri adına sahip öğeleri döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Meta veri adına sahip meta verilerin değerlerini döndürür.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Verilen meta veri adı ve değerine sahip öğeleri döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|

:::moniker-end
:::moniker range=">=vs-2019"

|İşlev|Örnek|Description|
|--------------|-------------|-----------------|
|`Combine`|`@(MyItems->Combine('path'))`|Tüm giriş öğelerine eklenen belirli bir göreli yol ile yeni bir öğe kümesi döndürür.|
|`Count`|`@(MyItems->Count())`|Öğelerin sayısını döndürür.|
|`DirectoryName`|`@(MyItems->DirectoryName())`|`Path.DirectoryName`Her öğe için eşdeğerini döndürür.|
|`Distinct`|`@(MyItems->Distinct())`|Farklı değerlere sahip öğeleri döndürür `Include` . Meta veriler yoksayıldı. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`DistinctWithCase`|`@(MyItems->DistinctWithCase())`|Farklı değerlere sahip öğeleri döndürür `itemspec` . Meta veriler yoksayıldı. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`Exists`|`@(MyItems->Exists())`|Öğelerin bir kümesini diskte bulunanlara filtreler.|
|`GetPathsOfAllDirectoriesAbove`| `@(MyItems->GetPathsOfAllFilesAbove())`|Bir dizi öğe verildiğinde, tüm üst dizinleri temsil eden öğeleri döndürür. Hiçbir sipariş garanti edilmez.|
|`Reverse`|`@(MyItems->Reverse())`|Öğeleri ters sırada döndürür.|
|`AnyHaveMetadataValue`|`@(MyItems->AnyHaveMetadataValue("MetadataName", "MetadataValue"))` | Herhangi bir `boolean` öğenin belirtilen meta veri adı ve değerine sahip olup olmadığını belirtmek için öğesini döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır. |
|`ClearMetadata`|`@(MyItems->ClearMetadata())` |Meta verileri işaretsiz öğeleri döndürür. Yalnızca, `itemspec` tutulur.|
|`HasMetadata`|`@(MyItems->HasMetadata("MetadataName"))`|Verilen meta veri adına sahip öğeleri döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`Metadata`|`@(MyItems->Metadata("MetadataName"))`|Meta veri adına sahip meta verilerin değerlerini döndürür.|
|`WithMetadataValue`|`@(MyItems->WithMetadataValue("MetadataName", "MetadataValue"))`|Verilen meta veri adı ve değerine sahip öğeleri döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|

> [!NOTE]
> `Exists`, diğer bağlamlarda da kullanılabilir; örneğin [](msbuild-conditions.md), örneğin `Condition="Exists('path')"` veya [statik özellik işlevlerinde](property-functions.md)MSBuild koşullarda `$([System.IO.File]::Exists("path"))` .
:::moniker-end

Aşağıdaki örnek, iç öğe işlevlerinin nasıl kullanılacağını göstermektedir.

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

## <a name="msbuild-condition-functions"></a>MSBuild koşul işlevleri

Ve işlevleri `Exists` `HasTrailingSlash` öğe işlevleri değildir. Bu öznitelikler, özniteliğiyle birlikte kullanılmak üzere kullanılabilir `Condition` . [MSBuild koşullara](msbuild-conditions.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

Öğe listelerinde, öğe meta verilerinde filtreleme gibi işlemler gerçekleştirmek için özniteliklerini de kullanabilirsiniz; [öğeleri](../msbuild/msbuild-items.md)görüntüleyin.
