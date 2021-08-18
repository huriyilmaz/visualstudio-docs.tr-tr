---
title: IIS bilgisayarında ASP.NET hatalarını uzaktan ayıklama
description: Visual Studio ASP.NET MVC 4.5.2 uygulamasını ayarlamayı ve yapılandırmayı, IIS'ye dağıtmayı ve uzaktan hata ayıklayıcıyı Visual Studio.
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: f05f4aee6df580796102bc76bee14c8e32e8dc2e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065359"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Uzak IIS ASP.NET Uzaktan Hata Ayıklama

IIS'ye ASP.NET bir uygulamanın hata ayıklaması için, uygulamanızı dağıtarak uzak araçları yükleyin ve çalıştırın ve ardından Visual Studio'dan çalışan uygulamanıza iliştirin.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Bu kılavuzda, Visual Studio ASP.NET MVC 4.5.2 uygulamasını ayarlama ve yapılandırma, IIS'ye dağıtma ve uzaktan hata ayıklayıcıyı Visual Studio.

> [!NOTE]
> Bunun yerine, ASP.NET Core uzaktan hata ayıklamak için [bkz. IIS ASP.NET Core Uzaktan Hata Ayıklama.](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) Azure App Service için, Snapshot Debugger (.NET 4.6.1 gerekir) veya [Sunucu Gezgini'den](../debugger/debug-live-azure-applications.md) hata ayıklayıcıyı kullanarak iis'nin önceden yapılandırılmış bir örneğinde kolayca dağıtabilir ve hata [ayıklayabilirsiniz.](../debugger/remote-debugging-azure.md)

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"
Visual Studio makalede gösterilen adımları takip etmek için Visual Studio 2019 gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio makalede gösterilen adımları takip etmek için Visual Studio 2017 gereklidir.
::: moniker-end

Bu yordamlar şu sunucu yapılandırmalarında test edilmiştir:

* Windows Server 2012 R2 ve IIS 8 (Windows Server 2008 R2 için sunucu adımları farklıdır)

## <a name="network-requirements"></a>Ağ gereksinimleri

Uzaktan hata ayıklayıcı, Windows Server 2008 Service Pack 2'den başlayarak Windows Server'da de desteklemektedir. Gereksinimlerin tam listesi için bkz. [Gereksinimler.](../debugger/remote-debugging.md#requirements_msvsmon)

> [!NOTE]
> Ara sunucu üzerinden bağlanan iki bilgisayar arasında hata ayıklama desteklenmiyor. Çevirmeli İnternet gibi yüksek gecikmeli veya düşük bant genişliğine sahip bir bağlantı üzerinden veya ülkeler arasında İnternet üzerinden hata ayıklamak önerilmez ve başarısız olabilir veya kabul edilemez düzeyde yavaş olabilir.

## <a name="app-already-running-in-iis"></a>Uygulama zaten IIS'de mi çalışıyor?

Bu makale, Windows sunucusunda IIS'nin temel yapılandırmasını ayarlama ve uygulamayı Visual Studio. Sunucuda gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırılaya kadar ve uzaktan hata ayıklamaya hazır olduğundan emin olmak için bu adımlar dahil edilir.

* Uygulamanız IIS'de çalışıyorsa ve yalnızca uzak hata ayıklayıcısını indirmek ve hata ayıklamayı başlatmak için Uzak araçları İndirme ve Yükleme 'ye gidin [Windows Server.](#BKMK_msvsmon)

* Hata ayıklamak için, uygulamanın IIS'de doğru şekilde ayarıldığından, dağıtıldığından ve çalıştırıldığından emin olmak için yardım almak için bu konudaki tüm adımları izleyin.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarda ASP.NET 4.5.2 Visual Studio oluşturma

1. Yeni bir MVC ASP.NET oluşturun.

    ::: moniker range=">=vs-2019"
    2019'Visual Studio **Ctrl + Q** tuşlarına basarak arama kutusunu açın, **asp.net** yazın, Şablonlar'ı seçin **ve** ardından Yeni ASP.NET Web Uygulaması **(.NET Framework) seçin.** Görüntülenen iletişim kutusunda projeyi **MyASPApp olarak adlandırarak** Oluştur'a **tıklayın.** **MVC'yi seçin** ve **Oluştur'a seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Bunu 2017'de Visual Studio için Dosya **> Yeni > Project'ı** ve ardından **Visual C# > Web Uygulaması'> ASP.NET seçin.** ASP.NET **4.5.2** şablonları bölümünde **MVC'yi seçin.** Docker Desteğini **Etkinleştir'in seçili olduğundan** ve Kimlik DoğrulamasıNın Kimlik **Doğrulaması** Yok olarak ayarlanmış olduğundan **emin olun.** Projeyi **MyASPApp olarak adlandır.)**
    ::: moniker-end

2. *HomeController.cs dosyasını* açın ve yönteminde bir kesme noktası `About()` ayarlayın.

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Windows Server'da IIS'yi Yükleme ve Yapılandırma

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server'da tarayıcı güvenlik ayarlarını güncelleştirme

Internet Explorer'da Gelişmiş Güvenlik Yapılandırması etkinleştirildiyse (varsayılan olarak etkindir), bazı web sunucusu bileşenlerini indirmenizi sağlamak için bazı etki alanlarını güvenilen siteler olarak eklemeniz gerekir. güvenilen siteleri eklemek için İnternet Seçenekleri'ne **> Security > Siteleri'ne > ekleyin.** Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı indirirken, çeşitli web sitesi betiklerini ve kaynaklarını yükleme izni vermek için istekler edinebilirsiniz. Bu kaynakların bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle'ye** tıklayın.

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a>Windows Server'a ASP.NET 4.5'i yükleme

IIS'ye yükleme hakkında daha ayrıntılı bilgi ASP.NET, bkz. IIS [8.0 Using ASP.NET 3.5 ve ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Uygulamanın sol bölmesinde IIS'Sunucu Yöneticisi **seçin.** Sunucuya sağ tıklayın ve Internet Information Services **(IIS) Yöneticisi'ni seçin.**

1. web platformu yükleyicisini (WebPI) kullanarak ASP.NET 4.5'i yükleyin (Windows Server 2012 R2'de Sunucu düğümünden Yeni **Web Platformu** Bileşenlerini Al'ı seçin ve ASP.NET)

    ![Web platformu bileşeni IIS: ASP.NET 4.5'i kırmızıyla çevrelerken asp.net için arama sonuçlarını gösteren Web Platformu Yükleyicisi 5.0'ın ekran görüntüsü.](../debugger/media/remotedbg_iis_aspnet_45.png)

    > [!NOTE]
    > Windows Server 2008 R2 kullanıyorsanız, bu ASP.NET 4'ü yükleyin:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Sistemi yeniden başlatın (veya sistem YOLUNDA bir değişiklik almak için bir komut isteminden net start w3svc ve ardından **net start w3svc)** **net stop** komutunu yürütün.

## <a name="choose-a-deployment-option"></a>Dağıtım seçeneği belirtin

Uygulamayı IIS'ye dağıtmak için yardıma ihtiyacınız varsa şu seçenekleri göz önünde bulun:

* IIS'de yayımlama ayarları dosyası oluşturarak ve ayarları iis'te içeri aktararak Visual Studio. Bazı senaryolarda bu, uygulamanızı dağıtmanın hızlı bir yoludur. Yayımlama ayarları dosyasını sanız, izinler IIS'de otomatik olarak ayarlanır.

* Dağıtımı yerel bir klasöre yayımlayıp tercih edilen bir yöntem tarafından IIS'de hazırlanmış bir uygulama klasörüne kopyalayıp dağıtın.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(İsteğe bağlı) Yayımlama ayarları dosyası kullanarak dağıtma

Bu seçeneği kullanarak bir yayımlama ayarları dosyası oluşturabilir ve dosyayı Visual Studio.

> [!NOTE]
> Bu dağıtım yöntemi Web Dağıtımı sunucuda yüklü olması gereken bir uygulama kullanır. Ayarları içeri aktarma Web Dağıtımı el ile yapılandırmak için, Barındırma Sunucuları için Web Dağıtımı 3.6 yerine Web Dağıtımı 3.6'Web Dağıtımı yükleyebilirsiniz. Ancak, sunucuyu Web Dağıtımı yapılandırdıysanız, sunucusundaki bir uygulama klasörünün doğru değer ve izinlerle yapılandırıldığından emin ASP.NET [gerekir.](#BKMK_deploy_asp_net)

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows Server Web Dağıtımı barındırmak için Windows yapılandırma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server'da IIS'de yayımlama ayarları dosyasını oluşturma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Yayımlama ayarlarını Visual Studio dağıtma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlatılır. Uygulama, uygulamanın başlangıç Visual Studio IIS'de başlatabilirsiniz.

1. Hata ayıklama yapılandırmasına geçiş.

   ::: moniker range=">=vs-2019"
   Profili **düzenlemek** için Düzenle'yi seçin ve sonra da **Ayarlar.** Bir Hata **ayıklama yapılandırması** seçin ve ardından Dosya Yayımlama **seçeneklerinin altında Hedefte** ek dosyaları **kaldır'ı** seçin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Hata **Ayarlar** iletişim kutusunda, Sonraki'ne tıklayarak hata ayıklamayı **etkinleştirin,** bir  **Hata** ayıklama yapılandırması seçin ve ardından Dosya Yayımlama seçeneklerinin altında Hedefte ek dosyaları **kaldır'ı** seçin.
   ::: moniker-end

   > [!IMPORTANT]
   > Yayın yapılandırması seçerseniz, yayımlarkenweb.configdosyasında *hata ayıklamayı* devre dışı bırakın.

1. **Kaydet'e** tıklayın ve uygulamayı yeniden yayımlar.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(İsteğe bağlı) Yerel bir klasöre yayımlaarak dağıtma

Uygulamayı PowerShell veya RoboCopy kullanarak IIS'ye kopyalamak veya dosyaları el ile kopyalamak için bu seçeneği kullanarak uygulamanızı dağıtabilirsiniz.

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Windows Server ASP.NET web sitesini yapılandırma

1. Yeni Windows açın ve yeni bir klasör oluşturun( **C:\Publish**). Burada daha sonra ASP.NET dağıtabilirsiniz.

2. Henüz açık değilse, Internet Information Services **(IIS) Yöneticisi'ni açın.** (Uygulamanın sol bölmesinde IIS Sunucu Yöneticisi'yi **seçin.** Sunucuya sağ tıklayın ve Internet Information Services **(IIS) Yöneticisi'ni** seçin.

3. Sol **bölmede** Bağlantılar'ın altında Siteler'e **gidin.**

4. Varsayılan **Web Sitesi'yi seçin,** Temel **Ayarlar'ı** seçin ve **Fiziksel** yolu **C:\Publish olarak ayarlayın.**

5. Varsayılan Web Sitesi **düğümüne sağ tıklayın ve** Uygulama **Ekle'yi seçin.**

6. Diğer Ad **alanını** **MyASPApp** olarak ayarlayın, varsayılan Uygulama Havuzunu (**DefaultAppPool**) kabul eder ve **Fiziksel** yolu **C:\Publish olarak ayarlayın.**

7. **Bağlantılar'ın** altında Uygulama **Havuzları'ı seçin.** **DefaultAppPool'ı** açın ve Uygulama havuzu **alanını ASP.NET v4.0** olarak ayarlayın (ASP.NET 4.5, Uygulama havuzu için bir seçenek değildir).

8. Site IIS Yöneticisi'nde seçiliyken İzinleri Düzenle'yi seçin ve IUSR, IIS_IUSRS veya Uygulama Havuzu için yapılandırılan kullanıcının Okuma ve Yürütme haklarına sahip yetkili bir kullanıcı olduğundan & olun. Bu kullanıcılardan hiçbiri mevcutsa IUSR'yi Okuma ve Yürütme haklarına sahip & ekleyin.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Visual Studio'den yerel bir klasöre yayımlar ve uygulamayı Visual Studio

Ayrıca, dosya sistemini veya diğer araçları kullanarak uygulamayı yayımlayın ve dağıtın.

1. (ASP.NET 4.5.2) web.config dosyasının .NET'in doğru sürümünü listeleyeli olduğundan emin olun.  Örneğin, 4.5.2 ASP.NET yi hedefle ediyorsanız, bu sürümün 4.5.2 sürümünde listelenmiş web.config.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    Örneğin, 4.5.2 yerine ASP.NET 4 yüklüyse sürüm 4.0 olabilir.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Uzak araçları Windows Server'a indirme ve yükleme

Uzak araçların, uygulama sürümle eşleşen sürümünü Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Windows Server'da uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izin eklemeniz, uzaktan hata ayıklayıcı için kimlik doğrulama modunu veya bağlantı noktası numarasını değiştirmenizi gerekirse, bkz. Uzaktan hata [ayıklayıcıyı yapılandırma.](../debugger/remote-debugging.md#configure_msvsmon)

Uzak hata ayıklayıcısını bir hizmet olarak çalıştırma hakkında bilgi için [bkz. Uzak hata ayıklayıcıyı bir hizmet olarak çalıştırma.](../debugger/remote-debugging.md#bkmk_configureService)

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Visual Studio bilgisayardan ASP.NET uygulamasına iliştirme

1. Visual Studio bilgisayarda, hata ayıklamaya çalıştığınız çözümü açın (bu makaledeki adımları takip ediyorsanız,**myaspapp** ).
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

5. **Tüm kullanıcıların süreçlerini göster**' i işaretleyin.

6. ASP.NET 4,5 **w3wp.exe** hızlı bir şekilde bulmak için işlem adının ilk harfini yazın.

    **w3wp.exe** gösteren birden çok işlem varsa, **Kullanıcı adı** sütununu kontrol edin. Bazı senaryolarda, **Kullanıcı adı** sütunu **IIS APPPOOL\DefaultAppPool** gibi uygulama havuzu adınızı gösterir. Uygulama havuzunu görürseniz doğru süreci belirlemenin kolay bir yolu, hata ayıklamak istediğiniz uygulama örneği için yeni bir adlandırılmış uygulama havuzu oluşturmak ve ardından bunu **Kullanıcı adı** sütununda kolayca bulabilirsiniz.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **Ekle** 'ye tıklayın

8. Uzak bilgisayarın Web sitesini açın. Bir tarayıcıda **http:// \<remote computer name>** adresine gidin.

    ASP.NET web sayfasını görmeniz gerekir.
9. çalışan ASP.NET uygulamasında, **hakkında** sayfasına yönelik bağlantıya tıklayın.

    Kesme noktasının Visual Studio isabet etmesi gerekir.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>sorun giderme: gerekli bağlantı noktalarını Windows sunucuda açın

çoğu kurulumda, gerekli bağlantı noktaları ASP.NET yüklemesi ve uzaktan hata ayıklayıcı tarafından açılır. Ancak, bağlantı noktalarının açık olduğunu doğrulamanız gerekebilir.

> [!NOTE]
> Bir Azure VM 'de, bağlantı noktalarını [ağ güvenlik grubu](/azure/virtual-machines/windows/nsg-quickstart-portal)üzerinden açmanız gerekir.

Gerekli bağlantı noktaları:

* 80-IIS için gereklidir
::: moniker range=">=vs-2019"
* 4024-Visual Studio 2019 ' den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
::: moniker range="vs-2017"
* 4022-Visual Studio 2017 ' den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
* UDP 3702-(Isteğe bağlı) bulma bağlantı noktası, Visual Studio uzaktan hata ayıklayıcıya eklerken **bul** düğmesine erişmenizi sağlar.

1. Windows sunucuda bir bağlantı noktasını açmak için **başlat** menüsünü açın, **gelişmiş güvenlik özellikli Windows güvenlik duvarı** araması yapın.

2. Sonra **gelen kuralları > yeni kural > bağlantı noktası** seçin. **İleri** ' yi ve **belirli yerel bağlantı noktaları**' nı seçin, bağlantı noktası numarasını girin, **Ileri**' ye tıklayın, **bağlantıya izin verin**, ileri ' ye tıklayın ve gelen kural için adı (**IIS**, **Web dağıtımı** veya **msvsmon**) ekleyin.

    Windows güvenlik duvarını yapılandırma hakkında daha fazla bilgi edinmek istiyorsanız, bkz. [uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Diğer gerekli bağlantı noktaları için ek kurallar oluşturun.