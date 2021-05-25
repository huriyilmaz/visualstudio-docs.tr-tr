---
title: Özellik Işlevleri | Microsoft Docs
description: MSBuild özellik tanımlarında görüntülenen .NET Framework yöntemlerine yapılan çağrılar olan özellik işlevlerini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7c4a6254f15a4108c525231d0e5e93c6fc71bfb3
ms.sourcegitcommit: d3577395cf016f2836eb5a3c1d496cca6d449baa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110413344"
---
# <a name="property-functions"></a>Özellik işlevleri

Özellik işlevleri, MSBuild özellik tanımlarında görüntülenen .NET Framework yöntemlerine yapılan çağrılardır. Görevlerin aksine, özellik işlevleri hedeflerin dışında kullanılabilir ve herhangi bir hedef çalışmadan önce değerlendirilir.

MSBuild görevlerini kullanmadan, sistem saatini okuyabilir, dizeleri karşılaştırabilir, normal ifadelerle eşleştirebilir ve derleme betiğinizdeki diğer işlemleri gerçekleştirebilirsiniz. MSBuild, dizeyi sayı ve sayı olarak dizeye dönüştürmeye ve diğer dönüştürmeleri gereken şekilde dönüştürmeye çalışır.

Özellik işlevlerinden döndürülen dize değerleri [özel karakterlerin](msbuild-special-characters.md) atlanmalıdır. Değerin doğrudan proje dosyasına yerleştirilmiş gibi değerlendirilmesini istiyorsanız, `$([MSBuild]::Unescape())` özel karakterlerin atmasını kaldırmak için kullanın.

Özellik işlevleri .NET Framework 4 ve üzeri sürümlerde kullanılabilir.

## <a name="property-function-syntax"></a>Özellik işlevi sözdizimi

Bunlar, üç tür özellik işlevleridir; Her işlevde farklı bir sözdizimi vardır:

- String (örnek) özellik işlevleri
- Static özellik işlevleri
- MSBuild özellik işlevleri

### <a name="string-property-functions"></a>Dize özelliği işlevleri

Tüm derleme özelliği değerleri yalnızca dize değerleridir. Herhangi bir özellik değerinde çalışmak için dize (örnek) yöntemlerini kullanabilirsiniz. Örneğin, bu kodu kullanarak tam yolu temsil eden bir Build özelliğinden sürücü adını (ilk üç karakter) ayıklayabilirsiniz:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Static özellik işlevleri

Yapı betiğinizdeki birçok sistem sınıfının statik özelliklerine ve yöntemlerine erişebilirsiniz. Statik bir özelliğin değerini almak için aşağıdaki sözdizimini kullanın; burada sistem sınıfının \<Class> adıdır \<Property> ve özelliğin adıdır.

```
$([Class]::Property)
```

Örneğin, bir derleme özelliğini geçerli tarih ve saat olarak ayarlamak için aşağıdaki kodu kullanabilirsiniz.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Statik bir yöntem çağrısı yapmak için aşağıdaki sözdizimini kullanın; burada sistem sınıfının adıdır, yöntemin adıdır ve ( ) yöntemin \<Class> \<Method> parametre \<Parameters> listesidir:

```
$([Class]::Method(Parameters))
```

Örneğin, bir derleme özelliğini yeni bir GUID olarak ayarlamak için şu betiği kullanabilirsiniz:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

Statik özellik işlevlerinde, bu sistem sınıflarının herhangi bir statik yöntemini veya özelliğini kullanabilirsiniz:

- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.Char?displayProperty=nameWithType>
- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Enum?displayProperty=nameWithType>
- <xref:System.Guid?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.IO.Path?displayProperty=nameWithType>
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.OSPlatform?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- <xref:System.TimeSpan?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- <xref:System.UriBuilder?displayProperty=nameWithType>
- <xref:System.Version?displayProperty=nameWithType>
- <xref:Microsoft.Build.Utilities.ToolLocationHelper?displayProperty=nameWithType>

Ayrıca, aşağıdaki statik yöntemleri ve özellikleri kullanabilirsiniz:

