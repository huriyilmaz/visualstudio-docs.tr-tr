---
title: Özellik İşlevleri | Microsoft Docs
description: Özellik tanımlarında görünen .NET Framework çağrıları olan özellik işlevlerini MSBuild öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0a6274a4648dc204bf451aaa68dbc2e47b1ce25e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726855"
---
# <a name="property-functions"></a>Özellik işlevleri

Özellik işlevleri, .NET Framework tanımlarında görünen MSBuild çağrılarıdır. Görevlerden farklı olarak, özellik işlevleri hedeflerin dışında kullanılabilir ve herhangi bir hedef çalışmadan önce değerlendirilir.

Bu MSBuild olmadan sistem zamanını okuyabilir, dizeleri karşılaştırabilirsiniz, normal ifadeleri eşler ve derleme betiğinize başka eylemler gerçekleştirebilirsiniz. MSBuild sayı ve sayı dizeye dönüştürmeye ve gerektiğinde diğer dönüştürmeleri yapmaya çalışacak.

Özellik işlevlerinden döndürülen dize değerlerinin özel [karakterleri vardır.](msbuild-special-characters.md) Değerin doğrudan proje dosyasına konmış gibi kabul 1000'den fazla olması için özel `$([MSBuild]::Unescape())` karakterlerin kaçışlarını kaldırabilirsiniz.

Özellik işlevleri 4 ve .NET Framework kullanılabilir.

## <a name="property-function-syntax"></a>Özellik işlevi söz dizimi

Bunlar üç tür özellik işlevidir; her işlevin farklı bir söz dizimi vardır:

- Dize (örnek) özellik işlevleri
- Statik özellik işlevleri
- MSBuild işlevleri

### <a name="string-property-functions"></a>Dize özelliği işlevleri

Tüm derleme özelliği değerleri yalnızca dize değerleridir. Herhangi bir özellik değerinde çalıştırmak için dize (örnek) yöntemlerini kullanabilirsiniz. Örneğin, bu kodu kullanarak tam yolu temsil eden bir derleme özelliğinden sürücü adını (ilk üç karakter) ayıkabilirsiniz:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Statik özellik işlevleri

Derleme betiğinde, birçok sistem sınıflarının statik özelliklerine ve yöntemlerine erişebilirsiniz. Statik bir özelliğin değerini almak için aşağıdaki sözdizimini kullanın; burada sistem sınıfının \<Class> adıdır \<Property> ve özelliğin adıdır.

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
- [System.Io.File::Exists](xref:System.IO.File.Exists*)
- [System.IO.File::GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System.Io.File::GetAttributes](xref:System.IO.File.GetAttributes*)
- [System.Io.File::GetLastAccessTime](xref:System.IO.File.GetLastAccessTime*)
- [System.IO.File::GetLastWriteTime](xref:System.IO.File.GetLastWriteTime*)
- [System.Io.File::ReadAllText](xref:System.IO.File.ReadAllText*)

### <a name="calling-instance-methods-on-static-properties"></a>Statik özelliklerde örnek yöntemlerini çağırma

Bir nesne örneği döndüren statik bir özellik erişersiniz, bu nesnenin örnek yöntemlerini çağırabilirsiniz. Bir örnek yöntemi çağırmak için aşağıdaki sözdizimini kullanın; burada sistem sınıfının adıdır, özelliğin adıdır, yöntemin adıdır ve ( ) yöntemin parametre \<Class> \<Property> \<Method> \<Parameters> listesidir:

```
$([Class]::Property.Method(Parameters))
```

Sınıfın adı ad alanıyla tam olarak tam olarak ad alanına sahip olması gerekir.

Örneğin, bir derleme özelliğini geçerli tarihe ayarlamak için aşağıdaki kodu kullanabilirsiniz.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>MSBuild işlevleri

Aritmetik, bitwise mantıksal ve kaçış karakteri desteği sağlamak için derlemenizin çeşitli statik yöntemlerine erişilebilir. Bu yöntemlere aşağıdaki söz dizimi kullanarak erişebilirsiniz; burada yöntemin \<Method> adıdır ve ( \<Parameters> ) yöntemin parametre listesidir.

```
$([MSBuild]::Method(Parameters))
```

Örneğin, sayısal değerlere sahip iki özelliği bir araya eklemek için aşağıdaki kodu kullanın.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Özellik işlevlerinin MSBuild listesi:

