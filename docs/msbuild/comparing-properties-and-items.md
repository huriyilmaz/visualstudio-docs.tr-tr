---
title: Özellikler ve Öğeler karşılaştırması | Microsoft Docs
description: Özellikleri ve MSBuild bilgileri görevlere nasıl iletir, koşulları değerlendirir ve proje dosyasının başvurabilirsiniz değerlerini depolamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e1348b4bd342e42f01fe6751d8ebdf6bae900b9789e9f2ebb3df4aaae89fa741
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443795"
---
# <a name="compare-properties-and-items"></a>Özellikleri ve öğeleri karşılaştırma

MSBuild özellikleri ve öğelerinin her ikisi de görevlere bilgi geçiş yapmak, koşulları değerlendirmek ve proje dosyası boyunca başvurulan değerleri depolamak için kullanılır.

- Özellikler ad-değer çiftleridir. Daha fazla bilgi için [bkz. MSBuild .](../msbuild/msbuild-properties.md)

- Öğeler genellikle dosyaları temsil eden nesnelerdir. Öğe nesnelerinin ilişkili meta veri koleksiyonları olabilir. Meta veriler ad-değer çiftleridir. Daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md)

## <a name="scalars-and-vectors"></a>Skaler ve vektörler

Bu MSBuild yalnızca bir dize değerine sahip olan ad-değer çiftleri olduğundan, bunlar genellikle *skaler olarak açıklanmıştır.* Bu MSBuild türleri öğe listesi olduğundan, bunlar genellikle vektör olarak *açıklanmıştır.* Ancak, pratikte özellikler birden çok değeri temsil eder ve öğe türleri sıfır veya bir öğeye sahip olabilir.

### <a name="target-dependency-injection"></a>Hedef bağımlılık ekleme

Özelliklerin birden çok değeri nasıl temsil saya olduğunu görmek için, bir hedef listesine bir hedef eklemek için ortak bir kullanım desenini göz önünde bulundurabilirsiniz. Bu liste genellikle noktalı virgülle ayrılmış hedef adlarla bir özellik değeriyle temsil edilen bir listedir.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

özelliği `BuildDependsOn` genellikle bir hedef özniteliğin bağımsız değişkeni olarak kullanılır ve bunu bir öğe listesine etkili bir şekilde `DependsOnTargets` dönüştürür. Bu özellik, hedef eklemek veya hedef yürütme sırası değiştirmek için geçersiz kılınabilir. Örneğin,

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

CustomBuild hedefini hedef listesine ekler ve değerini `BuildDependsOn` `BeforeBuild;CoreBuild;AfterBuild;CustomBuild` verir.

4.0 MSBuild başlayarak, hedef bağımlılık ekleme kullanım dışıdır. Bunun yerine `AfterTargets` ve `BeforeTargets` özniteliklerini kullanın. Daha fazla bilgi için [bkz. Hedef derleme sırası.](../msbuild/target-build-order.md)

### <a name="conversions-between-strings-and-item-lists"></a>Dizeler ve öğe listeleri arasındaki dönüştürmeler

MSBuild öğe türlerine ve dize değerlerine dönüştürmeleri gereken şekilde gerçekleştirir. Bir öğe listesinin dize değerine nasıl dönüşe olduğunu görmek için, bir öğe türü bir öğe türü MSBuild düşünün:

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

OutputDir öğe türünün `Include` "KeyFiles \\ ; \\Sertifikalar". MSBuild dizeyi iki öğeye ayrıştırıyor: KeyFiles\ ve Certificates \\ . OutputDirList özelliğinin değeri olarak OutputDir öğe türü kullanılırsa, MSBuild türü "KeyFiles" noktalı virgülle ayrılmış dizeye dönüştürür veya \\ "düzler". \\Sertifikalar".

## <a name="properties-and-items-in-tasks"></a>Görevlerdeki özellikler ve öğeler

Özellikler ve öğeler, görevleri gerçekleştirmek için giriş ve MSBuild kullanılır. Daha fazla bilgi için bkz. [Görevler.](../msbuild/msbuild-tasks.md)

Özellikler, görevlere öznitelik olarak geçirildi. Görev içinde, MSBuild değeri dizeye ve dizeden dönüştürülen bir özellik türüyle temsil edilen bir özellik türü. Desteklenen özellik türleri arasında `bool` , , , , , , , ve `char` `DateTime` `Decimal` `Double` `int` `string` işlebilir herhangi bir <xref:System.Convert.ChangeType%2A> tür yer almaktadır.

Öğeler görevlere nesne olarak <xref:Microsoft.Build.Framework.ITaskItem> geçirildi. Görev içinde, <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> öğenin değerini temsil eder <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> ve meta verilerini verir.