- [System.Environment::CommandLine](xref:System.Environment.CommandLine*)
- [System.Environment::ExpandEnvironmentVariables](xref:System.Environment.ExpandEnvironmentVariables*)
- [System.Environment::GetEnvironmentVariable](xref:System.Environment.GetEnvironmentVariable*)
- [System.Environment::GetEnvironmentVariables](xref:System.Environment.GetEnvironmentVariables*)
- [System.Environment::GetFolderPath](xref:System.Environment.GetFolderPath*)
- [System.Environment::GetLogicalDrives](xref:System.Environment.GetLogicalDrives*)
- [System.IO.Directory::GetDirectories](xref:System.IO.Directory.GetDirectories*)
- [System.IO.Directory::GetFiles](xref:System.IO.Directory.GetFiles*)
- [System.IO.Directory::GetLastAccessTime](xref:System.IO.Directory.GetLastAccessTime*)
- [System.IO.Directory::GetLastWriteTime](xref:System.IO.Directory.GetLastWriteTime*)
- [System.IO.Directory::GetParent](xref:System.IO.Directory.GetParent*)
- [System.IO.File::Exists](xref:System.IO.File.Exists*)
- [System.Io.File::GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System.Io.File::GetAttributes](xref:System.IO.File.GetAttributes*)
- [System. ıO. File:: GetLastAccessTime](xref:System.IO.File.GetLastAccessTime*)
- [System. ıO. File:: GetLastWriteTime](xref:System.IO.File.GetLastWriteTime*)
- [System. ıO. File:: ReadAllText](xref:System.IO.File.ReadAllText*)

### <a name="calling-instance-methods-on-static-properties"></a>Statik özelliklerde örnek yöntemleri çağırma

Bir nesne örneği döndüren statik bir özelliğe eriştiğinizde, bu nesnenin örnek yöntemlerini çağırabilirsiniz. Bir örnek yöntemi çağırmak için aşağıdaki sözdizimini kullanın; burada \<Class> sistem sınıfının adıdır, özelliğin adıdır, \<Property> \<Method> yöntemin adıdır ve ( \<Parameters> ) yöntemi için parametre listesidir:

```
$([Class]::Property.Method(Parameters))
```

Sınıfın adı ad alanıyla tam olarak nitelenmelidir.

Örneğin, bir Build özelliğini bugün geçerli tarihe ayarlamak için aşağıdaki kodu kullanabilirsiniz.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>MSBuild özellik işlevleri

Derlemenize yönelik birkaç statik yönteme aritmetik, bit düzeyinde mantıksal ve çıkış karakteri desteği sağlamak için erişilebilir. Bu yöntemlere, \<Method> yöntemin adı ve ( \<Parameters> ) yöntemin parametre listesi olduğu aşağıdaki sözdizimini kullanarak erişirsiniz.

```
$([MSBuild]::Method(Parameters))
```

Örneğin, sayısal değerlere sahip iki özelliği birlikte eklemek için aşağıdaki kodu kullanın.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

MSBuild özellik işlevlerinin bir listesi aşağıdadır:

