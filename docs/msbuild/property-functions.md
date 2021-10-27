---
title: Özellik Işlevleri | Microsoft Docs
description: MSBuild özellik tanımlarında görüntülenen .NET Framework yöntemlerine yapılan çağrılar olan özellik işlevlerini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/20/2021
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
ms.openlocfilehash: 268c0b2030b39ff512aa74fc7ea84c185331e0a2
ms.sourcegitcommit: 4efdab6a579b31927c42531bb3f7fdd92890e4ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "130350696"
---
# <a name="property-functions"></a>Özellik işlevleri

özellik işlevleri, MSBuild özellik tanımlarında görüntülenen .NET Framework yöntemlerine yapılan çağrılardır. Görevlerin aksine, özellik işlevleri hedeflerin dışında kullanılabilir. Özellik işlevleri, her bir hedefin dışındaki özellikler ve öğeler için herhangi bir hedef çalıştırılmadan önce ya da hedef değerlendirildiği zaman içindeki Özellik grupları ve öğe grupları için herhangi bir hedefin her genişletilmesinden önce olan özellikler veya öğeler her genişletildiğinde değerlendirilir.

MSBuild görevleri kullanmadan, sistem saatini okuyabilir, dizeleri karşılaştırabilir, normal ifadelerle eşleştirebilir ve derleme betiğinizdeki diğer işlemleri gerçekleştirebilirsiniz. MSBuild, dizeyi sayı ve sayı olarak dizeye dönüştürmeye ve diğer dönüştürmeleri gerekli olarak yapmaya çalışacaktır.

Özellik işlevlerinden döndürülen dize değerleri [özel karakterlerin](msbuild-special-characters.md) atlanmalıdır. Değerin doğrudan proje dosyasına yerleştirilmiş gibi değerlendirilmesini istiyorsanız, `$([MSBuild]::Unescape())` özel karakterlerin atmasını kaldırmak için kullanın.

özellik işlevleri .NET Framework 4 ve üzeri sürümlerde kullanılabilir.

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

Yapı betiğinizdeki birçok sistem sınıfının statik özelliklerine ve yöntemlerine erişebilirsiniz. Statik bir özelliğin değerini almak için aşağıdaki sözdizimini kullanın; burada, \<Class> sistem sınıfının adıdır ve \<Property> özelliğin adıdır.

```
$([Class]::Property)
```

Örneğin, geçerli tarih ve saate bir Build özelliği ayarlamak için aşağıdaki kodu kullanabilirsiniz.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Statik bir yöntemi çağırmak için aşağıdaki sözdizimini kullanın; burada, \<Class> sistem sınıfının adıdır, \<Method> yöntemin adıdır ve ( \<Parameters> ) yöntemi için parametre listesidir:

```
$([Class]::Method(Parameters))
```

Örneğin, bir yapı özelliğini yeni bir GUID 'ye ayarlamak için bu betiği kullanabilirsiniz:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

Statik Özellik işlevlerinde, bu sistem sınıflarının herhangi bir statik yöntemini veya özelliğini kullanabilirsiniz:

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

