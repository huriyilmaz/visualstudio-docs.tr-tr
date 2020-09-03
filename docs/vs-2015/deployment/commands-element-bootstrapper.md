---
title: '&lt;Commands &gt; öğesi (önyükleyici) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af10c9e0b26a6ef2c8e7a98bc345b8e86017682b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205341"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Commands &gt; öğesi (önyükleyici)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Commands`Öğesi, öğesinin altındaki öğeler tarafından tanımlanan testleri uygular `InstallChecks` ve [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] test başarısız olursa önyükleyici hangi pakete yükleneceğini bildirir.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `Commands`Öğe gereklidir. Öğesi aşağıdaki özniteliğe sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Reboot`|İsteğe bağlı. Paketlerin herhangi biri bir yeniden başlatma çıkış kodu döndürtakdirde sistemin yeniden başlatılıp başlatılmayacağını belirler. Aşağıdaki listede geçerli değerler gösterilmektedir:<br /><br /> `Defer`. Yeniden başlatma, gelecekte bir süre kadar ertelenir.<br /><br /> `Immediate`. Paketlerden biri bir yeniden başlatma çıkış kodu döndürmediğinde anında yeniden başlatmaya neden olur.<br /><br /> `None`. Yeniden başlatma isteklerinin yoksayılmasına neden olur.<br /><br /> Varsayılan değer: `Immediate`.|  
  
## <a name="command"></a>Komut  
 `Command`Öğesi, öğesinin bir alt öğesidir `Commands` . Bir `Commands` öğesinde bir veya daha fazla `Command` öğe olabilir. Öğesi aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`PackageFile`|Gereklidir. Yüklenecek paketin adı, false dönüş tarafından belirtilen bir veya daha fazla koşuldan oluşmalıdır `InstallConditions` . Paketin bir öğesi kullanılarak aynı dosyada tanımlanması gerekir `PackageFile` .|  