|İşlev imzası|Description|
|------------------------|-----------------|
|Double Ekle (çift a, çift b)|İki Double Ekle.|
|uzun ekleme (Long a, Long b)|İki Long ekleyin.|
|Çift çıkarma (çift a, çift b)|İki Double öğesini çıkar.|
|long Subtract(long a, long b)|İki uzun değer çıkar.|
|double Multiply(double a, double b)|İki çarpı çarpın.|
|long Multiply(long a, long b)|İki uzun değeri çarpın.|
|double Divide(double a, double b)|İki çifti bölün.|
|long Divide(long a, long b)|İki uzun bölme.|
|double Modulo(double a, double b)|Modulo iki double.|
|long Modulo(long a, long b)|Modulo iki longs.|
|string Escape(dize kaçışsız)|MSBuild kaçış kurallarına göre dizenin kaçış karakteri.|
|string Unescape(string escaped)|MSBuild kaçış kurallarına göre dizenin kaçış kaçışı.|
|int BitwiseOr(int first, int second)|Birinci ve ikincide bit `OR` olarak (birinci ve ikinci &#124; gerçekleştirin.|
|Int Bitwiseve (int First, int Second)|Birinci ve ikinci bir bit düzeyinde gerçekleştirin `AND` (ilk & saniye).|
|Int BitwiseXor (int First, int Second)|Birinci ve ikinci bit düzeyinde bit düzeyinde gerçekleştirin `XOR` (ilk ^ saniye).|
|Int Bitwıenot (ilk tamsayı)|Bit düzeyinde `NOT` (~ ilk) gerçekleştirin.|
|bool ısosplatform (dize platformString)|Geçerli işletim sistemi platformunun olup olmadığını belirtin `platformString` . `platformString` öğesinin üyesi olması gerekir <xref:System.Runtime.InteropServices.OSPlatform> .|
|bool ıosunixlike ()|Geçerli işletim sistemi bir UNIX sistemse true.|
|String NormalizePath (params String [] yol)|Belirtilen yolun kurallı tam yolunu alır ve geçerli işletim sistemi için doğru dizin ayırıcı karakterlerini içerdiğinden emin olur.|
|String NormalizeDirectory (params String [] yol)|Belirtilen dizinin kurallı tam yolunu alır ve sonunda eğik çizgi olduğundan emin olarak geçerli işletim sistemi için doğru dizin ayırıcı karakterlerini içerir.|
|dize Ensugeri çekme bölgesi (dize yolu)|Verilen yolun sonunda eğik çizgi yoksa bir tane ekleyin. Yol boş bir dize ise, onu değiştirmez.|
|String Getpathoffileyukarıdaki (dize dosyası, dize startingDirectory)|, İçin arama yapar ve geçerli derleme dosyasının konumunun üzerindeki dizin yapısındaki bir dosyanın tam yolunu ya da belirtilmişse öğesine göre döndürür `startingDirectory` .|
|GetDirectoryNameOfFileAbove(string startingDirectory, string fileName)|Belirtilen dizinde veya dizinin üzerindeki dizin yapısında yer alan bir dosyanın dizinini bulun ve geri dönüş.|
|string MakeRelative(string basePath, string path)|ile `path` ilgili `basePath` yapar. `basePath` mutlak bir dizin olmalıdır. Göreli `path` olarak bulunamazsa, tam olarak döndürülür. benzer `Uri.MakeRelativeUri` şekilde.|
|string ValueOrDefault(string conditionValue, string defaultValue)|'defaultValue' parametresinde dizeyi yalnızca 'conditionValue' parametresi boşsa, yoksa conditionValue değerini döndürür.|

## <a name="nested-property-functions"></a>İç içe özellik işlevleri

Aşağıdaki örnekte de olduğu gibi, daha karmaşık işlevler oluşturmak için özellik işlevlerini birleştirebilirsiniz.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Bu örnek, yolu tarafından <xref:System.IO.FileAttributes> `Archive` verilen dosyanın bit değerini (32 veya 0) `tempFile` döndürür. Numaralandı veri değerlerinin özellik işlevlerinde adına göre görüneyr. Bunun yerine sayısal değer (32) kullanılmalıdır.

Meta veriler iç içe özellik işlevlerinde de görünebilir. Daha fazla bilgi için bkz. [Toplu işleme.](../msbuild/msbuild-batching.md)

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

`DoesTaskHostExist`MSBuild'daki özellik işlevi, belirtilen çalışma zamanı ve mimari değerleri için bir görev ana bilgisayarının yüklü olup olmadığını döndürür.

Bu özellik işlevi aşağıdaki söz dizimlerini içerir:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

`EnsureTrailingSlash`MSBuild 'teki Özellik işlevi, zaten mevcut değilse sondaki eğik çizgi ekler.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild Getdirectorynameoffileyukarıdaki

MSBuild `GetDirectoryNameOfFileAbove` özelliği işlevi, yoldaki geçerli dizinin üzerindeki dizinlerde bulunan bir dosyayı arar.

 Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Aşağıdaki kod bu sözdizimine bir örnektir.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild Getpathoffileyukarıdaki

`GetPathOfFileAbove`MSBuild 'teki Özellik işlevi, geçerli dizinin üzerindeki dizin yapısında bulunuyorsa belirtilen dosyanın yolunu döndürür. Çağırmak için işlevsel olarak eşdeğerdir

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` özelliği işlevi bir kayıt defteri anahtarının değerini döndürür. Bu işlev iki bağımsız değişken alır, anahtar adı ve değer adı ve kayıt defterindeki değeri döndürür. Bir değer adı belirtmezseniz, varsayılan değer döndürülür.

Aşağıdaki örneklerde bu işlevin nasıl kullanıldığı gösterilmektedir:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

MSBuild `GetRegistryValueFromView` özelliği işlevi, kayıt defteri anahtarı, değeri ve bir veya daha fazla sıralı kayıt defteri görünümü verilen sistem kayıt defteri verilerini alır. Anahtar ve değer, her kayıt defteri görünümünde, bulunana kadar sırayla aranır.

Bu özellik işlevinin sözdizimi şöyledir:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Windows 64-bit işletim sistemi, 32 bit uygulamalar için bir **HKEY_LOCAL_MACHINE\SOFTWARE** kayıt defteri görünümü sunan **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** bir kayıt defteri anahtarı tutar.

Wow64 üzerinde çalışan 32 bitlik bir uygulama varsayılan olarak 32 bit kayıt defteri görünümüne, 64 bit uygulama ise 64 bit kayıt defteri görünümüne erişmektedir.

Aşağıdaki kayıt defteri görünümleri kullanılabilir:

|Kayıt defteri görünümü|Tanım|
|-------------------|----------------|
|RegistryView.Registry32|32 bit uygulama kayıt defteri görünümü.|
|RegistryView.Registry64|64 bit uygulama kayıt defteri görünümü.|
|RegistryView.Default|Uygulamanın üzerinde çalıştır olduğu işlemle eşleşen kayıt defteri görünümü.|

Bir örnek verilmiştir.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

önce 64 bit kayıt defteri görünümünde, sonra da 32 bit kayıt defteri görünümünde bakarak **ReferenceAssemblies** anahtarının **SLRuntimeInstallPath** verilerini alır.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

MSBuild `MakeRelative` özellik işlevi, birinci yola göre ikinci yolun göreli yolunu döndürür. Her yol bir dosya veya klasör olabilir.

Bu özellik işlevi aşağıdaki söz dizimlerini içerir:

```
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

Aşağıdaki kod, bu söz dizimlerinin bir örneğidir.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault

MSBuild `ValueOrDefault` özellik işlevi, null veya boş olmadığı sürece ilk bağımsız değişkeni döndürür. İlk bağımsız değişken null veya boşsa işlev ikinci bağımsız değişkeni döndürür.

Aşağıdaki örnekte bu işlevin nasıl kullanıldıkları gösterir.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault('$(UndefinedValue)', 'a'))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault('b', '$(Value1)'))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="msbuild-targetframework-and-targetplatform-functions"></a>MSBuild TargetFramework ve TargetPlatform işlevleri

