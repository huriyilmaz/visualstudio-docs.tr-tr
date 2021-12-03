---
title: öğe MSBuild | Microsoft Docs
description: bir yapıya dahil edilecek dosyaları belirtmek için ıtemgroup 'un MSBuild Include özniteliğini nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 11da7d47cf4d654564f5015afabfd842ce1f8d91
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133514525"
---
# <a name="msbuild-items"></a>MSBuild öğeleri

MSBuild öğeler derleme sistemine giriş ve genellikle dosyaları temsil eder (dosyalar `Include` özniteliğinde belirtilir). Öğeler öğe adlarına göre öğe türlerine gruplanır. Öğe türleri, görevler için parametre olarak kullanılabilecek öğelerin adlandırılmış listeleridir. Görevler, yapı işleminin adımlarını gerçekleştirmek için öğe değerlerini kullanır.

 Öğeler ait oldukları öğe türüne göre adlandırıldıklarından, "öğe" ve "öğe değeri" terimleri birbirlerinin yerine kullanılabilir.

## <a name="create-items-in-a-project-file"></a>Proje dosyasında öğe oluşturma

 Öğeleri proje dosyasında bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğeleri olarak bildirirsiniz. Alt öğenin adı öğenin türüdür. `Include`Öğesinin özniteliği, bu öğe türüne dahil edilecek öğeleri (dosyaları) belirtir. Örneğin, aşağıdaki XML iki dosya içeren adlı bir öğe türü oluşturur `Compile` .

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 *Dosya2. cs* öğesi *FILE1. cs*; öğesinin yerini almaz Bunun yerine, dosya adı öğe türü için değerler listesine eklenir `Compile` .

 Aşağıdaki XML, her iki dosyayı tek bir öznitelikte bildirerek aynı öğe türünü oluşturur `Include` . Dosya adlarının noktalı virgülle ayrıldığına dikkat edin.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

`Include`Özniteliği, öğe bir *. targets* dosyası gibi içeri aktarılan bir dosyada olsa bile, proje dosyasının klasörü ($ (MSBuildProjectPath) göreli olarak yorumlanan bir yoldur.

## <a name="create-items-during-execution"></a>Yürütme sırasında öğe oluşturma

 [Hedef](../msbuild/target-element-msbuild.md) öğelerin dışında kalan öğelere, bir yapı değerlendirme aşamasında değerler atanır. Sonraki yürütme aşamasında, öğeler aşağıdaki yollarla oluşturulabilir veya değiştirilebilir:

- Herhangi bir görev bir öğeyi yayabilir. Bir öğeyi oluşturmak için, [görev](../msbuild/task-element-msbuild.md) öğesinin bir özniteliği olan bir alt [Çıkış](../msbuild/output-element-msbuild.md) öğesi olması gerekir `ItemName` .

- [CreateItem](../msbuild/createitem-task.md) görevi bir öğeyi yayabilir. Bu kullanım önerilmiyor.

- .NET Framework 3,5 ' den başlayarak `Target` öğeler, öğe öğeleri içerebilen [ıtemgroup](../msbuild/itemgroup-element-msbuild.md) öğeleri içerebilir.

## <a name="reference-items-in-a-project-file"></a>Proje dosyasındaki başvuru öğeleri

 Proje dosyası boyunca öğe türlerine başvurmak için @ () söz dizimini kullanın \<ItemType> . Örneğin, kullanarak önceki örnekteki öğe türüne başvurarak `@(Compile)` . Bu söz dizimini kullanarak, öğe türünü bu görevin parametresi olarak belirterek öğeleri görevlere geçirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: derlenecek dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).

 Varsayılan olarak, bir öğe türünün öğeleri noktalı virgülle ayrılır (;) genişletilmişse. \<ItemType> \<separator> Varsayılan dışında bir ayırıcı belirtmek için @ (, ' ') sözdizimini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme](../msbuild/how-to-display-an-item-list-separated-with-commas.md).

