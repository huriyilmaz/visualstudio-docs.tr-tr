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
ms.workload:
- multiple
ms.openlocfilehash: a47ff76c98c5788fdfca3d633c87664b6802de70
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222961"
---
# <a name="property-functions"></a>Özellik işlevleri

Özellik işlevleri, .NET Framework tanımlarında görünen MSBuild çağrılarıdır. Görevlerden farklı olarak, özellik işlevleri hedeflerin dışında kullanılabilir ve herhangi bir hedef çalışmadan önce değerlendirilir.

Bu MSBuild olmadan sistem zamanını okuyabilir, dizeleri karşılaştırabilirsiniz, normal ifadelerle eş okuyabilir ve derleme betiğinize başka eylemler gerçekleştirebilirsiniz. MSBuild sayı ve sayı dizeye dönüştürmeye ve gerektiğinde diğer dönüştürmeleri yapmaya çalışacak.

Özellik işlevlerinden döndürülen dize değerlerinin özel [karakterleri vardır.](msbuild-special-characters.md) Değerin doğrudan proje dosyasına konan bir değer olarak kabul 1999'da özel karakterlerin `$([MSBuild]::Unescape())` kaçışlarını almak için kullanın.

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

Sınıfın adı, ad alanıyla tam olarak tam olarak ad alanına sahip olması gerekir.

Örneğin, bir derleme özelliğini geçerli tarihe ayarlamak için aşağıdaki kodu kullanabilirsiniz.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>MSBuild işlevleri

Derlemeniz içinde aritmetik, bitwise mantıksal ve kaçış karakteri desteği sağlamak için çeşitli statik yöntemlere erişilebilir. Bu yöntemlere aşağıdaki söz dizimi kullanarak erişebilirsiniz; burada yöntemin \<Method> adıdır ve ( \<Parameters> ) yöntemin parametre listesidir.

```
$([MSBuild]::Method(Parameters))
```

Örneğin, sayısal değerlere sahip iki özelliği bir araya eklemek için aşağıdaki kodu kullanın.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Özellik işlevlerinin MSBuild listesi:

|İşlev imzası|Açıklama|
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
|String Getpathoffileyukarıdaki (dize dosyası, dize startingDirectory)|, İçin arama yapar ve geçerli derleme dosyasının konumunun üzerindeki dizin yapısındaki bir dosyanın tam yolunu ya da belirtilmişse öğesine göre döndürür `startingDirectory` .|
|Getdirectorynameoffileyukarıdaki (dize startingDirectory, dize fileName)|Belirtilen dizinde ya da bu dizinin üzerindeki dizin yapısındaki bir konumda bulunan bir dosyanın dizinini bulun ve döndürün.|
|String MakeRelative (dize basePath, dize yolu)|`path`Göreli hale getirir `basePath` . `basePath` mutlak bir dizin olmalıdır. `path`Göreli hale getirilmezse, harfine döndürülür. Benzer `Uri.MakeRelativeUri` .|
|dize ValueOrDefault (dize conditionValue, String defaultValue)|' DefaultValue ' parametresindeki dizeyi yalnızca ' conditionValue ' parametresi boşsa, Else değerini döndürün.|

## <a name="nested-property-functions"></a>İç içe özellik işlevleri

Aşağıdaki örnekte gösterildiği gibi daha karmaşık işlevler oluşturmak için özellik işlevlerini birleştirebilirsiniz.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Bu örnek, <xref:System.IO.FileAttributes> `Archive` yol tarafından verilen dosyanın bit (32 veya 0) değerini döndürür `tempFile` . Numaralandırılmış veri değerlerinin özellik işlevleri içinde ada göre görünmediğine dikkat edin. Bunun yerine sayısal değer (32) kullanılmalıdır.

Meta veriler, iç içe geçmiş Özellik işlevlerinde de görünebilir. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.

## <a name="msbuild-doestaskhostexist"></a>MSBuild Yok Tasmi Hostexist

`DoesTaskHostExist`MSBuild özellik işlevi, belirtilen çalışma zamanı ve mimari değerleri için bir görev konağının şu anda yüklü olup olmadığını döndürür.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild Ensugeri çekme

`EnsureTrailingSlash`MSBuild özellik işlevi, zaten mevcut değilse sondaki eğik çizgi ekler.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild Getdirectorynameoffileyukarıdaki

MSBuild `GetDirectoryNameOfFileAbove` property işlevi, yoldaki geçerli dizinin üzerindeki dizinlerde bulunan bir dosyayı arar.

 Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Aşağıdaki kod bu sözdizimine bir örnektir.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild Getpathoffileyukarıdaki