MSBuild 16,7 ve üzeri, [TargetFramework ve TargetPlatform özelliklerini](msbuild-target-framework-and-target-platform.md)işlemek için çeşitli işlevler tanımlar.

|İşlev imzası|Description|
|------------------------|-----------------|
|Gettargetframeworkıdentifier (dize targetFramework)|Targetframeworkıdentifier 'ı TargetFramework 'ten ayrıştırın.|
|GetTargetFrameworkVersion (dize targetFramework)|TargetFrameworkVersion 'ı TargetFramework 'ten ayrıştırın.|
|Gettargetplatformıdentifier (dize targetFramework)|Targetplatformformıdentifier 'ı TargetFramework 'ten ayrıştırın.|
|GetTargetPlatformVersion (dize targetFramework)|Targetplatformden TargetPlatformVersion 'ı ayrıştırın.|
|Itargetframeworkcompatible (dize targetFrameworkTarget, String targetFrameworkCandidate)|Aday hedef çerçevesi bu hedef Framework ile uyumluysa ' true ', aksi takdirde false döndürün.|

Aşağıdaki örnek, bu işlevlerin nasıl kullanıldığını gösterir. 

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::GetTargetFrameworkIdentifier('net5.0-windows7.0'))</Value1>
        <Value2>$([MSBuild]::GetTargetFrameworkVersion('net5.0-windows7.0'))</Value2>
        <Value3>$([MSBuild]::GetTargetPlatformIdentifier('net5.0-windows7.0'))</Value3>
        <Value4>$([MSBuild]::GetTargetPlatformVersion('net5.0-windows7.0'))</Value4>
        <Value5>$([MSBuild]::IsTargetFrameworkCompatible('net5.0-windows', 'net5.0'))</Value5>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
        <Message Text="Value3 = $(Value3)" />
        <Message Text="Value4 = $(Value4)" />
        <Message Text="Value5 = $(Value5)" />
    </Target>
