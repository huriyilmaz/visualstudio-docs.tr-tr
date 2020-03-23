---
title: Önyükleyici paketleri oluşturma
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f84f91ebedd47df8c0804adee35dcbec18d8551
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301995"
---
# <a name="create-bootstrapper-packages"></a>Önyükleyici paketleri oluşturma
Kurulum programı, Windows Installer (*.msi*) dosyaları ve yürütülebilir programlar gibi yeniden dağıtılabilir bileşenleri algılamak ve yüklemek için yapılandırılabilen genel bir yükleyicidir. Yükleyici de bir bootstrapper olarak bilinir. Bileşenin yüklenmesini yönetmek için meta verileri belirten bir Dizi XML bildirimi aracılığıyla programlanır.  ClickOnce için **Önkoşullar** iletişim kutusunda görünen her yeniden dağıtılabilir bileşen veya ön koşul bir bootstrapper paketidir. Bootstrapper paketi, ön koşulun nasıl yüklenmesi gerektiğini açıklayan bildirim dosyaları içeren bir dizi dizin ve dosyadır.

Bootstrapper ilk herhangi bir önkoşul zaten yüklü olup olmadığını algılar. Ön koşullar yüklenmezse, önce bootstrapper lisans sözleşmelerini gösterir. İkinci olarak, son kullanıcı lisans sözleşmelerini kabul ettikten sonra, ön koşullar için yükleme başlar. Aksi takdirde, tüm ön koşullar tespit edilirse, bootstrapper sadece uygulama yükleyici başlar.

## <a name="create-custom-bootstrapper-packages"></a>Özel bootstrapper paketleri oluşturun
Visual Studio'daki XML Editor'u kullanarak bootstrapper manifestolarını oluşturabilirsiniz. Bootstrapper paketi oluşturma örneğini görmek için [Walkthrough: Özel bir bootstrapper gizlilik istemi oluşturun.](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)

Bootstrapper paketi oluşturmak için, bir ürün manifestosu ve bileşenin her yerelleştirilmiş sürümü için de bir paket manifestosu oluşturmanız gerekir.

* Ürün manifestosu, *product.xml,* paket için herhangi bir dil-nötr meta veri içerir. Bu, yeniden dağıtılabilir bileşenin tüm yerelleştirilmiş sürümlerinde ortak meta verileri içerir.  Bu dosyayı oluşturmak [için bkz.](../deployment/how-to-create-a-product-manifest.md)

* Paket manifestosu, *package.xml,* dile özgü meta veriler içerir; genellikle yerelleştirilmiş hata iletileri içerir. Bir bileşen, bu bileşenin her yerelleştirilmiş sürümü için en az bir paket bildirimine sahip olmalıdır. Bu dosyayı oluşturmak [için bkz.](../deployment/how-to-create-a-package-manifest.md)

Bu dosyalar oluşturulduktan sonra, ürün bildirimi dosyasını özel bootstrapper adlı bir klasöre koyun. Paket bildirimi dosyası, yerel bölge için adlı bir klasöre gider. Örneğin, paket bildirimi dosyası İngilizce yeniden dağıtım içinse, dosyayı en adlı bir klasöre koyun. Japonca için ja ve Almanca için de gibi her yerel bölge için bu işlemi yineleyin. Son özel bootstrapper paketi aşağıdaki klasör yapısına sahip olabilir.

```
CustomBootstrapperPackage
  product.xml
  CustomBootstrapper.msi
  de
    eula.rtf
    package.xml
  en
    eula.rtf
    package.xml
  ja
    eula.rtf
    package.xml
```

Ardından, yeniden dağıtılabilir dosyaları bootstrapper klasörü konumuna kopyalayın. Daha fazla bilgi için [bkz: Yerelleştirilmiş bootstrapper paketi oluşturun.](../deployment/how-to-create-a-localized-bootstrapper-package.md)

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

veya Visual Studio'nun eski sürümleri için

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