- [System. Environment:: CommandLine](xref:System.Environment.CommandLine*)
- [System. Environment:: ExpandEnvironmentVariables](xref:System.Environment.ExpandEnvironmentVariables*)
- [System. Environment:: GetEnvironmentVariable](xref:System.Environment.GetEnvironmentVariable*)
- [System. Environment:: GetEnvironmentVariables](xref:System.Environment.GetEnvironmentVariables*)
- [System. Environment:: GetFolderPath](xref:System.Environment.GetFolderPath*)
- [System. Environment:: GetLogicalDrives](xref:System.Environment.GetLogicalDrives*)
- [System. ıO. Directory:: Getdizinler](xref:System.IO.Directory.GetDirectories*)
- [System. ıO. Directory:: GetFiles](xref:System.IO.Directory.GetFiles*)
- [System. ıO. Directory:: GetLastAccessTime](xref:System.IO.Directory.GetLastAccessTime*)
- [System. ıO. Directory:: GetLastWriteTime](xref:System.IO.Directory.GetLastWriteTime*)
- [System. ıO. Directory:: GetParent](xref:System.IO.Directory.GetParent*)
- [System. ıO. File:: Exists](xref:System.IO.File.Exists*)
- [System. ıO. File:: GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System. ıO. File:: GetAttributes](xref:System.IO.File.GetAttributes*)
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
|uzun çıkarma (Long a, Long b)|İki Long çıkar.|
|Çift çarpma (çift a, çift b)|İki Double öğesini çarpın.|
|uzun çarpma (Long a, Long b)|İki Long 'yi çarpın.|
|Çift bölme (çift a, çift b)|İki Double öğesini bölün.|
|Uzun bölme (Long a, Long b)|İki Long bölün.|
|Çift modül (çift a, çift b)|İki Double modül.|
|uzun mod (Long a, Long b)|Modül iki Long.|
|dize kaçış (dize kaçışsız)|MSBuild kaçış kurallarına göre dizeyi kaçış.|
|dize Unkaçış (dize kaçan)|MSBuild kaçış kurallarına göre dizenin kaçış işaretini kaldırın.|
|int Bitwiseveya (int First, INT Second)|Birinci ve ikinci bir bit düzeyinde gerçekleştirin `OR` (ilk &#124; saniye).|
|Int Bitwiseve (int First, int Second)|Birinci ve ikinci bir bit düzeyinde gerçekleştirin `AND` (ilk & saniye).|
|Int BitwiseXor (int First, int Second)|Birinci ve ikinci bit düzeyinde bit düzeyinde gerçekleştirin `XOR` (ilk ^ saniye).|
|Int Bitwıenot (ilk tamsayı)|Bit düzeyinde `NOT` (~ ilk) gerçekleştirin.|
|bool ısosplatform (dize platformString)|Geçerli işletim sistemi platformunun olup olmadığını belirtin `platformString` . `platformString` öğesinin üyesi olması gerekir <xref:System.Runtime.InteropServices.OSPlatform> .|
|bool ıosunixlike ()|Geçerli işletim sistemi bir UNIX sistemse true.|
|String NormalizePath (params String [] yol)|Belirtilen yolun kurallı tam yolunu alır ve geçerli işletim sistemi için doğru dizin ayırıcı karakterlerini içerdiğinden emin olur.|
|String NormalizeDirectory (params String [] yol)|Belirtilen dizinin kurallı tam yolunu alır ve sonunda eğik çizgi olduğundan emin olarak geçerli işletim sistemi için doğru dizin ayırıcı karakterlerini içerir.|
|dize Ensugeri çekme bölgesi (dize yolu)|Verilen yolun sonunda eğik çizgi yoksa bir tane ekleyin. Yol boş bir dize ise, onu değiştirmez.|
|String Getpathoffileyukarıdaki (dize dosyası, dize startingDirectory)|, İçin arama yapar ve geçerli derleme dosyasının konumunun üzerindeki dizin yapısındaki bir dosyanın tam yolunu ya da belirtilmişse öğesine göre döndürür `startingDirectory` .|
|Getdirectorynameoffileyukarıdaki (dize startingDirectory, dize fileName)|Belirtilen dizinde ya da bu dizinin üzerindeki dizin yapısındaki bir konumda bulunan bir dosyanın dizinini bulun ve döndürün.|
|String MakeRelative (dize basePath, dize yolu)|`path`Göreli hale getirir `basePath` . `basePath` mutlak bir dizin olmalıdır. `path`Göreli hale getirilmezse, harfine döndürülür. Benzer `Uri.MakeRelativeUri` .|
|dize ValueOrDefault (dize conditionValue, String defaultValue)|' DefaultValue ' parametresindeki dizeyi yalnızca ' conditionValue ' parametresi boşsa, Else değerini döndürün.|

## <a name="nested-property-functions"></a>İç içe özellik işlevleri

Aşağıdaki örnekte gösterildiği gibi daha karmaşık işlevler oluşturmak için özellik işlevlerini birleştirebilirsiniz.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Bu örnek, değerini döndürür <xref:System.IO.FileAttributes> .`Archive` yol tarafından verilen dosyanın bit (32 veya 0) `tempFile` . Numaralandırılmış veri değerlerinin bazı bağlamlarda ada göre görünmediğine dikkat edin. Önceki örnekte, bunun yerine sayısal değer (32) kullanılmalıdır. Diğer durumlarda, çağrılan yöntemin beklentilerine bağlı olarak, enum veri değeri kullanılmalıdır. Aşağıdaki örnekte, Enum değeri <xref:System.Text.RegularExpressions.RegexOptions> .`ECMAScript` Bu yöntemin beklediği için sayısal bir değer dönüştürülemediğinden kullanılmalıdır.

```xml
<PropertyGroup>
    <GitVersionHeightWithOffset>$([System.Text.RegularExpressions.Regex]::Replace("$(PrereleaseVersion)", "^.*?(\d+)$", "$1", "System.Text.RegularExpressions.RegexOptions.ECMAScript"))</GitVersionHeightWithOffset>
</PropertyGroup>
```

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

MSBuild `GetDirectoryNameOfFileAbove` property işlevi, belirtilen dosyayı (ve dahil) başlayarak belirtilen dizini içeren bir dizin için yukarı doğru arar. Bulunursa dosyayı içeren en yakın dizinin tam yolunu, aksi takdirde boş bir dize döndürür.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string startingDirectory, string fileName))
```

Bu örnek, yalnızca bir eşleşme bulunursa geçerli klasörün içinde veya üzerinde en yakın *EnlistmentInfo. props* dosyasının nasıl içeri aktarılacağını gösterir:

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

Bunun yerine işlevi kullanılarak bu örneğin daha öz yazılabilir yazıldığını unutmayın `GetPathOfFileAbove` :

```xml
<Import Project="$([MSBuild]::GetPathOfFileAbove(EnlistmentInfo.props))" Condition=" '$([MSBuild]::GetPathOfFileAbove(EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild Getpathoffileyukarıdaki

