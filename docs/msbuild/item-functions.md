---
title: Öğe Işlevleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af4fb872206611ea5eb1aa93b7aa759615b56e41
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633687"
---
# <a name="item-functions"></a>Öğe işlevleri

Görev ve hedeflerdeki kod, projedeki öğeler hakkında bilgi almak için (MSBuild 4,0 ve üzeri) öğe işlevlerini çağırabilir. Bu işlevler ayrı öğeler almayı basitleştirir ve öğeler aracılığıyla döngüden daha hızlıdır.

## <a name="string-item-functions"></a>Dize öğesi işlevleri

Herhangi bir öğe değerinde çalıştırmak için .NET Framework dize yöntemleri ve özellikleri kullanabilirsiniz. <xref:System.String> yöntemler için yöntem adını belirtin. <xref:System.String> özellikler için, "get_" sonra özellik adını belirtin.

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

|İşlev|Örnek|Açıklama|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Öğelerin sayısını döndürür.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|Her öğe için `Path.DirectoryName` eşdeğerini döndürür.|
|`Distinct`|`@(MyItem->Distinct())`|Farklı `Include` değerlerine sahip öğeleri döndürür. Meta veriler yoksayıldı. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Farklı `itemspec` değerlerine sahip öğeleri döndürür. Meta veriler yoksayıldı. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`Reverse`|`@(MyItem->Reverse())`|Öğeleri ters sırada döndürür.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Herhangi bir öğenin belirtilen meta veri adı ve değerine sahip olup olmadığını belirtmek için bir `boolean` döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Meta verileri işaretsiz öğeleri döndürür. Yalnızca `itemspec` korunur.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Verilen meta veri adına sahip öğeleri döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Meta veri adına sahip meta verilerin değerlerini döndürür.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Verilen meta veri adı ve değerine sahip öğeleri döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|

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

## <a name="see-also"></a>Ayrıca bkz.

- [Öğeler](../msbuild/msbuild-items.md)
