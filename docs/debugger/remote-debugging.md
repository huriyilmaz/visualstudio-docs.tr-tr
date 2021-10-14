---
title: Uzaktan hata ayıklama | Microsoft Docs
description: Uzak hata Visual Studio kullanarak farklı bir bilgisayara dağıtılmış bir uygulamanın Visual Studio ayıkla.
ms.custom:
- remotedebugging
- SEO-VS-2020
ms.date: 09/10/2021
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ddae69c5261b63ef0e62fded1f94de448f82b984
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972394"
---
# <a name="remote-debugging"></a>Uzaktan Hata Ayıklama
Farklı bir bilgisayarda Visual Studio bir uygulamanın hata ayıklaması. Bunu yapmak için uzak hata ayıklayıcısını Visual Studio kullanın.

Uzaktan hata ayıklama hakkında ayrıntılı yönergeler için bu konulara bakın.

|Senaryo|Bağlantı|
|-|-|-|
|Azure App Service|[Azure'ASP.NET uzaktan hata](../debugger/remote-debugging-azure.md) ayıklama veya Visual Studio Enterprise [için](../debugger/debug-live-azure-applications.md) Snapshot Debugger|
|Azure VM|[Azure’da ASP.NET hatalarını uzaktan ayıklama](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Azure Service Fabric uygulamasında hata ayıklama](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Uzaktan hata ayıklama ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) [veya Uzaktan Hata Ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# veya Visual Basic|[Uzaktan C# veya Visual Basic projesi hatası ayıklama](../debugger/remote-debugging-csharp.md)|
|C++|[C++ projesinin hatalarını uzaktan ayıklama](../debugger/remote-debugging-cpp.md)|
|Universal Windows Apps (UWP)|[Uzak makinede UWP uygulamaları çalıştırma veya](../debugger/run-windows-store-apps-on-a-remote-machine.md) [Yüklü uygulama paketinde hata ayıklama](../debugger/debug-installed-app-package.md)|

Yalnızca uzaktan hata ayıklayıcısını indirip yüklemek ve senaryo için ek yönergelere ihtiyacınız yoksa, bu makaledeki adımları izleyin.

## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Gereksinim -leri

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> (İsteğe bağlı) Uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırmak için

Uzaktan hata ayıklayıcısını (*msvsmon.exe*) Visual Studio Community, Professional veya yüklü Enterprise bulabilirsiniz. Bazı senaryolarda uzaktan hata ayıklamayı ayarlamanın en kolay yolu, uzak hata ayıklayıcıyı (msvsmon.exe) bir dosya paylaşımından çalıştırmaktır. Kullanım sınırlamaları için uzaktan hata ayıklayıcının Yardım sayfasına ( Uzaktan **hata ayıklayıcıda > Yardım** sayfasına bakın).

1. Dizinde *msvsmon.exe* sürümünüzle eşleşen Visual Studio:

   ::: moniker range=">=vs-2022"

   *Program Files\Microsoft Visual Studio\2022\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   *Program Files\Microsoft Visual Studio\2022\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2019"

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Uzak Hata **Ayıklayıcı klasörünü** Visual Studio paylaşın.

3. Uzak bilgisayarda, paylaşılan *msvsmon.exe'i* çalıştırın. Kurulum [yönergelerini izleyin.](#bkmk_setup)

> [!TIP]
> Komut satırı yüklemesi ve komut satırı başvurusu *için,msvsmon.exe'nin* yüklü olduğu bilgisayardaki komut satırına yazarak Visual Studio yardım sayfasına bakın (veya uzak hata ayıklayıcıda Yardım ``msvsmon.exe /?`` > **Kullanımı'na** gidin).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> Uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Uzaktan hata ayıklayıcıyı yapılandırma
Uzaktan hata ayıklayıcıyı ilk kez başlattıktan sonra yapılandırmanın bazı yönlerini değiştirebilirsiniz.

- Diğer kullanıcıların uzaktan hata ayıklayıcısına bağlanması için izinler eklemeniz gerekirse Araçlar ve **İzinler'> seçin.** İzinleri vermek veya reddetmek için yönetici ayrıcalıklarınızın olması gerekir.

     > [!IMPORTANT]
     > Uzak hata ayıklayıcıyı, Visual Studio bilgisayarda kullanmakta olan kullanıcı hesabından farklı bir kullanıcı hesabı altında çalıştırabilirsiniz, ancak uzak hata ayıklayıcının izinlerine farklı kullanıcı hesabını eklemeniz gerekir.

     Alternatif olarak, uzak hata ayıklayıcısını komut satırına **/allow \<username>** parametresiyle **başlatabilirsiniz: msvsmon /allow \<username@computer>**.

- Kimlik Doğrulama modunu veya bağlantı noktası numarasını değiştirmeniz veya uzak araçlar için bir zaman aşımı değeri belirtmeniz gerekirse: Araçlar ve **Seçenekler'i > seçin.**

     Varsayılan olarak kullanılan bağlantı noktası numaralarının listesi için bkz. [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları.](../debugger/remote-debugger-port-assignments.md)

     > [!WARNING]
     > Uzak araçları Kimlik Doğrulaması Yok modunda çalıştırmayı seçebilirsiniz, fakat bu mod kesinlikle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Kimlik Doğrulaması Yok modunu yalnızca ağın kötü amaçlı veya saldırgan trafik riski altında olduğundan emin değilken seçin.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> (İsteğe bağlı) Uzak hata ayıklayıcıyı hizmet olarak yapılandırma
ASP.NET ve diğer sunucu ortamlarında hata ayıklama için, uzak hata ayıklayıcıyı yönetici olarak çalıştırmanız veya her zaman çalıştırmak için uzak hata ayıklayıcıyı bir hizmet olarak çalıştırmanız gerekir.

 Uzak hata ayıklayıcıyı bir hizmet olarak yapılandırmak için aşağıdaki adımları izleyin.

1. Uzaktan Hata **Ayıklayıcı Yapılandırma Sihirbazı'nı (rdbgwiz.exe).** (Bu, Uzaktan Hata Ayıklayıcı'dan ayrı bir uygulamadır.) Yalnızca uzak araçları yüklemenizde kullanılabilir. Bu, Visual Studio.

