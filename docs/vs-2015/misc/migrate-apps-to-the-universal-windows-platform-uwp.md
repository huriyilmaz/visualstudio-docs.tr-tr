---
title: Uygulamaları Evrensel Windows Platformu geçirme (UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60951091914474f07f19672799fb59c8b2d0aa56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919136"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Uygulamaları Evrensel Windows Platformu’na (UWP) geçirme
Visual Studio 2015 RTM ile kullanılabilmesi için, Windows Mağazası 8,1 uygulamaları, Windows Phone 8,1 uygulamaları veya Visual Studio 2015 RC ile oluşturulan Evrensel Windows uygulamaları için gerekli olan proje dosyalarınızda el ile yapılan değişiklikleri yapın. (Hem Windows uygulama projesi hem de Windows Phone projesi olan bir Windows 8.1 Universal uygulamanız varsa, her bir projeyi geçirmek için adımları izlemeniz gerekir.)

 Evrensel Windows Platformu, artık uygulamanızı bir veya daha fazla cihaz ailesinden hedefleyebilirsiniz. Evrensel Windows uygulamaları hakkında daha fazla bilgi edinmek istiyorsanız, bu [Platform kılavuzuna](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx)göz atın.

- [Mevcut C#/vb Windows mağazası 8,1 veya Windows Phone 8,1 uygulamalarınızı](#MigrateCSharp) Evrensel Windows platformu kullanacak şekilde geçirin.

- [Mevcut C++ Windows mağazası 8,1 veya Windows Phone 8,1 uygulamalarınızı](#MigrateCPlusPlus) Evrensel Windows platformu kullanacak şekilde geçirin.

- [Visual Studio 2015 RC ile oluşturulan mevcut Evrensel Windows uygulamaları için gerekli değişiklikler](#PreviousVersions).

- [Visual Studio 2015 RC ile oluşturulan Evrensel Windows uygulamaları için mevcut birim testi projeleri için gerekli değişiklikler](#MigrateUnitTest).

  Tüm bu değişiklikleri yapmak istemiyorsanız, [mevcut uygulamalarınızın](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) yeni bir Evrensel Windows projesine nasıl bağlantı sağladığını öğrenin.

## <a name="migrate-your-cvb-windows-store-81-or-windows-phone-81-apps-to-use-the-universal-windows-platform"></a><a name="MigrateCSharp"></a> C#/vb Windows Mağazası 8,1 veya Windows Phone 8,1 uygulamalarınızı Evrensel Windows Platformu kullanacak şekilde geçirin

#### <a name="migrate-your-cvb-project-files"></a>C#/vb proje dosyalarınızı geçirme

1. Yüklediğiniz Evrensel Windows Platformu bulmak için şu klasörü açın: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü her bir Evrensel Windows Platformu klasörlerinin listesini içerir. Klasör adı, yüklediğiniz Evrensel Windows Platformu sürümdür. Örneğin, bu Windows 10 cihazında yüklü Evrensel Windows Platformu sürüm 10.0.10240.0 vardır.

     ![Yüklü sürümleri görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Evrensel Windows Platformu birden fazla sürümü yüklenebilir. Uygulamanız için en son sürümü kullanmanızı öneririz.

2. Dosya Gezgini 'ni kullanarak UWP projenizin depolandığı klasöre gidin. Bu klasörde bir. JSON dosyası oluşturun. Dosyayı project.jsolarak adlandırın ve ardından şu içeriği bu dosyaya ekleyin:

    ```json
    {
      "dependencies": {
        "Microsoft.ApplicationInsights": "1.0.0",
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
      },
      "frameworks": {
        "uap10.0": {}
      },
      "runtimes": {
        "win10-arm": {},
        "win10-arm-aot": {},
        "win10-x86": {},
        "win10-x86-aot": {},
        "win10-x64": {},
        "win10-x64-aot": {}
      }
    }

    ```

3. Aşağıdaki içeriklerle default.rd.xml adlı bir dosya oluşturun. Bir VB projeniz varsa, bu dosyayı projeniz için projem dizinine ekleyin. Bir C# projeniz varsa, bu dosyayı projenizin Özellikler dizinine ekleyin.

    ```xml
    <?xml version="1.0"?>
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->
    <Assembly Dynamic="Required All" Name="*Application*"/>
    <!-- Add your application specific runtime directives here. -->
    </Application></Directives>
    ```

4. Visual Studio 'da mevcut Windows Mağazası 8,1 uygulamanızı veya Windows Phone 8,1 uygulamanızı içeren çözümünüzü açın.

5. Çözüm Gezgini içinde uygulamanız için mevcut projenize sağ tıklayın ve ardından **Projeyi Kaldır**' ı seçin. Proje kaldırıldıktan sonra proje dosyasına tekrar sağ tıklayın ve. csproj veya. vbproj dosyasını düzenlemeyi seçin.

     ![Projeye sağ tıklayın ve Düzenle ' yi seçin.](../misc/media/uap-editproject.png "UAP_EditProject")

6. \<PropertyGroup> \<TargetPlatformVersion> 8,1 değerine sahip öğeyi içeren öğeyi bulun. Bu öğe için aşağıdaki adımları uygulayın \<PropertyGroup> :

    1. \<Platform>Öğesinin değerini: **x86**olarak ayarlayın.

    2. Bir \<TargetPlatformIdentifier> öğe ekleyin ve değerini: **UAP**olarak ayarlayın.

    3. Öğesinin varolan değerini, \<TargetPlatformVersion> yüklediğiniz Evrensel Windows platformu sürümünün değeri olacak şekilde değiştirin. Ayrıca bir \<TargetPlatformMinVersion> öğesi ekleyin ve aynı değere verin.

    4. \<MinimumVisualStudioVersion>Öğenin değerini: **14**olarak değiştirin.

    5. \<ProjectTypeGuids>Öğesini aşağıda gösterildiği gibi değiştirin:

         C# için:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        ```

         VB için:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        ```

    6. Bir \<EnableDotNetNativeCompatibleProfile> öğe ekleyin ve değerini: **true**olarak ayarlayın.

    7. Evrensel Windows uygulamaları için varsayılan varlık ölçeği 200 ' dir. Projeniz 200 değerinde ölçeklendirilmemiş varlıklar içeriyorsa, \<UapDefaultAssetScale> Bu PropertyGroup 'a varlıklarınızın ölçeğine sahip bir öğe eklemeniz gerekir. [Varlıklar ve ölçekler](https://msdn.microsoft.com/library/jj679352.aspx)hakkında daha fazla bilgi edinin.

         Artık şu \<PropertyGroup> örneğe benzer görünmelidir:

        ```xml
        <PropertyGroup>
            …
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

7. Şu anda kullandığınız Visual Studio sürümünü yansıtmak için 12,0 olan tüm örnekleri 14,0 ile değiştirin. Şu örnekler gibi:

    ```xml
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

    ```
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">
        <VisualStudioVersion>14.0</VisualStudioVersion>
    ```

8. \<PropertyGroup>Koşul özniteliğinin bir parçası olarak anycpu platformu için yapılandırılmış öğeleri bulun. Bu öğeleri ve tüm alt öğelerini kaldırın. Visual Studio 2015 ' de Windows 10 uygulamaları için AnyCPU desteklenmez. Örneğin, \<PropertyGroup> bunlar gibi öğeleri kaldırmanız gerekir:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
    ```

9. Kalan her \<PropertyGroup> öğe için, öğenin sürüm yapılandırması olan bir koşul özniteliğine sahip olup olmadığını denetleyin. Varsa, ancak bir öğesi içermiyorsa bir \<UseDotNetNativeToolchain> tane ekleyin. Öğesi için değeri \<UseDotNetNativeToolchain> true olarak ayarlayın, şöyle:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">
        <OutputPath>bin\x64\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <Optimize>true</Optimize>
        <NoWarn>;2008</NoWarn>
        <DebugType>pdbonly</DebugType>
        <PlatformTarget>x64</PlatformTarget>
        <UseVSHostingProcess>false</UseVSHostingProcess>
        <ErrorReport>prompt</ErrorReport>
        <Prefer32Bit>true</Prefer32Bit>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

10. Yalnızca Windows Phone projeleri için, \<PropertyGroup> \<TargetPlatformIdentifier> WindowsPhoneApp değeri olan bir öğe içeren öğeyi kaldırın. Bu öğenin tüm alt öğelerini de kaldır:

    ```xml
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>
    </PropertyGroup>
    ```

11. \<ItemGroup>Öğesini içeren öğeyi bulun \<AppxManifest> . Aşağıdaki \<None> öğeyi öğesinin bir alt öğesi olarak ekleyin \<ItemGroup> :

    ```xml
    <None Include="project.json" />
    ```

12. \<ItemGroup>Projenize eklenen logo. png dosyaları () gibi diğer varlıkları içeren öğeyi bulun \<Content Include="Assets\Logo.scale-100.png" /> . Aşağıdaki \<Content> alt öğeyi bu \<ItemGroup> öğeye ekleyin:

     **C# için:**

    ```xml
    <Content Include="Properties\default.rd.xml" />
    ```

     **VB için:**

    ```xml
    <Content Include="My Project\default.rd.xml" />
    ```

13. \<ItemGroup> \<Reference> NuGet paketlerine alt öğeler içeren öğeyi bulun. Projenizi yeniden yükledikten sonra NuGet Paket Yöneticisi ile indirmeniz gerekeceğinden, kullandığınız NuGet paketlerini bir yere göz atın. Bunu \<ItemGroup> alt öğeleri ile birlikte kaldırın. Örneğin, UWP projesinde kaldırılması gereken aşağıdaki NuGet paketleri olabilir:

    ```xml
    <ItemGroup>
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
          <Private>True</Private>
        </Reference>
      </ItemGroup>
    ```

14. Yaptığınız değişiklikleri kaydedin.

15. . Csproj veya. vbproj dosyasını kapatın.

16. Çözüm Gezgini ' de projenize sağ tıklayın ve bağlam menüsünden projeyi yeniden yükle ' yi seçin. Projenizdeki tüm dosyalar artık Çözüm Gezgini görüntülenmelidir.

17. Daha önceki bir adımda sildiğiniz paketleri geri eklemek için NuGet yöneticisini kullanın.

     Şimdi tüm Windows Mağazası 8,1 veya Windows Phone 8,1 projelerinizin [Paket bildirim dosyalarını güncelleştirmek](#PackageManifest) için adımları izlemeniz gerekir.

## <a name="migrate-your-c-windows-store-81-or-windows-phone-81-apps-to-use-the-universal-windows-platform"></a><a name="MigrateCPlusPlus"></a> C++ Windows Mağazası 8,1 veya Windows Phone 8,1 uygulamalarınızı Evrensel Windows Platformu kullanmak için geçirin

#### <a name="migrate-your-c-project-files"></a>C++ proje dosyalarınızı geçirme

1. Yüklediğiniz Evrensel Windows Platformu bulmak için şu klasörü açın: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü her bir Evrensel Windows Platformu klasörlerinin listesini içerir. Klasör adı, yüklediğiniz Evrensel Windows Platformu sürümdür. Örneğin, bu Windows 10 cihazında yüklü Evrensel Windows Platformu sürüm 10.0.10240.0 vardır.

     ![Yüklü sürümleri görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Evrensel Windows Platformu birden fazla sürümü yüklenebilir. Uygulamanız için en son sürümü kullanmanızı öneririz.

2. Visual Studio 'da mevcut C++ Windows Mağazası 8,1 uygulamanızı veya Windows Phone 8,1 uygulamanızı içeren çözümünüzü açın.

     Çözüm Gezgini ' nde mevcut projenize sağ tıklayın ve ardından **Projeyi Kaldır**' ı seçin. Proje kaldırıldıktan sonra proje dosyasına tekrar sağ tıklayın ve. vcxproj dosyasını düzenlemeyi seçin.

     ![Sağ&#45;proje dosyası ' na tıklayın ve düzenlemek için seçin](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")

3. \<PropertyGroup> \<ApplicationTypeRevision> 8,1 değerine sahip öğeyi içeren öğeyi bulun. Bu öğe için aşağıdaki adımları uygulayın \<PropertyGroup> :

    1. Bir \<WindowsTargetPlatformVersion> öğe ve bir \<WindowsTargetPlatformMinVersion> öğesi ekleyin ve yüklediğiniz Evrensel Windows platformu sürümünün değerini verin.

    2. ApplicationTypeRevision öğesinin değerini 8,1 ' den 10,0 ' e güncelleştirin.

    3. \<MinimumVisualStudioVersion>Öğenin değerini: 14 olarak değiştirin.

    4. Bir \<EnableDotNetNativeCompatibleProfile> öğe ekleyin ve değerini: true olarak ayarlayın.

    5. Evrensel Windows uygulamaları için varsayılan varlık ölçeği 200 ' dir. Projeniz 200 değerinde ölçeklendirilmemiş varlıklar içeriyorsa, \<UapDefaultAssetScale> Bu PropertyGroup 'a varlıklarınızın ölçeğine sahip bir öğe eklemeniz gerekir. [Varlıklar ve ölçekler](https://msdn.microsoft.com/library/jj679352.aspx)hakkında daha fazla bilgi edinin.

    6. Yalnızca Windows Phone projeleri için, \<ApplicationType> Windows Phone değerini Windows Mağazası olarak değiştirin.

         Artık şu \<PropertyGroup> örneğe benzer görünmelidir:

        ```xml
        <PropertyGroup>
            …
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
             <ApplicationType>Windows Store</ApplicationType>
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

4. Öğesinin tüm örneklerini \<PlatformToolset> v140 değerine sahip olacak şekilde değiştirin. Örneğin:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

5. Kalan her \<PropertyGroup> öğe için, öğenin sürüm yapılandırması olan bir koşul özniteliğine sahip olup olmadığını denetleyin. Varsa, ancak bir öğesi içermiyorsa bir \<UseDotNetNativeToolchain> tane ekleyin. Öğesi için değeri \<UseDotNetNativeToolchain> true olarak ayarlayın, şöyle:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

6. Yaptığınız değişiklikleri kaydedin. Ardından proje dosyasını kapatın.

7. Çözüm Gezgini ' de proje dosyanıza sağ tıklayın ve bağlam menüsünden projeyi yeniden yükle ' yi seçin. Projenizdeki tüm dosyalar artık Çözüm Gezgini görüntülenmelidir.

     Şimdi tüm Windows Mağazası 8,1 veya Windows Phone 8,1 projelerinizin [Paket bildirim dosyalarını güncelleştirmek](#PackageManifest) için adımları izlemeniz gerekir.

## <a name="update-your-package-manifest-file-for-all-your-windows-store-81-or-windows-phone-81-projects"></a><a name="PackageManifest"></a> Paket bildirim dosyanızı tüm Windows Mağazası 8,1 veya Windows Phone 8,1 projeleriniz için güncelleştirin
 Çözümünüzde her bir proje için paket bildirim dosyasını güncelleştirmeniz gerekir.

#### <a name="update-your-package-manifest-file"></a>Paket bildirim dosyanızı güncelleştirme

1. Projenizde Package. appxmanifest dosyasını açın. Windows Mağazası ve Windows Phone projelerinin her biri için Package. AppxManifest dosyasını düzenlemeniz gerekir.

2. \<Package>Öğeyi mevcut proje türüne göre yeni şemalar ile güncelleştirmeniz gerekir. İlk olarak, bir Windows Mağazası veya Windows Phone projesi olup olmadığına bağlı olarak aşağıdaki şemaları kaldırın.

    **Windows Mağazası projesi Için eski:** \<Package> Öğe şuna benzer.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">

   ```

    **Windows Phone projesi Için eski:** \<Package> Öğe şuna benzer.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">
   ```

    **Evrensel Windows platformu Için yeni:** Aşağıdaki şemaları \<Package> öğesine ekleyin. Yeni kaldırdığınız şemaların öğelerinden ilişkili ad alanı tanımlayıcı öneklerini kaldırın. Ignorablenamespaces özelliğini şu şekilde güncelleştirin: UAP MP. Yeni \<Package> öğe şuna benzer görünmelidir.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
      IgnorableNamespaces= "uap mp">

   ```

3. Öğeye bir \<Dependencies> alt öğesi ekleyin \<Package> . Daha sonra \<TargetDeviceFamily> Bu \<Dependencies> öğeye Name, MinVersion ve MaxVersionTested ile test edilmiş öznitelikleri ekleyerek bir alt öğesi ekleyin. Name özniteliğine: Windows. Universal değerini verin. MinVersion ve Maxversion'in yüklediğiniz Evrensel Windows Platformu sürümünün değerini test edin. Bu öğe şuna benzer görünmelidir:

   ```xml
   <Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />
   </Dependencies>
   ```

4. **Yalnızca Windows Mağazası için:** \<mp:PhoneIdentity> Öğeye bir alt öğe eklemeniz gerekiyor \<Package> . Phoneproductıd özniteliği ve Phonepublisherıd özniteliği ekleyin. Phoneproductıd 'yi öğedeki Name özniteliğiyle aynı değere sahip olacak şekilde ayarlayın \<Identity> . PhonePublishedId değerini şu şekilde ayarlayın: 00000000-0000-0000-0000-000000000000. Böyle:

   ```xml
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>
   ```

5. Öğesini bulun \<Prerequisites> ve bu öğeyi ve içerdiği tüm alt öğeleri silin.

6. **Uıap** ad alanını şu \<Resource> öğelere ekleyin: Scale, dxfeaturelevel. Örneğin:

   ```xml
   <Resources>
     <Resource Language="en-us"/>
    <Resource uap:Scale="180"/>
    <Resource uap:DXFeatureLevel="dx11"/>
   </Resources>

   ```

7. **UAP** ad alanını şu \<Capability> öğelere ekleyin: Documentslibrary, Resimkitaplığı, Videoslibrary, MusicLibrary, enterpriseAuthentication, Sharedusercertificates, removableStorage, randevular ve Contacts. Örneğin:

   ```xml
   <Capabilities>
     <uap:Capability Name="documentsLibrary"/>
     <uap:Capability Name="removableStorage"/>
   </Capabilities>

   ```

8. **Uıap** ad alanını \<VisualElements> öğeye ve alt öğelerinden birine ekleyin. Örneğin:

   ```xml
   <uap:VisualElements
       DisplayName="My WWA App"
       Square150x150Logo="images/150x150.png"
       Square44x44Logo="images/44x44.png"
       Description="My WWA App"
       BackgroundColor="#777777">
     <uap:SplashScreen Image="images/splash.png"/>
   </uap:VisualElements>

   ```

    **Yalnızca Windows Mağazası için geçerlidir:** Kutucuk boyutu adları değişti. Öğesi içindeki öznitelikleri, \<VisualElements> Yeni yakınsanmış döşeme boyutlarını yansıtacak şekilde değiştirin. 70x70, 71x71 olur ve 30x30, 44x44 olur.

    **Eski:** kutucuk boyutu adları

   ```xml
   <m2:VisualElements
       …
       Square30x30Logo="Assets\SmallLogo.png"
       …>
    <m2:DefaultTile
         …
         Square70x70Logo="images/70x70.png">
   </m2:VisualElements>

   ```

    **Yeni:** döşeme boyutu adları

   ```xml
   <uap:VisualElements
       …
       Square44x44Logo="Assets\SmallLogo.png"
       …>
    <uap:DefaultTile
         …
         Square71x71Logo="images/70x70.png">
   </uap:VisualElements>

   ```

9. **Uıap** ad alanını \<ApplicationContentUriRules> ve tüm alt öğelerine ekleyin. Örneğin:

    ```xml
    <uap:ApplicationContentUriRules>
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>
      <uap:Rule Type="exclude" Match="*.pdf"/>
    </uap:ApplicationContentUriRules>

    ```

10. Aşağıdaki öğelere ve tüm alt öğelerine **UAP** ad alanını ekleyin \<Extension> : Windows. accountpicturesağlamasını, Windows. alarm, Windows. Randevutmentsprovider Windows. autoPlayContent, Windows. autoPlayDevice, Windows. cachedFileUpdate, Windows. cameraSettings, Windows. FileOpenPicker, Windows. fileTypeAssociation, Windows. fileSavePicke, Windows. lockScreenCall, Windows. printtasksettings, Windows. Protocol, Windows. Search, Windows. shareTarget. Örneğin:

    ```xml
    <Extensions>
      <uap:Extension Category="windows.alarm"/>
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>
      <uap:Extension Category="windows.protocol">
        <uap:Protocol Name="mailto" DesiredView="useHalf">
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>
        </uap:Protocol>
      </uap:Extension>
    </Extensions>

    ```

11. **Uıap** ad alanını chatMessageNotification türündeki arka plan görevlerine ekleyin. Örneğin:

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
     <BackgroundTasks ServerName="MyBackgroundTasks">
        <uap:Task Type="chatMessageNotification"/>
      </BackgroundTasks>
    </Extension>

    ```

12. Çerçeve bağımlılıklarını değiştirin. Tüm öğelere yayımcı adı ekleyin \<PackageDependency> ve henüz belirtilmemişse bir MinVersion belirtin.

     **Eski:** \<PackageDependency> dosyalarında

    ```xml
    <Dependencies>
     <PackageDependency Name="Microsoft.VCLibs.120.00" />
    </Dependencies>

    ```

     **Yeni:** \<PackageDependency> dosyalarında

    ```xml
    <Dependencies>
     <PackageDependency
          Name="Microsoft.VCLibs.120.00"
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"
          MinVersion="12.0.30113.0" />
    </Dependencies>

    ```

     Kullanmakta olduğunuz gerçek çerçeve için uygun yayımcı ve MinVersion değerlerini kullanın. Bu adların Windows 10 için değiştiklerini unutmayın.

13. GattCharacteristicNotification ve rfcommConnection arka plan türü görevlerini Bluetooth tür göreviyle değiştirin. Örneğin:

     **ESKISI**

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
                <Task Type="rfcommConnection"/>
               <Task Type="gattCharacteristicNotification"/>
    </BackgroundTasks>
    </Extension>
    ```

     **Yeni:** Bluetooth tür görevi ile.

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
               <Task Type="bluetooth"/>
    </BackgroundTasks>
    </Extension>
    ```

14. Bluetooth. RFCOMM ve Bluetooth. genericAttributeProfile Bluetooth cihaz yeteneklerini genel Bluetooth özelliği ile değiştirin. Örneğin:

     **ESKISI**

    ```xml
    <Capabilities>
      <m2:DeviceCapability Name="bluetooth.rfcomm">
        <m2:Device Id="any">
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>
        </m2:Device>
      </m2:DeviceCapability>
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">
        <m2:Device Id="any">
         <m2:Function Type="name:heartRate"/>
        </m2:Device>
      </m2:DeviceCapability>
    </Capabilities>
    ```

     **Yeni:** Genel Bluetooth özelliği ile değiştirilmiştir.

    ```xml
    <Capabilities>
      <uap:DeviceCapability Name="bluetooth"/>
    </Capabilities>

    ```

15. Kullanım dışı bırakılmış öğeleri kaldırın.

    1. İçin bu öznitelikler \<VisualElements> kullanımdan kaldırılmıştır ve kaldırılmalı:

       - \<VisualElements>Öznitelikler: ForegroundText, Toastyetenekli

       - \<DefaultTile>DefaultSize özniteliği

       - \<ApplicationView>Öğe

         Örneğin:

       ```xml
       <m2:VisualElements
           …
           ForegroundText="dark"
           ToastCapable="true">
       <m2:DefaultTile DefaultSize="square150x150Logo"/>
         <m2:ApplicationView MinWidth="width320"/>
       </m2:VisualElements>

       ```

    2. Windows. Contact ve Windows. contactPicker uzantılarını ve bu uzantıların altındaki tüm öğeleri kaldırın.

16. Package. appxmanifest dosyasını kaydedin. Ardından Visual Studio 'Yu kapatın.

17. Çözümünüzü yeniden kullanabilmek için bazı gizli dosyaları kaldırmanız gerekir.

    1. Dosya Gezgini 'ni açın, araç çubuğunda **Görünüm** ' e tıklayın ve **gizli öğeler** ve **dosya adı uzantıları**' nı seçin. Bu klasörü makinenizde açın: \<path for the location of your solution> \\ . vs \\ {Project Name} \v14. . Suo dosya uzantısına sahip bir dosya varsa, silin.

    2. Şimdi çözümünüzün bulunduğu klasöre geri dönün. Çözümünüzde bulunan projeler için herhangi bir klasör açın. Bu proje klasörlerinin içindeki bir dosyanın. csproj. User veya. vbproj. User uzantısı varsa, silin.

         Artık çözümünüzü Visual Studio 'da yeniden açabilirsiniz. Evrensel Windows Platformu kullanarak uygulamanızda kod oluşturmaya, yapılandırmaya ve hata ayıklamaya hazırlanın.

         Evrensel Windows Platformu ile ilgili yeniliklerin avantajlarından yararlanmak için [kodunuzu nasıl uyarlayacağınızı](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) öğrenin.

## <a name="changes-required-for-existing-universal-windows-apps-created-with-visual-studio-2015-rc"></a><a name="PreviousVersions"></a> Visual Studio 2015 RC ile oluşturulan mevcut Evrensel Windows uygulamaları için gereken değişiklikler
 Visual Studio 2015 RC ile Windows 10 Universal uygulamaları oluşturduysanız, Visual Studio 2015 ' nin en son sürümüyle yüklü Evrensel Windows Platformu sürümünü kullanmak için projenizi yeniden hedeflemeniz gerekir. Önceki tüm sürümleri desteklenmez. Uygulamanızı oluşturmak için kullandığınız dile bağlı olarak, gerekli değişiklikler farklıdır:

- [C#/vb uygulamaları](#RCUpdate10CSharp)

- [C++ uygulamaları](#RCUpdate10CPlusPlus)

### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a><a name="RCUpdate10CSharp"></a> C#/vb projelerinizi en son Evrensel Windows Platformu kullanacak şekilde güncelleştirin
 Çözümünüzü mevcut uygulamanız için açtığınızda, uygulamanızın bir güncelleştirme gerektirdiğini görürsünüz:

 ![Projenizi Çözüm Gezgini görüntüleyin](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")

 Bu projeyi Çözüm Gezgini yeniden yüklemeyi seçerseniz Şu iletişim kutusu görüntülenir:

 ![Doğru SDK 'Yı kullanmak için uygulamanızı yeniden hedefleyin](../misc/media/missingsdkforuap.png "MissingSDKforUAP")

 Projeniz için Evrensel Windows Platformu SDK 'Sı artık desteklenmediğinden, bu dosyayı yükleyemeyeceksiniz. Tamam ' a tıkladıktan sonra aşağıdaki adımları izlemeniz yeterlidir.

##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>C#/vb projelerinizi en son Evrensel Windows Platformu kullanacak şekilde güncelleştirin

1. Yüklediğiniz Evrensel Windows Platformu bulmak için şu klasörü açın: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü her bir Evrensel Windows Platformu klasörlerinin listesini içerir. Klasör adı, yüklediğiniz Evrensel Windows Platformu sürümdür. Örneğin, bu Windows 10 cihazında yüklü Evrensel Windows Platformu sürüm 10.0.10240.0 vardır.

    ![Yüklü sürümleri görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

    Evrensel Windows Platformu birden fazla sürümü yüklenebilir. Uygulamanız için en son sürümü kullanmanızı öneririz.

2. Dosya Gezgini 'ni kullanarak UWP projenizin depolandığı klasöre gidin. packages.config dosyasını silin ve bu klasörde yeni bir. JSON dosyası oluşturun. Dosyayı project.jsolarak adlandırın ve ardından şu içeriği bu dosyaya ekleyin:

   ```json

   {
     "dependencies": {
       "Microsoft.ApplicationInsights": "1.0.0",
       "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
       "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
       "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
     },
     "frameworks": {
       "uap10.0": {}
     },
     "runtimes": {
       "win10-arm": {},
       "win10-arm-aot": {},
       "win10-x86": {},
       "win10-x86-aot": {},
       "win10-x64": {},
       "win10-x64-aot": {}
     }
   }

   ```

3. Visual Studio ile, C#/vb Universal Windows uygulamanızı içeren çözümünüzü açın. Proje dosyanızın (. csproj veya. vbproj dosyası) güncelleştirilmesi gerektiğini görürsünüz. Proje dosyasına sağ tıklayın ve bu dosyayı düzenlemek için seçin.

    ![Projeye sağ tıklayın ve Düzenle ' yi seçin.](../misc/media/uap-editproject.png "UAP_EditProject")

4. \<PropertyGroup>Ve öğelerini içeren öğesini bulun \<TargetPlatformVersion> \<TargetPlatformMinVersion> . Ve öğelerinin var olan değerini \<TargetPlatformVersion> \<TargetPlatformMinVersion> yüklediğiniz Evrensel Windows platformu aynı sürümü olacak şekilde değiştirin.

    Evrensel Windows uygulamaları için varsayılan varlık ölçeği 200 ' dir. Visual Studio 2015 RC ile oluşturulan ve 100 ' de ölçeklendirilmiş varlıklar içeren projeler, \<UapDefaultAssetScale> Bu PropertyGroup 'a bir 100 değeri olan bir öğe eklemeniz gerekecektir. [Varlıklar ve ölçekler](https://msdn.microsoft.com/library/jj679352.aspx)hakkında daha fazla bilgi edinin.

5. UWP uzantısı SDK 'larına herhangi bir başvuru eklediyseniz (örneğin: Windows Mobile SDK) SDK sürümünü güncelleştirmeniz gerekir. Örneğin, bu \<SDKReference> öğe:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.0.1">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

    Şu şekilde değiştirilmelidir:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.10240.0">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

6. \<Target>Şu değere sahip olan bir name özniteliğine sahip öğeyi bulun: Ensurtrıgetpackagebuildımports. Bu öğeyi ve tüm alt öğelerini silin.

   ```xml
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">
       <PropertyGroup>
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
       </PropertyGroup>
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />
   </Target>
   ```

7. \<Import>Aşağıdaki gibi Microsoft. Diagnostics. Tracing. EventSource ve Microsoft. ApplicationInsights 'a başvuran proje ve koşul öznitelikleriyle öğeleri bulun ve silin:

   ```xml
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />

   ```

8. \<ItemGroup> \<Reference> NuGet paketlerine alt öğeleri olan öğesini bulun. Gelecek bir adım için bu bilgilere ihtiyaç duyduğundan, başvurulan NuGet paketlerini göz önünde bulabilirsiniz. Visual Studio 2015 RC ile Visual Studio 2015 RTM arasındaki Windows 10 proje biçimi arasındaki önemli bir fark, RTM biçiminin [NuGet](/nuget/) sürüm 3 ' ü kullanmadır.

    \<ItemGroup>Ve tüm alt öğelerini kaldırın. Örneğin, Visual Studio RC ile oluşturulan UWP projesi, kaldırılması gereken aşağıdaki NuGet paketlerine sahip olacaktır:

   ```xml
   <ItemGroup>
       <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
         <Private>True</Private>
       </Reference>
     </ItemGroup>

   ```

9. \<ItemGroup>Öğe içeren öğeyi bulun \<AppxManifest> . \<None>İçerme özniteliği şu şekilde ayarlanmış bir öğe varsa: packages.config, silin. Ayrıca, \<None> içerme özniteliği içeren bir öğesi ekleyin ve değerini olarak ayarlayın: project.json.

10. Yaptığınız değişiklikleri kaydedin. Ardından proje dosyasını kapatın.

11. Çözüm Gezgini ' de proje dosyanıza sağ tıklayın ve bağlam menüsünden projeyi yeniden yükle ' yi seçin. Projenizdeki tüm dosyalar artık Çözüm Gezgini görüntülenmelidir.

12. Dosya ApplicationInsights.config Çözüm Gezgini seçin ve özelliklerini açın. Yapı eylemi özelliğini "Içerik" olarak ve çıkış dizinine Kopyala özelliğini "daha sonra Kopyala" olarak ayarlayın.

13. Projenizde Package. appxmanifest dosyasını açın.

    1. Öğesini bulun \<TargetDeviceFamily> . MinVersion ve Maxversionsınanan özniteliklerini, yüklediğiniz Evrensel Windows Platformu sürümüne karşılık gelecek şekilde değiştirin. Böyle:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Yaptığınız değişiklikleri kaydedin.

14. Önceki adımda sildiğiniz paketleri eklemek için NuGet yöneticisini kullanın. Visual Studio 2015 RC ile Visual Studio 2015 RTM arasındaki Windows 10 proje biçimi arasındaki önemli bir fark, RTM biçiminin [NuGet](/nuget/) sürüm 3 ' ü kullanmadır.

    Artık uygulamanızı kodleyebilir, oluşturabilir ve hata ayıklayabilirsiniz.

    Evrensel Windows uygulamalarınız için birim testi projelerine sahipseniz, [Bu adımları](#MigrateUnitTest)da izlemeniz gerekir.

### <a name="update-your-c-projects-to-use-the-latest-universal-windows-platform"></a><a name="RCUpdate10CPlusPlus"></a> C++ projelerinizi en son Evrensel Windows Platformu kullanacak şekilde güncelleştirin

1. Yüklediğiniz Evrensel Windows Platformu bulmak için şu klasörü açın: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü her bir Evrensel Windows Platformu klasörlerinin listesini içerir. Klasör adı, yüklediğiniz Evrensel Windows Platformu sürümdür. Örneğin, bu Windows 10 cihazında yüklü Evrensel Windows Platformu sürüm 10.0.10240.0 vardır.

     ![Yüklü sürümleri görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Evrensel Windows Platformu birden fazla sürümü yüklenebilir. Uygulamanız için en son sürümü kullanmanızı öneririz.

2. C++ Windows Evrensel uygulamanızı içeren çözümünüzü açın. Project. vcxproj dosyasına sağ tıklayın ve proje dosyasını kaldırmayı seçin. Proje kaldırıldıktan sonra proje dosyasına tekrar sağ tıklayın ve düzenlemeyi seçin.

     ![Projeyi kaldırma, sonra proje dosyasını düzenleme](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")

3. \<PropertyGroup>Koşul özniteliği içermeyen ancak bir öğesi içeren herhangi bir öğeyi bulun \<ApplicationTypeRevision> . ApplicationTypeRevision değerini 8,2 ' den 10,0 ' e güncelleştirin. Bir \<WindowsTargetPlatformVersion> ve öğesi ekleyin \<WindowsTargetPlatformMinVersion> ve değerlerini yüklediğiniz Evrensel Windows platformu sürümünün değeri olarak ayarlayın.

     Öğe \<EnableDotNetNativeCompatibleProfile> zaten yoksa, bir öğe ekleyin ve değerini true olarak ayarlayın.

     Evrensel Windows uygulamaları için varsayılan varlık ölçeği 200 ' dir. Visual Studio 2015 RC ile oluşturulan ve 100 ' de ölçeklendirilmiş varlıklar içeren projeler, \<UapDefaultAssetScale> Bu PropertyGroup 'a bir 100 değeri olan bir öğe eklemeniz gerekecektir. [Varlıklar ve ölçekler](https://msdn.microsoft.com/library/jj679352.aspx)hakkında daha fazla bilgi edinin.

     Bu \<PropertyGroup> öğe artık şuna benzer olacaktır:

    ```xml
    <PropertyGroup Label="Globals">
        …
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>
        <ApplicationType>Windows Store</ApplicationType>
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
        <UapDefaultAssetScale>100</UapDefaultAssetScale>
      </PropertyGroup>

    ```

4. Kalan her \<PropertyGroup> öğe için, öğenin sürüm yapılandırması olan bir koşul özniteliğine sahip olup olmadığını denetleyin. Varsa, ancak bir öğesi içermiyorsa bir \<UseDotNetNativeToolchain> tane ekleyin. Öğesi için değeri \<UseDotNetNativeToolchain> true olarak ayarlayın, şöyle:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

5. \<EnableDotNetNativeCompatibleProfile>.NET Native etkinleştirmek için öğeyi ve öğeyi güncelleştirmeniz gerekir \<UseDotNetNativeToolchain> , ancak C++ şablonlarında .NET Native etkinleştirilmemiştir.

     Yaptığınız değişiklikleri kaydedin. Ardından proje dosyasını kapatın.

6. Çözüm Gezgini ' de proje dosyanıza sağ tıklayın ve bağlam menüsünden projeyi yeniden yükle ' yi seçin. Projenizdeki tüm dosyalar artık Çözüm Gezgini görüntülenmelidir.

7. Projenizde Package. appxmanifest dosyasını açın.

    1. Öğesini bulun \<TargetDeviceFamily> . MinVersion ve Maxversionsınanan özniteliklerini, yüklediğiniz Evrensel Windows Platformu sürümüne karşılık gelecek şekilde değiştirin. Böyle:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Yaptığınız değişiklikleri kaydedin.

         Artık uygulamanızı kodleyebilir, oluşturabilir ve hata ayıklayabilirsiniz.

         Evrensel Windows uygulamalarınız için birim testi projelerine sahipseniz, [Bu adımları](#MigrateUnitTest)da izlemeniz gerekir.

## <a name="changes-required-for-existing-unit-test-projects-for-universal-windows-apps-created-with-visual-studio-2015-rc"></a><a name="MigrateUnitTest"></a> Visual Studio 2015 RC ile oluşturulan Evrensel Windows uygulamaları için mevcut birim testi projeleri için gereken değişiklikler
 Visual Studio 2015 RC ile Windows 10 Universal uygulamaları için birim testi projeleri oluşturduysanız, bu test projelerini Visual Studio 2015 ' nin en son sürümüyle kullanabilmek için proje dosyalarınızda bu ek değişiklikleri yapmanız gerekir. Uygulamanızı oluşturmak için kullandığınız dile bağlı olarak, gerekli değişiklikler farklıdır:

- [C#/vb uygulamaları](#UnitTestRCUpdate10CSharp)

- [C++ uygulamaları](#UnitTestRCUpdate10CPlusPlus)

### <a name="update-your-cvb-unit-test-projects"></a><a name="UnitTestRCUpdate10CSharp"></a> C#/vb birim testi projelerinizi güncelleştirme

1. Visual Studio ile, C#/vb birim testi projenizi içeren çözümünüzü açın. \<OuttputType>Öğesinin değerini olarak değiştirin: appcontainerexe.

   ```xml

   <OutputType>AppContainerExe</OutputType>

   ```

2. Bu öğe \<EnableCoreRuntime> değerini \</EnableCoreRuntime> aşağıdaki öğeyle değiştirin:

   ```xml

   <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>

   ```

3. Aşağıdaki satırları kaldırın:

   ```xml

   <PropertyGroup>
       <AppXPackage>True</AppXPackage>
       <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
       <PlatformTarget>AnyCPU</PlatformTarget>
       <DebugType>pdbonly</DebugType>
       <Optimize>true</Optimize>
       <OutputPath>bin\Release\</OutputPath>
       <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
       <ErrorReport>prompt</ErrorReport>
       <WarningLevel>4</WarningLevel>
    </PropertyGroup>

   ```

4. Bu öğeyi bu \<UseDotNetNativeToolchain> \</UseDotNetNativeToolchain> özellik gruplarına bir alt öğe olarak true olarak ekleyin:

   ```xml

   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">

   ```

5. Aşağıdaki öğeleri silin \<ItemGroup> :

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="packages.config" />
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\Default.rd.xml" />
      <Content Include="Assets\Logo.scale-240.png" />
      <Content Include="Assets\SmallLogo.scale-240.png" />
      <Content Include="Assets\SplashScreen.scale-240.png" />
      <Content Include="Assets\Square71x71Logo.scale-240.png" />
      <Content Include="Assets\StoreLogo.scale-240.png" />
      <Content Include="Assets\WideLogo.scale-240.png" />
   </ItemGroup>

   ```

    Bunları şu öğelerle değiştirin:

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTestApp.xaml.cs">
         <DependentUpon>UnitTestApp.xaml</DependentUpon>
      </Compile>
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <ApplicationDefinition Include="UnitTestApp.xaml">
         <Generator>MSBuild:Compile</Generator>
         <SubType>Designer</SubType>
      </ApplicationDefinition>
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\UnitTestApp.rd.xml" />
      <Content Include="Assets\LockScreenLogo.scale-200.png" />
      <Content Include="Assets\SplashScreen.scale-200.png" />
      <Content Include="Assets\Square150x150Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
      <Content Include="Assets\StoreLogo.png" />
      <Content Include="Assets\Wide310x150Logo.scale-200.png" />
   </ItemGroup>
   ```

6. Yeni bir birim testi projesi oluşturun ve bu yeni projeden UnitTestApp. xaml ve UnitTestApp.xaml.cs dosyalarını güncelleştirdiğiniz mevcut birim testi projenize kopyalayın.

7. Yeni birim testi projesinin Özellikler klasöründen UnitTestApp.rd.xml dosyasını güncelleştirdiğiniz mevcut birim testi projenizin Özellikler klasörüne kopyalayın.

8. Projenizde Package. appxmanifest dosyasını açın. Sonra bu öğeleri bundan silin:

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="vstest.executionengine.appcontainer.uap.exe"
            EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
         <uap:VisualElements
            DisplayName="UnitTestProject1"
            Square150x150Logo="Assets\Logo.png"
            Square44x44Logo="Assets\SmallLogo.png"
            Description="UnitTestProject1"
            BackgroundColor="#464646">
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClientServer" />
   </Capabilities>
   ```

    Bu silinmiş öğeleri aşağıdaki öğelerle değiştirin. Aşağıdaki öğelerde UnitTestProject1 yerine proje adına bağlı olarak ProjectName için uygun değeri kullanın:

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="$targetnametoken$.exe"
            EntryPoint="UnitTestProject1.App">
         <uap:VisualElements
               DisplayName="UnitTestProject1"
               Square150x150Logo="Assets\Square150x150Logo.png"
               Square44x44Logo="Assets\Square44x44Logo.png"
               Description="UnitTestProject1"
               BackgroundColor="transparent">
            <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClient" />
   </Capabilities>
   ```

   Artık birim testlerinizi çalıştırabilirsiniz.

### <a name="update-your-c-projects-to-use-the-latest-universal-windows-platform"></a><a name="UnitTestRCUpdate10CPlusPlus"></a> C++ projelerinizi en son Evrensel Windows Platformu kullanacak şekilde güncelleştirin

1. Visual Studio ile, C++ birim testi projenizi içeren çözümünüzü açın. Aşağıdaki öğeleri kaldırın:

    ```xml

    <TestApplication>true</TestApplication>
    <AppxPackage>True</AppxPackage>
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>
    <EnableCoreRuntime>false</EnableCoreRuntime>

    ```

2. Şu öğeleri, \<ProjectConfiguration> \<ItemGroup Label="ProjectConfigurations"> zaten bu filde içinde olmayan bu öğenin altına ekleyin:

    ```xml

    <ProjectConfiguration Include="Debug|x64">
       <Configuration>Debug</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|x64">
       <Configuration>Release</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>

    ```

3. Bu öğenin her oluşumunu Değiştir:

    ```xml

    <ConfigurationType>DynamicLibrary</ConfigurationType>

    ```

     Şununla değiştirin:

    ```xml

    <ConfigurationType>Application</ConfigurationType>

    ```

4. \<PropertyGroup>Zaten dosyada değilse, bu öğeleri ekleyin:

    ```xml

    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>true</UseDebugLibraries>
       <PlatformToolset>v140</PlatformToolset>
    </PropertyGroup>
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>false</UseDebugLibraries>
       <WholeProgramOptimization>true</WholeProgramOptimization>
       <PlatformToolset>v140</PlatformToolset>
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
    </PropertyGroup>

    ```

5. Bu öğenin her oluşumunu Değiştir:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
    ```

     Şununla değiştirin:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>

    ```

6. Bu öğenin her oluşumunu Değiştir:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

     Şununla değiştirin:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

7. Bu \<ItemDefinitionGroup> öğeleri, zaten diğer öğeleri içeren bölüme ekleyin \<ItemDefinitionGroup> :

    ```xml

    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
    <Link>
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
    </Link>
    </ItemDefinitionGroup>
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
       <Link>
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
       </Link>
    </ItemDefinitionGroup>

    ```

8. Aşağıdaki öğeyi silin \< ItemGroup> :

    ```xml

    <ItemGroup>
       <Image Include="Assets\Logo.scale-100.png" />
       <Image Include="Assets\SmallLogo.scale-100.png" />
       <Image Include="Assets\StoreLogo.scale-100.png" />
       <Image Include="Assets\SplashScreen.scale-100.png" />
       <Image Include="Assets\WideLogo.scale-100.png" />
    </ItemGroup>

    ```

     Bu \<ItemGroup> öğeyle değiştirin:

    ```xml

    <ItemGroup>
       <Image Include="Assets\LockScreenLogo.scale-200.png" />
       <Image Include="Assets\SplashScreen.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
       <Image Include="Assets\Square150x150Logo.scale-200.png" />
       <Image Include="Assets\StoreLogo.png" />
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />
    </ItemGroup>

    ```

9. Aşağıdaki öğeyi silin \< ItemGroup> :

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
    </ItemGroup>
    ```

     Şu \<ItemGroup> öğelerle değiştirin:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
       <ClInclude Include="UnitTestApp.xaml.h">
          <DependentUpon>UnitTestApp.xaml</DependentUpon>
       </ClInclude>
    </ItemGroup>
    <ItemGroup>
       <ApplicationDefinition Include="UnitTestApp.xaml">
          <SubType>Designer</SubType>
       </ApplicationDefinition>
    </ItemGroup>

    ```

10. Aşağıdaki öğeyi silin:

    ```xml
    <ClCompile Include="UnitTest.cpp"/>
    ```

     Şu \<CICompile> öğelerle değiştirin:

    ```xml

    <ClCompile Include="UnitTestApp.xaml.cpp">
       <DependentUpon>UnitTestApp.xaml</DependentUpon>
    </ClCompile>
    <ClCompile Include="UnitTest.cpp"/>

    ```

11. Bu öğeyi Ekle:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
    ```

     Dosyadaki bu öğenin üstünde:

    ```xml

    <ItemGroup>
       <Xml Include="UnitTestApp.rd.xml" />
    </ItemGroup>
    ```

12. Yeni bir birim testi C++ projesi oluşturun ve UnitTestApp. xaml, UnitTestApp. xaml. cpp, UnitTestApp. xaml. h ve UnitTestApp.rd.xml dosyalarını bu projeden güncelleştirdiğiniz mevcut projenize kopyalayın.

13. Projenizde Package. appxmanifest dosyasını açın. Sonra bu öğeleri bundan silin:

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
             Executable="vstest.executionengine.appcontainer.uap.exe"
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
          <uap:VisualElements
             DisplayName="UnitTestProject1"
             Square150x150Logo="Assets\Logo.png"
             Square44x44Logo="Assets\SmallLogo.png"
             Description="UnitTestProject1"
             BackgroundColor="#464646">
             <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClientServer" />
    </Capabilities>

    ```

     Bu silinmiş öğeleri aşağıdaki öğelerle değiştirin. Aşağıdaki öğelerde UnitTestProject1 yerine proje adına bağlı olarak ProjectName için uygun değeri kullanın:

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
                Executable="$targetnametoken$.exe"
                EntryPoint="UnitTestProject1.App">
          <uap:VisualElements
                DisplayName="UnitTestProject1"
                Square150x150Logo="Assets\Square150x150Logo.png"
                Square44x44Logo="Assets\Square44x44Logo.png"
                Description="UnitTestProject1"
                BackgroundColor="transparent">
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
                <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClient" />
    </Capabilities>

    ```