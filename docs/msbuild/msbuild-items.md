---
title: MSBuild Öğeler | Microsoft Docs
description: Bir derlemeye dahil edilecek MSBuild belirtmek için ItemGroup'ta MSBuild Include özniteliğini kullanmayı öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 520349f829a696e2b34aef262efd01e937ad1998
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077237"
---
# <a name="msbuild-items"></a>MSBuild öğeleri

MSBuild, derleme sistemine girişlerdir ve genellikle dosyaları temsil eder (dosyalar özniteliğinde `Include` belirtilir). Öğeler, öğe adlarına göre öğe türlerine göre gruptur. Öğe türleri, görevler için parametre olarak kullanılan öğelerin adlandırılmış listeleridir. Görevler, derleme işleminin adımlarını gerçekleştirmek için öğe değerlerini kullanır.

 Öğeler ait olduğu öğe türüne göre adlandırılmış olduğundan, "öğe" ve "öğe değeri" terimleri birbirinin yerine kullanılabilir.

## <a name="create-items-in-a-project-file"></a>Proje dosyasında öğe oluşturma

 Proje dosyasındaki öğeleri bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğeleri olarak bildirebilirsiniz. Alt öğenin adı, öğenin t t'tir. `Include`öğesinin özniteliği, bu öğe türüne dahil edilecek öğeleri (dosyaları) belirtir. Örneğin, aşağıdaki XML iki dosya içeren adlı bir `Compile` öğe türü oluşturur.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 item *file2.cs* öğesi *file1.cs öğesinin yerini alaz;* Bunun yerine, dosya adı öğe türü için değer listesine `Compile` eklenir.

 Aşağıdaki XML, her iki dosyanın da tek bir öznitelikte bildirerek aynı öğe türünü `Include` oluşturur. Dosya adlarının noktalı virgülle ayrıldığına dikkat olun.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