## <a name="use-wildcards-to-specify-items"></a>Öğeleri belirtmek için joker karakterler kullanın

`**` `*` `?` Her dosyayı ayrı olarak listelemek yerine, bir dosya grubunu bir derleme için giriş olarak belirtmek üzere,, ve joker karakterlerini kullanabilirsiniz.

- `?`Joker karakter tek bir karakterle eşleşiyor.
- `*`Joker karakter sıfır veya daha fazla karakterle eşleşiyor.
- `**`Joker karakter dizisi kısmi bir yol ile eşleşiyor.

Örneğin, proje dosyanızda `.cs` aşağıdaki öğesini kullanarak proje dosyasını içeren dizindeki tüm dosyaları belirtebilirsiniz.

```xml
<CSFile Include="*.cs"/>
```

Aşağıdaki öğe `.vb` sürücüdeki tüm dosyaları seçer `D:` :

```xml
<VBFile Include="D:/**/*.vb"/>
```

`*` `?` Joker karakter genişletme olmadan bir öğeye değişmez değer veya karakterler eklemek istiyorsanız, [joker karakterleri atlamanız](../msbuild/how-to-escape-special-characters-in-msbuild.md)gerekir.

Joker karakterler hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturulacak dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).

## <a name="use-the-exclude-attribute"></a>Exclude özniteliğini kullanma

 Öğe öğeleri `Exclude` , belirli öğeleri (dosyaları) öğe türünden dışlayan özniteliği içerebilir. `Exclude`Özniteliği genellikle joker karakterlerle birlikte kullanılır. Örneğin, aşağıdaki XML dizinindeki her *. cs* dosyasını, *DoNotBuild. cs* dosyası hariç CSFile öğe türüne ekler.

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 `Exclude`Özniteliği yalnızca, `Include` her ikisini de içeren öğe öğesindeki özniteliği tarafından eklenen öğeleri etkiler. Aşağıdaki örnek, önceki item öğesine eklenen *Form1. cs* dosyasını dışlayamazsınız.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Daha fazla bilgi için bkz. [nasıl yapılır: derlemeden dosya çıkarma](../msbuild/how-to-exclude-files-from-the-build.md).

## <a name="item-metadata"></a>Öğe meta verileri

 Öğeler `Include` ve özniteliklerindeki bilgilere ek olarak meta veriler içerebilir `Exclude` . Bu meta veriler, öğeler veya toplu görevler ve hedefler hakkında daha fazla bilgi gerektiren görevler tarafından kullanılabilir. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.

 Meta veri, proje dosyasında bir öğe öğesinin alt öğeleri olarak belirtilen anahtar-değer çiftleri koleksiyonudur. Alt öğenin adı, meta verilerin adıdır ve alt öğenin değeri meta verilerin değeridir.

 Meta veriler, kendisini içeren öğe öğesiyle ilişkilendirilir. Örneğin, aşağıdaki XML, `Culture` değeri olan meta verileri `Fr` hem *tek. cs* hem de CSFile öğe türünün *iki. cs* öğesine ekler.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Bir öğe sıfır veya daha fazla meta veri değerine sahip olabilir. Meta veri değerlerini dilediğiniz zaman değiştirebilirsiniz. Meta verileri boş bir değere ayarlarsanız derlemeden etkin bir şekilde kaldırırsınız.

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Proje dosyasındaki başvuru öğesi meta verileri

 Proje dosyasının tamamında,%() sözdizimini kullanarak öğe meta verilerine başvurabilirsiniz \<ItemMetadataName> . Belirsizlik varsa, öğe türü adını kullanarak bir başvuruyu niteleyebilirsiniz. Örneğin,%( \<ItemType.ItemMetaDataName> ) belirtebilirsiniz. Aşağıdaki örnek, Ileti görevinin toplu işi için görüntüleme meta verilerini kullanır. Toplu işleme için öğe meta verilerini kullanma hakkında daha fazla bilgi için, bkz. [görev toplu işleme Içindeki öğe meta verileri](../msbuild/item-metadata-in-task-batching.md).

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

 Öğe türüne bir öğe eklendiğinde, bu öğeye bazı iyi bilinen meta veriler atanır. Örneğin, tüm öğeler, \<Filename> değeri öğenin dosya adı (uzantısı olmadan) olan%() iyi bilinen meta verilere sahiptir. Daha fazla bilgi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Meta verileri kullanarak öğe türlerini dönüştürme

 Meta verileri kullanarak öğe listelerini yeni öğe listelerine dönüştürebilirsiniz. Örneğin, `CppFiles` *. cpp* dosyalarını temsil eden öğeler içeren bir öğe türünü, ifadesini kullanarak. cpp dosyalarını karşılık gelen bir *. obj* dosyası listesine dönüştürebilirsiniz `@(CppFiles -> '%(Filename).obj')` .

 Aşağıdaki kod, `CultureResource` `EmbeddedResource` meta verileri olan tüm öğelerin kopyalarını içeren bir öğe türü oluşturur `Culture` . `Culture`Meta veri değeri, yeni meta verilerin değeri olur `CultureResource.TargetDirectory` .

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

