---
title: IIS ve Azure'da Uzaktan Hata Ayıklama ASP.NET Core | Microsoft Dokümanlar
ms.custom: remotedebugging
ms.date: 04/14/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 079e324f2304118c9041118c13e8ebc0cce2015c
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385504"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Visual Studio'da Azure'da IIS'de Uzaktan Hata Ayıklama ASP.NET Core

Bu kılavuz, Visual Studio ASP.NET Core uygulamasını nasıl ayarlayıp yapılandırışlanız, Azure kullanarak IIS'ye nasıl dağıtılanın ve Visual Studio'dan uzaktan hata ayıklama ekini açıklar.

Azure'da uzaktan hata ayıklama için önerilen yol senaryonuza bağlıdır:

* Azure Uygulama Hizmeti'nde ASP.NET Çekirdek hata sını ayıklamak için [Anlık Görüntü Hata Ayıklama'yı kullanarak Azure uygulamalarını hata ayıklama bölümüne](../debugger/debug-live-azure-applications.md)bakın. Bu önerilen yöntemdir.
* Daha geleneksel hata ayıklama özelliklerini kullanarak Azure Uygulama Hizmeti'nde ASP.NET Core hata ayıklama için bu konudaki adımları izleyin [(Azure Uygulama Hizmeti'ndeki Uzaktan hata ayıklama](#remote_debug_azure_app_service)bölümüne bakın).

    Bu senaryoda, uygulamanızı Visual Studio'dan Azure'a dağıtmanız gerekir, ancak aşağıdaki resimde gösterildiği gibi IIS veya uzaktan hata ayıklayıcıyı (bu bileşenler noktalı çizgilerle gösterilir) el ile yüklemeniz veya yapılandırmanız gerekmez.

    ![Uzaktan hata ayıklama bileşenleri](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Bir Azure VM'de IIS hatasını ayıklamak için bu konuyla ilgili adımları izleyin [(Azure VM'deki Uzaktan Hata Ayıklama](#remote_debug_azure_vm)bölümüne bakın). Bu, IIS'nin özelleştirilmiş yapılandırmasını kullanmanıza olanak tanır, ancak kurulum ve dağıtım adımları daha karmaşıktır.

    Azure VM için uygulamanızı Visual Studio'dan Azure'a dağıtmanız ve aşağıdaki resimde gösterildiği gibi IIS rolünü ve uzaktan hata ayıklamayı el ile yüklemeniz gerekir.

    ![Uzaktan hata ayıklama bileşenleri](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Azure Hizmet Kumaşı'nda ASP.NET Çekirdeğini hata ayıklamak için [uzaktan hizmet kumaşı uygulaması hata ayıklama](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)bölümüne bakın.

> [!WARNING]
> Bu öğreticideki adımları tamamladığınızda oluşturduğunuz Azure kaynaklarını sildiğimden emin olun. Bu şekilde gereksiz ücretlere maruz kalmanızı önleyebilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

::: moniker range=">=vs-2019"
Visual Studio 2019 bu makalede gösterilen adımları takip etmek için gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 bu makalede gösterilen adımları takip etmek için gereklidir.
::: moniker-end

### <a name="network-requirements"></a>Ağ gereksinimleri

Proxy üzerinden bağlanan iki bilgisayar arasında hata ayıklama desteklenmez. Çevirmeli Internet gibi yüksek gecikmeli veya düşük bant genişliği bağlantısı üzerinden veya ülkeler arasında Internet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya kabul edilemez derecede yavaş olabilir. Gereksinimlerin tam listesi için [Gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon)bölümüne bakın.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarında ASP.NET Core uygulamasını oluşturma

1. Yeni bir ASP.NET Core uygulaması oluşturun.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'da, arama kutusunu açmak için **Ctrl + Q** yazın, **asp.net**yazın, **Şablonlar'ı**seçin, ardından **yeni ASP.NET Core Web Uygulaması oluştur'u**seçin. Görünen iletişim kutusunda, proje **MyASPApp**adını ve sonra **Oluştur'u**seçin. Ardından, **Web Uygulaması (Model-View-Controller) seçeneğini**belirleyin ve ardından **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de **Dosya > Yeni > Projesi'ni**seçin, ardından Visual **C# > Web > ASP.NET Core Web Application'ı**seçin. ASP.NET Çekirdek şablonları bölümünde **Web Uygulaması (Model-View-Controller)** seçeneğini belirleyin. Core 2.1 ASP.NET seçildiğinden, **Docker Desteğini Etkinleştir'in** seçilmediğinden ve **Kimlik Doğrulamanın** **Kimlik Doğrulama yok**olarak ayarlandıklarına emin olun. Proje **MyASPApp**adı .
    ::: moniker-end

1. About.cshtml.cs dosyasını açın ve `OnGet` yöntemde bir kesme noktası ayarlayın (eski şablonlarda, bunun `About()` yerine HomeController.cs açın ve yöntemde kesme noktasını ayarlayın).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a>Azure Uygulama Hizmetinde Uzaktan Hata Ayıklama ASP.NET Çekirdek

Visual Studio'dan, uygulamanızı hızlı bir şekilde yayımlayabilir ve hata ayıklayabilirsiniz. Ancak, IIS yapılandırması önceden ayarlanmıştır ve bunu özelleştiremezsiniz. Daha ayrıntılı talimatlar için Visual Studio'ASP.NET kullanarak [Azure'a bir ASP.NET Core web uygulamasını dağıt'a](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)bakın. (IIS'yi özelleştirme yeteneğine ihtiyacınız varsa, [Azure VM'de](#remote_debug_azure_vm)hata ayıklamayı deneyin.)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Bulut Gezgini'ni kullanarak uygulamayı ve uzaktan hata ayıklamayı dağıtmak için

1. Visual Studio'da proje düğümüne sağ tıklayın ve **Yayımla'yı**seçin.

    Yayımlama profillerini daha önce yapılandırmışsanız, **Yayımla** bölmesi görüntülenir. **Yeni profili**tıklatın.

1. **Yayımla** iletişim kutusundan **Azure Uygulama Hizmeti'ni** seçin, **Yeni Oluştur'u**seçin ve profil oluşturmak için istemleri izleyin.

    Ayrıntılı talimatlar için Visual [Studio'ASP.NET Core web uygulamasını Azure'a dağıt'a](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)bakın.

    ![Azure App Service’e yayımlama](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Yayımla penceresinde **Yapılandırmayı Edit'i** seçin ve Hata Ayıklama yapılandırmasına geçin ve ardından **Yayımla'yı**seçin.

   Uygulamayı hata ayıklamak için hata ayıklama yapılandırması gereklidir.

1. **Bulut Gezgini'ni** Aç (**Bulut Gezginini****Görüntüle** > ), Uygulama Hizmeti örneğine sağ tıklayın ve **Hata Ayıklama'yı seçin.**

   Bulut Gezgini kullanılamıyorsa, bunun yerine Server Explorer'ı açın. Ardından, Server Explorer'daki Uygulama Hizmeti örneğine sağ tıklayın ve **Hata Ayıklama Ekle'yi**seçin.

1. Çalışan ASP.NET uygulamasında, **Hakkında** sayfasına bağlantı tıklayın.

    Kırılma noktası Visual Studio'da vurulmalıdır.

    İşte bu kadar! Bu konudaki diğer adımlar, Azure VM'de uzaktan hata ayıklama için geçerlidir.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Azure VM'de Uzaktan Hata Ayıklama ASP.NET Çekirdeği

Windows Server için bir Azure VM oluşturabilir ve ardından IIS ve diğer gerekli yazılım bileşenlerini yükleyebilir ve yapılandırabilirsiniz. Bu, bir Azure Uygulama Hizmetine dağıtmaktan daha fazla zaman alır ve bu öğreticide kalan adımları izlemenizi gerektirir.

Bu yordamlar bu sunucu yapılandırmalarında sınanmıştır:
* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Uygulama Azure VM'de IIS'de zaten çalışıyor mu?

Bu makalede, Windows sunucusunda Temel Bir IIS yapılandırması kurma ve uygulamayı Visual Studio'dan dağıtma adımları yer almaktadır. Bu adımlar, sunucunun gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırıladığından ve uzaktan hata ayıklama yapmaya hazır olduğundan emin olmak için dahildir.

* Uygulamanız IIS'de çalışıyorsa ve uzaktan hata ayıklamayı indirip hata ayıklamaya başlamak istiyorsanız, [Windows Server'daki uzak araçları indirip yükleyin.](#BKMK_msvsmon)

* Hata ayıklama yapabilmeniz için uygulamanızın IIS'de ayarlanıp dağıtıldığınızdan ve doğru şekilde çalıştırdığından emin olmak için yardım istiyorsanız, bu konuyla ilgili tüm adımları izleyin.

  * Başlamadan [önce, Yükle ve IIS'yi çalıştır'da](/azure/virtual-machines/windows/quick-create-portal)açıklanan tüm adımları izleyin.

  * Ağ güvenlik grubunda 80 bağlantı noktasını açtığınızda, uzaktan hata ayıklayıcı (4024 veya 4022) için [doğru bağlantı noktasını](#bkmk_openports) da açın. Böylece daha sonra açmak zorunda kalmazsın.

### <a name="update-browser-security-settings-on-windows-server"></a>Windows Server'da tarayıcı güvenlik ayarlarını güncelleştirme

Gelişmiş Güvenlik Yapılandırması Internet Explorer'da etkinleştirilmişse (varsayılan olarak etkinleştirilir), bazı web sunucusu bileşenlerini karşıdan yükleyebilmeniz için bazı etki alanlarını güvenilir siteler olarak eklemeniz gerekebilir. **Güvenilen siteleri, Güvenlik > > Güvenilir Siteler > Siteler>e**giderek güvenilir siteleri ekleyin. Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı karşıdan yüklediğinizde, çeşitli web sitesi komut dosyalarını ve kaynaklarını yüklemek için izin verme isteği alabilirsiniz. Bu kaynaklardan bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle'yi** tıklatın.

### <a name="install-aspnet-core-on-windows-server"></a>Windows Server'da ASP.NET Core'u yükleme

1. Barındırma sistemine [.NET Core Windows Server Hosting](https://aka.ms/dotnetcore-2-windowshosting) paketini yükleyin. Paket ,NET Core Runtime, .NET Core Library ve ASP.NET Çekirdek Modül'üne yüklenir. Daha ayrıntılı talimatlar için [IIS'ye Yayımlama'ya](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)bakın.

    > [!NOTE]
    > Sistemin Internet bağlantısı yoksa, .NET Core Windows Server Hosting paketini yüklemeden önce *[Microsoft Visual C++ 2015 Yeniden Dağıtılabilir'i](https://www.microsoft.com/download/details.aspx?id=53840)* edinin ve yükleyin.

3. Sistemi yeniden başlatın (veya **net stop /y** sistem PATH bir değişiklik almak için bir komut istemi net **start w3svc** izledi yürütmek).

## <a name="choose-a-deployment-option"></a>Dağıtım seçeneği ni seçin

Uygulamayı IIS'ye dağıtmak için yardıma ihtiyacınız varsa, aşağıdaki seçenekleri göz önünde bulundurun:

* IIS'de bir yayımlama ayarları dosyası oluşturarak ve Visual Studio'daki ayarları içe aktararak dağıtın. Bazı senaryolarda bu, uygulamanızı dağıtmanın hızlı bir yoludur. Yayımlama ayarları dosyasını oluşturduğunuzda, izinler otomatik olarak IIS'de ayarlanır.

* Yerel bir klasöre yayımlayarak ve çıktıyı tercih edilen yöntemle IIS'de hazırlanmış bir uygulama klasörüne kopyalayarak dağıtın.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(İsteğe bağlı) Yayımlama ayarları dosyalarını kullanarak dağıtma

Bu seçeneği kullanarak bir yayımlama ayarları dosyası oluşturabilir ve Visual Studio'ya aktarabilirsiniz.

> [!NOTE]
> Bu dağıtım yöntemi Web Dağıtımı'nı kullanır. Ayarları almak yerine Visual Studio'da Web Dağıtımı'nı el ile yapılandırmak istiyorsanız, Sunucuları Barındırmak için Web Dağıtma 3.6 yerine Web Dağıtımı'nı yükleyebilirsiniz. Ancak, Web Dağıtımı'nı el ile yapılandırıyorsanız, sunucudaki bir uygulama klasöründen doğru değerler ve izinlerle yapılandırıldığından emin olmanız gerekir (bkz. [ASP.NET Web sitesini yapılandırma).](#BKMK_deploy_asp_net)

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows Server'da Sunucu Barındırma için Web Dağıtımı'nı yükleme ve yapılandırma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server'da IIS'de yayımlama ayarları dosyasını oluşturma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio'da yayımlama ayarlarını içe aktarma ve dağıtma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlamalıdır. Uygulama Visual Studio'dan başlamazsa, uygulamayı IIS'de başlatın. ASP.NET Core için, **DefaultAppPool'un** Uygulama havuzu alanının Yönetilen **Kod Yok**olarak ayarlandığınızdan emin olmanız gerekir.

1. **Ayarlar** iletişim kutusunda, **İleri'yi**tıklatarak hata ayıklamayı etkinleştirin, **hata ayıklama** yapılandırması seçin ve ardından **Dosya Yayımlama** seçenekleri altında **hedefteki ek dosyaları kaldır'ı** seçin.

    > [!NOTE]
    > Bir Sürüm yapılandırması seçerseniz, yayımladığınızda *web.config* dosyasında hata ayıklama devre dışı kağınızda.

1. **Kaydet'i** tıklatın ve ardından uygulamayı yeniden yayımlayın.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(İsteğe bağlı) Yerel bir klasöre yayımlayarak dağıtma

Uygulamayı PowerShell, RoboCopy kullanarak IIS'ye kopyalamak veya dosyaları el ile kopyalamak istiyorsanız uygulamanızı dağıtmak için bu seçeneği kullanabilirsiniz.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Windows Server bilgisayarındaki ASP.NET Core Web sitesini yapılandırma

Yayımlama ayarlarını alıyorsanız, bu bölümü atlayabilirsiniz.

1. İnternet **Bilgi Hizmetleri (IIS) Yöneticisi'ni** açın ve **Sitelere**gidin.

2. Varsayılan Web **Sitesi** düğümüne sağ tıklayın ve **Uygulama Ekle'yi**seçin.

3. Diğer **Ad** alanını **MyASPApp'a** ve Uygulama havuzu alanını **Yönetilen Kod Yok'a**ayarlayın. Fiziksel **yolu** **C:\Publish** 'e (daha sonra ASP.NET Çekirdek projesini dağıtacağınız) ayarlayın.

4. IIS Yöneticisi'nde seçilen siteyle, **İzinleri Edit'i**seçin ve Uygulama Havuzu için yapılandırılan IUSR, IIS_IUSRS veya kullanıcının Oku & Yürüt haklarına sahip yetkili bir kullanıcı olduğundan emin olun.

    Bu kullanıcılardan birini erişimi olan görmüyorsanız, Okuma & Yürüt haklarına sahip bir kullanıcı olarak IUSR eklemek için adımları izleyin.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(İsteğe bağlı) Visual Studio'dan yerel bir klasöre yayınlayarak uygulamayı yayımlayın ve dağıtın

Web Dağıtımı kullanmıyorsanız, dosya sistemini veya diğer araçları kullanarak uygulamayı yayımlamanız ve dağıtmanız gerekir. Dosya sistemini kullanarak bir paket oluşturarak başlayabilir ve paketi el ile dağıtabilir veya PowerShell, RoboCopy veya XCopy gibi diğer araçları kullanabilirsiniz. Bu bölümde, Web Dağıtımı kullanmıyorsanız paketi el ile kopyaladığınızı varsayıyoruz.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Windows Server'daki uzak araçları indirin ve yükleyin

Visual Studio sürümünüzle eşleşen uzak araçların sürümünü indirin.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Windows Server'da uzaktan hata ayıklama yı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izin eklemeniz, kimlik doğrulama modunu veya uzak hata ayıklayıcının bağlantı noktası numarasını değiştirmeniz gerekiyorsa, [bkz.](../debugger/remote-debugging.md#configure_msvsmon)

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Visual Studio bilgisayarından ASP.NET uygulamasına ekleme

1. Visual Studio bilgisayarında hata ayıklamaya çalıştığınız çözümü açın (Bu makaledeki adımları takip ediyorsanız**MyASPApp).**
2. Visual Studio'da **Hata Ayıklama > İşleme Ekle 'yi** (Ctrl + Alt + P) tıklatın.

    > [!TIP]
    > Visual Studio 2017 ve sonraki sürümlerinde, **Hata Ayıklama > İşleme Yeniden Ekle...** (Shift+Alt+P) kullanarak daha önce eklediğiniz aynı işleme yeniden bağlanabilirsiniz.

3. Eleme alanını ** \<uzak bilgisayar adı>** ayarlayın ve **Enter**tuşuna basın.

    Visual Studio'nun bilgisayar adına gerekli bağlantı noktasını eklediğine ve biçimde görünen: ** \<uzak bilgisayar adı>:port**

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'da ** \<uzak bilgisayar adını>:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de ** \<uzak bilgisayar adını>:4022**
    ::: moniker-end
    Bağlantı noktası gereklidir. Bağlantı noktası numarasını görmüyorsanız, el ile ekleyin.

4. **Yenile**'ye tıklayın.
    **Kullanılabilir İşlemler** penceresinde bazı işlemlerin göründüğünü görmeniz gerekir.

    Herhangi bir işlem görmüyorsanız, uzak bilgisayar adı yerine IP adresini kullanmayı deneyin (bağlantı noktası gereklidir). IPv4 `ipconfig` adresini almak için komut satırında kullanabilirsiniz.

    **Bul** düğmesini kullanmak istiyorsanız, sunucuda [UDP bağlantı noktası 3702'yi açmanız](#bkmk_openports) gerekebilir.

5. **Tüm kullanıcıların süreçlerini göster'i**denetleyin.

6. Uygulamanızı hızla bulmak için işlem adınızın ilk harfini yazın.

    * **dotnet.exe'yi** seçin (.NET Core için)

      **dotnet.exe'yi**gösteren birden çok işlem varsa, **Kullanıcı Adı** sütununa bakın. Bazı senaryolarda, **Kullanıcı Adı** sütunu **IIS APPPOOL\DefaultAppPool**gibi uygulama havuzu adınızı gösterir. Uygulama Havuzu'nu görürseniz, doğru işlemi belirlemenin kolay bir yolu hata ayıklamak istediğiniz uygulama örneği için yeni bir Uygulama Havuzu oluşturmaktır ve ardından **kullanıcı adı** sütununda kolayca bulabilirsiniz.

    * Bazı IIS senaryolarında, Uygulama adınızı **MyASPApp.exe**gibi işlem listesinde bulabilirsiniz. Bunun yerine bu işleme ekleyebilirsiniz.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **Ekle'yi**tıklatın.

8. Uzak bilgisayarın web sitesini açın. Bir tarayıcıda, **uzak\<http:// bilgisayar adı>** gidin.

    ASP.NET web sayfasını görmelisiniz.
9. Çalışan ASP.NET uygulamasında, **Hakkında** sayfasına bağlantı tıklayın.

    Kırılma noktası Visual Studio'da vurulmalıdır.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Sorun giderme: Windows Server'da gerekli bağlantı noktalarını açma

Çoğu kurulumda, gerekli bağlantı noktaları ASP.NET ve uzaktan hata ayıklama nın yüklenmesiyle açılır. Ancak, dağıtım sorunlarını giderirseniz ve uygulama bir güvenlik duvarının arkasında barındırılıyorsa, doğru bağlantı noktalarının açık olduğunu doğrulamanız gerekebilir.

Azure VM'de, Ağ güvenlik [grubu](/azure/virtual-machines/windows/nsg-quickstart-portal)aracılığıyla bağlantı noktalarını açmanız gerekir.

Gerekli bağlantı noktaları:

* 80 - IIS için gerekli
::: moniker range=">=vs-2019"
* 4024 - Visual Studio 2019'dan uzaktan hata ayıklama için gereklidir (daha fazla bilgi için [Uzaktan Hata Ayıklama Bağlantı Noktası Atamaları'na](../debugger/remote-debugger-port-assignments.md) bakın).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Visual Studio 2017'den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için [Uzaktan Hata Ayıklama Bağlantı Noktası Atamaları'na](../debugger/remote-debugger-port-assignments.md) bakın).
::: moniker-end
* UDP 3702 - (İsteğe bağlı) Discovery bağlantı noktası, Visual Studio'daki uzaktan hata ayıklamaya takarken **Bul** düğmesine basmanızı sağlar.

Buna ek olarak, bu bağlantı noktaları zaten ASP.NET yükleme tarafından açılmalıdır:
- 8172 - (İsteğe bağlı) Visual Studio'dan uygulamayı dağıtmak için Web Dağıtımı için gereklidir
