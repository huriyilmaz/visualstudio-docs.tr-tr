---
title: Derleme Sistemini Özelleştirme
description: Bu makale, Mac için Visual Studio tarafından kullanılan MSBuild derleme sistemine kısa bir Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: c9545b701dc3041fa57dacf5288fe8ab29cd9ea49b89afba1645505d185399f8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121349830"
---
# <a name="customizing-the-build-system"></a>Derleme sistemini özelleştirme

Bu Microsoft Build Engine, uygulamalar için bir platformdur. Diğer adıyla MSBuild altyapı, Microsoft tarafından geliştirilmiştir ve .NET uygulamalarının inşa 1. Mono çerçevesinin, Microsoft'un Derleme Altyapısı'nın **xbuild** adlı kendi uygulaması da vardır. Ancak şu anda xbuild, tüm işletim sistemlerinde MSBuild kullanımdan çıkarıldı.

**MSBuild,** Mac için Visual Studio'daki projeler için derleme sistemi olarak kullanılır ve kaynak dosyalar gibi bir dizi giriş alarak çalışır ve bunları yürütülebilir dosyalar gibi çıkışlara dönüştürerek çalışır. Derleyici gibi araçları kullanarak bu çıkışı elde ediyor.

## <a name="msbuild-file"></a>MSBuild dosyası

MSBuild projenizin parçası olan Öğeleri (görüntü kaynakları gibi) ve projenizi derlemek için gereken Özellikleri  tanımlayan proje dosyası olarak adlandırılan bir XML dosyası kullanır.  Bu proje dosyası, C# projeleri gibi ile biten `proj` bir dosya `.csproj` uzantısına her zaman sahip olur.

### <a name="viewing-the-msbuild-file"></a>MSBuild görüntüleme

Proje MSBuild sağ tıklar ve Bulıcı'da Ortaya Çıkar'ı seçerek **bir dosya bulun.** Bulıcı penceresi, aşağıdaki görüntüde gösterildiği gibi dosya dahil olmak üzere projeniz ile `.csproj` ilgili tüm dosyaları ve klasörleri görüntüler:

![Bulıcı'da csproj konumu](media/customizing-build-system-image1.png)

dosyasını yeni bir sekmede görüntülemek Mac için Visual Studio proje adınıza sağ tıklayın ve Araçlar'a göz > `.csproj` **dosyasını düzenleyin:**

![kaynak düzenleyicisinde csproj'ı açma](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Dosyanın MSBuild oluşturma

Tüm MSBuild zorunlu bir kök öğe `Project` içerir, şöyle:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Genellikle, proje bir dosyayı da içeri `.targets` aktarır. Bu dosya, çeşitli dosyaları işlemeyi ve derlemeyi açıklayan birçok kuralı içerir. İçeri aktarma işlemi genellikle dosyanın alt `proj` kısmında görünür ve C# projeleri için aşağıdaki gibi görünür:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Hedefler dosyası bir diğer MSBuild dosyasıdır. Bu dosya, MSBuild proje tarafından yeniden kullanılabilir bir kod içerir. Örneğin, özelliğiyle (veya değişkeniyle) temsil edilen bir dizinde bulunan dosya, C# kaynak dosyalarından C# derlemeleri derleme `Microsoft.CSharp.targets` `MSBuildBinPath` mantığını içerir.

### <a name="items-and-properties"></a>Öğeler ve özellikler

Veri verilerinde iki temel veri MSBuild *vardır: öğeler* ve *özellikler*, aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.

#### <a name="properties"></a>Özellikler

Özellikler, derlemeyi etkileyen ayarları (derleyici seçenekleri gibi) depolamak için kullanılan anahtar/değer çiftleridir.

Bir PropertyGroup kullanılarak ayarlanır ve herhangi bir sayıda özellik içeren herhangi bir sayıda PropertiesGroup içerebilir.

Örneğin, basit bir konsol uygulaması için PropertyGroup aşağıdaki XML'ye benzer olabilir:

```xml
<PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
    <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
    <OutputType>Exe</OutputType>
    <RootNamespace>refactoring</RootNamespace>
    <AssemblyName>refactoring</AssemblyName>
    <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
</PropertyGroup>
```

Özellikler, söz dizimi kullanılarak ifadelerden `$()` başvurulabilirsiniz. Örneğin, `$(Foo)` özelliğinin değeri olarak `Foo` değerlendirilir. Özellik ayarlanmazsa, herhangi bir hata olmadan boş bir dize olarak değerlendirilir.

#### <a name="items"></a>Öğeler

Öğeler, derleme sistemine girişlerle listeler veya kümeler olarak ilgilenmek için bir yol sağlar ve genellikle dosyaları temsil eder. Her öğenin bir öğe *türü, öğe* özellikleri *ve* isteğe bağlı rastgele meta verileri *vardır.* Tek MSBuild üzerinde çalışmayabilirsiniz; öğe kümesi olarak adlandırılan bir türdeki tüm öğeleri *alır*

Öğeler bir bildirerek `ItemGroup` oluşturulur. Herhangi bir sayıda öğe içeren herhangi bir sayıda ItemGroup olabilir.

Örneğin, aşağıdaki kod parçacığı iOS Başlatma Ekranlarını oluşturur. Başlatma Ekranları, görüntünün yolu `BundleResource` olarak özelikle birlikte derleme türüne sahip olur:

```xml
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```

 Öğe kümeleri, söz dizimi kullanılarak ifadelerden `@()` başvurulabilirsiniz. Örneğin, `@(BundleResource)` Tüm BundleResource öğeleri anlamına gelen BundleResource öğe kümesi olarak değerlendirilir. Bu türde bir öğe yoksa, herhangi bir hata olmadan boş olur.

## <a name="resources-for-learning-msbuild"></a>Öğrenme kaynakları MSBuild

Aşağıdaki kaynaklar, daha ayrıntılı bir şekilde MSBuild için kullanılabilir:

* [MSBuild Genel bakış](/visualstudio/msbuild/msbuild)
* [MSBuild Kavram](/visualstudio/msbuild/msbuild-concepts)
