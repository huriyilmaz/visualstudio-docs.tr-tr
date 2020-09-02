---
title: MSBuild öğeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19f22fc56881287cfb501143aaa4397f9a035d78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821642"
---
# <a name="msbuild-items"></a>MSBuild Öğeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild öğeleri, derleme sistemine giriş gösterir ve genellikle dosyaları temsil eder. Öğeler öğe adlarına göre öğe türlerine gruplanır. Öğe türleri, görevler için parametre olarak kullanılabilecek öğelerin adlandırılmış listeleridir. Görevler, yapı işleminin adımlarını gerçekleştirmek için öğe değerlerini kullanır.  
  
 Öğeler ait oldukları öğe türüne göre adlandırıldıklarından, "öğe" ve "öğe değeri" terimleri birbirlerinin yerine kullanılabilir.  
  
 **Bu konuda**  
  
- [Proje dosyasında öğe oluşturma](#BKMK_Creating1)  
  
- [Yürütme sırasında öğe oluşturma](#BKMK_Creating2)  
  
- [Proje dosyasındaki öğelere başvurma](#BKMK_ReferencingItems)  
  
- [Öğeleri belirtmek için joker karakterler kullanma](#BKMK_Wildcards)  
  
- [Exclude özniteliğini kullanma](#BKMK_ExcludeAttribute)  
  
- [Öğe meta verileri](#BKMK_ItemMetadata)  
  
  - [Proje dosyasındaki öğe meta verilerine başvurma](#BKMK_ReferencingItemMetadata)  

  - [Tanınmış Öğe Meta Verisi](#BKMK_WellKnownItemMetadata)  

  - [Meta verileri kullanarak öğe türlerini dönüştürme](#BKMK_Transforming)  
  
- [Öğe tanımları](#BKMK_ItemDefinitions)  
  
- [Bir hedefin ItemGroup 'lerindeki öğelerin öznitelikleri](#BKMK_AttributesWithinTargets)  
  
  - [Özniteliği kaldır](#BKMK_RemoveAttribute)  

  - [KeepMetadata özniteliği](#BKMK_KeepMetadata)  

  - [RemoveMetadata özniteliği](#BKMK_RemoveMetadata)  

  - [Mi Pduplilıları özniteliği](#BKMK_KeepDuplicates)  
  
## <a name="creating-items-in-a-project-file"></a><a name="BKMK_Creating1"></a> Proje dosyasında öğe oluşturma  
 Öğeleri proje dosyasında bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğeleri olarak bildirirsiniz. Alt öğenin adı öğenin türüdür. `Include`Öğesinin özniteliği, bu öğe türüne dahil edilecek öğeleri (dosyaları) belirtir. Örneğin, aşağıdaki XML iki dosya içeren adlı bir öğe türü oluşturur `Compile` .  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 "File2.cs" öğesi "file1.cs" öğesinin yerini almaz; Bunun yerine, dosya adı öğe türü için değerler listesine eklenir `Compile` . Bir derlemeyi değerlendirme aşamasında bir öğe türünden kaldıramazsınız.  
  
 Aşağıdaki XML, her iki dosyayı tek bir öznitelikte bildirerek aynı öğe türünü oluşturur `Include` . Dosya adlarının noktalı virgülle ayrıldığına dikkat edin.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
## <a name="creating-items-during-execution"></a><a name="BKMK_Creating2"></a> Yürütme sırasında öğe oluşturma  
 [Hedef](../msbuild/target-element-msbuild.md) öğelerin dışında kalan öğelere, bir yapı değerlendirme aşamasında değerler atanır. Sonraki yürütme aşamasında, öğeler aşağıdaki yollarla oluşturulabilir veya değiştirilebilir:  
  
- Herhangi bir görev bir öğeyi yayabilir. Bir öğeyi oluşturmak için, [görev](../msbuild/task-element-msbuild.md) öğesinin bir özniteliği olan bir alt [Çıkış](../msbuild/output-element-msbuild.md) öğesi olması gerekir `ItemName` .  
  
- [CreateItem](../msbuild/createitem-task.md) görevi bir öğeyi yayabilir. Bu kullanım önerilmiyor.  
  
- .NET Framework 3,5 ' den başlayarak `Target` öğeler, öğe öğeleri Içerebilen [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğeleri içerebilir.  
  
## <a name="referencing-items-in-a-project-file"></a><a name="BKMK_ReferencingItems"></a> Proje dosyasındaki öğelere başvurma  
 Proje dosyası boyunca öğe türlerine başvurmak için @ () söz dizimini kullanın `ItemType` . Örneğin, kullanarak önceki örnekteki öğe türüne başvurarak `@(Compile)` . Bu söz dizimini kullanarak, öğe türünü bu görevin parametresi olarak belirterek öğeleri görevlere geçirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: derlenecek dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).  
  
 Varsayılan olarak, bir öğe türünün öğeleri noktalı virgülle ayrılır (;) genişletilmişse. Varsayılan dışında bir ayırıcı belirtmek için @ (*ItemType*, '*separator*') sözdizimini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
## <a name="using-wildcards-to-specify-items"></a><a name="BKMK_Wildcards"></a> Öğeleri belirtmek için joker karakterler kullanma  
 * *,, Ve kullanın. \* bir dosya grubunu, her dosyayı ayrı olarak listelemek yerine bir derleme için giriş olarak belirtmek için joker karakterler.  
  
- ? işareti joker karakter tek bir karakterle eşleşiyor.  
  
- * Joker karakteri sıfır veya daha fazla karakterle eşleşiyor.  
  
- * * Joker karakter dizisi kısmi bir yolla eşleşir.  
  
  Örneğin, proje dosyanızda aşağıdaki öğesini kullanarak proje dosyasını içeren dizindeki tüm. cs dosyalarını belirtebilirsiniz.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 Aşağıdaki öğe D: sürücüsündeki tüm. vb dosyalarını seçer:  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Joker karakterler hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturulacak dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).  
  
## <a name="using-the-exclude-attribute"></a><a name="BKMK_ExcludeAttribute"></a> Exclude özniteliğini kullanma  
 Öğe öğeleri `Exclude` , belirli öğeleri (dosyaları) öğe türünden dışlayan özniteliği içerebilir. `Exclude`Özniteliği genellikle joker karakterlerle birlikte kullanılır. Örneğin, aşağıdaki XML, dizin içindeki her. cs dosyasını dosya dışında CSFile öğe türüne ekler `DoNotBuild.cs` .  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 `Exclude`Özniteliği yalnızca, `Include` her ikisini de içeren öğe öğesindeki özniteliği tarafından eklenen öğeleri etkiler. Aşağıdaki örnek, önceki item öğesine eklenen Form1.cs dosyasını dışlayamazsınız.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: derlemeden dosya çıkarma](../msbuild/how-to-exclude-files-from-the-build.md).  
  
## <a name="item-metadata"></a><a name="BKMK_ItemMetadata"></a> Öğe meta verileri  
 Öğeler `Include` ve özniteliklerindeki bilgilere ek olarak meta veriler içerebilir `Exclude` . Bu meta veriler, öğeler veya toplu görevler ve hedefler hakkında daha fazla bilgi gerektiren görevler tarafından kullanılabilir. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.  
  
 Meta veri, proje dosyasında bir öğe öğesinin alt öğeleri olarak belirtilen anahtar-değer çiftleri koleksiyonudur. Alt öğenin adı, meta verilerin adıdır ve alt öğenin değeri meta verilerin değeridir.  
  
 Meta veriler, kendisini içeren öğe öğesiyle ilişkilendirilir. Örneğin, aşağıdaki XML, değeri olan `Culture` meta verileri `Fr` hem "One.cs" hem de CSFile öğe türünün "Two.cs" öğelerine ekler.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Bir öğe sıfır veya daha fazla meta veri değerine sahip olabilir. Meta veri değerlerini dilediğiniz zaman değiştirebilirsiniz. Meta verileri boş bir değere ayarlarsanız derlemeden etkin bir şekilde kaldırırsınız.  
  
### <a name="referencing-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Proje dosyasındaki öğe meta verilerine başvurma  
 Proje dosyasının tamamında,%() sözdizimini kullanarak öğe meta verilerine başvurabilirsiniz `ItemMetadataName` . Belirsizlik varsa, öğe türü adını kullanarak bir başvuruyu niteleyebilirsiniz. Örneğin,%(*ItemType. ItemMetaDataName*) belirtebilirsiniz. Aşağıdaki örnek, Ileti görevinin toplu işi için görüntüleme meta verilerini kullanır. Toplu işleme için öğe meta verilerini kullanma hakkında daha fazla bilgi için, bkz. [görev toplu işleme Içindeki öğe meta verileri](../msbuild/item-metadata-in-task-batching.md).  
  
```  
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
 Öğe türüne bir öğe eklendiğinde, bu öğeye bazı iyi bilinen meta veriler atanır. Örneğin, tüm öğeler, `%(Filename)` değeri öğenin dosya adı olan iyi bilinen meta verilere sahiptir. Daha fazla bilgi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).  
  
### <a name="transforming-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Meta verileri kullanarak öğe türlerini dönüştürme  
 Meta verileri kullanarak öğe listelerini yeni öğe listelerine dönüştürebilirsiniz. Örneğin, `CppFiles` . cpp dosyalarını temsil eden öğeler içeren bir öğe türünü, ifadesini kullanarak. cpp dosyalarını karşılık gelen bir. obj dosyası listesine dönüştürebilirsiniz `@(CppFiles -> '%(Filename).obj')` .  
  
 Aşağıdaki kod, `CultureResource` `EmbeddedResource` meta verileri olan tüm öğelerin kopyalarını içeren bir öğe türü oluşturur `Culture` . `Culture`Meta veri değeri, yeni meta verilerin değeri olur `CultureResource.TargetDirectory` .  
  
```  
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
  
## <a name="item-definitions"></a><a name="BKMK_ItemDefinitions"></a> Öğe tanımları  
 3,5 .NET Framework başlayarak, [ItemDefinitionGroup öğesini](../msbuild/itemdefinitiongroup-element-msbuild.md)kullanarak herhangi bir öğe türüne varsayılan meta veri ekleyebilirsiniz. İyi bilinen meta veriler gibi, varsayılan meta veriler belirttiğiniz öğe türünün tüm öğeleriyle ilişkilendirilir. Bir öğe tanımında varsayılan meta verileri açıkça geçersiz kılabilirsiniz. Örneğin, aşağıdaki XML " `Compile` One.cs" ve "Three.cs" öğelerini `BuildDay` "Pazartesi" değerine sahip meta verileri sağlar. Kod, "two.cs" öğesini `BuildDay` "Salı" değerine sahip meta veriler olarak verir.  
  
```  
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
  
## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a><a name="BKMK_AttributesWithinTargets"></a> Bir hedefin ItemGroup 'lerindeki öğelerin öznitelikleri  
 .NET Framework 3,5 ' den başlayarak `Target` öğeler, öğe öğeleri Içerebilen [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğeleri içerebilir. Bu bölümdeki öznitelikler, içindeki bir öğesi için belirtildiğinde geçerlidir `ItemGroup` `Target` .  
  
### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Özniteliği kaldır  
 `ItemGroup`Bir hedefin içindeki öğeler `Remove` , öğe türünden belirli öğeleri (dosyaları) kaldıran özniteliğini içerebilir. Bu öznitelik .NET Framework 3,5 ' de tanıtılmıştı.  
  
 Aşağıdaki örnek, derleme öğesi türünden her. config dosyasını kaldırır.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> KeepMetadata özniteliği  
 Bir hedef içinde bir öğe oluşturulduysa, öğe öğesi `KeepMetadata` özniteliğini içerebilir. Bu öznitelik belirtilmişse, yalnızca noktalı virgülle ayrılmış ad listesinde belirtilen meta veriler, kaynak öğeden hedef öğeye aktarılır. Bu öznitelik için boş bir değer, Belirtmemeye eşdeğerdir. `KeepMetadata`Öznitelik .NET Framework 4,5 ' de tanıtılmıştı.  
  
 Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir `KeepMetadata` .  
  
```  
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
 Bir hedef içinde bir öğe oluşturulduysa, öğe öğesi `RemoveMetadata` özniteliğini içerebilir. Bu öznitelik belirtilmişse, tüm meta veriler kaynak öğeden, adları noktalı virgülle ayrılmış ad listesinde yer alan meta veriler hariç hedef öğeye aktarılır. Bu öznitelik için boş bir değer, Belirtmemeye eşdeğerdir. `RemoveMetadata`Öznitelik .NET Framework 4,5 ' de tanıtılmıştı.  
  
 Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir `RemoveMetadata` .  
  
```  
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
  
### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> Mi Pduplilıları özniteliği  
 Bir hedef içinde bir öğe oluşturulduysa, öğe öğesi `KeepDuplicates` özniteliğini içerebilir. `KeepDuplicates` öğe, `Boolean` varolan bir öğenin tam yinelemesi ise, bir öğenin hedef gruba eklenip eklenmeyeceğini belirten bir özniteliktir.  
  
 Kaynak ve hedef öğe aynı ekleme değerine ancak farklı meta verilere sahip ise, olarak ayarlanmış olsa bile öğe eklenir `KeepDuplicates` `false` . Bu öznitelik için boş bir değer, Belirtmemeye eşdeğerdir. `KeepDuplicates`Öznitelik .NET Framework 4,5 ' de tanıtılmıştı.  
  
 Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir `KeepDuplicates` .  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)  
 [MSBUILD](msbuild.md)   
 [Nasıl yapılır: derlenecek dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md)   
 [Nasıl yapılır: derlemeden Dosya dışlama](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Öğe tanımları](../msbuild/item-definitions.md)   
 [İşlem](../msbuild/msbuild-batching.md)   
 [Öğe Unsuru (MSBuild)](../msbuild/item-element-msbuild.md)