öğeler hakkında daha fazla işlem için bkz. [MSBuild öğe işlevleri](item-functions.md) ve [dönüştürmeleri](../msbuild/msbuild-transforms.md).

## <a name="item-definitions"></a>Öğe tanımları

 3,5 .NET Framework başlayarak, [ıtemdefinitiongroup öğesini](../msbuild/itemdefinitiongroup-element-msbuild.md)kullanarak herhangi bir öğe türüne varsayılan meta veri ekleyebilirsiniz. İyi bilinen meta veriler gibi, varsayılan meta veriler belirttiğiniz öğe türünün tüm öğeleriyle ilişkilendirilir. Bir öğe tanımında varsayılan meta verileri açıkça geçersiz kılabilirsiniz. Örneğin, aşağıdaki XML `Compile` *bir. cs* ve *üç. cs* öğelerini `BuildDay` "Pazartesi" değeriyle meta veriler olarak verir. Kod, "Salı" değerine sahip meta verileri *iki. cs* öğesine verir. `BuildDay`

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

 Daha fazla bilgi için bkz. [öğe tanımları](../msbuild/item-definitions.md).

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Bir hedefin ItemGroup 'lerindeki öğelerin öznitelikleri

 .NET Framework 3,5 ' den başlayarak `Target` öğeler, öğe öğeleri içerebilen [ıtemgroup](../msbuild/itemgroup-element-msbuild.md) öğeleri içerebilir. Bu bölümdeki öznitelikler, içindeki bir öğesi için belirtildiğinde geçerlidir `ItemGroup` `Target` .

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Özniteliği kaldır

 `Remove`Öznitelik, öğe türünden belirli öğeleri (dosyaları) kaldırır. bu öznitelik .NET Framework 3,5 ' de tanıtılmıştı (yalnızca hedefler içinde). MSBuild 15,0 ' den başlayarak hem iç hem de dış hedeflerin desteklendiği desteklenir.

 Aşağıdaki örnek, derleme öğesi türünden her *.config* dosyasını kaldırır.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

#### <a name="matchonmetadata-attribute"></a>MatchOnMetadata özniteliği

`MatchOnMetadata`Özniteliği yalnızca `Remove` diğer öğelere başvuran öznitelikler için geçerlidir (örneğin, `Remove="@(Compile);@(Content)"` ) ve Remove işleminin, öğe değerlerine göre eşleştirmek yerine, belirtilen meta veri adlarının değerlerine göre öğeleri eşleşecek şekilde yönlendirir.