MSBuild `GetPathOfFileAbove` property işlevi, belirtilen dosyayı (ve dahil) başlayarak belirtilen dizini içeren bir dizin için yukarı doğru arar. Bulunursa, en yakın eşleşen dosyanın tam yolunu, yoksa boş bir dize döndürür.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string file, [string startingDirectory]))
```

Burada arama `file` yapılacak dosyanın adıdır ve `startingDirectory` içinde aramayı başlatmak için isteğe bağlı bir dizindir. Varsayılan olarak, arama geçerli dosyanın kendi dizininde başlar.
 
Bu örnek, yalnızca bir eşleşme bulunursa geçerli dizinin içinde veya üzerinde *dir. props* adlı bir dosyanın nasıl içeri aktarılacağını gösterir:

```xml
<Import Project="$([MSBuild]::GetPathOfFileAbove(dir.props))" Condition=" '$([MSBuild]::GetPathOfFileAbove(dir.props))' != '' " />
```

işlevsel olarak eşdeğer

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))' != '' " />
```

Ancak, bazı durumlarda, geçerli dosyanın eşleşmesini önlemek için aramayı ana dizinde başlatmanız gerekebilir. Bu örnek, bir *Directory. Build. props* dosyasının en yakın *Dizin. Build. props* dosyasını, yinelemeli olarak içeri aktarmadan, ağacın tamamen daha yüksek bir düzeyinde nasıl içeri aktaragösterdiğini gösterir:

```xml
<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />
```