2. Yapılandırma sihirbazını çalıştırmaya başlama. İlk sayfa geldiğinde, Sonraki'ne **tıklayın.**

3. Visual Studio **2015** Uzaktan Hata Ayıklayıcısını hizmet olarak çalıştır onay kutusunu işaretleyin.

4. Kullanıcı hesabının adını ve parolasını ekleyin.

    Bu hesaba hizmet  olarak oturum açma kullanıcı hakkı eklemeniz (Başlangıç sayfasında veya penceresinde Yerel Güvenlik  İlkesini **Bul** (secpol.msc) veya bir komut isteminde **secpol** yazmanız gerekir. Pencere görüntülendiğinde Kullanıcı Hakları **Ataması'ne çift tıklayın** ve ardından sağ **bölmede** Hizmet olarak oturum aç'ı bulun. Çift tıklayın. Kullanıcı hesabını Özellikler penceresine ekleyin **ve Tamam'a** **tıklayın.** **İleri**’ye tıklayın.

5. Uzak araçların iletişim kurması istediğiniz ağ türünü seçin. En az bir ağ türü seçilmelidir. Bilgisayarlar bir etki alanı üzerinden bağlı ise, ilk öğeyi seçmeniz gerekir. Bilgisayarlar bir çalışma grubu veya ev grubu üzerinden bağlıysa, ikinci veya üçüncü öğeleri seçmeniz gerekir. **İleri**’ye tıklayın.

6. Hizmet başlatlanıyorsa, Yapılandırma **Sihirbazı'nı başarıyla tamamladınız Visual Studio Uzaktan Hata Ayıklayıcı görüntülenir.** Hizmet başlatılamayacaksa, Yapılandırma **Sihirbazı'nda Visual Studio Uzaktan Hata Ayıklayıcı görüntülenir.** Sayfa ayrıca hizmeti başlatmaya yardımcı olmak için takip edecek bazı ipuçları da sağlar.

7. **Finish (Son)** düğmesine tıklayın.

   Bu noktada uzak hata ayıklayıcı bir hizmet olarak çalışıyor. Denetim Masası > **Services'e gidip Visual Studio** **2015 Uzaktan Hata Ayıklayıcı'ya bakarak bunu doğruabilirsiniz.**

   uzaktan hata ayıklayıcı hizmetini Denetim Masası > **başlatabilirsiniz.**

## <a name="set-up-debugging-with-remote-symbols"></a>Uzak sembollerle hata ayıklamayı ayarlama

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Uzaktan Hata Windows Güvenlik Duvarı'nı yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzak IIS ASP.NET Core Uzaktan Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)