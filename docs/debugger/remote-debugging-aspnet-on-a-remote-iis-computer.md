---
title: Uzak IIS ASP.NET Core'da Uzaktan Hata Ayıklama | Microsoft Docs
description: Uzak hata ASP.NET Core (IIS) bilgisayarına dağıtılmış bir Internet Information Services uygulamanın Visual Studio ayıklar.
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
ms.openlocfilehash: 89481b5e7b6fba10a776531a516e511856aee510
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627932"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Visual Studio'ASP.NET Core Uzak IIS Bilgisayarına Uzaktan Hata Visual Studio

IIS'ye ASP.NET Core bir uygulamanın hata ayıklaması için, uygulamanızı dağıtarak uzak araçları yükleyin ve çalıştırın ve ardından Visual Studio.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Bu kılavuzda, bir kümeyi ayarlama ve yapılandırma Visual Studio ASP.NET Core IIS'ye dağıtma ve uzaktan hata ayıklayıcıyı Visual Studio. 4.5.2 ASP.NET uzaktan hata ayıklamak için bkz. [IIS ASP.NET Uzaktan Hata Ayıklama.](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) Azure'ı kullanarak IIS'de de dağıtım ve hata ayıklama da sabilirsiniz. Daha Azure App Service, önceden yapılandırılmış bir IIS örneğinde ve uzaktan hata ayıklayıcıda Snapshot Debugger kullanarak veya [hata](../debugger/debug-live-azure-applications.md) ayıklayıcıyı [Sunucu Gezgini.](../debugger/remote-debugging-azure.md)

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"
Visual Studio 2019'un bu makalede gösterilen adımları izlemesi gerekir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio makalede gösterilen adımları takip etmek için 2017'ye bakın.
::: moniker-end

Bu yordamlar şu sunucu yapılandırmalarında test edilmiştir:
* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve IIS 10
* Windows Server 2019 ve IIS 10

## <a name="network-requirements"></a>Ağ gereksinimleri

