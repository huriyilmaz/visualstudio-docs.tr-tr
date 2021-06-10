---
title: Önyükleyici paketleri oluşturma
description: Kurulum programı ve ClickOnce bileşenlerinin yüklemesini yönetmek için meta verileri belirten XML bildirimlerini kullanma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 007a7f42448ab8026d8acdc262ce5e0dcdd99b28
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877734"
---
# <a name="create-bootstrapper-packages"></a>Önyükleyici paketleri oluşturma
Kurulum programı, Windows Installer (.msi) dosyaları ve yürütülebilir programlar gibi yeniden dağıtılabilir bileşenleri algılamak ve yüklemek *için yapılandırılan* genel bir yükleyicidir. Yükleyici, önyükleyici olarak da bilinir. Bileşenin yüklemesini yönetmek için meta verileri belirten xml bildirimleri kümesi aracılığıyla programlanır.  ClickOnce için Önkoşullar iletişim kutusunda  görünen her yeniden dağıtılabilir bileşen veya önkoşul bir önkoşuldur. Önyükleyici paketi, önkoşulların nasıl yük olacağını açıklayan bildirim dosyalarını içeren bir dizin ve dosya grubudur.

Önyükleyici önce önkoşullardan herhangi biri zaten yüklü olup olmadığını algılar. Önkoşullar yüklenmezse, önce önyükleyici lisans sözleşmelerini gösterir. İkinci olarak, son kullanıcı lisans sözleşmelerini kabul ettikten sonra yükleme önkoşullar için başlar. Aksi takdirde, tüm önkoşullar algılanırsa önyükleyici yalnızca uygulama yükleyicisini başlatır.

## <a name="create-custom-bootstrapper-packages"></a>Özel önyükleyici paketleri oluşturma
Xml Düzenleyicisi'ni kullanarak önyükleyici bildirimlerini Visual Studio. Önyükleyici paketi oluşturma örneğini görmek için bkz. Adım [adım: Gizlilik istemiyle özel önyükleyici oluşturma.](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)

Önyükleyici paketi oluşturmak için bir ürün bildirimi ve bir bileşenin yerelleştirilmiş her sürümü için de bir paket bildirimi oluşturmanız gerekir.

