---
title: Özellik Işlevleri | Microsoft Docs
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
ms.openlocfilehash: b0551162a00437b01c7357dfdac16462aad8f2fc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597392"
---
# <a name="property-functions"></a>Özellik işlevleri

.NET Framework sürüm 4 ve 4,5 ' de, MSBuild betikleri değerlendirmek için özellik işlevleri kullanılabilir. Özellik işlevleri, özelliklerin göründüğü her yerde kullanılabilir. Görevlerin aksine, özellik işlevleri hedeflerin dışında kullanılabilir ve herhangi bir hedef çalışmadan önce değerlendirilir.

 MSBuild görevlerini kullanmadan, sistem saatini okuyabilir, dizeleri karşılaştırabilir, normal ifadelerle eşleştirebilir ve derleme betiğinizdeki diğer işlemleri gerçekleştirebilirsiniz. MSBuild, dizeyi sayı ve sayı olarak dizeye dönüştürmeye ve diğer dönüştürmeleri gereken şekilde dönüştürmeye çalışır.
 
Özellik işlevlerinden döndürülen dize değerleri [özel karakterlerin](msbuild-special-characters.md) atlanmalıdır. Değerin doğrudan proje dosyasına yerleştirilmiş gibi değerlendirilmesini istiyorsanız, özel karakterlerin atmasını kaldırmak için `$([MSBuild]::Unescape())` kullanın.

## <a name="property-function-syntax"></a>Özellik işlevi sözdizimi

Bunlar, üç tür özellik işlevleridir; Her işlevde farklı bir sözdizimi vardır:

- String (örnek) özellik işlevleri
- Static özellik işlevleri
- MSBuild özellik işlevleri

### <a name="string-property-functions"></a>Dize özelliği işlevleri

Tüm derleme özelliği değerleri yalnızca dize değerleridir. Herhangi bir özellik değerinde çalışmak için dize (örnek) yöntemlerini kullanabilirsiniz. Örneğin, bu kodu kullanarak tam yolu temsil eden bir Build özelliğinden sürücü adını (ilk üç karakter) ayıklayabilirsiniz:

```fundamental
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Static özellik işlevleri

Yapı betiğinizdeki birçok sistem sınıfının statik özelliklerine ve yöntemlerine erişebilirsiniz. Statik bir özelliğin değerini almak için aşağıdaki sözdizimini kullanın; burada \<class > Sistem sınıfının adı ve \<Özellik > özelliğin adıdır.

```fundamental
$([Class]::Property)
```

Örneğin, geçerli tarih ve saate bir Build özelliği ayarlamak için aşağıdaki kodu kullanabilirsiniz.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Statik bir yöntemi çağırmak için aşağıdaki sözdizimini kullanın; burada \<class > Sistem sınıfının adıdır, \<Yöntem > yöntemin adıdır ve (\<Parameters >) yöntemin parametre listesidir:

```fundamental
$([Class]::Method(Parameters))
```

Örneğin, bir yapı özelliğini yeni bir GUID 'ye ayarlamak için bu betiği kullanabilirsiniz:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

Statik Özellik işlevlerinde, bu sistem sınıflarının herhangi bir statik yöntemini veya özelliğini kullanabilirsiniz:

- System. Byte
- System. Char
- System. Convert
- System.DateTime
- System. Decimal
- System. Double
- System. Enum
- System. Guid
- System. Int16
- System.Int32
- System.Int64
- System. ıO. Path
- System. Math
- System. Runtime. InteropServices. OSPlatform
- System.Runtime.InteropServices.RuntimeInformation
- System. UInt16
- System.UInt32
- System.UInt64
- System. SByte
- System. Single
- System. String
- System. StringComparer
- System.TimeSpan
- System.Text.RegularExpressions.Regex
- System. UriBuilder
- System. Version
- Microsoft. Build. Utilities. ToolLocationHelper

Ayrıca, aşağıdaki statik yöntemleri ve özellikleri kullanabilirsiniz:

- System. Environment:: CommandLine
- System. Environment:: ExpandEnvironmentVariables
- System. Environment:: GetEnvironmentVariable
- System. Environment:: GetEnvironmentVariables
- System. Environment:: GetFolderPath
- System. Environment:: GetLogicalDrives
- System. ıO. Directory:: Getdizinler
- System. ıO. Directory:: GetFiles
- System. ıO. Directory:: GetLastAccessTime
- System. ıO. Directory:: GetLastWriteTime
- System. ıO. Directory:: GetParent
- System. ıO. File:: Exists
- System. ıO. File:: GetCreationTime
- System. ıO. File:: GetAttributes
- System. ıO. File:: GetLastAccessTime
- System. ıO. File:: GetLastWriteTime
- System. ıO. File:: ReadAllText

### <a name="calling-instance-methods-on-static-properties"></a>Statik özelliklerde örnek yöntemleri çağırma

Bir nesne örneği döndüren statik bir özelliğe eriştiğinizde, bu nesnenin örnek yöntemlerini çağırabilirsiniz. Bir örnek yöntemi çağırmak için aşağıdaki sözdizimini kullanın; burada \<class > Sistem sınıfının adıdır, \<Özellik > özelliğin adıdır \<Yöntem > yöntemin adıdır ve (\<Parameters >) yöntemin parametre listesidir:

```fundamental
$([Class]::Property.Method(Parameters))
```

Sınıfın adı ad alanıyla tam olarak nitelenmelidir.

Örneğin, bir Build özelliğini bugün geçerli tarihe ayarlamak için aşağıdaki kodu kullanabilirsiniz.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>MSBuild özellik işlevleri

Derlemenize yönelik birkaç statik yönteme aritmetik, bit düzeyinde mantıksal ve çıkış karakteri desteği sağlamak için erişilebilir. Aşağıdaki sözdizimini kullanarak bu yöntemlere erişebilirsiniz; burada \<yöntemi > yöntemin adı ve (\<Parameters >) yöntemin parametre listesidir.

```fundamental
$([MSBuild]::Method(Parameters))
```

Örneğin, sayısal değerlere sahip iki özelliği birlikte eklemek için aşağıdaki kodu kullanın.

```fundamental
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
|int Bitwiseveya (int First, INT Second)|İlk ve ikinci bit düzeyinde bir `OR` gerçekleştirin (ilk &#124; saniye).|
|Int Bitwiseve (int First, int Second)|Birinci ve ikinci bit düzeyinde bir `AND` gerçekleştirin (ilk & saniye).|
|Int BitwiseXor (int First, int Second)|İlk ve ikinci bit düzeyinde bir `XOR` gerçekleştirin (ilk ^ saniye).|
|Int Bitwıenot (ilk tamsayı)|Bit düzeyinde `NOT` gerçekleştirin (ilk).|
|bool ısosplatform (dize platformString)|Geçerli işletim sistemi platformunun `platformString`olup olmadığını belirtin. `platformString`, <xref:System.Runtime.InteropServices.OSPlatform>bir üyesi olmalıdır.|
|bool ıosunixlike ()|Geçerli işletim sistemi bir UNIX sistemse true.|
|String NormalizePath (params String [] yol)|Belirtilen yolun kurallı tam yolunu alır ve geçerli işletim sistemi için doğru dizin ayırıcı karakterlerini içerdiğinden emin olur.|
|String NormalizeDirectory (params String [] yol)|Belirtilen dizinin kurallı tam yolunu alır ve sonunda eğik çizgi olduğundan emin olarak geçerli işletim sistemi için doğru dizin ayırıcı karakterlerini içerir.|
|dize Ensugeri çekme bölgesi (dize yolu)|Verilen yolun sonunda eğik çizgi yoksa bir tane ekleyin. Yol boş bir dize ise, onu değiştirmez.|
|String Getpathoffileyukarıdaki (dize dosyası, dize startingDirectory)|Geçerli derleme dosyasının konumuna göre veya belirtilmişse `startingDirectory`göre bir dosya arar.|
|Getdirectorynameoffileyukarıdaki (dize startingDirectory, dize fileName)|Belirtilen dizinde veya dizinin üzerindeki dizin yapısında bulunan bir konuma bir dosya bulun.|
|String MakeRelative (dize basePath, dize yolu)|`path` `basePath`göreli hale getirir. `basePath` mutlak bir dizin olmalıdır. `path` göreli hale getirilmezse, tam olarak döndürülür. `Uri.MakeRelativeUri`benzer.|
|dize ValueOrDefault (dize conditionValue, String defaultValue)|' DefaultValue ' parametresindeki dizeyi yalnızca ' conditionValue ' parametresi boşsa, Else değerini döndürün.|

## <a name="nested-property-functions"></a>İç içe özellik işlevleri

Aşağıdaki örnekte gösterildiği gibi daha karmaşık işlevler oluşturmak için özellik işlevlerini birleştirebilirsiniz.

```fundamental
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Bu örnek, yol `tempFile`tarafından verilen dosyanın <xref:System.IO.FileAttributes>`Archive` bit (32 veya 0) değerini döndürür. Numaralandırılmış veri değerlerinin özellik işlevleri içinde ada göre görünmediğine dikkat edin. Bunun yerine sayısal değer (32) kullanılmalıdır.

Meta veriler, iç içe geçmiş Özellik işlevlerinde de görünebilir. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.

## <a name="msbuild-doestaskhostexist"></a>MSBuild yok Taskhostexist

MSBuild 'teki `DoesTaskHostExist` Property işlevi, belirtilen çalışma zamanı ve mimari değerleri için bir görev konağının o anda yüklü olup olmadığını döndürür.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```fundamental
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild Ensuvanıingeğik çizgi

MSBuild 'teki `EnsureTrailingSlash` Property işlevi, zaten mevcut değilse sondaki eğik çizgi ekler.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```fundamental
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild Getdirectorynameoffileyukarıdaki

MSBuild `GetDirectoryNameOfFileAbove` Özellik işlevi, yoldaki geçerli dizinin üzerindeki dizinlerde bulunan bir dosyayı arar.

 Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```fundamental
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Aşağıdaki kod bu sözdizimine bir örnektir.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild Getpathoffileyukarıdaki

MSBuild 'teki `GetPathOfFileAbove` Property işlevi, dosyanın yolunu hemen önceki bir şekilde döndürür. Çağırmak için işlevsel olarak eşdeğerdir

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```fundamental
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` Özellik işlevi bir kayıt defteri anahtarının değerini döndürür. Bu işlev iki bağımsız değişken alır, anahtar adı ve değer adı ve kayıt defterindeki değeri döndürür. Bir değer adı belirtmezseniz, varsayılan değer döndürülür.

Aşağıdaki örneklerde bu işlevin nasıl kullanıldığı gösterilmektedir:

```fundamental
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

MSBuild `GetRegistryValueFromView` Özellik işlevi, kayıt defteri anahtarı, değeri ve bir veya daha fazla sıralanmış kayıt defteri görünümü verilen sistem kayıt defteri verilerini alır. Anahtar ve değer, her kayıt defteri görünümünde, bulunana kadar sırayla aranır.

Bu özellik işlevinin sözdizimi şöyledir:

```fundamental
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Windows 64-bit işletim sistemi, 32 bit uygulamalar için **HKEY_LOCAL_MACHINE \Software** kayıt defteri görünümü sunan bir **HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node** kayıt defteri anahtarı sağlar.

Varsayılan olarak, WOW64 üzerinde çalışan 32 bitlik bir uygulama 32 bit kayıt defteri görünümüne erişir ve 64 bit uygulama, 64 bit kayıt defteri görünümüne erişir.

Aşağıdaki kayıt defteri görünümleri kullanılabilir:

|Kayıt defteri görünümü|Tanım|
|-------------------|----------------|
|RegistryView. Registry32|32 bit uygulama kayıt defteri görünümü.|
|RegistryView. Registry64|64 bit uygulama kayıt defteri görünümü.|
|RegistryView. Default|Uygulamanın üzerinde çalıştığı işlemle eşleşen kayıt defteri görünümü.|

Aşağıda bir örnek verilmiştir.

 ```fundamental
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

önce 64 bit kayıt defteri görünümüne, sonra da 32 bit kayıt defteri görünümünde arayarak **ReferenceAssemblies** anahtarının **SLRuntimeInstallPath** verilerini alır.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

MSBuild `MakeRelative` Özellik işlevi, ilk yola göre ikinci yolun göreli yolunu döndürür. Her yol bir dosya veya klasör olabilir.

Bu özellik işlevi aşağıdaki sözdizimine sahiptir:

```fundamental
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

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)

- [MSBuild genel bakış](../msbuild/msbuild.md)
