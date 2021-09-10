---
title: Derleme Sistemini Özelleştirme
description: bu makale, Mac için Visual Studio tarafından kullanılan MSBuild derleme sistemine kısa bir giriş niteliğindedir
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 0c511c448136210038f1034321a2828e5153add1
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964770"
---
# <a name="customizing-the-build-system"></a>Yapı sistemini özelleştirme

Microsoft Build Engine, uygulama oluşturmaya yönelik bir platformdur. MSBuild olarak da bilinen altyapı, Microsoft tarafından geliştirilmiştir ve .net uygulamalarının oluşturulmasına izin verir. Mono çerçevesinin Ayrıca, **xbuild** adlı Microsoft Build Engine uygulamasına sahip olması gerekir. ancak, şu anda xbuild, tüm işletim sistemlerinde MSBuild kullanımı için kullanıma hazır.

**MSBuild** , Mac için Visual Studio projeler için derleme sistemi olarak kullanılır ve kaynak dosyalar gibi bir giriş kümesi alarak ve bunları yürütülebilir dosyalar gibi çıkışlara dönüştürür. Derleyici gibi araçları çağırarak bu çıktıyı elde eder.

## <a name="msbuild-file"></a>MSBuild dosyası

MSBuild, projenizin bir parçası olan *öğeleri* (görüntü kaynakları gibi) ve projenizi oluşturmak için gereken *özellikleri* tanımlayan bir proje dosyası olarak adlandırılan bir XML dosyası kullanır. Bu proje dosyası `proj` , `.csproj` C# projeleri için gibi her zaman bir dosya uzantısına sahip olacaktır.

### <a name="viewing-the-msbuild-file"></a>MSBuild dosyasını görüntüleme

proje adına sağ tıklayıp **Finder 'da göster '** i seçerek MSBuild dosyasını bulun. Finder penceresinde, `.csproj` aşağıdaki görüntüde gösterildiği gibi, dosyası dahil olmak üzere projenizle ilgili tüm dosya ve klasörler görüntülenir:

![Finder 'da csproj konumu](media/customizing-build-system-image1.png)

`.csproj`Mac için Visual Studio yeni bir sekmede göstermek için, proje adına sağ tıklayın ve **dosyayı düzenle > araçlar**'a gidin:

![Kaynak düzenleyicisinde csproj açılıyor](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>MSBuild dosyasının oluşturulması

tüm MSBuild dosyaları zorunlu bir kök `Project` öğe içerir, örneğin:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Genellikle proje de bir dosyayı içeri aktarır `.targets` . Bu dosya, çeşitli dosyaların nasıl işleyeceğini ve oluşturulacağını betimleyen kuralların çoğunu içerir. İçeri aktarma genellikle dosyanızın en altına doğru görünür `proj` ve C# projeleri için şuna benzer şekilde görünür:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

hedef dosya başka bir MSBuild dosyasıdır. bu dosya birden fazla proje tarafından yeniden kullanılabilir MSBuild kod içeriyor. Örneğin, `Microsoft.CSharp.targets` Özelliği (veya değişkeni) tarafından temsil edilen bir dizinde bulunan dosyası `MSBuildBinPath` , c# kaynak dosyalarından c# derlemeleri oluşturmaya yönelik mantığı içerir.

### <a name="items-and-properties"></a>Öğeler ve Özellikler

MSBuild iki temel veri türü vardır: *öğeler* ve *özellikler* aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.

#### <a name="properties"></a>Özellikler

Özellikler, derleme seçenekleri gibi derlemeyi etkileyen ayarları depolamak için kullanılan anahtar/değer çiftleridir.

Bunlar bir PropertyGroup kullanılarak ayarlanırlar ve herhangi bir sayıda özellik içerebilen herhangi bir sayıda PropertiesGroups içerebilir.

Örneğin, bir basit konsol uygulaması için PropertyGroup aşağıdaki XML gibi görünebilir:

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

Özellikler, söz dizimi kullanılarak ifadelerden ifade edilebilir `$()` . Örneğin, `$(Foo)` özelliğinin değeri olarak değerlendirilir `Foo` . Özellik ayarlanmamışsa, herhangi bir hata olmadan boş bir dize olarak değerlendirilir.

#### <a name="items"></a>Öğeler

Öğeler, derleme sistemine listeler veya kümeler olarak giriş ile ilgili bir yol sağlar ve genellikle dosyaları temsil eder. Her öğenin bir öğe *türü*, bir öğe *belirtimi* ve isteğe bağlı rastgele *meta veriler* vardır. MSBuild bağımsız öğeler üzerinde çalışmadığına, belirli bir türün tüm öğelerini (öğe *kümesi* olarak adlandırılır) aldığını unutmayın

Öğeler bir bildirerek oluşturulur `ItemGroup` . Herhangi bir sayıda öğe içerebilen herhangi bir sayıda ItemGroups olabilir.

Örneğin, aşağıdaki kod parçacığı iOS başlatma ekranlarını oluşturur. Başlatma ekranları yapı türüne sahiptir ve bu özellik, `BundleResource` görüntünün yolu olarak belirtimdir:

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

 Öğe kümelerine sözdizimi kullanılarak deyimlerden başvurulabilir `@()` . Örneğin, paketleme `@(BundleResource)` leresource öğe kümesi olarak değerlendirilir. Bu, tüm paket \ kaynak öğeleri anlamına gelir. Bu türden bir öğe yoksa, herhangi bir hata olmadan boş olur.

## <a name="resources-for-learning-msbuild"></a>Öğrenme kaynakları MSBuild

daha ayrıntılı bilgi edinmek için aşağıdaki kaynaklar kullanılabilir MSBuild:

* [MSBuild Bakýþ](/visualstudio/msbuild/msbuild)
* [MSBuild Tiren](/visualstudio/msbuild/msbuild-concepts)
