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
ms.openlocfilehash: 534a1abf01f3b1493018c4d7adb5161e1a02cf60
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077354"
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

|İşlev|Örnek|Açıklama|
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

## <a name="msbuild-condition-functions"></a>MSBuild işlevleri

ve işlevleri `Exists` `HasTrailingSlash` öğe işlevleri değildir. Bunlar özniteliğiyle `Condition` kullanılabilir. Bkz. [MSBuild koşulları.](msbuild-conditions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğeler](../msbuild/msbuild-items.md)
