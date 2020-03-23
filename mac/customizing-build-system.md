---
title: Derleme Sistemini Özelleştirme
description: Bu makale, Mac için Visual Studio tarafından kullanılan MSBuild yapı sistemine kısa bir giriştir
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 0c511c448136210038f1034321a2828e5153add1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128383"
---
# <a name="customizing-the-build-system"></a>Yapı sistemini özelleştirme

Microsoft Build Engine, uygulama oluşturmak için bir platformdur. MSBuild olarak da bilinen motor, Microsoft tarafından geliştirilmiştir ve .NET uygulamalarının oluşturulmasına olanak sağlar. Mono çerçeve de Microsoft'un Build Engine kendi uygulaması vardır, **xbuild**denir. Ancak şu anda xbuild, tüm işletim sistemlerinde MSBuild'in kullanılması lehine aşamalı olarak devre dışı bırakılmıştır.

**MSBuild,** Visual Studio for Mac'teki projeler için yapı sistemi olarak kullanılır ve kaynak dosyalar gibi bir dizi girdi alarak çalışır ve bunları yürütülebilir dosyalar gibi çıktılara dönüştürür. Derleyici gibi araçları çağırarak bu çıktıyı elde eder.

## <a name="msbuild-file"></a>MSBuild dosyası

MSBuild, projenizin parçası olan *Öğeleri* (görüntü kaynakları gibi) ve projenizi oluşturmak için gereken *Özellikleri* tanımlayan proje dosyası adı verilen bir XML dosyası kullanır. Bu proje dosyasında her zaman `proj`C# `.csproj` projeleri gibi biten bir dosya uzantısı olacaktır.

### <a name="viewing-the-msbuild-file"></a>MSBuild dosyasını görüntüleme

Proje adınızı sağ tıklayarak ve **Finder'da Göster'i**seçerek MSBuild dosyasını bulun. Bulma penceresi, `.csproj` aşağıdaki resimde gösterildiği gibi, dosya da dahil olmak üzere projenizle ilgili tüm dosya ve klasörleri görüntüler:

![Finder csproj konumu](media/customizing-build-system-image1.png)

Mac için `.csproj` Visual Studio'da yeni bir sekmeyi görüntülemek için proje adınızı sağ tıklatın ve **Dosyayı > Araçlara**göz atın:

![kaynak editör csproj açılması](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>MSBuild dosyasının bileşimi

Tüm MSBuild dosyaları gibi `Project` zorunlu bir kök öğesi içerir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Genellikle, proje de bir `.targets` dosya yı içeri aktaracak. Bu dosya, çeşitli dosyaların nasıl işlenir ve oluşturulan açıklayan kurallar birçok içerir. Alma işlemi genellikle dosyanızın `proj` altına doğru görünür ve C# projeleri için aşağıdaki gibi görünür:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Hedefler dosyası başka bir MSBuild dosyasıdır. Bu dosya, birden çok proje tarafından yeniden kullanılabilir MSBuild kodu içerir. Örneğin, `MSBuildBinPath` özellik `Microsoft.CSharp.targets` (veya değişken) tarafından temsil edilen bir dizinde bulunan dosya, C# kaynak dosyalarından C# derlemeleri oluşturma mantığını içerir.

### <a name="items-and-properties"></a>Öğeler ve özellikler

MSBuild'te iki temel veri türü vardır: aşağıdaki bölümlerde daha ayrıntılı olarak açıklanan *öğeler* ve *özellikler.*

#### <a name="properties"></a>Özellikler

Özellikler, derleyici seçenekleri gibi derlemeyi etkileyen ayarları depolamak için kullanılan anahtar/değer çiftleridir.

Bir Özellik Grubu kullanılarak ayarlanırlar ve herhangi bir sayıda özellik içerebilen herhangi bir sayıda PropertiesGroups içerebilirler.

Örneğin, basit bir konsol uygulaması için PropertyGroup aşağıdaki XML gibi görünebilir:

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

Özellikler `$()` sözdizimini kullanarak ifadelerden başvurulabilir. Örneğin, `$(Foo)` `Foo` özelliğin değeri olarak değerlendirilir. Özellik ayarlanmadıysa, herhangi bir hata olmadan boş bir dize olarak değerlendirilir.

#### <a name="items"></a>Öğeler

Öğeler, yapı sistemine giren girdilerle liste veya küme olarak başa çıkmanın bir yolunu sağlar ve genellikle dosyaları temsil eder. Her öğenin bir madde *türü,* bir öğe *spec*ve isteğe bağlı rasgele *meta veri*vardır. MSBuild'in tek tek öğeler üzerinde çalışmadığını, belirli bir tür adı verilen öğe *kümesinin* tüm öğelerini aldığını unutmayın

Öğeler bir `ItemGroup`. Herhangi bir sayıda öğe içerebilen herhangi bir sayıda Öğe Grubu olabilir.

Örneğin, aşağıdaki kod parçacığı iOS Başlatma Ekranlarını oluşturur. Başlatma Ekranları, görüntüye giden yol olarak spec ile, yapı türüne `BundleResource`sahiptir:

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

 Madde kümeleri `@()` sözdizimini kullanarak ifadelerden yönlendirilebilir. Örneğin, `@(BundleResource)` tüm BundleResource öğeleri anlamına gelen BundleResource madde kümesi olarak değerlendirilir. Bu tür öğeler yoksa, herhangi bir hata olmadan boş olacaktır.

## <a name="resources-for-learning-msbuild"></a>MSBuild öğrenmek için kaynaklar

Aşağıdaki kaynaklar MSBuild hakkında daha ayrıntılı bilgi edinmek için kullanılabilir:

* [MSBuild'e Genel Bakış](/visualstudio/msbuild/msbuild)
* [MSBuild Kavramları](/visualstudio/msbuild/msbuild-concepts)