`GetPathOfFileAbove`MSBuild özellik işlevi, geçerli dizinin üzerindeki dizin yapısında bulunuyorsa belirtilen dosyanın yolunu döndürür. Çağırmak için işlevsel olarak eşdeğerdir

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` property işlevi bir kayıt defteri anahtarının değerini döndürür. Bu işlev iki bağımsız değişken alır, anahtar adı ve değer adı ve kayıt defterindeki değeri döndürür. Bir değer adı belirtmezseniz, varsayılan değer döndürülür.

Aşağıdaki örneklerde bu işlevin nasıl kullanıldığı gösterilmektedir:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

MSBuild `GetRegistryValueFromView` property işlevi, kayıt defteri anahtarı, değeri ve bir veya daha fazla sıralanmış kayıt defteri görünümü verilen sistem kayıt defteri verilerini alır. Anahtar ve değer, her kayıt defteri görünümünde, bulunana kadar sırayla aranır.

Bu özellik işlevinin sözdizimi şöyledir:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Windows 64-bit işletim sistemi, 32 bit uygulamalar için **HKEY_LOCAL_MACHINE\SOFTWARE** kayıt defteri görünümü sunan **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** bir kayıt defteri anahtarı tutar.

Varsayılan olarak, WOW64 üzerinde çalışan 32 bitlik bir uygulama 32 bit kayıt defteri görünümüne erişir ve 64 bit uygulama, 64 bit kayıt defteri görünümüne erişir.

Aşağıdaki kayıt defteri görünümleri kullanılabilir:

|Kayıt defteri görünümü|Tanım|
|-------------------|----------------|
|RegistryView. Registry32|32 bit uygulama kayıt defteri görünümü.|
|RegistryView. Registry64|64 bit uygulama kayıt defteri görünümü.|
|RegistryView. Default|Uygulamanın üzerinde çalıştığı işlemle eşleşen kayıt defteri görünümü.|

Bir örnek verilmiştir.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

önce 64 bit kayıt defteri görünümüne, sonra da 32 bit kayıt defteri görünümünde arayarak **ReferenceAssemblies** anahtarının **SLRuntimeInstallPath** verilerini alır.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

MSBuild `MakeRelative` property işlevi, ilk yola göre ikinci yolun göreli yolunu döndürür. Her yol bir dosya veya klasör olabilir.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

Aşağıdaki kod bu sözdizimine bir örnektir.

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

MSBuild `ValueOrDefault` property işlevi, null veya boş olmadığı takdirde ilk bağımsız değişkeni döndürür. İlk bağımsız değişken null veya boşsa, işlev ikinci bağımsız değişkeni döndürür.

Aşağıdaki örnek, bu işlevin nasıl kullanıldığını gösterir.

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

MSBuild 16,7 ve üzeri, [targetframework ve TargetPlatform özelliklerini](msbuild-target-framework-and-target-platform.md)işlemek için birkaç işlevi tanımlar.

|İşlev imzası|Açıklama|
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

MSBuild 16,5 ve üzeri sürümleri temsil eden dizeleri karşılaştırmak için birkaç işlevi tanımlar.

> [!Note]
> Koşullarda karşılaştırma işleçleri, [ `System.Version` nesne olarak ayrıştırılabilecek dizeleri karşılaştırabilir](msbuild-conditions.md#comparing-versions), ancak karşılaştırma beklenmeyen sonuçlar üretebilir. Özellik işlevlerini tercih edin.

|İşlev imzası|Açıklama|
|------------------------|-----------------|
|VersionEquals (dize a, dize b)|`true`Sürümler `a` ve `b` aşağıdaki kurallara göre eşdeğer olursa döndürün.|
|VersionGreaterThan (dize a, dize b)|`true`Sürüm `a` `b` aşağıdaki kurallara göre daha büyükse döndürün.|
|VersionGreaterThanOrEquals (dize a, dize b)|`true`Sürüm `a` aşağıdaki kurallara göre daha büyükse veya eşitse döndürün `b` .|
|VersionLessThan (dize a, dize b)|`true`Sürüm `a` `b` aşağıdaki kurallara göre daha küçükse döndürün.|
|Versionlessals Okoşulları (dize a, dize b)|`true`Sürüm `a` aşağıdaki kurallara göre daha küçük veya ona eşitse döndürün `b` .|
|Versionnot Quals (dize a, dize b)|`false`Sürümler `a` ve `b` aşağıdaki kurallara göre eşdeğer olursa döndürün.|

Bu yöntemlerde, sürümler <xref:System.Version?displayProperty=fullName> aşağıdaki özel durumlarla benzer şekilde ayrıştırılır:

* Önünde `v` veya `V` buna karşılaştırmaya izin veren yok sayılır `$(TargetFrameworkVersion)` .

* İlk '-' veya ' + ' türünden sürüm dizesinin sonuna kadar olan her şey yok sayılır. Bu, semantik sürümlerin (semver) geçirilmesine izin verir, ancak sipariş semver ile aynı değildir. Bunun yerine, ön veri belirleyicileri ve derleme meta verileri herhangi bir sıralama ağırlığına sahip değildir. Bu, örneğin, için bir özelliği açmak ve özelliğinin üzerinde `>= x.y` devreye açması için yararlı `x.y.z-pre` olabilir.

* Belirtilmeyen parçalar sıfır değer parçalarıyla aynıdır. (`x == x.0 == x.0.0 == x.0.0.0`).

* Tamsayı bileşenlerinde boşluklara izin verilmez.

* Yalnızca ana sürüm geçerlidir ( `3` `3.0.0.0` eşittir)

* `+` tamsayı bileşenlerinin pozitif oturum açmasına izin verilmez (semver meta verileri olarak kabul edilir ve yoksayılır)

> [!TIP]
> [TargetFramework özelliklerinin karşılaştırmaları genellikle](msbuild-target-framework-and-target-platform.md) sürümleri ayıklar ve karşılaştırmak yerine [IsTargetFrameworkCompatible](#TargetFramework) kullanır. Bu, `TargetFramework` sürümle birlikte değişenleri `TargetFrameworkIdentifier` karşılaştırmaya olanak sağlar.

## <a name="msbuild-condition-functions"></a>MSBuild işlevleri

ve işlevleri `Exists` `HasTrailingSlash` özellik işlevleri değildir. Bunlar özniteliğiyle `Condition` kullanılabilir. Bkz. [MSBuild koşulları.](msbuild-conditions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)

- [MSBuild genel bakış](../msbuild/msbuild.md)
