---
title: Uzak IIS ASP.NET Core'da Uzaktan Hata Ayıklama | Microsoft Docs
description: Uzak ASP.NET Core (IIS) bilgisayarına dağıtılmış bir Internet Information Services hata ayıklayıcısını kullanarak Visual Studio ayıklar.
ms.custom: remotedebugging, SEO-VS-2020
ms.date: 08/27/2021
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 376a0f438e17d1023644e545812c50cf35b34dca
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635944"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Visual Studio'ASP.NET Core Uzak IIS Bilgisayarına Uzaktan Hata Ayıklama Visual Studio

IIS'ye ASP.NET Core bir uygulamanın hata ayıklaması için, uygulamayı dağıtarak uzak araçları yükleyin ve çalıştırın ve ardından Visual Studio.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Bu kılavuzda bir sanal ağ oluşturma ve yapılandırma Visual Studio ASP.NET Core IIS'ye dağıtma ve uzaktan hata ayıklayıcıyı Visual Studio. 4.5.2 ASP.NET uzaktan hata ayıklamak için bkz. [IIS ASP.NET Uzaktan Hata Ayıklama.](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) Azure'ı kullanarak IIS'de de dağıtım ve hata ayıklama da sabilirsiniz. Daha Azure App Service, önceden yapılandırılmış bir IIS örneğinde ve uzaktan hata ayıklayıcıda Snapshot Debugger kullanarak veya [hata](../debugger/debug-live-azure-applications.md) ayıklayıcıyı [Sunucu Gezgini.](../debugger/remote-debugging-azure.md)

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"
Visual Studio makalede gösterilen adımları takip etmek için Visual Studio 2019 gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio makalede gösterilen adımları takip etmek için Visual Studio 2017 gereklidir.
::: moniker-end

Bu yordamlar şu sunucu yapılandırmalarında test edilmiştir:
* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve IIS 10
* Windows Server 2019 ve IIS 10

## <a name="network-requirements"></a>Ağ gereksinimleri

