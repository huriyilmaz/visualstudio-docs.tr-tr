---
title: '&lt;Installdenetimlerin &gt; öğesi (önyükleyici) | Microsoft Docs'
description: Installdenetimleri öğesi, bir uygulamaya ait tüm önkoşulların yüklendiğinden emin olmak için yerel bilgisayardaki çeşitli testlerin başlatılmasını destekler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 0f2487489d75ca4ce7275153fd754b6fac7ebf5e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051579"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;Installdenetimlerin &gt; öğesi (önyükleyici)
`InstallChecks`Öğesi, bir uygulamaya yönelik tüm uygun önkoşulların yüklendiğinden emin olmak için yerel bilgisayara karşı çeşitli testlerin başlatılmasını destekler.

## <a name="syntax"></a>Syntax

```xml
<InstallChecks>
    <AssemblyCheck
        Property
        Name
        PublicKeyToken
        Version
        Language
        ProcessorArchitecture
    />
    <RegistryCheck
        Property
        Key
        Value
    />
    <ExternalCheck
        PackageFile
        Property
        Arguments
    />
    <FileCheck
        Property
        FileName
        SearchPath
        SpecialFolder
        SearchDepth
    />
    <MsiProductCheck
        Property
        Product
        Feature
    />
    <RegistryFileCheck
        Property
        Key
        Value
        FileName
        SearchDepth
    />
</InstallChecks>
```

## <a name="assemblycheck"></a>AssemblyCheck
 Bu öğe, öğesinin isteğe bağlı bir alt öğesidir `InstallChecks` . Her bir örneği için `AssemblyCheck` Önyükleyici, genel derleme önbelleğinde (GAC) öğe tarafından tanımlanan derlemenin mevcut olduğundan emin olur. Öğesi içermez ve aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Property`|Gereklidir. Sonucu depolayacak özelliğin adı. Bu özelliğe, öğesinin alt öğesi olan öğesinin altındaki bir testten başvurulabilir `InstallConditions` `Command` . Daha fazla bilgi için bkz. [ \<Commands> öğesi](../deployment/commands-element-bootstrapper.md).|
|`Name`|Gereklidir. Denetlenecek derlemenin tam adı.|
|`PublicKeyToken`|Gereklidir. Bu kesin adlandırılmış bütünleştirilmiş kod ile ilişkili ortak anahtarın kısaltılmış biçimi. GAC 'de depolanan tüm derlemeler bir ada, sürüme ve ortak anahtara sahip olmalıdır.|
|`Version`|Gereklidir. Derlemenin sürümü.<br /><br /> Sürüm numarası şu biçimdedir \<*major version*> ... \<*minor version*> \<*build version*> \<*revision version*> .|
|`Language`|İsteğe bağlı. Yerelleştirilmiş bir derlemenin dili. `neutral` varsayılan değerdir.|
|`ProcessorArchitecture`|İsteğe bağlı. Bu yüklemenin hedeflediği bilgisayar işlemcisi. `msil` varsayılan değerdir.|

## <a name="externalcheck"></a>ExternalCheck
 Bu öğe, öğesinin isteğe bağlı bir alt öğesidir `InstallChecks` . Her bir örneği için `ExternalCheck` , önyükleyici adlandırılmış dış programı ayrı bir işlemde yürütür ve onun çıkış kodunu tarafından belirtilen özellikte depolar `Property` . `ExternalCheck` karmaşık bağımlılık denetimleri uygulamak için veya bir bileşenin varlığını denetetmenin tek yolu bu örneği oluşturmak için kullanışlıdır.

 `ExternalCheck` öğesi içermez ve aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Property`|Gereklidir. Sonucu depolayacak özelliğin adı. Bu özelliğe, öğesinin alt öğesi olan öğesinin altındaki bir testten başvurulabilir `InstallConditions` `Command` . Daha fazla bilgi için bkz. [ \<Commands> öğesi](../deployment/commands-element-bootstrapper.md).|
|`PackageFile`|Gereklidir. Yürütülecek harici program. Program, kurulum dağıtım paketinin parçası olmalıdır.|
|`Arguments`|İsteğe bağlı. Tarafından adlandırılan yürütülebilir dosyaya komut satırı bağımsız değişkenleri sağlar `PackageFile` .|

## <a name="filecheck"></a>Dosya denetimi
 Bu öğe, öğesinin isteğe bağlı bir alt öğesidir `InstallChecks` . Her bir örneği için `FileCheck` , önyükleyici adlandırılmış dosyanın mevcut olup olmadığını tespit eder ve dosyanın sürüm numarasını döndürür. Dosyanın bir sürüm numarası yoksa, önyükleyici adlı özelliği ile `Property` 0 olarak ayarlar. Dosya yoksa, `Property` herhangi bir değere ayarlı değildir.

 `FileCheck` öğesi içermez ve aşağıdaki özniteliklere sahiptir.

