---
title: MSBuild Toplu işleme | Microsoft Docs
description: öğe listelerini, öğe meta verilerine bağlı olarak farklı kategorilere veya toplu işlerle MSBuild ayırır ve her batch ile bir kez hedef veya görev çalıştırır.
ms.custom: SEO-VS-2020
ms.date: 06/09/2020
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b9b018871c95cf87fbac226ed768b51bdc69398d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068965"
---
# <a name="msbuild-batching"></a>MSBuild toplu işleme

MSBuild öğe listelerini, öğe meta verilerine göre farklı kategorilere veya toplu işlemlere böler ve her batch ile bir kez bir hedef veya görev çalıştırır.

## <a name="task-batching"></a>Görev toplu işleme

Görev toplu işleme, öğe listelerini farklı toplu işlemlere bölmek ve bu toplu işlerin her birini ayrı bir göreve geçirmek için bir yol sağlayarak Proje dosyalarınızı basitleştirmenize olanak tanır. Bu, bir proje dosyasının, birkaç kez çalıştırılabilse de, yalnızca görevin ve özniteliklerinin bir kez bildirilmesine ihtiyaç duyacağı anlamına gelir.

görev özniteliklerinden birindeki gösterimi kullanarak bir görevle toplu işleme gerçekleştirmesini MSBuild istediğinizi belirtirsiniz `%(ItemMetaDataName)` . Aşağıdaki örnek, öğe `Example` listesini `Color` öğe meta veri değerine göre toplu işlemlere böler ve toplu işlerin her birini `MyTask` göreve ayrı geçirir.

