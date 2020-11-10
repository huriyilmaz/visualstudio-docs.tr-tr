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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fa104ece39e20fbd00abcc2e1616a3dd52a5d4c
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437129"
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

|İşlev imzası|Açıklama|
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

Bu örnek, <xref:System.IO.FileAttributes> `Archive` yol tarafından verilen dosyanın bit (32 veya 0) değerini döndürür `tempFile` . Numaralandırılmış veri değerlerinin özellik işlevleri içinde ada göre görünmediğine dikkat edin. Bunun yerine sayısal değer (32) kullanılmalıdır.

Meta veriler, iç içe geçmiş Özellik işlevlerinde de görünebilir. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.

## <a name="msbuild-doestaskhostexist"></a>MSBuild yok Taskhostexist

`DoesTaskHostExist`MSBuild 'teki Özellik işlevi, belirtilen çalışma zamanı ve mimari değerleri için bir görev konağının Şu anda yüklü olup olmadığını döndürür.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild Ensuvanıingeğik çizgi

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

MSBuild `MakeRelative` özelliği işlevi, ilk yola göre ikinci yolun göreli yolunu döndürür. Her yol bir dosya veya klasör olabilir.

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

MSBuild `ValueOrDefault` Özellik işlevi, null veya boş olmadığı takdirde ilk bağımsız değişkeni döndürür. İlk bağımsız değişken null veya boşsa, işlev ikinci bağımsız değişkeni döndürür.

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

## <a name="msbuild-targetframework-and-targetplatform-functions"></a>MSBuild TargetFramework ve TargetPlatform işlevleri

MSBuild [, TargetFramework ve TargetPlatform özelliklerini](msbuild-target-framework-and-target-platform.md)işlemek için çeşitli işlevler tanımlar.

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

## <a name="msbuild-condition-functions"></a>MSBuild koşul işlevleri

İşlevler `Exists` ve `HasTrailingSlash` özellik işlevleri değildir. Bu öznitelikler, özniteliğiyle birlikte kullanılmak üzere kullanılabilir `Condition` . Bkz. [MSBuild koşulları](msbuild-conditions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)

- [MSBuild genel bakış](../msbuild/msbuild.md)