* ürün bildirimi *(product.xml,* paketin dil bağımsız meta verilerini içerir. Bu, yeniden dağıtılabilir bileşenin tüm yerelleştirilmiş sürümleri için ortak meta verileri içerir.  Bu dosyayı oluşturmak için [bkz. Nasıl: Ürün Bildirimi Oluşturma.](../deployment/how-to-create-a-product-manifest.md)

* paket bildirimi *(package.xml,* dile özgü meta veriler içerir; Genellikle yerelleştirilmiş hata iletileri içerir. Bir bileşenin her yerelleştirilmiş sürümü için en az bir paket bildirimine sahip olması gerekir. Bu dosyayı oluşturmak için [bkz. Nasıl: Paket Bildirimi Oluşturma.](../deployment/how-to-create-a-package-manifest.md)

Bu dosyalar oluşturulduktan sonra ürün bildirim dosyasını özel önyükleyici için adlı bir klasöre alın. Paket bildirim dosyası, yerel olarak adlandırılmış bir klasöre gider. Örneğin, paket bildirim dosyası İngilizce yeniden dağıtım içinse dosyayı en adlı bir klasöre koyabilirsiniz. Bu işlemi japonca için ja, Almanca için de gibi her yerel seçim için tekrarlayın. Son özel önyükleyici paketi aşağıdaki klasör yapısına sahip olabilir.

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

Ardından, yeniden dağıtılabilir dosyaları önyükleyici klasörü konuma kopyalayın. Daha fazla bilgi için, [bkz. How to: Create a localized bootstrapper package](../deployment/how-to-create-a-localized-bootstrapper-package.md).

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages*
```

veya

```
*<VS Install Path>\MSBuild\Microsoft\VisualStudio\BootstrapperPackages*
```

>[!NOTE]
>Yükleme yolu'Visual Studio yukarıda listelenen yol, Visual Studio 2019 Güncelleştirme 7 sürümüyle başlayarak çalışır.

Önyükleyici klasörünün konumunu aşağıdaki kayıt defteri **anahtarında Yol** değerinden de bulabilirsiniz:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

64 bit sistemlerde aşağıdaki kayıt defteri anahtarını kullanın:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Yeniden dağıtılabilir her bileşen, packages dizini altındaki kendi alt klasörlerinde görünür. Ürün bildirimi ve yeniden dağıtılabilir dosyalar bu alt klasöre alınarak girilebilir. Bileşen ve paket bildirimlerinin yerelleştirilmiş sürümleri Kültür Adı'nın altında yer alan alt klasörlere konmalı.

Bu dosyalar önyükleyici klasörüne kopyalandıktan sonra önyükleyici paketi önkoşullar iletişim Visual Studio **otomatik olarak** görünür. Özel önyükleyici paketiniz görünmüyorsa Önkoşullar iletişim **kutusunu kapatın ve yeniden** açın. Daha fazla bilgi için [bkz. Önkoşullar iletişim kutusu.](../ide/reference/prerequisites-dialog-box.md)

Aşağıdaki tablo, önyükleyici tarafından otomatik olarak doldurulan özellikleri gösterir.

|Özellik|Açıklama|
|--------------|-----------------|
|ApplicationName|Uygulamanın adı.|
|ProcessorArchitecture|Bir yürütülebilir dosya tarafından hedeflenen platformun işlemci ve bit/sözcük sayısı. Değerler aşağıdakileri içerir:<br /><br /> - Intel<br />- IA64<br />- AMD64|
|[Sürüm9x](/windows/desktop/Msi/version9x)|Microsoft Windows 95, Windows 98 veya Windows ME işletim sistemlerinin sürüm numarası. Sürümün söz dizimi Major.Minor.ServicePack'tir.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 veya Windows 7 işletim sistemlerinin sürüm numarası. Sürümün söz dizimi Major.Minor.ServicePack'tir.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Yükleme sırasında Windows Installer derlemenin (msi.dll) sürümü.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Kullanıcının yönetici ayrıcalıkları varsa bu özellik ayarlanır. Değerler true veya false olur.|
|InstallMode|Yükleme modu, bileşenin nereden yüklenmesi gerektiğini belirtir. Değerler aşağıdakileri içerir:<br /><br /> - HomeSite - önkoşullar satıcının Web sitesinden yüklenir.<br />- SpecificSite - önkoşullar, seçerek yüklenir.<br />- SameSite - önkoşullar uygulamayla aynı konumdan yüklenir.|

## <a name="separate-redistributables-from-application-installations"></a>Yeniden dağıtılabilirleri uygulama yüklemelerinden ayırma
Yeniden dağıtılabilir dosyalarınızın Kurulum projelerinde dağıtılmasını önleyebilirsiniz. Bunu yapmak için, .NET Framework dizininizin RedistList klasöründe yeniden dağıtılabilir bir liste oluşturun:

`%ProgramFiles%\Microsoft.NET\RedistList`

Yeniden dağıtılabilir listesi, şu biçimi kullanarak ad ve soyadınız olan bir XML *\<Company Name> dosyasıdır: . \<Component Name>.RedistList.xml.* Bu nedenle, örneğin, bileşenin Adı Acme tarafından yapılan DataWidgets ise, *Acme.DataWidgets.RedistList.xml.* Yeniden dağıtılabilir listenin içeriği aşağıdakine benzer olabilir:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kurulur: ClickOnce uygulamasıyla önkoşulları yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md)
- [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)
- [Yüklemenizi başlatmak Visual Studio için Visual Studio 2005 önyükleyicisini kullanın](/archive/msdn-magazine/2004/october/visual-studio-2005-bootstrapper-start-kick-your-installation)
