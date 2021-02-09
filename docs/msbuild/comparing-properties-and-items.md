---
title: Özellikleri ve öğeleri karşılaştırma | Microsoft Docs
description: MSBuild özelliklerinin ve öğelerinin görevlere bilgi iletmekte, koşulları değerlendirmenize ve proje dosyasının başvurbileceği değerleri nasıl depoleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 226b86d621de2faee5a71d9fdb3fea39f20b984e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888127"
---
# <a name="compare-properties-and-items"></a>Özellikleri ve öğeleri karşılaştırma

MSBuild özellikleri ve öğeleri, bilgileri görevlere geçirmek, koşulları değerlendirmek ve proje dosyası genelinde başvurulabilen değerleri depolamak için kullanılır.

- Özellikler ad-değer çiftleridir. Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

- Öğeler genellikle dosyaları temsil eden nesnelerdir. Öğe nesnelerinde ilişkili meta veri koleksiyonları olabilir. Meta veriler ad-değer çiftleridir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

## <a name="scalars-and-vectors"></a>Dolandırılabilen ve vektörlerini

MSBuild özellikleri yalnızca bir dize değeri olan ad-değer çiftleri olduğundan, genellikle *skaler* olarak tanımlanır. MSBuild öğe türleri öğe listeleri olduğundan, genellikle *vektör* olarak tanımlanır. Ancak, uygulamada Özellikler birden çok değeri temsil edebilir ve öğe türlerinde sıfır veya bir öğe olabilir.

### <a name="target-dependency-injection"></a>Hedef bağımlılığı ekleme

Özelliklerin birden çok değeri nasıl temsil ettiğini görmek için, oluşturulacak hedefler listesine bir hedef eklemek için ortak kullanım modelini göz önünde bulundurun. Bu liste genellikle, hedef adları noktalı virgülle ayırarak bir özellik değeri ile temsil edilir.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

`BuildDependsOn`Özelliği genellikle bir hedef özniteliğin bağımsız değişkeni olarak kullanılır `DependsOnTargets` , etkin bir şekilde bir öğe listesine dönüştürülüyor. Hedef eklemek veya hedef yürütme sırasını değiştirmek için bu özellik geçersiz kılınabilir. Örneğin,

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

değer vererek CustomBuild hedefini hedef listeye ekler `BuildDependsOn` `BeforeBuild;CoreBuild;AfterBuild;CustomBuild` .

MSBuild 4,0 ' den başlayarak hedef bağımlılığı ekleme kullanımdan kaldırılmıştır. `AfterTargets` `BeforeTargets` Bunun yerine ve özniteliklerini kullanın. Daha fazla bilgi için bkz. [hedef derleme sırası](../msbuild/target-build-order.md).

### <a name="conversions-between-strings-and-item-lists"></a>Dizeler ve öğe listeleri arasındaki dönüşümler

MSBuild, gerektiğinde öğe türlerine ve dize değerlerine dönüştürme yapar. Bir öğe listesinin nasıl bir dize değeri haline gelebileceklerini görmek için, bir MSBuild özelliğinin değeri olarak bir öğe türü kullanıldığında ne olacağını göz önünde bulundurun:

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

OutputDir öğe türü `Include` "KeyFiles;" değerine sahip bir özniteliğe sahip \\ Sertifikalar \\ ". MSBuild bu dizeyi iki öğe olarak ayrıştırır: KeyFiles \ ve Certificates \\ . OutputDir öğe türü OutputDirList özelliğinin değeri olarak kullanıldığında, MSBuild, öğe türünü noktalı virgülle ayrılmış "KeyFiles;" dizesine dönüştürür veya "düzleştirir" \\ Sertifikalar \\ ".

## <a name="properties-and-items-in-tasks"></a>Görevlerdeki Özellikler ve öğeler

Özellikler ve öğeler, MSBuild görevlerine giriş ve çıkış olarak kullanılır. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

Özellikler görevlere öznitelik olarak geçirilir. Görev içinde, bir MSBuild özelliği, değeri bir dizeye ve dizeden dönüştürülebileceği bir özellik türü ile temsil edilir. Desteklenen özellik türleri,,,,,, `bool` `char` `DateTime` `Decimal` `Double` `int` `string` ve işleyebileceği herhangi bir tür içerir <xref:System.Convert.ChangeType%2A> .

Öğeler görevlere nesneler olarak geçirilir <xref:Microsoft.Build.Framework.ITaskItem> . Görev içinde, <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> öğenin değerini temsil eder ve <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> meta verilerini alır.

Öğe türünün öğe listesi bir nesne dizisi olarak geçirilebilir `ITaskItem` . .NET Framework 3,5 ' den başlayarak, öğeler bir hedefteki öğe listesinden özniteliği kullanılarak kaldırılabilir `Remove` . Öğeler bir öğe listesinden kaldırılabildiğinden, öğe türünde sıfır öğe olması mümkündür. Bir öğeye bir öğe listesi geçirilirse, görevdeki kod bu olasılığa göz atın.

