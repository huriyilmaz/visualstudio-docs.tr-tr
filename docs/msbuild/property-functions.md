---
title: Özellik Fonksiyonları | Microsoft Dokümanlar
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
ms.openlocfilehash: bb4c44b4e642ff1137df7f0afe02502224060a64
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302912"
---
# <a name="property-functions"></a>Özellik işlevleri

Özellik işlevleri, MSBuild özellik tanımlarında görünen .NET Framework yöntemlerine yapılan çağrılardır. Görevlerin aksine, özellik işlevleri hedeflerin dışında kullanılabilir ve herhangi bir hedef çalıştırmadan önce değerlendirilir.

MSBuild görevlerini kullanmadan sistem süresini okuyabilir, dizeleri karşılaştırabilir, normal ifadeleri eşleyebilir ve yapı komut dosyanızda diğer eylemleri gerçekleştirebilirsiniz. MSBuild dizeyi sayıya ve sayıya dönüştürmeyi ve gerektiğinde diğer dönüşümleri yapmaya çalışır.

Özellik işlevlerinden döndürülen dize değerlerinde [kaçan özel karakterler](msbuild-special-characters.md) vardır. Değerin doğrudan proje dosyasına konurmuş gibi davranılmasını `$([MSBuild]::Unescape())` istiyorsanız, özel karakterlerden kaçmak için kullanın.

Özellik işlevleri .NET Framework 4 ve sonrası ile kullanılabilir.

## <a name="property-function-syntax"></a>Özellik fonksiyonu sözdizimi

Bunlar üç tür özellik işlevidir; her işlevin farklı bir sözdizimi vardır:

- String (instance) özellik fonksiyonları
- Statik özellik fonksiyonları
- MSBuild özellik fonksiyonları

### <a name="string-property-functions"></a>Dize özellik işlevleri

Tüm yapı özelliği değerleri sadece dize değerleridir. Herhangi bir özellik değeri üzerinde çalışmak için dize (örnek) yöntemlerini kullanabilirsiniz. Örneğin, bu kodu kullanarak tam bir yolu temsil eden bir yapı özelliğinden sürücü adını (ilk üç karakter) ayıklayabilirsiniz:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Statik özellik fonksiyonları

Yapı komut dosyanızda, birçok sistem sınıfının statik özelliklerine ve yöntemlerine erişebilirsiniz. Statik bir özelliğin değerini almak için, Sınıf \<>'nin sistem sınıfının adı \<olduğu ve Özellik> özelliğin adı olduğu aşağıdaki sözdizimini kullanın.

```
$([Class]::Property)
```

Örneğin, yapı özelliğini geçerli tarih ve saate ayarlamak için aşağıdaki kodu kullanabilirsiniz.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Statik bir yöntem çağırmak için, Sınıf \<> sistem sınıfının adı, \<Yöntem> yöntemin adı ve\<( Parametreler>) yöntemiçin parametre listesi olduğu aşağıdaki sözdizimini kullanın:

```
$([Class]::Method(Parameters))
```

Örneğin, yapı özelliğini yeni bir GUID olarak ayarlamak için bu komut dosyasını kullanabilirsiniz:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

Statik özellik işlevlerinde, bu sistem sınıflarının herhangi bir statik yöntemini veya özelliğini kullanabilirsiniz:

- System.Byte
- Char
- Convert
- Datetime
- Decimal
- Double
- System.Enum
- System.Guid
- Sistem.Int16
- Sistem.Int32
- Sistem.Int64
- System.IO.Path
- Math
- System.Runtime.InteropServices.OSPlatform
- System.Runtime.InteropServices.RuntimeInformation
- Sistem.UInt16
- Sistem.UInt32
- Sistem.UInt64
- System.SByte
- System.Single
- System
- System.StringComparer
- Timespan
- System.Text.RegularExpressions.Regex
- System.UriBuilder
- Version
- Microsoft.Build.Utilities.ToolLocationHelper

Ayrıca, aşağıdaki statik yöntemleri ve özellikleri kullanabilirsiniz:

- System.Environment::CommandLine
- System.Environment::ExpandEnvironmentVariables
- System.Environment::GetEnvironmentVariable
- System.Environment::GetEnvironmentVariables
- System.Environment::GetFolderPath
- System.Environment::GetLogicalSürücüler
- System.IO.Directory::GetDirectories
- System.IO.Directory::GetFiles
- System.IO.Directory::GetLastAccessTime
- System.IO.Directory::GetLastWriteTime
- System.IO.Directory::GetParent
- System.IO.File::Var
- System.IO.File::GetCreationTime
- System.IO.File::GetAttributes
- System.IO.File::GetLastAccessTime
- System.IO.File::GetLastWriteTime
- System.IO.File::ReadAllText