or

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

Ayrıca aşağıdaki kayıt defteri anahtarında **Path** değerinden bootstrapper klasörü konumunu bulabilirsiniz:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

64 bit sistemlerde aşağıdaki kayıt defteri anahtarını kullanın:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Yeniden dağıtılabilir her bileşen, paketler dizininin altında kendi alt klasöründe görünür. Ürün bildirimi ve yeniden dağıtılabilir dosyalar bu alt klasöre konulmalıdır. Bileşenin ve paket bildirimlerinin yerelleştirilmiş sürümleri Kültür Adına göre adlandırılan alt klasörlere konulmalıdır.

Bu dosyalar bootstrapper klasörüne kopyalandıktan sonra, bootstrapper paketi otomatik olarak Visual Studio **Prerequisites** iletişim kutusunda görünür. Özel bootstrapper paketiniz görünmüyorsa, **Önkoşullar** iletişim kutusunu kapatın ve yeniden açın. Daha fazla bilgi için [Önkoşullar iletişim kutusuna](../ide/reference/prerequisites-dialog-box.md)bakın.

Aşağıdaki tablo, bootstrapper tarafından otomatik olarak doldurulan özellikleri gösterir.

|Özellik|Açıklama|
|--------------|-----------------|
|ApplicationName|Uygulamanın adı.|
|ProcessorArchitecture|Yürütülebilir bir platform tarafından hedeflenen işlemci ve kelime başına bit. Değerler şunlardır:<br /><br /> - Intel<br />- IA64<br />- AMD64|
|[Sürüm9x](/windows/desktop/Msi/version9x)|Microsoft Windows 95, Windows 98 veya Windows ME işletim sistemleri için sürüm numarası. Sürümün sözdizimi Major.Minor.ServicePack'tir.|
|[SürümNT](/windows/desktop/Msi/versionnt)|Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 veya Windows 7 işletim sistemlerinin sürüm numarası. Sürümün sözdizimi Major.Minor.ServicePack'tir.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Yükleme sırasında çalışacak Windows Installer derlemesinin (msi.dll) sürümü.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Kullanıcının yönetici ayrıcalıkları varsa bu özellik ayarlanır. Değerler doğru veya yanlıştır.|
|Yükleme Modu|Yükleme modu, bileşenin nereden yüklenmesi gerektiğini gösterir. Değerler şunlardır:<br /><br /> - HomeSite - ön koşullar satıcının Web sitesinden yüklenir.<br />- SpecificSite - ön koşullar seçtiğiniz konumdan yüklenir.<br />- SameSite - ön koşullar uygulama ile aynı yerden yüklenir.|

## <a name="separate-redistributables-from-application-installations"></a>Uygulama yüklemelerinden ayrı yeniden dağıtılabilir
Yeniden dağıtılabilir dosyalarınızın Kurulum projelerinde dağıtılmasını engelleyebilirsiniz. Bunu yapmak için, .NET Framework dizininizdeki RedistList klasöründe yeniden dağıtılabilir bir liste oluşturun:

`%ProgramFiles%\Microsoft.NET\RedistList`

Yeniden dağıtılabilir liste, aşağıdaki biçimi kullanarak adlandırmanız gereken bir XML dosyasıdır: * \<Şirket Adı>.\< Bileşen Adı>. RedistList.xml*. Yani, örneğin, bileşen Acme tarafından yapılan DataWidgets denirse, *Acme.DataWidgets.RedistList.xml*kullanın. Yeniden dağıtılabilir listenin içeriğine bir örnek şuna benzeyebilir:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ClickOnce uygulamasıyla ön koşulları yükleyin](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md)
- [Ürün ve paket şeması referansı](../deployment/product-and-package-schema-reference.md)
- [Visual Studio 2005 bootstrapper'ı kullanarak kurulumunuzu başlatın](https://msdn.microsoft.com/magazine/cc163899.aspx)
