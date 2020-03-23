---
title: 'Nasıl Yapılsın: Farklı Seçeneklerle Aynı Kaynak Dosyaları Oluşturma | Microsoft Dokümanlar'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c31da244e5c264bb81498c6091aefce7e6318bb2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633947"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Nasıl yapılı: Farklı seçeneklerle aynı kaynak dosyaları oluşturma

Projeler oluştururken, sık sık farklı yapı seçenekleriyle aynı bileşenleri derlersiniz. Örneğin, simge bilgileri yle birlikte bir hata ayıklama yapısı veya simge bilgisi olmayan ancak optimizasyonlar etkinleştirilmiş bir sürüm yapısı oluşturabilirsiniz. Veya x86 veya x64 gibi belirli bir platformda çalışacak bir proje oluşturabilirsiniz. Tüm bu durumlarda, yapı seçeneklerinin çoğu aynı kalır; yapı yapılandırmasını denetlemek için yalnızca birkaç seçenek değiştirilir. MSBuild ile, farklı yapı yapılandırmaları oluşturmak için özellikleri ve koşulları kullanırsınız.

## <a name="use-properties-to-control-build-settings"></a>Yapı ayarlarını denetlemek için özellikleri kullanma

Öğe, `Property` geçici bir dizinin konumu gibi bir proje dosyasında birkaç kez başvurulan veya Hata Ayıklama yapısı ve Sürüm yapısı gibi çeşitli yapılandırmalarda kullanılan özelliklerin değerlerini ayarlamak için birkaç kez başvurulan bir değişken tanımlar. Özellikler hakkında daha fazla bilgi için [MSBuild özelliklerine](../msbuild/msbuild-properties.md)bakın.

Proje dosyasını değiştirmek zorunda kalmadan yapınızın yapılandırmasını değiştirmek için özellikleri kullanabilirsiniz. Öğenin `Condition` ve öğenin `PropertyGroup` özniteliği özelliklerin değerini değiştirmenizi sağlar. `Property` MSBuild koşulları hakkında daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>Başka bir özelliğe bağlı bir özellik grubu ayarlamak için

- Aşağıdakilere `Condition` benzer bir `PropertyGroup` öğede bir öznitelik kullanın:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>Başka bir özelliğe bağlı bir özelliği tanımlamak için

- Aşağıdakilere `Condition` benzer bir `Property` öğede bir öznitelik kullanın:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Komut satırındaki özellikleri belirtin

Proje dosyanız birden çok yapılandırmayı kabul etmek üzere yazıldıktan sonra, projenizi her oluşturduğunuzda bu yapılandırmaları değiştirme yeteneğine sahip olmanız gerekir. MSBuild bu **yeteneği, -özellik** veya **-p** anahtarı nı kullanarak komut satırında özelliklerin belirtilmesine izin vererek sağlar.

### <a name="to-set-a-project-property-at-the-command-line"></a>Komut satırında proje özelliği ayarlamak için

- Özellik ve özellik değeri ile **-özellik** anahtarını kullanın. Örnek:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  or

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Komut satırında birden fazla proje özelliği belirtmek için

- **-özellik** veya **-p** anahtarını özellik ve özellik değerleriyle birden çok kez kullanın veya bir **-özellik** veya **-p** anahtarı kullanın ve birden çok özelliği yarı kolonlu (;). Örnek:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  or

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Ortam değişkenleri de özellik olarak kabul edilir ve msbuild tarafından otomatik olarak dahil edilir. Çevre değişkenlerini kullanma hakkında daha fazla bilgi için [bkz: Yapıdaki ortam değişkenlerini kullanma.](../msbuild/how-to-use-environment-variables-in-a-build.md)

  Komut satırında belirtilen özellik değeri, proje dosyasındaki aynı özellik için ayarlanan değerden önce gelir ve proje dosyasındaki değer bir ortam değişkenindeki değerden önce gelir.

  Proje etiketindeki `TreatAsLocalProperty` özniteliği kullanarak bu davranışı değiştirebilirsiniz. Bu öznitelikile listelenen özellik adları için, komut satırında belirtilen özellik değeri proje dosyasındaki değerden önce gelmez. Daha sonra bu konuda bir örnek bulabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, "Hello World" projesi, hata ayıklama yapısı ve Sürüm yapısı oluşturmak için kullanılabilecek iki yeni özellik grubu içerir.

Bu projenin hata ayıklama sürümünü oluşturmak için şunları yazın:

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

Bu projenin perakende sürümünü oluşturmak için şunları yazın:

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

## <a name="example"></a>Örnek

Aşağıdaki örnek, özniteliğin `TreatAsLocalProperty` nasıl kullanılacağını göstermektedir. Özelliğin `Color` proje `Blue` dosyasında ve `Green` komut satırında bir değeri vardır. Proje `TreatAsLocalProperty="Color"` etiketinde , komut satırı özelliği`Green`( ) proje dosyasında tanımlanan özelliği geçersiz kılmaz (`Blue`).

Projeyi oluşturmak için aşağıdaki komutu girin:

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

- [Msbuild](../msbuild/msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Proje öğesi (MSBuild)](../msbuild/project-element-msbuild.md)