Bir öğe türünün öğe listesi bir nesne dizisi olarak `ITaskItem` geçirebilirsiniz. 3.NET Framework 3.5'den itibaren, öğeleri özniteliği kullanılarak hedef öğe listesinden `Remove` kaldırılabilir. Öğeler bir öğe listesinden kaldırılalana kadar, bir öğe türünün sıfır öğeye sahip olması mümkündür. Bir öğe listesi bir göreve geçirilse, görev kodu bu olasılığı denetlemeli.

## <a name="property-and-item-evaluation-order"></a>Özellik ve öğe değerlendirme sırası

Derlemenin değerlendirme aşamasında, içe aktarılan dosyalar, görünme sırasına göre derlemeye dahil olur. Özellikler ve öğeler üç geçişte aşağıdaki sırayla tanımlanır:

- Özellikler, görünme sırasına göre tanımlanır ve değiştirilir.

- Öğe tanımları, görünme sırasına göre tanımlanır ve değiştirilir.

- Öğeler, görünme sırasına göre tanımlanır ve değiştirilir.

Bir derlemenin yürütme aşamasında, hedefler içinde tanımlanan özellikler ve öğeler, tek bir aşamada, bunların görünme sırasına göre birlikte değerlendirilir.

Ancak bu tam bir hikaye değildir. Bir özellik, öğe tanımı veya öğe tanımlandığı zaman, değeri değerlendirilir. İfade değerlendiricisi, değeri belirten dizeyi genişlettir. Dize genişletmesi derleme aşamasına bağlıdır. Daha ayrıntılı bir özellik ve öğe değerlendirme sırası şu şekildedir:

- Derlemenin değerlendirme aşamasında:

  - Özellikler, görünme sırasına göre tanımlanır ve değiştirilir. Özellik işlevleri yürütülür. $(PropertyName) formundaki özellik değerleri ifadelerin içinde genişletilir. Özellik değeri genişletilmiş ifadeye ayarlanır.

  - Öğe tanımları, görünme sırasına göre tanımlanır ve değiştirilir. Özellik işlevleri zaten ifadelerin içinde genişletildi. Meta veri değerleri genişletilmiş ifadelere ayarlanır.

  - Öğe türleri, görünme sırasına göre tanımlanır ve değiştirilir. @(ItemType) formundaki öğe değerleri genişletilir. Öğe dönüştürmeleri de genişletilir. Özellik işlevleri ve değerleri zaten ifadelerin içinde genişletildi. Öğe listesi ve meta veri değerleri genişletilmiş ifadelere ayarlanır.

- Derlemenin yürütme aşamasında:

  - Hedefler içinde tanımlanan özellikler ve öğeler, görünme sırasına göre birlikte değerlendirilir. Özellik işlevleri yürütülür ve özellik değerleri ifadelerin içinde genişletilir. Öğe değerleri ve öğe dönüştürmeleri de genişletilir. Özellik değerleri, öğe türü değerleri ve meta veri değerleri genişletilmiş ifadelere ayarlanır.

### <a name="subtle-effects-of-the-evaluation-order"></a>Değerlendirme siparişinin hafif etkileri

Derlemenin değerlendirme aşamasında özellik değerlendirmesi öğe değerlendirmeden önce olur. Bununla birlikte, özellikler öğe değerlerine bağlı olarak görünen değerlere sahip olabilir. Aşağıdaki betiği göz önünde bulundurarak.

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

İleti görevinin yürütülmesi şu iletiyi görüntüler:

```
KeyFileVersion: 1.0.0.3
```

Bunun nedeni, değerinin aslında `KeyFileVersion` " \@ (KeyFile->'%(Sürüm)')" dizesidir. Özellik ilk tanımlandığı zaman öğe ve öğe dönüştürmeleri genişletilmemiştir, bu nedenle özelliğine genişletilmemiş `KeyFileVersion` dizenin değeri atanmıştır.

Derlemenin yürütme aşaması sırasında, MSBuild " \@ (KeyFile->'%(Sürüm)')" dizesini genişletarak "1.0.0.3" döndürür.

Özellik ve öğe grupları sırasıyla tersine çevrilse bile aynı iletinin görüntüye sahip olduğunu unutmayın.

İkinci bir örnek olarak, özellik ve öğe grupları hedeflerde yer alıyorsa neler olacağını göz önünde bulundurabilirsiniz:

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

İleti görevi şu iletiyi görüntüler:

```
KeyFileVersion:
```

Bunun nedeni, derlemenin yürütme aşamasında, hedeflerde tanımlanan özellik ve öğe gruplarının aynı anda en üstten aşağıya doğru değerlendirilmesidir. tanımlandığı `KeyFileVersion` zaman `KeyFile` bilinmiyor. Bu nedenle, öğe dönüştürmesi boş bir dizeye genişler.

Bu durumda, özellik ve öğe gruplarının sırası ters çevrilerek özgün ileti geri yüklemesi iletiyi geri alır:

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

değeri `KeyFileVersion` "1.0.0.3" olarak ayarlanır ve " \@ (KeyFile->'%(Version)')" olarak ayarlanmaz. İleti görevi şu iletiyi görüntüler:

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
