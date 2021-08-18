---
title: MSBuild Ayrılmış ve Iyi bilinen Özellikler | Microsoft Docs
description: ayrılmış ve iyi bilinen MSBuild, proje dosyası ve MSBuild ikilileri hakkında bilgi depolayan önceden tanımlanmış özellikler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 534e6c3de1046398df277b6ca05566c41674062b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108661"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild ayrılmış ve tanınmış özellikleri

MSBuild, proje dosyası ve MSBuild ikilileri hakkında bilgi depolayan önceden tanımlanmış özellikler kümesi sağlar. bu özellikler diğer MSBuild özellikleriyle aynı şekilde değerlendirilir. Örneğin, özelliğini kullanmak için `MSBuildProjectFile` , yazın `$(MSBuildProjectFile)` .

 MSBuild, ayrılmış ve iyi bilinen özellikleri önceden tanımlamak için aşağıdaki tablodaki değerleri kullanır. Ayrılmış Özellikler geçersiz kılınamaz, ancak aynı adlı ortam özellikleri, genel özellikler veya proje dosyasında belirtilen özellikler kullanılarak iyi bilinen özellikler geçersiz kılınabilir.

## <a name="reserved-and-well-known-properties"></a>Ayrılmış ve iyi bilinen Özellikler

bu bölümdeki tabloda önceden tanımlanmış MSBuild özellikler gösterilmektedir. tablodaki örnek sütun, aşağıdaki örnek proje dosyası ile ilgilidir ve ' de bulunduğu varsayılır `C:\Source\Repos\ConsoleApp1\ConsoleApp1` ve MSBuild özel komut satırı seçenekleri olmadan çağrıldığında, Visual Studio 2019 sürüm 16,7 ' nin önizleme derlemesi olan bu özelliklerin değerlerini gösterir.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