Ara sunucu üzerinden bağlanan iki bilgisayar arasında hata ayıklama desteklenmiyor. Çevirmeli İnternet gibi yüksek gecikmeli veya düşük bant genişliğine sahip bir bağlantı üzerinden veya ülkeler arasında İnternet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya kabul edilemez düzeyde yavaş olabilir. Gereksinimlerin tam listesi için bkz. [Gereksinimler.](../debugger/remote-debugging.md#requirements_msvsmon)

## <a name="app-already-running-in-iis"></a>Uygulama zaten IIS'de mi çalışıyor?

Bu makale, Windows sunucusunda IIS'nin temel yapılandırmasını ayarlama ve uygulamayı Visual Studio. Bu adımlar sunucuda gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırılaya kadar olduğundan ve uzaktan hata ayıklamaya hazır olduğundan emin olmak için dahil edilir.

* Uygulamanız IIS'de çalışıyorsa ve yalnızca uzak hata ayıklayıcısını indirmek ve hata ayıklamayı başlatmak için Uzak araçları İndirme ve Yükleme 'ye gidin [ve Windows Server'a gidin.](#BKMK_msvsmon)

* Hata ayıklamak için, uygulamanın IIS'de doğru şekilde ayarıldığından, dağıtıldığından ve çalıştırıldığından emin olmak için yardım almak için bu konudaki tüm adımları izleyin.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>ASP.NET Core bilgisayarda Visual Studio oluşturma

1. Yeni bir web ASP.NET Core oluşturun.

    ::: moniker range=">=vs-2019"
    2019'Visual Studio'da başlangıç **penceresinde Yeni proje oluştur'a** tıklayın. Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne**  >  **tıklayın.** **Web uygulaması yazın,** dil **olarak C#** seçin, ardından ASP.NET Core Web Uygulaması **(Model-Görünüm-Denetleyici)** ve ardından Sonraki'yi **seçin.** Sonraki ekranda projeye **MyASPApp adını ve ardından** Sonraki'yi **seçin.**

    Önerilen hedef çerçeveyi veya .NET 6'yi seçin ve ardından **Oluştur'a seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    2017 Visual Studio de Dosya > **Yeni**> Project'ı ve ardından **Visual C# > Web Uygulaması'> ASP.NET Core seçin.** Uygulama şablonları ASP.NET Core Web Uygulaması **(Model-View-Controller) öğesini seçin.** 2.1 ASP.NET Core, **Docker** Desteğini Etkinleştir'in seçili olduğundan ve Kimlik  Doğrulaması Yok olarak ayarlanmış olduğundan **emin olun.** Projeye **MyASPApp adını girin.**
    ::: moniker-end

4. About.cshtml.cs dosyasını açın ve yönteminde bir kesme noktası ayarlayın (eski şablonlarda bunun yerine HomeController.cs dosyasını açın ve yönteminde `OnGet` kesme noktası `About()` ayarlayın).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Windows Server'da IIS'yi Yükleme ve Yapılandırma

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server'da tarayıcı güvenlik ayarlarını güncelleştirme

Internet Explorer'da Gelişmiş Güvenlik Yapılandırması etkinleştirildiyse (varsayılan olarak etkindir), bazı web sunucusu bileşenlerini indirmenizi sağlamak için bazı etki alanlarını güvenilen siteler olarak eklemeniz gerekir. Güvenilen Siteler ve Siteleri için İnternet Seçenekleri'ne **> Güvenlik > siteleri > ekleyin.** Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı indirirken, çeşitli web sitesi betiklerini ve kaynaklarını yükleme izni vermek için istekler edinebilirsiniz. Bu kaynakların bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle'ye** tıklayın.

## <a name="install-aspnet-core-on-windows-server"></a>ASP.NET Core Server'Windows yükleme

1. .NET Core Barındırma Paketi'nin barındırma sistemine yükleyin. Paket. .NET Core Çalışma Zamanı, .NET Core Kitaplığı ve ASP.NET Core Modülü'ASP.NET Core yüklenir. Daha ayrıntılı yönergeler için bkz. [IIS'de yayımlama.](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)

    Geçerli .NET Core barındırma paketi için, ASP.NET Core [Paketi'ne yükleyin.](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)
    .NET Core 2 için [.NET Core'Windows Sunucu Barındırma'ya yükleyin.](https://aka.ms/dotnetcore-2-windowshosting)

    > [!NOTE]
    > Sistemin İnternet bağlantısı yoksa, .NET Core Windows Server Hosting paketi yüklemeden önce *[Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)* Yeniden Dağıtılabilir'i alın ve yükleyin.

2. Sistemi yeniden başlatın (veya sistem YOLUNDA bir değişiklik almak için bir komut isteminden net start w3svc ve ardından **net start w3svc)** **net stop** komutunu yürütün.

## <a name="choose-a-deployment-option"></a>Dağıtım seçeneği belirtin

Uygulamayı IIS'ye dağıtmak için yardıma ihtiyacınız varsa şu seçenekleri göz önünde bulun:

* IIS'de yayımlama ayarları dosyası oluşturarak ve ayarları iis'te içeri aktararak Visual Studio. Bazı senaryolarda bu, uygulamanızı dağıtmanın hızlı bir yoludur. Yayımlama ayarları dosyasını sanız, izinler IIS'de otomatik olarak ayarlanır.

* Dağıtımı yerel bir klasöre yayımlayıp tercih edilen bir yöntem tarafından IIS'de hazırlanmış bir uygulama klasörüne kopyalayıp dağıtın.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(İsteğe bağlı) Yayımlama ayarları dosyası kullanarak dağıtma

Bu seçeneği kullanarak bir yayımlama ayarları dosyası oluşturabilir ve dosyayı Visual Studio.

> [!NOTE]
> Bu dağıtım yöntemi Web Dağıtımı sunucuda yüklü olması gereken bir uygulama kullanır. Ayarları içeri aktarma Web Dağıtımı el ile yapılandırmak için, Barındırma Sunucuları için Web Dağıtımı 3.6 yerine Web Dağıtımı 3.6'Web Dağıtımı yükleyebilirsiniz. Ancak, sunucuyu Web Dağıtımı yapılandırdıysanız, sunucusundaki bir uygulama klasörünün doğru değer ve izinlerle yapılandırıldığından emin ASP.NET [gerekir.](#BKMK_deploy_asp_net)

### <a name="configure-the-aspnet-core-web-site"></a>ASP.NET Core web sitesini yapılandırma

1. IIS Yöneticisi'nde, sol bölmede **Bağlantılar'ın altında** Uygulama **Havuzları'nı seçin.** **DefaultAppPool'ı** açın ve **.NET CLR sürümünü Yönetilen** **Kod Yok olarak ayarlayın.** Bu, daha fazla ASP.NET Core. Varsayılan Web Sitesi DefaultAppPool kullanır.

2. DefaultAppPool'u durdurun ve yeniden başlatın.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows Server'Web Dağıtımı barındırmak için Windows yapılandırma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server'da IIS'de yayımlama ayarları dosyasını oluşturma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Yayımlama ayarlarını içeri aktarma Visual Studio dağıtma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlatılır. Uygulama bir uygulamanın çalışma Visual Studio doğru çalıştığını doğrulamak için IIS'de uygulamayı başlatabilirsiniz. Daha ASP.NET Core, **DefaultAppPool** için Uygulama havuzu alanı'nın Yönetilen Kod Yok olarak ayarlanmış olduğundan **da emin olun.**

1. Hata ayıklama yapılandırmasına geçiş.

   ::: moniker range=">=vs-2019"
   Profili **düzenlemek** için Düzenle'yi seçin ve sonra da **Ayarlar.** Bir Hata **ayıklama yapılandırması** seçin ve ardından Dosya Yayımlama **seçeneklerinin altında Hedefte** ek dosyaları **kaldır'ı** seçin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Yeni **Ayarlar** iletişim kutusunda, Sonraki'ne tıklayarak hata ayıklamayı **etkinleştirin,** bir  **Hata** ayıklama yapılandırması seçin ve ardından Dosya Yayımlama seçenekleri altında Hedefte ek dosyaları **kaldır'ı** seçin.
   ::: moniker-end

   > [!IMPORTANT]
   > Yayın yapılandırmasını seçerseniz, yayımlarkenweb.configdosyasında *hata ayıklamayı* devre dışı bırakın.

1. **Kaydet'e** tıklayın ve uygulamayı yeniden yayımlar.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(İsteğe bağlı) Yerel bir klasöre yayımlaarak dağıtma

Uygulamayı PowerShell veya RoboCopy kullanarak IIS'ye kopyalamak veya dosyaları el ile kopyalamak için bu seçeneği kullanarak uygulamanızı dağıtabilirsiniz.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Windows Server ASP.NET Core web sitesini yapılandırma

1. Yeni Windows açın ve yeni bir klasör oluşturun: **C:\Publish**, burada daha sonra ASP.NET Core dağıtın.

2. Henüz açık değilse, Internet Information Services **(IIS) Yöneticisi'ni açın.** (Uygulamanın sol bölmesinde IIS'Sunucu Yöneticisi **seçin.** Sunucuya sağ tıklayın ve Internet Information Services **(IIS) Yöneticisi'ni** seçin.)

3. Sol **bölmede** Bağlantılar'ın altında Siteler'e **gidin.**

4. Varsayılan **Web Sitesi'yi seçin,** Temel **Ayarlar'ı** seçin ve **Fiziksel** yolu **C:\Publish olarak ayarlayın.**

5. Varsayılan Web Sitesi **düğümüne sağ tıklayın ve** Uygulama Ekle'yi **seçin.**

6. Diğer Ad **alanını** **MyASPApp** olarak ayarlayın, varsayılan Uygulama Havuzunu (**DefaultAppPool**) kabul eder ve **Fiziksel** yolu **C:\Publish olarak ayarlayın.**

7. **Bağlantılar'ın** altında Uygulama **Havuzları'ı seçin.** **DefaultAppPool'ı** açın ve Uygulama havuzu alanını Yönetilen **Kod Yok olarak ayarlayın.**

8. IIS Yöneticisi'nde yeni siteye sağ tıklayın, İzinleri Düzenle'yi seçin ve web uygulamasına erişim için yapılandırılmış IUSR, IIS_IUSRS veya kullanıcının Okuma ve Yürütme haklarına sahip yetkili bir kullanıcı olduğundan emin & olun.

    Erişimi olan bu kullanıcılardan birini görmüyorsanız IUSR'yi Okuma ve Yürütme haklarına sahip bir kullanıcı & uygulayın.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Visual Studio'den yerel bir klasöre yayımlar ve uygulamayı Visual Studio

Ayrıca, dosya sistemini veya diğer araçları kullanarak uygulamayı yayımlayın ve dağıtın.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Uzak araçları Windows Server'a indirme ve yükleme

Uzak araçların, uygulama sürümle eşleşen sürümünü Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Windows Server'da uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izin eklemeniz, uzak hata ayıklayıcı için kimlik doğrulama modunu veya bağlantı noktası numarasını değiştirmenizi gerekirse, bkz. Uzaktan hata [ayıklayıcıyı yapılandırma.](../debugger/remote-debugging.md#configure_msvsmon)

Uzak hata ayıklayıcısını bir hizmet olarak çalıştırma hakkında bilgi için [bkz. Uzak hata ayıklayıcıyı bir hizmet olarak çalıştırma.](../debugger/remote-debugging.md#bkmk_configureService)

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>ASP.NET bilgisayardan Visual Studio ekleme

1. Bu Visual Studio hata ayıklamaya çalıştığın çözümü açın ( bu makaledeki tüm adımları takip ediyorsanız **MyASPApp).**
2. Bu Visual Studio İşleme Ekle **(Ctrl** + Alt + P) > Hata Ayıkla'ya tıklayın.

    > [!TIP]
    > 2017 ve sonraki Visual Studio sürümlerinde **>** Hata Ayıklama ve İşleme Yeniden İliştir... (Shift + Alt + P) kullanarak daha önce bağlı olduğunuz işleme yeniden iliştirebilirsiniz.

3. Niteleyici alanını olarak ayarlayın ve **\<remote computer name>** Enter tuşuna **basın.**

    Gerekli Visual Studio bilgisayar adına eklendiğinden emin olun. Bu bağlantı noktası şu biçimde görünür: **\<remote computer name> :p ort**

    ::: moniker range=">=vs-2022"
    2022 Visual Studio de **\<remote computer name> :4026 görüyor gerekir**
    ::: moniker-end
    ::: moniker range="vs-2019"
    **\<remote computer name> 2019'Visual Studio:4024'ü görüyoruz**
    ::: moniker-end
    ::: moniker range="vs-2017"
    2017 Visual Studio de **\<remote computer name> :4022 ifadesini görüyor gerekir**
    ::: moniker-end
    Bağlantı noktası gereklidir. Bağlantı noktası numarasını görmüyorsanız el ile ekleyin.

4. **Yenile**'ye tıklayın.
    Kullanılabilir İşlemler penceresinde bazı **işlemlerin görüntü olduğunu görüyoruz.**

    Herhangi bir işlem görmüyorsanız, uzak bilgisayar adı (bağlantı noktası gereklidir) yerine IP adresini kullanmayı deneyin. `ipconfig`IPv4 adresini almak için komut satırı içinde kullanabilirsiniz.

    Bul düğmesini kullanmak **için** sunucuda UDP bağlantı noktası [3702'yi açmanız](#bkmk_openports) gerekir.

5. Tüm **kullanıcıların işlemlerini göster'i seçin.**

6. Uygulamanızı hızla bulmak için işlem adının ilk harfini yazın.

    * IIS'de işlem [içinde barındırma modelini kullanıyorsanız,](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) işlem için doğru **w3wp.exe** seçin. .NET Core 3'te başlayarak bu varsayılan değerdir.

    * Aksi takdirde, **dotnet.exe** seçin. (Bu işlem dışında barındırma modelidir.)

    Bir veya birden çok işlem *w3wp.exe* *dotnet.exe* Kullanıcı Adı **sütununu** kontrol edin. Bazı senaryolarda Kullanıcı Adı **sütunu,** **IIS APPPOOL\DefaultAppPool gibi** uygulama havuzu adını gösterir. Uygulama Havuzu'nun benzersiz olmadığını görüyorsanız, hata ayıklamak istediğiniz uygulama örneği için yeni bir adlandırılmış Uygulama Havuzu oluşturun ve bunu Kullanıcı Adı **sütununda** kolayca bulabilirsiniz.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **Ekle'ye tıklayın.**

8. Uzak bilgisayarın web sitesini açın. Bir tarayıcıda, 'a **http://. \<remote computer name>**

    Web sayfasında ASP.NET gerekir.

9. Çalışan ASP.NET sayfasında Hakkında sayfasına **tıklayın.**

    Kesme noktası, Visual Studio.

## <a name="troubleshooting-iis-deployment"></a>IIS dağıtımı sorunlarını giderme

- Ana bilgisayar adını kullanarak ana bilgisayara bağlanamıyorsanız bunun yerine IP adresini deneyin.
- Uzak sunucuda gerekli bağlantı noktalarının açık olduğundan emin olun.
- Daha ASP.NET Core için **DefaultAppPool** uygulama havuzu alanı'nın Yönetilen Kod Yok olarak ayarlanmış **olduğundan emin olun.**
- Uygulamanıza kullanılan ASP.NET sürümünün, sunucuda yüklü olan sürümle aynı olduğunu doğrulayın. Uygulamanız için, Özellikler sayfasında sürümü görüntüleyebilirsiniz ve **ayarlayın.** Uygulamayı farklı bir sürüme ayarlamak için bu sürümün yüklü olması gerekir.
- Uygulama açılmaya çalışsa ama bir sertifika uyarısı görüyorsanız siteye güvenmeyi seçin. Uyarıyı zaten kapattıysanız projenize bir *.pubxml dosyası olan yayımlama profilini düzenleyebilir ve aşağıdaki öğeyi eklersiniz (yalnızca test için): `<AllowUntrustedCertificate>true</AllowUntrustedCertificate>`
- Uygulama, uygulamanın Visual Studio doğru dağıtıldığından emin olmak için IIS'de başlatabilirsiniz.
- Durum bilgileri için Visual Studio penceresini ve hata iletilerinizi kontrol edin.

## <a name="open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Windows Server'da gerekli bağlantı noktalarını açma

Çoğu kurulumda gerekli bağlantı noktaları, ASP.NET ve uzaktan hata ayıklayıcının yüklenmesiyle açılır. Ancak, bağlantı noktalarının açık olduğunu doğrulamanız gerekir.

> [!NOTE]
> Bir Azure VM'de, Ağ güvenlik grubu aracılığıyla bağlantı [noktalarını açabilirsiniz.](/azure/virtual-machines/windows/nsg-quickstart-portal)

Gerekli bağlantı noktaları:

* 80 - IIS için gereklidir (HTTP)
::: moniker range=">=vs-2022"
* 4026 - Visual Studio 2022'den uzaktan hata ayıklama için gereklidir [(daha](../debugger/remote-debugger-port-assignments.md) fazla bilgi için bkz. Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları).
::: moniker-end
::: moniker range="vs-2019"
* 4024 - Visual Studio 2019'dan uzaktan hata ayıklama için gereklidir [(daha](../debugger/remote-debugger-port-assignments.md) fazla bilgi için bkz. Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Visual Studio 2017'den uzaktan hata ayıklama için gereklidir [(daha](../debugger/remote-debugger-port-assignments.md) fazla bilgi için bkz. Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları).
::: moniker-end
* UDP 3702 - (İsteğe bağlı)  Bulma bağlantı noktası, ağ içinde uzak hata ayıklayıcıya iliştirme sırasında Bul düğmesini Visual Studio.

1. Windows Server'da bir bağlantı noktası açmak için Başlat menüsünü **açın,** gelişmiş güvenlik **Windows güvenlik duvarı araması yapabilirsiniz.**

2. Ardından Yeni **Kural bağlantı noktası > Gelen Kuralları'> ve** ardından Sonraki 'ye **tıklayın.** (UDP 3702 için bunun yerine **Giden Kuralları'ı** seçin.)

3. Belirli **yerel bağlantı noktaları altında** bağlantı noktası numarasını girin, Ardından'ya **tıklayın.**

4. Bağlantıya **İzin Ver'e tıklayın,** Ardından'ya **tıklayın.**

5. Bağlantı noktası için etkinleştirmek istediğiniz bir veya daha fazla ağ türü seçin ve Ardından'ya **tıklayın.**

    Seçen türün uzak bilgisayarın bağlı olduğu ağı içermesi gerekir.

6. Gelen Kuralı için adı **(örneğin, IIS**, **Web Dağıtımı** veya **msvsmon)** ekleyin ve Son'a **tıklayın.**

    Yeni kuralınızı Gelen Kurallar veya Giden Kuralları listesinde görüyor gerekir.

    Güvenlik Duvarı'nı yapılandırma hakkında daha fazla Windows, bkz. Uzaktan Hata [Ayıklama Windows Güvenlik Duvarı'nı yapılandırma.](../debugger/configure-the-windows-firewall-for-remote-debugging.md)

3. Diğer gerekli bağlantı noktaları için ek kurallar oluşturun.