İçin eşleşen kural: meta verileri olan `B Remove="@(A)" MatchOnMetadata="M"` tüm öğeleri, meta veri `B` `M` değeri, `V` `M` `A` değeri meta verileri ile eşleşen herhangi bir öğeyle eşleşir `M` `V` .

```xml
<Project>
  <ItemGroup>
    <A Include='a1' M1='1' M2='a' M3="e"/>
    <A Include='b1' M1='2' M2='x' M3="f"/>
    <A Include='c1' M1='3' M2='y' M3="g"/>
    <A Include='d1' M1='4' M2='b' M3="h"/>

    <B Include='a2' M1='x' m2='c' M3="m"/>
    <B Include='b2' M1='2' m2='x' M3="n"/>
    <B Include='c2' M1='2' m2='x' M3="o"/>
    <B Include='d2' M1='3' m2='y' M3="p"/>
    <B Include='e2' M1='3' m2='Y' M3="p"/>
    <B Include='f2' M1='4'        M3="r"/>
    <B Include='g2'               M3="s"/>

    <B Remove='@(A)' MatchOnMetadata='M1;M2'/>
  </ItemGroup>

  <Target Name="PrintEvaluation">
    <Message Text="%(B.Identity) M1='%(B.M1)' M2='%(B.M2)' M3='%(B.M3)'" />
  </Target>
</Project>
```

Yukarıdaki örnekte, öğe değerleri `b2` , `c2` ve `d2` Şu nedenle öğesinden kaldırılır `B` :
 - `b2` ve `c2` ile `B` `b1` arasında `A` `M1=2` ve arasında `M2=x`
 - `d2``B` `c1` `A` , ve üzerindeki ile arasında `M1=3``M2=y`

`Message`Görev aşağıdakileri çıktı:
```
  a2 M1='x' M2='c' M3='m'
  e2 M1='3' M2='Y' M3='p'
  f2 M1='4' M2='' M3='r'
  g2 M1='' M2='' M3='s'
```