|`Arguments`|İsteğe bağlı. Paket dosyasına geçirilecek komut satırı bağımsız değişkenleri kümesi.|  
|`EstimatedInstallSeconds`|İsteğe bağlı. Saniye cinsinden tahmini süre, paketin yüklenmesi için sürer. Bu değer, önyükleyicinin kullanıcıya görüntülediği ilerleme çubuğunun boyutunu belirler. Varsayılan değer 0 ' dır ve bu durumda bir süre tahmini belirtilmez.|  
|`EstimatedDiskBytes`|İsteğe bağlı. Yükleme tamamlandıktan sonra paketin kaplayacağı, bayt cinsinden tahmini disk alanı miktarı. Bu değer, önyükleyicinin Kullanıcı tarafından görüntülediği sabit disk alanı gereksinimlerinde kullanılır. Varsayılan değer 0 ' dır, bu durumda önyükleyici herhangi bir sabit disk alanı gereksinimini göstermez.|  
|`EstimatedTempBytes`|İsteğe bağlı. Paketin gerekli olacağı, bayt cinsinden tahmini geçici disk alanı miktarı.|  
|`Log`|İsteğe bağlı. Paketin kök dizinine göre, paketin oluşturduğu günlük dosyasının yolu.|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions`Öğesi, öğesinin bir alt öğesidir `Command` . Her `Command` öğenin en fazla bir öğesi olabilir `InstallConditions` . Hiçbir `InstallConditions` öğe yoksa, tarafından belirtilen paket `Condition` her zaman çalışır.  
  
## <a name="bypassif"></a>BypassIf  
 Öğesi `BypassIf` öğesinin bir alt öğesidir `InstallConditions` ve komutun yürütülmemelidir pozitif bir durum tanımlar. Her `InstallConditions` öğenin sıfır veya daha fazla `BypassIf` öğesi olabilir.  
  
 `BypassIf` Aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Property`|Gereklidir. Sınanacak özelliğin adı. Özelliği daha önce öğesinin bir alt öğesi tarafından tanımlanmış olmalıdır `InstallChecks` . Daha fazla bilgi için bkz. [ \<InstallChecks> öğesi](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Gereklidir. Gerçekleştirilecek karşılaştırma türü. Aşağıdaki listede geçerli değerler gösterilmektedir:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Gereklidir. Özelliği ile karşılaştırılacak değer.|  
|`Schedule`|İsteğe bağlı. `Schedule`Bu kuralın değerlendirilmesi gerektiğinde tanımlayan bir etiketin adı.|  
  
## <a name="failif"></a>FailIf  
 Öğesi, `FailIf` öğesinin bir alt öğesidir `InstallConditions` ve yüklemesinin durması gereken pozitif bir koşulu açıklar. Her `InstallConditions` öğenin sıfır veya daha fazla `FailIf` öğesi olabilir.  
  
 `FailIf` Aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Property`|Gereklidir. Sınanacak özelliğin adı. Özelliği daha önce öğesinin bir alt öğesi tarafından tanımlanmış olmalıdır `InstallChecks` . Daha fazla bilgi için bkz. [ \<InstallChecks> öğesi](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Gereklidir. Gerçekleştirilecek karşılaştırma türü. Aşağıdaki listede geçerli değerler gösterilmektedir:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Gereklidir. Özelliği ile karşılaştırılacak değer.|  
|`String`|İsteğe bağlı. Hata sonrasında kullanıcıya görüntülenecek metin.|  
|`Schedule`|İsteğe bağlı. `Schedule`Bu kuralın değerlendirilmesi gerektiğinde tanımlayan bir etiketin adı.|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes`Öğesi, öğesinin bir alt öğesidir `Command` . `ExitCodes`Öğesi bir veya daha fazla `ExitCode` öğe içeriyor ve bu, yüklemenin bir paketten çıkış koduna yanıt olarak ne yapması gerektiğini belirleyen bir veya daha fazla öğe içeriyor. `ExitCode`Bir öğenin altında bir isteğe bağlı öğe olabilir `Command` . `ExitCodes` hiç özniteliği yok.  
  
## <a name="exitcode"></a>ExitCode  
 `ExitCode`Öğesi, öğesinin bir alt öğesidir `ExitCodes` . `ExitCode`Öğesi, yüklemenin bir paket üzerinden çıkış koduna yanıt olarak ne yapması gerektiğini belirler. `ExitCode` alt öğesi içermez ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Value`|Gereklidir. Bu öğenin uygulandığı çıkış kodu değeri `ExitCode` .|  
|`Result`|Gereklidir. Yükleme bu çıkış koduna nasıl tepki sağlamalıdır. Aşağıdaki listede geçerli değerler gösterilmektedir:<br /><br /> `Success`. Paketi başarıyla yüklendi olarak işaretler.<br /><br /> `SuccessReboot`. Paketi başarıyla yüklendi olarak işaretler ve sistemi yeniden başlatmasını söyler.<br /><br /> `Fail`. Paketi başarısız olarak işaretler.<br /><br /> `FailReboot`. Paketi başarısız olarak işaretler ve sistemi yeniden başlatmasını söyler.|  
|`String`|İsteğe bağlı. Bu çıkış koduna yanıt olarak kullanıcıya görüntülenecek değer.|  
|`FormatMessageFromSystem`|İsteğe bağlı. Çıkış koduna karşılık gelen sistem tarafından sağlanmış hata iletisinin kullanılıp kullanılmayacağını belirler veya içinde belirtilen değeri kullanın `String` . Geçerli değerler `true` , sistem tarafından sağlanmış hatanın kullanılması anlamına gelir ve `false` tarafından belirtilen dizeyi kullanmak anlamına gelir `String` . Varsayılan değer: `false`. Bu özellik `false` , ancak ayarlanmamışsa, `String` sistem tarafından belirtilen hata kullanılır.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği 2,0 .NET Framework yüklemeye yönelik komutları tanımlar.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks> Dosyalarında](../deployment/installchecks-element-bootstrapper.md)
