---
title: MSBuild öğeleri | Microsoft Docs
description: Bir yapıya dahil edilecek dosyaları belirtmek için ItemGroup 'un MSBuild Include özniteliğini kullanın
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
ms.openlocfilehash: a8ed6b9789569e9f68706a5b132aa9000b25d910
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590650"
---
# <a name="msbuild-items"></a>MSBuild öğeleri
MSBuild öğeleri, derleme sistemine giriş gösterir ve genellikle dosyaları temsil eder (dosyalar `Include` özniteliğinde belirtilir). Öğeler öğe adlarına göre öğe türlerine gruplanır. Öğe türleri, görevler için parametre olarak kullanılabilecek öğelerin adlandırılmış listeleridir. Görevler, yapı işleminin adımlarını gerçekleştirmek için öğe değerlerini kullanır.

 Öğeler ait oldukları öğe türüne göre adlandırıldıklarından, "öğe" ve "öğe değeri" terimleri birbirlerinin yerine kullanılabilir.

## <a name="create-items-in-a-project-file"></a>Proje dosyasında öğe oluşturma
 Öğeleri proje dosyasında bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğeleri olarak bildirirsiniz. Alt öğenin adı öğenin türüdür. Öğesinin `Include` özniteliği, bu öğe türüne dahil edilecek öğeleri (dosyalar) belirtir. Örneğin, aşağıdaki XML iki dosya içeren `Compile`adlı bir öğe türü oluşturur.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Öğe *File2.cs* öğenin yerini almaz *File1.cs*; Bunun yerine, dosya adı `Compile` öğesi türü için değerler listesine eklenir.

 Aşağıdaki XML, her iki dosyayı da bir `Include` özniteliğinde bildirerek aynı öğe türünü oluşturur. Dosya adlarının noktalı virgülle ayrıldığına dikkat edin.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

## <a name="create-items-during-execution"></a>Yürütme sırasında öğe oluşturma
 [Hedef](../msbuild/target-element-msbuild.md) öğelerin dışında kalan öğelere, bir yapı değerlendirme aşamasında değerler atanır. Sonraki yürütme aşamasında, öğeler aşağıdaki yollarla oluşturulabilir veya değiştirilebilir:

- Herhangi bir görev bir öğeyi yayabilir. Bir öğeyi oluşturmak için, [görev](../msbuild/task-element-msbuild.md) öğesinin bir `ItemName` özniteliğine sahip bir alt [Çıkış](../msbuild/output-element-msbuild.md) öğesi olması gerekir.

- [CreateItem](../msbuild/createitem-task.md) görevi bir öğeyi yayabilir. Bu kullanım önerilmiyor.

- .NET Framework 3,5 ' den başlayarak `Target` öğeler, öğe öğeleri içerebilen [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğelerini içerebilir.

## <a name="reference-items-in-a-project-file"></a>Proje dosyasındaki başvuru öğeleri
 Proje dosyası boyunca öğe türlerine başvurmak için @ (\<ItemType >) sözdizimini kullanırsınız. Örneğin, `@(Compile)`kullanarak önceki örnekteki öğe türüne başvurabilirsiniz. Bu söz dizimini kullanarak, öğe türünü bu görevin parametresi olarak belirterek öğeleri görevlere geçirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: derlenecek dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).

 Varsayılan olarak, bir öğe türünün öğeleri noktalı virgülle ayrılır (;) genişletilmişse. Varsayılan dışında bir ayırıcı belirtmek için @ (\<ItemType >, '\<separator > ') sözdizimini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme](../msbuild/how-to-display-an-item-list-separated-with-commas.md).

## <a name="use-wildcards-to-specify-items"></a>Öğeleri belirtmek için joker karakterler kullanın

Bir dosya grubunu her dosyayı ayrı olarak listelemek yerine bir derleme için giriş olarak belirtmek için `**`, `*`ve `?` joker karakterlerini kullanabilirsiniz.

- `?` joker karakteri tek bir karakterle eşleşiyor.
- `*` joker karakteri sıfır veya daha fazla karakterle eşleşiyor.
- `**` joker karakter sırası kısmi bir yol ile eşleşiyor.

Örneğin, proje dosyanızda aşağıdaki öğesini kullanarak proje dosyasını içeren dizindeki tüm `.cs` dosyalarını belirtebilirsiniz.

```xml
<CSFile Include="*.cs"/>
```