işlevsel olarak eşdeğer

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove('$(MSBuildThisFileDirectory)../', 'Directory.Build.props'))/Directory.Build.props" />
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` property işlevi bir kayıt defteri anahtarının değerini döndürür. Bu işlev iki bağımsız değişken alır, anahtar adı ve değer adı ve kayıt defterindeki değeri döndürür. Bir değer adı belirtmezseniz, varsayılan değer döndürülür.

Aşağıdaki örneklerde bu işlevin nasıl kullanıldığı gösterilmektedir:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

> [!WARNING]
> MSBuild () .net SDK sürümünde `dotnet build` bu işlev desteklenmez.

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

> [!WARNING]
> MSBuild () .net SDK sürümünde `dotnet build` bu işlev desteklenmez.

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

|İşlev imzası|Description|
|------------------------|-----------------|
|Gettargetframeworkıdentifier (dize targetFramework)|Targetframeworkıdentifier 'ı TargetFramework 'ten ayrıştırın.|
|GetTargetFrameworkVersion (dize targetFramework, int versionPartCount)|TargetFrameworkVersion 'ı TargetFramework 'ten ayrıştırın.|
|Gettargetplatformıdentifier (dize targetFramework)|Targetplatformformıdentifier 'ı TargetFramework 'ten ayrıştırın.|
|GetTargetPlatformVersion (dize targetFramework, int versionPartCount)|Targetplatformden TargetPlatformVersion 'ı ayrıştırın.|
|Itargetframeworkcompatible (dize targetFrameworkTarget, String targetFrameworkCandidate)|Aday hedef çerçevesi bu hedef Framework ile uyumluysa ' true ', aksi takdirde false döndürün.|

`versionPartCount` `GetTargetFrameworkVersion` Ve parametresinin `GetTargetPlatformVersion` varsayılan değeri 2 ' dir.

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

|İşlev imzası|Description|
|------------------------|-----------------|
|VersionEquals (dize a, dize b)|`true`Sürümler `a` ve `b` aşağıdaki kurallara göre eşdeğer olursa döndürün.|
|VersionGreaterThan (dize a, dize b)|`true`Sürüm `a` `b` aşağıdaki kurallara göre daha büyükse döndürün.|
|VersionGreaterThanOrEquals (dize a, dize b)|`true`Sürüm `a` aşağıdaki kurallara göre daha büyükse veya eşitse döndürün `b` .|
|VersionLessThan (dize a, dize b)|`true`Sürüm `a` `b` aşağıdaki kurallara göre daha küçükse döndürün.|
|Versionlessals Okoşulları (dize a, dize b)|`true`Sürüm `a` aşağıdaki kurallara göre daha küçük veya ona eşitse döndürün `b` .|
|Versionnot Quals (dize a, dize b)|`false`Sürümler `a` ve `b` aşağıdaki kurallara göre eşdeğer olursa döndürün.|

Bu yöntemlerde, sürümler <xref:System.Version?displayProperty=fullName> aşağıdaki özel durumlarla benzer şekilde ayrıştırılır:

* Önünde `v` veya `V` buna karşılaştırmaya izin veren yok sayılır `$(TargetFrameworkVersion)` .

* İlk '-' veya ' + ' türünden sürüm dizesinin sonuna kadar olan her şey yok sayılır. Bu, semantik sürümlerin (semver) geçirilmesine izin verir, ancak sipariş semver ile aynı değildir. Bunun yerine, ön sürüm belirticileri ve derleme meta verilerinde sıralama ağırlığı yoktur. Bu, örneğin bir özelliği açmak ve üzerinde oturum açmak için yararlı olabilir `>= x.y` `x.y.z-pre` .

* Belirtilmeyen parçalar sıfır değer parçalarıyla aynı. (`x == x.0 == x.0.0 == x.0.0.0`).

* Tamsayı bileşenlerinde boşluğa izin verilmez.

* Yalnızca ana sürüm geçerlidir ( `3` eşittir `3.0.0.0` )

* `+` tamsayı bileşenlerinde pozitif oturum açma izni verilmez (semver meta verisi olarak kabul edilir ve yoksayıldı)

> [!TIP]
> [TargetFramework özelliklerinin](msbuild-target-framework-and-target-platform.md) karşılaştırmaları genellikle sürümleri ayıklamak ve karşılaştırmak yerine [ıtargetframeworkcompatible](#TargetFramework) ' i kullanmalıdır. Bu `TargetFramework` , ' ın yanı sıra sürümünde değişen ' nin karşılaştırılmasına olanak sağlar `TargetFrameworkIdentifier` .

## <a name="msbuild-condition-functions"></a>MSBuild koşul işlevleri

İşlevler `Exists` ve `HasTrailingSlash` özellik işlevleri değildir. Bu öznitelikler, özniteliğiyle birlikte kullanılmak üzere kullanılabilir `Condition` . [MSBuild koşullara](msbuild-conditions.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)

- [MSBuild genel bakış](../msbuild/msbuild.md)