Ara sunucu üzerinden bağlanan iki bilgisayar arasında hata ayıklama desteklenmiyor. Çevirmeli İnternet gibi yüksek gecikmeli veya düşük bant genişliğine sahip bir bağlantı üzerinden veya ülkeler arasında İnternet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya kabul edilemez düzeyde yavaş olabilir. Gereksinimlerin tam listesi için bkz. [Gereksinimler.](../debugger/remote-debugging.md#requirements_msvsmon)

## <a name="app-already-running-in-iis"></a>Uygulama zaten IIS'de mi çalışıyor?

Bu makale, Windows sunucusunda IIS'nin temel yapılandırmasını ayarlama ve uygulamayı Visual Studio. Bu adımlar sunucuda gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırılaya kadar olduğundan ve uzaktan hata ayıklamaya hazır olduğundan emin olmak için dahil edilir.

* Uygulamanız IIS'de çalıştırıyorsa ve yalnızca uzak hata ayıklayıcısını indirmek ve hata ayıklamayı başlatmak için Uzak araçları İndirme ve Yükleme 'ye gidin [Windows Sunucusuna gidin.](#BKMK_msvsmon)

* Hata ayıklamak için, uygulamanın IIS'de doğru şekilde ayarıldığından, dağıtıldığından ve çalıştırıldığından emin olmak için yardım almak için bu konudaki tüm adımları izleyin.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarda ASP.NET Core oluşturma

1. Yeni bir web ASP.NET Core oluşturun.

    ::: moniker range=">=vs-2019"
    2019 Visual Studio da başlangıç **penceresinde Yeni proje oluştur'a** tıklayın. Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne**  >  **tıklayın.** **Web uygulaması yazın,** dil **olarak C#** seçin, ardından ASP.NET Core Web Uygulaması **(Model-Görünüm-Denetleyici)** ve ardından Sonraki'yi **seçin.** Sonraki ekranda projeye **MyASPApp adını ve ardından** Sonraki'yi **seçin.**

    Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    2017 Visual Studio de Dosya > **Yeni**> Project'yi ve ardından **Visual C# > Web Uygulaması'> ASP.NET Core seçin.** Şablonlar ASP.NET Core Web Uygulaması **(Model-View-Controller) öğesini seçin.** 2.1 ASP.NET Core, **Docker** Desteğini Etkinleştir'in seçili olduğundan ve Kimlik  Doğrulaması Yok olarak ayarlanmış olduğundan **emin olun.** Projeye **MyASPApp adını girin.**
    ::: moniker-end

4. About.cshtml.cs dosyasını açın ve yönteminde bir kesme noktası ayarlayın (eski şablonlarda bunun yerine HomeController.cs dosyasını açın ve yönteminde `OnGet` kesme noktası `About()` ayarlayın).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Windows Server'da IIS'yi Yükleme ve Yapılandırma

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server'da tarayıcı güvenlik ayarlarını güncelleştirme

Internet Explorer'da Gelişmiş Güvenlik Yapılandırması etkinleştirildiyse (varsayılan olarak etkindir), bazı web sunucusu bileşenlerini indirmenizi sağlamak için bazı etki alanlarını güvenilen siteler olarak eklemeniz gerekir. Güvenilen Siteler ve Siteleri için İnternet **Seçenekleri'ne > Güvenlik > siteleri > ekleyin.** Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı indirirken, çeşitli web sitesi betiklerini ve kaynaklarını yükleme izni vermek için istekler edinebilirsiniz. Bu kaynakların bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle'ye** tıklayın.

## <a name="install-aspnet-core-on-windows-server"></a>Windows Server'ASP.NET Core yükleme

1. .NET Core Barındırma Paketi'nin barındırma sistemine yükleyin. Paket. .NET Core Çalışma Zamanı, .NET Core Kitaplığı ve ASP.NET Core Modülü'ASP.NET Core yüklenir. Daha ayrıntılı yönergeler için bkz. [IIS'de yayımlama.](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)

    Geçerli .NET Core barındırma paketi için, ASP.NET Core [Paketi'ne yükleyin.](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)
    .NET Core 2 için [.NET Core'Windows Sunucu Barındırma'ya yükleyin.](https://aka.ms/dotnetcore-2-windowshosting)

    > [!NOTE]
    > Sistemin bir İnternet bağlantısı yoksa, .NET Core Windows Server Barındırma paketi yüklemeden önce Microsoft Visual C++ *[2015](https://www.microsoft.com/download/details.aspx?id=53840)* Yeniden Dağıtılabilir'i alın ve yükleyin.

2. Sistemi yeniden başlatın (veya sistem YOLUNDA bir değişiklik almak için bir komut isteminden net start w3svc ve ardından **net start w3svc)** **net stop** komutunu yürütün.

## <a name="choose-a-deployment-option"></a>Dağıtım seçeneği belirtin

Uygulamayı IIS'ye dağıtmak için yardıma ihtiyacınız varsa şu seçenekleri göz önünde bulun:

* IIS'de yayımlama ayarları dosyası oluşturarak ve ayarları iis'te içeri aktararak Visual Studio. Bazı senaryolarda bu, uygulamanızı dağıtmanın hızlı bir yoludur. Yayımlama ayarları dosyasını sanız, izinler IIS'de otomatik olarak ayarlanır.

* Dağıtımı yerel bir klasöre yayımlayıp tercih edilen bir yöntem tarafından IIS'de hazırlanmış bir uygulama klasörüne kopyalayıp dağıtın.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(İsteğe bağlı) Yayımlama ayarları dosyası kullanarak dağıtma

Bu seçeneği kullanarak bir yayımlama ayarları dosyası oluşturabilir ve dosyayı Visual Studio.

> [!NOTE]
> Bu dağıtım yöntemi Web Dağıtımı sunucuda yüklü olması gereken bir uygulama kullanır. Ayarları içeri aktarma yerine Web Dağıtımı el ile yapılandırmak için, Barındırma Sunucuları için Web Dağıtımı 3.6 yerine Web Dağıtımı 3.6'Web Dağıtımı yükleyebilirsiniz. Ancak, sunucuyu el Web Dağıtımı yapılandırdıysanız, sunucusundaki bir uygulama klasörünün doğru değerler ve izinlerle yapılandırıldığından emin olun (bkz. Web [sitesini ASP.NET yapılandırma).](#BKMK_deploy_asp_net)

### <a name="configure-the-aspnet-core-web-site"></a>ASP.NET Core web sitesini yapılandırma

1. IIS Yöneticisi'nde, sol bölmede **Bağlantılar'ın altında** Uygulama **Havuzları'nı seçin.** **DefaultAppPool'ı** açın ve **.NET CLR sürümünü Yönetilen** **Kod Yok olarak ayarlayın.** Bu, daha fazla ASP.NET Core. Varsayılan Web Sitesi DefaultAppPool kullanır.

2. DefaultAppPool'u durdurun ve yeniden başlatın.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows Server Web Dağıtımı barındırmak için Windows yapılandırma

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
   > Yayın yapılandırmasını seçerseniz, yayımlarkenweb.configdosyasında *hata ayıklamayı* devre dışı yapılandırmasını devre dışı yapılandırmasınız.

1. **Kaydet'e** tıklayın ve uygulamayı yeniden yayımlar.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(İsteğe bağlı) Yerel bir klasöre yayımlaarak dağıtma

Uygulamayı PowerShell veya RoboCopy kullanarak IIS'ye kopyalamak veya dosyaları el ile kopyalamak için bu seçeneği kullanarak uygulamanızı dağıtabilirsiniz.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Windows Server ASP.NET Core web sitesini yapılandırma

1. Yeni Windows açın ve daha sonra ASP.NET Core projesini dağıtacak olan **C:\Publish** ASP.NET Core oluşturun.

2. Henüz açık değilse, Internet Information Services **(IIS) Yöneticisi'ni açın.** (Uygulamanın sol bölmesinde IIS Sunucu Yöneticisi'yi **seçin.** Sunucuya sağ tıklayın ve Internet Information Services **(IIS) Yöneticisi'ni** seçin.)

3. Sol **bölmede** Bağlantılar'ın altında Siteler'e **gidin.**

4. Varsayılan **Web Sitesi'yi seçin,** **Temel Ayarlar'ı** seçin ve **Fiziksel** yolu **C:\Publish olarak ayarlayın.**

5. Varsayılan Web Sitesi **düğümüne sağ tıklayın ve** Uygulama Ekle'yi **seçin.**

6. Diğer Ad **alanını** **MyASPApp** olarak ayarlayın, varsayılan Uygulama Havuzunu (**DefaultAppPool**) kabul eder ve **Fiziksel** yolu **C:\Publish olarak ayarlayın.**

7. **Bağlantılar'ın** altında Uygulama **Havuzları'ı seçin.** **DefaultAppPool'ı** açın ve Uygulama havuzu alanını Yönetilen **Kod Yok olarak ayarlayın.**

8. IIS Yöneticisi'nde yeni siteye sağ tıklayın, İzinleri Düzenle'yi seçin ve web uygulamasına erişim için yapılandırılmış IUSR, IIS_IUSRS veya kullanıcının Okuma ve Yürütme haklarına sahip yetkili bir kullanıcı olduğundan emin & olun.

    Erişimi olan bu kullanıcılardan birini görmüyorsanız IUSR'yi Okuma ve Yürütme haklarına sahip bir kullanıcı & izleyin.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Visual Studio 'den yerel bir klasöre yayımlayarak uygulamayı yayımlayın ve dağıtın

Ayrıca, dosya sistemini veya diğer araçları kullanarak uygulamayı yayımlayabilir ve dağıtabilirsiniz.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Windows sunucusuna uzak araçları indirme ve yükleme

Visual Studio sürümünüzle eşleşen uzak araçların sürümünü indirin.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Windows sunucuda uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izinler eklemeniz gerekiyorsa, kimlik doğrulama modunu veya uzaktan hata ayıklayıcı bağlantı noktası numarasını değiştirin, bkz. [Uzaktan hata ayıklayıcıyı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).

Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırma hakkında bilgi için bkz. [Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırma](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Visual Studio bilgisayardan ASP.NET uygulamasına iliştirme

1. Visual Studio bilgisayarda, hata ayıklamaya çalıştığınız çözümü açın (bu makaledeki tüm adımları takip ediyorsanız,**myaspapp** ).
2. Visual Studio, **hata ayıkla > işleme iliştir** (Ctrl + Alt + P) seçeneğine tıklayın.

    > [!TIP]
    > Visual Studio 2017 ve sonraki sürümlerinde, **hata ayıkla > işlemek için yeniden iliştir.** .. (shıft + Alt + P) kullanarak daha önce eklediğiniz işleme yeniden iliştirebilirsiniz.

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

## <a name="open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Windows sunucuda gerekli bağlantı noktalarını açın

çoğu kurulumda, gerekli bağlantı noktaları ASP.NET yüklemesi ve uzaktan hata ayıklayıcı tarafından açılır. Ancak, bağlantı noktalarının açık olduğunu doğrulamanız gerekebilir.

> [!NOTE]
> Bir Azure VM 'de, bağlantı noktalarını [ağ güvenlik grubu](/azure/virtual-machines/windows/nsg-quickstart-portal)üzerinden açmanız gerekir.

Gerekli bağlantı noktaları:

* 80-IIS için gereklidir (HTTP)
::: moniker range=">=vs-2019"
* 4024-Visual Studio 2019 ' den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
::: moniker range="vs-2017"
* 4022-Visual Studio 2017 ' den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
* UDP 3702-(Isteğe bağlı) bulma bağlantı noktası, Visual Studio uzaktan hata ayıklayıcıya eklerken **bul** düğmesini kullanmanıza olanak sağlar.

1. Windows sunucuda bir bağlantı noktasını açmak için **başlat** menüsünü açın, **gelişmiş güvenlik özellikli Windows güvenlik duvarı** araması yapın.

2. Sonra **gelen kuralları yeni kural > bağlantı noktası >** seçin ve ardından **İleri**' ye tıklayın. (UDP 3702 için bunun yerine **giden kurallar** ' ı seçin.)

3. **Belirli yerel bağlantı noktaları** altında, bağlantı noktası numarasını girin, **İleri**' ye tıklayın.

4. **Bağlantıya Izin ver**' e tıklayın, **İleri**' ye tıklayın.

5. Bağlantı noktası için etkinleştirilecek bir veya daha fazla ağ türü seçin ve **İleri**' ye tıklayın.

    Seçtiğiniz tür, uzak bilgisayarın bağlı olduğu ağı içermelidir.

6. Gelen kuralı için adı (örneğin, **IIS**, **Web dağıtımı** veya **msvsmon**) ekleyin ve **son**' a tıklayın.

    Yeni kuralınızı gelen kurallar veya giden kurallar listesinde görmeniz gerekir.

    Windows güvenlik duvarını yapılandırma hakkında daha fazla bilgi edinmek istiyorsanız, bkz. [uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Diğer gerekli bağlantı noktaları için ek kurallar oluşturun.
