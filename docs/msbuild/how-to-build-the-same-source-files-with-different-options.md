---
title: Aynı kaynak dosyalarını farklı seçeneklerle derleme
description: Farklı seçeneklerle aynı kaynak MSBuild oluşturmak için farklı derleme yapılandırmaları oluşturma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7892facb24caabe874e18773dd37996bad19f7a3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093781"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Nasıl kullanılır: Farklı seçeneklerle aynı kaynak dosyaları oluşturma

Projeleri derlerken, sık sık aynı bileşenleri farklı derleme seçenekleriyle derlersiniz. Örneğin, sembol bilgileriyle bir hata ayıklama derlemesi veya sembol bilgisi olan ancak iyileştirmeler etkinleştirilmiş bir yayın derlemesi oluşturabilirsiniz. Veya x86 veya x64 gibi belirli bir platformda çalıştıracak bir proje oluşturabilirsiniz. Tüm bu durumlarda, derleme seçeneklerinin çoğu aynı kalır; derleme yapılandırmasını kontrol etmek için yalnızca birkaç seçenek değiştirilir. Bu MSBuild, farklı derleme yapılandırmalarını oluşturmak için özellikleri ve koşulları kullanır.

## <a name="use-properties-to-control-build-settings"></a>Derleme ayarlarını kontrol etmek için özellikleri kullanma

öğesi, geçici bir dizinin konumu gibi bir proje dosyasında birkaç kez başvurulan veya Hata ayıklama derlemesi ve Yayın derlemesi gibi çeşitli yapılandırmalarda kullanılan özelliklerin değerlerini ayarlamak için bir değişken `Property` tanımlar. Özellikler hakkında daha fazla bilgi için [bkz. MSBuild.](../msbuild/msbuild-properties.md)

Proje dosyasını değiştirmek zorunda kalmadan derlemenizin yapılandırmasını değiştirmek için özellikleri kullanabilirsiniz. `Condition`öğesinin özniteliği `Property` ve `PropertyGroup` öğesi, özelliklerin değerini değiştirmenizi sağlar. Koşullar hakkında daha fazla MSBuild için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>Başka bir özele bağlı bir özellik grubu ayarlamak için

- Aşağıdakine `Condition` benzer bir `PropertyGroup` öğede özniteliğini kullanın:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>Başka bir özele bağlı bir özellik tanımlamak için

- Aşağıdakine `Condition` benzer bir `Property` öğede özniteliğini kullanın:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Komut satırı özelliklerini belirtme

Proje dosyanız birden çok yapılandırmayı kabul etmek için yazıldığı zaman, projenizi her derlemek için bu yapılandırmaları değiştirebilirsiniz. MSBuild , -property veya **-p** anahtarı kullanılarak komut satırı üzerinde özelliklerin belirt özeliklerine  izin vererek bu özelliği sağlar.

### <a name="to-set-a-project-property-at-the-command-line"></a>Komut satırına bir proje özelliği ayarlamak için

- özellik ve özellik değeri ile **-property** anahtarını kullanın. Örnek:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  veya

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Komut satırına birden fazla proje özelliği belirtmek için

- Özellik **ve özellik değerleriyle -property** veya **-p** anahtarını birden çok kez kullanın ya da bir **-property** veya **-p** anahtarı kullanın ve noktalı virgülle birden çok özelliği ayırın (;). Örnek:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  veya

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Ortam değişkenleri de özellik olarak kabul edilir ve ortam değişkenleri tarafından otomatik olarak MSBuild. Ortam değişkenlerini kullanma hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Derlemede ortam değişkenlerini kullanma.](../msbuild/how-to-use-environment-variables-in-a-build.md)

  Komut satırı üzerinde belirtilen özellik değeri, proje dosyasındaki aynı özellik için ayarlanmış herhangi bir değerden önceliklidir ve proje dosyasındaki bu değer bir ortam değişkeninde yer alan değerden önceliklidir.

  Bir proje etiketinde özniteliğini `TreatAsLocalProperty` kullanarak bu davranışı değiştirebilirsiniz. Bu öznitelikle listelenen özellik adları için, komut satırı üzerinde belirtilen özellik değeri proje dosyasındaki değerden öncelikli değildir. Bu konunun devamlarında bir örnek bulabilirsiniz.

## <a name="example-1"></a>Örnek 1

Aşağıdaki kod örneği olan "Merhaba Dünya" projesi, hata ayıklama derlemesi ve Yayın derlemesi oluşturmak için kullanılan iki yeni özellik grubu içerir.

Bu projenin hata ayıklama sürümünü oluşturmak için şunları yazın:

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

Bu projenin perakende sürümünü oluşturmak için yazın:

```cmd
msbuild consolehwcs1.proj -p:flavor=retail
```

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Sets the default flavor if an environment variable called
    Flavor is not set or specified on the command line -->
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
    </PropertyGroup>

    <!-- Define the DEBUG settings -->
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
        <DebugType>full</DebugType>
        <Optimize>no</Optimize>
    </PropertyGroup>

    <!-- Define the RETAIL settings -->
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">
        <DebugType>pdbonly</DebugType>
        <Optimize>yes</Optimize>
    </PropertyGroup>

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files
        of type CSFile -->
        <CSC  Sources = "@(CSFile)"
            DebugType="$(DebugType)"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe" >

            <!-- Set the OutputAssembly attribute of the CSC
            task to the name of the executable file that is
            created -->
            <Output TaskParameter="OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Örnek 2

Aşağıdaki örnek özniteliğinin nasıl kullanılageldi? `TreatAsLocalProperty` özelliği, `Color` proje dosyasında ve komut satırı içinde `Blue` `Green` değerine sahip. proje etiketinde ile, komut satırı özelliği ( ) proje dosyasında tanımlanan `TreatAsLocalProperty="Color"` `Green` özelliği geçersiz kılmaz ( `Blue` ).

Projeyi derlemek için aşağıdaki komutu girin:

```cmd
msbuild colortest.proj -t:go -property:Color=Green
```

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0" TreatAsLocalProperty="Color">

    <PropertyGroup>
        <Color>Blue</Color>
    </PropertyGroup>

    <Target Name="go">
        <Message Text="Color: $(Color)" />
    </Target>
</Project>

<!--
  Output with TreatAsLocalProperty="Color" in project tag:
     Color: Blue

  Output without TreatAsLocalProperty="Color" in project tag:
     Color: Green
-->
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Project öğesi (MSBuild)](../msbuild/project-element-msbuild.md)
