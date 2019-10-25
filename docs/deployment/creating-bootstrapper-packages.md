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
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806938"
---
# <a name="create-bootstrapper-packages"></a>Önyükleyici paketleri oluşturma
Kurulum programı, Windows Installer ( *. msi*) dosyaları ve yürütülebilir programlar gibi yeniden dağıtılabilir bileşenleri tespit etmek ve yüklemek için yapılandırılabilecek genel bir yükleyicidir. Yükleyici, önyükleyici olarak da bilinir. Bileşenin yüklenmesini yönetmek için meta verileri belirten bir XML bildirimleri kümesi aracılığıyla programlanır.  ClickOnce için **Önkoşullar** iletişim kutusunda görünen her yeniden dağıtılabilir bileşen veya önkoşul, bir önyükleyici paketidir. Önyükleyici paketi, önkoşulun nasıl yükleneceğini tanımlayan bildirim dosyalarını içeren bir dizin ve dosya grubudur.

Önyükleyici önce önkoşullardan birinin zaten yüklü olup olmadığını algılar. Önkoşullar yüklü değilse, ilk olarak önyükleyici lisans sözleşmelerini gösterir. İkincisi, son kullanıcı lisans sözleşmelerini kabul ettikten sonra, yükleme önkoşulları için başlar. Aksi takdirde, önkoşullardan bazıları algılanırsa önyükleyici yalnızca uygulama yükleyicisini başlatır.

## <a name="create-custom-bootstrapper-packages"></a>Özel önyükleyici paketleri oluşturma
Önyükleyici bildirimlerini Visual Studio 'daki XML düzenleyicisini kullanarak oluşturabilirsiniz. Önyükleyici paketi oluşturma örneği hakkında bir örnek görmek için bkz. [Izlenecek yol: Gizlilik istemiyle özel önyükleyici oluşturma](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).

Bir önyükleyici paketi oluşturmak için bir ürün bildirimi ve bir bileşenin yerelleştirilmiş her sürümü için bir paket bildirimi oluşturmanız gerekir.

* Ürün bildirimi, *Product. xml*, paket için dilden bağımsız meta veriler içerir. Bu, yeniden dağıtılabilir bileşenin tüm yerelleştirilmiş sürümlerinde ortak olan meta verileri içerir.  Bu dosyayı oluşturmak için bkz. [nasıl yapılır: Ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md).

* Package *. xml*paket bildirimi dile özgü meta veriler içerir; genellikle yerelleştirilmiş hata iletileri içerir. Bir bileşen, bu bileşenin yerelleştirilmiş her sürümü için en az bir paket bildirimine sahip olmalıdır. Bu dosyayı oluşturmak için bkz. [nasıl yapılır: paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md).

Bu dosyalar oluşturulduktan sonra, ürün bildirim dosyasını özel önyükleyici için adlı bir klasöre koyun. Paket bildirim dosyası, yerel ayar için adlı bir klasöre gider. Örneğin, Paket bildirim dosyası Ingilizce yeniden dağıtım için ise, dosyayı en-adlı bir klasöre koyun. Bu işlemi her yerel ayar için (Japonca için ja ve Almanca için de) yineleyin. Son özel önyükleyici paketi aşağıdaki klasör yapısına sahip olabilir.

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

Sonra, yeniden dağıtılabilir dosyaları önyükleyici klasörü konumuna kopyalayın. Daha fazla bilgi için bkz. [nasıl yapılır: yerelleştirilmiş önyükleyici paketi oluşturma](../deployment/how-to-create-a-localized-bootstrapper-package.md).

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

veya, Visual Studio 'nun eski sürümleri için

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

veya

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

Ayrıca, aşağıdaki kayıt defteri anahtarındaki **yol** değerinden önyükleyici klasörü konumunu bulabilirsiniz:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

64 bit sistemlerde aşağıdaki kayıt defteri anahtarını kullanın:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Her yeniden dağıtılabilir bileşen, paketler dizini altındaki kendi alt klasöründe görünür. Ürün bildirimi ve yeniden dağıtılabilir dosyalar bu alt klasöre koymalıdır. Bileşen ve paket bildirimlerinin yerelleştirilmiş sürümleri, kültür adına göre adlı alt klasörlere yerleştirilmelidir.

Bu dosyalar önyükleyici klasörüne kopyalandıktan sonra, önyükleyici paketi otomatik olarak Visual Studio **önkoşulları** iletişim kutusunda görünür. Özel önyükleyici paketiniz görünmezse, **Önkoşullar** iletişim kutusunu kapatın ve yeniden açın. Daha fazla bilgi için bkz. [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).

Aşağıdaki tabloda, önyükleyici tarafından otomatik olarak doldurulan özellikler gösterilmektedir.

|Özellik|Açıklama|
|--------------|-----------------|
|ApplicationName|Uygulamanın adı.|
|ProcessorArchitecture|Bir yürütülebilir dosya tarafından hedeflenen platformun işlemci ve sözcük başına bit sayısı. Değerler şunlardır:<br /><br /> -Intel<br />-IA64<br />-AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Microsoft Windows 95, Windows 98 veya Windows ME işletim sistemleri için sürüm numarası. Sürümün sözdizimi, birincil. Minor. hizmetpaketi.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 ya da Windows 7 işletim sistemleri için sürüm numarası. Sürümün sözdizimi, birincil. Minor. hizmetpaketi.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Yükleme sırasında çalıştırılacak Windows Installer derlemesinin (msi. dll) sürümü.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Kullanıcının yönetici ayrıcalıkları varsa, bu özellik ayarlanır. Değerler true veya false şeklindedir.|
|InstallMode|Yükleme modu, bileşenin nereden yüklenmesi gerektiğini gösterir. Değerler şunlardır:<br /><br /> -HomeSite-Önkoşullar, satıcının Web sitesinden yüklenir.<br />-SpecificSite-Önkoşullar seçtiğiniz konumdan yüklenir.<br />-SameSite-Önkoşullar uygulamayla aynı konumdan yüklenir.|

## <a name="separate-redistributables-from-application-installations"></a>Uygulama yüklemelerinden yeniden dağıtılabilir ayır
Yeniden dağıtılabilir dosyaların Kurulum projelerinde dağıtılmasını engelleyebilirsiniz. Bunu yapmak için .NET Framework dizininizdeki RedistList klasöründe yeniden dağıtılabilir bir liste oluşturun:

`%ProgramFiles%\Microsoft.NET\RedistList`

Yeniden dağıtılabilir liste, şu biçimi kullanarak ad almanız gereken bir XML dosyasıdır: *\<şirket adı >.\<bileşen adı >. RedistList. xml*. Bu nedenle, örneğin, bileşen Acme tarafından yapılan veri öğeleri olarak çağrılırsa, *Acme. Datapencere öğeleri. RedistList. xml*kullanın. Yeniden dağıtılabilir listenin içeriğine bir örnek şuna benzeyebilir:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: ClickOnce uygulamasıyla önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md)
- [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)
- [Yüklemeyi başlatmak için Visual Studio 2005 önyükleyici kullanın](https://msdn.microsoft.com/magazine/cc163899.aspx)
