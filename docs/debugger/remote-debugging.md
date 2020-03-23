---
title: Uzaktan hata ayıklama | Microsoft Dokümanlar
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302079"
---
# <a name="remote-debugging"></a>Uzaktan Hata Ayıklama
Farklı bir bilgisayarda dağıtılan bir Visual Studio uygulamasını hata ayıklayabilirsiniz. Bunu yapmak için Visual Studio uzaktan hata ayıklama sını kullanırsınız.

Uzaktan hata ayıklama yla ilgili ayrıntılı talimatlar için bu konulara bakın.

|Senaryo|Bağlantı|
|-|-|-|
|Azure App Service|[Azure'da Anlık Görüntü Hata Ayıklama](../debugger/debug-live-azure-applications.md) veya [Uzaktan Hata Ayıklama ASP.NET](../debugger/remote-debugging-azure.md)|
|Azure VM|[Azure’da ASP.NET hatalarını uzaktan ayıklama](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Azure Hizmet Kumaşı uygulamasını hata ayıklama](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Uzak hata ayıklama ASP.NET Çekirdek](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) veya [Uzaktan Hata Ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# veya Visual Basic|[Uzaktan C# veya Visual Basic projesi hatası ayıklama](../debugger/remote-debugging-csharp.md)|
|C++|[Uzaktan hata ayıklama c++ projesi](../debugger/remote-debugging-cpp.md)|
|Evrensel Windows Uygulamaları (UWP)|[UWP uygulamalarını uzak bir makinede çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md) veya [yüklü bir uygulama paketini hata ayıklama](../debugger/debug-installed-app-package.md)|

Uzaktan hata ayıklamayı indirmek ve yüklemek istiyorsanız ve senaryonuz için ek talimatlara ihtiyacınız yoksa, bu makaledeki adımları izleyin.

## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirin ve yükleyin

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a>Gereksinim -leri

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a>(İsteğe bağlı) Dosya paylaşımından uzak hata ayıklamaçalıştırmak için

Uzaktan hata ayıklayıcıyı *(msvsmon.exe)* Visual Studio Community, Professional veya Enterprise yüklü bir bilgisayarda bulabilirsiniz. Bazı senaryolarda uzaktan hata ayıklama ayarlamanın en kolay yolu, uzak hata ayıklamayı (msvsmon.exe) dosya paylaşımından çalıştırmaktır. Kullanım sınırlamaları için, uzaktan hata ayıklama nın Yardım sayfasına bakın (Uzaktan hata ayıklamada **> Kullanımına Yardımcı olun).**

1. Visual Studio sürümünüzle eşleşen dizinde *msvsmon.exe'yi* bulun:

   ::: moniker range=">=vs-2019"

   *Program Dosyaları (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Dosyaları (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Dosyaları (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Dosyaları (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Uzak **Hata Ayıklama** klasörünü Visual Studio bilgisayarında paylaşın.

3. Uzak bilgisayarda, paylaşılan klasörden *msvsmon.exe* çalıştırın. Kurulum [yönergelerini](#bkmk_setup)izleyin.

> [!TIP]
> Komut satırı yükleme ve komut satırı başvurusu için, Visual Studio yüklü ``msvsmon.exe /?`` bilgisayardaki komut satırına yazarak *msvsmon.exe* için Yardım sayfasına bakın (veya uzaktan hata ayıklayıcıda **> Kullanımına Yardım'a** gidin).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Uzaktan hata ayıklamayı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a>Uzak hata ayıklamayı yapılandırma
Uzaktan hata ayıklamanın yapılandırmasının bazı yönlerini ilk kez başlattıktan sonra değiştirebilirsiniz.

- Diğer kullanıcıların uzak hata ayıklayıcıya bağlanması için izin eklemeniz gerekiyorsa, **Araçlar > İzinleri'ni**seçin. İzinleri vermek veya reddetmek için yönetici ayrıcalıklarınızın olması gerekir.

     > [!IMPORTANT]
     > Uzak hata ayıklamayı Visual Studio bilgisayarında kullandığınız kullanıcı hesabından farklı bir kullanıcı hesabı altında çalıştırabilirsiniz, ancak uzaktan hata ayıklama izinlerine farklı kullanıcı hesabı eklemeniz gerekir.

     Alternatif olarak, komut satırından **/allow \<kullanıcı adı>** parametresi ile uzaktan hata ayıklama başlatabilirsiniz: **msvsmon \< username@computer /allow>**.

- Kimlik Doğrulama modunu veya bağlantı noktası numarasını değiştirmeniz veya uzak araçlar için bir zaman ekme değeri belirtmeniz gerekiyorsa: **Araçlar > Seçenekleri'ni**seçin.

     Varsayılan olarak kullanılan bağlantı noktası numaralarının listesi için, [Uzaktan Hata Ayıklama Bağlantı Noktası Atamaları'na](../debugger/remote-debugger-port-assignments.md)bakın.

     > [!WARNING]
     > Uzak araçları Kimlik Doğrulaması Yok modunda çalıştırmayı seçebilirsiniz, fakat bu mod kesinlikle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Yalnızca ağın kötü amaçlı veya düşmanca trafik riski altında olmadığından eminseniz Kimlik Doğrulama Yok modunu seçin.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a>(İsteğe bağlı) Uzaktan hata ayıklamayı hizmet olarak yapılandırma
ASP.NET ve diğer sunucu ortamlarında hata ayıklama için uzaktan hata ayıklayıcıyı Yönetici olarak çalıştırmanız veya her zaman çalışmasını istiyorsanız, uzaktan hata ayıklayıcıyı hizmet olarak çalıştırmanız gerekir.

 Uzak hata ayıklamayı bir hizmet olarak yapılandırmak istiyorsanız, aşağıdaki adımları izleyin.

1. Uzaktan **Hata Ayıklama Yapılandırma Sihirbazı** (rdbgwiz.exe) bulun. (Bu Uzak Hata Ayıklama ayrı bir uygulamadır.) Yalnızca uzak araçları yüklediğinizde kullanılabilir. Visual Studio yüklü değildir.

2. Yapılandırma sihirbazını çalıştırmaya başlayın. İlk sayfa geldiğinde **İleri'yi**tıklatın.

3. Hizmet onay kutusu **olarak Visual Studio 2015 Uzaktan Hata Ayıklama'yı çalıştır'ı** kontrol edin.

4. Kullanıcı hesabının ve parolanın adını ekleyin.

    **Giriş'i bu** hesaba hizmet kullanıcısı olarak eklemeniz gerekebilir **(Başlangıç** sayfasında veya penceresinde **Yerel Güvenlik Politikası** Bul (secpol.msc) (veya komut isteminde **secpol** yazın). Pencere göründüğünde, Kullanıcı Hakları **Ataması'nı**çift tıklatın, ardından **Oturum Aç'ı** sağ bölmede bir hizmet olarak bulun. Çift tıkla. **Özellikler** penceresine kullanıcı hesabı ekleyin ve **Tamam'ı**tıklatın). **İleri**'ye tıklayın.

5. Uzak araçların iletişim kurmasını istediğiniz ağ türünü seçin. En az bir ağ türü seçilmelidir. Bilgisayarlar bir etki alanı üzerinden bağlıysa, ilk öğeyi seçmeniz gerekir. Bilgisayarlar bir çalışma grubu veya ev grubu üzerinden bağlıysa, ikinci veya üçüncü öğeleri seçmeniz gerekir. **İleri**'ye tıklayın.

6. Hizmet başlatılabilirse, Visual **Studio Uzaktan Hata Ayıklama Yapılandırma Sihirbazı'nı başarıyla tamamladığınızı**göreceksiniz. Hizmet başlatılamazsa, Visual **Studio Uzaktan Hata Ayıklama Yapılandırma Sihirbazı'nı tamamlayamadı**göreceksiniz. Sayfa da başlatmak için hizmet almak için takip etmek için bazı ipuçları verir.

7. **Son**'a tıklayın.

   Bu noktada uzaktan hata ayıklama bir hizmet olarak çalışıyor. Bunu **Kontrol Paneli > Hizmetleri'ne** giderek ve Visual Studio **2015 Remote Debugger'ı**arayarak doğrulayabilirsiniz.

   **Denetim Masası > Hizmetleri'nden**uzaktan hata ayıklama hizmetini durdurup başlatabilirsiniz.

## <a name="set-up-debugging-with-remote-symbols"></a>Uzak sembollerle hata ayıklama ayarlama

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Uzaktan Hata Ayıklama için Windows Güvenlik Duvarını Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzaktan IIS Bilgisayarda ASP.NET Çekirdeğini Uzaktan Algılama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)