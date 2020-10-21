---
title: IIS ve Azure 'da uzaktan hata ayıklama ASP.NET Core | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 926bd4a6630d9d99726ee6c1479d04c476756c18
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "92298743"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Visual Studio 'da Azure 'da IIS 'de uzaktan hata ayıklama ASP.NET Core

Bu kılavuzda, Visual Studio ASP.NET Core uygulamasını ayarlama ve yapılandırma, Azure kullanarak IIS 'ye dağıtma ve Visual Studio 'dan uzaktan hata ayıklayıcıyı iliştirme açıklanmaktadır.

Azure 'da uzaktan hata ayıklama için önerilen yol, senaryonuza bağlıdır:

* Azure App Service ASP.NET Core hata ayıklamak için bkz. [Snapshot Debugger kullanarak Azure uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md). Önerilen yöntem budur.
* Daha geleneksel hata ayıklama özelliklerini kullanarak Azure App Service ASP.NET Core hata ayıklamak için, bu konudaki adımları izleyin (bkz. [Azure App Service üzerinde uzaktan hata ayıklama](#remote_debug_azure_app_service)bölümü).

    Bu senaryoda, uygulamanızı Visual Studio 'dan Azure 'a dağıtmanız gerekir, ancak aşağıdaki çizimde gösterildiği gibi IIS veya uzaktan hata ayıklayıcıyı el ile yüklemeniz veya yapılandırmanız gerekmez (Bu bileşenler noktalı çizgilerle temsil edilir).

    ![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Azure VM 'de IIS 'de hata ayıklamak için bu konudaki adımları izleyin (bkz. [Azure VM 'de uzaktan hata ayıklama](#remote_debug_azure_vm)bölümü). Bu, IIS 'in özelleştirilmiş bir yapılandırmasını kullanmanızı sağlar, ancak kurulum ve dağıtım adımları daha karmaşıktır.

    Bir Azure VM için uygulamanızı Visual Studio 'dan Azure 'a dağıtmanız ve ayrıca aşağıdaki çizimde gösterildiği gibi IIS rolünü ve uzaktan hata ayıklayıcıyı el ile yüklemeniz gerekir.

    ![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Azure Service Fabric üzerinde ASP.NET Core hata ayıklamak için bkz. [uzak Service Fabric uygulamasında hata ayıklama](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Bu öğreticideki adımları tamamladığınızda oluşturduğunuz Azure kaynaklarını sildiğinizden emin olun. Bu şekilde, gereksiz ücretleri kullanmaktan kaçınabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

::: moniker range=">=vs-2019"
Visual Studio 2019, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end

### <a name="network-requirements"></a>Ağ gereksinimleri

Proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmez. Yüksek gecikme veya düşük bant genişliğine sahip bir bağlantı (örneğin, Internet veya ülkeler arasında Internet üzerinden) için hata ayıklama önerilmez ve başarısız olabilir veya aşırı derecede yavaş olabilir. Gereksinimlerin tüm listesi için bkz. [gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarında ASP.NET Core uygulamasını oluşturma

1. Yeni bir ASP.NET Core uygulaması oluşturun.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de **CTRL + Q** yazarak arama kutusunu açın, **ASP.net**yazın, **Şablonlar**' ı seçin ve sonra **Yeni ASP.NET Core Web uygulaması oluştur**' u seçin. Görüntülenen iletişim kutusunda, projeyi **Myaspapp**olarak adlandırın ve ardından **Oluştur**' u seçin. Ardından **Web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de **dosya > yeni > proje**' yi seçin ve ardından **Visual C# > web > ASP.NET Core Web uygulaması**' nı seçin. ASP.NET Core Şablonları bölümünde **Web uygulaması (Model-View-Controller)** öğesini seçin. ASP.NET Core 2,1 ' nin seçildiğinden emin olun, **Docker desteğinin etkinleştirilmesi** ve **kimlik** doğrulamasının **kimlik doğrulaması yok**olarak ayarlandığından emin olun. Projeyi **Myaspapp**olarak adlandırın.
    ::: moniker-end

1. About.cshtml.cs dosyasını açın ve yöntemde bir kesme noktası ayarlayın `OnGet` (eski şablonlarda, bunun yerine HomeController.cs ' yi açın ve yöntemde kesme noktasını ayarlayın `About()` ).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a> Azure App Service uzaktan hata ayıklama ASP.NET Core

Visual Studio 'da uygulamanızı hızlı bir şekilde sağlanan bir IIS örneğine hızlıca yayımlayabilir ve hata ayıklayabilirsiniz. Ancak, IIS yapılandırması önceden ayarlanmış olur ve bunu özelleştiremezsiniz. Daha ayrıntılı yönergeler için bkz. [Visual Studio kullanarak Azure 'a ASP.NET Core Web uygulaması dağıtma](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (IIS 'yi özelleştirme olanağına ihtiyacınız varsa, bir [Azure VM](#remote_debug_azure_vm)'de hata ayıklamayı deneyin.)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Cloud Explorer 'ı kullanarak uygulamayı ve uzaktan hata ayıklamayı dağıtmak için

1. Visual Studio 'da proje düğümüne sağ tıklayın ve **Yayımla**' yı seçin.

    Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** bölmesi görüntülenir. **Yeni profil**' e tıklayın.

1. **Yayımla** iletişim kutusundan **Azure App Service** öğesini seçin, **Yeni oluştur**' u seçin ve bir profil oluşturmak için istemleri izleyin.

    Ayrıntılı yönergeler için bkz. [Visual Studio kullanarak Azure 'da ASP.NET Core Web uygulaması dağıtma](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Azure App Service’e yayımlama](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Yayımla penceresinde **yapılandırmayı Düzenle** ' yi seçin ve bir hata ayıklama yapılandırmasına geçin ve ardından **Yayımla**' yı seçin.

   Uygulamada hata ayıklamak için bir hata ayıklama yapılandırması gerekir.

1. **Cloud Explorer 'ı** açın**View**(  >  **bulut Gezginini**görüntüleyin), App Service örneğine sağ tıklayıp **hata ayıklayıcı Ekle**' yi seçin.

   Bulut Gezgini yoksa, bunun yerine Sunucu Gezgini açın. Sonra, Sunucu Gezgini App Service örneğine sağ tıklayın ve **hata ayıklayıcı Ekle**' yi seçin.

1. Çalışan ASP.NET uygulamasında **hakkında** sayfasına tıklayın.

    Kesme noktası Visual Studio 'da isabet almalıdır.

    İşte bu kadar! Bu konudaki adımların geri kalanı, bir Azure sanal makinesinde uzaktan hata ayıklama için geçerlidir.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a> Azure VM 'de uzaktan hata ayıklama ASP.NET Core

Windows Server için bir Azure VM oluşturabilir, ardından IIS 'yi ve diğer gerekli yazılım bileşenlerini yükleyip yapılandırabilirsiniz. Bu, bir Azure App Service dağıtmaya kıyasla daha fazla zaman alır ve bu öğreticideki kalan adımları izlemenizi gerektirir.

Bu yordamlar, bu sunucu yapılandırmalarında test edilmiştir:
* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve IIS 10
* Windows Server 2019 ve IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Uygulama Azure VM 'de zaten IIS 'de çalışıyor mu?

Bu makalede, Windows Server 'da IIS 'nin temel yapılandırmasını ayarlama ve uygulamayı Visual Studio 'dan dağıtma adımları yer alır. Bu adımlar, sunucuda gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırılabilmesi ve uzaktan hata ayıklama için hazırsanız emin olmak için eklenmiştir.

* Uygulamanız IIS 'de çalışıyorsa ve yalnızca uzaktan hata ayıklayıcıyı indirmek ve hata ayıklamayı başlatmak istiyorsanız, [Windows Server 'da uzak araçları indirme ve yükleme](#BKMK_msvsmon)bölümüne gidin.

* Uygulamanızın Hata ayıklayabilmeniz, dağıtılması ve IIS 'de doğru şekilde çalıştığından emin olmak istiyorsanız, bu konudaki tüm adımları izleyin.

  * Başlamadan önce, [IIS 'Yi yükleyip çalıştırma](/azure/virtual-machines/windows/quick-create-portal)bölümünde açıklanan tüm adımları izleyin.

  * Ağ güvenlik grubunda 80 numaralı bağlantı noktasını açtığınızda, uzaktan hata ayıklayıcı için [doğru bağlantı noktasını](#bkmk_openports) da açın (4024 veya 4022). Bu şekilde, daha sonra açmanız gerekmez. Web Dağıtımı kullanıyorsanız, 8172 numaralı bağlantı noktasını da açın.

### <a name="update-browser-security-settings-on-windows-server"></a>Windows Server 'da tarayıcı güvenlik ayarlarını güncelleştirme

Internet Explorer 'da artırılmış güvenlik yapılandırması etkinse (varsayılan olarak etkindir), Web sunucusu bileşenlerinden bazılarını indirmeniz için bazı etki alanlarını güvenilen siteler olarak eklemeniz gerekebilir. Güvenilen siteleri, **güvenlik > güvenilen siteler > siteleri > Internet seçeneklerine**giderek ekleyin. Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı indirdiğinizde, çeşitli web sitesi betikleri ve kaynakları yüklemek için izin verme istekleri alabilirsiniz. Bu kaynaklardan bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle** ' ye tıklayın.

### <a name="install-aspnet-core-on-windows-server"></a>Windows Server 'a ASP.NET Core yüklemesi

1. .NET Core barındırma paketi 'ni barındırma sistemine yükler. Paket, .NET Core çalışma zamanı, .NET Core kitaplığı ve ASP.NET Core modülünü de yüklüyor. Daha ayrıntılı yönergeler için bkz. IIS 'de [Yayımlama](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    .NET Core 3 için [.NET Core barındırma paketi](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)' ni yükler.
    .NET Core 2 için [.NET Core Windows Server barındırmayı](https://aka.ms/dotnetcore-2-windowshosting)yükler.

    > [!NOTE]
    > Sistemin bir Internet bağlantısı yoksa, .NET Core Windows Server barındırma paketi 'ni yüklemeden önce *[Microsoft Visual C++ 2015 yeniden dağıtılabilir](https://www.microsoft.com/download/details.aspx?id=53840)* sürümünü edinin ve yükleme.

3. Sistemi yeniden başlatın (veya **net stop was/y** ' i yürütün ve ardından sistem yolunda bir değişiklik yapmak için bir komut isteminden net **start w3svc** ' i çalıştırın).

## <a name="choose-a-deployment-option"></a>Dağıtım seçeneği seçin

Uygulamayı IIS 'ye dağıtmak için yardıma ihtiyacınız varsa, şu seçenekleri göz önünde bulundurun:

* IIS 'de bir yayımlama ayarları dosyası oluşturarak ve ayarları Visual Studio 'da içeri aktararak dağıtın. Bazı senaryolarda bu, uygulamanızı dağıtmanın hızlı bir yoludur. Yayınlama ayarları dosyasını oluştururken, izinler IIS 'de otomatik olarak ayarlanır.

* Yerel bir klasöre yayımlayarak ve çıktıyı tercih edilen bir yönteme IIS üzerindeki hazırlanmış bir uygulama klasörüne kopyalayarak dağıtın.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Seçim Yayımlama ayarları dosyası kullanarak dağıtma

Bu seçeneği kullanarak bir yayımlama ayarları dosyası oluşturabilir ve Visual Studio 'ya aktarabilirsiniz.

> [!NOTE]
> Bu dağıtım yöntemi, sunucuda yüklü olması gereken Web Dağıtımı kullanır. Ayarları içeri aktarmak yerine Web Dağıtımı el ile yapılandırmak istiyorsanız, barındırma sunucuları için Web Dağıtımı 3,6 yerine Web Dağıtımı 3,6 yükleyebilirsiniz. Ancak Web Dağıtımı el ile yapılandırırsanız, sunucudaki bir uygulama klasörünün doğru değerler ve izinlerle yapılandırıldığından emin olmanız gerekir (bkz. [configure ASP.NET Web site](#BKMK_deploy_asp_net)).

### <a name="configure-the-aspnet-core-web-site"></a>ASP.NET Core Web sitesini yapılandırma

1. IIS Yöneticisi 'nde, sol bölmedeki **Bağlantılar**altında **uygulama havuzları**' nı seçin. **DefaultAppPool** ' i açın ve **.NET CLR sürümünü** **yönetilen kod olmadan**ayarlayın. ASP.NET Core için bu gereklidir. Varsayılan Web sitesi, DefaultAppPool 'yi kullanır.

2. DefaultAppPool öğesini durdurup yeniden başlatın.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows Server 'da barındırma sunucuları için Web Dağıtımı yükleyip yapılandırın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server 'da IIS 'de yayımlama ayarları dosyası oluşturma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio 'da yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> Bir Azure VM 'yi yeniden başlatırsanız, IP adresi değişebilir.

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlamalıdır. Uygulama Visual Studio 'dan başlamazsa, düzgün çalıştığını doğrulamak için uygulamayı IIS 'de başlatın. ASP.NET Core için, **DefaultAppPool** için uygulama havuzu alanının **yönetilen kod yok**olarak ayarlandığından emin olmanız gerekir.

1. **Ayarlar** iletişim kutusunda, **İleri**' ye tıklayarak hata ayıklamayı etkinleştirin, **hata ayıklama** yapılandırması ' nı seçin ve ardından **dosya yayımlama** seçenekleri altında **Hedefteki ek dosyaları Kaldır** ' ı seçin.

    > [!IMPORTANT]
    > Bir yayın yapılandırması seçerseniz, ' ı yayımladığınızda *web.config* dosyasında hata ayıklamayı devre dışı bırakabilirsiniz.

1. **Kaydet** ' e tıklayın ve uygulamayı yeniden yayımlayın.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Seçim Yerel bir klasöre yayımlayarak dağıtma

Uygulamayı PowerShell, RoboCopy kullanarak IIS 'e kopyalamak istiyorsanız veya dosyaları el ile kopyalamak istiyorsanız uygulamanızı dağıtmak için bu seçeneği kullanabilirsiniz.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Windows Server bilgisayarında ASP.NET Core Web sitesini yapılandırma

Yayımlama ayarlarını içeri aktarıyorsanız, bu bölümü atlayabilirsiniz.

1. **Internet Information Services (IIS) Yöneticisi** ' ni açın ve **siteler**' e gidin.

2. **Varsayılan Web sitesi** düğümüne sağ tıklayın ve **Uygulama Ekle**' yi seçin.

3. **Diğer ad** alanını **Myaspapp** ve uygulama havuzu alanına **yönetilen kod yok**olarak ayarlayın. **Fiziksel yolu** **C:\publish** olarak ayarlayın (ASP.NET Core projeyi daha sonra dağıtacaksınız).

4. IIS Yöneticisi 'nde site seçiliyken, **Izinleri Düzenle**' yi seçin ve uygulama havuzu için yapılandırılmış ıusr, IIS_IUSRS veya kullanıcının okuma & yürütme haklarına sahip yetkili bir kullanıcı olduğundan emin olun.

    Erişim izni olan bu kullanıcılardan birini görmüyorsanız, okuma & yürütme hakları olan bir kullanıcı olarak ıUSR ekleme adımlarını izleyin.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Seçim Visual Studio 'dan yerel bir klasöre yayımlayarak uygulamayı yayımlayın ve dağıtın

Web Dağıtımı kullanmıyorsanız, dosya sistemini veya diğer araçları kullanarak uygulamayı yayımlamanız ve dağıtmanız gerekir. Dosya sistemini kullanarak bir paket oluşturarak başlayabilir ve ardından paketi el ile dağıtabilir ya da PowerShell, RoboCopy ya da XCopy gibi diğer araçları kullanabilirsiniz. Bu bölümde, Web Dağıtımı kullanmıyorsanız paketi el ile kopyaladığınızı varsaytık.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Windows Server 'da uzak araçları indirme ve yükleme

Visual Studio sürümünüz ile eşleşen uzak araçların sürümünü indirin.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Windows Server 'da uzaktan hata ayıklayıcı 'yı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izinler eklemeniz gerekiyorsa, kimlik doğrulama modunu veya uzaktan hata ayıklayıcı bağlantı noktası numarasını değiştirin, bkz. [Uzaktan hata ayıklayıcıyı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Visual Studio bilgisayarından ASP.NET uygulamasına iliştirme

1. Visual Studio bilgisayarında, hata ayıklamaya çalıştığınız çözümü açın (Bu makaledeki adımları takip ediyorsanız,**Myaspapp** ).
2. Visual Studio 'da, **Işleme eklemek > hata ayıkla** ' ya tıklayın (Ctrl + Alt + P).

    > [!TIP]
    > Visual Studio 2017 ve sonraki sürümlerinde, **hata ayıkla > işlem...** (SHIFT + alt + P) kullanarak daha önce eklediğiniz işleme yeniden iliştirebilirsiniz.

3. Niteleyici alanını olarak ayarlayın **\<remote computer name>** ve **ENTER**tuşuna basın.

    Visual Studio 'Nun gerekli bağlantı noktasını bilgisayar adına eklediğini doğrulayın ve şu biçimde görünür: ** \<remote computer name> :p ort**

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de şunları görmeniz gerekir ** \<remote computer name> : 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de şunları görmeniz gerekir ** \<remote computer name> : 4022**
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

    *w3wp.exe* veya *dotnet.exe*gösteren birden çok Işlem varsa, **Kullanıcı adı** sütununu kontrol edin. Bazı senaryolarda, **Kullanıcı adı** sütunu **IIS APPPOOL\DefaultAppPool**gibi uygulama havuzu adınızı gösterir. Uygulama havuzunu görürseniz, ancak benzersiz değilse, hata ayıklamak istediğiniz uygulama örneği için yeni bir adlandırılmış uygulama havuzu oluşturun ve ardından **Kullanıcı adı** sütununda kolayca bulabilirsiniz.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **Ekle**' ye tıklayın.

8. Uzak bilgisayarın Web sitesini açın. Bir tarayıcıda **http:// \<remote computer name> **adresine gidin.

    ASP.NET Web sayfasını görmeniz gerekir.
9. Çalışan ASP.NET uygulamasında **hakkında** sayfasına tıklayın.

    Kesme noktası Visual Studio 'da isabet almalıdır.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Sorun giderme: gerekli bağlantı noktalarını Windows Server 'da aç

Çoğu kurulumda, gerekli bağlantı noktaları ASP.NET ve uzaktan hata ayıklayıcı yüklemesi tarafından açılır. Ancak, dağıtım sorunlarını gidermekte ve uygulama bir güvenlik duvarının arkasında barındırılıyorsa, doğru bağlantı noktalarının açık olduğunu doğrulamanız gerekebilir.

Bir Azure VM 'de, bağlantı noktalarını [ağ güvenlik grubu](/azure/virtual-machines/windows/nsg-quickstart-portal)üzerinden açmanız gerekir.

Gerekli bağlantı noktaları:

* 80-IIS için gereklidir
::: moniker range=">=vs-2019"
* 4024-Visual Studio 2019 uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
::: moniker range="vs-2017"
* 4022-Visual Studio 2017 uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
* UDP 3702-(Isteğe bağlı) bulma bağlantı noktası, Visual Studio 'da uzaktan hata ayıklayıcıya eklerken **bul** düğmesine erişmenizi sağlar.

Ayrıca, bu bağlantı noktaları ASP.NET yüklemesi tarafından zaten açılmalıdır:
- 8172-(isteğe bağlı) uygulamayı Visual Studio 'dan dağıtmak için Web Dağıtımı gerekir