| Öznitelik | Açıklama |
|-----------------| - |
| `Property` | Gereklidir. Sonucu depolayacak özelliğin adı. Bu özelliğe, öğesinin alt öğesi olan öğesinin altındaki bir testten başvurulabilir `InstallConditions` `Command` . Daha fazla bilgi için bkz. [ \<Commands> öğesi](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Gereklidir. Bulunacak dosyanın adı. |
| `SearchPath` | Gereklidir. Dosyanın aranacağı disk veya klasör. Bu, atanmışsa göreli bir yol olmalıdır `SpecialFolder` ; Aksi takdirde, mutlak bir yol olmalıdır. |
| `SpecialFolder` | İsteğe bağlı. Windows veya için özel anlamlı olan bir klasör [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Varsayılan değer `SearchPath` mutlak yol olarak yorumlanamıyor. Geçerli değerler şunlardır:<br /><br /> `AppDataFolder`. Bu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama için geçerli kullanıcıya özgü uygulama verileri klasörü.<br /><br /> `CommonAppDataFolder`. Tüm kullanıcılar tarafından kullanılan uygulama verileri klasörü.<br /><br /> `CommonFilesFolder`. Geçerli Kullanıcı için ortak dosyalar klasörü.<br /><br /> `LocalDataAppFolder`. Dolaşım olmayan uygulamalar için veri klasörü.<br /><br /> `ProgramFilesFolder`. 32 bitlik uygulamalar için standart program dosyaları klasörü.<br /><br /> `StartUpFolder`. Sistem başlangıcında başlatılan tüm uygulamaları içeren klasör.<br /><br /> `SystemFolder`. 32 bitlik sistem dll 'Leri içeren klasör.<br /><br /> `WindowsFolder`. Windows sistemi yüklemesini içeren klasör.<br /><br /> `WindowsVolume`. Windows sistemi yüklemesini içeren sürücü veya bölüm. |
| `SearchDepth` | İsteğe bağlı. Adlandırılmış dosya için alt klasörlerin aranacağı derinlik. Arama öncelikle derinlemesine bir değer. Varsayılan değer 0 ' dır. Bu, aramayı ve SearchPath tarafından belirtilen en üst düzey klasöre `SpecialFolder` kısıtlar . |

## <a name="msiproductcheck"></a>MsiProductCheck
 Bu öğe, öğesinin isteğe bağlı bir alt öğesidir `InstallChecks` . önyükleyici, her bir örneği için `MsiProductCheck` , belirtilen Microsoft Windows Installer yüklemesinin tamamlanana kadar çalıştırılıp çalıştırılmadığını kontrol eder. Özellik değeri, yüklü ürünün durumuna bağlı olarak ayarlanır. Pozitif bir değer ürünün yüklü olduğunu, 0 veya-1 olduğunu gösterir. (daha fazla bilgi için lütfen bkz. msiqueryfeaturestate Windows Installer SDK işlevi.) . Windows Installer bilgisayarda yüklü değilse, `Property` ayarlı değildir.

 `MsiProductCheck` öğesi içermez ve aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Property`|Gereklidir. Sonucu depolayacak özelliğin adı. Bu özelliğe, öğesinin alt öğesi olan öğesinin altındaki bir testten başvurulabilir `InstallConditions` `Command` . Daha fazla bilgi için bkz. [ \<Commands> öğesi](../deployment/commands-element-bootstrapper.md).|
|`Product`|Gereklidir. Yüklü ürün için GUID.|
|`Feature`|İsteğe bağlı. Yüklenen uygulamanın belirli bir özelliği için GUID.|

## <a name="registrycheck"></a>RegistryCheck
 Bu öğe, öğesinin isteğe bağlı bir alt öğesidir `InstallChecks` . Önyükleyici, her bir örneği için `RegistryCheck` belirtilen kayıt defteri anahtarının var olup olmadığını veya belirtilen değere sahip olup olmadığını denetler.

 `RegistryCheck` hiçbir öğe içerir ve aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Property`|Gereklidir. Sonucu depolamak için özelliğin adı. Bu özelik, öğesinin alt öğesi olan `InstallConditions` öğesinin altındaki bir testten `Command` başvurulabilirsiniz. Daha fazla bilgi için bkz. [ \<Commands> Öğesi.](../deployment/commands-element-bootstrapper.md)|
|`Key`|Gereklidir. Kayıt defteri anahtarının adı.|
|`Value`|İsteğe bağlı. Alınan kayıt defteri değerinin adı. Varsayılan değer, varsayılan değerin metnini geri dönmektir. `Value` bir Dize veya DWORD olmalıdır.|

## <a name="registryfilecheck"></a>RegistryFileCheck
 Bu öğe isteğe bağlı bir alt `InstallChecks` öğesidir. her örneği için, önyükleyici belirtilen dosyanın sürümünü, önce belirtilen kayıt defteri anahtarından dosyanın yolunu almaya `RegistryFileCheck` çalışırken alınır. Bu, özellikle kayıt defterinde değer olarak belirtilen bir dizinde bir dosyayı görmek için kullanışlıdır.

 `RegistryFileCheck` hiçbir öğe içerir ve aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Property`|Gereklidir. Sonucu depolamak için özelliğin adı. Bu özelik, öğesinin alt öğesi olan `InstallConditions` öğesinin altındaki bir testten `Command` başvurulabilirsiniz. Daha fazla bilgi için bkz. [ \<Commands> Öğesi.](../deployment/commands-element-bootstrapper.md)|
|`Key`|Gereklidir. Kayıt defteri anahtarının adı. Özniteliği ayarlanmadıkça değeri bir dosyanın yolu `File` olarak yorumlanır. Bu anahtar yoksa `Property` ayarlanmaz.|
|`Value`|İsteğe bağlı. Alınan kayıt defteri değerinin adı. Varsayılan değer, varsayılan değerin metnini geri dönmektir. `Value` bir Dize olmalıdır.|
|`FileName`|İsteğe bağlı. Bir dosyanın adı. Belirtilirse, kayıt defteri anahtarından alınan değerin bir dizin yolu olduğu varsayılır ve bu ad buna eklenir. Belirtilmezse, kayıt defterinden döndürülen değerin bir dosyanın tam yolu olduğu varsayılır.|
|`SearchDepth`|İsteğe bağlı. Adlandırılmış dosya için alt klasörlerin aranma derinliği. Arama önce derinliktir. Varsayılan değer 0'dır ve bu da aramanın kayıt defteri anahtarının değeri tarafından belirtilen üst düzey klasörle kısıtlar.|

## <a name="remarks"></a>Açıklamalar
 Altındaki öğeler `InstallChecks` çalıştıracak testleri tanımlar ancak bunları yürütmez. Testleri yürütmek için öğesinin altında `Command` öğeler oluşturmanız `Commands` gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, öğesi için ürün dosyasında kullanılan `InstallChecks` öğesini .NET Framework.

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>ınstallconditions
 Değerlendirilerek `InstallChecks` özellikler üretirler. Özellikler daha sonra tarafından, bir `InstallConditions` paketin yükleme, atlama veya başarısız olması gerektiğini belirlemek için kullanılır. Aşağıdaki tabloda aşağıdaki liste yer `InstallConditions` alır:

|Koşul|Açıklama|
|-|-|
|`FailIf`|Herhangi bir `FailIf` koşul true olarak değerlendirilirse paket başarısız olur. Koşulların geri kalanı değerlendirilmez.|
|`BypassIf`|Herhangi bir `BypassIf` koşul true olarak değerlendirilirse paket atlanır. Koşulların geri kalanı değerlendirilmez.|

## <a name="predefined-properties"></a>Önceden tanımlanmış özellikler
 Aşağıdaki tablo ve öğelerini `BypassIf` `FailIf` listeler:

|Özellik|Notlar|Olası Değerler|
|--------------|-----------|---------------------|
|`Version9X`|Windows 9X işletim sisteminin sürüm numarası.|4,10 = Windows 98|
|`VersionNT`|Windows NT tabanlı bir işletim sisteminin sürüm numarası.|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|
|`VersionNT64`|64 bitlik ve Windows NT işletim sisteminin sürüm numarası.|Daha önce belirtildiği gibi.|
|`VersionMsi`|Windows Installer hizmetinin sürüm numarası.|2.0 = Windows Yükleyicisi 2.0|
|`AdminUser`|Bir kullanıcının Windows NT tabanlı bir işletim sisteminde yönetici ayrıcalıklarına sahip olup olmadığını belirtir.|0 = yönetici ayrıcalıkları yok<br /><br /> 1 = yönetici ayrıcalıkları|

 Örneğin, Windows 95 çalıştıran bir bilgisayara yüklemesini engellemek için aşağıdaki gibi bir kod kullanın:

```xml
    <!-- Block install on Windows 95 -->
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>
```

 Bir FailIf veya BypassIf koşulu karşılanırsa yükleme denetimlerini çalıştırmayı atlamak için BeforeInstallChecks özniteliğini kullanın.  Örnek:

```xml
    <!-- Block install and do not evaluate install checks if user does not have admin privileges -->
    <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired" BeforeInstallChecks="true"/>
```

>[!NOTE]
>özniteliği, `BeforeInstallChecks` Visual Studio 2019 Güncelleştirme 9 sürümüyle başlayarak de desteklemektedir.

## <a name="see-also"></a>Ayrıca bkz.
- [\<Commands> Öğe](../deployment/commands-element-bootstrapper.md)
- [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)