özniteliği, öğe .targets dosyası gibi içe aktarılan bir dosyada olsa bile proje dosyasının klasörüne göre yorumlanır `Include` ($(MSBuildProjectPath). 

## <a name="create-items-during-execution"></a>Yürütme sırasında öğe oluşturma

 Target öğelerinin [dışında](../msbuild/target-element-msbuild.md) olan öğelere, derlemenin değerlendirme aşamasında değerler atanır. Sonraki yürütme aşamasında öğeler aşağıdaki yollarla oluşturulabilir veya değiştirilebilir:

- Herhangi bir görev bir öğe yayır. Bir öğeyi yayma için, [Görev öğesinin](../msbuild/task-element-msbuild.md) bir özniteliği [olan](../msbuild/output-element-msbuild.md) bir alt Çıkış öğesi olması `ItemName` gerekir.

- [CreateItem görevi](../msbuild/createitem-task.md) bir öğe yayır. Bu kullanım önerilmiyor.

- 3.5 .NET Framework başlayarak, `Target` öğeler öğe öğeleri içerenin [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğelerini içerebilir.

## <a name="reference-items-in-a-project-file"></a>Proje dosyasındaki başvuru öğeleri

 Proje dosyası boyunca öğe türlerine başvuru yapmak için @( sözdizimini \<ItemType> kullanırsınız. Örneğin, kullanarak önceki örnekte öğe türüne `@(Compile)` başvurabilirsiniz. Bu söz dizimi kullanarak, öğe türünü bu görevin parametresi olarak belirterek öğeleri görevlere geçebilirsiniz. Daha fazla bilgi için, [bkz. How to: Select the files to build](../msbuild/how-to-select-the-files-to-build.md).

 Varsayılan olarak, bir öğe türünün öğeleri noktalı virgülle (;) genişletilirken. Varsayılandan farklı bir ayırıcı belirtmek için @( \<ItemType> , \<separator> ' ') söz dizimi kullanabilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Virgülle ayrılmış bir öğe listesi görüntüleme.](../msbuild/how-to-display-an-item-list-separated-with-commas.md)

## <a name="use-wildcards-to-specify-items"></a>Öğeleri belirtmek için joker karakterler kullanma

Her dosyayı ayrı listelemek yerine, bir dosya grubunu derleme için giriş olarak belirtmek için , `**` `*` ve joker `?` karakterlerini kullanabilirsiniz.

- Joker `?` karakter tek bir karakterle eştir.
- Joker `*` karakter sıfır veya daha fazla karakterle eşler.
- Joker `**` karakter dizisi kısmi bir yol ile eştir.

Örneğin, proje dosyanız içinde aşağıdaki öğeyi kullanarak proje dosyasını içeren dizindeki `.cs` tüm dosyaları belirtebilirsiniz.

```xml
<CSFile Include="*.cs"/>
```

Aşağıdaki öğe sürücüdeki `.vb` tüm dosyaları `D:` seçer:

```xml
<VBFile Include="D:/**/*.vb"/>
```

Joker karakter genişletmesi olmayan bir öğeye sabit veya karakter eklemek için joker karakter `*` `?` [karakterlerini kaçış karakteri olarak yazmalısiniz.](../msbuild/how-to-escape-special-characters-in-msbuild.md)

Joker karakterler hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Derlemek için dosyaları seçme.](../msbuild/how-to-select-the-files-to-build.md)

## <a name="use-the-exclude-attribute"></a>Exclude özniteliğini kullanma

 Öğe öğeleri, belirli `Exclude` öğeleri (dosyalar) öğe türünün dışında bırakan özniteliğini içerebilir. Özniteliği `Exclude` genellikle joker karakterlerle birlikte kullanılır. Örneğin, aşağıdaki XML dizinde yer alan *her .cs* dosyasını *DoNotBuild.cs* dosyası dışında CSFile öğe türüne ekler.

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 özniteliği `Exclude` yalnızca her ikisini de içeren öğe `Include` öğesinde özniteliği tarafından eklenen öğeleri etkiler. Aşağıdaki örnek, önceki öğe öğesine eklenen *Form1.cs* dosyasını dışlamaz.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Daha fazla bilgi için, [bkz. How to: Exclude files from the build](../msbuild/how-to-exclude-files-from-the-build.md).

## <a name="item-metadata"></a>Öğe meta verileri

 Öğeler ve özniteliklerinde bilgilere ek olarak meta `Include` `Exclude` veriler içerebilir. Bu meta veriler, öğeler hakkında daha fazla bilgi gerektiren görevler veya toplu görevler ve hedefler için kullanılabilir. Daha fazla bilgi için bkz. [Toplu işleme.](../msbuild/msbuild-batching.md)

 Meta veriler, proje dosyasında bir öğe öğesinin alt öğeleri olarak bildirilen anahtar-değer çiftleri koleksiyonudur. Alt öğenin adı meta verilerin adı, alt öğenin değeri ise meta verilerin değeridir.

 Meta veriler, onu içeren öğe öğesiyle ilişkilendirildi. Örneğin, aşağıdaki XML `Culture` CSFile öğe türünün hem `Fr` one.cs hem de *two.cs*  öğelerine değere sahip meta verileri ekler.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Bir öğe sıfır veya daha fazla meta veri değerine sahip olabilir. Meta veri değerlerini herhangi bir zamanda değiştirebilirsiniz. Meta verileri boş bir değere ayarsanız, bunu derlemeden etkili bir şekilde kaldırmış oluruz.

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Proje dosyasındaki başvuru öğesi meta verileri

 %( söz dizimi kullanarak proje dosyası boyunca öğe meta verilerine \<ItemMetadataName> başvurabilirsiniz. Belirsizlik varsa, öğe türünün adını kullanarak bir başvuruya uygun olabilir. Örneğin, %( ) \<ItemType.ItemMetaDataName> belirtebiliyoruz. Aşağıdaki örnekte İleti görevini toplu olarak çalıştırmak için Meta verileri görüntüle kullanılır. Toplu işlem için öğe meta verilerini kullanma hakkında daha fazla bilgi için bkz. Görev toplu [işlemesinde öğe meta verileri.](../msbuild/item-metadata-in-task-batching.md)

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Stuff Include="One.cs" >
            <Display>false</Display>
        </Stuff>
        <Stuff Include="Two.cs">
            <Display>true</Display>
        </Stuff>
    </ItemGroup>
    <Target Name="Batching">
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>
    </Target>
</Project>
```

### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> İyi bilinen öğe meta verileri

 Bir öğe türüne bir öğe ekleniyorsa, bu öğeye bazı iyi bilinen meta veriler atanır. Örneğin, tüm öğelerin değeri öğenin dosya adı olan (uzantı olmadan) iyi bilinen %( \<Filename> meta verilerine sahip olur. Daha fazla bilgi için [bkz. İyi bilinen öğe meta verileri.](../msbuild/msbuild-well-known-item-metadata.md)

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Meta verileri kullanarak öğe türlerini dönüştürme

 Meta verileri kullanarak öğe listelerini yeni öğe listelerine dönüştürebilirsiniz. Örneğin, .cpp dosyalarını temsil eden öğeleri olan bir öğe türünü ifadeyi kullanarak karşılık gelen `CppFiles` *bir .obj* dosyaları listesine  dönüştürebilirsiniz. `@(CppFiles -> '%(Filename).obj')`

 Aşağıdaki kod, meta `CultureResource` verileri olan tüm öğelerin kopyalarını içeren bir öğe türü `EmbeddedResource` `Culture` oluşturur. Meta `Culture` veri değeri, yeni meta verilerin değeri `CultureResource.TargetDirectory` olur.

```xml
<Target Name="ProcessCultureResources">
    <ItemGroup>
        <CultureResource Include="@(EmbeddedResource)"
            Condition="'%(EmbeddedResource.Culture)' != ''">
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>
        </CultureResource>
    </ItemGroup>
</Target>
```

 Daha fazla bilgi için bkz. [Dönüşümler.](../msbuild/msbuild-transforms.md)

## <a name="item-definitions"></a>Öğe tanımları

 3.5 .NET Framework [başlayarak, ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md)öğesini kullanarak herhangi bir öğe türüne varsayılan meta veriler ebilirsiniz. İyi bilinen meta veriler gibi varsayılan meta veriler de belirttiğiniz öğe türünün tüm öğeleriyle ilişkilendirilmektedir. Bir öğe tanımında varsayılan meta verileri açıkça geçersiz kılabilirsiniz. Örneğin, aşağıdaki XML öğelerine `Compile` *one.cs ve three.cs* *meta* verilerini `BuildDay` "Monday" değeriyle verir. Kod, *two.cs öğesine* `BuildDay` "Tuesday" değerine sahip meta verileri verir.

```xml
<ItemDefinitionGroup>
    <Compile>
        <BuildDay>Monday</BuildDay>
    </Compile>
</ItemDefinitionGroup>
<ItemGroup>
    <Compile Include="one.cs;three.cs" />
    <Compile Include="two.cs">
        <BuildDay>Tuesday</BuildDay>
    </Compile>
</ItemGroup>
```

 Daha fazla bilgi için [bkz. Öğe tanımları.](../msbuild/item-definitions.md)

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Bir Hedefin ItemGroup'larında öğeler için öznitelikler

 3.5 .NET Framework başlayarak, `Target` öğeler öğe öğeleri içerenin [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğelerini içerebilir. Bu bölümdeki öznitelikler, içinde olan bir öğe için `ItemGroup` belirtildikleri zaman `Target` geçerlidir.

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Özniteliği kaldırma

 özniteliği, `Remove` belirli öğeleri (dosyalar) öğe türünden kaldırır. Bu öznitelik 3.5 .NET Framework (yalnızca hedeflerin içinde) tanıtıldı. Hem iç hem de dış hedefler, 15.0'dan MSBuild destekleni.

 Aşağıdaki örnek, Derleme *.config* dosyanın her birini kaldırır.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> KeepMetadata özniteliği

 Bir öğe hedef içinde oluşturulursa öğe öğesi özniteliğini `KeepMetadata` içerebilir. Bu öznitelik belirtilirse, yalnızca noktalı virgülle ayrılmış ad listesinde belirtilen meta veriler kaynak öğeden hedef öğeye aktarılır. Bu öznitelik için boş bir değer belirtmeye eşdeğerdir. özniteliği, `KeepMetadata` 4.5 .NET Framework tanıtıldı.

 Aşağıdaki örnek özniteliğinin nasıl kullanılageldi? `KeepMetadata`

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0">

    <ItemGroup>
        <FirstItem Include="rhinoceros">
            <Class>mammal</Class>
            <Size>large</Size>
        </FirstItem>

    </ItemGroup>
    <Target Name="MyTarget">
        <ItemGroup>
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />
        </ItemGroup>

        <Message Text="FirstItem: %(FirstItem.Identity)" />
        <Message Text="  Class: %(FirstItem.Class)" />
        <Message Text="  Size:  %(FirstItem.Size)"  />

        <Message Text="SecondItem: %(SecondItem.Identity)" />
        <Message Text="  Class: %(SecondItem.Class)" />
        <Message Text="  Size:  %(SecondItem.Size)"  />
    </Target>
</Project>

<!--
Output:
  FirstItem: rhinoceros
    Class: mammal
    Size:  large
  SecondItem: rhinoceros
    Class: mammal
    Size:
-->
```

### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> RemoveMetadata özniteliği

 Bir öğe hedef içinde oluşturulursa öğe öğesi özniteliğini `RemoveMetadata` içerebilir. Bu öznitelik belirtilirse, adları noktalı virgülle ayrılmış ad listesinde yer alan meta veriler dışında tüm meta veriler kaynak öğeden hedef öğeye aktarılır. Bu öznitelik için boş bir değer belirtmeye eşdeğerdir. özniteliği, `RemoveMetadata` 4.5 .NET Framework tanıtıldı.

 Aşağıdaki örnek özniteliğinin nasıl kullanılageldi? `RemoveMetadata`

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <MetadataToRemove>Size;Material</MetadataToRemove>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)" />
        <Message Text="  Size:     %(Item1.Size)" />
        <Message Text="  Color:    %(Item1.Color)" />
        <Message Text="  Material: %(Item1.Material)" />
        <Message Text="Item2: %(Item2.Identity)" />
        <Message Text="  Size:     %(Item2.Size)" />
        <Message Text="  Color:    %(Item2.Color)" />
        <Message Text="  Material: %(Item2.Material)" />
    </Target>
</Project>

<!--
Output:
  Item1: stapler
    Size:     medium
    Color:    black
    Material: plastic
  Item2: stapler
    Size:
    Color:    black
    Material:
-->
```

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> KeepDuplicates özniteliği

 Bir öğe hedef içinde oluşturulursa öğe öğesi özniteliğini `KeepDuplicates` içerebilir. `KeepDuplicates` , bir öğenin var olan bir öğenin tam olarak yineleniyorsa hedef gruba ekli olup olmadığını `Boolean` belirten bir özniteliktir.

 Kaynak ve hedef öğe aynı Include değerine ancak farklı meta verilere sahipse, öğesi olarak ayarlanmış `KeepDuplicates` olsa bile `false` eklenir. Bu öznitelik için boş bir değer belirtmeye eşdeğerdir. özniteliği, `KeepDuplicates` 4.5 .NET Framework tanıtıldı.

 Aşağıdaki örnek özniteliğinin nasıl kullanılageldi? `KeepDuplicates`

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Item1 Include="hourglass;boomerang" />
        <Item2 Include="hourglass;boomerang" />
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item1 Include="hourglass" KeepDuplicates="false" />
            <Item2 Include="hourglass" />
        </ItemGroup>

        <Message Text="Item1: @(Item1)" />
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />
        <Message Text="Item2: @(Item2)" />
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />
    </Target>
</Project>

<!--
Output:
  Item1: hourglass;boomerang
    hourglass  Count: 1
    boomerang  Count: 1
  Item2: hourglass;boomerang;hourglass
    hourglass  Count: 2
    boomerang  Count: 1
-->
```

## <a name="updating-metadata-on-items-in-an-itemgroup-outside-of-a-target"></a>Hedef dışında bir ItemGroup'ta öğelerdeki meta verileri güncelleştirme

Hedeflerin dışındaki öğelerin mevcut meta verileri özniteliği aracılığıyla `Update` güncelleştirilebilir. Bu **öznitelik, hedefler** altındaki öğeler için kullanılamaz.

```xml
<Project>
    <PropertyGroup>
        <MetadataToUpdate>pencil</MetadataToUpdate>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Color>red</Color>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="notebook">
            <Size>SMALL</Size>
            <Color>YELLOW</Color>
        </Item2>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="$(MetadataToUpdate);stapler;er*r;@(Item2)" Price="10" Material="">
            <Color>RED</Color>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: RED
    Material:
    Price: 10
Item1: pencil
    Size: small
    Color: RED
    Material:
    Price: 10
Item1: eraser
    Size:
    Color: RED
    Material:
    Price: 10
Item1: notebook
    Size: large
    Color: RED
    Material:
    Price: 10
-->
```

:::moniker range=">=vs-2019"
Sürüm MSBuild 16.6 ve sonraki sürümlerde özniteliği, iki veya daha fazla öğeden meta verileri içeri aktarmayı kolaylaştırmak için nitelikli meta veri `Update` başvurularını destekler.

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item3 Include="notebook">
            <Size>SMALL</Size>
            <Color>BLUE</Color>
            <Price>20</Price>
        </Item3>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="@(Item2);er*r;@(Item3)" Size="%(Size)" Color="%(Item2.Color)" Price="%(Item3.Price)" Model="2020">
            <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: black
    Material: plastic
    Price:
    Model:
Item1: pencil
    Size: small
    Color: RED
    Material: Premium PLASTIC
    Price:
    Model: 2020
Item1: eraser
    Size: small
    Color:
    Material: gum
    Price:
    Model: 2020
Item1: notebook
    Size: large
    Color:
    Material: paper
    Price: 20
    Model: 2020
-->
```

Açıklamalar:
- Tam olmayan meta veriler (%(M)) güncelleştirilen öğe türüne `Item1` (yukarıdaki örnekte) bağlar. Nitelikli meta veriler ( `%(Item2.Color)` ) Update ifadesinde yakalanan eşleşen öğe türleri kümesi içinde bağlar.
- Bir öğe, başvurulan birden çok öğenin içinde ve arasında birden çok kez eş olursa:
  - Başvurulan her öğe türünden son oluşum yakalanır (bu nedenle her öğe türü için bir yakalanan öğe).
  - Bu, hedef altında toplu iş işleme görev öğesinin davranışıyla eşler.
- Burada %() başvuruları yer almaktadır:
  - Meta veri
  - Meta veri koşulları
- Meta veri adı eşleştirmesi büyük/büyük/büyük harfe duyarlı değildir.
:::moniker-end

## <a name="updating-metadata-on-items-in-an-itemgroup-of-a-target"></a>Bir Hedefin ItemGroup'larında öğelerdeki meta verileri güncelleştirme

Meta veriler, hedeflerde de yerine daha az ifade eden söz dizimi ile `Update` değiştirilebilir:

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item2 Include="ruler">
            <Color>GREEN</Color>
        </Item2>

    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <!-- Metadata can be expressed either as attributes or as elements -->
            <Item1 Size="GIGANTIC" Color="%(Item2.Color)">
                <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
            </Item1>
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: pencil
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: eraser
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: notebook
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
-->
```

## <a name="see-also"></a>Ayrıca bkz.

- [Öğe öğesi (MSBuild)](../msbuild/item-element-msbuild.md)
- [Yaygın MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Nasıl kullanılır: Derlemek için dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md)
- [Nasıl kullanılır: Dosyaları derlemeden dışlama](../msbuild/how-to-exclude-files-from-the-build.md)
- [Nasıl kullanılır: Virgülle ayrılmış bir öğe listesi görüntüleme](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Öğe tanımları](../msbuild/item-definitions.md)
- [Toplu İşleme](../msbuild/msbuild-batching.md)
