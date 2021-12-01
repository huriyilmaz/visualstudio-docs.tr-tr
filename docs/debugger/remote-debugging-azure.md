---
title: IIS ve Azure ASP.NET Core Uzaktan Hata Ayıklama | Microsoft Docs
description: Visual Studio ASP.NET Core uygulamasını ayarlamayı ve yapılandırmayı, Azure kullanarak IIS'ye dağıtmayı ve uzaktan hata ayıklayıcıyı Visual Studio.
ms.custom: remotedebugging
ms.date: 10/05/2021
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: fea205ffd691ed965f87d4df8334a26ae562af14
ms.sourcegitcommit: 263703af9c4840e0e0876aa99df6dd7455c43519
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2021
ms.locfileid: "133387160"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Visual Studio'ASP.NET Core Azure'da IIS'de Uzaktan Hata Ayıklama Visual Studio

Bu kılavuzda bir Visual Studio ASP.NET Core uygulamasını ayarlama ve yapılandırma, Azure kullanarak IIS'ye dağıtma ve uzaktan hata ayıklayıcıyı Visual Studio.

IIS senaryoları için Linux desteklenmiyor.

Azure'da uzaktan hata ayıklama için önerilen yol senaryonıza bağlıdır:

* Sanal ağlarda ASP.NET Core ayıklamak Azure App Service bkz. azure uygulamalarını [kullanarak Snapshot Debugger.](../debugger/debug-live-azure-applications.md) Bu önerilen yöntemdir.
* Daha geleneksel hata ASP.NET Core kullanarak Azure App Service hata ayıklamada hata ayıklamak için bu konudaki adımları izleyin (Azure App Service [üzerinde uzaktan hata ayıklama).](#remote_debug_azure_app_service)

    Bu senaryoda, uygulamanızı Visual Studio'den Azure'a dağıtmanız gerekir, ancak aşağıdaki çizimde gösterildiği gibi IIS'yi veya uzak hata ayıklayıcısını (bu bileşenler noktalı satırlarla gösterilir) el ile yüklemeniz veya yapılandırmanız gerekmez.

    ![Visual Studio, Azure App Service ve ASP.NET gösteren diyagram. IIS ve Uzaktan Hata Ayıklayıcı noktalı satırlarla temsil edildi.](../debugger/media/remote-debugger-azure-app-service.png)

* Azure VM'sinde IIS'de hata ayıklamak için bu konudaki adımları izleyin [(Azure VM'de Uzaktan](#remote_debug_azure_vm)Hata Ayıklama bölümüne bakın). Bu, IIS'nin özelleştirilmiş bir yapılandırmasını kullanmanızı sağlar, ancak kurulum ve dağıtım adımları daha karmaşıktır.

    Bir Azure VM için uygulamanızı Visual Studio Azure'a dağıtmanız ve ayrıca aşağıdaki çizimde gösterildiği gibi IIS rolünü ve uzaktan hata ayıklayıcıyı el ile yüklemeniz gerekir.

    ![Visual Studio, Azure VM ve ASP.NET gösteren diyagram. IIS ve Uzaktan Hata Ayıklayıcı düz çizgilerle temsil edildi.](../debugger/media/remote-debugger-azure-vm.png)

* Azure ASP.NET Core'Service Fabric hata ayıklamak için [bkz. Uzak Service Fabric hata ayıklama.](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)

> [!WARNING]
> Bu öğreticide yer alan adımları tamamlayan azure kaynaklarını silebilirsiniz. Bu sayede gereksiz ücretlerden kaçınarak ücret ödemezsiniz.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"
Visual Studio 2019 veya sonraki sürümlerin bu makalede gösterilen adımları izlemesi gerekir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio makalede gösterilen adımları takip etmek için 2017'ye bakın.
::: moniker-end

### <a name="network-requirements"></a>Ağ gereksinimleri

Ara sunucu üzerinden bağlanan iki bilgisayar arasında hata ayıklama desteklenmiyor. Çevirmeli İnternet gibi yüksek gecikme süresi veya düşük bant genişliği bağlantısı üzerinden veya ülkeler arasında İnternet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya kabul edilemez düzeyde yavaş olabilir. Gereksinimlerin tam listesi için bkz. [Gereksinimler.](../debugger/remote-debugging.md#requirements_msvsmon)

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>ASP.NET Core bilgisayarda Visual Studio oluşturma

1. Yeni bir web ASP.NET Core oluşturun.

    ::: moniker range=">=vs-2019"
    2019 Visual Studio da başlangıç **penceresinde Yeni proje oluştur'a** tıklayın. Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne**  >  **tıklayın.** **Web uygulaması yazın,** dil **olarak C#** seçin, ardından ASP.NET Core Web Uygulaması **(Model-Görünüm-Denetleyici)** ve ardından Sonraki'yi **seçin.** Sonraki ekranda projeye **MyASPApp adını ve ardından** Sonraki'yi **seçin.**

    Önerilen hedef çerçeveyi veya .NET 6'yi seçin ve ardından **Oluştur'a seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    2017 Visual Studio de Dosya **> Yeni**> Project'ı ve ardından **Visual C# > Web Uygulaması'> ASP.NET Core seçin.** Uygulama şablonları ASP.NET Core Web Uygulaması **(Model-View-Controller) öğesini seçin.** 2.1 ASP.NET Core veya sonraki bir sonraki bir dosyanın seçili olduğundan, **Docker** Desteğini Etkinleştir'in seçili olduğundan ve Kimlik Doğrulaması Yok olarak ayarlanmış **olduğundan emin olun.**  Projeye **MyASPApp adını girin.**
    ::: moniker-end

1. About.cshtml.cs dosyasını açın ve yönteminde bir kesme noktası ayarlayın (eski şablonlarda bunun yerine HomeController.cs dosyasını açın ve yönteminde `OnGet` kesme noktası `About()` ayarlayın).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service-windows"></a><a name="remote_debug_azure_app_service"></a>Bir Azure App Service ASP.NET Core Uzaktan Hata Ayıklama (Windows)

Bu Visual Studio, tam olarak sağlanan bir IIS örneğini temel alan Azure App Service Windows uygulamanıza hızla yayımlayın ve hata ayıklayın. BIR VM'de IIS barındırıyorsanız, Azure VM'de hata [ayıklamayı deneyin.)](#remote_debug_azure_vm)

::: moniker range=">= vs-2022"

1. Yayımla penceresini kullanarak Azure App Service yayımlama profili oluşturun.

1. Profilde Barındırma altında **...** menüsünü **seçin.** Hata **Ayıklayıcı ekle seçeneğini** belirleyin.

   Visual Studio, uzaktan hata ayıklayıcıyı profilin yayım Azure App Service (Windows) örneğine eklemeye çalışır.

   :::image type="content" source="../debugger/media/attach-debugger-publish-profile.png" alt-text="Yayımlama özeti sayfasının içindeki Hata Ayıklayıcı ekle seçeneğinin ekran görüntüsü.":::

> [!NOTE]
> 2022 Visual Studio de, Cloud Explorer kullanım dışıdır. Cloud Explorer, uzaktan hata ayıklamanın önceki yöntemini Azure App Service.

::: moniker-end
::: moniker range="<= vs-2019"
#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Cloud Explorer kullanarak uygulamayı ve uzaktan hata ayıklamayı dağıtmak için

1. Bu Visual Studio proje düğümüne sağ tıklayın ve Yayımla'yı **seçin.**

    Daha önce herhangi bir yayımlama profili yapılandırdıysanız Yayımla **bölmesi** görüntülenir. Yeni veya **Yeni** **profil'i seçin.**

1. Yeni bir yayımlama profili oluşturun.

    Yayımla **iletişim kutusundan** **Azure'ı** seçin ve **Ardından'yı seçin.** Ardından Azure App Service **(Windows) öğesini** seçin, **Sonraki**'yi seçin ve istemleri takip edin ve profil oluşturun.

    ![Visual Studio kullanarak Azure’a bir ASP.NET Core web uygulaması dağıtın](../debugger/media/vs-2019/remotedbg-azure-app-service-profile.png)

    2017 Visual Studio de Yayımla **iletişim kutusundan** Azure App Service'yi seçin, Yeni Oluştur'a tıklayın ve profil oluşturmak için istemleri izleyin. 

    Daha ayrıntılı yönergeler için [bkz. ASP.NET Core kullanarak Azure'a bir web Visual Studio.](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)

1. Yayımla penceresinde Yapılandırmayı **Düzenle'yi seçin,** bir Hata ayıklama yapılandırmasına geçiş ve ardından Yayımla'yı **seçin.**

   Uygulamada hata ayıklamak için hata ayıklama yapılandırması gerekir.

1. Bulut **Gezgini 'ni** (**Bulut** > **Gezginini Görüntüle)** açın, App Service'ye sağ tıklayın ve Hata **Ayıklayıcı Ekle'yi seçin.**

   Bulut Gezgini kullanılamıyorsa, bunun yerine Sunucu Gezgini açın. Ardından, App Service'daki App Service sağ tıklayın ve Sunucu Gezgini **Ekle'yi seçin.**

1. Çalışan ASP.NET sayfasında Hakkında sayfasına **tıklayın.**

    Kesme noktası, Visual Studio.

    İşte bu kadar! Bu konudaki adımların geri kalanı Azure VM'sinde uzaktan hata ayıklama için geçerlidir.

::: moniker-end

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Azure VM'ASP.NET Core Uzaktan Hata Ayıklama

Windows Server için bir Azure VM oluşturabilir ve ardından IIS'yi ve diğer gerekli yazılım bileşenlerini yükleyebilir ve yapılandırabilirsiniz. Bu işlem, bir dağıtım Azure App Service daha uzun sürer ve bu öğreticide kalan adımları izlemesini gerektirir.

Bu yordamlar şu sunucu yapılandırmalarında test edilmiştir:

* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve IIS 10
* Windows Server 2019 ve IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Uygulama Zaten Azure VM'de IIS'de mi çalışıyor?

Bu makale, Windows sunucusunda IIS'nin temel yapılandırmasını ayarlama ve uygulamayı Visual Studio. Bu adımlar, sunucuda gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırılaya kadar olduğundan ve uzaktan hata ayıklamaya hazır olduğundan emin olmak için dahil edilir.

* Uygulamanız IIS'de çalışıyorsa ve yalnızca uzak hata ayıklayıcısını indirmek ve hata ayıklamayı başlatmak için Uzak araçları İndirme ve Yükleme 'ye gidin [Windows Server.](#BKMK_msvsmon)

* Hata ayıklamak için, uygulamanın IIS'de doğru şekilde ayarıldığından, dağıtıldığından ve çalıştırıldığından emin olmak için yardım almak için bu konudaki tüm adımları izleyin.

  * Başlamadan önce, IIS web sunucusunu yükleme adımlarını [içeren Windows](/azure/virtual-machines/windows/quick-create-portal)Sanal Makine Oluşturma altında açıklanan tüm adımları izleyin.

  * 80 bağlantı noktasını Azure Ağ güvenlik grubunda açık [olduğundan emin olun.](/azure/virtual-machines/windows/nsg-quickstart-portal) 80 bağlantı noktasının açık olduğunu doğrularken, uzak hata ayıklayıcısı (4026, 4024 veya 4022) için de doğru bağlantı noktasını açın. [](#bkmk_openports) Bu şekilde, daha sonra açmak zorunda olmayacaktır. Web Dağıtımı 8172 bağlantı noktasını da açın.

### <a name="update-browser-security-settings-on-windows-server"></a>Windows Server'da tarayıcı güvenlik ayarlarını güncelleştirme

Internet Explorer'da Gelişmiş Güvenlik Yapılandırması etkinleştirildiyse (varsayılan olarak etkindir), bazı web sunucusu bileşenlerini indirmenizi sağlamak için bazı etki alanlarını güvenilen siteler olarak eklemeniz gerekir. Güvenilen Siteler ve Siteleri için İnternet **Seçenekleri'ne > Güvenlik > sitelere > ekleyin.** Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı indirirken, çeşitli web sitesi betiklerini ve kaynaklarını yükleme izni vermek için istekler edinebilirsiniz. Bu kaynakların bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle'ye** tıklayın.

### <a name="install-aspnet-core-on-windows-server"></a>ASP.NET Core Server'Windows yükleme

1. .NET Core Barındırma Paketi'nin barındırma sistemine yükleyin. Paket. .NET Core Çalışma Zamanı, .NET Core Kitaplığı ve ASP.NET Core Modülü'ASP.NET Core yüklenir. Daha ayrıntılı yönergeler için bkz. [IIS'de yayımlama.](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)

    Geçerli .NET Core barındırma paketi için, ASP.NET Core [Paketi'ne yükleyin.](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)
    .NET Core 2 için [.NET Core'Windows Sunucu Barındırma'ya yükleyin.](https://aka.ms/dotnetcore-2-windowshosting)

    > [!NOTE]
    > Sistemin İnternet bağlantısı yoksa, .NET Core Windows Server Hosting paketi yüklemeden önce Microsoft Visual C++ *[2015](https://www.microsoft.com/download/details.aspx?id=53840)* Yeniden Dağıtılabilir'i alın ve yükleyin.

2. Sistemi yeniden başlatın (veya sistem YOLUNDA bir değişiklik almak için bir komut isteminden net start w3svc ve ardından **net start w3svc)** **net stop** komutunu yürütün.

## <a name="choose-a-deployment-option"></a>Dağıtım seçeneği belirtin

Uygulamayı IIS'ye dağıtmak için yardıma ihtiyacınız varsa şu seçenekleri göz önünde bulun:

* IIS'de yayımlama ayarları dosyası oluşturarak ve ayarları iis'te içeri aktararak Visual Studio. Bazı senaryolarda bu, uygulamanızı dağıtmanın hızlı bir yoludur. Yayımlama ayarları dosyasını sanız, izinler IIS'de otomatik olarak ayarlanır.

* Dağıtımı yerel bir klasöre yayımlayıp tercih edilen bir yöntem tarafından IIS'de hazırlanmış bir uygulama klasörüne kopyalayıp dağıtın.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(İsteğe bağlı) Yayımlama ayarları dosyası kullanarak dağıtma

Bu seçeneği kullanarak bir yayımlama ayarları dosyası oluşturabilir ve dosyayı Visual Studio.

> [!NOTE]
> Bu dağıtım yöntemi Web Dağıtımı sunucuda yüklü olması gereken bir uygulama kullanır. Ayarları içeri aktarma Web Dağıtımı el ile yapılandırmak için, Barındırma Sunucuları için Web Dağıtımı 3.6 yerine Web Dağıtımı 3.6'Web Dağıtımı yükleyebilirsiniz. Ancak, sunucuyu Web Dağıtımı yapılandırdıysanız, sunucusundaki bir uygulama klasörünün doğru değer ve izinlerle yapılandırıldığından emin ASP.NET [gerekir](#BKMK_deploy_asp_net).

### <a name="configure-the-aspnet-core-web-site"></a>ASP.NET Core web sitesini yapılandırma

1. IIS Yöneticisi'nde, sol bölmede **Bağlantılar'ın altında** Uygulama **Havuzları'nı seçin.** **DefaultAppPool'ı** açın ve **.NET CLR sürümünü Yönetilen** **Kod Yok olarak ayarlayın.** Bu, ASP.NET Core. Varsayılan Web Sitesi DefaultAppPool kullanır.

2. DefaultAppPool'u durdurun ve yeniden başlatın.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows Server'da Barındırma Sunucuları için Web Dağıtımı yükleme ve yapılandırma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server'da IIS'de yayımlama ayarları dosyasını oluşturma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Yayımlama ayarlarını içeri aktarma Visual Studio dağıtma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> Azure VM'sini yeniden başlattıktan sonra IP adresi değişebilir.

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlatılır. Uygulama bir uygulamanın çalışma Visual Studio doğru şekilde çalıştığını doğrulamak için IIS'de uygulamayı başlatabilirsiniz. Daha ASP.NET Core, **DefaultAppPool** için Uygulama havuzu alanı'nın Yönetilen Kod Yok olarak ayarlanmış olduğundan **da emin olun.**

1. Hata **Ayarlar** iletişim kutusunda, Sonraki'ne tıklayarak hata ayıklamayı **etkinleştirin,** bir  **Hata** ayıklama yapılandırması seçin ve ardından Dosya Yayımlama seçeneklerinin altında Hedefte ek dosyaları **kaldır'ı** seçin.

    > [!IMPORTANT]
    > Yayın yapılandırmasını seçerseniz, yayımlarkenweb.configdosyasında *hata ayıklamayı* devre dışı yapılandırmasını devre dışı yapılandırmasınız.

1. **Kaydet'e** tıklayın ve uygulamayı yeniden yayımlar.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(İsteğe bağlı) Yerel bir klasöre yayımlaarak dağıtma

Uygulamayı PowerShell veya RoboCopy kullanarak IIS'ye kopyalamak veya dosyaları el ile kopyalamak için bu seçeneği kullanarak uygulamanızı dağıtabilirsiniz.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Windows Server ASP.NET Core web sitesini yapılandırma

Yayımlama ayarlarını içeri aktarıyorsanız bu bölümü atlayabilirsiniz.

1. Internet Information Services **(IIS) Yöneticisi'ni açın** ve Siteler'e **gidin.**

2. Varsayılan Web Sitesi **düğümüne sağ tıklayın ve** Uygulama **Ekle'yi seçin.**

3. Diğer Ad **alanını** **MyASPApp,** Uygulama havuzu alanını Ise Yönetilen Kod Yok **olarak ayarlayın.** Fiziksel yolu **C:\Publish** olarak ayarlayın (burada daha sonra ASP.NET Core dağıtacaksınız). 

4. Site IIS Yöneticisi'nde seçiliyken İzinleri Düzenle'yi seçin ve IUSR, IIS_IUSRS veya Uygulama Havuzu için yapılandırılmış kullanıcının Okuma ve Yürütme haklarına sahip yetkili bir kullanıcı olduğundan & olun.

    Erişimi olan bu kullanıcılardan birini görmüyorsanız IUSR'yi Okuma ve Yürütme haklarına sahip bir kullanıcı & izleyin.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(İsteğe bağlı) Visual Studio'den yerel bir klasöre yayımlar ve uygulamayı Visual Studio

Web Dağıtımı'yi kullanamıyorsanız, uygulamayı dosya sistemini veya diğer araçları kullanarak yayımlamanız ve dağıtmanız gerekir. Dosya sistemini kullanarak bir paket oluşturarak başlayabilir ve ardından paketi el ile dağıtabilirsiniz veya PowerShell, Robocopy veya XCopy gibi diğer araçları kullanabilirsiniz. Bu bölümde, bir paket kullanıyorsanız paketi el ile kopyalayıp Web Dağıtımı.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Uzak araçları Windows Server'a indirme ve yükleme

Uzak araçların, uygulama sürümle eşleşen sürümünü Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Windows Server'da uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izin eklemeniz, uzaktan hata ayıklayıcı için kimlik doğrulama modunu veya bağlantı noktası numarasını değiştirmenizi gerekirse, bkz. Uzaktan hata [ayıklayıcıyı yapılandırma.](../debugger/remote-debugging.md#configure_msvsmon)

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Uygulamanın ASP.NET bilgisayardan Visual Studio ekleme

1. Bu Visual Studio hata ayıklamaya çalıştığın çözümü açın ( bu makaledeki adımları takip ediyorsanız **MyASPApp).**
2. Bu Visual Studio İşleme Ekle (Ctrl + Alt + **P) >** Hata Ayıkla'ya tıklayın.

    > [!TIP]
    > 2017 Visual Studio ve sonraki sürümlerde > Hata Ayıkla ve İşleme Yeniden **Ekle...** (Shift+Alt+P) kullanarak daha önce bağlı olduğunuz işleme yeniden iliştirebilirsiniz.

3. Niteleyici alanını olarak ayarlayın ve **\<remote computer name>** Enter tuşuna **basın.**

    Gerekli Visual Studio bilgisayar adına eklendiğinden emin olun. Bu bağlantı noktası şu biçimde görünür: **\<remote computer name> :p ort**

    ::: moniker range=">=vs-2022"
    2022'de **\<remote computer name> :4026'Visual Studio gerekir**
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

    Herhangi bir işlem görmüyorsanız, uzak bilgisayar adı yerine IP adresini kullanmayı deneyin (bağlantı noktası gereklidir). `ipconfig`IPv4 adresini almak için komut satırı içinde kullanabilirsiniz.

    Bul düğmesini kullanmak **için** sunucuda UDP bağlantı noktası [3702'yi açmanız](#bkmk_openports) gerekir.

5. Tüm **kullanıcıların işlemlerini göster'i seçin.**

6. Uygulamanızı hızla bulmak için işlem adının ilk harfini yazın.

    * IIS'de işlem [içinde barındırma modelini kullanıyorsanız,](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) doğru işlem **w3wp.exe** seçin. .NET Core 3'te başlayarak bu varsayılan değerdir.

    * Aksi takdirde, **dotnet.exe** seçin. (Bu işlem dışında barındırma modelidir.)

    Bir veya birden çok işlem *w3wp.exe* *dotnet.exe* Kullanıcı Adı **sütununu** kontrol edin. Bazı senaryolarda, Kullanıcı **Adı sütunu** uygulama havuzu adınızı gösterir, örneğin **IIS APPPOOL\DefaultAppPool.** Uygulama Havuzu'nun benzersiz olmadığını görüyorsanız, hata ayıklamak istediğiniz uygulama örneği için yeni bir adlandırılmış Uygulama Havuzu oluşturun ve bunu Kullanıcı Adı **sütununda** kolayca bulabilirsiniz.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **Ekle'ye tıklayın.**

8. Uzak bilgisayarın web sitesini açın. Bir tarayıcıda, **web'e \<remote computer name> http://.**

    Web sayfasında ASP.NET gerekir.
9. Çalışan ASP.NET sayfasında Hakkında sayfasına **tıklayın.**

    Kesme noktası, Visual Studio.

## <a name="troubleshooting-iis-deployment"></a>IIS dağıtımı sorunlarını giderme

- Ana bilgisayar adını kullanarak ana bilgisayara bağlanamıyorsanız bunun yerine IP adresini deneyin.
- Uzak sunucuda gerekli bağlantı noktalarının açık olduğundan emin olun.
- Daha ASP.NET Core için **DefaultAppPool** için Uygulama havuzu alanı'nın Yönetilen Kod Yok olarak ayarlanmış **olduğundan emin olun.**
- Uygulamanıza kullanılan ASP.NET sürümünün, sunucuda yüklü olan sürümle aynı olduğunu doğrulayın. Uygulamanız için, Özellikler sayfasında sürümü görüntüleyebilirsiniz ve **ayarlayın.** Uygulamayı farklı bir sürüme ayarlamak için bu sürümün yüklü olması gerekir.
- Uygulama açılmaya çalışsa ama bir sertifika uyarısı görüyorsanız siteye güvenmeyi seçin. Uyarıyı zaten kapattıysanız projenize *.pubxml dosyası olan yayımlama profilini düzenleyebilir ve aşağıdaki öğeyi eklersiniz (yalnızca test için): `<AllowUntrustedCertificate>true</AllowUntrustedCertificate>`
- Uygulama, uygulamanın Visual Studio doğru dağıtıldığından emin olmak için IIS'de başlatabilirsiniz.
- Durum bilgileri için Visual Studio penceresini ve hata iletilerinizi kontrol edin.

### <a name="open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Windows Server'da gerekli bağlantı noktalarını açma

Çoğu kurulumda gerekli bağlantı noktaları, ASP.NET ve uzaktan hata ayıklayıcının yüklenmesiyle açılır. Ancak, dağıtım sorunlarını gidermeye devam ediyorsanız ve uygulama bir güvenlik duvarının arkasında barındırıldıysa, doğru bağlantı noktalarının açık olduğunu doğrulamanız gerekebilir.

Bir Azure VM'de, Ağ güvenlik grubu aracılığıyla bağlantı [noktalarını açabilirsiniz.](/azure/virtual-machines/windows/nsg-quickstart-portal)

Gerekli bağlantı noktaları:

* 80 - IIS için gereklidir
::: moniker range=">=vs-2022"
* 4026 - Visual Studio 2022'den uzaktan hata ayıklama için gereklidir [(daha](../debugger/remote-debugger-port-assignments.md) fazla bilgi için bkz. Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları).
::: moniker-end
::: moniker range="vs-2019"
* 4024 - Visual Studio 2019'dan uzaktan hata ayıklama için gereklidir [(daha](../debugger/remote-debugger-port-assignments.md) fazla bilgi için bkz. Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Visual Studio 2017'den uzaktan hata ayıklama için gereklidir [(daha](../debugger/remote-debugger-port-assignments.md) fazla bilgi için bkz. Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları).
::: moniker-end
* UDP 3702 - (İsteğe bağlı)  Bulma bağlantı noktası, hata ayıklayıcısında uzak hata ayıklayıcıya iliştirme sırasında Bul Visual Studio.

Ayrıca, bu bağlantı noktaları yüklemesi tarafından ASP.NET gerekir:
- 8172 - (İsteğe bağlı) Uygulamayı Web Dağıtımı dağıtmak için Visual Studio