### <a name="calling-instance-methods-on-static-properties"></a>Statik özelliklere örnek yöntemleri çağırma

Nesne örneğini döndüren statik bir özelliğe eriştiyseniz, bu nesnenin örnek yöntemlerini çağırabilirsiniz. Örnek bir yöntem çağırmak için, Sınıf \<> sistem sınıfının adı, \<Özellik> özelliğin adı, \<Yöntem> yöntemin adı ve\<( Parametreler>) yöntemiçin parametre listesi olduğu aşağıdaki sözdizimini kullanın:

```
$([Class]::Property.Method(Parameters))
```

Sınıfın adı, ad alanı yla tam olarak nitelikli olmalıdır.

Örneğin, yapı özelliğini bugün geçerli tarihe ayarlamak için aşağıdaki kodu kullanabilirsiniz.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>MSBuild özellik fonksiyonları

Yapınızdaki çeşitli statik yöntemlere erişilen aritmetik, bitwise mantıksal ve kaçış karakter desteği sağlamak için. Bu yöntemlere, Yöntem>'nin \<yöntemin adı ve (Parametreler\<>) yöntemin parametre listesi olduğu aşağıdaki sözdizimini kullanarak erişebilirsiniz.

```
$([MSBuild]::Method(Parameters))
```

Örneğin, sayısal değerlere sahip iki özelliği bir araya getirmek için aşağıdaki kodu kullanın.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Burada MSBuild özellik işlevlerinin bir listesi:

|İşlev imzası|Açıklama|
|------------------------|-----------------|
|çift Ekle(çift a, çift b)|İki çift ekleyin.|
|uzun Ekle (uzun a, uzun b)|İki long saki ekle.|
|çift Çıkarma (çift a, çift b)|İki dublör çıkar.|
|uzun Çıkarma (uzun a, uzun b)|İki uzunluk çıkar.|
|çift Çarpma (çift a, çift b)|İki katı çarpın.|
|uzun Çarpma (uzun a, uzun b)|İki uzunla çarpın.|
|çift Bölme (çift a, çift b)|İki katı böl.|
|uzun Bölme (uzun a, uzun b)|İki uzunluk böl.|
|çift Modulo(çift a, çift b)|Modulo iki çift.|
|uzun Modulo(uzun a, uzun b)|Modulo iki uzun.|
|string Escape(string unescape)|MSBuild kaçış kurallarına göre dize kaçış.|
|string Unescape(string kaçtı)|MSBuild kaçış kurallarına göre dize kaçış.|
|int BitwiseOr(int birinci, int ikinci)|Birinci ve `OR` ikinci (ilk &#124; ikinci) biraz akıllıca gerçekleştirin.|
|int BitwiseAnd(int birinci, int ikinci)|Birinci ve `AND` ikinci (ilk & ikinci) biraz akıllıca gerçekleştirin.|
|int BitwiseXor(int birinci, int ikinci)|Birinci ve `XOR` ikinci (ilk ^ ikinci) biraz akıllıca gerçekleştirin.|
|int BitwiseNot(int ilk)|Biraz akıllıca `NOT` gerçekleştirin (~ilk).|
|bool IsOsPlatform(string platformString)|Geçerli işletim sistemi platformunun. `platformString` `platformString`<xref:System.Runtime.InteropServices.OSPlatform>üyesi olmalıdır.|
|bool IsOSUnixLike()|Geçerli işletim sistemi bir Unix sistemi ise doğrudur.|
|string NormalizePath(params string[] yolu)|Sağlanan yolun kanonikleştirilmiş tam yolunu alır ve geçerli işletim sistemi için doğru dizin ayırıcı karakterleri içerir sağlar.|
|string NormalizeDirectory(params string[] yolu)|Sağlanan dizinin kanonikleştirilmiş tam yolunu alır ve bir izleme eğik çizgi sağlarken geçerli işletim sistemi için doğru dizin ayırıcı karakterleri içerir sağlar.|
|string EnsureTrailingSlash(string yolu)|Verilen yol bir izleme eğik çizgi yoksa o zaman bir ekleyin. Yol boş bir dizeise, onu değiştirmez.|
|string GetPathOfFileAbove(string dosyası, string başlangıçDirectory)|Tam yolu arar ve geçerli yapı dosyasının konumunun üzerindeki dizin yapısındaki bir `startingDirectory`dosyaya veya belirtildiği takdirde ,|
|GetDirectoryNameOfFileAbove(string başlangıçDirectory, string fileName)|Bir dosyanın dizinini belirtilen dizinde veya bu dizinin üzerindeki dizin yapısındaki bir konumu bulun ve döndürün.|
|string MakeRelative(string basePath, string path)|Göreceli `path` hale `basePath`getirir. `basePath`mutlak bir dizin olmalıdır. Göreceli `path` olarak yapılamıyorsa, tam olarak döndürülür. Benzer `Uri.MakeRelativeUri`.|
|string ValueOrDefault(string conditionValue, string defaultValue)|'defaultValue' parametresi 'conditionValue' boşsa, diğer, değer koşuldeğeriDeğer'i döndürün.|

## <a name="nested-property-functions"></a>İç içe özellik işlevleri

Aşağıdaki örnekte görüldüğü gibi, özellik işlevlerini birleştirerek daha karmaşık işlevler oluşturabilirsiniz.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Bu örnek, yol <xref:System.IO.FileAttributes> `Archive` `tempFile`tarafından verilen dosyanın bit (32 veya 0) değerini döndürür. Numaralandırılmış veri değerlerinin özellik işlevleri içinde ada göre görünemeyeceğine dikkat edin. Bunun yerine sayısal değer (32) kullanılmalıdır.

Meta veriler iç içe geçen özellik işlevlerinde de görünebilir. Daha fazla bilgi için [Toplu İşlem'e](../msbuild/msbuild-batching.md)bakın.

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

MSBuild'teki `DoesTaskHostExist` özellik işlevi, belirtilen çalışma zamanı ve mimari değerleri için şu anda bir görev ana bilgisayarının yüklü olup olmadığını döndürür.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild Güvenli TrailingSlash

MSBuild'teki `EnsureTrailingSlash` özellik işlevi, zaten yoksa, bir çizgi oluşturur.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

MSBuild `GetDirectoryNameOfFileAbove` özellik işlevi, yoldaki geçerli dizin üzerinde dizinlerde bir dosya arar.

 Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Aşağıdaki kod bu sözdizimine bir örnektir.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

MSBuild'teki `GetPathOfFileAbove` özellik işlevi, geçerli dizinin üzerindeki dizin yapısında bulunuyorsa, belirtilen dosyanın yolunu döndürür. İşlevsel olarak aramaya eşdeğerdir

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` özellik işlevi bir kayıt defteri anahtarının değerini döndürür. Bu işlev iki bağımsız değişken, anahtar adı ve değer adı alır ve kayıt defterinden değeri döndürür. Bir değer adı belirtmezseniz, varsayılan değer döndürülür.

Aşağıdaki örnekler, bu işlevin nasıl kullanıldığını gösterir:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

MSBuild `GetRegistryValueFromView` özellik işlevi, kayıt defteri anahtarı, değeri ve bir veya daha fazla sıralı kayıt defteri görünümü verilen sistem kayıt defteri verilerini alır. Anahtar ve değer, bulunana kadar her kayıt defteri görünümünde sırayla aranır.

Bu özellik işlevi için sözdizimi:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Windows 64-bit işletim sistemi, 32 bit uygulamalar için **HKEY_LOCAL_MACHINE\SOFTWARE** kayıt defteri görünümü sunan bir **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** kayıt defteri anahtarını korur.

Varsayılan olarak, WOW64'te çalışan 32 bit lik bir uygulama 32 bit kayıt defteri görünümüne erişir ve 64 bit uygulama 64 bit kayıt defteri görünümüne erişer.

Aşağıdaki kayıt defteri görünümleri kullanılabilir:

|Kayıt defteri görünümü|Tanım|
|-------------------|----------------|
|RegistryView.Registry32|32 bit uygulama kayıt defteri görünümü.|
|RegistryView.Registry64|64 bit uygulama kayıt defteri görünümü.|
|RegistryView.Default|Uygulamanın yürüttüğü işlemle eşleşen kayıt defteri görünümü.|

Bir örnek verilmiştir.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

64 bit kayıt defteri görünümünde önce ve ardından 32 bit kayıt defteri görünümünde **bakarak, ReferenceAssemblies** anahtarının **SLRuntimeInstallPath** verilerini alır.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

MSBuild `MakeRelative` özellik işlevi, ikinci yolun göreli yolunu ilk yola göredöndürür. Her yol bir dosya veya klasör olabilir.

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

MSBuild `ValueOrDefault` özellik işlevi, null veya boş olmadığı sürece ilk bağımsız değişkeni döndürür. İlk bağımsız değişken boş veya boşsa, işlev ikinci bağımsız değişkeni döndürür.

Aşağıdaki örnekte, bu işlevin nasıl kullanıldığı gösterilmektedir.

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

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)

- [MSBuild'e genel bakış](../msbuild/msbuild.md)
