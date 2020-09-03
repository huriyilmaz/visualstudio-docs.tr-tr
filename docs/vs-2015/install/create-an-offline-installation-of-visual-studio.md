---
title: Çevrimdışı yükleme oluştur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a6a9707d517a8a43d9a9ca156a5f7291ecee9bee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81445072"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio’nun Çevrimdışı Yüklemesini Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. Visual [Studio 'nun çevrimdışı yüklemesini oluşturma](/visualstudio/install/create-an-offline-installation-of-visual-studio) veya [Visual Studio 'Nun ağ yüklemesi oluşturma](/visualstudio/install/create-a-network-installation-of-visual-studio).

Bu sayfada, Internet 'e bağlı değilseniz Visual Studio 2015 ' nin nasıl yükleneceği açıklanır. Ancak, "bağlantısı kesik" bir yükleme gerçekleştirmek için, önce Internet 'e bağlı bir makine kullanarak bir çevrimdışı yükleme düzeni oluşturmanız gerekir. Bunun nasıl yapılacağını aşağıda bulabilirsiniz.

> [!IMPORTANT]
> Çevrimdışı makineniz Windows 7 SP1 veya Windows Server 2008 R2 çalıştırıyorsa, lütfen bu konunun [çevrimdışı yüklemesinde sorun giderme](#BKMK_tshoot) bölümündeki özel yönergelere bakın.  Visual Studio 2015 ' i yüklemeden *önce* bu yönergeleri izlemeniz gerekir.

## <a name="installing-by-creating-an-offline-installation"></a><a name="BKMK_Offline"></a> Çevrimdışı yükleme oluşturarak yükleme

#### <a name="to-create-an-offline-installation-layout"></a>Çevrimdışı yükleme düzeni oluşturmak için

1. [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) Download sayfasından yüklemek Istediğiniz Visual Studio sürümünü seçin.

2. Yükleyiciyi dosya sisteminizdeki bir konuma indirdikten sonra, " \<executable name> /layout" komutunu çalıştırın.

     Örneğin şunu çalıştırın: `vs_enterprise.exe /layout D:\VisualStudio2015`

     `/layout`Anahtarı kullanarak, yalnızca indirme makinesi için uygun olanları değil, neredeyse tüm yükleme paketlerini indirebilirsiniz. Bu yaklaşım, bu yükleyiciyi her yerde çalıştırmak için ihtiyacınız olan dosyaları sağlar ve başlangıçta yüklenmemiş bileşenleri yüklemek istiyorsanız yararlı olabilir.

3. Bu komutu çalıştırdıktan sonra, çevrimdışı yükleme düzeninin bulunmasını istediğiniz klasörü değiştirmenize olanak sağlayan bir iletişim kutusu görüntülenir.   Sonra **İndir** düğmesine tıklayın.

     Paket indirmesi başarılı olduğunda, kurulumun başarılı olduğunu belirten bir ileti görmeniz gerekir **! Belirtilen tüm bileşenler başarıyla alındı.**

4. Daha önce belirttiğiniz klasörü bulun. (Örneğin, D:\VisualStudio2015. bulun) Bu klasör, paylaşılan bir konuma kopyalamak veya medya yüklemek için gereken her şeyi içerir.

    > [!CAUTION]
    > Şu anda Android SDK çevrimdışı yükleme deneyimini desteklemez. Android SDK Kurulum öğelerini Internet 'e bağlı olmayan bir bilgisayara yüklerseniz, yükleme başarısız olabilir. Daha fazla bilgi için, bu konudaki "çevrimdışı yüklemede sorun giderme" bölümüne bakın.

5. Yüklemeyi dosya konumundan veya yükleme medyasından çalıştırın.

## <a name="updating-an-offline-installation"></a>Çevrimdışı yükleme güncelleştiriliyor
 Microsoft, Visual Studio 2015 için birkaç güncelleştirme yayımlamıştır. Visual Studio yüklemenizi güncelleştirmek için,  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) indirme sayfasından istediğiniz sürümü yüklemeniz yeterlidir. Ardından, bu konuda açıklanan adımları izleyerek yeni bir çevrimdışı yükleme düzeni oluşturun ve ardından Visual Studio 2015 kopyanızı güncelleştirmek için kullanın.

