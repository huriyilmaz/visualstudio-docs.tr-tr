---
title: Aynı kaynak dosyalarını farklı seçeneklerle derleme
description: farklı seçeneklerle aynı kaynak dosyaları oluşturmak için farklı MSBuild yapı yapılandırmalarının nasıl oluşturulacağını öğrenin.
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
ms.openlocfilehash: cd2a701d8e5be3084466617e966f0475807e74db4645ffe6c1754a0cf0bafdaf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427866"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme

Proje oluştururken, aynı bileşenleri farklı derleme seçenekleriyle sık sık derleyebilirsiniz. Örneğin, simge bilgileriyle bir hata ayıklama derlemesi veya sembol bilgisi olmadan bir yayın derlemesi oluşturabilirsiniz, ancak iyileştirmeler etkin hale getirebilirsiniz. Ya da bir projeyi x86 veya x64 gibi belirli bir platformda çalıştırmak için oluşturabilirsiniz. Tüm bu durumlarda, çoğu yapı seçeneği aynı kalır; yapı yapılandırmasını denetlemek için yalnızca birkaç seçenek değiştirilmiştir. MSBuild, özellikleri ve koşulları farklı derleme yapılandırması oluşturmak için kullanırsınız.

## <a name="use-properties-to-control-build-settings"></a>Yapı ayarlarını denetlemek için özellikleri kullanma

Öğesi, bir `Property` Proje dosyasında, geçici bir dizinin konumu gibi birkaç kez başvurulan bir değişkeni tanımlar veya hata ayıklama derlemesi ve bir yayın derlemesi gibi çeşitli yapılandırmalarda kullanılan özelliklerin değerlerini ayarlar. özellikler hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

Proje dosyasını değiştirmek zorunda kalmadan, yapınızı yapılandırmayı değiştirmek için özellikleri kullanabilirsiniz. `Condition` `Property` Öğesi ve öğesi özniteliği, `PropertyGroup` özelliklerinin değerini değiştirmenize izin verir. MSBuild koşulları hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>Başka bir özelliğe bağlı bir özellik grubu ayarlamak için

- `Condition`Aşağıdaki şuna benzer bir öğe içinde bir özniteliği kullanın `PropertyGroup` :

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>Başka bir özelliğe bağımlı olan bir özellik tanımlamak için

- `Condition`Aşağıdaki şuna benzer bir öğe içinde bir özniteliği kullanın `Property` :

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Komut satırında özellikleri belirtin

Proje dosyanız birden çok yapılandırmayı kabul etmek üzere yazıldıktan sonra, projenizi her oluşturduğunuzda bu konfigürasyonları değiştirme olanağına sahip olmanız gerekir. MSBuild, **-property** veya **-p** anahtarı kullanılarak komut satırında özelliklerin belirtilmesine izin vererek bu yeteneği sağlar.

### <a name="to-set-a-project-property-at-the-command-line"></a>Komut satırında bir proje özelliği ayarlamak için

- Özellik ve özellik değeri ile **-Property** anahtarını kullanın. Örnek:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  veya

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Komut satırında birden fazla proje özelliği belirtmek için

- Özellik ve özellik değerleriyle birden çok kez **-Property** veya **-p** anahtarı kullanın ya da bir **-Property** veya **-p** anahtarı kullanın ve birden çok özelliği noktalı virgülle ayırın (;). Örnek:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  veya

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Ortam değişkenleri de özellikler olarak değerlendirilir ve MSBuild tarafından otomatik olarak eklenir. Ortam değişkenlerini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir derlemede ortam değişkenlerini kullanma](../msbuild/how-to-use-environment-variables-in-a-build.md).

  Komut satırında belirtilen özellik değeri, proje dosyasında aynı özellik için ayarlanan herhangi bir değere göre önceliklidir ve proje dosyasındaki değer, bir ortam değişkeninde değeri öncelikli olarak alır.

  Bu davranışı `TreatAsLocalProperty` bir proje etiketinde özniteliğini kullanarak değiştirebilirsiniz. Bu öznitelikle listelenen özellik adları için, komut satırında belirtilen özellik değeri proje dosyasındaki değerden önceliklidir. Bu konunun ilerleyen kısımlarında bir örnek bulabilirsiniz.

## <a name="example-1"></a>Örnek 1

Aşağıdaki kod örneğinde, "Merhaba Dünya" projesi, hata ayıklama derlemesi ve yayın derlemesi oluşturmak için kullanılabilecek iki yeni özellik grubu içerir.

Bu projenin hata ayıklama sürümünü oluşturmak için şunu yazın:

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

Bu projenin perakende sürümünü oluşturmak için şunu yazın:

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

Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir `TreatAsLocalProperty` . `Color`Özelliği `Blue` Proje dosyasında ve `Green` komut satırında değerini içerir. `TreatAsLocalProperty="Color"`Proje etiketinde, komut satırı özelliği ( `Green` ) proje dosyasında tanımlanan özelliği () geçersiz kılmaz `Blue` .

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