## <a name="property-and-item-evaluation-order"></a>Özellik ve öğe değerlendirme sırası

Bir yapılandırmanın değerlendirme aşamasında, içeri aktarılan dosyalar, göründükleri sırada yapıya dahil edilir. Özellikler ve öğeler üç geçişte aşağıdaki sırada tanımlanır:

- Özellikler, göründükleri sırada tanımlanır ve değiştirilir.

- Öğe tanımları, göründükleri sırada tanımlanır ve değiştirilir.

- Öğeler, göründükleri sırada tanımlanır ve değiştirilir.

Bir yapı yürütme aşamasında, hedefler içinde tanımlanan özellikler ve öğeler göründükleri sırada tek bir aşamada birlikte değerlendirilir.

Ancak, bu tam hikaye değildir. Bir özellik, öğe tanımı veya öğe tanımlandığında, değeri değerlendirilir. İfade değerlendirici değeri belirten dizeyi genişletir. Dize genişletmesi derleme aşamasına bağımlıdır. Daha ayrıntılı bir özellik ve öğe değerlendirme sırası aşağıda verilmiştir:

- Bir yapı değerlendirme aşamasında:

  - Özellikler, göründükleri sırada tanımlanır ve değiştirilir. Özellik işlevleri yürütülür. $ (PropertyName) biçimindeki özellik değerleri ifadeler içinde genişletilir. Özellik değeri genişletilen ifadeye ayarlanır.

  - Öğe tanımları, göründükleri sırada tanımlanır ve değiştirilir. Özellik işlevleri ifadelerde zaten genişletilmişti. Meta veri değerleri genişletilmiş ifadelere ayarlanır.

  - Öğe türleri, göründükleri sırada tanımlanır ve değiştirilir. @ (ItemType) formundaki öğe değerleri genişletilir. Öğe dönüştürmeleri de genişletilir. Özellik işlevleri ve değerleri ifadelerde zaten genişletilmişti. Öğe listesi ve meta veri değerleri genişletilmiş ifadelere ayarlanır.

- Bir yapı yürütme aşamasında:

  - Hedefler içinde tanımlanan özellikler ve öğeler göründükleri sırada birlikte değerlendirilir. Özellik işlevleri yürütülür ve özellik değerleri ifadeler içinde genişletilir. Öğe değerleri ve öğe dönüştürmeleri de genişletilir. Özellik değerleri, öğe türü değerleri ve meta veri değerleri genişletilmiş ifadelere ayarlanır.

### <a name="subtle-effects-of-the-evaluation-order"></a>Değerlendirme sırasının hafif etkileri

Bir yapılandırmanın değerlendirme aşamasında, özellik değerlendirmesi öğe değerlendirmesinden önce gelir. Bununla birlikte, özellikler öğe değerlerine bağlı olarak görünen değerlere sahip olabilir. Aşağıdaki betiği göz önünde bulundurun.

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

Ileti görevinin yürütülmesi şu iletiyi görüntüler:

```
KeyFileVersion: 1.0.0.3
```

Bunun nedeni değeri `KeyFileVersion` aslında " \@ (KeyFile-> '% (sürüm) ')" dizesidir. Özellik ilk tanımlandığında öğe ve öğe dönüştürmeleri genişletilmedi, bu nedenle `KeyFileVersion` özelliğe genişletilmemiş dizenin değeri atandı.

Yapı yürütme aşamasında Ileti görevini işlediğinde, MSBuild " \@ (keyfile-> '% (sürüm) ')" dizesini "1.0.0.3" yield olarak genişletir.

Özellik ve öğe grupları sırayla ters çevrilse de aynı iletinin göründüğünden emin olun.

İkinci bir örnek olarak, özellik ve öğe grupları hedefler içinde bulunduğunda neler olabileceğini göz önünde bulundurun:

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

Ileti görevi şu iletiyi görüntüler:

```
KeyFileVersion:
```

Bunun nedeni, oluşturma işlemi sırasında, hedeflerin içinde tanımlanan özellik ve öğe gruplarının aynı anda en alta doğru değerlendirilmesinden kaynaklanır. `KeyFileVersion`Tanımlandığında, `KeyFile` bilinmiyor. Bu nedenle, öğe dönüştürmesi boş bir dizeye genişletilir.

Bu durumda, özellik ve öğe gruplarının sırasını tersine çevirme özgün iletiyi geri yükler:

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

Değeri `KeyFileVersion` "1.0.0.3" olarak ayarlanır ve " \@ (KeyFile-> '% (sürüm) ')" olarak ayarlanmıştır. Ileti görevi şu iletiyi görüntüler:

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