## <a name="troubleshooting-an-offline-installation"></a><a name="BKMK_tshoot"></a> Çevrimdışı yükleme sorunlarını giderme
 Çevrimdışı Install önbelleğinizi çevrimdışı yüklediğinizde, bazı bileşen ve paketleri yükleyemeyecek hakkında uyarı iletileri görebilirsiniz. Aşağıdaki tablo, bu senaryolar için olası çözümleri içerir.

| Bileşen veya paket | Çözüm |
|-|-|
| Dotfuscator ve Analytics Community Edition 5.19.1 ( **Windows 7 SP1** ve **Windows Server 2008 R2**'de yüklü olarak Visual Studio 'nun Community, Professional ve Enterprise sürümleri için) | Çevrimdışı makineniz **Windows 7 SP1** veya **Windows Server 2008 R2**çalıştırıyorsa, Visual Studio 2015 ' yi yüklemeden önce aşağıdaki adımları gerçekleştirmeniz gerekir:<br /><br /> 1. CTL dosyalarını indirmek için bir dosya veya Web sunucusu yapılandırın.<br /><br /> 2. bağlantısı kesilmiş bir ortam için Microsoft otomatik güncelleştirme URL 'sini yeniden yönlendirin.<br /><br /> Daha fazla bilgi için Microsoft TechNet sitesindeki [Güvenilen kökleri ve Izin verilmeyen sertifikaları yapılandırma](https://technet.microsoft.com/library/dn265983.aspx) sayfasına bakın. |
| Android SDK kurulumu (API düzeyi) | Android SDK (API düzeyi) paketlerini yüklemek için bir internet bağlantınızın olması gerekir. Kısıtlı bir ağ kullanıyorsanız, Visual Studio 'Yu yüklerken aşağıdaki URL 'Lere erişime izin vermeniz gerekir:<br /><br /> -   `https://dl.google.com:443`<br />-   `https://dl-ssl.google.com:443`<br />-   `https://dl-ssl.google.com/android/repository/*`<br /> <br />Proxy ayarlarıyla ilgili olası sorunları çözme hakkında daha fazla bilgi için, proxy blog gönderisinin [arkasındaki Visual Studio 2015 yükleme hataları (Android SDK Kurulum)](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) bölümüne bakın. |
| Visual Studio genişletilebilirlik öğe şablonları<br /><br /> Visual Studio için GitHub Uzantısı<br /><br /> Visual Studio için PowerShell Araçları | Visual Studio 2015 ' i yüklerken Internet bağlantınız yoksa çevrimdışı yükleme düzeni oluşturmak için özel bir çevrimdışı akış kullanabilirsiniz. **Note:**  Bu özel akış, Visual Studio 2015 için en son güncelleştirmeleri içerir. <br /><br /> Özel çevrimdışı akış oluşturmak için şu komutu çalıştırın:/Layout *Drive:* \VisualStudio2015/overdefeeduri *URL-to-Feed-XML*<br /><br /> Örneğin, Visual Studio 2015 Enterprise 'ın Ingilizce dildeki özel bir çevrimiçi akışı için şunu çalıştırın:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Seçtiğiniz dilde özel bir çevrimdışı akış oluşturmak için kullanabileceğiniz URL 'lerin tüm listesi için aşağıdaki tabloya bakın. |

 Yukarıdaki tabloda açıklandığı gibi dile özgü özel bir akış oluşturmak için aşağıdaki URL 'Leri kullanın.

|       Dil        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| Basitleştirilmiş Çince  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Geleneksel Çince | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Çekçe         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Almanca         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        İngilizce        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        İspanyolca        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Fransızca         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        İtalyanca        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japonca        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Korece         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Lehçe         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portekizce       | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Rusça        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Türkçe        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio'yu yükleme](install-visual-studio-2015.md)