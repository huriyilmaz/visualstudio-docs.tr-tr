---
title: 'Nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bf76967363f4c0d97d93c895fbeb6209c8503f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821679"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Nasıl Yapılır: Farklı Seçeneklerle Aynı Kaynak Dosyaları Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje oluştururken, aynı bileşenleri farklı derleme seçenekleriyle sık sık derleyebilirsiniz. Örneğin, simge bilgileriyle bir hata ayıklama derlemesi veya sembol bilgisi olmadan bir yayın derlemesi oluşturabilirsiniz, ancak iyileştirmeler etkin hale getirebilirsiniz. Ya da bir projeyi x86 veya gibi belirli bir platformda çalıştırmak için oluşturabilirsiniz [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] . Tüm bu durumlarda, çoğu yapı seçeneği aynı kalır; yapı yapılandırmasını denetlemek için yalnızca birkaç seçenek değiştirilmiştir. İle [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , farklı yapı yapılandırmalarının oluşturulması için özellikleri ve koşulları kullanırsınız.  
  
## <a name="using-properties-to-modify-projects"></a>Projeleri değiştirmek için özellikleri kullanma  
 Öğesi, bir `Property` Proje dosyasında, geçici bir dizinin konumu gibi birkaç kez başvurulan bir değişkeni tanımlar veya hata ayıklama derlemesi ve bir yayın derlemesi gibi çeşitli yapılandırmalarda kullanılan özelliklerin değerlerini ayarlar. Özellikler hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](msbuild-properties1.md).  
  
 Proje dosyasını değiştirmek zorunda kalmadan, yapınızı yapılandırmayı değiştirmek için özellikleri kullanabilirsiniz. `Condition` `Property` Öğesi ve öğesi özniteliği, `PropertyGroup` özelliklerinin değerini değiştirmenize izin verir. Koşullar hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bkz. [koşullar](../msbuild/msbuild-conditions.md).  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Bir özellik grubunu başka bir özelliğe göre ayarlamak için  
  
- `Condition`Aşağıdaki şuna benzer bir öğe içinde bir özniteliği kullanın `PropertyGroup` :  
  
    ```  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>Bir özelliği başka bir özelliğe göre tanımlamak için  
  
- `Condition`Aşağıdaki şuna benzer bir öğe içinde bir özniteliği kullanın `Property` :  
  
    ```  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specifying-properties-on-the-command-line"></a>Komut satırında özellikleri belirtme  
 Proje dosyanız birden çok yapılandırmayı kabul etmek üzere yazıldıktan sonra, projenizi her oluşturduğunuzda bu konfigürasyonları değiştirme olanağına sahip olmanız gerekir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Bu özelliği, komut satırında **/Property** veya **/p** anahtarı kullanılarak belirtilen özelliklerin kullanılmasına izin vererek sağlar.  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>Komut satırında bir proje özelliği ayarlamak için  
  
- Özellik ve özellik değeri ile **/Property** anahtarını kullanın. Örneğin:  
  
    ```  
    msbuild file.proj /property:Flavor=Debug  
    ```  
  
     \- veya  
  
    ```  
    Msbuild file.proj /p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Komut satırında birden fazla proje özelliği belirtmek için  
  
- Özellik ve özellik değerleriyle birden çok kez **/Property** veya **/p** anahtarı kullanın veya bir **/Property** ya da **/p** anahtarı kullanın ve birden çok özelliği noktalı virgülle ayırın (;). Örneğin:  
  
  ```  
  msbuild file.proj /p:Flavor=Debug;Platform=x86  
  ```  
  
   \- veya  
  
  ```  
  msbuild file.proj /p:Flavor=Debug /p:Platform=x86  
  ```  
  
  Ortam değişkenleri Ayrıca özellik olarak değerlendirilir ve tarafından otomatik olarak eklenir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Ortam değişkenlerini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir derlemede ortam değişkenlerini kullanma](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
  Komut satırında belirtilen özellik değeri, proje dosyasında aynı özellik için ayarlanan herhangi bir değere göre önceliklidir ve proje dosyasındaki değer, bir ortam değişkeninde değeri öncelikli olarak alır.  
  
  Bu davranışı `TreatAsLocalProperty` bir proje etiketinde özniteliğini kullanarak değiştirebilirsiniz. Bu öznitelikle listelenen özellik adları için, komut satırında belirtilen özellik değeri proje dosyasındaki değerden önceliklidir. Bu konunun ilerleyen kısımlarında bir örnek bulabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, "Merhaba Dünya" projesi, hata ayıklama derlemesi ve yayın derlemesi oluşturmak için kullanılabilecek iki yeni özellik grubu içerir.  
  
 Bu projenin hata ayıklama sürümünü oluşturmak için şunu yazın:  
  
```  
msbuild consolehwcs1.proj /p:flavor=debug  
```  
  
 Bu projenin perakende sürümünü oluşturmak için şunu yazın:  
  
```  
msbuild consolehwcs1.proj /p:flavor=retail  
```  
  
```  
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
 Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir `TreatAsLocalProperty` . `Color`Özelliği `Blue` Proje dosyasında ve `Green` komut satırında değerini içerir. `TreatAsLocalProperty="Color"`Proje etiketinde, komut satırı özelliği ( `Green` ) proje dosyasında tanımlanan özelliği () geçersiz kılmaz `Blue` .  
  
 Projeyi derlemek için aşağıdaki komutu girin:  
  
```  
msbuild colortest.proj /t:go /property:Color=Green  
```  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
[MSBUILD](msbuild.md)  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Proje Öğesi (MSBuild)](../msbuild/project-element-msbuild.md)
