---
title: IIS bilgisayarında ASP.NET hatalarını uzaktan ayıklama
description: bir Visual Studio ASP.NET MVC 4.5.2 uygulamasını ayarlamayı ve yapılandırmayı, ııs 'ye dağıtmayı ve Visual Studio uzaktan hata ayıklayıcıyı eklemeyi öğrenin.
ms.custom:
- remotedebugging
- seodec18
ms.date: 08/31/2021
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: 406f05fbb5d1517fd953c8732eaa8f4ac9522b3d
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427245"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>uzak ııs bilgisayarında uzaktan hata ayıklama ASP.NET

ııs 'ye dağıtılan ASP.NET bir uygulamada hata ayıklamak için, uzak araçları uygulamanızı dağıttığınız bilgisayara yükleyip çalıştırın ve ardından Visual Studio üzerinde çalışan uygulamanıza ekleyin.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

bu kılavuzda, bir Visual Studio ASP.NET MVC 4.5.2 uygulamasını ayarlama ve yapılandırma, ııs 'ye dağıtma ve Visual Studio uzaktan hata ayıklayıcıyı iliştirme açıklanmaktadır.

> [!NOTE]
> bunun yerine uzaktan hata ayıklama ASP.NET Core için, bkz. [uzaktan hata ayıklama ASP.NET Core bir ııs bilgisayarında](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Azure App Service için, önceden yapılandırılmış bir IIS örneğini [Snapshot Debugger](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 required) kullanarak veya [hata ayıklayıcıyı Sunucu Gezgini ekleyerek](../debugger/remote-debugging-azure.md)kolayca dağıtabilir ve hata ayıklayabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"
Visual Studio 2019, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017, bu makalede gösterilen adımları izlemek için gereklidir.
::: moniker-end

Bu yordamlar, bu sunucu yapılandırmalarında test edilmiştir:

* Windows Server 2012 R2 ve ııs 8 (Windows server 2008 R2 için sunucu adımları farklıdır)

## <a name="network-requirements"></a>Ağ gereksinimleri

uzaktan hata ayıklayıcı, Windows server 2008 Service Pack 2 ' den başlayarak Windows server 'da desteklenir. Gereksinimlerin tüm listesi için bkz. [gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmez. Yüksek gecikme veya düşük bant genişliğine sahip bir bağlantı (örneğin, Internet veya ülkeler arasında Internet üzerinden) için hata ayıklama önerilmez ve başarısız olabilir veya aşırı derecede yavaş olabilir.

## <a name="app-already-running-in-iis"></a>Uygulama IIS 'de zaten çalışıyor mu?

bu makale, Windows sunucuda ııs 'nin temel yapılandırmasını ayarlama ve uygulamayı Visual Studio dağıtma adımlarını içerir. Bu adımlar, sunucuda gerekli bileşenlerin yüklü olduğundan, uygulamanın doğru şekilde çalıştırılabilmesi ve uzaktan hata ayıklama için hazırsanız emin olmak için eklenmiştir.

* uygulamanız ııs 'de çalışıyorsa ve yalnızca uzaktan hata ayıklayıcıyı indirmek ve hata ayıklamayı başlatmak istiyorsanız, [uzak araçları Windows sunucusuna indir ve yükle](#BKMK_msvsmon)' ye gidin.

* Uygulamanızın Hata ayıklayabilmeniz, dağıtılması ve IIS 'de doğru şekilde çalıştığından emin olmak istiyorsanız, bu konudaki tüm adımları izleyin.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarda ASP.NET 4.5.2 uygulaması oluşturma

1. yeni bir MVC ASP.NET uygulaması oluşturun.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de, **Ctrl + Q** yazarak arama kutusunu açın, **asp.net** yazın, **şablonlar**' ı seçin ve sonra **yeni ASP.NET Web uygulaması oluştur (.NET Framework)** öğesini seçin. Görüntülenen iletişim kutusunda, projeyi **Myaspapp** olarak adlandırın ve ardından **Oluştur**' u seçin. **MVC** ' yi seçin ve **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    bunu Visual Studio 2017 ' de yapmak için **dosya > yeni > Project**' i seçin ve ardından **Visual C# > web > ASP.NET web uygulaması**' nı seçin. **ASP.NET 4.5.2** şablonları bölümünde **MVC**' yi seçin. **Docker desteğini etkinleştir** ' in seçili olmadığından ve **kimlik** doğrulamasının **kimlik doğrulaması yok** olarak ayarlandığından emin olun. Projeyi **Myaspapp** olarak adlandırın.)
    ::: moniker-end

2. *HomeController. cs* dosyasını açın ve yönteminde bir kesme noktası ayarlayın `About()` .

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Windows sunucusuna ııs yükleyip yapılandırma

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows sunucuda tarayıcı güvenlik ayarlarını güncelleştir

Internet Explorer 'da artırılmış güvenlik yapılandırması etkinse (varsayılan olarak etkindir), Web sunucusu bileşenlerinden bazılarını indirmeniz için bazı etki alanlarını güvenilen siteler olarak eklemeniz gerekebilir. Güvenilen siteleri, **güvenlik > güvenilen siteler > siteleri > Internet seçeneklerine** giderek ekleyin. Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı indirdiğinizde, çeşitli web sitesi betikleri ve kaynakları yüklemek için izin verme istekleri alabilirsiniz. Bu kaynaklardan bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle** ' ye tıklayın.

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a>Windows sunucusuna ASP.NET 4,5 'yi yükler

ııs 'de ASP.NET yüklemek için daha ayrıntılı bilgi isterseniz, bkz. [ASP.NET 3,5 ve ASP.NET 4,5 ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Sunucu Yöneticisi sol bölmesinde **IIS**' yi seçin. sunucuya sağ tıklayın ve **Internet Information Services (ııs) yöneticisi**' ni seçin.

1. web platformu yükleyicisi (webpı) kullanarak ASP.NET 4,5 ' yi (Windows Server 2012 R2 'deki sunucu düğümünden, **yeni Web platformu bileşenleri al** ' ı seçin ve ardından ASP.NET arayın)

    ![web platform bileşeni ııs: ASP.NET 4,5 daire içinde olan asp.net için arama sonuçlarını gösteren web platformu yükleyicisi 5,0 ekran görüntüsü.](../debugger/media/remotedbg_iis_aspnet_45.png)

    > [!NOTE]
    > Windows Server 2008 R2 kullanıyorsanız, bu komutu kullanmak yerine ASP.NET 4 ' ü yükleyebilirsiniz:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe-IR**

2. Sistemi yeniden başlatın (veya **net stop was/y** ' i yürütün ve ardından sistem yolunda bir değişiklik yapmak için bir komut isteminden net **start w3svc** ' i çalıştırın).

## <a name="choose-a-deployment-option"></a>Dağıtım seçeneği seçin

Uygulamayı IIS 'ye dağıtmak için yardıma ihtiyacınız varsa, şu seçenekleri göz önünde bulundurun:

* IIS 'de bir yayımlama ayarları dosyası oluşturup Visual Studio ayarları içeri aktararak dağıtın. Bazı senaryolarda bu, uygulamanızı dağıtmanın hızlı bir yoludur. Yayınlama ayarları dosyasını oluştururken, izinler IIS 'de otomatik olarak ayarlanır.

* Yerel bir klasöre yayımlayarak ve çıktıyı tercih edilen bir yönteme IIS üzerindeki hazırlanmış bir uygulama klasörüne kopyalayarak dağıtın.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Seçim Yayımlama ayarları dosyası kullanarak dağıtma

Bu seçeneği, bir yayımlama ayarları dosyası oluşturup Visual Studio içine aktarabilirsiniz.

> [!NOTE]
> Bu dağıtım yöntemi, sunucuda yüklü olması gereken Web Dağıtımı kullanır. Ayarları içeri aktarmak yerine Web Dağıtımı el ile yapılandırmak istiyorsanız, barındırma sunucuları için Web Dağıtımı 3,6 yerine Web Dağıtımı 3,6 yükleyebilirsiniz. ancak Web Dağıtımı el ile yapılandırırsanız, sunucudaki bir uygulama klasörünün doğru değerler ve izinlerle yapılandırıldığından emin olmanız gerekir (bkz. [ASP.NET Web sitesini yapılandırma](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Windows sunucusunda barındırma sunucuları için Web Dağıtımı yükleyip yapılandırın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows sunucuda ııs 'de yayımlama ayarları dosyası oluşturma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlamalıdır. uygulama Visual Studio başlamadıysanız uygulamayı ııs 'de başlatın.

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

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Windows sunucusu bilgisayarında ASP.NET Web sitesini yapılandırma

1. Windows gezginini açın ve ASP.NET projesi daha sonra dağıtacağınız yeni bir klasör oluşturun ( **C:\Publish**).

2. zaten açık değilse, **Internet Information Services (ııs) yöneticisi**' ni açın. (Sunucu Yöneticisi sol bölmesinde **IIS**' yi seçin. sunucuya sağ tıklayın ve **Internet Information Services (ııs) yöneticisi**' ni seçin.)

3. Sol bölmedeki **Bağlantılar** ' ın altında, **siteler**' e gidin.

4. **varsayılan Web sitesini** seçin, **temel Ayarlar** seçin ve **fiziksel yolu** **C:\Publish** olarak ayarlayın.

5. **Varsayılan Web sitesi** düğümüne sağ tıklayın ve **Uygulama Ekle**' yi seçin.

6. **Diğer ad** alanını **Myaspapp** olarak ayarlayın, varsayılan uygulama havuzunu (**DefaultAppPool**) kabul edin ve **fiziksel yolu** **C:\publish** olarak ayarlayın.

7. **Bağlantılar** altında **uygulama havuzları**' nı seçin. **DefaultAppPool** 'yi açın ve uygulama havuzu alanını **ASP.NET v 4.0** olarak ayarlayın (ASP.NET 4,5, uygulama havuzu için bir seçenek değildir).

8. IIS Yöneticisi 'nde site seçiliyken, **Izinleri Düzenle**' yi seçin ve uygulama havuzu için yapılandırılmış ıusr, IIS_IUSRS veya kullanıcının okuma & yürütme haklarına sahip yetkili bir kullanıcı olduğundan emin olun. Bu kullanıcılardan hiçbiri yoksa, okuma & yürütme hakları olan bir kullanıcı olarak ıUSR ekleyin.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Visual Studio 'den yerel bir klasöre yayımlayarak uygulamayı yayımlayın ve dağıtın

Ayrıca, dosya sistemini veya diğer araçları kullanarak uygulamayı yayımlayabilir ve dağıtabilirsiniz.

1. (ASP.NET 4.5.2) web.config dosyasında .NET sürümünün doğru olduğundan emin olun.  örneğin, ASP.NET 4.5.2 hedefliyorsanız, bu sürümün web.config listelendiğinden emin olun.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    örneğin, 4.5.2 yerine ASP.NET 4 ' ü yüklüyorsanız sürüm 4,0 olmalıdır.

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

1. Visual Studio bilgisayarda, hata ayıklamaya çalıştığınız çözümü açın (bu makaledeki adımları takip ediyorsanız,**myaspapp** ).
2. Visual Studio, **hata ayıkla > işleme iliştir** (Ctrl + Alt + P) seçeneğine tıklayın.

    > [!TIP]
    > Visual Studio 2017 ve sonraki sürümlerinde, **hata ayıkla > işlemek için yeniden iliştir.** .. (shıft + Alt + P) kullanarak daha önce eklediğiniz işleme yeniden iliştirebilirsiniz.

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

## <a name="troubleshooting-iis-deployment"></a>IIS dağıtımında sorun giderme

- Ana bilgisayara konak adını kullanarak bağlanamıyorsanız, bunun yerine IP adresini deneyin.
- Gerekli bağlantı noktalarının uzak sunucuda açık olduğundan emin olun.
- uygulamanızda kullanılan ASP.NET sürümünün sunucuda yüklü olan sürümle aynı olduğunu doğrulayın. Uygulamanız için **Özellikler** sayfasındaki sürümü görüntüleyebilir ve ayarlayabilirsiniz. Uygulamayı farklı bir sürüme ayarlamak için bu sürümün yüklü olması gerekir.
- Uygulama açılmaya çalıştıysanız, ancak bir sertifika uyarısı görürseniz, siteye güvenmeyi seçin. Uyarıyı zaten kapattıysanız, projenizde bir *. pubxml dosyası olan yayımlama profilini düzenleyebilir ve aşağıdaki öğeyi ekleyebilirsiniz (yalnızca test için): `<AllowUntrustedCertificate>true</AllowUntrustedCertificate>`
- uygulama Visual Studio başlamazsa, doğru şekilde dağıtıldığını test etmek için uygulamayı ııs 'de başlatın.
- durum bilgileri için Visual Studio çıkış penceresini kontrol edin ve hata iletilerinizi kontrol edin.
- 
## <a name="open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Windows sunucuda gerekli bağlantı noktalarını açın

çoğu kurulumda, gerekli bağlantı noktaları ASP.NET yüklemesi ve uzaktan hata ayıklayıcı tarafından açılır. Ancak, bağlantı noktalarının açık olduğunu doğrulamanız gerekebilir.

> [!NOTE]
> Bir Azure VM 'de, bağlantı noktalarını [ağ güvenlik grubu](/azure/virtual-machines/windows/nsg-quickstart-portal)üzerinden açmanız gerekir.

Gerekli bağlantı noktaları:

* 80-IIS için gereklidir
::: moniker range=">=vs-2022"
* 4026-Visual Studio 2022 ' den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
::: moniker-end
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