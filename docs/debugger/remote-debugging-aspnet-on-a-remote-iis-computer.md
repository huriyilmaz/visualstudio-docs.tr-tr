---
title: Uzak IIS bilgisayarında uzaktan hata ayıklama ASP.NET Core | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: f3741f9b510450dabfea5c1df4eec4b2e0868b26
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181145"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Visual Studio 'da uzak IIS bilgisayarında uzaktan hata ayıklama ASP.NET Core

IIS 'ye dağıtılan ASP.NET Core bir uygulamada hata ayıklamak için, uzak araçları uygulamanızı dağıttığınız bilgisayara yükleyip çalıştırın ve ardından Visual Studio 'dan çalışan uygulamanıza bağlayın.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Bu kılavuzda, Visual Studio ASP.NET Core ayarlama ve yapılandırma, IIS 'ye dağıtma ve Visual Studio 'dan uzaktan hata ayıklayıcı iliştirme açıklanır. Uzaktan hata ayıklama ASP.NET 4.5.2 için, bkz. [BIR IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Ayrıca, Azure kullanarak IIS 'de dağıtabilir ve hata ayıklayabilirsiniz. Azure App Service için, önceden yapılandırılmış IIS ve uzaktan hata ayıklayıcı örneğini [Snapshot Debugger](../debugger/debug-live-azure-applications.md) kullanarak veya [Sunucu Gezgini hata ayıklayıcıyı ekleyerek](../debugger/remote-debugging-azure.md)kolayca dağıtabilir ve hata ayıklayabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"
Visual Studio 2019, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end

Bu yordamlar bu sunucu yapılandırmaları üzerinde test edilmiştir:
* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve IIS 10

## <a name="network-requirements"></a>Ağ gereksinimleri

Bir proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmiyor. Ülkeler yüksek gecikme süresi veya çevirmeli, Internet gibi düşük bant genişliği bağlantı üzerinden veya Internet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya edilemeyecek kadar yavaş. Gereksinimlerin tüm listesi için bkz. [gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Zaten IIS içinde çalışan uygulama?

Bu makalede, temel bir Windows server IIS yapılandırmasını ayarlama ve uygulamayı Visual Studio'dan dağıtma adımlarını içerir. Sunucu bileşenleri yüklü, uygulamanın doğru şekilde çalıştırabilir ve uzaktan hata ayıklama için hazır olduğunu istedi emin olmak için bu adımları dahildir.

* Uygulamanız IIS 'de çalışıyorsa ve yalnızca uzaktan hata ayıklayıcıyı indirmek ve hata ayıklamayı başlatmak istiyorsanız, [Windows Server 'da uzak araçları indirme ve yükleme](#BKMK_msvsmon)bölümüne gidin.

* Emin olmak için Yardım istiyorsanız uygulamanızı, dağıtılan, ayarlanır ve böylece hata ayıklaması yapabilirsiniz, IIS'de doğru çalışmasını, bu konudaki tüm adımları izleyin.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarında ASP.NET Core uygulamasını oluşturma

1. Yeni bir ASP.NET Core Web uygulaması oluşturun. 

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de **CTRL + Q** yazarak arama kutusunu açın, **ASP.net**yazın, **Şablonlar**' ı seçin ve sonra **Yeni ASP.NET Core Web uygulaması oluştur**' u seçin. Görüntülenen iletişim kutusunda, projeyi **Myaspapp**olarak adlandırın ve ardından **Oluştur**' u seçin. Ardından **Web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de **dosya > yeni > proje**' yi seçin ve **ardından C# Visual > Web > ASP.NET Core Web uygulaması**' nı seçin. ASP.NET Core Şablonları bölümünde **Web uygulaması (Model-View-Controller)** öğesini seçin. ASP.NET Core 2,1 ' nin seçildiğinden emin olun, **Docker desteğinin etkinleştirilmesi** ve **kimlik** doğrulamasının **kimlik doğrulaması yok**olarak ayarlandığından emin olun. Projeyi **Myaspapp**olarak adlandırın.
    ::: moniker-end

4. About.cshtml.cs dosyasını açın ve `OnGet` yöntemde bir kesme noktası ayarlayın (eski şablonlarda, bunun yerine HomeController.cs ' yi açın ve `About()` yönteminde kesme noktasını ayarlayın).

## <a name="bkmk_configureIIS"></a>Windows Server 'da IIS 'yi yükleyip yapılandırma

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server'da tarayıcınızın güvenlik ayarlarını güncelleştirin

(Varsayılan olarak etkindir) Internet Explorer Artırılmış Güvenlik Yapılandırması etkinse, bazı web sunucusu bileşenlerini yükleme sağlamak için Güvenilen siteler bazı etki alanları eklemek gerekebilir. Güvenilen siteleri, **güvenlik > güvenilen siteler > siteleri > Internet seçeneklerine**giderek ekleyin. Aşağıdaki etki alanlarını ekleyin.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Yazılımı indirdiğinizde, çeşitli web sitesi komut dosyaları ve kaynakları yüklemeye izin vermek için istekleri alabilirsiniz. Bu kaynaklardan bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle** ' ye tıklayın.

## <a name="install-aspnet-core-on-windows-server"></a>Windows Server 'a ASP.NET Core yüklemesi

1. [.NET Core Windows Server barındırma](https://aka.ms/dotnetcore-2-windowshosting) paketi 'ni barındırma sistemine yükler. Paket, .NET Core çalışma zamanı, .NET Core kitaplığı ve ASP.NET Core modülünü de yüklüyor. Daha ayrıntılı yönergeler için bkz. IIS 'de [Yayımlama](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Sistemin bir Internet bağlantısı yoksa, .NET Core Windows Server barındırma paketi 'ni yüklemeden önce *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* 'ı edinin ve yükleme.

3. Sistemi yeniden başlatın (veya **net stop was/y** ' i yürütün ve ardından sistem yolunda bir değişiklik yapmak için bir komut isteminden net **start w3svc** ' i çalıştırın).

## <a name="choose-a-deployment-option"></a>Bir dağıtım seçeneği seçin

IIS uygulama dağıtmak için yardıma gereksinim duyarsanız, bu seçenekleri göz önünde bulundurun:

* IIS'de bir yayımlama ayarları dosyası oluşturarak ve Visual Studio ayarları içeri aktarma dağıtın. Bazı senaryolarda, uygulamanızı dağıtmak için hızlı bir yolu budur. Yayımlama ayarları dosyası oluşturduğunuzda, IIS'de izinleri otomatik olarak ayarlanır.

* Yerel bir klasöre yayınlayarak ve IIS üzerinde bir hazır uygulamasını klasöre tarafından tercih edilen bir yöntem çıkışı kopyalama dağıtın.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(İsteğe bağlı) Yayımlama ayarları dosyası kullanarak dağıtma

Bu seçeneği kullanabilirsiniz. Visual Studio'ya içeri aktarma ve yayımlama ayarları dosyası oluşturun.

> [!NOTE]
> Bu dağıtım yöntemi, Web dağıtımı kullanır. Web dağıtımı el ile Visual Studio ayarları içeri aktarma yerine yapılandırmak istiyorsanız, barındırma sunucuları için Web dağıtımı 3.6 yerine Web dağıtma 3.6 yükleyebilirsiniz. Ancak Web Dağıtımı el ile yapılandırırsanız, sunucudaki bir uygulama klasörünün doğru değerler ve izinlerle yapılandırıldığından emin olmanız gerekir (bkz. [configure ASP.NET Web site](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Yükleme ve Windows Server üzerinde barındırma sunucuları için Web dağıtımı yapılandırma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>IIS Windows Server'da yayımlama ayarları dosyası oluşturma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio'da yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlayacaktır. Uygulamayı Visual Studio'dan başlatılmazsa, IIS'de uygulamayı başlatın. ASP.NET Core için, **DefaultAppPool** için uygulama havuzu alanının **yönetilen kod yok**olarak ayarlandığından emin olmanız gerekir.

1. **Ayarlar** iletişim kutusunda, **İleri**' ye tıklayarak hata ayıklamayı etkinleştirin, **hata ayıklama** yapılandırması ' nı seçin ve ardından **dosya yayımlama** seçenekleri altında **Hedefteki ek dosyaları Kaldır** ' ı seçin.

    > [!NOTE]
    > Bir yayın yapılandırması seçerseniz, ' ı yayımladığınızda *Web. config* dosyasında hata ayıklamayı devre dışı bırakabilirsiniz.

1. **Kaydet** ' e tıklayın ve uygulamayı yeniden yayımlayın.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(İsteğe bağlı) Yerel bir klasöre yayımlayarak dağıtma

Uygulamayı PowerShell, RoboCopy kullanarak IIS 'e kopyalamak istiyorsanız veya dosyaları el ile kopyalamak istiyorsanız uygulamanızı dağıtmak için bu seçeneği kullanabilirsiniz.

### <a name="BKMK_deploy_asp_net"></a>Windows Server bilgisayarında ASP.NET Core Web sitesini yapılandırma

1. Windows Gezgini 'ni açın ve yeni bir klasör oluşturun **, burada**ASP.NET Core projeyi daha sonra dağıtacaksınız.

2. Zaten açık değilse, **Internet Information Services (IIS) Yöneticisi**' ni açın. (Sunucu Yöneticisi sol bölmesinde **IIS**' yi seçin. Sunucuya sağ tıklayın ve **Internet Information Services (IIS) Yöneticisi**' ni seçin.)

3. Sol bölmedeki **Bağlantılar** ' ın altında, **siteler**' e gidin.

4. **Varsayılan Web sitesini**seçin, **temel ayarlar**' ı seçin ve **fiziksel yolu** **C:\publish**olarak ayarlayın.

4. **Varsayılan Web sitesi** düğümüne sağ tıklayın ve **Uygulama Ekle**' yi seçin.

5. **Diğer ad** alanını **Myaspapp**olarak ayarlayın, varsayılan uygulama havuzunu (**DefaultAppPool**) kabul edin ve **fiziksel yolu** **C:\publish**olarak ayarlayın.

6. **Bağlantılar**altında **uygulama havuzları**' nı seçin. **DefaultAppPool** ' i açın ve uygulama havuzu alanını **yönetilen kod olmadan**ayarlayın.

7. IIS Yöneticisi 'nde yeni siteye sağ tıklayın, **Izinleri Düzenle**' yi seçin ve Web uygulamasına erişim için yapılandırılmış ıusr, IIS_IUSRS veya kullanıcının okuma & yürütme haklarına sahip yetkili bir kullanıcı olduğundan emin olun.

    Erişim izni olan bu kullanıcılardan birini görmüyorsanız, okuma & yürütme hakları olan bir kullanıcı olarak ıUSR ekleme adımlarını izleyin.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Yayımlama ve uygulamayı yayımlayarak bir yerel klasöre Visual Studio'dan dağıtma

Ayrıca, yayımlama ve dosya sistemi veya diğer araçları kullanarak uygulamayı dağıtırsınız.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a>Windows Server 'da uzak araçları indirme ve yükleme

Visual Studio sürümünüz ile eşleşen uzak araçların sürümünü indirin.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a>Windows Server 'da uzaktan hata ayıklayıcı 'yı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izinler eklemeniz gerekiyorsa, kimlik doğrulama modunu veya uzaktan hata ayıklayıcı bağlantı noktası numarasını değiştirin, bkz. [Uzaktan hata ayıklayıcıyı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).

Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırma hakkında bilgi için bkz. [Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırma](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a>Visual Studio bilgisayarından ASP.NET uygulamasına iliştirme

1. Visual Studio bilgisayarda, hata ayıklamaya çalıştığınız çözümü açın (Bu makaledeki tüm adımları takip ediyorsanız,**Myaspapp** ).
2. Visual Studio 'da, **Işleme eklemek > hata ayıkla** ' ya tıklayın (Ctrl + Alt + P).

    > [!TIP]
    > Visual Studio 2017 ve sonraki sürümlerinde, **hata ayıkla > işlem...** (SHIFT + alt + P) kullanarak daha önce eklediğiniz işleme yeniden iliştirebilirsiniz.

3. Niteleyici alanını **\<uzak bilgisayar adı >** olarak ayarlayın ve **ENTER**tuşuna basın.

    Visual Studio 'Nun gerekli bağlantı noktasını, şu biçimde görünen bilgisayar adına eklediğinden emin olun: **\<uzak bilgisayar adı >:p ort**

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de **\<uzak bilgisayar adı > görmeniz gerekir: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de **\<uzak bilgisayar adı > görmeniz gerekir: 4022**
    ::: moniker-end
    Bağlantı noktası gereklidir. Bağlantı noktası numarasını görmüyorsanız, el ile ekleyin.

4. **Yenile**'ye tıklayın.
    **Kullanılabilir süreçler** penceresinde bazı işlemlerin göründüğünü görmeniz gerekir.

    Herhangi bir işlem görmüyorsanız (bağlantı noktası gereklidir) uzak bilgisayar adı yerine IP adresini kullanarak deneyin. IPv4 adresini almak için, bir komut satırında `ipconfig` kullanabilirsiniz.

    **Bul** düğmesini kullanmak istiyorsanız, sunucuda [UDP bağlantı noktası 3702](#bkmk_openports) ' u açmanız gerekebilir.

5. **Tüm kullanıcıların süreçlerini göster**' i işaretleyin.

6. Uygulamanızı hızlı bir şekilde bulmak için işlem adınızın ilk harfini yazın.

    * **DotNet. exe**' yi seçin.

      **DotNet. exe**' yi gösteren birden çok Işlem varsa **Kullanıcı adı** sütununu kontrol edin. Bazı senaryolarda, **Kullanıcı adı** sütunu **IIS APPPOOL\DefaultAppPool**gibi uygulama havuzu adınızı gösterir. Uygulama havuzunu görürseniz doğru süreci belirlemenin kolay bir yolu, hata ayıklamak istediğiniz uygulama örneği için yeni bir adlandırılmış uygulama havuzu oluşturmak ve ardından bunu **Kullanıcı adı** sütununda kolayca bulabilirsiniz.

    * Bazı IIS senaryolarında, uygulama adınızı **Myaspapp. exe**gibi işlem listesinde bulabilirsiniz. Bunun yerine bu işleme ekleyebilirsiniz.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **Ekle**' ye tıklayın.

8. Uzak bilgisayarın Web sitesini açın. Bir tarayıcıda, **http://\<uzak bilgisayar adı >** ' na gidin.

    ASP.NET web sayfası görmeniz gerekir.

9. Çalışan ASP.NET uygulamasında **hakkında** sayfasına tıklayın.

    Visual Studio'da kesme noktasına isabet.

## <a name="bkmk_openports"></a>Sorun giderme: gerekli bağlantı noktalarını Windows Server 'da aç

Çoğu ayarlar ASP.NET ve uzaktan hata ayıklayıcı yüklemesi tarafından gerekli bağlantı noktalarının açıldığından. Ancak, bağlantı noktalarının açık olduğunu doğrulamak gerekebilir.

> [!NOTE]
> Bir Azure VM 'de, bağlantı noktalarını [ağ güvenlik grubu](/azure/virtual-machines/windows/nsg-quickstart-portal)üzerinden açmanız gerekir.

Gerekli bağlantı noktaları:

* 80 - IIS için gerekli
::: moniker range=">=vs-2019"
* 4024-Visual Studio 2019 uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
::: moniker range="vs-2017"
* 4022-Visual Studio 2017 uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
* UDP 3702-(Isteğe bağlı) bulma bağlantı noktası, Visual Studio 'da uzaktan hata ayıklayıcıya eklerken **bul** düğmesine erişmenizi sağlar.

1. Windows Server 'da bir bağlantı noktasını açmak için **Başlat** menüsünü açın, **Gelişmiş Güvenlik Özellikli Windows Güvenlik Duvarı**araması yapın.

2. Sonra **gelen kuralları yeni kural > bağlantı noktası >** seçin ve ardından **İleri**' ye tıklayın. (UDP 3702 için bunun yerine **giden kurallar** ' ı seçin.)

3. **Belirli yerel bağlantı noktaları**altında, bağlantı noktası numarasını girin, **İleri**' ye tıklayın.

4. **Bağlantıya Izin ver**' e tıklayın, **İleri**' ye tıklayın.

5. Bağlantı noktası için etkinleştirilecek bir veya daha fazla ağ türü seçin ve **İleri**' ye tıklayın.

    Seçtiğiniz tür, uzak bilgisayarın bağlı olduğu ağı içermelidir.
6. Gelen kuralı için adı (örneğin, **IIS**, **Web dağıtımı**veya **msvsmon**) ekleyin ve **son**' a tıklayın.

    Yeni kuralınızı gelen kurallar veya giden kurallar listesinde görmeniz gerekir.

    Windows Güvenlik Duvarı 'nı yapılandırma hakkında daha fazla bilgi edinmek istiyorsanız bkz. [Uzaktan hata ayıklama Için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Diğer gerekli bağlantı noktaları için ek kurallar oluşturun.
