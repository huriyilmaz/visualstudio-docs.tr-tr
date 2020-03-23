---
title: Özellikleri ve Öğeleri Karşılaştırma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a86365ffe839b45fcd09862040fb88f0d4148bc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634415"
---
# <a name="compare-properties-and-items"></a>Özellikleri ve öğeleri karşılaştırma

MSBuild özellikleri ve öğelerinin her ikisi de bilgileri görevlere aktarmak, koşulları değerlendirmek ve proje dosyası boyunca başvurulabilen değerleri depolamak için kullanılır.

- Özellikler ad değeri çiftleridir. Daha fazla bilgi için [MSBuild özelliklerine](../msbuild/msbuild-properties.md)bakın.

- Öğeler genellikle dosyaları temsil eden nesnelerdir. Öğe nesneleri ilişkili meta veri koleksiyonları olabilir. Meta veriler ad değeri çiftleridir. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.

## <a name="scalars-and-vectors"></a>Skaler ve vektörler

MSBuild özellikleri tek bir dize değerine sahip ad değeri çiftleri olduğundan, genellikle *skaler*olarak tanımlanırlar. MSBuild madde türleri öğelerin listeleri olduğundan, genellikle *vektör*olarak tanımlanır. Ancak, uygulamada, özellikler birden çok değeri temsil edebilir ve madde türleri sıfır veya bir öğeye sahip olabilir.

### <a name="target-dependency-injection"></a>Hedef bağımlılık enjeksiyonu

Özelliklerin birden çok değeri nasıl temsil edebileceğini görmek için, oluşturulacak hedefler listesine hedef eklemek için ortak bir kullanım deseni düşünün. Bu liste genellikle bir özellik değeri ile temsil edilir ve hedef adlar yarı iki nokta üst üste ayrılmıştır.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Özellik `BuildDependsOn` genellikle bir hedef `DependsOnTargets` özniteliğibağımsız değişkeni olarak kullanılır ve etkili bir öğe listesine dönüştürür. Bu özellik, hedef eklemek veya hedef yürütme düzenini değiştirmek için geçersiz kılınabilir. Örneğin,

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

Değer `BuildDependsOn` `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`vererek CustomBuild hedefini hedef listesine ekler.

MSBuild 4.0 ile başlayarak, hedef bağımlılık enjeksiyonu azalır. Bunun `AfterTargets` yerine `BeforeTargets` ve öznitelikleri kullanın. Daha fazla bilgi için Bkz. [Hedef oluşturma sırası.](../msbuild/target-build-order.md)

### <a name="conversions-between-strings-and-item-lists"></a>Dizeleri ve madde listeleri arasında dönüşümler

MSBuild, gerektiğinde madde türlerine ve dize değerlerine dönüşümler gerçekleştirir. Madde listesinin nasıl bir dize değerine dönüşebileceğini görmek için, bir öğe türü MSBuild özelliğinin değeri olarak kullanıldığında neler olacağını göz önünde bulundurun:

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

Madde türü OutputDir `Include` değeri "KeyFiles;\\ Sertifikalar\\". MSBuild bu dizeyi iki öğeye ayrılır:\\KeyFiles\ ve Sertifikalar. Öğe türü OutputDir OutputDirList özelliğinin değeri olarak kullanıldığında, MSBuild öğe türünü yarı sütunlu ayrılmış dize "KeyFiles;\\ Sertifikalar\\".

## <a name="properties-and-items-in-tasks"></a>Görevlerdeki özellikler ve öğeler