`MatchOnMetadata` [MSBuild ortak SDK](https://github.com/dotnet/msbuild/blob/808b2ae2a176679d15f8c3299e551a63cb55b799/src/Tasks/Microsoft.Common.CurrentVersion.targets#L5019)'dan örnek kullanım:
```xml
      <_TransitiveItemsToCopyToOutputDirectory Remove="@(_ThisProjectItemsToCopyToOutputDirectory)" MatchOnMetadata="TargetPath" MatchOnMetadataOptions="PathLike" />
```
Yukarıdaki satır, `_TransitiveItemsToCopyToOutputDirectory` `TargetPath` içindeki öğelerden aynı meta veri değerlerine sahip olan öğeleri kaldırır `_ThisProjectItemsToCopyToOutputDirectory`

#### <a name="matchonmetadataoptions-attribute"></a>MatchOnMetadataOptions özniteliği

`MatchOnMetadata`Öğeler arasındaki meta veri değerlerini eşleştirmek için tarafından kullanılan dize ile eşleşen stratejiyi belirtir (meta veri adları her zaman büyük/küçük harfe duyarlıdır). Olası değerler `CaseSensitive` , `CaseInsensitive` , veya `PathLike` . `CaseSensitive` varsayılan değerdir.

`PathLike` eğik çizgi yönlerinin normalleştirilmesi, sondaki eğik çizgileri yoksayarak `.` ve `..` tüm göreli yolların geçerli dizine göre mutlak hale getirilmesi gibi değerlere yol algılayan normalleştirme uygular.

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> KeepMetadata özniteliği

 Bir hedef içinde bir öğe oluşturulduysa, öğe öğesi `KeepMetadata` özniteliğini içerebilir. Bu öznitelik belirtilmişse, yalnızca noktalı virgülle ayrılmış ad listesinde belirtilen meta veriler, kaynak öğeden hedef öğeye aktarılır. Bu öznitelik için boş bir değer, Belirtmemeye eşdeğerdir. `KeepMetadata`öznitelik .NET Framework 4,5 ' de tanıtılmıştı.

 Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir `KeepMetadata` .

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

 Bir hedef içinde bir öğe oluşturulduysa, öğe öğesi `RemoveMetadata` özniteliğini içerebilir. Bu öznitelik belirtilmişse, tüm meta veriler kaynak öğeden, adları noktalı virgülle ayrılmış ad listesinde yer alan meta veriler hariç hedef öğeye aktarılır. Bu öznitelik için boş bir değer, Belirtmemeye eşdeğerdir. `RemoveMetadata`öznitelik .NET Framework 4,5 ' de tanıtılmıştı.

 Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir `RemoveMetadata` .

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

öğeler hakkında daha fazla işlem için bkz. [MSBuild öğe işlevleri](item-functions.md).

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> Mi Pduplilıları özniteliği

 Bir hedef içinde bir öğe oluşturulduysa, öğe öğesi `KeepDuplicates` özniteliğini içerebilir. `KeepDuplicates` öğe, `Boolean` varolan bir öğenin tam yinelemesi ise, bir öğenin hedef gruba eklenip eklenmeyeceğini belirten bir özniteliktir.

 Kaynak ve hedef öğe aynı ekleme değerine ancak farklı meta verilere sahip ise, olarak ayarlanmış olsa bile öğe eklenir `KeepDuplicates` `false` . Bu öznitelik için boş bir değer, Belirtmemeye eşdeğerdir. `KeepDuplicates`öznitelik .NET Framework 4,5 ' de tanıtılmıştı.

 Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir `KeepDuplicates` .

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

## <a name="updating-metadata-on-items-in-an-itemgroup-outside-of-a-target"></a>Bir hedef dışındaki bir ItemGroup öğelerinde bulunan öğelerde meta verileri güncelleştirme

Hedeflerin dışındaki öğeler, var olan meta verilerinin öznitelik aracılığıyla güncelleştirilmesini sağlayabilir `Update` . Bu öznitelik, hedefler altındaki öğeler **için kullanılamaz.**

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
MSBuild sürüm 16,6 ve üzeri sürümlerde öznitelik, `Update` iki veya daha fazla öğeden meta verilerin içeri aktarılmasını kolaylaştırmak için nitelikli meta veri başvurularını destekler.

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

Açıklamalarının
- Nitelenmemiş meta veriler (% (e)) güncelleştirilmekte olan öğe türüne bağlar ( `Item1` Yukarıdaki örnekte). Nitelenmiş meta veriler ( `%(Item2.Color)` ), güncelleştirme ifadesinden yakalanan eşleşen öğe türleri kümesinin içine bağlar.
- Bir öğe, birden fazla başvurulan öğe içinde birden çok kez eşleşiyorsa:
  - Başvurulan her öğe türünden son oluşum yakalanır (Bu nedenle, öğe türü başına yakalanan bir öğe).
  - Bu, hedefler altında görev öğesi toplu işleme davranışını eşleştirir.
- Her biri%() başvuruyu koyabileceği yer:
  - Meta veri
  - Meta veri koşulları
- Meta veri adı eşleştirmesi büyük/küçük harfe duyarlıdır.
:::moniker-end

## <a name="updating-metadata-on-items-in-an-itemgroup-of-a-target"></a>Bir hedefin ItemGroup öğelerinde bulunan öğelerde meta verileri güncelleştirme

Meta veriler, daha az bir ifade sözdizimi ile hedefler içinde değiştirilebilir `Update` :

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
- [Nasıl yapılır: derlenecek dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md)
- [Nasıl yapılır: derlemeden Dosya dışlama](../msbuild/how-to-exclude-files-from-the-build.md)
- [Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Öğe tanımları](../msbuild/item-definitions.md)
- [Toplu İşleme](../msbuild/msbuild-batching.md)
