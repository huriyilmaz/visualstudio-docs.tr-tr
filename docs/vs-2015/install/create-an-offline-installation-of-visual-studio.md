---
title: Çevrimdışı Yükleme Oluşturma | Microsoft Dokümanlar
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
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445072"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio’nun Çevrimdışı Yüklemesini Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son dokümantasyon için Visual [Studio'nun çevrimdışı yüklemesini oluştur](/visualstudio/install/create-an-offline-installation-of-visual-studio) veya [Visual Studio'nun ağ yüklemesini oluşturun](/visualstudio/install/create-a-network-installation-of-visual-studio)bölümüne bakın.

Bu sayfa, Internet'e bağlı değilken Visual Studio 2015'in nasıl yüklenirolduğunu açıklar. Ancak, "bağlantısı kesilmiş" bir yükleme gerçekleştirmek için, önce Internet'e bağlı bir makine kullanarak çevrimdışı yükleme düzeni oluşturmanız gerekir. Bunu şu şekilde yapabilirsiniz.

> [!IMPORTANT]
> Çevrimdışı makineniz Windows 7 SP1 veya Windows Server 2008 R2 çalıştırıyorsa, lütfen sorun [giderme](#BKMK_tshoot) bölümündeki özel yönergeleri görün.  Visual Studio 2015'i yüklemeden *önce* bu yönergeleri izlemeniz gerekir.

## <a name="installing-by-creating-an-offline-installation"></a><a name="BKMK_Offline"></a>Çevrimdışı yükleme oluşturarak yükleme

#### <a name="to-create-an-offline-installation-layout"></a>Çevrimdışı yükleme düzeni oluşturmak için

1. [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) indirme sayfasından yüklemek istediğiniz Visual Studio sürümünü seçin.

2. Yükleyiciyi dosya sisteminizdeki bir konuma indirdikten\<sonra " çalıştırılabilir ad> /düzen" çalıştırın.

     Örneğin, çalıştırın:`vs_enterprise.exe /layout D:\VisualStudio2015`

     `/layout` Anahtarı kullanarak, yalnızca indirme makinesine uygulananları değil, hemen hemen tüm yükleme paketlerini indirebilirsiniz. Bu yaklaşım, bu yükleyiciyi her yerde çalıştırmak için gereken dosyaları verir ve başlangıçta yüklenmemiş bileşenleri yüklemek istiyorsanız yararlı olabilir.

3. Bu komutu çalıştırdıktan sonra, çevrimdışı yükleme düzeninin bulunduğu klasörü değiştirmenize olanak tanıyan bir iletişim kutusu görüntülenir.   Ardından **İndir** düğmesini tıklatın.

     Paket indirme başarılı olduğunda, Kurulum Başarılı yazan bir ileti görmeniz **gerekir! Belirtilen tüm bileşenler başarıyla elde edilmiştir.**

4. Daha önce belirttiğiniz klasörü bulun. (Örneğin, D:\VisualStudio2015'i bulun.) Bu klasör, paylaşılan bir konuma kopyalamak veya ortam yüklemek için gereken her şeyi içerir.

    > [!CAUTION]
    > Şu anda, Android SDK çevrimdışı yükleme deneyimini desteklemiyor. Android SDK Kurulum öğelerini internete bağlı olmayan bir bilgisayara yüklerseniz, yükleme başarısız olabilir. Daha fazla bilgi için bu konudaki "Çevrimdışı yükleme sorunu" bölümüne bakın.

5. Yüklemeyi dosya konumundan veya yükleme medyasından çalıştırın.

## <a name="updating-an-offline-installation"></a>Çevrimdışı yüklemeyi güncelleştirme
 Microsoft, Visual Studio 2015 için çeşitli Güncelleştirmeler yayımladı. Visual Studio yüklemenizi güncellemek için [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) indirme sayfasından istediğiniz sürümü indirmeniz yeterlidir. Ardından, yeni bir çevrimdışı yükleme düzeni oluşturmak için bu konuda özetlenen adımları izleyin ve ardından Visual Studio 2015 kopyanızı güncelleştirmek için kullanın.

## <a name="troubleshooting-an-offline-installation"></a><a name="BKMK_tshoot"></a>Çevrimdışı yüklemede sorun giderme
 Çevrimdışı yükleme önbelleğinizden çevrimdışı yüklediğinizde, bazı bileşenleri ve paketleri yükleyememe konusunda uyarı iletileri görebilirsiniz. Aşağıdaki tablo, bu senaryolar için olası çözümleri içerir.

| Bileşen veya Paket | Çözüm |
|-|-|
| Dotfuscator ve Analytics Community Edition 5.19.1 (Visual Studio'nun Topluluk, Profesyonel ve Kurumsal sürümleri için **Windows 7 SP1** ve **Windows Server 2008 R2'de**yüklenmiştir) | Çevrimdışı makineniz Windows **7 SP1** veya **Windows Server 2008 R2**çalıştırıyorsa, Visual Studio 2015'i yüklemeden önce aşağıdaki adımları gerçekleştirmeniz gerekir:<br /><br /> 1. CTL dosyalarını indirmek için bir dosyayı veya web sunucusunu yapılandırın.<br /><br /> 2. Bağlantısı kesilen bir ortam için Microsoft Otomatik Güncelleştirme URL'sini yeniden yönlendirin.<br /><br /> Daha fazla bilgi için, Microsoft TechNet sitesindeki [Güvenilir Kökleri ve İzin Verilmeyen Sertifikaları Yapılandırıyorum](https://technet.microsoft.com/library/dn265983.aspx) sayfasına bakın. |
| Android SDK Kurulumu (API Seviyesi) | Android SDK (API Düzeyi) paketlerini yüklemek için internet bağlantınız olmalıdır. Kısıtlı bir ağdaysanız, Visual Studio'yu yüklediğinizde aşağıdaki URL'lere erişmenize izin vermelisiniz:<br /><br /> -   `https://dl.google.com:443`<br />-   `https://dl-ssl.google.com:443`<br />-   `https://dl-ssl.google.com/android/repository/*`<br /> <br />Proxy ayarlarıyla ilgili olası sorunları nasıl çözeceğiniz hakkında daha fazla bilgi için, Proxy blog gönderisinin [arkasındaki Visual Studio 2015 yükleme hatalarına (Android SDK Kurulumu)](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) bakın. |
| Visual Studio Genişletilebilirlik Öğe Şablonları<br /><br /> Visual Studio için GitHub Uzantısı<br /><br /> Visual Studio için PowerShell Araçları | Visual Studio 2015'i yüklediğinizde internet bağlantınız yoksa, çevrimdışı yükleme düzenini oluşturmak için özel bir çevrimdışı akış kullanabilirsiniz. **Not:**  Bu özel özet akışı, Visual Studio 2015'in en son Güncellemelerini içerir. <br /><br /> Özel çevrimdışı akışı oluşturmak için aşağıdaki komutu çalıştırın: /layout *Drive:* \VisualStudio2015 /overridefeeduri *URL-to-feed-xml*<br /><br /> Örneğin, Visual Studio 2015 Enterprise'ın İngilizce özel çevrimdışı yayını için çalıştırın:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Seçtiğiniz dilde özel bir çevrimdışı özet akışı oluşturmak için kullanabileceğiniz URL'lerin tam listesi için aşağıdaki tabloya bakın. |

 Yukarıdaki tabloda açıklandığı gibi, dile özel çevrimdışı akış oluşturmak için aşağıdaki URL'leri kullanın.

|       Dil        |                            URL'si                            |
|-----------------------|-----------------------------------------------------------|
| Çince (Basitleştirilmiş)  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| seçenekleri yerine | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Çekçe         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Almanca         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Türkçe        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
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