Özellikler ve öğeler, MSBuild görevlerine giriş ve çıktı olarak kullanılır. Daha fazla bilgi için [Görevler'e](../msbuild/msbuild-tasks.md)bakın.

Özellikler öznitelik olarak görevlere geçirilir. Görev içinde, bir MSBuild özelliği değeri bir dize dönüştürülebilir ve bu özellik türü tarafından temsil edilir. Desteklenen özellik türleri, `bool` `char`, `DateTime` `Decimal`, `Double` `int`, `string`, , <xref:System.Convert.ChangeType%2A> , ve işleyebilir herhangi bir tür içerir.

Öğeler görevlere nesne <xref:Microsoft.Build.Framework.ITaskItem> olarak aktarılır. Görev içinde, <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> öğenin değerini temsil <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> eder ve meta verilerini alır.

Bir öğe türünün madde listesi bir `ITaskItem` nesne dizisi olarak geçirilebilir. .NET Framework 3.5 ile başlayarak, öğeler öznitelik kullanılarak hedefteki `Remove` madde listesinden kaldırılabilir. Öğeler madde listesinden kaldırılabildiği için, madde türünün sıfır öğesi olması mümkündür. Bir madde listesi bir göreve aktarılırsa, görevdeki kod bu olasılığı denetlemelidir.

## <a name="property-and-item-evaluation-order"></a>Özellik ve madde değerlendirme emri

Yapının değerlendirme aşamasında, alınan dosyalar göründükleri sırada yapıya dahil edilir. Özellikler ve öğeler aşağıdaki sırayla üç geçişte tanımlanır:

- Özellikler göründükleri sırada tanımlanır ve değiştirilir.

- Madde tanımları, göründükleri sırada tanımlanır ve değiştirilir.

- Öğeler göründükleri sırada tanımlanır ve değiştirilir.

Yapının yürütme aşamasında, hedefler içinde tanımlanan özellikler ve öğeler göründükleri sırada tek bir aşamada birlikte değerlendirilir.

Ancak, bu tam hikaye değildir. Bir özellik, madde tanımı veya madde tanımlandığında, değeri değerlendirilir. İfade değerlendiricisi, değeri belirten dizeyi genişletir. Dize genişletme yapı aşamasına bağlıdır. Aşağıda daha ayrıntılı bir özellik ve madde değerlendirme sırası ve

- Bir yapının değerlendirme aşamasında:

  - Özellikler göründükleri sırada tanımlanır ve değiştirilir. Özellik işlevleri yürütülür. $(PropertyName) şeklindeki özellik değerleri ifadeler içinde genişletilir. Özellik değeri genişletilmiş ifadeye ayarlanır.

  - Madde tanımları, göründükleri sırada tanımlanır ve değiştirilir. Özellik işlevleri zaten ifadeler içinde genişletildi. Meta veri değerleri genişletilmiş ifadelere ayarlanır.

  - Madde türleri göründükleri sırada tanımlanır ve değiştirilir. @(ItemType) şeklindeki öğe değerleri genişletilir. Öğe dönüşümleri de genişletilir. Özellik işlevleri ve değerleri zaten ifadeler içinde genişletildi. Madde listesi ve meta veri değerleri genişletilmiş ifadelere ayarlanır.

- Yapının yürütme aşamasında:

  - Hedefler içinde tanımlanan özellikler ve öğeler göründükleri sırada birlikte değerlendirilir. Özellik işlevleri yürütülür ve özellik değerleri ifadeler içinde genişletilir. Madde değerleri ve madde dönüşümleri de genişletilir. Özellik değerleri, madde türü değerleri ve meta veri değerleri genişletilmiş ifadelere ayarlanır.

### <a name="subtle-effects-of-the-evaluation-order"></a>Değerlendirme sırasının ince etkileri

Bir yapının değerlendirme aşamasında, özellik değerlendirmesi madde değerlendirmesinden önce gelir. Bununla birlikte, özellikleri madde değerlerine bağlı görünen değerlere sahip olabilir. Aşağıdaki komut dosyasını göz önünde bulundurun.

```xml
<ItemGroup>
    <KeyFile Include="KeyFile.cs">
        <Version>1.0.0.3</Version>
    </KeyFile>
</ItemGroup>
<PropertyGroup>
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
</PropertyGroup>
<Target Name="AfterBuild">
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

İleti görevini yürütme, şu iletiyi görüntüler:

```
KeyFileVersion: 1.0.0.3
```

Bunun nedeni, değerin aslında `KeyFileVersion` "\@(KeyFile->'%(Version)')"dizesi olmasıdır. Öğe ve madde dönüşümleri özellik ilk tanımlandığında genişletilmedi, bu nedenle `KeyFileVersion` özellik genişletilmemiş dize değeri atandı.

Yapının yürütme aşamasında, İleti görevini işlediği nde, MSBuild "\@(KeyFile->'%(Version)') dizesini "1.0.0.3" olarak genişletir.

Özellik ve madde grupları sırayla tersine çevrilse bile aynı iletinin görüneceğine dikkat edin.

İkinci bir örnek olarak, özellik ve madde grupları hedefler içinde bulunduğunda neler olabileceğini göz önünde bulundurun:

```xml
<Target Name="AfterBuild">
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

İleti görevi bu iletiyi görüntüler:

```
KeyFileVersion:
```

Bunun nedeni, yapının yürütme aşamasında, hedefler içinde tanımlanan özellik ve madde gruplarının aynı anda yukarıdan aşağıya doğru değerlendirilmesidir. Ne `KeyFileVersion` zaman `KeyFile` tanımlanır, bilinmemektedir. Bu nedenle, öğe dönüştürme boş bir dize genişletir.

Bu durumda, özellik ve öğe gruplarının sırasını tersine çevirmek özgün iletiyi geri yükler:

```xml
<Target Name="AfterBuild">
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Değeri `KeyFileVersion` "1.0.0.3" olarak ayarlanır ve "(KeyFile->'%(Version)')")\@olarak ayarlanır. İleti görevi bu iletiyi görüntüler:

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