> [!NOTE]
> Görev özniteliklerinin başka bir yerinde öğe listesine başvurmayın veya meta veri adı belirsiz olabilir, toplu işleme için kullanılacak öğe meta verileri değerini tamamen nitelemek için%(<ItemCollection. ItemMetaDataName>) gösterimini kullanabilirsiniz.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Daha özel toplu işlem örnekleri için bkz. [görev toplu işleme Içindeki öğe meta verileri](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Hedef toplu işleme

MSBuild, hedefin giriş ve çıkışları hedefi çalıştırmadan önce güncel olup olmadığını denetler. Hem giriş hem de çıkış güncel olursa hedef atlanır. bir hedefin içindeki bir görev toplu işlem kullanıyorsa, MSBuild her öğe için giriş ve çıktıların güncel olup olmadığını belirlemesi gerekir. Aksi takdirde, hedef her vurışında yürütülür.

Aşağıdaki örnek, `Target` gösterimiyle bir özniteliği içeren bir öğesini gösterir `Outputs` `%(ItemMetadataName)` . MSBuild öğe listesini, `Example` öğe meta verileri temelinde toplu işlemlere böler `Color` ve her toplu iş için çıkış dosyalarının zaman damgalarını analiz eder. Bir toplu işteki çıktılar güncel değilse, hedef çalıştırılır. Aksi takdirde, hedef atlanır.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Hedef toplu işleme bir örnek için bkz. [hedef toplu işleme Içindeki öğe meta verileri](../msbuild/item-metadata-in-target-batching.md).

## <a name="item-and-property-mutations"></a>Öğe ve özellik mutasyonları

Bu bölümde, hedef toplu işleme veya görev toplu işi kullanılırken özellikleri ve/veya öğe meta verilerini değiştirmenin etkilerini anlamak açıklanmaktadır.

hedef toplu işleme ve görev toplu işlemi iki farklı MSBuild işlem olduğundan, her durumda MSBuild tam olarak hangi türde toplu işlem kullandığını anlamak önemlidir. toplu işleme söz dizimi hedefteki bir `%(ItemMetadataName)` görevde göründüğünde, ancak hedefteki bir öznitelikte yer alırken MSBuild görev toplu işlem kullanır. Hedef toplu işleme belirtmenin tek yolu, genellikle özniteliği bir hedef özniteliğinde toplu işleme söz dizimini kullanmaktır `Outputs` .

Hem hedef toplu işleme hem de görev toplu işleme ile, toplu işler bağımsız olarak çalışacak şekilde düşünülebilir. Tüm toplu işlemler, özellik ve öğe meta verileri değerlerinin başlangıç durumunun bir kopyasıyla başlar. Toplu yürütme sırasında özellik değerlerinin herhangi bir mutasyonları diğer toplu işler için görünür değildir. Aşağıdaki örneği inceleyin:

```xml
  <ItemGroup>
    <Thing Include="2" Color="blue" />
    <Thing Include="1" Color="red" />
  </ItemGroup>

  <Target Name="DemoIndependentBatches">
    <ItemGroup>
      <Thing Condition=" '%(Color)' == 'blue' ">
        <Color>red</Color>
        <NeededColorChange>true</NeededColorChange>
      </Thing>
    </ItemGroup>
    <Message Importance="high"
             Text="Things: @(Thing->'%(Identity) is %(Color); needed change=%(NeededColorChange)')"/>
  </Target>
```

Çıkış şöyle olur:

```output
Target DemoIndependentBatches:
  Things: 2 is red; needed change=true;1 is red; needed change=
```

`ItemGroup`Hedefteki öğesi örtük olarak bir görevdir ve `%(Color)` `Condition` özniteliğinde görev toplu işlemi gerçekleştirilir. İki toplu işlem vardır: biri kırmızı ve diğeri mavi için. Özelliği `%(NeededColorChange)` yalnızca `%(Color)` meta veriler mavi ise ayarlanır ve bu ayar yalnızca mavi toplu iş çalıştırıldığında koşulla eşleşen tek öğeyi etkiler. `Message`Görevin özniteliği, `Text` `%(ItemMetadataName)` bir öğe dönüştürmesi içinde kullanıldığı için, söz dizimi olmasına rağmen toplu işleme tetiklemez.

Toplu işlemler bağımsız olarak çalışır, ancak paralel olarak çalışmaz. Bu, toplu yürütmede değişen meta veri değerlerine eriştiğinizde farklılık yapar. Toplu yürütmede bazı meta verileri temel alan bir özelliği ayarladığınız durumda, özelliği *son* değer kümesini alır:

```xml
   <PropertyGroup>
       <SomeProperty>%(SomeItem.MetadataValue)</SomeProperty>
   </PropertyGroup>
```

Batch yürütmeden sonra özelliği, son değerini korur `%(MetadataValue)` .

Toplu işlemler bağımsız olarak çalıştırılsa da, hedef toplu işleme ve görev toplu işleme arasındaki farkı göz önünde bulundurmanız ve hangi türün durumunuza uygulanacağını bilmenizde yarar vardır. Bu farkın önemini daha iyi anlamak için aşağıdaki örneği göz önünde bulundurun.

Görevler, örtülü görevlerle görev toplu işleme gerçekleştiğinde kafa karıştırıcı olmak üzere açık yerine örtük olabilir. Bir `PropertyGroup` veya `ItemGroup` öğesi öğesinde göründüğünde `Target` , gruptaki her bir özellik bildirimi örtük olarak ayrı bir [CreateProperty](createproperty-task.md) veya [CreateItem](createitem-task.md) görevi gibi işlenir. Bu, hedef toplu olarak, hedef toplu olmadığında (özniteliğinde söz dizimi olmadığında) farklılık gösteren davranışın farklı olduğu anlamına gelir `%(ItemMetadataName)` `Outputs` . Hedef toplu yapıldığında, `ItemGroup` her hedef için bir kez yürütülür, ancak hedef toplu olmadığında, `CreateItem` veya görevlerinin örtük eşdeğerleri `CreateProperty` görev toplu işlemi kullanılarak toplu yapılır, bu nedenle hedef yalnızca bir kez yürütülür ve grup içindeki her öğe veya özellik görev toplu işleme kullanılarak ayrı olarak oluşturulur.

Aşağıdaki örnek, meta verilerin kullanıldığı durumda hedef toplu işleme ve görev toplu işleme ile gösterir. A ve B klasörlerinin bulunduğu bir durumu göz önünde bulundurun:

```
A\1.stub
B\2.stub
B\3.stub
```

Şimdi bu iki benzer projenin çıktısına bakın.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build" Outputs="%(StubDirs.Identity)">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

Çıkış şöyle olur:

```output
Test1:
  >> A\ 'A\' 'A'
Test1:
  >> B\ 'B\' 'B'
```

Şimdi, `Outputs` hedef toplu işleme belirtilen özniteliğini kaldırın.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

Çıkış şöyle olur:

```output
Test1:
  >> A\ 'B\' 'B'
  >> B\ 'B\' 'B'
```

Başlığın `Test1` yalnızca bir kez yazdırıldığını, ancak önceki örnekte iki kez yazdırıldığını unutmayın. Bu, hedefin toplu olmadığı anlamına gelir.  Sonuç olarak, çıkış de farklı şekilde yapılır.

Bu nedenle, hedef toplu işleme kullanılırken her bir hedef Batch her şeyi tüm özellik ve öğelerin bağımsız kopyasıyla birlikte yürütür, ancak `Outputs` özniteliği atlarsanız, özellik grubundaki tek satırlar ayrı, potansiyel olarak toplanmış görevler olarak değerlendirilir. Bu durumda, `ComponentDir` görev toplu olarak `%(ItemMetadataName)` çalıştırılır (söz dizimini kullanır), böylece `ComponentName` satır yürütülür ve her iki satır toplu işi `ComponentDir` tamamlanır ve ikinci satırda görüldüğü gibi değeri belirlenen ikinci bir değer belirlenir.

## <a name="property-functions-using-metadata"></a>Meta verileri kullanan özellik işlevleri

Toplu işlem, meta veri içeren özellik işlevleri tarafından denetlenebilir. Örneğin,

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

<xref:System.IO.Path.Combine%2A>bir kök klasör yolunu derleme öğesi yoluyla birleştirmek için kullanır.

Özellik işlevleri, meta veri değerleri içinde görünmeyebilir. Örneğin,

`%(Compile.FullPath.Substring(0,3))`

izin verilmiyor.

Özellik işlevleri hakkında daha fazla bilgi için bkz. [özellik işlevleri](../msbuild/property-functions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [ItemMetadata öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
