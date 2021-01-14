---
title: Uzak IIS bilgisayarında uzaktan hata ayıklama ASP.NET Core | Microsoft Docs
description: Visual Studio uzaktan hata ayıklayıcı kullanılarak uzak bir Internet Information Services (IIS) bilgisayara dağıtılan ASP.NET Core bir uygulamada hata ayıklayın.
ms.custom: remotedebugging, SEO-VS-2020
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: bc746d5139b897d51d4d038f077906f56aa5d552
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205820"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Visual Studio 'da uzak IIS bilgisayarında uzaktan hata ayıklama ASP.NET Core

IIS 'ye dağıtılan ASP.NET Core bir uygulamada hata ayıklamak için, uzak araçları uygulamanızı dağıttığınız bilgisayara yükleyip çalıştırın ve ardından Visual Studio 'dan çalışan uygulamanıza bağlayın.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Bu kılavuzda, Visual Studio ASP.NET Core ayarlama ve yapılandırma, IIS 'ye dağıtma ve Visual Studio 'dan uzaktan hata ayıklayıcı iliştirme açıklanır. Uzaktan hata ayıklama ASP.NET 4.5.2 için, bkz. [BIR IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Ayrıca, Azure kullanarak IIS 'de dağıtabilir ve hata ayıklayabilirsiniz. Azure App Service için, önceden yapılandırılmış IIS ve uzaktan hata ayıklayıcı örneğini [Snapshot Debugger](../debugger/debug-live-azure-applications.md) kullanarak veya [Sunucu Gezgini hata ayıklayıcıyı ekleyerek](../debugger/remote-debugging-azure.md)kolayca dağıtabilir ve hata ayıklayabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

::: moniker range=">=vs-2019"
Visual Studio 2019, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end

Bu yordamlar, bu sunucu yapılandırmalarında test edilmiştir:
* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve IIS 10
* Windows Server 2019 ve IIS 10

## <a name="network-requirements"></a>Ağ gereksinimleri

Proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmez. Yüksek gecikme veya düşük bant genişliğine sahip bir bağlantı (örneğin, Internet veya ülkeler arasında Internet üzerinden) için hata ayıklama önerilmez ve başarısız olabilir veya aşırı derecede yavaş olabilir. Gereksinimlerin tüm listesi için bkz. [gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Uygulama IIS 'de zaten çalışıyor mu?

Bu makalede, Windows Server 'da IIS 'nin temel yapılandırmasını ayarlama ve uygulamayı Visual Studio 'dan dağıtma adımları yer alır. Bu adımlar, sunucuda gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırılabilmesi ve uzaktan hata ayıklama için hazırsanız emin olmak için eklenmiştir.

* Uygulamanız IIS 'de çalışıyorsa ve yalnızca uzaktan hata ayıklayıcıyı indirmek ve hata ayıklamayı başlatmak istiyorsanız, [Windows Server 'da uzak araçları indirme ve yükleme](#BKMK_msvsmon)bölümüne gidin.

* Uygulamanızın Hata ayıklayabilmeniz, dağıtılması ve IIS 'de doğru şekilde çalıştığından emin olmak istiyorsanız, bu konudaki tüm adımları izleyin.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarında ASP.NET Core uygulamasını oluşturma

1. Yeni bir ASP.NET Core Web uygulaması oluşturun.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de **CTRL + Q** yazarak arama kutusunu açın, **ASP.net** yazın, **Şablonlar**' ı seçin ve sonra **Yeni ASP.NET Core Web uygulaması oluştur**' u seçin. Görüntülenen iletişim kutusunda, projeyi **Myaspapp** olarak adlandırın ve ardından **Oluştur**' u seçin. Ardından **Web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de **dosya > yeni > proje**' yi seçin ve ardından **Visual C# > web > ASP.NET Core Web uygulaması**' nı seçin. ASP.NET Core Şablonları bölümünde **Web uygulaması (Model-View-Controller)** öğesini seçin. ASP.NET Core 2,1 ' nin seçildiğinden emin olun, **Docker desteğinin etkinleştirilmesi** ve **kimlik** doğrulamasının **kimlik doğrulaması yok** olarak ayarlandığından emin olun. Projeyi **Myaspapp** olarak adlandırın.
    ::: moniker-end

4. About.cshtml.cs dosyasını açın ve yöntemde bir kesme noktası ayarlayın `OnGet` (eski şablonlarda, bunun yerine HomeController.cs ' yi açın ve yöntemde kesme noktasını ayarlayın `About()` ).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> Windows Server 'da IIS 'yi yükleyip yapılandırma

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server 'da tarayıcı güvenlik ayarlarını güncelleştirme

Internet Explorer 'da artırılmış güvenlik yapılandırması etkinse (varsayılan olarak etkindir), Web sunucusu bileşenlerinden bazılarını indirmeniz için bazı etki alanlarını güvenilen siteler olarak eklemeniz gerekebilir. Güvenilen siteleri, **güvenlik > güvenilen siteler > siteleri > Internet seçeneklerine** giderek ekleyin. Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı indirdiğinizde, çeşitli web sitesi betikleri ve kaynakları yüklemek için izin verme istekleri alabilirsiniz. Bu kaynaklardan bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle** ' ye tıklayın.

## <a name="install-aspnet-core-on-windows-server"></a>Windows Server 'a ASP.NET Core yüklemesi

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

1. IIS Yöneticisi 'nde, sol bölmedeki **Bağlantılar** altında **uygulama havuzları**' nı seçin. **DefaultAppPool** ' i açın ve **.NET CLR sürümünü** **yönetilen kod olmadan** ayarlayın. ASP.NET Core için bu gereklidir. Varsayılan Web sitesi, DefaultAppPool 'yi kullanır.

2. DefaultAppPool öğesini durdurup yeniden başlatın.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows Server 'da barındırma sunucuları için Web Dağıtımı yükleyip yapılandırın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server 'da IIS 'de yayımlama ayarları dosyası oluşturma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio 'da yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlamalıdır. Uygulama Visual Studio 'dan başlamazsa, düzgün çalıştığını doğrulamak için uygulamayı IIS 'de başlatın. ASP.NET Core için, **DefaultAppPool** için uygulama havuzu alanının **yönetilen kod yok** olarak ayarlandığından emin olmanız gerekir.

1. **Ayarlar** iletişim kutusunda, **İleri**' ye tıklayarak hata ayıklamayı etkinleştirin, **hata ayıklama** yapılandırması ' nı seçin ve ardından **dosya yayımlama** seçenekleri altında **Hedefteki ek dosyaları Kaldır** ' ı seçin.

    > [!IMPORTANT]
    > Bir yayın yapılandırması seçerseniz, ' ı yayımladığınızda *web.config* dosyasında hata ayıklamayı devre dışı bırakabilirsiniz.

1. **Kaydet** ' e tıklayın ve uygulamayı yeniden yayımlayın.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Seçim Yerel bir klasöre yayımlayarak dağıtma

Uygulamayı PowerShell, RoboCopy kullanarak IIS 'e kopyalamak istiyorsanız veya dosyaları el ile kopyalamak istiyorsanız uygulamanızı dağıtmak için bu seçeneği kullanabilirsiniz.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Windows Server bilgisayarında ASP.NET Core Web sitesini yapılandırma

1. Windows Gezgini 'ni açın ve yeni bir klasör oluşturun **, burada** ASP.NET Core projeyi daha sonra dağıtacaksınız.

2. Zaten açık değilse, **Internet Information Services (IIS) Yöneticisi**' ni açın. (Sunucu Yöneticisi sol bölmesinde **IIS**' yi seçin. Sunucuya sağ tıklayın ve **Internet Information Services (IIS) Yöneticisi**' ni seçin.)

3. Sol bölmedeki **Bağlantılar** ' ın altında, **siteler**' e gidin.

4. **Varsayılan Web sitesini** seçin, **temel ayarlar**' ı seçin ve **fiziksel yolu** **C:\publish** olarak ayarlayın.

4. **Varsayılan Web sitesi** düğümüne sağ tıklayın ve **Uygulama Ekle**' yi seçin.

5. **Diğer ad** alanını **Myaspapp** olarak ayarlayın, varsayılan uygulama havuzunu (**DefaultAppPool**) kabul edin ve **fiziksel yolu** **C:\publish** olarak ayarlayın.

6. **Bağlantılar** altında **uygulama havuzları**' nı seçin. **DefaultAppPool** ' i açın ve uygulama havuzu alanını **yönetilen kod olmadan** ayarlayın.

7. IIS Yöneticisi 'nde yeni siteye sağ tıklayın, **Izinleri Düzenle**' yi seçin ve Web uygulamasına erişim için yapılandırılmış ıusr, IIS_IUSRS veya kullanıcının okuma & yürütme haklarına sahip yetkili bir kullanıcı olduğundan emin olun.

    Erişim izni olan bu kullanıcılardan birini görmüyorsanız, okuma & yürütme hakları olan bir kullanıcı olarak ıUSR ekleme adımlarını izleyin.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Visual Studio 'dan yerel bir klasöre yayımlayarak uygulamayı yayımlayın ve dağıtın

Ayrıca, dosya sistemini veya diğer araçları kullanarak uygulamayı yayımlayabilir ve dağıtabilirsiniz.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Windows Server 'da uzak araçları indirme ve yükleme

Visual Studio sürümünüz ile eşleşen uzak araçların sürümünü indirin.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Windows Server 'da uzaktan hata ayıklayıcı 'yı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izinler eklemeniz gerekiyorsa, kimlik doğrulama modunu veya uzaktan hata ayıklayıcı bağlantı noktası numarasını değiştirin, bkz. [Uzaktan hata ayıklayıcıyı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).

Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırma hakkında bilgi için bkz. [Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırma](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Visual Studio bilgisayarından ASP.NET uygulamasına iliştirme

1. Visual Studio bilgisayarda, hata ayıklamaya çalıştığınız çözümü açın (Bu makaledeki tüm adımları takip ediyorsanız,**Myaspapp** ).
2. Visual Studio 'da, **Işleme eklemek > hata ayıkla** ' ya tıklayın (Ctrl + Alt + P).

    > [!TIP]
    > Visual Studio 2017 ve sonraki sürümlerinde, **hata ayıkla > işlem...** (SHIFT + alt + P) kullanarak daha önce eklediğiniz işleme yeniden iliştirebilirsiniz.

3. Niteleyici alanını olarak ayarlayın **\<remote computer name>** ve **ENTER** tuşuna basın.

    Visual Studio 'Nun gerekli bağlantı noktasını bilgisayar adına eklediğini doğrulayın ve şu biçimde görünür: **\<remote computer name> :p ort**

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

    ASP.NET Web sayfasını görmeniz gerekir.

9. Çalışan ASP.NET uygulamasında **hakkında** sayfasına tıklayın.

    Kesme noktası Visual Studio 'da isabet almalıdır.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Sorun giderme: gerekli bağlantı noktalarını Windows Server 'da aç

Çoğu kurulumda, gerekli bağlantı noktaları ASP.NET ve uzaktan hata ayıklayıcı yüklemesi tarafından açılır. Ancak, bağlantı noktalarının açık olduğunu doğrulamanız gerekebilir.

> [!NOTE]
> Bir Azure VM 'de, bağlantı noktalarını [ağ güvenlik grubu](/azure/virtual-machines/windows/nsg-quickstart-portal)üzerinden açmanız gerekir.

Gerekli bağlantı noktaları:

* 80-IIS için gereklidir
::: moniker range=">=vs-2019"
* 4024-Visual Studio 2019 uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
::: moniker range="vs-2017"
* 4022-Visual Studio 2017 uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
* UDP 3702-(Isteğe bağlı) bulma bağlantı noktası, Visual Studio 'da uzaktan hata ayıklayıcıya eklerken **bul** düğmesine erişmenizi sağlar.

1. Windows Server 'da bir bağlantı noktasını açmak için **Başlat** menüsünü açın, **Gelişmiş Güvenlik Özellikli Windows Güvenlik Duvarı** araması yapın.

2. Sonra **gelen kuralları yeni kural > bağlantı noktası >** seçin ve ardından **İleri**' ye tıklayın. (UDP 3702 için bunun yerine **giden kurallar** ' ı seçin.)

3. **Belirli yerel bağlantı noktaları** altında, bağlantı noktası numarasını girin, **İleri**' ye tıklayın.

4. **Bağlantıya Izin ver**' e tıklayın, **İleri**' ye tıklayın.

5. Bağlantı noktası için etkinleştirilecek bir veya daha fazla ağ türü seçin ve **İleri**' ye tıklayın.

    Seçtiğiniz tür, uzak bilgisayarın bağlı olduğu ağı içermelidir.
6. Gelen kuralı için adı (örneğin, **IIS**, **Web dağıtımı** veya **msvsmon**) ekleyin ve **son**' a tıklayın.

    Yeni kuralınızı gelen kurallar veya giden kurallar listesinde görmeniz gerekir.

    Windows Güvenlik Duvarı 'nı yapılandırma hakkında daha fazla bilgi edinmek istiyorsanız bkz. [Uzaktan hata ayıklama Için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Diğer gerekli bağlantı noktaları için ek kurallar oluşturun.
