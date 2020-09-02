---
title: Öğe Işlevleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c94624aaea629c087b552ee46266a44f534888d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192903"
---
# <a name="item-functions"></a>Öğe İşlevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild 4,0 ' den başlayarak, görev ve hedeflerdeki kod, projedeki öğeler hakkında bilgi almak için öğe işlevlerini çağırabilir. Bu işlevler ayrı () öğeleri almayı basitleştirir ve öğeler aracılığıyla döngüden daha hızlıdır.  
  
## <a name="string-item-functions"></a>Dize öğesi Işlevleri  
 Herhangi bir öğe değerinde çalıştırmak için .NET Framework dize yöntemleri ve özellikleri kullanabilirsiniz. <xref:System.String>Yöntemler için yöntem adını belirtin. <xref:System.String>Özellikler için, "get_" öğesinden sonra özellik adını belirtin.  
  
 Birden çok dizeye sahip öğeler için, dize yöntemi veya özelliği her bir dizede çalışır.  
  
 Aşağıdaki örnekte, bu dize öğesi işlevlerinin nasıl kullanılacağı gösterilmektedir.  
  
```  
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
  
## <a name="intrinsic-item-functions"></a>İç öğe Işlevleri  
 Aşağıdaki tabloda, öğeler için kullanılabilen iç işlevler listelenmiştir.  
  
|İşlev|Örnek|Açıklama|  
|--------------|-------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Öğelerin sayısını döndürür.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|`Path.DirectoryName`Her öğe için eşdeğerini döndürür.|  
|`Distinct`|`@(MyItem->Distinct())`|Farklı değerlere sahip öğeleri döndürür `Include` . Meta veriler yoksayıldı. Karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Farklı değerlere sahip öğeleri döndürür `itemspec` . Meta veriler yoksayıldı. Karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`Reverse`|`@(MyItem->Reverse())`|Öğeleri ters sırada döndürür.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Herhangi bir `boolean` öğenin belirtilen meta veri adı ve değerine sahip olup olmadığını belirtmek için öğesini döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Meta verileri işaretsiz öğeleri döndürür. Yalnızca, `itemspec` tutulur.|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Verilen meta veri adına sahip öğeleri döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Meta veri adına sahip meta verilerin değerlerini döndürür.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Verilen meta veri adı ve değerine sahip öğeleri döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|  
  
 Aşağıdaki örnek, iç öğe işlevlerinin nasıl kullanılacağını göstermektedir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğeler](../msbuild/msbuild-items.md)
