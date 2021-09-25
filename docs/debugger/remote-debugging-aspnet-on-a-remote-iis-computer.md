---
title: uzak ııs bilgisayarında uzaktan hata ayıklama ASP.NET Core | Microsoft Docs
description: Visual Studio uzaktan hata ayıklayıcı kullanılarak uzak bir Internet Information Services (ııs) bilgisayara dağıtılan ASP.NET Core bir uygulamada hata ayıklayın.
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
ms.openlocfilehash: bc4c527506c80aaf8d4a0d60a31bd1d2adb4d31f
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427232"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Visual Studio içindeki uzak ııs bilgisayarında uzaktan hata ayıklama ASP.NET Core

ııs 'ye dağıtılan ASP.NET Core bir uygulamada hata ayıklamak için, uzak araçları uygulamanızı dağıttığınız bilgisayara yükleyip çalıştırın ve ardından Visual Studio üzerinde çalışan uygulamanıza ekleyin.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

bu kılavuzda, bir Visual Studio ASP.NET Core ayarlama ve yapılandırma, ııs 'ye dağıtma ve uzaktan hata ayıklayıcıyı Visual Studio iliştirme açıklanmaktadır. uzaktan hata ayıklama ASP.NET 4.5.2 için, bkz. [uzaktan hata ayıklama ASP.NET bir ııs bilgisayarında](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Ayrıca, Azure kullanarak IIS 'de dağıtabilir ve hata ayıklayabilirsiniz. Azure App Service için, önceden yapılandırılmış IIS ve uzaktan hata ayıklayıcı örneğini [Snapshot Debugger](../debugger/debug-live-azure-applications.md) kullanarak veya [Sunucu Gezgini hata ayıklayıcıyı ekleyerek](../debugger/remote-debugging-azure.md)kolayca dağıtabilir ve hata ayıklayabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"
Visual Studio 2019, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end

Bu yordamlar, bu sunucu yapılandırmalarında test edilmiştir:
* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve ııs 10
* Windows Sunucu 2019 ve IIS 10

## <a name="network-requirements"></a>Ağ gereksinimleri

Proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmez. Yüksek gecikme veya düşük bant genişliğine sahip bir bağlantı (örneğin, Internet veya ülkeler arasında Internet üzerinden) için hata ayıklama önerilmez ve başarısız olabilir veya aşırı derecede yavaş olabilir. Gereksinimlerin tüm listesi için bkz. [gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Uygulama IIS 'de zaten çalışıyor mu?

bu makale, Windows sunucuda ııs 'nin temel yapılandırmasını ayarlama ve uygulamayı Visual Studio dağıtma adımlarını içerir. Bu adımlar, sunucuda gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırılabilmesi ve uzaktan hata ayıklama için hazırsanız emin olmak için eklenmiştir.

* uygulamanız ııs 'de çalışıyorsa ve yalnızca uzaktan hata ayıklayıcıyı indirmek ve hata ayıklamayı başlatmak istiyorsanız, [uzak araçları Windows sunucusuna indir ve yükle](#BKMK_msvsmon)' ye gidin.

* Uygulamanızın Hata ayıklayabilmeniz, dağıtılması ve IIS 'de doğru şekilde çalıştığından emin olmak istiyorsanız, bu konudaki tüm adımları izleyin.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarda ASP.NET Core uygulamasını oluşturma

1. yeni bir ASP.NET Core web uygulaması oluşturun.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de, başlangıç penceresinde **yeni proje oluştur** ' u seçin. Başlangıç penceresi açık değilse **Dosya**  >  **Başlangıç penceresi**' ni seçin. **web** uygulaması yazın, dil olarak **C#** ' yi seçin, ardından **ASP.NET Core web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **ileri**' yi seçin. Sonraki ekranda, **Myaspapp** projesini adlandırın ve ardından **İleri**' yi seçin.

    Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de **dosya > yeni > Project**' i seçin, sonra **Visual C# > web > ASP.NET Core web uygulaması**' nı seçin. ASP.NET Core şablonları bölümünde **Web uygulaması (Model-View-Controller)** öğesini seçin. ASP.NET Core 2,1 ' nin seçildiğinden emin olun, **docker desteğinin etkinleştirilmesi** ve **kimlik** doğrulamasının **kimlik doğrulaması yok** olarak ayarlandığından emin olun. Projeyi **Myaspapp** olarak adlandırın.
    ::: moniker-end

4. . Cshtml. cs dosyasını açın ve yöntemde bir kesme noktası ayarlayın `OnGet` (eski şablonlarda, bunun yerine HomeController. cs dosyasını açın ve yönteminde kesme noktasını ayarlayın `About()` ).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Windows sunucusuna ııs yükleyip yapılandırma

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows sunucuda tarayıcı güvenlik ayarlarını güncelleştir

Internet Explorer 'da artırılmış güvenlik yapılandırması etkinse (varsayılan olarak etkindir), Web sunucusu bileşenlerinden bazılarını indirmeniz için bazı etki alanlarını güvenilen siteler olarak eklemeniz gerekebilir. Güvenilen siteleri, **güvenlik > güvenilen siteler > siteleri > Internet seçeneklerine** giderek ekleyin. Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı indirdiğinizde, çeşitli web sitesi betikleri ve kaynakları yüklemek için izin verme istekleri alabilirsiniz. Bu kaynaklardan bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle** ' ye tıklayın.

## <a name="install-aspnet-core-on-windows-server"></a>Windows sunucusuna ASP.NET Core yüklemesi

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

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlamalıdır. uygulama Visual Studio başlamazsa, düzgün çalıştığını doğrulamak için uygulamayı ııs 'de başlatın. ASP.NET Core için, **DefaultAppPool** için uygulama havuzu alanının **yönetilen kod yok** olarak ayarlandığından emin olmanız gerekir.

1. Hata ayıklama yapılandırmasına geçiş yapın.

   ::: moniker range=">=vs-2019"
   profili düzenlemek için **düzenle** ' yi seçin ve ardından **Ayarlar** öğesini seçin. Bir **hata ayıklama** yapılandırması seçin ve ardından **dosya yayımlama** seçenekleri altında **Hedefteki ek dosyaları Kaldır** ' ı seçin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   **Ayarlar** iletişim kutusunda, **ileri**' ye tıklayarak hata ayıklamayı etkinleştirin, bir **hata ayıklama** yapılandırması seçin ve ardından **dosya yayımlama** seçenekleri altında **hedefteki ek dosyaları kaldır** ' ı seçin.
   ::: moniker-end

   > [!IMPORTANT]
   > Bir yayın yapılandırması seçerseniz, ' ı yayımladığınızda *web.config* dosyasında hata ayıklamayı devre dışı bırakabilirsiniz.

1. **Kaydet** ' e tıklayın ve uygulamayı yeniden yayımlayın.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Seçim Yerel bir klasöre yayımlayarak dağıtma

Uygulamayı PowerShell, RoboCopy kullanarak IIS 'e kopyalamak istiyorsanız veya dosyaları el ile kopyalamak istiyorsanız uygulamanızı dağıtmak için bu seçeneği kullanabilirsiniz.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Windows sunucusu bilgisayarında ASP.NET Core Web sitesini yapılandırma

1. Windows gezginini açın ve ASP.NET Core projesi daha sonra dağıtacağınız yeni bir klasör oluşturun ( **C:\Publish**).

2. zaten açık değilse, **Internet Information Services (ııs) yöneticisi**' ni açın. (Sunucu Yöneticisi sol bölmesinde **IIS**' yi seçin. sunucuya sağ tıklayın ve **Internet Information Services (ııs) yöneticisi**' ni seçin.)

3. Sol bölmedeki **Bağlantılar** ' ın altında, **siteler**' e gidin.

4. **varsayılan Web sitesini** seçin, **temel Ayarlar** seçin ve **fiziksel yolu** **C:\Publish** olarak ayarlayın.

5. **Varsayılan Web sitesi** düğümüne sağ tıklayın ve **Uygulama Ekle**' yi seçin.

6. **Diğer ad** alanını **Myaspapp** olarak ayarlayın, varsayılan uygulama havuzunu (**DefaultAppPool**) kabul edin ve **fiziksel yolu** **C:\publish** olarak ayarlayın.

7. **Bağlantılar** altında **uygulama havuzları**' nı seçin. **DefaultAppPool** ' i açın ve uygulama havuzu alanını **yönetilen kod olmadan** ayarlayın.

8. IIS Yöneticisi 'nde yeni siteye sağ tıklayın, **Izinleri Düzenle**' yi seçin ve Web uygulamasına erişim için yapılandırılmış ıusr, IIS_IUSRS veya kullanıcının okuma & yürütme haklarına sahip yetkili bir kullanıcı olduğundan emin olun.

    Erişim izni olan bu kullanıcılardan birini görmüyorsanız, okuma & yürütme hakları olan bir kullanıcı olarak ıUSR ekleme adımlarını izleyin.

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

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Uygulamanın ASP.NET bilgisayardan Visual Studio ekleme

1. Bu Visual Studio hata ayıklamaya çalıştığın çözümü açın ( bu makaledeki tüm adımları takip ediyorsanız **MyASPApp).**
2. Bu Visual Studio İşleme Ekle (Ctrl + Alt + **P) >** Hata Ayıkla'ya tıklayın.

    > [!TIP]
    > 2017 Visual Studio ve sonraki sürümlerde Hata Ayıklama ve İşleme Yeniden İliştir... (Shift + Alt + P) kullanarak daha önce bağlı olduğunuz **> işleme** yeniden iliştirebilirsiniz.

3. Niteleyici alanını olarak ayarlayın ve **\<remote computer name>** Enter tuşuna **basın.**

    Gerekli Visual Studio bilgisayar adına eklendiğinden emin olun. Bu bağlantı noktası şu biçimde görünür: **\<remote computer name> :p ort**

    ::: moniker range=">=vs-2022"
    2022 Visual Studio de **\<remote computer name> :4026 görüyor gerekir**
    ::: moniker-end
    ::: moniker range="vs-2019"
    2019 Visual Studio da **\<remote computer name> :4024'ü görüyor gerekir**
    ::: moniker-end
    ::: moniker range="vs-2017"
    2017 Visual Studio de **\<remote computer name> :4022 ifadesini görüyor gerekir**
    ::: moniker-end
    Bağlantı noktası gereklidir. Bağlantı noktası numarasını görmüyorsanız el ile ekleyin.

4. **Yenile**'ye tıklayın.
    Kullanılabilir İşlemler penceresinde bazı **işlemlerin görünmesi** gerekir.

    Herhangi bir işlem görmüyorsanız, uzak bilgisayar adı (bağlantı noktası gereklidir) yerine IP adresini kullanmayı deneyin. `ipconfig`IPv4 adresini almak için komut satırı içinde kullanabilirsiniz.

    Bul düğmesini kullanmak **için** sunucuda UDP bağlantı noktası [3702'yi açmanız](#bkmk_openports) gerekir.

5. Tüm **kullanıcıların işlemlerini göster'i seçin.**

6. Uygulamanızı hızla bulmak için işlem adının ilk harfini yazın.

    * IIS'de işlem [sırasında barındırma modelini kullanıyorsanız,](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) doğru işlem **w3wp.exe** seçin. .NET Core 3'te başlayarak bu varsayılan değerdir.

    * Aksi takdirde, **dotnet.exe** seçin. (Bu işlem dışında barındırma modelidir.)

    Bir veya daha fazla işlem *w3wp.exe* *dotnet.exe,* Kullanıcı Adı **sütununu** kontrol edin. Bazı senaryolarda Kullanıcı Adı **sütunu,** **IIS APPPOOL\DefaultAppPool gibi** uygulama havuzu adını gösterir. Uygulama Havuzu'nun benzersiz olmadığını görüyorsanız, hata ayıklamak istediğiniz uygulama örneği için yeni bir adlandırılmış Uygulama Havuzu oluşturun ve bunu Kullanıcı Adı **sütununda** kolayca bulabilirsiniz.

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
- Uygulamanıza ASP.NET sürümünün sunucuya yüklemiş olduğunu doğrulayın. Uygulamanız için, Özellikler sayfasında sürümü görüntüleyebilirsiniz ve **ayarlayın.** Uygulamayı farklı bir sürüme ayarlamak için bu sürümün yüklü olması gerekir.
- Uygulama açılmaya çalışsa ama bir sertifika uyarısı görüyorsanız siteye güvenmeyi seçin. Uyarıyı zaten kapattıysanız projenize bir *.pubxml dosyası olan yayımlama profilini düzenleyebilir ve aşağıdaki öğeyi eklersiniz (yalnızca test için): `<AllowUntrustedCertificate>true</AllowUntrustedCertificate>`
- Uygulama, uygulamanın Visual Studio doğru dağıtıldığından emin olmak için IIS'de başlatabilirsiniz.
- Durum bilgileri için Visual Studio penceresindeki Çıkış penceresini ve hata iletilerinizi kontrol edin.

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

2. Ardından Yeni **Kural bağlantı noktası > Gelen Kuralları'> ve** ardından Sonraki'ne **tıklayın.** (UDP 3702 için bunun yerine **Giden Kuralları'ı** seçin.)

3. Belirli **yerel bağlantı noktaları altında** bağlantı noktası numarasını girin, Ardından'ya **tıklayın.**

4. Bağlantıya **İzin Ver'e tıklayın,** Ardından'ya **tıklayın.**

5. Bağlantı noktası için etkinleştirmek istediğiniz bir veya daha fazla ağ türü seçin ve Ardından'ya **tıklayın.**

    Seçen türün uzak bilgisayarın bağlı olduğu ağı içermesi gerekir.

6. Gelen Kuralı için adı **(örneğin, IIS**, **Web Dağıtımı** veya **msvsmon)** ekleyin ve Son'a **tıklayın.**

    Yeni kuralınızı Gelen Kurallar veya Giden Kuralları listesinde görüyor gerekir.

    Güvenlik Duvarı'nı yapılandırma hakkında daha fazla Windows, bkz. Uzaktan Hata [Ayıklama Windows Güvenlik Duvarı'nı yapılandırma.](../debugger/configure-the-windows-firewall-for-remote-debugging.md)

3. Diğer gerekli bağlantı noktaları için ek kurallar oluşturun.
