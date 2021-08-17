---
title: Ürün ve Paket Şema Başvurusu | Microsoft Docs
description: Bir uygulamanın ihtiyaç ettiği dış bağımlılıkları açıklayan bir XML bildirimi olan ürün dosyası hakkında ClickOnce öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.CircularIncludes
- MSBuild.ResolveManifestFiles.PublishFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, product and package files
- Windows Installer, product and package files
- product files [ClickOnce]
- ClickOnce, bootstrapper elements
- package files [Windows Installer]
- product files [Windows Installer]
- package files [ClickOnce]
- Windows Installer, bootstrapper elements
ms.assetid: 5a74878f-b896-4cca-b968-98d00fe78fb0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 420d3ca592094b67210efd625a17d97545e7ec54
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065234"
---
# <a name="product-and-package-schema-reference"></a>Ürün ve paket şema başvurusu
Ürün *dosyası,* bir uygulamanın ihtiyaç ettiği tüm dış bağımlılıkları açıklayan bir XML [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimidir. Dış bağımlılıklara örnek olarak .NET Framework Ve Microsoft Veri Erişim Bileşenleri (MDAC) yer alır. Paket dosyası bir ürün dosyasına benzer, ancak yerelleştirilmiş derlemeler, lisans anlaşmaları ve belgeler gibi bağımlılığın kültüre bağımlı bileşenlerini yüklemek için kullanılır.

 Ürün ve paket dosyası, her biri aşağıdaki öğeleri içeren bir üst `Product` `Package` düzey veya öğeden oluşur.

|Öğe|Açıklama|Öznitelikler|
|-------------|-----------------|----------------|
|[\<Product> Öğe](../deployment/product-element-bootstrapper.md)|Ürün dosyaları için gerekli üst düzey öğe.|Hiçbiri|
|[\<Package> Öğe](../deployment/package-element-bootstrapper.md)|Paket dosyaları için gerekli üst düzey öğe.|`Culture`<br /><br /> `Name`<br /><br /> `EULA`|
|[\<RelatedProducts> Öğe](../deployment/relatedproducts-element-bootstrapper.md)|Ürün dosyaları için isteğe bağlı öğesi. Bu ürünün yüklemiş olduğu veya bağlı olduğu diğer ürünler.|Hiçbiri|
|[\<InstallChecks> Öğe](../deployment/installchecks-element-bootstrapper.md)|Gerekli öğe. Yükleme sırasında yerel bilgisayarda gerçekleştirecek bağımlılık denetimlerini listeler.|Hiçbiri|
|[\<Commands> Öğe](../deployment/commands-element-bootstrapper.md)|Gerekli öğe.  tarafından açıklandığı gibi bir veya daha fazla yükleme denetimi yürütür ve denetim `InstallChecks` başarısız olursa hangi paketin yük kurulacak olduğunu ifade ediyor.|Hiçbiri|
|[\<PackageFiles> Öğe](../deployment/packagefiles-element-bootstrapper.md)|Gerekli öğe. Bu yükleme işlemi tarafından yüklenebilirsiniz paketleri listeler.|Hiçbiri|
|[\<Strings> Öğe](../deployment/strings-element-bootstrapper.md)|Gerekli öğe. Ürün adı ve hata dizelerinin yerelleştirilmiş sürümlerini depolar.|Hiçbiri|

## <a name="remarks"></a>Açıklamalar
 Paket şeması, ms *Setup.exe* önyükleme görevi tarafından oluşturulan ve kendi çok az sabit kodlu mantığını içeren saplama programı olanSetup.exetarafından tüketilir. Şema, yükleme işleminin her yönünü destekler.

 `InstallChecks` bu setup.exe paketin varlığı için gerçekleştirmesi gereken testler. `PackageFiles` , verilen bir test başarısız olursa kurulum işleminin yüklemesi gerektirmiş olabileceği tüm paketleri listeler. Komutlar altındaki her Komut girişi, tarafından açıklanan testlerden birini yürütür ve testin `InstallChecks` başarısız `PackageFile` olması için çalıştıracakları testleri belirtir. Ürün adlarını ve hata iletilerini yerelleştirmek için öğesini kullanabilirsiniz, böylece herhangi bir sayıda dil için uygulamanızı yüklemek üzere tek bir yükleme `Strings` ikilisi kullanabilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, uygulamanın yüklemesi için eksiksiz bir ürün .NET Framework.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Product
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  ProductCode="Microsoft.Net.Framework.2.0"
>

    <RelatedProducts>
        <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
    </RelatedProducts>

    <!-- Defines list of files to be copied on build -->
    <PackageFiles>
        <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>
        <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
        <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
        <PackageFile Name="dotnetchk.exe"/>
    </PackageFiles>

    <InstallChecks>
        <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
        <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
    </InstallChecks>

    <!-- Defines how to invoke the setup for the .NET Framework redist -->
    <!-- TODO: Needs EstrimatedTempSpace, LogFile, and an update of EstimatedDiskSpace -->
    <Commands Reboot="Defer">
        <Command PackageFile="instmsia.exe"
                 Arguments= ' /q /c:"msiinst /delayrebootq"'
                 EstimatedInstallSeconds="20" >
            <InstallConditions>
                <BypassIf Property="VersionNT" Compare="ValueExists"/>
                <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>
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

                <!-- Block install if user does not have admin privileges -->
                <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>

                <!-- Block install on Windows 95 -->
                <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>

                <!-- Block install on Windows 2000 SP 2 or less -->
                <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>

                <!-- Block install if Internet Explorer 5.01 or greater is not present -->
                <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />
                <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />

                <!-- Block install if the platform is not x86 -->
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
</Product>
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)