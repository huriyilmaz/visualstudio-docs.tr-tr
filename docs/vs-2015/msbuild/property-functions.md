---
title: Özellik Işlevleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4108e478e9e77a5ed5699b39dfae44884a6befd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826172"
---
# <a name="property-functions"></a>Özellik İşlevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Framework sürüm 4 ve 4,5 ' de, MSBuild betikleri değerlendirmek için özellik işlevleri kullanılabilir. Özellik işlevleri, özelliklerin göründüğü her yerde kullanılabilir. Görevlerin aksine, özellik işlevleri hedeflerin dışında kullanılabilir ve herhangi bir hedef çalışmadan önce değerlendirilir.  
  
 MSBuild görevlerini kullanmadan, sistem saatini okuyabilir, dizeleri karşılaştırabilir, normal ifadelerle eşleştirebilir ve derleme betiğinizdeki diğer işlemleri gerçekleştirebilirsiniz. MSBuild, dizeyi sayı ve sayı olarak dizeye dönüştürmeye ve diğer dönüştürmeleri gereken şekilde dönüştürmeye çalışır.  
  
 **Bu konuda:**  
  
- [Özellik Işlevi sözdizimi](#BKMK_Syntax)  
  
  - [Dize özelliği Işlevleri](#BKMK_String)  

  - [Static özellik Işlevleri](#BKMK_Static)  

  - [Statik özelliklerde örnek yöntemleri çağırma](#BKMK_InstanceMethods)  

  - [MSBuild özellik Işlevleri](#BKMK_PropertyFunctions)  
  
- [İç içe Özellik Işlevleri](#BKMK_Nested)  
  
- [MSBuild yok Taskhostexist](#BKMK_DoesTaskHostExist)  
  
- [MSBuild Getdirectorynameoffileyukarıdaki](#BKMK_GetDirectoryNameOfFileAbove)  
  
- [MSBuild GetRegistryValue](#BKMK_GetRegistryValue)  
  
- [MSBuild GetRegistryValueFromView](#BKMK_GetRegistryValueFromView)  
  
- [MSBuild MakeRelative](#BKMK_MakeRelative)  
  
- [MSBuild ValueOrDefault](#BKMK_ValueOrDefault)  
  
## <a name="property-function-syntax"></a><a name="BKMK_Syntax"></a> Özellik Işlevi sözdizimi  
 Bunlar, üç tür özellik işlevleridir; Her işlevde farklı bir sözdizimi vardır:  
  
- String (örnek) özellik işlevleri  
  
- Static özellik işlevleri  
  
- MSBuild özellik işlevleri  
  
### <a name="string-property-functions"></a><a name="BKMK_String"></a> Dize özelliği Işlevleri  
 Tüm derleme özelliği değerleri yalnızca dize değerleridir. Herhangi bir özellik değerinde çalışmak için dize (örnek) yöntemlerini kullanabilirsiniz. Örneğin, bu kodu kullanarak tam yolu temsil eden bir Build özelliğinden sürücü adını (ilk üç karakter) ayıklayabilirsiniz:  
  
 `$(ProjectOutputFolder.Substring(0,3))`  
  
### <a name="static-property-functions"></a><a name="BKMK_Static"></a> Static özellik Işlevleri  
 Yapı betiğinizdeki birçok sistem sınıfının statik özelliklerine ve yöntemlerine erişebilirsiniz. Statik bir özelliğin değerini almak için aşağıdaki sözdizimini kullanın; burada *sınıf* sistem sınıfının adıdır ve *özellik* özelliğin adıdır.  
  
 `$([Class]::Property)`  
  
 Örneğin, geçerli tarih ve saate bir Build özelliği ayarlamak için aşağıdaki kodu kullanabilirsiniz.  
  
 `<Today>$([System.DateTime]::Now)</Today>`  
  
 Statik bir yöntemi çağırmak için aşağıdaki sözdizimini kullanın; burada *sınıf* sistem sınıfının *adıdır, yöntem yöntemin adıdır* ve *(parametreler)* yöntemin parametre listesidir:  
  
 `$([Class]::Method(Parameters))`  
  
 Örneğin, bir yapı özelliğini yeni bir GUID 'ye ayarlamak için bu betiği kullanabilirsiniz:  
  
 `<NewGuid>$([System.Guid]::NewGuid())</NewGuid>`  
  
 Statik Özellik işlevlerinde, bu sistem sınıflarının herhangi bir statik yöntemini veya özelliğini kullanabilirsiniz:  
  
- System. Byte  
  
- System. Char  
  
- System. Convert  
  
- System. DateTime  
  
- System. Decimal  
  
- System. Double  
  
- System. Enum  
  
- System. Guid  
  
- System. Int16  
  
- System. Int32  
  
- System. Int64  
  
- System. ıO. Path  
  
- System. Math  
  
- System. UInt16  
  
- System. UInt32  
  
- System. UInt64  
  
- System. SByte  
  
- System. Single  
  
- System. String  
  
- System. StringComparer  
  
- System. TimeSpan  
  
- System. Text. RegularExpressions. Regex  
  
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
  
### <a name="calling-instance-methods-on-static-properties"></a><a name="BKMK_InstanceMethods"></a> Statik özelliklerde örnek yöntemleri çağırma  
 Bir nesne örneği döndüren statik bir özelliğe eriştiğinizde, bu nesnenin örnek yöntemlerini çağırabilirsiniz. Bir örnek yöntemi çağırmak için aşağıdaki sözdizimini kullanın; burada *sınıf* sistem sınıfının adıdır, *özellik* özelliğin adıdır, *Yöntem* yöntemin adıdır ve *(parametreler)* yöntemin parametre listesidir:  
  
 `$([Class]::Property.Method(Parameters))`  
  
 Sınıfın adı ad alanıyla tam olarak nitelenmelidir.  
  
 Örneğin, bir Build özelliğini bugün geçerli tarihe ayarlamak için aşağıdaki kodu kullanabilirsiniz.  
  
 `<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>`  
  
### <a name="msbuild-property-functions"></a><a name="BKMK_PropertyFunctions"></a> MSBuild özellik Işlevleri  
 Derlemenize yönelik birkaç statik yönteme aritmetik, bit düzeyinde mantıksal ve çıkış karakteri desteği sağlamak için erişilebilir. Aşağıdaki sözdizimini kullanarak bu yöntemlere erişebilirsiniz; burada *Yöntem* yöntemin adıdır ve *Parametreler* yöntemin parametre listesidir.  
  
 `$([MSBuild]::Method(Parameters))`  
  
 Örneğin, sayısal değerlere sahip iki özelliği birlikte eklemek için aşağıdaki kodu kullanın.  
  
 `$([MSBuild]::Add($(NumberOne), $(NumberTwo))`  
  
 MSBuild özellik işlevlerinin bir listesi aşağıdadır:  
  
|İşlev Imzası|Description|  
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
  
## <a name="nested-property-functions"></a><a name="BKMK_Nested"></a> İç içe Özellik Işlevleri  
 Aşağıdaki örnekte gösterildiği gibi daha karmaşık işlevler oluşturmak için özellik işlevlerini birleştirebilirsiniz.  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 Bu örnek, <xref:System.IO.FileAttributes> `Archive` yol tarafından verilen dosyanın bit (32 veya 0) değerini döndürür `tempFile` . Numaralandırılmış veri değerlerinin özellik işlevleri içinde ada göre görünmediğine dikkat edin. Bunun yerine sayısal değer (32) kullanılmalıdır.  
  
 Meta veriler, iç içe geçmiş Özellik işlevlerinde de görünebilir. Daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.  
  
## <a name="msbuild-doestaskhostexist"></a><a name="BKMK_DoesTaskHostExist"></a> MSBuild yok Taskhostexist  
 `DoesTaskHostExist`MSBuild 'teki Özellik işlevi, belirtilen çalışma zamanı ve mimari değerleri için bir görev konağının Şu anda yüklü olup olmadığını döndürür.  
  
 Bu özellik işlevi aşağıdaki sözdizimine sahiptir:  
  
```  
$[MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture)  
```  
  
## <a name="msbuild-getdirectorynameoffileabove"></a><a name="BKMK_GetDirectoryNameOfFileAbove"></a> MSBuild Getdirectorynameoffileyukarıdaki  
 MSBuild `GetDirectoryNameOfFileAbove` özelliği işlevi, yoldaki geçerli dizinin üzerindeki dizinlerde bulunan bir dosyayı arar.  
  
 Bu özellik işlevi aşağıdaki sözdizimine sahiptir:  
  
```  
$[MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile)  
```  
  
 Aşağıdaki kod bu sözdizimine bir örnektir.  
  
```  
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />  
```  
  
## <a name="msbuild-getregistryvalue"></a><a name="BKMK_GetRegistryValue"></a> MSBuild GetRegistryValue  
 MSBuild `GetRegistryValue` özelliği işlevi bir kayıt defteri anahtarının değerini döndürür. Bu işlev iki bağımsız değişken alır, anahtar adı ve değer adı ve kayıt defterindeki değeri döndürür. Bir değer adı belirtmezseniz, varsayılan değer döndürülür.  
  
 Aşağıdaki örneklerde bu işlevin nasıl kullanıldığı gösterilmektedir:  
  
```  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))  
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value  
  
```  
  
## <a name="msbuild-getregistryvaluefromview"></a><a name="BKMK_GetRegistryValueFromView"></a> MSBuild GetRegistryValueFromView  
 MSBuild `GetRegistryValueFromView` özelliği işlevi, kayıt defteri anahtarı, değeri ve bir veya daha fazla sıralı kayıt defteri görünümü verilen sistem kayıt defteri verilerini alır. Anahtar ve değer, her kayıt defteri görünümünde, bulunana kadar sırayla aranır.  
  
 Bu özellik işlevinin sözdizimi şöyledir:  
  
 [MSBuild \] :: GetRegistryValueFromView (dize KeyName, dize DeğerAdı, nesne DefaultValue, params nesnesi [] görünümleri)  
  
 Windows 64-bit işletim sistemi, 32 bit uygulamalar için HKEY_LOCAL_MACHINE \SOFTWARE kayıt defteri görünümü sunan bir HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node kayıt defteri anahtarı sağlar.  
  
 Varsayılan olarak, WOW64 üzerinde çalışan 32 bitlik bir uygulama 32 bit kayıt defteri görünümüne erişir ve 64 bit uygulama, 64 bit kayıt defteri görünümüne erişir.  
  
 Aşağıdaki kayıt defteri görünümleri kullanılabilir:  
  
|Kayıt defteri görünümü|Tanım|  
|-------------------|----------------|  
|RegistryView. Registry32|32 bit uygulama kayıt defteri görünümü.|  
|RegistryView. Registry64|64 bit uygulama kayıt defteri görünümü.|  
|RegistryView. Default|Uygulamanın üzerinde çalıştığı işlemle eşleşen kayıt defteri görünümü.|  
  
 Bir örnek verilmiştir.  
  
 `$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))`  
  
 önce 64 bit kayıt defteri görünümüne, sonra da 32 bit kayıt defteri görünümünde arayarak ReferenceAssemblies anahtarının SLRuntimeInstallPath verilerini alır.  
  
## <a name="msbuild-makerelative"></a><a name="BKMK_MakeRelative"></a> MSBuild MakeRelative  
 MSBuild `MakeRelative` özelliği işlevi, ilk yola göre ikinci yolun göreli yolunu döndürür. Her yol bir dosya veya klasör olabilir.  
  
 Bu özellik işlevi aşağıdaki sözdizimine sahiptir:  
  
```  
$[MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2))  
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
  
## <a name="msbuild-valueordefault"></a><a name="BKMK_ValueOrDefault"></a> MSBuild ValueOrDefault  
 MSBuild `ValueOrDefault` Özellik işlevi, null veya boş olmadığı takdirde ilk bağımsız değişkeni döndürür. İlk bağımsız değişken null veya boşsa, işlev ikinci bağımsız değişkeni döndürür.  
  
 Aşağıdaki örnek, bu işlevin nasıl kullanıldığını gösterir.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>  
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>  
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

## <a name="see-also"></a>Ayrıca Bkz.
[MSBuild özellikleri](msbuild-properties1.md)   
[MSBuild genel bakış](msbuild.md)