Aşağıdaki öğe `D:` sürücüsündeki tüm `.vb` dosyalarını seçer:

```xml
<VBFile Include="D:/**/*.vb"/>
```

Joker karakter genişletme olmadan bir öğeye sabit `*` veya `?` karakterleri eklemek istiyorsanız, [joker karakterleri atlamanız](../msbuild/how-to-escape-special-characters-in-msbuild.md)gerekir.

Joker karakterler hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturulacak dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).

## <a name="use-the-exclude-attribute"></a>Exclude özniteliğini kullanma
 Öğe öğeleri, belirli öğeleri (dosyaları) öğe türünden dışlayan `Exclude` özniteliğini içerebilir. `Exclude` özniteliği genellikle joker karakterlerle birlikte kullanılır. Örneğin, aşağıdaki XML, dizinindeki her *. cs* dosyasını *DoNotBuild.cs* dosyası hariç CSFile öğe türüne ekler.

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 `Exclude` özniteliği, yalnızca bunları içeren item öğesinde `Include` özniteliği tarafından eklenen öğeleri etkiler. Aşağıdaki örnek, önceki item öğesine eklenen *Form1.cs*dosyasını dışlayamazsınız.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Daha fazla bilgi için bkz. [nasıl yapılır: derlemeden dosya çıkarma](../msbuild/how-to-exclude-files-from-the-build.md).

## <a name="item-metadata"></a>Öğe meta verileri
 Öğeler `Include` ve `Exclude` özniteliklerindeki bilgilere ek olarak meta veriler içerebilir. Bu meta veriler, öğeler veya toplu görevler ve hedefler hakkında daha fazla bilgi gerektiren görevler tarafından kullanılabilir. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.

 Meta veri, proje dosyasında bir öğe öğesinin alt öğeleri olarak belirtilen anahtar-değer çiftleri koleksiyonudur. Alt öğenin adı, meta verilerin adıdır ve alt öğenin değeri meta verilerin değeridir.

 Meta veriler, kendisini içeren öğe öğesiyle ilişkilendirilir. Örneğin, aşağıdaki XML, hem *One.cs* hem de CSFile öğe türünün *Two.cs* öğelerine `Fr` değeri olan `Culture` meta verileri ekler.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Bir öğe sıfır veya daha fazla meta veri değerine sahip olabilir. Meta veri değerlerini dilediğiniz zaman değiştirebilirsiniz. Meta verileri boş bir değere ayarlarsanız derlemeden etkin bir şekilde kaldırırsınız.

### <a name="BKMK_ReferencingItemMetadata"></a>Proje dosyasındaki başvuru öğesi meta verileri
 Proje dosyasının tamamında,%(\<ItemMetaDataName >) sözdizimini kullanarak öğe meta verilerine başvurabilirsiniz. Belirsizlik varsa, öğe türü adını kullanarak bir başvuruyu niteleyebilirsiniz. Örneğin,%(\<ItemType. ItemMetaDataName >) belirtebilirsiniz. Aşağıdaki örnek, Ileti görevinin toplu işi için görüntüleme meta verilerini kullanır. Toplu işleme için öğe meta verilerini kullanma hakkında daha fazla bilgi için, bkz. [görev toplu işleme Içindeki öğe meta verileri](../msbuild/item-metadata-in-task-batching.md).

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

### <a name="BKMK_WellKnownItemMetadata"></a>İyi bilinen öğe meta verileri
 Öğe türüne bir öğe eklendiğinde, bu öğeye bazı iyi bilinen meta veriler atanır. Örneğin, tüm öğelerin, değeri öğenin dosya adı olan%(\<filename >) bilinen meta verileri vardır. Daha fazla bilgi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).

### <a name="BKMK_Transforming"></a>Meta verileri kullanarak öğe türlerini dönüştürme
 Meta verileri kullanarak öğe listelerini yeni öğe listelerine dönüştürebilirsiniz. Örneğin, *. cpp* dosyalarını temsil eden öğeler içeren bir öğe türü `CppFiles`, `@(CppFiles -> '%(Filename).obj')`ifadesini kullanarak. cpp dosyalarını karşılık gelen bir *. obj* dosyası listesine dönüştürebilirsiniz.

 Aşağıdaki kod, `Culture` meta verileri ile tüm `EmbeddedResource` öğelerinin kopyalarını içeren `CultureResource` bir öğe türü oluşturur. `Culture` meta veri değeri, yeni meta veri `CultureResource.TargetDirectory`değeri olur.

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

 Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).

