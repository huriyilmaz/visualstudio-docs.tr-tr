---
title: Öğe Öğesi (MSBuild) | Microsoft Dokümanlar
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff7e446c319a08004260125580cdace43412cdba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169358"
---
# <a name="item-element-msbuild"></a>Öğe öğesi (MSBuild)

Kullanıcı tanımlı bir öğe ve meta verilerini içerir. BIR MSBuild projesinde kullanılan her öğe, bir `ItemGroup` öğenin alt öğesi olarak belirtilmelidir.

\<Proje \<> ItemGroup> \<Madde>

## <a name="syntax"></a>Sözdizimi

```xml
<Item Include="*.cs"
        Exclude="MyFile.cs"
        Condition="'String A'=='String B'">
    <ItemMetadata1>...</ItemMetadata1>
    <ItemMetadata2>...</ItemMetadata2>
</Item>
```

## <a name="specify-metadata-as-attributes"></a>Meta verileri öznitelik olarak belirtin

MSBuild 15.1 veya sonraki durumlarda, geçerli öznitelik listesiyle çakışmayan bir ada sahip herhangi bir meta veri isteğe bağlı olarak bir öznitelik olarak ifade edilebilir.

Örneğin, NuGet paketlerinin listesini belirtmek için normalde aşağıdaki sözdizimi gibi bir şey kullanırsınız.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Ancak şimdi, `Version` meta verileri aşağıdaki sözdiziminde olduğu gibi bir öznitelik olarak geçirebilirsiniz:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Include`|İsteğe bağlı öznitelik.<br /><br /> Öğeler listesine dahil edilen dosya veya joker karakter.|
|`Exclude`|İsteğe bağlı öznitelik.<br /><br /> Öğeler listesinden hariç tutmak için dosya veya joker karakter.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek durum. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|
|`Remove`|İsteğe bağlı öznitelik.<br /><br /> Öğeler listesinden kaldırılacak dosya veya joker karakter.<br /><br />|
|`KeepDuplicates`|İsteğe bağlı öznitelik.<br /><br /> Varolan bir öğenin tam kopyasıysa, bir öğenin hedef gruba eklenip eklenmeyeceğini belirtir. Kaynak ve hedef öğe aynı `Include` değere sahipse ancak farklı `KeepDuplicates` meta verilere `false`sahipse, madde . Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.<br /><br /> Bu öznitelik, yalnızca bir `ItemGroup` `Target`'de bulunan bir madde için belirtilmişse geçerlidir.|
|`KeepMetadata`|İsteğe bağlı öznitelik.<br /><br /> Hedef öğelere eklenecek kaynak öğeleriçin meta veriler. Yalnızca yarı sütunlu sınırlı listede adları belirtilen meta veriler bir kaynak öğeden hedef öğeye aktarılır. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.<br /><br /> Bu öznitelik, yalnızca bir `ItemGroup` `Target`'de bulunan bir madde için belirtilmişse geçerlidir.|
|`RemoveMetadata`|İsteğe bağlı öznitelik.<br /><br /> Kaynak maddelerin hedef maddelere aktarılmayan meta verileri. Tüm meta veriler, adları yarı sütunlu sınırlı adlar listesinde bulunan meta veriler dışında bir kaynak öğeden hedef öğeye aktarılır. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.<br /><br /> Bu öznitelik, yalnızca bir `ItemGroup` `Target`'de bulunan bir madde için belirtilmişse geçerlidir.|
|`Update`|İsteğe bağlı öznitelik. (Visual Studio 2017 veya sonraki yıllarda sadece .NET Core projeleri için kullanılabilir.)<br /><br /> Glob kullanılarak eklenen bir dosyanın meta verilerini değiştirmenizi sağlar.<br /><br /> Bu öznitelik, yalnızca bir `ItemGroup` `Target`'de olmayan bir madde için belirtilmişse geçerlidir.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Madde meta veri değerini içeren kullanıcı tanımlı madde meta veri anahtarı. Bir öğede sıfır `ItemMetadata` veya daha fazla öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ıtemgroup](../msbuild/itemgroup-element-msbuild.md)|Öğeler için gruplandırma öğesi.|

## <a name="remarks"></a>Açıklamalar

`Item`öğeler yapı sistemine girişleri tanımlar ve kullanıcı tanımlı koleksiyon adlarına göre madde koleksiyonlarına gruplanır. Bu madde koleksiyonları, yapı işleminin adımlarını gerçekleştirmek için koleksiyonlarda tek tek öğeleri kullanan [görevler](../msbuild/msbuild-tasks.md)için parametre olarak kullanılabilir. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.

@(myType\<>) notunu kullanmak, myType> \<türündeki öğelerin bir koleksiyonunun yarı sütunlu dizeler listesine genişletilmesini ve bir parametreye geçirilmesini sağlar. Parametre türündeise, `string`parametrenin değeri yarım nokta nokta ile ayrılmış öğelerin listesidir. Parametre dizeleri bir dizi ise`string[]`( ), sonra her öğe yarım iki nokta üzerinde konuma göre dizi içine eklenir. Görev parametresi türdeyse, <xref:Microsoft.Build.Framework.ITaskItem> `[]`değer madde koleksiyonunun içeriği ve ekli herhangi bir meta veridir. Her öğeyi yarı sütun dışında bir karakter kullanarak sınırlamak için\<@(myType\<>, ' ayırıcı>' sözdizimini kullanın.

MSBuild altyapısı gibi joker karakterleri `*` `?` ve * / \* \* / \*.cs*gibi özyinelemeli joker karakterleri değerlendirebilir. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.

## <a name="examples"></a>Örnekler

Aşağıdaki kod örneği, iki tür `CSFile`öğenin nasıl bildirilen gösterir. İkinci bildirilen öğe, '' `MyMetadata` olarak `HelloWorld`ayarlanmış meta verileri içerir.

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

Aşağıdaki kod örneği, glob `Update` yoluyla eklenen *somefile.cs* adlı bir dosyadaki meta verileri değiştirmek için özniteliğin nasıl kullanılacağını gösterir. (Visual Studio 2017 veya sonraki yıllarda sadece .NET Core projeleri için kullanılabilir.)

```xml
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Öğeler](../msbuild/msbuild-items.md)
- [Ortak MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
