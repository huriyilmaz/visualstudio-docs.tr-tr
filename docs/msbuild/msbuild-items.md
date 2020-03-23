---
title: MSBuild Ürünleri | Microsoft Dokümanlar
description: Bir yapıya eklenecek dosyaları belirtmek için ItemGroup'un MSBuild Ekle özniteliğini kullanın
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7c41539ec50cb166dfe60690a4722992b29a47a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093966"
---
# <a name="msbuild-items"></a>MSBuild öğeleri

MSBuild öğeleri yapı sistemine girişlerdir ve genellikle dosyaları temsil eder (dosyalar `Include` öznitelikte belirtilir). Öğeler öğe adlarına göre madde türlerine ayrılır. Madde türleri, görevler için parametre olarak kullanılabilecek öğelerin listeleri olarak adlandırılır. Görevler, yapı işleminin adımlarını gerçekleştirmek için madde değerlerini kullanır.

 Maddeler ait oldukları madde türüne göre adlandırıldıklarına göre, "madde" ve "madde değeri" terimleri birbirinin yerine kullanılabilir.

## <a name="create-items-in-a-project-file"></a>Proje dosyasında öğe oluşturma

 Proje dosyasındaki öğeleri bir [Öğe Grubu](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğeleri olarak beyan emzebilirsiniz. Alt öğenin adı öğenin türüdür. Öğenin `Include` özniteliği, bu madde türüne eklenecek öğeleri (dosyaları) belirtir. Örneğin, aşağıdaki XML, iki dosya içeren adlandırılmış `Compile`bir öğe türü oluşturur.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Madde *file2.cs* öğe *file1.cs*değiştirmiyor; bunun yerine, dosya adı `Compile` madde türü için değerler listesine eklenir.

 Aşağıdaki XML, her iki dosyayı tek bir `Include` öznitelikte beyan ederek aynı madde türünü oluşturur. Dosya adlarının bir yarı nokta nokta ile ayrıldığına dikkat edin.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

Öznitelik, `Include` öğe *.targets* dosyası gibi içe aktarılan bir dosyada olsa bile, proje dosyasının klasörüne göre yorumlanan bir yoldur.

## <a name="create-items-during-execution"></a>Yürütme sırasında öğe oluşturma

 [Hedef](../msbuild/target-element-msbuild.md) öğelerin dışındaki öğeler, yapının değerlendirme aşamasında değerler atanır. Sonraki yürütme aşamasında, öğeler oluşturulabilir veya aşağıdaki şekillerde değiştirilebilir:

- Herhangi bir görev bir öğe yontabilir. Bir öğeyi yalamak için [Görev](../msbuild/task-element-msbuild.md) öğesinin özniteliği olan `ItemName` bir alt [çıktı](../msbuild/output-element-msbuild.md) öğesi olması gerekir.

- [CreateItem](../msbuild/createitem-task.md) görevi bir öğe yatabilir. Bu kullanım önerilmiyor.

- .NET Framework 3.5'ten `Target` başlayarak, öğeler öğe öğeleri içerebilecek [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğeleri içerebilir.

## <a name="reference-items-in-a-project-file"></a>Proje dosyasındaki başvuru öğeleri

 Proje dosyası boyunca madde türlerine başvurmak için @(ItemType>)\<sözdizimini kullanırsınız. Örneğin, önceki örnekte madde türüne . `@(Compile)` Bu sözdizimini kullanarak, madde türünü bu görevin parametresi olarak belirterek maddeleri görevlere geçirebilirsiniz. Daha fazla bilgi için [bkz: Oluşturmak için dosyaları seçin.](../msbuild/how-to-select-the-files-to-build.md)

 Varsayılan olarak, bir madde türünün öğeleri yarım iki nokta üst üste (;) genişletildiğinde. Varsayılan dışında bir ayırıcı\<belirtmek için\<sözdizimi @(ItemType>, ' ayırıcı>' kullanabilirsiniz. Daha fazla bilgi için [bkz: Virgülle ayrılmış bir öğe listesini görüntüleyin.](../msbuild/how-to-display-an-item-list-separated-with-commas.md)

## <a name="use-wildcards-to-specify-items"></a>Öğeleri belirtmek için joker karakterleri kullanma

Her dosyayı `**` `*`ayrı `?` ayrı listelemek yerine bir yapı girişi olarak bir dosya grubu belirtmek için , ve joker karakter ekleyebilirsiniz.

- `?` Joker karakter tek bir karakterle eşleşir.
- `*` Joker karakter sıfır veya daha fazla karakterle eşleşir.
- `**` Joker karakter dizisi kısmi bir yolile eşleşir.

Örneğin, proje dosyanızda `.cs` aşağıdaki öğeyi kullanarak proje dosyasını içeren dizindeki tüm dosyaları belirtebilirsiniz.

```xml
<CSFile Include="*.cs"/>
```

Aşağıdaki öğe sürücüdeki `.vb` `D:` tüm dosyaları seçer:

```xml
<VBFile Include="D:/**/*.vb"/>
```

Joker karakter genişletmesi `*` olmayan `?` bir öğeye gerçek veya karakter eklemek istiyorsanız, [joker karakterden kaçmalısınız.](../msbuild/how-to-escape-special-characters-in-msbuild.md)

Joker karakter hakkında daha fazla bilgi için [bkz.](../msbuild/how-to-select-the-files-to-build.md)

## <a name="use-the-exclude-attribute"></a>Dışa bakma özniteliğini kullanma

 Öğe öğeleri, `Exclude` belirli öğeleri (dosyaları) öğe türünden hariç öznitelik içerebilir. Öznitelik `Exclude` genellikle joker karakterlerle birlikte kullanılır. Örneğin, aşağıdaki XML, *dizindeki* her *.cs* dosyasını DoNotBuild.cs dosya dışında CSFile öğe türüne ekler.

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 Öznitelik, `Exclude` yalnızca her ikisini de `Include` içeren madde öğesindeki öznitelik tarafından eklenen öğeleri etkiler. Aşağıdaki örnek, önceki öğe öğesine eklenen dosya *Form1.cs*hariç tutmaz.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Daha fazla bilgi için [bkz.](../msbuild/how-to-exclude-files-from-the-build.md)

## <a name="item-metadata"></a>Madde meta verileri

 Öğeler, `Include` `Exclude` özniteliklerdeki bilgilere ek olarak meta veriler içerebilir. Bu meta veriler, öğeler hakkında daha fazla bilgi gerektiren görevler veya toplu iş görevleri ve hedefler için kullanılabilir. Daha fazla bilgi için [Toplu İşlem'e](../msbuild/msbuild-batching.md)bakın.

 Meta veriler, proje dosyasında bir öğe öğesinin alt öğeleri olarak bildirilen anahtar değer çiftleri topluluğudur. Alt öğenin adı meta verilerin adıdır ve alt öğenin değeri meta verilerin değeridir.

 Meta veri, onu içeren öğe öğesi ile ilişkilidir. Örneğin, aşağıdaki XML, `Culture` CSFile öğe `Fr` türünün hem *one.cs* hem de *two.cs* öğelerine değer içeren meta veriler ekler.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Bir öğe sıfır veya daha fazla meta veri değerine sahip olabilir. Meta veri değerlerini istediğiniz zaman değiştirebilirsiniz. Meta verileri boş bir değere ayarlarsanız, bu verileri yapıdan etkili bir şekilde kaldırırsınız.

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a>Proje dosyasındaki başvuru öğesi meta verileri

 Sözdizimi %(ItemMetadataName\<>) kullanarak proje dosyası boyunca madde meta verilerine başvuruyapabilirsiniz. Belirsizlik varsa, madde türünün adını kullanarak bir başvuruyu hak kazanabilirsiniz. Örneğin, %(ItemType.ItemMetaDataName\<>) belirtebilirsiniz. Aşağıdaki örnek, İleti görevini toplu olarak almak için Görüntü meta verilerini kullanır. Toplu iş için madde meta verilerinin nasıl kullanılacağı hakkında daha fazla bilgi [için, görev toplu işlerinde Madde meta verilerine](../msbuild/item-metadata-in-task-batching.md)bakın.

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

### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a>İyi bilinen öğe meta verileri

 Bir öğe bir öğe türüne eklendiğinde, bu öğeye iyi bilinen bazı meta veriler atanır. Örneğin, tüm öğeler, değeri öğenin dosya\<adı (uzantısı olmadan) olan iyi bilinen meta veri %(Filename>) vardır. Daha fazla bilgi için, [bilinen öğe meta verilerine](../msbuild/msbuild-well-known-item-metadata.md)bakın.

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a>Meta verileri kullanarak madde türlerini dönüştürme

 Meta verileri kullanarak madde listelerini yeni madde listelerine dönüştürebilirsiniz. Örneğin, *.cpp* dosyalarını `CppFiles` temsil eden öğeleri olan bir madde türünü ifadeyi `@(CppFiles -> '%(Filename).obj')`kullanarak *.obj* dosyalarının karşılık gelen listesine dönüştürebilirsiniz.

 Aşağıdaki kod, meta `CultureResource` verileri olan `EmbeddedResource` `Culture` tüm öğelerin kopyalarını içeren bir madde türü oluşturur. Meta `Culture` veri değeri yeni meta verilerin `CultureResource.TargetDirectory`değeri olur.

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

 Daha fazla bilgi için [Transforms'a](../msbuild/msbuild-transforms.md)bakın.

## <a name="item-definitions"></a>Madde tanımları

 .NET Framework 3.5'ten başlayarak, [ItemDefinitionGroup öğesini](../msbuild/itemdefinitiongroup-element-msbuild.md)kullanarak herhangi bir madde türüne varsayılan meta veri ekleyebilirsiniz. İyi bilinen meta veriler gibi, varsayılan meta veriler de belirttiğiniz madde türündeki tüm öğelerle ilişkilidir. Madde tanımında varsayılan meta verileri açıkça geçersiz kılabilirsiniz. Örneğin, aşağıdaki XML `Compile` öğeleri *one.cs* verir ve "Pazartesi" değeri ile meta verileri `BuildDay` *three.cs.* Kod, *öğeye* "Salı" `BuildDay` değeriyle meta verileri two.cs verir.

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

 Daha fazla bilgi için [Madde tanımlarına](../msbuild/item-definitions.md)bakın.

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Hedefin ItemGroup'undaki öğelerin öznitelikleri

 .NET Framework 3.5'ten `Target` başlayarak, öğeler öğe öğeleri içerebilecek [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğeleri içerebilir. Bu bölümdeki öznitelikler, bir `ItemGroup` `Target`'de bulunan bir madde için belirtildiğinde geçerlidir.

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a>Özniteliği kaldırma

 Öznitelik, `Remove` öğe türünden belirli öğeleri (dosyaları) kaldırır. Bu özellik .NET Framework 3.5'te (yalnızca içerideki hedefler) tanıtıldı. MSBuild 15.0'dan başlayarak hem iç hem de dış hedefler desteklenir.

 Aşağıdaki örnek, Derleme öğesi türünden her *.config* dosyasını kaldırır.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a>Meta veri özniteliğini koru

 Bir öğe bir hedef içinde oluşturulursa, `KeepMetadata` öğe öğesi özniteliği içerebilir. Bu öznitelik belirtilirse, yalnızca yarı sütunlu sınırlı adlar listesinde belirtilen meta veriler kaynak öğeden hedef öğeye aktarılır. Bu öznitelik için boş bir değer belirtmemeye eşdeğerdir. Öznitelik `KeepMetadata` .NET Framework 4.5'te tanıtıldı.

 Aşağıdaki örnek, özniteliğin `KeepMetadata` nasıl kullanılacağını göstermektedir.

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

### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a>KaldırmaMetaveri özniteliği

 Bir öğe bir hedef içinde oluşturulursa, `RemoveMetadata` öğe öğesi özniteliği içerebilir. Bu öznitelik belirtilirse, adları yarı sütunlu sınırlı adlar listesinde bulunan meta veriler dışında tüm meta veriler kaynak öğeden hedef öğeye aktarılır. Bu öznitelik için boş bir değer belirtmemeye eşdeğerdir. Öznitelik `RemoveMetadata` .NET Framework 4.5'te tanıtıldı.

 Aşağıdaki örnek, özniteliğin `RemoveMetadata` nasıl kullanılacağını göstermektedir.

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

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a>KeepDuplicates özniteliği

 Bir öğe bir hedef içinde oluşturulursa, `KeepDuplicates` öğe öğesi özniteliği içerebilir. `KeepDuplicates`öğe `Boolean` varolan bir öğenin tam bir kopyasıysa, bir öğenin hedef gruba eklenip eklenmeyeceğini belirten bir özniteliktir.

 Kaynak ve hedef öğe aynı Include değerine sahipse, ancak `KeepDuplicates` farklı meta `false`veriler varsa, öğe ' ye ayarlanmış olsa bile eklenir. Bu öznitelik için boş bir değer belirtmemeye eşdeğerdir. Öznitelik `KeepDuplicates` .NET Framework 4.5'te tanıtıldı.

 Aşağıdaki örnek, özniteliğin `KeepDuplicates` nasıl kullanılacağını göstermektedir.

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

## <a name="see-also"></a>Ayrıca bkz.

- [Öğe öğesi (MSBuild)](../msbuild/item-element-msbuild.md)
- [Ortak MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Msbuild](../msbuild/msbuild.md)
- [Nasıl yapılsın: Oluşturmak için dosyaları seçin](../msbuild/how-to-select-the-files-to-build.md)
- [Nasıl yapılı: Dosyaları yapıdan hariç tutma](../msbuild/how-to-exclude-files-from-the-build.md)
- [Nasıl yapılsın: Virgülle ayrılmış bir öğe listesini görüntüleme](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Madde tanımları](../msbuild/item-definitions.md)
- [İşlem grubu oluşturma](../msbuild/msbuild-batching.md)
