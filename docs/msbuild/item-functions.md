---
title: Öğe Fonksiyonları | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633687"
---
# <a name="item-functions"></a>Öğe işlevleri

Görevlerdeki ve hedeflerdeki kod, projedeki öğeler hakkında bilgi almak için madde işlevlerini çağırabilir (MSBuild 4.0 ve sonraki durumlarda). Bu işlevler farklı öğeler almayı kolaylaştırır ve öğeler arasında döngü yapmaktan daha hızlıdır.

## <a name="string-item-functions"></a>Dize öğesi işlevleri

Herhangi bir madde değeri üzerinde çalışmak için .NET Framework'deki dize yöntemlerini ve özelliklerini kullanabilirsiniz. Yöntemler <xref:System.String> için yöntem adını belirtin. Özellikler <xref:System.String> için özellik adını "get_"den sonra belirtin.

Birden çok dize olan öğeler için dize yöntemi veya özelliği her dize üzerinde çalışır.

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

## <a name="intrinsic-item-functions"></a>Içsel madde fonksiyonları

Aşağıdaki tabloda öğeler için kullanılabilir içsel işlevleri listelenmektedir.

|İşlev|Örnek|Açıklama|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Öğelerin sayısını döndürür.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|Her madde `Path.DirectoryName` için eşdeğerini verir.|
|`Distinct`|`@(MyItem->Distinct())`|Farklı `Include` değerlere sahip öğeleri döndürür. Meta veriler yoksayılır. Karşılaştırma büyük/küçük harf duyarsız.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Farklı `itemspec` değerlere sahip öğeleri döndürür. Meta veriler yoksayılır. Karşılaştırma büyük/küçük harf duyarlıdır.|
|`Reverse`|`@(MyItem->Reverse())`|Maddeleri ters sırada döndürür.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Herhangi `boolean` bir öğenin verilen meta veri adı ve değerine sahip olup olmadığını belirtmek için a döndürür. Karşılaştırma büyük/küçük harf duyarsız.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Meta verileri temizlenmiş öğeleri döndürür. Sadece `itemspec` korunur.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Verilen meta veri adı olan öğeleri döndürür. Karşılaştırma büyük/küçük harf duyarsız.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Meta veri adı olan meta verilerin değerlerini döndürür.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Verilen meta veri adı ve değerine sahip öğeleri döndürür. Karşılaştırma büyük/küçük harf duyarsız.|

Aşağıdaki örnek, içsel madde işlevlerinin nasıl kullanılacağını gösterir.

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
