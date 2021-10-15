---
title: ııs ve Azure 'da uzaktan hata ayıklama ASP.NET Core | Microsoft Docs
description: Visual Studio ASP.NET Core uygulamasını ayarlamayı ve yapılandırmayı, Azure kullanarak ııs 'ye dağıtmayı ve Visual Studio uzaktan hata ayıklayıcıyı eklemeyi öğrenin.
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
ms.openlocfilehash: 148daa4649e3b5280b61e6223c07fef328ef8be6
ms.sourcegitcommit: 485f0f6f578568ee31b2ac093e32a6d01dc9c1c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130016036"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Visual Studio 'de Azure 'da ııs 'de uzaktan hata ayıklama ASP.NET Core

bu kılavuzda, bir Visual Studio ASP.NET Core uygulamasının nasıl ayarlanacağı ve yapılandırılacağı, Azure kullanarak ııs 'e nasıl dağıtılacağı ve uzaktan hata ayıklayıcıyı Visual Studio nasıl ekleneceği açıklanmaktadır.

IIS senaryolarında Linux desteklenmez.

Azure 'da uzaktan hata ayıklama için önerilen yol, senaryonuza bağlıdır:

* Azure App Service ASP.NET Core hata ayıklamak için bkz. [Snapshot Debugger kullanarak Azure uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md). Önerilen yöntem budur.
* daha geleneksel hata ayıklama özelliklerini kullanarak Azure App Service ASP.NET Core hata ayıklamak için, bu konudaki adımları izleyin (bkz. [Azure App Service üzerinde uzaktan hata ayıklama](#remote_debug_azure_app_service)bölümü).

    bu senaryoda, uygulamanızı Visual Studio Azure 'a dağıtmanız gerekir, ancak ııs veya uzaktan hata ayıklayıcıyı el ile yüklemeniz veya yapılandırmanız gerekmez (bu bileşenler noktalı çizgilerle gösterilir) ve aşağıdaki çizimde gösterildiği gibi.

    ![Visual Studio, Azure App Service ve bir ASP.NET uygulaması arasındaki ilişkiyi gösteren diyagram. IIS ve uzaktan hata ayıklayıcı noktalı çizgiler ile temsil edilir.](../debugger/media/remote-debugger-azure-app-service.png)

* Azure VM 'de IIS 'de hata ayıklamak için bu konudaki adımları izleyin (bkz. [Azure VM 'de uzaktan hata ayıklama](#remote_debug_azure_vm)bölümü). Bu, IIS 'in özelleştirilmiş bir yapılandırmasını kullanmanızı sağlar, ancak kurulum ve dağıtım adımları daha karmaşıktır.

    azure VM 'de, uygulamanızı Visual Studio azure 'a dağıtmanız gerekir ve ayrıca aşağıdaki çizimde gösterildiği gibi ııs rolünü ve uzaktan hata ayıklayıcıyı el ile yüklemeniz gerekir.

    ![Visual Studio, bir Azure VM ve ASP.NET uygulaması arasındaki ilişkiyi gösteren diyagram. IIS ve uzaktan hata ayıklayıcı katı satırlarla temsil edilir.](../debugger/media/remote-debugger-azure-vm.png)

* Azure Service Fabric üzerinde ASP.NET Core hata ayıklamak için bkz. [uzak Service Fabric uygulamasında hata ayıklama](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Bu öğreticideki adımları tamamladığınızda oluşturduğunuz Azure kaynaklarını sildiğinizden emin olun. Bu şekilde, gereksiz ücretleri kullanmaktan kaçınabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"
Visual Studio 2019 veya sonraki sürümler bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end

### <a name="network-requirements"></a>Ağ gereksinimleri

Proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmez. Yüksek gecikme veya düşük bant genişliğine sahip bir bağlantı (örneğin, Internet veya ülkeler arasında Internet üzerinden) için hata ayıklama önerilmez ve başarısız olabilir veya aşırı derecede yavaş olabilir. Gereksinimlerin tüm listesi için bkz. [gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarda ASP.NET Core uygulamasını oluşturma

1. yeni bir ASP.NET Core web uygulaması oluşturun.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de, başlangıç penceresinde **yeni proje oluştur** ' u seçin. Başlangıç penceresi açık değilse **Dosya**  >  **Başlangıç penceresi**' ni seçin. **web** uygulaması yazın, dil olarak **C#** ' yi seçin, ardından **ASP.NET Core web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **ileri**' yi seçin. Sonraki ekranda, **Myaspapp** projesini adlandırın ve ardından **İleri**' yi seçin.

    Önerilen hedef Framework veya .NET 6 ' ı seçin ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de **dosya > yeni > Project**' i seçin, sonra **Visual C# > web > ASP.NET Core web uygulaması**' nı seçin. ASP.NET Core şablonları bölümünde **Web uygulaması (Model-View-Controller)** öğesini seçin. ASP.NET Core 2,1 ' nin seçildiğinden emin olun, **docker desteğinin etkinleştirilmesi** ve **kimlik** doğrulamasının **kimlik doğrulaması yok** olarak ayarlandığından emin olun. Projeyi **Myaspapp** olarak adlandırın.
    ::: moniker-end

1. . Cshtml. cs dosyasını açın ve yöntemde bir kesme noktası ayarlayın `OnGet` (eski şablonlarda, bunun yerine HomeController. cs dosyasını açın ve yönteminde kesme noktasını ayarlayın `About()` ).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service-windows"></a><a name="remote_debug_azure_app_service"></a>Azure App Service üzerinde uzaktan hata ayıklama ASP.NET Core (Windows)

Visual Studio, ııs 'nin tam olarak sağlanan bir örneğini temel alan Windows Azure App Service için uygulamanızı hızlı bir şekilde yayımlayabilir ve hata ayıklayabilirsiniz. IIS 'yi bir VM 'de barındırıyorsanız, bir [Azure VM](#remote_debug_azure_vm)'de hata ayıklamayı deneyin.)

::: moniker range=">= vs-2022"

1. Yayımla penceresini kullanarak Azure App Service için bir yayımlama profili oluşturun.

1. Profilde, **barındırma** altındaki **...** menüsünü seçin. **Hata ayıklayıcı Ekle** seçeneğini belirleyin.

   Visual Studio, uzak hata ayıklayıcıyı profilin yayımlamakta olduğu Azure App Service (Windows) örneğine iliştirmeye çalışır.

   :::image type="content" source="../debugger/media/attach-debugger-publish-profile.png" alt-text="Yayımlama Özeti sayfasının içinden hata ayıklayıcı ekle seçeneğinin ekran görüntüsü.":::

> [!NOTE]
> Visual Studio 2022 ' de, Cloud Explorer kullanım dışıdır. Bulut Gezgini, uzaktan hata ayıklama Azure App Service önceki yöntemini sağladı.

::: moniker-end
::: moniker range="<= vs-2019"
#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Cloud Explorer 'ı kullanarak uygulamayı ve uzaktan hata ayıklamayı dağıtmak için

1. Visual Studio, proje düğümüne sağ tıklayın ve **yayımla**' yı seçin.

    Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** bölmesi görüntülenir. **Yeni** ya da **Yeni profil**' i seçin.

1. Yeni bir yayımlama profili oluşturun.

    **Yayımla** Iletişim kutusundan **Azure** ' u seçin ve **İleri ' yi** seçin. **Azure App Service (Windows)** öğesini seçin, **ileri**' yi seçin ve bir profil oluşturmak için istemleri izleyin.

    ![Visual Studio kullanarak Azure’a bir ASP.NET Core web uygulaması dağıtın](../debugger/media/vs-2019/remotedbg-azure-app-service-profile.png)

    Visual Studio 2017 ' de, **yayımla** iletişim kutusunda **Azure App Service** ' i seçin, **yeni oluştur**' u seçin ve bir profil oluşturmak için istemleri izleyin.

    daha ayrıntılı yönergeler için bkz. [Visual Studio kullanarak Azure 'a ASP.NET Core web uygulaması dağıtma](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

1. Yayımla penceresinde **yapılandırmayı Düzenle** ' yi seçin ve bir hata ayıklama yapılandırmasına geçin ve ardından **Yayımla**' yı seçin.

   Uygulamada hata ayıklamak için bir hata ayıklama yapılandırması gerekir.

1. **Cloud Explorer 'ı** açın ( > **bulut Gezginini** görüntüleyin), App Service örneğine sağ tıklayıp **hata ayıklayıcı Ekle**' yi seçin.

   Bulut Gezgini yoksa, bunun yerine Sunucu Gezgini açın. Sonra, Sunucu Gezgini App Service örneğine sağ tıklayın ve **hata ayıklayıcı Ekle**' yi seçin.

1. çalışan ASP.NET uygulamasında, **hakkında** sayfasına yönelik bağlantıya tıklayın.

    Kesme noktasının Visual Studio isabet etmesi gerekir.

    İşte bu kadar! Bu konudaki adımların geri kalanı, bir Azure sanal makinesinde uzaktan hata ayıklama için geçerlidir.

::: moniker-end

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Azure VM 'de uzaktan hata ayıklama ASP.NET Core

Windows sunucusu için bir Azure VM oluşturabilir ve ardından ııs 'yi ve diğer gerekli yazılım bileşenlerini yükleyip yapılandırabilirsiniz. Bu, bir Azure App Service dağıtmaya kıyasla daha fazla zaman alır ve bu öğreticideki kalan adımları izlemenizi gerektirir.

Bu yordamlar, bu sunucu yapılandırmalarında test edilmiştir:

* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve ııs 10
* Windows Sunucu 2019 ve IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Uygulama Azure VM 'de zaten IIS 'de çalışıyor mu?

bu makale, Windows sunucuda ııs 'nin temel yapılandırmasını ayarlama ve uygulamayı Visual Studio dağıtma adımlarını içerir. Bu adımlar, sunucuda gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırılabilmesi ve uzaktan hata ayıklama için hazırsanız emin olmak için eklenmiştir.

* uygulamanız ııs 'de çalışıyorsa ve yalnızca uzaktan hata ayıklayıcıyı indirmek ve hata ayıklamayı başlatmak istiyorsanız, [uzak araçları Windows sunucusuna indir ve yükle](#BKMK_msvsmon)' ye gidin.

* Uygulamanızın Hata ayıklayabilmeniz, dağıtılması ve IIS 'de doğru şekilde çalıştığından emin olmak istiyorsanız, bu konudaki tüm adımları izleyin.

  * başlamadan önce, ııs web sunucusunu yüklemeye yönelik adımları içeren [Windows sanal makinesi oluşturma](/azure/virtual-machines/windows/quick-create-portal)bölümünde açıklanan tüm adımları izleyin.

  * Azure [ağ güvenlik grubunda](/azure/virtual-machines/windows/nsg-quickstart-portal)80 numaralı bağlantı noktasını açtığınızdan emin olun. 80 bağlantı noktasının açık olduğunu doğruladıktan sonra, uzaktan hata ayıklayıcı için [doğru bağlantı noktasını](#bkmk_openports) açın (4026, 4024 veya 4022). Bu şekilde, daha sonra açmanız gerekmez. Web Dağıtımı kullanıyorsanız, 8172 numaralı bağlantı noktasını da açın.

### <a name="update-browser-security-settings-on-windows-server"></a>Windows sunucuda tarayıcı güvenlik ayarlarını güncelleştir

Internet Explorer 'da artırılmış güvenlik yapılandırması etkinse (varsayılan olarak etkindir), Web sunucusu bileşenlerinden bazılarını indirmeniz için bazı etki alanlarını güvenilen siteler olarak eklemeniz gerekebilir. Güvenilen siteleri, **güvenlik > güvenilen siteler > siteleri > Internet seçeneklerine** giderek ekleyin. Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı indirdiğinizde, çeşitli web sitesi betikleri ve kaynakları yüklemek için izin verme istekleri alabilirsiniz. Bu kaynaklardan bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle** ' ye tıklayın.

### <a name="install-aspnet-core-on-windows-server"></a>Windows sunucusuna ASP.NET Core yüklemesi

1. .NET Core barındırma paketi 'ni barındırma sistemine yükler. paket, .net core çalışma zamanı, .net core kitaplığı ve ASP.NET Core modülünü de yüklüyor. Daha ayrıntılı yönergeler için bkz. IIS 'de [Yayımlama](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    geçerli .net Core barındırma paketi için [ASP.NET Core barındırma paketi](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)' ni yükler.
    .net core 2 için, [.net core Windows sunucusu barındırma](https://aka.ms/dotnetcore-2-windowshosting)' i yükler.

    > [!NOTE]
    > sistemin Internet bağlantısı yoksa, .net Core Windows Server barındırma paketi 'ni yüklemeden önce *[Microsoft Visual C++ 2015 yeniden dağıtılabilir](https://www.microsoft.com/download/details.aspx?id=53840)* sürümünü edinin ve yükleme.

2. Sistemi yeniden başlatın (veya **net stop was/y** ' i yürütün ve ardından sistem yolunda bir değişiklik yapmak için bir komut isteminden net **start w3svc** ' i çalıştırın).

## <a name="choose-a-deployment-option"></a>Dağıtım seçeneği seçin

Uygulamayı IIS 'ye dağıtmak için yardıma ihtiyacınız varsa, şu seçenekleri göz önünde bulundurun:

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

    ::: moniker range=">=vs-2022"
    Visual Studio 2022 ' de şunları görmeniz gerekir **\<remote computer name> : 4026**
    ::: moniker-end
    ::: moniker range="vs-2019"
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
::: moniker range=">=vs-2022"
* 4026-Visual Studio 2022 ' den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
::: moniker range="vs-2019"
* 4024-Visual Studio 2019 ' den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Visual Studio 2017'den uzaktan hata ayıklama için gereklidir [(daha](../debugger/remote-debugger-port-assignments.md) fazla bilgi için bkz. Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları).
::: moniker-end
* UDP 3702 - (İsteğe bağlı)  Bulma bağlantı noktası, hata ayıklayıcısında uzak hata ayıklayıcıya iliştirme sırasında Bul Visual Studio.

Ayrıca, bu bağlantı noktaları yüklemesi tarafından ASP.NET gerekir:
- 8172 - (İsteğe bağlı) Uygulamayı Web Dağıtımı dağıtmak için Visual Studio
