---
title: IIS ve Azure ASP.NET Core Uzaktan Hata Ayıklama | Microsoft Docs
description: Visual Studio ASP.NET Core uygulamasını ayarlamayı ve yapılandırmayı, Azure'ı kullanarak IIS'ye dağıtmayı ve uzaktan hata ayıklayıcıyı Visual Studio.
ms.custom: remotedebugging
ms.date: 08/27/2021
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
ms.openlocfilehash: d4b33cb34472ddcec6869075bdb055e3551ec0fe
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627920"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Azure'da ASP.NET Core IIS'de Uzaktan Hata Ayıklama Visual Studio

Bu kılavuzda bir Visual Studio ASP.NET Core uygulamasını ayarlama ve yapılandırma, Azure kullanarak IIS'ye dağıtma ve uzaktan hata ayıklayıcıyı Visual Studio.

Azure'da uzaktan hata ayıklama için önerilen yol senaryonıza bağlıdır:

* Sanal ağlarda ASP.NET Core ayıklamak Azure App Service bkz. azure uygulamalarını [kullanarak Snapshot Debugger.](../debugger/debug-live-azure-applications.md) Bu önerilen yöntemdir.
* Daha geleneksel hata ASP.NET Core kullanarak Azure App Service hata ayıklamak için bu konudaki adımları izleyin (Azure App Service üzerinde uzaktan [hata ayıklama bölümüne bakın).](#remote_debug_azure_app_service)

    Bu senaryoda, uygulamanızı Visual Studio'dan Azure'a dağıtmanız gerekir, ancak aşağıdaki çizimde gösterildiği gibi IIS'yi veya uzak hata ayıklayıcısını (bu bileşenler noktalı satırlarla gösterilir) el ile yüklemeniz veya yapılandırmanız gerekmez.

    ![Visual Studio, Azure App Service ve ASP.NET gösteren diyagram. IIS ve Uzaktan Hata Ayıklayıcı noktalı satırlarla temsil edildi.](../debugger/media/remote-debugger-azure-app-service.png)

* Azure VM'sinde IIS'de hata ayıklamak için bu konudaki adımları izleyin (Azure VM'de Uzaktan [Hata Ayıklama bölümüne bakın).](#remote_debug_azure_vm) Bu, IIS'nin özelleştirilmiş bir yapılandırmasını kullanmanızı sağlar, ancak kurulum ve dağıtım adımları daha karmaşıktır.

    Bir Azure VM için uygulamanızı Visual Studio Azure'a dağıtmanız ve ayrıca aşağıdaki çizimde gösterildiği gibi IIS rolünü ve uzaktan hata ayıklayıcıyı el ile yüklemeniz gerekir.

    ![Visual Studio, Azure VM ve ASP.NET gösteren diyagram. IIS ve Uzaktan Hata Ayıklayıcı düz çizgilerle temsil edildi.](../debugger/media/remote-debugger-azure-vm.png)

* Azure ASP.NET Core'Service Fabric hata ayıklamak için bkz. [Uzak Service Fabric uygulamanın hata ayıklaması.](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)

> [!WARNING]
> Bu öğreticide yer alan adımları tamamlayan azure kaynaklarını silebilirsiniz. Bu sayede gereksiz ücretlerden kaçınarak ücret ödemezsiniz.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"
Visual Studio makalede gösterilen adımları takip etmek için Visual Studio 2019 gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio makalede gösterilen adımları takip etmek için 2017'ye bakın.
::: moniker-end

### <a name="network-requirements"></a>Ağ gereksinimleri

Ara sunucu üzerinden bağlanan iki bilgisayar arasında hata ayıklama desteklenmiyor. Çevirmeli İnternet gibi yüksek gecikme süresi veya düşük bant genişliği bağlantısı üzerinden veya ülkeler arasında İnternet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya kabul edilemez düzeyde yavaş olabilir. Gereksinimlerin tam listesi için bkz. [Gereksinimler.](../debugger/remote-debugging.md#requirements_msvsmon)

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarda ASP.NET Core oluşturma

1. Yeni bir web ASP.NET Core oluşturun.

    ::: moniker range=">=vs-2019"
    2019 Visual Studio da başlangıç **penceresinde Yeni proje oluştur'a** tıklayın. Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne**  >  **tıklayın.** **Web uygulaması yazın,** dil **olarak C#** seçin, ardından ASP.NET Core Web Uygulaması **(Model-Görünüm-Denetleyici)** ve ardından Sonraki'yi **seçin.** Sonraki ekranda projeye **MyASPApp adını ve ardından** Sonraki'yi **seçin.**

    Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    2017 Visual Studio de Dosya > **Yeni**> Project'ı ve ardından **Visual C# > Web Uygulaması'> ASP.NET Core seçin.** Şablon ASP.NET Core bölümünde Web Uygulaması **(Model-View-Controller) öğesini seçin.** 2.1 ASP.NET Core, **Docker** Desteğini Etkinleştir'in seçili olduğundan ve Kimlik  Doğrulaması Yok olarak ayarlanmış olduğundan **emin olun.** Projeye **MyASPApp adını girin.**
    ::: moniker-end

1. About.cshtml.cs dosyasını açın ve yönteminde bir kesme noktası ayarlayın (eski şablonlarda bunun yerine HomeController.cs dosyasını açın ve yönteminde `OnGet` kesme noktası `About()` ayarlayın).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a>Bir ASP.NET Core Uzaktan Hata Ayıklama Azure App Service

Bu Visual Studio, tam olarak sağlanan bir IIS örneğinde uygulamalarınızı hızla yayımlayın ve hata ayıklayın. Ancak, IIS yapılandırması önceden ayarlanmıştır ve bunu özelleştiresiniz. Daha ayrıntılı yönergeler için [bkz. ASP.NET Core kullanarak Azure'a bir web Visual Studio.](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs) (IIS'yi özelleştirme olanağına ihtiyacınız varsa, Azure VM'de hata [ayıklamayı deneyin.)](#remote_debug_azure_vm)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Cloud Explorer kullanarak uygulamayı ve uzaktan hata ayıklamayı dağıtmak için

1. Bu Visual Studio proje düğümüne sağ tıklayın ve Yayımla'yı **seçin.**

    Daha önce herhangi bir yayımlama profili yapılandırdıysanız **Yayımla** bölmesi görüntülenir. Yeni veya **Yeni** **profil'i seçin.**

1. Yeni bir yayımlama profili oluşturun.

    ::: moniker range=">=vs-2019"
    Yayımla **iletişim kutusundan** **Azure'ı** ve ardından Sonraki'yi **seçin.** Ardından Azure App Service **(Windows) öğesini** seçin, Sonraki 'yi seçin ve istemleri takip edin ve profil oluşturun.

    :::image type="content" source="../debugger/media/vs-2019/remotedbg-azure-app-service-profile.png" alt-text="Visual Studio kullanarak Azure’a bir ASP.NET Core web uygulaması dağıtın":::
    ::: moniker-end
    ::: moniker range="vs-2017"

    Yayımla **Azure App Service'yi seçin,** Yeni **Oluştur'a tıklayın** ve profil oluşturmak için istemleri izleyin. 

    ![Azure App Service’e yayımlama](../debugger/media/remotedbg_azure_app_service_profile.png)
    ::: moniker-end

    Daha ayrıntılı yönergeler için [bkz. ASP.NET Core kullanarak Azure'a bir web Visual Studio.](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)

1. Yayımla penceresinde Yapılandırmayı **Düzenle'yi seçin,** hata ayıklama yapılandırmasına geçiş ve ardından Yayımla'yı **seçin.**

   Uygulamada hata ayıklamak için hata ayıklama yapılandırması gerekir.

1. Bulut **Gezgini'ni** (**Bulut**  >  **Gezginini Görüntüle)** açın, App Service'ye sağ tıklayın ve Hata **Ayıklayıcı ekle'yi seçin.**

   Bulut Gezgini kullanılamıyorsa, bunun yerine Sunucu Gezgini açın. Ardından, App Service'Sunucu Gezgini **ekle'yi seçin.**

1. Çalışan ASP.NET sayfasında Hakkında sayfasına **tıklayın.**

    Kesme noktası, Visual Studio.

    İşte bu kadar! Bu konu başlığında yer alan diğer adımlar, Azure VM'sinde uzaktan hata ayıklama için geçerlidir.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Azure VM'ASP.NET Core Uzaktan Hata Ayıklama

Windows Server için bir Azure VM oluşturabilir ve ardından IIS ve diğer gerekli yazılım bileşenlerini yükp yapılandırabilirsiniz. Bu işlem, bir dağıtım Azure App Service daha uzun sürer ve bu öğreticide kalan adımları izlemesini gerektirir.

Bu yordamlar şu sunucu yapılandırmalarında test edilmiştir:

* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve IIS 10
* Windows Server 2019 ve IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Uygulama Zaten Azure VM'de IIS'de mi çalışıyor?

Bu makale, Windows sunucusunda IIS'nin temel yapılandırmasını ayarlama ve uygulamayı Visual Studio. Sunucuda gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırılaya kadar ve uzaktan hata ayıklamaya hazır olduğundan emin olmak için bu adımlar dahil edilir.

* Uygulamanız IIS'de çalışıyorsa ve yalnızca uzak hata ayıklayıcısını indirmek ve hata ayıklamayı başlatmak için Uzak araçları İndirme ve Yükleme 'ye gidin [ve Windows Server'a gidin.](#BKMK_msvsmon)

* Hata ayıklamak için, uygulamanın IIS'de doğru şekilde ayarıldığından, dağıtıldığından ve çalıştırıldığından emin olmak için yardım almak için bu konudaki tüm adımları izleyin.

  * Başlamadan önce, IIS web sunucusunu yükleme adımlarını [içeren Windows Sanal](/azure/virtual-machines/windows/quick-create-portal)Makine oluşturma konusunda açıklanan tüm adımları izleyin.

  * 80 bağlantı noktasını Azure Ağ güvenlik grubunda açık [olduğundan emin olun.](/azure/virtual-machines/windows/nsg-quickstart-portal) 80 bağlantı noktasının açık olduğunu doğrularken, uzak hata ayıklayıcısı (4024 veya 4022) için de doğru bağlantı noktasını açın. [](#bkmk_openports) Bu şekilde, daha sonra açmak zorunda olmayacaktır. Web Dağıtımı 8172 bağlantı noktasını da açın.

### <a name="update-browser-security-settings-on-windows-server"></a>Windows Server'da tarayıcı güvenlik ayarlarını güncelleştirme

Internet Explorer'da Gelişmiş Güvenlik Yapılandırması etkinleştirildiyse (varsayılan olarak etkindir), bazı web sunucusu bileşenlerini indirmenizi sağlamak için bazı etki alanlarını güvenilen siteler olarak eklemeniz gerekir. güvenilen siteleri eklemek için İnternet Seçenekleri'ne **> Güvenlik > Siteleri'ne > ekleyin.** Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı indirirken, çeşitli web sitesi betiklerini ve kaynaklarını yükleme izni vermek için istekler edinebilirsiniz. Bu kaynakların bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle'ye** tıklayın.

### <a name="install-aspnet-core-on-windows-server"></a>ASP.NET Core Server'Windows yükleme

1. .NET Core Barındırma Paketi'nin barındırma sistemine yükleyin. Paket .NET Core Çalışma Zamanı, .NET Core Kitaplığı ve ASP.NET Core Modülü'ASP.NET Core yüklenir. Daha ayrıntılı yönergeler için bkz. [IIS'de yayımlama.](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)

    Geçerli .NET Core barındırma paketi için, ASP.NET Core [Paketi'ne yükleyin.](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)
    .NET Core 2 için [.NET Core'Windows Sunucu Barındırma'ya yükleyin.](https://aka.ms/dotnetcore-2-windowshosting)

    > [!NOTE]
    > Sistemin İnternet bağlantısı yoksa, .NET Core Windows Server Hosting paketi yüklemeden önce *[Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)* Yeniden Dağıtılabilir'i alın ve yükleyin.

2. Sistemi yeniden başlatın (veya sistem YOLUNDA bir değişiklik almak için bir komut isteminden net start w3svc ve ardından **net start w3svc)** **net stop** komutunu yürütün.

## <a name="choose-a-deployment-option"></a>Dağıtım seçeneği belirtin

Uygulamayı IIS'ye dağıtmak için yardıma ihtiyacınız varsa şu seçenekleri göz önünde bulun:

* IIS 'de bir yayımlama ayarları dosyası oluşturup Visual Studio ayarları içeri aktararak dağıtın. Bazı senaryolarda bu, uygulamanızı dağıtmanın hızlı bir yoludur. Yayınlama ayarları dosyasını oluştururken, izinler IIS 'de otomatik olarak ayarlanır.

* Yerel bir klasöre yayımlayarak ve çıktıyı tercih edilen bir yönteme IIS üzerindeki hazırlanmış bir uygulama klasörüne kopyalayarak dağıtın.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Seçim Yayımlama ayarları dosyası kullanarak dağıtma

Bu seçeneği, bir yayımlama ayarları dosyası oluşturup Visual Studio içine aktarabilirsiniz.

> [!NOTE]
> Bu dağıtım yöntemi, sunucuda yüklü olması gereken Web Dağıtımı kullanır. Ayarları içeri aktarmak yerine Web Dağıtımı el ile yapılandırmak istiyorsanız, barındırma sunucuları için Web Dağıtımı 3,6 yerine Web Dağıtımı 3,6 yükleyebilirsiniz. ancak Web Dağıtımı el ile yapılandırırsanız, sunucudaki bir uygulama klasörünün doğru değerler ve izinlerle yapılandırıldığından emin olmanız gerekir (bkz. [ASP.NET Web sitesini yapılandırma](#BKMK_deploy_asp_net)).

### <a name="configure-the-aspnet-core-web-site"></a>ASP.NET Core web sitesini yapılandırma

1. IIS Yöneticisi 'nde, sol bölmedeki **Bağlantılar** altında **uygulama havuzları**' nı seçin. **DefaultAppPool** ' i açın ve **.NET CLR sürümünü** **yönetilen kod olmadan** ayarlayın. ASP.NET Core için bu gereklidir. Varsayılan Web sitesi, DefaultAppPool 'yi kullanır.

2. DefaultAppPool öğesini durdurup yeniden başlatın.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows sunucusunda barındırma sunucuları için Web Dağıtımı yükleyip yapılandırın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows sunucuda ııs 'de yayımlama ayarları dosyası oluşturma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> Bir Azure VM 'yi yeniden başlatırsanız, IP adresi değişebilir.

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlamalıdır. uygulama Visual Studio başlamazsa, düzgün çalıştığını doğrulamak için uygulamayı ııs 'de başlatın. ASP.NET Core için, **DefaultAppPool** için uygulama havuzu alanının **yönetilen kod yok** olarak ayarlandığından emin olmanız gerekir.

1. **Ayarlar** iletişim kutusunda, **ileri**' ye tıklayarak hata ayıklamayı etkinleştirin, bir **hata ayıklama** yapılandırması seçin ve ardından **dosya yayımlama** seçenekleri altında **hedefteki ek dosyaları kaldır** ' ı seçin.

    > [!IMPORTANT]
    > Bir yayın yapılandırması seçerseniz, ' ı yayımladığınızda *web.config* dosyasında hata ayıklamayı devre dışı bırakabilirsiniz.

1. **Kaydet** ' e tıklayın ve uygulamayı yeniden yayımlayın.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Seçim Yerel bir klasöre yayımlayarak dağıtma

Uygulamayı PowerShell, RoboCopy kullanarak IIS 'e kopyalamak istiyorsanız veya dosyaları el ile kopyalamak istiyorsanız uygulamanızı dağıtmak için bu seçeneği kullanabilirsiniz.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Windows sunucusu bilgisayarında ASP.NET Core Web sitesini yapılandırma

Yayımlama ayarlarını içeri aktarıyorsanız, bu bölümü atlayabilirsiniz.

1. **Internet Information Services (ııs) yöneticisi** ' ni açın ve **siteler**' e gidin.

2. **Varsayılan Web sitesi** düğümüne sağ tıklayın ve **Uygulama Ekle**' yi seçin.

3. **Diğer ad** alanını **Myaspapp** ve uygulama havuzu alanına **yönetilen kod yok** olarak ayarlayın. **fiziksel yolu** **C:\Publish** olarak ayarlayın (ASP.NET Core projeyi daha sonra dağıtacaksınız).

4. IIS Yöneticisi 'nde site seçiliyken, **Izinleri Düzenle**' yi seçin ve uygulama havuzu için yapılandırılmış ıusr, IIS_IUSRS veya kullanıcının okuma & yürütme haklarına sahip yetkili bir kullanıcı olduğundan emin olun.

    Erişim izni olan bu kullanıcılardan birini görmüyorsanız, okuma & yürütme hakları olan bir kullanıcı olarak ıUSR ekleme adımlarını izleyin.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Seçim Visual Studio 'den yerel bir klasöre yayımlayarak uygulamayı yayımlayın ve dağıtın

Web Dağıtımı kullanmıyorsanız, dosya sistemini veya diğer araçları kullanarak uygulamayı yayımlamanız ve dağıtmanız gerekir. Dosya sistemini kullanarak bir paket oluşturarak başlayabilir ve ardından paketi el ile dağıtabilir ya da PowerShell, Robocopy ya da XCopy gibi diğer araçları kullanabilirsiniz. Bu bölümde, Web Dağıtımı kullanmıyorsanız paketi el ile kopyaladığınızı varsaytık.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Windows sunucusuna uzak araçları indirme ve yükleme

Visual Studio sürümünüzle eşleşen uzak araçların sürümünü indirin.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Windows sunucuda uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izinler eklemeniz gerekiyorsa, kimlik doğrulama modunu veya uzaktan hata ayıklayıcı bağlantı noktası numarasını değiştirin, bkz. [Uzaktan hata ayıklayıcıyı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Visual Studio bilgisayardan ASP.NET uygulamasına iliştirme

1. Visual Studio bilgisayarda, hata ayıklamaya çalıştığınız çözümü açın (bu makaledeki adımları takip ediyorsanız,**myaspapp** ).
2. Visual Studio, **hata ayıkla > işleme iliştir** (Ctrl + Alt + P) seçeneğine tıklayın.

    > [!TIP]
    > Visual Studio 2017 ve sonraki sürümlerinde, **hata ayıkla > işlemek için** yeniden iliştir... (shıft + Alt + P) kullanarak daha önce eklediğiniz işleme yeniden iliştirebilirsiniz.

3. Niteleyici alanını olarak ayarlayın **\<remote computer name>** ve **ENTER** tuşuna basın.

    Visual Studio şu biçimde görünen bilgisayar adına gereken bağlantı noktasını eklediğini doğrulayın: **\<remote computer name> :p ort**

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de şunları görmeniz gerekir **\<remote computer name> : 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de şunları görmeniz gerekir **\<remote computer name> : 4022**
    ::: moniker-end
    Bağlantı noktası gereklidir. Bağlantı noktası numarasını görmüyorsanız, el ile ekleyin.

4. **Yenile**'ye tıklayın.
    **Kullanılabilir süreçler** penceresinde bazı işlemlerin göründüğünü görmeniz gerekir.

    Herhangi bir işlem görmüyorsanız, uzak bilgisayar adı yerine IP adresini kullanmayı deneyin (bağlantı noktası gereklidir). `ipconfig`Bir komut satırında, IPv4 adresini almak için kullanabilirsiniz.

    **Bul** düğmesini kullanmak istiyorsanız, sunucuda [UDP bağlantı noktası 3702](#bkmk_openports) ' u açmanız gerekebilir.

5. **Tüm kullanıcıların süreçlerini göster**' i işaretleyin.

6. Uygulamanızı hızlı bir şekilde bulmak için işlem adınızın ilk harfini yazın.

    * IIS 'de [işlem içi barındırma modeli](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) kullanıyorsanız doğru **w3wp.exe** işlemini seçin. .NET Core 3 ' te başlayarak bu varsayılandır.

    * Aksi takdirde **dotnet.exe** işlemini seçin. (Bu işlem dışı barındırma modelidir.)

    *w3wp.exe* veya *dotnet.exe* gösteren birden çok Işlem varsa, **Kullanıcı adı** sütununu kontrol edin. Bazı senaryolarda, **Kullanıcı adı** sütunu **IIS APPPOOL\DefaultAppPool** gibi uygulama havuzu adınızı gösterir. Uygulama havuzunu görürseniz, ancak benzersiz değilse, hata ayıklamak istediğiniz uygulama örneği için yeni bir adlandırılmış uygulama havuzu oluşturun ve ardından **Kullanıcı adı** sütununda kolayca bulabilirsiniz.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **Ekle**' ye tıklayın.

8. Uzak bilgisayarın Web sitesini açın. Bir tarayıcıda **http:// \<remote computer name>** adresine gidin.

    ASP.NET web sayfasını görmeniz gerekir.
9. çalışan ASP.NET uygulamasında, **hakkında** sayfasına yönelik bağlantıya tıklayın.

    Kesme noktasının Visual Studio isabet etmesi gerekir.

## <a name="troubleshooting-iis-deployment"></a>IIS dağıtımında sorun giderme

- Ana bilgisayara konak adını kullanarak bağlanamıyorsanız, bunun yerine IP adresini deneyin.
- Gerekli bağlantı noktalarının uzak sunucuda açık olduğundan emin olun.
- ASP.NET Core için, **DefaultAppPool** için uygulama havuzu alanının **yönetilen kod yok** olarak ayarlandığından emin olmanız gerekir.
- uygulamanızda kullanılan ASP.NET sürümünün sunucuda yüklü olan sürümle aynı olduğunu doğrulayın. Uygulamanız için **Özellikler** sayfasındaki sürümü görüntüleyebilir ve ayarlayabilirsiniz. Uygulamayı farklı bir sürüme ayarlamak için bu sürümün yüklü olması gerekir.
- Uygulama açılmaya çalıştıysanız, ancak bir sertifika uyarısı görürseniz, siteye güvenmeyi seçin. Uyarıyı zaten kapattıysanız, projenizde bir *. pubxml dosyası olan yayımlama profilini düzenleyebilir ve aşağıdaki öğeyi ekleyebilirsiniz (yalnızca test için): `<AllowUntrustedCertificate>true</AllowUntrustedCertificate>`
- uygulama Visual Studio başlamazsa, doğru şekilde dağıtıldığını test etmek için uygulamayı ııs 'de başlatın.
- durum bilgileri için Visual Studio çıkış penceresini kontrol edin ve hata iletilerinizi kontrol edin.

### <a name="open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Windows sunucuda gerekli bağlantı noktalarını açın

çoğu kurulumda, gerekli bağlantı noktaları ASP.NET yüklemesi ve uzaktan hata ayıklayıcı tarafından açılır. Ancak, dağıtım sorunlarını gidermekte ve uygulama bir güvenlik duvarının arkasında barındırılıyorsa, doğru bağlantı noktalarının açık olduğunu doğrulamanız gerekebilir.

Bir Azure VM 'de, bağlantı noktalarını [ağ güvenlik grubu](/azure/virtual-machines/windows/nsg-quickstart-portal)üzerinden açmanız gerekir.

Gerekli bağlantı noktaları:

* 80-IIS için gereklidir
::: moniker range=">=vs-2019"
* 4024-Visual Studio 2019 ' den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
::: moniker range="vs-2017"
* 4022-Visual Studio 2017 ' den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
* UDP 3702-(Isteğe bağlı) bulma bağlantı noktası, Visual Studio uzaktan hata ayıklayıcıya eklerken **bul** düğmesine erişmenizi sağlar.

ayrıca, bu bağlantı noktaları ASP.NET yüklemesi tarafından zaten açılmalıdır:
- 8172-(isteğe bağlı) Web Dağıtımı uygulamayı Visual Studio dağıtım için gerekli