|İşlev imzası|Description|
|------------------------|-----------------|
|double Add(double a, double b)|İki çift değer ekleyin.|
|long Add(long a, long b)|İki uzun değer ekleyin.|
|double Subtract(double a, double b)|İki çift çıkar.|
|long Subtract(long a, long b)|İki uzun değer çıkar.|
|double Multiply(double a, double b)|İki çarpı çarpın.|
|long Multiply(long a, long b)|İki uzun değeri çarpın.|
|double Divide(double a, double b)|İki çifti bölün.|
|long Divide(long a, long b)|İki uzun bölme.|
|double Modulo(double a, double b)|Modulo iki double.|
|long Modulo(long a, long b)|Modulo iki longs.|
|string Escape(dize kaçışsız)|Kaçış kurallarına göre MSBuild kaçış.|
|string Unescape(string escaped)|Kaçış kurallarına göre dizenin MSBuild kaçışı.|
|int BitwiseOr(int first, int second)|Birinci ve ikincide bit `OR` olarak (birinci ve ikinci &#124; gerçekleştirin.|
|int BitwiseAnd(int first, int second)|Birinci ve ikincide bit `AND` olarak (birinci ve ikinci & gerçekleştirin.|
|int BitwiseXor(int first, int second)|Birinci ve ikincide bit `XOR` olarak gerçekleştirin (ilk ^ saniye).|
|int BitwiseNot(ilk olarak int)|Bitwise `NOT` (~first) gerçekleştirin.|
|bool IsOsPlatform(string platformString)|Geçerli işletim sistemi platformunun olup olmadığını `platformString` belirtin. `platformString` , üyesi olması <xref:System.Runtime.InteropServices.OSPlatform> gerekir.|
|bool IsOSUnixLike()|Geçerli işletim sistemi bir Unix sistemi ise True.|
|string NormalizePath(params string[] path)|Sağlanan yolun kurallı tam yolunu alır ve geçerli işletim sistemi için doğru dizin ayırıcı karakterlerini içerdiğini sağlar.|
|string NormalizeDirectory(params string[] path)|Sağlanan dizinin kurallı tam yolunu alır ve geçerli işletim sistemi için doğru dizin ayırıcı karakterlerini içerirken sondaki eğik çizgiye sahip olmasını sağlar.|
|string EnsureTrailingSlash(dize yolu)|Verilen yolun sonunda eğik çizgi yoksa bir eğik çizgi ekleyin. Yol boş bir dize ise, bunu değiştirmez.|
|string GetPathOfFileAbove(dize dosyası, string startingDirectory)|için arama ve geçerli derleme dosyasının konumunun üzerindeki dizin yapısındaki bir dosyanın tam yolunu veya belirtilmişse dosyasını `startingDirectory` temel alarak döndürür.|
|GetDirectoryNameOfFileAbove(string startingDirectory, string fileName)|Belirtilen dizinde veya dizinin üzerindeki dizin yapısında bir dosyanın dizinini bulun ve geri dönüş.|
|string MakeRelative(string basePath, string path)|ile `path` ilgili `basePath` yapar. `basePath` mutlak bir dizin olmalıdır. Göreli `path` olarak bulunamazsa, tam olarak döndürülür. benzer `Uri.MakeRelativeUri` şekilde.|
|string ValueOrDefault(string conditionValue, string defaultValue)|'defaultValue' parametresinde dizeyi yalnızca 'conditionValue' parametresi boşsa, yoksa conditionValue değerini döndürür.|

## <a name="nested-property-functions"></a>İç içe özellik işlevleri

Aşağıdaki örnekte de olduğu gibi, daha karmaşık işlevler oluşturmak için özellik işlevlerini birleştirebilirsiniz.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Bu örnek, yolu tarafından <xref:System.IO.FileAttributes> `Archive` verilen dosyanın bit değerini (32 veya 0) `tempFile` döndürür. Numaralandı veri değerlerinin özellik işlevlerinde adına göre görüneyr. Bunun yerine sayısal değer (32) kullanılmalıdır.

Meta veriler iç içe özellik işlevlerinde de görünebilir. Daha fazla bilgi için bkz. [Toplu İşlem.](../msbuild/msbuild-batching.md)

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

MSBuild özelliği işlevi, belirtilen çalışma zamanı ve mimari değerleri için bir görev ana bilgisayarının yüklü `DoesTaskHostExist` olup olmadığını döndürür.

Bu özellik işlevi aşağıdaki söz dizimlerini içerir:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

MSBuild özelliği işlevi, henüz yoksa `EnsureTrailingSlash` sonda bir eğik çizgi ekler.

Bu özellik işlevi aşağıdaki söz dizimlerini içerir:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

MSBuild `GetDirectoryNameOfFileAbove` özelliği işlevi, yol üzerindeki geçerli dizinin üzerindeki dizinlerde bir dosyanın olduğunu gösterir.

 Bu özellik işlevi aşağıdaki söz dizimlerini içerir:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Aşağıdaki kod, bu söz dizimlerinin bir örneğidir.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

MSBuild özelliği işlevi, geçerli dizinin üzerindeki dizin yapısında yer alıyorsa `GetPathOfFileAbove` belirtilen dosyanın yolunu döndürür. İşlevsel olarak çağrısına eşdeğerdir

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Bu özellik işlevi aşağıdaki söz dizimlerini içerir:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` özelliği işlevi bir kayıt defteri anahtarının değerini döndürür. Bu işlev anahtar adı ve değer adı olmak kaydından iki bağımsız değişken alır ve değeri kayıt defterinden döndürür. Bir değer adı belirtmezseniz varsayılan değer döndürülür.

Aşağıdaki örneklerde bu işlevin nasıl kullanıldıkları verilmiştir:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

Bu MSBuild işlevi kayıt defteri anahtarı, değeri ve bir veya daha fazla sıralı kayıt defteri görünümlerini kullanarak `GetRegistryValueFromView` sistem kayıt defteri verilerini alır. Anahtar ve değer, bulunana kadar her kayıt defteri görünümünde sırayla aranır.

Bu özellik işlevinin söz dizimi şöyledir:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

64 bit Windows sistemi, 32 bit **uygulamalar içinHKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** kayıt defteri görünümü sunan bir **HKEY_LOCAL_MACHINE\SOFTWARE** kayıt defteri anahtarını sürdürür.

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

, önce 64 bit kayıt defteri görünümünde ve ardından 32 bit kayıt defteri görünümünde bakarak **ReferenceAssemblies** anahtarının **SLRuntimeInstallPath** verilerini alır.

## <a name="msbuild-makerelative"></a>MSBuild Makerelative

MSBuild `MakeRelative` özelliği işlevi, birinci yola göre ikinci yolun göreli yolunu döndürür. Her yol bir dosya veya klasör olabilir.

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

MSBuild `ValueOrDefault` özelliği işlevi, null veya boş olmadığı sürece ilk bağımsız değişkeni döndürür. İlk bağımsız değişken null veya boşsa işlev ikinci bağımsız değişkeni döndürür.

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

<a name="TargetFramework"></a>

## <a name="msbuild-targetframework-and-targetplatform-functions"></a>MSBuild TargetFramework ve TargetPlatform işlevleri

MSBuild 16.7 ve üst, [TargetFramework ve TargetPlatform özelliklerini işlemeye yönelik çeşitli işlevler tanımlar.](msbuild-target-framework-and-target-platform.md)

|İşlev imzası|Description|
|------------------------|-----------------|
|GetTargetFrameworkIdentifier(string targetFramework)|TargetFramework'den TargetFrameworkIdentifier'i ayrıştır.|
|GetTargetFrameworkVersion(string targetFramework)|TargetFrameworkVersion'i TargetFramework'den ayrıştırın.|
|GetTargetPlatformIdentifier(string targetFramework)|TargetPlatformIdentifier'i TargetFramework'den ayrıştır.|
|GetTargetPlatformVersion(string targetFramework)|TargetPlatformVersion'i TargetFramework'den ayrıştırın.|
|IsTargetFrameworkCompatible(string targetFrameworkTarget, string targetFrameworkCandidate)|Aday hedef çerçeve bu hedef çerçeveyle uyumluysa 'True', aksi takdirde false döndürür.|

Aşağıdaki örnekte, bu işlevlerin nasıl kullanıldıkları gösterir. 

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

## <a name="msbuild-version-comparison-functions"></a>MSBuild karşılaştırma işlevlerini kullanın

MSBuild 16.5 ve üst sürümleri temsil eden dizeleri karşılaştırmak için çeşitli işlevler tanımlar.

> [!Note]
> Koşullardaki karşılaştırma [işleçleri nesne olarak ayrıştırılana dizeleri `System.Version` karşılaştırabilirsiniz,](msbuild-conditions.md#comparing-versions)ancak karşılaştırma beklenmeyen sonuçlar üretebilir. Özellik işlevlerini tercih eder.

|İşlev imzası|Description|
|------------------------|-----------------|
|VersionEquals(string a, string b)|ve `true` sürümleri aşağıdaki `a` `b` kurallara göre eşdeğerse dönüş.|
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
> [TargetFramework özelliklerinin karşılaştırmaları genellikle](msbuild-target-framework-and-target-platform.md) sürümleri ayıklamak ve karşılaştırmak yerine [IsTargetFrameworkCompatible](#TargetFramework) kullandırır. Bu, `TargetFramework` sürümle birlikte değişenleri `TargetFrameworkIdentifier` karşılaştırmaya olanak sağlar.

## <a name="msbuild-condition-functions"></a>MSBuild koşulu işlevleri

ve işlevleri `Exists` `HasTrailingSlash` özellik işlevleri değildir. Bunlar özniteliğiyle `Condition` kullanılabilir. Bkz. [MSBuild koşulları.](msbuild-conditions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)

- [MSBuild genel bakış](../msbuild/msbuild.md)