| Özellik | Ayrılmış veya iyi bilinen | Açıklama | Örnek |
|----------------------------------|------------------------| - | - |
| `MSBuildBinPath` | Ayrılmıştır | kullanılmakta olan MSBuild ikililerin bulunduğu klasörün mutlak yolu (örneğin, *c:\ Windows \\ \<versionNumber> \microsoft.net\framework*). MSBuild dizinindeki dosyalara başvurmanız gerekirse bu özellik faydalıdır.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildExtensionsPath` | İyi bilinen | .NET Framework 4 ' te tanıtılan: varsayılan değerleri ve arasında bir fark yoktur `MSBuildExtensionsPath` `MSBuildExtensionsPath32` . `MSBUILDLEGACYEXTENSIONSPATH`Önceki sürümlerde varsayılan değerinin davranışını etkinleştirmek için ortam değişkenini null olmayan bir değere ayarlayabilirsiniz `MSBuildExtensionsPath` .<br /><br /> .NET Framework 3,5 ve önceki sürümlerde, varsayılan değeri, `MSBuildExtensionsPath` geçerli işlemin bit büyüklüğüne bağlı olarak, *\program files \\* veya *\program files (x86)* klasörü altındaki MSBuild alt klasörünün yolunu işaret eder. Örneğin, 64 bit bir makinedeki 32 bitlik bir işlem için bu özellik, *\Program Files (x86)* klasörünü işaret eder. 64 bit makinede 64 bitlik bir işlem için bu özellik *\Program Files* klasörünü işaret eder.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin.<br /><br /> Bu konum, özel hedef dosyaları yerleştirmek için kullanışlı bir yerdir. örneğin, hedef dosyalarınız *\program files \ MSBuild \myfiles\northwind.exe dizinine* yüklenip bu XML kodu kullanılarak proje dosyalarına aktarılabilir:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath32` | İyi bilinen | *\program files* veya *\program files (x86)* klasörü altındaki MSBuild alt klasörünün yolu. Yol her zaman 32 bit makinedeki 32-bit *\Program Files (x86)* klasörünü ve 64-bit makinesindeki *\Program dosyalarını* işaret eder. ". Ayrıca bkz `MSBuildExtensionsPath` `MSBuildExtensionsPath64` . ve.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath64` | İyi bilinen | *\program Files* klasörü altındaki MSBuild alt klasörünün yolu. 64 bitlik bir makine için bu yol her zaman *\Program Files* klasörünü işaret eder. 32 bitlik bir makine için bu yol boştur. Ayrıca bkz `MSBuildExtensionsPath` `MSBuildExtensionsPath32` . ve.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. | `C:\Program Files\MSBuild`|
| `MSBuildInteractive` | Ayrılmıştır | `true`MSBuild etkileşimli olarak çalışıyorsa, kullanıcı girişine izin verir. Bu ayar, `-interactive` komut satırı seçeneği tarafından denetlenir. | `false` |
| `MSBuildLastTaskResult` | Ayrılmıştır | `true` önceki görev herhangi bir hata olmadan tamamlanırsa (Uyarılar olsa bile) veya `false` önceki görevde hatalar varsa. Genellikle, bir görevde bir hata oluştuğunda, hata bu projede gerçekleşen son şeydir. Bu nedenle, bu özelliğin değeri hiçbir `false` şekilde bu senaryolar haricinde değildir:<br /><br /> - `ContinueOnError` [görev öğesinin özniteliği (MSBuild)](../msbuild/task-element-msbuild.md) , `WarnAndContinue` (veya `true` ) veya olarak ayarlandığında `ErrorAndContinue` .<br /><br /> -, bir `Target` alt öğe olarak bir ıbir ıda [(MSBuild) öğesine](../msbuild/onerror-element-msbuild.md) sahip. | `true` |
| `MSBuildNodeCount` | Ayrılmıştır | Oluşturulurken kullanılan eşzamanlı işlem sayısı üst sınırı. Bu, komut satırında **-maxcpucount** için belirttiğiniz değerdir. Değer belirtmeden **-maxcpucount** belirttiyseniz, `MSBuildNodeCount` bilgisayardaki işlemci sayısını belirtir. Daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md) ve [paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). | 1 |
| `MSBuildProgramFiles32` | Ayrılmıştır | 32 bit program klasörünün konumu; Örneğin, *C:\Program Files (x86)*.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. | `C:\Program Files (x86)`|
| `MSBuildProjectDefaultTargets` | Ayrılmıştır | Öğesinin özniteliğinde belirtilen hedeflerin tamamı listesi `DefaultTargets` `Project` . Örneğin, aşağıdaki `Project` öğe bir özellik değerine sahip olacaktır `MSBuildDefaultTargets` `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >` | `Build`|
| `MSBuildProjectDirectory` | Ayrılmıştır | Proje dosyasının bulunduğu dizinin mutlak yolu, örneğin *C:\company\myproduct*.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. | `C:\Source\Repos\ConsoleApp1\ConsoleApp1` |
| `MSBuildProjectDirectoryNoRoot` | Ayrılmıştır | `MSBuildProjectDirectory`Kök sürücü hariç, özelliğin değeri.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. | `Source\Repos\ConsoleApp1\ConsoleApp1`|
| `MSBuildProjectExtension` | Ayrılmıştır | Proje dosyasının süresi de dahil olmak üzere dosya adı uzantısı; Örneğin, *. proj*. | `.csproj`|
| `MSBuildProjectFile` | Ayrılmıştır | Proje dosyasının dosya adı uzantısı da dahil olmak üzere dosyanın tamamı. Örneğin, *MyApp. proj*. | `ConsoleApp1.csproj`|
| `MSBuildProjectFullPath` | Ayrılmıştır | Dosya adı uzantısı da dahil olmak üzere, proje dosyasının mutlak yolu ve tam dosya adı. Örneğin, *C:\mycompany\myproduct\myapp.exe*. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj`|
| `MSBuildProjectName` | Ayrılmıştır | Dosya adı uzantısı olmadan proje dosyasının dosya adı; Örneğin, *MyApp*. | `ConsoleApp1` |
| `MSBuildRuntimeType` | Ayrılmıştır | Şu anda yürütülmekte olan çalışma zamanının türü. MSBuild 15 ' te tanıtılmıştır. değer tanımsız olabilir (MSBuild 15 ' ten önce) `Full` .NET Framework MSBuild, `Core` MSBuild .net Core üzerinde çalıştığını (örneğin `dotnet build` ,) veya `Mono` MSBuild Mono üzerinde çalıştığını gösterir. | `Full` |
| `MSBuildStartupDirectory` | Ayrılmıştır | MSBuild çağrıldığı klasörün mutlak yolu. Bu özelliği kullanarak, her dizinde *\<dirs> . proj* dosyaları oluşturmadan bir proje ağacındaki belirli bir noktanın altındaki her şeyi oluşturabilirsiniz. Bunun yerine, burada gösterildiği gibi yalnızca bir projeniz vardır — örneğin, *c:\traversal.proj*.<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Ağaçta herhangi bir noktada derlemek için şunu yazın:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin. | `c:\Source\Repos\ConsoleApp1` |
| `MSBuildThisFile` | Ayrılmıştır | Öğesinin dosya adı ve dosya uzantısı kısmı `MSBuildThisFileFullPath` . | `ConsoleApp1.csproj` |
| `MSBuildThisFileDirectory` | Ayrılmıştır | Öğesinin dizin bölümü `MSBuildThisFileFullPath` .<br /><br /> Yola son ters eğik çizgiyi ekleyin. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileDirectoryNoRoot` | Ayrılmıştır | `MSBuildThisFileFullPath`Kök sürücü hariç, öğesinin dizin bölümü.<br /><br /> Yola son ters eğik çizgiyi ekleyin. | `Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileExtension` | Ayrılmıştır | Öğesinin dosya adı uzantısı kısmı `MSBuildThisFileFullPath` . | `.csproj` |
| `MSBuildThisFileFullPath` | Ayrılmıştır | Çalıştıran hedefi içeren projenin veya hedef dosyanın mutlak yolu.<br /><br /> İpucu: asıl proje dosyasına göre değil, hedef dosya ile ilişkili olan bir hedefler dosyasında göreli bir yol belirtebilirsiniz. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj` |
| `MSBuildThisFileName` | Ayrılmıştır | Dosya adı uzantısı olmadan öğesinin dosya adı kısmı `MSBuildThisFileFullPath` . | `ConsoleApp1` |
| `MSBuildToolsPath` | Ayrılmıştır | değeriyle ilişkili MSBuild sürümünün yükleme `MSBuildToolsVersion` yolu.<br /><br /> Yola son ters eğik çizgiyi dahil etmek yok.<br /><br /> Bu özellik geçersiz kılınamaz. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildToolsVersion` | Ayrılmıştır | Projeyi derlemek MSBuild araç kümesi sürümü.<br /><br /> Not: MSBuild araç kümesi, uygulama oluşturmak için kullanılan görevlerden, hedeflerden ve araçlardan oluşur. Araçlar,csc.exeve *vbc.exe.* ** Daha fazla bilgi için [bkz. Araç Kümesi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)ve [Standart ve özel Araç Kümesi yapılandırmaları.](../msbuild/standard-and-custom-toolset-configurations.md) | `Current` |
| `MSBuildVersion` | Ayrılmıştır | Projeyi derlemek MSBuild için kullanılan dosyanın sürümü. <br /><br/> Bu özellik geçersiz kılınabilir, aksi takdirde hata `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` iletisi döndürülür. | 16.11.0 |
| `MSBuildAssemblyVersion` | Ayrılmıştır | Projeyi derlemek MSBuild derlemelerinin sürümü. | 16.0 |
| `MSBuildFileVersion` | Ayrılmıştır | Projeyi derlemek için kullanılan MSBuild derlemelerinin 4 bölüm sürümü. | 16.11.0.30701 |
| `MSBuildSemanticVersion` | Ayrılmıştır | Projeyi derlemek için kullanılan derlemelerin tam semver 2.0 MSBuild derlemeleri. | 16.11.0-preview-21302-05+5e37cc992 |

## <a name="names-that-conflict-with-msbuild-elements"></a>Tüm öğelerle çakışan MSBuild adları

Yukarıdakilere ek olarak, MSBuild dil öğelerine karşılık gelen adlar kullanıcı tanımlı özellikler, öğeler veya öğe meta verileri için kullanılamaz:

* VisualStudioProject
* Hedef
* Propertygroup
* Çıktı
* ıtemgroup
* Usingtask
* ProjectExtensions
* Onerror
* ImportGroup
* Seçin:
* Ne zaman
* Aksi takdir -de

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