## <a name="item-definitions"></a>Öğe tanımları
 3,5 .NET Framework başlayarak, [ItemDefinitionGroup öğesini](../msbuild/itemdefinitiongroup-element-msbuild.md)kullanarak herhangi bir öğe türüne varsayılan meta veri ekleyebilirsiniz. İyi bilinen meta veriler gibi, varsayılan meta veriler belirttiğiniz öğe türünün tüm öğeleriyle ilişkilendirilir. Bir öğe tanımında varsayılan meta verileri açıkça geçersiz kılabilirsiniz. Örneğin, aşağıdaki XML, *One.cs* ve *Three.cs* öğelerini, meta `BuildDay` verileri "Pazartesi" değeriyle `Compile` verir. Kod, *Two.cs* öğesini "Salı" değeriyle `BuildDay` meta veri olarak verir.

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
 .NET Framework 3,5 ' den başlayarak `Target` öğeler, öğe öğeleri içerebilen [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğelerini içerebilir. Bu bölümdeki öznitelikler, bir `Target``ItemGroup` bir öğe için belirtildiğinde geçerlidir.

### <a name="BKMK_RemoveAttribute"></a>Özniteliği kaldır
 `Remove` özniteliği, öğe türünden belirli öğeleri (dosyaları) kaldırır. Bu öznitelik .NET Framework 3,5 ' de tanıtılmıştı (yalnızca hedefler içinde). Hem iç hem de dış hedefler, MSBuild 15,0 ' den itibaren desteklenmektedir.

 Aşağıdaki örnek, derleme öğesi türünden her *. config* dosyasını kaldırır.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="BKMK_KeepMetadata"></a>KeepMetadata özniteliği
 Bir hedef içinde bir öğe oluşturulduysa, öğe öğesi `KeepMetadata` özniteliğini içerebilir. Bu öznitelik belirtilmişse, yalnızca noktalı virgülle ayrılmış ad listesinde belirtilen meta veriler, kaynak öğeden hedef öğeye aktarılır. Bu öznitelik için boş bir değer, Belirtmemeye eşdeğerdir. `KeepMetadata` özniteliği .NET Framework 4,5 ' de tanıtılmıştı.

 Aşağıdaki örnekte `KeepMetadata` özniteliğinin nasıl kullanılacağı gösterilmektedir.

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

### <a name="BKMK_RemoveMetadata"></a>RemoveMetadata özniteliği
 Bir hedef içinde bir öğe oluşturulduysa, öğe öğesi `RemoveMetadata` özniteliğini içerebilir. Bu öznitelik belirtilmişse, tüm meta veriler kaynak öğeden, adları noktalı virgülle ayrılmış ad listesinde yer alan meta veriler hariç hedef öğeye aktarılır. Bu öznitelik için boş bir değer, Belirtmemeye eşdeğerdir. `RemoveMetadata` özniteliği .NET Framework 4,5 ' de tanıtılmıştı.

 Aşağıdaki örnekte `RemoveMetadata` özniteliğinin nasıl kullanılacağı gösterilmektedir.

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

### <a name="BKMK_KeepDuplicates"></a>Mi Pduplilıları özniteliği
 Bir hedef içinde bir öğe oluşturulduysa, öğe öğesi `KeepDuplicates` özniteliğini içerebilir. `KeepDuplicates`, öğe var olan bir öğenin tam yinelemesi ise, bir öğenin hedef gruba eklenip eklenmeyeceğini belirten bir `Boolean` özniteliğidir.

 Kaynak ve hedef öğe aynı ekleme değerine ancak farklı meta verilere sahip ise, `KeepDuplicates` `false`olarak ayarlanmış olsa bile öğe eklenir. Bu öznitelik için boş bir değer, Belirtmemeye eşdeğerdir. `KeepDuplicates` özniteliği .NET Framework 4,5 ' de tanıtılmıştı.

 Aşağıdaki örnekte `KeepDuplicates` özniteliğinin nasıl kullanılacağı gösterilmektedir.

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
- [Item öğesi (MSBuild)](../msbuild/item-element-msbuild.md)
- [Ortak MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Nasıl yapılır: derlenecek dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md)
- [Nasıl yapılır: derlemeden Dosya dışlama](../msbuild/how-to-exclude-files-from-the-build.md)
- [Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Öğe tanımları](../msbuild/item-definitions.md)
- [Toplu İşleme](../msbuild/msbuild-batching.md)
