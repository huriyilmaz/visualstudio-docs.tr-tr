---
title: 'Nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme | Microsoft Docs'
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
ms.openlocfilehash: b196ae92b7388e8b9f4e1cee60a62b3839a9c120
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585238"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme
Proje oluştururken, aynı bileşenleri farklı derleme seçenekleriyle sık sık derleyebilirsiniz. Örneğin, simge bilgileriyle bir hata ayıklama derlemesi veya sembol bilgisi olmadan bir yayın derlemesi oluşturabilirsiniz, ancak iyileştirmeler etkin hale getirebilirsiniz. Ya da bir projeyi, x86 veya [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]gibi belirli bir platformda çalıştırmak için oluşturabilirsiniz. Tüm bu durumlarda, çoğu yapı seçeneği aynı kalır; yapı yapılandırmasını denetlemek için yalnızca birkaç seçenek değiştirilmiştir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], özellikleri ve koşulları farklı derleme yapılandırması oluşturmak için kullanırsınız.

## <a name="use-properties-to-modify-projects"></a>Projeleri değiştirmek için özellikleri kullanma
`Property` öğesi, bir proje dosyasında, geçici bir dizinin konumu gibi birkaç kez başvurulan bir değişkeni tanımlar veya hata ayıklama derlemesi ve bir yayın derlemesi gibi çeşitli yapılandırmalarda kullanılan özelliklerin değerlerini ayarlar. Özellikler hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

Proje dosyasını değiştirmek zorunda kalmadan, yapınızı yapılandırmayı değiştirmek için özellikleri kullanabilirsiniz. `Property` öğesinin ve `PropertyGroup` öğesinin `Condition` özniteliği, özelliklerinin değerini değiştirmenize izin verir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] koşulları hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).

#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Bir özellik grubunu başka bir özelliğe göre ayarlamak için

- Bir `PropertyGroup` öğesinde şuna benzer bir `Condition` özniteliği kullanın:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

#### <a name="to-define-a-property-based-on-another-property"></a>Bir özelliği başka bir özelliğe göre tanımlamak için

- Bir `Property` öğesinde şuna benzer bir `Condition` özniteliği kullanın:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Komut satırında özellikleri belirtin
Proje dosyanız birden çok yapılandırmayı kabul etmek üzere yazıldıktan sonra, projenizi her oluşturduğunuzda bu konfigürasyonları değiştirme olanağına sahip olmanız gerekir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], **-Property** veya **-p** anahtarı kullanılarak komut satırında özelliklerin belirtilmesine izin vererek bu yeteneği sağlar.

#### <a name="to-set-a-project-property-at-the-command-line"></a>Komut satırında bir proje özelliği ayarlamak için

- Özellik ve özellik değeri ile **-Property** anahtarını kullanın. Örneğin:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  veya

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Komut satırında birden fazla proje özelliği belirtmek için

- Özellik ve özellik değerleriyle birden çok kez **-Property** veya **-p** anahtarı kullanın ya da bir **-Property** veya **-p** anahtarı kullanın ve birden çok özelliği noktalı virgülle ayırın (;). Örneğin:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  veya

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Ortam değişkenleri de özellikler olarak değerlendirilir ve [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]tarafından otomatik olarak eklenir. Ortam değişkenlerini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir derlemede ortam değişkenlerini kullanma](../msbuild/how-to-use-environment-variables-in-a-build.md).

  Komut satırında belirtilen özellik değeri, proje dosyasında aynı özellik için ayarlanan herhangi bir değere göre önceliklidir ve proje dosyasındaki değer, bir ortam değişkeninde değeri öncelikli olarak alır.

  Bu davranışı bir proje etiketinde `TreatAsLocalProperty` özniteliğini kullanarak değiştirebilirsiniz. Bu öznitelikle listelenen özellik adları için, komut satırında belirtilen özellik değeri proje dosyasındaki değerden önceliklidir. Bu konunun ilerleyen kısımlarında bir örnek bulabilirsiniz.

## <a name="example"></a>Örnek
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

    <!-- Sets the default flavor of an environment variable called
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
Aşağıdaki örnekte `TreatAsLocalProperty` özniteliğinin nasıl kullanılacağı gösterilmektedir. `Color` özelliği, proje dosyasında `Blue` bir değere sahiptir ve komut satırında `Green`. Proje etiketinde `TreatAsLocalProperty="Color"`, komut satırı özelliği (`Green`) proje dosyasında tanımlanan özelliği (`Blue`) geçersiz kılmaz.

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
- [Proje öğesi (MSBuild)](../msbuild/project-element-msbuild.md)
