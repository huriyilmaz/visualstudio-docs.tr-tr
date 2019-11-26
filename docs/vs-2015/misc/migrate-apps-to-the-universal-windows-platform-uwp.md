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
ms.openlocfilehash: 5794aa5ab7dc14932c65a9156ea9252e71731155
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299478"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Uygulamaları Evrensel Windows Platformu’na (UWP) geçirme
Visual Studio 2015 RTM ile kullanılabilmesi için, Windows Mağazası 8,1 uygulamaları, Windows Phone 8,1 uygulamaları veya Visual Studio 2015 RC ile oluşturulan Evrensel Windows uygulamaları için gerekli olan proje dosyalarınızda el ile yapılan değişiklikleri yapın. (Hem Windows uygulama projesi hem de Windows Phone projesi olan bir Windows 8.1 Universal uygulamanız varsa, her bir projeyi geçirmek için adımları izlemeniz gerekir.)

 Evrensel Windows Platformu, artık uygulamanızı bir veya daha fazla cihaz ailesinden hedefleyebilirsiniz. Evrensel Windows uygulamaları hakkında daha fazla bilgi edinmek istiyorsanız, bu [Platform kılavuzuna](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx)göz atın.

- [Mevcut C#/vb Windows mağazası 8,1 veya Windows Phone 8,1 uygulamalarınızı](#MigrateCSharp) Evrensel Windows platformu kullanacak şekilde geçirin.

- [ C++ Mevcut Windows mağazası 8,1 veya Windows Phone 8,1 uygulamalarınızı](#MigrateCPlusPlus) Evrensel Windows platformu kullanacak şekilde geçirin.

- [Visual Studio 2015 RC ile oluşturulan mevcut Evrensel Windows uygulamaları için gerekli değişiklikler](#PreviousVersions).

- [Visual Studio 2015 RC ile oluşturulan Evrensel Windows uygulamaları için mevcut birim testi projeleri için gerekli değişiklikler](#MigrateUnitTest).

  Tüm bu değişiklikleri yapmak istemiyorsanız, [mevcut uygulamalarınızın](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) yeni bir Evrensel Windows projesine nasıl bağlantı sağladığını öğrenin.

## <a name="MigrateCSharp"></a>C#/Vb Windows Mağazası 8,1 veya Windows Phone 8,1 uygulamalarınızı Evrensel Windows platformu kullanacak şekilde geçirin

#### <a name="migrate-your-cvb-project-files"></a>C#/Vb proje dosyalarınızı geçirin

1. Yüklediğiniz Evrensel Windows Platformu bulmak için şu klasörü açın: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü her bir Evrensel Windows Platformu klasörlerinin listesini içerir. Klasör adı, yüklediğiniz Evrensel Windows Platformu sürümdür. Örneğin, bu Windows 10 cihazında yüklü Evrensel Windows Platformu sürüm 10.0.10240.0 vardır.

     ![Yüklü sürümleri görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Evrensel Windows Platformu birden fazla sürümü yüklenebilir. Uygulamanız için en son sürümü kullanmanızı öneririz.

2. Dosya Gezgini 'ni kullanarak UWP projenizin depolandığı klasöre gidin. Bu klasörde bir. JSON dosyası oluşturun. Dosyayı şu şekilde adlandırın: Project. JSON ve sonra şu içeriği bu dosyaya ekleyin:

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

3. Varsayılan. RD. xml adlı bir dosyayı aşağıdaki içeriklerle oluşturun. Bir VB projeniz varsa, bu dosyayı projeniz için projem dizinine ekleyin. Bir C# projeniz varsa, bu dosyayı projenizin Özellikler dizinine ekleyin.

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

6. 8,1 değerine sahip \<TargetPlatformVersion > öğesini içeren \<PropertyGroup > öğesini bulun. Bu \<PropertyGroup > öğesi için aşağıdaki adımları uygulayın:

    1. \<platform > öğesinin değerini: **x86**olarak ayarlayın.

    2. \<targetPlatformIdentifier > öğesi ekleyin ve değerini: **UAP**olarak ayarlayın.

    3. \<TargetPlatformVersion > öğesinin var olan değerini yüklediğiniz Evrensel Windows Platformu sürümünün değeri olacak şekilde değiştirin. Ayrıca, bir \<TargetPlatformMinVersion > öğesi ekleyin ve aynı değere verin.

    4. \<MinimumVisualStudioVersion > öğesinin değerini: **14**olarak değiştirin.

    5. \<Projecttypeguid > öğesini aşağıda gösterildiği gibi değiştirin:

         C# için:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        ```

         VB için:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        ```

    6. \<EnableDotNetNativeCompatibleProfile > öğesi ekleyin ve değerini: **true**olarak ayarlayın.

    7. Evrensel Windows uygulamaları için varsayılan varlık ölçeği 200 ' dir. Projeniz 200 değerinde ölçeklendirilmemiş varlıklar içeriyorsa, bu PropertyGroup 'a varlıklarınızın ölçeğine sahip \<Uıapdefaultassetscale > öğesi eklemeniz gerekecektir. [Varlıklar ve ölçekler](https://msdn.microsoft.com/library/jj679352.aspx)hakkında daha fazla bilgi edinin.

         \<PropertyGroup > öğesi Şu örneğe benzer şekilde görünmelidir:

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

8. Koşul özniteliğinin bir parçası olarak AnyCPU platformu için yapılandırılmış \<PropertyGroup > öğelerini bulun. Bu öğeleri ve tüm alt öğelerini kaldırın. Visual Studio 2015 ' de Windows 10 uygulamaları için AnyCPU desteklenmez. Örneğin, bunlar gibi \<PropertyGroup > öğelerini kaldırmanız gerekir:

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

9. Kalan her \<PropertyGroup > öğesi için, öğenin Sürüm yapılandırmasına sahip bir koşul özniteliğine sahip olup olmadığını denetleyin. Varsa, ancak bir \<Usedotnetnativetoolzincirine > öğesi içermiyorsa bir tane ekleyin. \<Usedotnetnativetoolzincirine > öğesi için değeri true olarak ayarlayın:

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

10. Yalnızca Windows Phone projeleri için, bir \<targetPlatformIdentifier > öğesi içeren \<PropertyGroup > öğesini WindowsPhoneApp değeriyle kaldırın. Bu öğenin tüm alt öğelerini de kaldır:

    ```xml
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>
    </PropertyGroup>
    ```

11. \<AppxManifest > öğesini içeren \<ItemGroup > öğesini bulun. Aşağıdaki \<None > öğesini \<ItemGroup > öğesinin bir alt öğesi olarak ekleyin:

    ```xml
    <None Include="project.json" />
    ```

12. Projenize eklenen logo. png dosyaları (\<Içerik dahil = "Assets\Logo.scale-100.png"/>) gibi diğer varlıkları içeren \<ItemGroup > öğesini bulun. Aşağıdaki \<Content > alt öğesini bu \<ItemGroup > öğesine ekleyin:

     **İçin C#:**

    ```xml
    <Content Include="Properties\default.rd.xml" />
    ```

     **VB için:**

    ```xml
    <Content Include="My Project\default.rd.xml" />
    ```

13. \<ItemGroup > öğesini, alt öğeleri NuGet paketlerine > \<başvurusunu içerir. Projenizi yeniden yükledikten sonra NuGet Paket Yöneticisi ile indirmeniz gerekeceğinden, kullandığınız NuGet paketlerini bir yere göz atın. Bu \<ItemGroup > alt öğeleri ile birlikte kaldırın. Örneğin, UWP projesinde kaldırılması gereken aşağıdaki NuGet paketleri olabilir:

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

## <a name="MigrateCPlusPlus"></a>Evrensel Windows Platformu kullanmak C++ Için Windows Mağazası 8,1 veya Windows Phone 8,1 uygulamalarınızı geçirin

#### <a name="migrate-your-c-project-files"></a>C++ Proje dosyalarınızı geçirin

1. Yüklediğiniz Evrensel Windows Platformu bulmak için şu klasörü açın: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü her bir Evrensel Windows Platformu klasörlerinin listesini içerir. Klasör adı, yüklediğiniz Evrensel Windows Platformu sürümdür. Örneğin, bu Windows 10 cihazında yüklü Evrensel Windows Platformu sürüm 10.0.10240.0 vardır.

     ![Yüklü sürümleri görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Evrensel Windows Platformu birden fazla sürümü yüklenebilir. Uygulamanız için en son sürümü kullanmanızı öneririz.

2. Visual Studio 'da mevcut C++ Windows Mağazası 8,1 uygulamanızı veya Windows Phone 8,1 uygulamanızı içeren çözümünüzü açın.

     Çözüm Gezgini ' nde mevcut projenize sağ tıklayın ve ardından **Projeyi Kaldır**' ı seçin. Proje kaldırıldıktan sonra proje dosyasına tekrar sağ tıklayın ve. vcxproj dosyasını düzenlemeyi seçin.

     ![Proje&#45;dosyası ' na sağ tıklayın ve düzenlemek için seçin](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")

3. 8,1 değerine sahip \<ApplicationTypeRevision > öğesini içeren \<PropertyGroup > öğesini bulun. Bu \<PropertyGroup > öğesi için aşağıdaki adımları uygulayın:

    1. \<WindowsTargetPlatformVersion > öğesi ve bir \<WindowsTargetPlatformMinVersion > öğesi ekleyin ve bu değere yüklediğiniz Evrensel Windows Platformu sürümünün değerini verin.

    2. ApplicationTypeRevision öğesinin değerini 8,1 ' den 10,0 ' e güncelleştirin.

    3. \<MinimumVisualStudioVersion > öğesinin değerini: 14 olarak değiştirin.

    4. \<EnableDotNetNativeCompatibleProfile > öğesi ekleyin ve değerini: true olarak ayarlayın.

    5. Evrensel Windows uygulamaları için varsayılan varlık ölçeği 200 ' dir. Projeniz 200 değerinde ölçeklendirilmemiş varlıklar içeriyorsa, bu PropertyGroup 'a varlıklarınızın ölçeğine sahip \<Uıapdefaultassetscale > öğesi eklemeniz gerekecektir. [Varlıklar ve ölçekler](https://msdn.microsoft.com/library/jj679352.aspx)hakkında daha fazla bilgi edinin.

    6. Yalnızca Windows Phone projeleri için, \<ApplicationType > değerini Windows Phone 'den Windows Mağazası 'na değiştirin.

         \<PropertyGroup > öğesi Şu örneğe benzer şekilde görünmelidir:

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

4. \<Platformaraç takımı > öğesinin tüm örneklerini v140 değerine sahip olacak şekilde değiştirin. Örneğin:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

5. Kalan her \<PropertyGroup > öğesi için, öğenin Sürüm yapılandırmasına sahip bir koşul özniteliğine sahip olup olmadığını denetleyin. Varsa, ancak bir \<Usedotnetnativetoolzincirine > öğesi içermiyorsa bir tane ekleyin. \<Usedotnetnativetoolzincirine > öğesi için değeri true olarak ayarlayın:

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

## <a name="PackageManifest"></a>Paket bildirim dosyanızı tüm Windows Mağazası 8,1 veya Windows Phone 8,1 projeleriniz için güncelleştirin
 Çözümünüzde her bir proje için paket bildirim dosyasını güncelleştirmeniz gerekir.

#### <a name="update-your-package-manifest-file"></a>Paket bildirim dosyanızı güncelleştirme

1. Projenizde Package. appxmanifest dosyasını açın. Windows Mağazası ve Windows Phone projelerinin her biri için Package. AppxManifest dosyasını düzenlemeniz gerekir.

2. \<paketi > öğesini mevcut proje türüne göre yeni şemalarla güncelleştirmeniz gerekir. İlk olarak, bir Windows Mağazası veya Windows Phone projesi olup olmadığına bağlı olarak aşağıdaki şemaları kaldırın.

    **Windows Mağazası projesi Için eski:** \<paketiniz > öğesi şuna benzer.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">

   ```

    **Windows Phone projesi Için eski:** \<paketiniz > öğesi şuna benzer.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">
   ```

    **Evrensel Windows platformu Için yeni:** Aşağıdaki şemaları \<Package > öğesine ekleyin. Yeni kaldırdığınız şemaların öğelerinden ilişkili ad alanı tanımlayıcı öneklerini kaldırın. Ignorablenamespaces özelliğini şu şekilde güncelleştirin: UAP MP. Yeni \<paketinizin > öğesi şuna benzer görünmelidir.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
      IgnorableNamespaces= "uap mp">

   ```

3. \<Package > öğesine > alt öğesi \<bir bağımlılıklar ekleyin. Daha sonra bu \<> bağımlılıklara \<bir TargetDeviceFamily > alt öğesi ekleyin. Bu, Name, MinVersion ve MaxVersionTested. Name özniteliğine: Windows. Universal değerini verin. MinVersion ve Maxversion'in yüklediğiniz Evrensel Windows Platformu sürümünün değerini test edin. Bu öğe şuna benzer görünmelidir:

   ```xml
   <Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />
   </Dependencies>
   ```

4. **Yalnızca Windows Mağazası için:** \<paketi > öğesine \<MP: Phoneıdentity > alt öğesi eklemeniz gerekir. Phoneproductıd özniteliği ve Phonepublisherıd özniteliği ekleyin. Phoneproductıd 'yi, \<Identity > öğesindeki name özniteliğiyle aynı değere sahip olacak şekilde ayarlayın. PhonePublishedId değerini şu şekilde ayarlayın: 00000000-0000-0000-0000-000000000000. Böyle:

   ```xml
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>
   ```

5. \<önkoşulları > öğesini bulun ve bu öğeyi ve içerdiği tüm alt öğeleri silin.

6. **Uıap** ad alanını şu \<kaynak > öğelerine ekleyin: Scale, DXFeatureLevel. Örneğin:

   ```xml
   <Resources>
     <Resource Language="en-us"/>
    <Resource uap:Scale="180"/>
    <Resource uap:DXFeatureLevel="dx11"/>
   </Resources>

   ```

7. **UAP** ad alanını şu \<yetenek > öğelerine ekleyin: documentsLibrary, Resimkitaplığı, Videoslibrary, MusicLibrary, enterpriseAuthentication, sharedUserCertificates, removableStorage, randevular ve kişiler. Örneğin:

   ```xml
   <Capabilities>
     <uap:Capability Name="documentsLibrary"/>
     <uap:Capability Name="removableStorage"/>
   </Capabilities>

   ```

8. \<Görselleştirbir > öğesine ve alt öğelerinden herhangi birine **UAP** ad alanını ekleyin. Örneğin:

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

    **Yalnızca Windows Mağazası için geçerlidir:** Kutucuk boyutu adları değişti. \<Görselitelements > öğesindeki öznitelikleri, yeni yakınsanmış döşeme boyutunu yansıtacak şekilde değiştirin. 70x70, 71x71 olur ve 30x30, 44x44 olur.

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

9. **UAP** ad alanını \<ApplicationContentUriRules > ve onun tüm alt öğelerine ekleyin. Örneğin:

    ```xml
    <uap:ApplicationContentUriRules>
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>
      <uap:Rule Type="exclude" Match="*.pdf"/>
    </uap:ApplicationContentUriRules>

    ```

10. **UAP** ad alanını aşağıdaki \<uzantısına > öğelerine ve tüm alt öğelerine ekleyin: Windows. Accountpicturesağlamasını, Windows. alarm, Windows. Randevutmentsprovider Windows. autoPlayContent, Windows. autoPlayDevice, Windows. cachedFileUpdate, Windows. cameraSettings, Windows. fileOpenPicker, Windows. fileTypeAssociation, Windows. fileSavePicke, Windows. lockScreenCall, Windows. printTaskSettings, Windows. Protocol, Windows. Search, Windows. shareTarget. Örneğin:

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

12. Çerçeve bağımlılıklarını değiştirin. Tüm \<PackageDependency > öğelerine bir yayımcı adı ekleyin ve henüz belirtilmemişse bir MinVersion belirtin.

     **Eski:** \<packagedependency > öğesi

    ```xml
    <Dependencies>
     <PackageDependency Name="Microsoft.VCLibs.120.00" />
    </Dependencies>

    ```

     **Yeni:** \<packagedependency > öğesi

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

    1. \<Görselleştirmeli > için bu öznitelikler kullanımdan kaldırılmıştır ve kaldırılmalı:

       - \<Görselleştirmelements > öznitelikler: ForegroundText, Toastuyumlu

       - \<DefaultTile > öznitelik DefaultSize özniteliği

       - \<ApplicationView > öğesi

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

    1. Dosya Gezgini 'ni açın, araç çubuğunda **Görünüm** ' e tıklayın ve **gizli öğeler** ve **dosya adı uzantıları**' nı seçin. Makinenizde bu klasörü açın: çözümünüzün konumu için \<yol >\\. vs\\{Project Name} \v14. . Suo dosya uzantısına sahip bir dosya varsa, silin.

    2. Şimdi çözümünüzün bulunduğu klasöre geri dönün. Çözümünüzde bulunan projeler için herhangi bir klasör açın. Bu proje klasörlerinin içindeki bir dosyanın. csproj. User veya. vbproj. User uzantısı varsa, silin.

         Artık çözümünüzü Visual Studio 'da yeniden açabilirsiniz. Evrensel Windows Platformu kullanarak uygulamanızda kod oluşturmaya, yapılandırmaya ve hata ayıklamaya hazırlanın.

         Evrensel Windows Platformu ile ilgili yeniliklerin avantajlarından yararlanmak için [kodunuzu nasıl uyarlayacağınızı](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) öğrenin.

## <a name="PreviousVersions"></a>Visual Studio 2015 RC ile oluşturulan mevcut Evrensel Windows uygulamaları için gereken değişiklikler
 Visual Studio 2015 RC ile Windows 10 Universal uygulamaları oluşturduysanız, Visual Studio 2015 ' nin en son sürümüyle yüklü Evrensel Windows Platformu sürümünü kullanmak için projenizi yeniden hedeflemeniz gerekir. Önceki tüm sürümleri desteklenmez. Uygulamanızı oluşturmak için kullandığınız dile bağlı olarak, gerekli değişiklikler farklıdır:

- [C#/VB uygulamaları](#RCUpdate10CSharp)

- [C++gör](#RCUpdate10CPlusPlus)

### <a name="RCUpdate10CSharp"></a>C#/Vb projelerinizi en son Evrensel Windows platformu kullanacak şekilde güncelleştirin
 Çözümünüzü mevcut uygulamanız için açtığınızda, uygulamanızın bir güncelleştirme gerektirdiğini görürsünüz:

 ![Projenizi Çözüm Gezgini görüntüleyin](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")

 Bu projeyi Çözüm Gezgini yeniden yüklemeyi seçerseniz Şu iletişim kutusu görüntülenir:

 ![Doğru SDK 'Yı kullanmak için uygulamanızı yeniden hedefleyin](../misc/media/missingsdkforuap.png "MissingSDKforUAP")

 Projeniz için Evrensel Windows Platformu SDK 'Sı artık desteklenmediğinden, bu dosyayı yükleyemeyeceksiniz. Tamam ' a tıkladıktan sonra aşağıdaki adımları izlemeniz yeterlidir.

##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>C#/Vb projelerinizi en son Evrensel Windows platformu kullanacak şekilde güncelleştirin

1. Yüklediğiniz Evrensel Windows Platformu bulmak için şu klasörü açın: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü her bir Evrensel Windows Platformu klasörlerinin listesini içerir. Klasör adı, yüklediğiniz Evrensel Windows Platformu sürümdür. Örneğin, bu Windows 10 cihazında yüklü Evrensel Windows Platformu sürüm 10.0.10240.0 vardır.

    ![Yüklü sürümleri görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

    Evrensel Windows Platformu birden fazla sürümü yüklenebilir. Uygulamanız için en son sürümü kullanmanızı öneririz.

2. Dosya Gezgini 'ni kullanarak UWP projenizin depolandığı klasöre gidin. Packages. config dosyasını silin ve bu klasörde yeni bir. JSON dosyası oluşturun. Dosyayı şu şekilde adlandırın: Project. JSON ve sonra şu içeriği bu dosyaya ekleyin:

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

3. Visual Studio ile C#/vb Universal Windows uygulamanızı içeren çözümünüzü açın. Proje dosyanızın (. csproj veya. vbproj dosyası) güncelleştirilmesi gerektiğini görürsünüz. Proje dosyasına sağ tıklayın ve bu dosyayı düzenlemek için seçin.

    ![Projeye sağ tıklayın ve Düzenle ' yi seçin.](../misc/media/uap-editproject.png "UAP_EditProject")

4. \<TargetPlatformVersion > ve \<TargetPlatformMinVersion > öğelerini içeren \<PropertyGroup > öğesini bulun. \<TargetPlatformVersion > var olan değerini ve TargetPlatformMinVersion > öğelerini \<yüklediğiniz Evrensel Windows Platformu aynı sürümü olacak şekilde değiştirin.

    Evrensel Windows uygulamaları için varsayılan varlık ölçeği 200 ' dir. Visual Studio 2015 RC dahil edilen ve 100 ' de ölçeklendirilmiş olan projeler, bu PropertyGroup 'a bir 100 değeri olan bir \<UapDefaultAssetScale > öğesi eklemeniz gerekir. [Varlıklar ve ölçekler](https://msdn.microsoft.com/library/jj679352.aspx)hakkında daha fazla bilgi edinin.

5. UWP uzantısı SDK 'larına herhangi bir başvuru eklediyseniz (örneğin: Windows Mobile SDK) SDK sürümünü güncelleştirmeniz gerekir. Örneğin bu \<SDKReference > öğesi:

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

6. Şu değere sahip bir Name özniteliğiyle \<Target > öğesini bulun: Ensurtrts. Bu öğeyi ve tüm alt öğelerini silin.

   ```xml
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">
       <PropertyGroup>
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
       </PropertyGroup>
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />
   </Target>
   ```

7. Aşağıdaki gibi Microsoft. Diagnostics. Tracing. EventSource ve Microsoft. ApplicationInsights 'a başvuran proje ve koşul öznitelikleriyle \<Içeri aktarma > öğelerini bulun ve silin:

   ```xml
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />

   ```

8. > Öğeleri NuGet paketlerine > \<başvurusuna sahip \<ItemGroup bulun. Gelecek bir adım için bu bilgilere ihtiyaç duyduğundan, başvurulan NuGet paketlerini göz önünde bulabilirsiniz. Visual Studio 2015 RC ile Visual Studio 2015 RTM arasındaki Windows 10 proje biçimi arasındaki önemli bir fark, RTM biçiminin [NuGet](https://docs.microsoft.com/nuget/) sürüm 3 ' ü kullanmadır.

    \<ItemGroup > ve tüm alt öğelerini kaldırın. Örneğin, Visual Studio RC ile oluşturulan UWP projesi, kaldırılması gereken aşağıdaki NuGet paketlerine sahip olacaktır:

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

9. \<AppxManifest > öğesi içeren \<ItemGroup > öğesini bulun. Include özniteliği: Packages. config olarak ayarlanmış bir \<None > öğesi varsa, silin. Ayrıca, Include özniteliğiyle birlikte \<None > öğesi ekleyin ve değerini: Project. JSON olarak ayarlayın.

10. Yaptığınız değişiklikleri kaydedin. Ardından proje dosyasını kapatın.

11. Çözüm Gezgini ' de proje dosyanıza sağ tıklayın ve bağlam menüsünden projeyi yeniden yükle ' yi seçin. Projenizdeki tüm dosyalar artık Çözüm Gezgini görüntülenmelidir.

12. Çözüm Gezgini ' de ApplicationInsights. config dosyasını seçin ve özelliklerini açın. Yapı eylemi özelliğini "Içerik" olarak ve çıkış dizinine Kopyala özelliğini "daha sonra Kopyala" olarak ayarlayın.

13. Projenizde Package. appxmanifest dosyasını açın.

    1. \<TargetDeviceFamily > öğesini bulun. MinVersion ve Maxversionsınanan özniteliklerini, yüklediğiniz Evrensel Windows Platformu sürümüne karşılık gelecek şekilde değiştirin. Böyle:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Yaptığınız değişiklikleri kaydedin.

14. Önceki adımda sildiğiniz paketleri eklemek için NuGet yöneticisini kullanın. Visual Studio 2015 RC ile Visual Studio 2015 RTM arasındaki Windows 10 proje biçimi arasındaki önemli bir fark, RTM biçiminin [NuGet](https://docs.microsoft.com/nuget/) sürüm 3 ' ü kullanmadır.

    Artık uygulamanızı kodleyebilir, oluşturabilir ve hata ayıklayabilirsiniz.

    Evrensel Windows uygulamalarınız için birim testi projelerine sahipseniz, [Bu adımları](#MigrateUnitTest)da izlemeniz gerekir.

### <a name="RCUpdate10CPlusPlus"></a>C++ Projelerinizi en son Evrensel Windows platformu kullanacak şekilde güncelleştirin

1. Yüklediğiniz Evrensel Windows Platformu bulmak için şu klasörü açın: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü her bir Evrensel Windows Platformu klasörlerinin listesini içerir. Klasör adı, yüklediğiniz Evrensel Windows Platformu sürümdür. Örneğin, bu Windows 10 cihazında yüklü Evrensel Windows Platformu sürüm 10.0.10240.0 vardır.

     ![Yüklü sürümleri görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Evrensel Windows Platformu birden fazla sürümü yüklenebilir. Uygulamanız için en son sürümü kullanmanızı öneririz.

2. C++ Windows Evrensel uygulamanızı içeren çözümünüzü açın. Project. vcxproj dosyasına sağ tıklayın ve proje dosyasını kaldırmayı seçin. Proje kaldırıldıktan sonra proje dosyasına tekrar sağ tıklayın ve düzenlemeyi seçin.

     ![Projeyi kaldırma, sonra proje dosyasını düzenleme](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")

3. Koşul özniteliği içermeyen, ancak bir \<ApplicationTypeRevision > öğesi içeren bir \<PropertyGroup > öğesi bulun. ApplicationTypeRevision değerini 8,2 ' den 10,0 ' e güncelleştirin. \<WindowsTargetPlatformVersion > ve bir \<WindowsTargetPlatformMinVersion > öğesi ekleyin ve değerlerini yüklediğiniz Evrensel Windows Platformu sürümünün değeri olarak ayarlayın.

     \<EnableDotNetNativeCompatibleProfile > öğesi ekleyin ve öğesi zaten yoksa değeri true olarak ayarlayın.

     Evrensel Windows uygulamaları için varsayılan varlık ölçeği 200 ' dir. Visual Studio 2015 RC dahil edilen ve 100 ' de ölçeklendirilmiş olan projeler, bu PropertyGroup 'a bir 100 değeri olan bir \<UapDefaultAssetScale > öğesi eklemeniz gerekir. [Varlıklar ve ölçekler](https://msdn.microsoft.com/library/jj679352.aspx)hakkında daha fazla bilgi edinin.

     Bu nedenle, bu \<PropertyGroup > öğesi artık şuna benzer:

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

4. Kalan her \<PropertyGroup > öğesi için, öğenin Sürüm yapılandırmasına sahip bir koşul özniteliğine sahip olup olmadığını denetleyin. Varsa, ancak bir \<Usedotnetnativetoolzincirine > öğesi içermiyorsa bir tane ekleyin. \<Usedotnetnativetoolzincirine > öğesi için değeri true olarak ayarlayın:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

5. .NET Native etkinleştirmek için \<EnableDotNetNativeCompatibleProfile > öğesini ve \<Usedotnetnativetoolzincirine > öğesini güncelleştirmeniz gerekir, ancak C++ şablonlarda .NET Native etkin değildir.

     Yaptığınız değişiklikleri kaydedin. Ardından proje dosyasını kapatın.

6. Çözüm Gezgini ' de proje dosyanıza sağ tıklayın ve bağlam menüsünden projeyi yeniden yükle ' yi seçin. Projenizdeki tüm dosyalar artık Çözüm Gezgini görüntülenmelidir.

7. Projenizde Package. appxmanifest dosyasını açın.

    1. \<TargetDeviceFamily > öğesini bulun. MinVersion ve Maxversionsınanan özniteliklerini, yüklediğiniz Evrensel Windows Platformu sürümüne karşılık gelecek şekilde değiştirin. Böyle:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Yaptığınız değişiklikleri kaydedin.

         Artık uygulamanızı kodleyebilir, oluşturabilir ve hata ayıklayabilirsiniz.

         Evrensel Windows uygulamalarınız için birim testi projelerine sahipseniz, [Bu adımları](#MigrateUnitTest)da izlemeniz gerekir.

## <a name="MigrateUnitTest"></a>Visual Studio 2015 RC ile oluşturulan Evrensel Windows uygulamaları için mevcut birim testi projeleri için gereken değişiklikler
 Visual Studio 2015 RC ile Windows 10 Universal uygulamaları için birim testi projeleri oluşturduysanız, bu test projelerini Visual Studio 2015 ' nin en son sürümüyle kullanabilmek için proje dosyalarınızda bu ek değişiklikleri yapmanız gerekir. Uygulamanızı oluşturmak için kullandığınız dile bağlı olarak, gerekli değişiklikler farklıdır:

- [C#/VB uygulamaları](#UnitTestRCUpdate10CSharp)

- [C++gör](#UnitTestRCUpdate10CPlusPlus)

### <a name="UnitTestRCUpdate10CSharp"></a>C#/Vb birim testi projelerinizi güncelleştirin

1. Visual Studio ile C#/vb birim testi projenizi içeren çözümünüzü açın. \<OuttputType > öğesinin değerini: AppContainerExe olarak değiştirin.

   ```xml

   <OutputType>AppContainerExe</OutputType>

   ```

2. Bu öğeyi \<EnableCoreRuntime > false\</EnableCoreRuntime > aşağıdaki öğeyle değiştirin:

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

4. Bu öğe \<Usedotnetnativetoolzincirini > true\</Usedotnetnativetoolzincirine > bir alt öğe olarak bu özellik gruplarına ekleyin:

   ```xml

   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">

   ```

5. Aşağıdaki \<ItemGroup > öğelerini silin:

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

7. Yeni birim testi projesinin Özellikler klasöründen UnitTestApp. RD. xml dosyasını, güncelleştirmekte olduğunuz mevcut birim testi projenizin Özellikler klasörüne kopyalayın.

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

### <a name="UnitTestRCUpdate10CPlusPlus"></a>C++ Projelerinizi en son Evrensel Windows platformu kullanacak şekilde güncelleştirin

1. Visual Studio ile, C++ birim testi projenizi içeren çözümünüzü açın. Aşağıdaki öğeleri kaldırın:

    ```xml

    <TestApplication>true</TestApplication>
    <AppxPackage>True</AppxPackage>
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>
    <EnableCoreRuntime>false</EnableCoreRuntime>

    ```

2. Şu \<ProjectConfiguration > öğelerini bu öğenin altına ekleyin \<ItemGroup etiketi = "ProjectConfigurations" > Bu filde henüz yoksa:

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

4. Bu \<PropertyGroup > öğelerini zaten dosyada yoksa ekleyin:

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

7. Bu \<ItemDefinitionGroup > öğelerini zaten diğer \<ItemDefinitionGroup > öğelerini içeren bölüme ekleyin:

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

8. Aşağıdaki \< ItemGroup > öğesini silin:

    ```xml

    <ItemGroup>
       <Image Include="Assets\Logo.scale-100.png" />
       <Image Include="Assets\SmallLogo.scale-100.png" />
       <Image Include="Assets\StoreLogo.scale-100.png" />
       <Image Include="Assets\SplashScreen.scale-100.png" />
       <Image Include="Assets\WideLogo.scale-100.png" />
    </ItemGroup>

    ```

     Bu \<ItemGroup > öğesiyle değiştirin:

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

9. Aşağıdaki \< ItemGroup > öğesini silin:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
    </ItemGroup>
    ```

     Bu \<ItemGroup > öğeleriyle değiştirin:

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

     Bu \<Cıile > öğeleriyle değiştirin:

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

12. Yeni bir birim testi C++ projesi oluşturun ve bu projeden UnitTestApp. xaml, UnitTestApp. xaml. cpp, UnitTestApp. xaml. h ve UnitTestApp. RD. xml dosyalarını güncelleştirdiğiniz mevcut projenize kopyalayın.

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