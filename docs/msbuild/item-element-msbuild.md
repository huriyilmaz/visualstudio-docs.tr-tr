---
title: Item öğesi (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 730e7d317ffa3fd5a450978f35659df3fe5629f3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573670"
---
# <a name="item-element-msbuild"></a>Item öğesi (MSBuild)
Kullanıcı tanımlı bir öğe ve onun meta verilerini içerir. Bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projesinde kullanılan her öğe, bir `ItemGroup` öğesinin alt öğesi olarak belirtilmelidir.

\<Proje > \<ItemGroup > \<öğesi >

## <a name="syntax"></a>Sözdizimi

```xml
<Item Include="*.cs"
        Exclude="MyFile.cs"
        Remove="RemoveFile.cs"
        Condition="'String A'=='String B'" >
    <ItemMetadata1>...</ItemMetadata1>
    <ItemMetadata2>...</ItemMetadata2>
</Item>
```

## <a name="specify-metadata-as-attributes"></a>Meta verileri öznitelik olarak belirt
MSBuild 15,1 veya sonraki sürümlerde, geçerli öznitelik listesiyle çakışmayan bir ada sahip tüm meta veriler, isteğe bağlı olarak bir öznitelik olarak ifade edilebilir.

Örneğin, NuGet paketlerinin listesini belirtmek için normalde aşağıdaki söz dizimi gibi bir şey kullanırsınız.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Ancak, `Version` meta verilerini aşağıdaki sözdiziminde olduğu gibi bir öznitelik olarak geçirebilirsiniz:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Include`|İsteğe bağlı öznitelik.<br /><br /> Öğe listesine dahil edilecek dosya veya joker karakter.|
|`Exclude`|İsteğe bağlı öznitelik.<br /><br /> Öğe listesinden dışlanacak dosya veya joker karakter.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|
|`Remove`|İsteğe bağlı öznitelik.<br /><br /> Öğe listesinden kaldırılacak dosya veya joker karakter.<br /><br />|
|`KeepDuplicates`|İsteğe bağlı öznitelik.<br /><br /> Bir öğenin, var olan bir öğenin tam yinelemesi olması halinde, hedef gruba eklenip eklenmeyeceğini belirtir. Kaynak ve hedef öğe aynı `Include` değerine sahip ancak farklı meta veriler içeriyorsa, `KeepDuplicates` `false`olarak ayarlanmış olsa bile öğe eklenir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca bir `Target`olan `ItemGroup` bir öğe için belirtilmişse geçerlidir.|
|`KeepMetadata`|İsteğe bağlı öznitelik.<br /><br /> Hedef öğelere eklenecek kaynak öğelerinin meta verileri. Yalnızca adları noktalı virgülle ayrılmış listede belirtilen meta veriler bir kaynak öğeden hedef öğeye aktarılır. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca bir `Target`olan `ItemGroup` bir öğe için belirtilmişse geçerlidir.|
|`RemoveMetadata`|İsteğe bağlı öznitelik.<br /><br /> Hedef öğelere aktarılamayan kaynak öğelerinin meta verileri. Tüm meta veriler, adları noktalı virgülle ayrılmış ad listesinde yer alan meta veriler hariç bir kaynak öğeden hedef öğeye aktarılır. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca bir `Target`olan `ItemGroup` bir öğe için belirtilmişse geçerlidir.|
|`Update`|İsteğe bağlı öznitelik. (Yalnızca Visual Studio 2017 veya üzeri sürümlerde .NET Core projeleri için kullanılabilir.)<br /><br /> Bir glob kullanılarak dahil edilen bir dosyanın meta verilerini değiştirmenize olanak sağlar.<br /><br /> Bu öznitelik yalnızca bir `Target`olmayan `ItemGroup` bir öğe için belirtilmişse geçerlidir.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Öğe meta veri değerini içeren Kullanıcı tanımlı öğe meta verileri anahtarı. Bir öğede sıfır veya daha fazla `ItemMetadata` öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Öğeler için gruplandırma öğesi.|

## <a name="remarks"></a>Açıklamalar
`Item` öğeleri, derleme sistemine girdileri tanımlar ve Kullanıcı tanımlı koleksiyon adlarına göre öğe koleksiyonları halinde gruplandırılır. Bu öğe koleksiyonları, yapı işlemi adımlarını gerçekleştirmek için koleksiyonlardaki ayrı öğeleri kullanan [Görevler](../msbuild/msbuild-tasks.md)için parametre olarak kullanılabilir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

@ (\<myType >) gösterimini kullanmak, \<myType > türünde öğelerin toplanmasını, noktalı virgülle ayrılmış dizeler listesine genişletmenizi ve bir parametreye geçirilmesini sağlar. Parametre `string`türünde ise, parametrenin değeri noktalı virgülle ayırarak öğelerin listesidir. Parametre bir dizeler diziyse (`string[]`), her öğe noktalı virgül konumunu temel alarak diziye eklenir. Görev parametresi <xref:Microsoft.Build.Framework.ITaskItem>`[]`türünde ise, değer, eklenen tüm meta verilerle birlikte öğe koleksiyonunun içeriğidir. Noktalı virgül dışında bir karakter kullanarak her öğeyi sınırlandırmak için @ (\<myType >, '\<separator > ') sözdizimini kullanın.

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] altyapısı, `*` ve `?` gibi joker karakterleri ve/\*\*/\* *. cs*gibi özyinelemeli joker karakterleri değerlendirebilir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

## <a name="examples"></a>Örnekler
Aşağıdaki kod örneği, `CSFile`türünde iki öğenin nasıl bildirilemeyeceğini gösterir. Belirtilen ikinci öğe, `HelloWorld`olarak ayarlanmış `MyMetadata` meta veriler içeriyor.

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

Aşağıdaki kod örneği, bir glob aracılığıyla eklenen *somefile.cs* adlı bir dosyadaki meta verileri değiştirmek için `Update` özniteliğinin nasıl kullanılacağını gösterir. (Yalnızca Visual Studio 2017 veya üzeri sürümlerde .NET Core projeleri için kullanılabilir.)

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