</Project>
```

```output
Value1 = .NETCoreApp
Value2 = 5.0
Value3 = windows
Value4 = 7.0
Value5 = True
```

## <a name="msbuild-version-comparison-functions"></a>MSBuild sürümü-karşılaştırma işlevleri

MSBuild 16,5 ve üzeri sürümleri temsil eden dizeleri karşılaştırmak için çeşitli işlevler tanımlar.

> [!Note]
> Koşullarda karşılaştırma işleçleri, [ `System.Version` nesne olarak ayrıştırılabilecek dizeleri karşılaştırabilir](#msbuild-conditions.md#Comparing-versions), ancak karşılaştırma beklenmeyen sonuçlar üretebilir. Özellik işlevlerini tercih edin.

|İşlev imzası|Description|
|------------------------|-----------------|
|VersionEquals (dize a, dize b)|`true`Sürümler `a` ve `b` aşağıdaki kurallara göre eşdeğer olursa döndürün.|
|VersionGreaterThan(string a, string b)|Sürüm, `true` aşağıdaki `a` kurallara göre daha `b` büyükse geri döner.|
|VersionGreaterThanOrEquals(string a, string b)|Sürüm `true` aşağıdaki `a` kurallara göre büyüktür veya buna `b` eşitse dönüş.|
|VersionLessThan(string a, string b)|Sürüm `true` aşağıdaki `a` kurallara göre daha `b` küçükse dönüş.|
|VersionLessThanOrEquals(string a, string b)|Sürüm `true` aşağıdaki `a` kurallara göre küçükse veya `b` ona eşitse dönüş.|
|VersionNotEquals(string a, string b)|ve `false` sürümleri aşağıdaki `a` `b` kurallara göre eşdeğerse dönüş.|

Bu yöntemlerde, sürümleri gibi ayrıştırıldı ve <xref:System.Version?displayProperty=fullName> aşağıdaki özel durumlar dışında:

* Ile `v` `V` karşılaştırmaya olanak sağlayan başında veya yoksayılır. `$(TargetFrameworkVersion)`

* İlk '-' veya '+' ile sürüm dizesinin sonuna kadar olan her şey yoksayılır. Bu, semantik sürümlerin (semver) geçişe olanak sağlar, ancak sıra semver ile aynı değildir. Bunun yerine, ön veri belirleyicileri ve derleme meta verileri herhangi bir sıralama ağırlığına sahip değildir. Bu, örneğin, için bir özelliği açmak ve özelliğinin üzerinde `>= x.y` devreye açması için yararlı `x.y.z-pre` olabilir.

* Belirtilmeyen parçalar sıfır değer parçalarıyla aynıdır. (`x == x.0 == x.0.0 == x.0.0.0`).

* Tamsayı bileşenlerinde boşluklara izin verilmez.

* Yalnızca ana sürüm geçerlidir ( `3` `3.0.0.0` eşittir)

* `+` tamsayı bileşenlerinin pozitif oturum açmasına izin verilmez (semver meta verileri olarak kabul edilir ve yoksayılır)

> [!TIP]
> [TargetFramework özelliklerinin](msbuild-target-framework-and-target-platform.md) karşılaştırmaları genellikle sürümleri ayıklamak ve karşılaştırmak yerine [ıtargetframeworkcompatible](#MSBuild-TargetFramework-and-TargetPlatform-functions) ' i kullanmalıdır. Bu `TargetFramework` , ' ın yanı sıra sürümünde değişen ' nin karşılaştırılmasına olanak sağlar `TargetFrameworkIdentifier` .

## <a name="msbuild-condition-functions"></a>MSBuild koşul işlevleri

İşlevler `Exists` ve `HasTrailingSlash` özellik işlevleri değildir. Bu öznitelikler, özniteliğiyle birlikte kullanılmak üzere kullanılabilir `Condition` . Bkz. [MSBuild koşulları](msbuild-conditions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)

- [MSBuild genel bakış](../msbuild/msbuild.md)
