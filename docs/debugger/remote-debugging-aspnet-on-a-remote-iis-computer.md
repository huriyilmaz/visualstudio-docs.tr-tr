---
title: Uzaktan IIS Bilgisayarda Uzaktan Hata Ayıklama ASP.NET Çekirdek | Microsoft Dokümanlar
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
ms.openlocfilehash: b33ead969456935dab54c042ba4fbaf1f5ff44f4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385474"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Visual Studio'da Uzaktan IIS Bilgisayarında Uzaktan Hata Ayıklama ASP.NET Core

IIS'ye dağıtılan bir ASP.NET Core uygulamasını hata ayıklamak için, uygulamanızı dağıttığınız bilgisayardaki uzak araçları yükleyin ve çalıştırın ve ardından Visual Studio'dan çalışan uygulamanıza iliştirin.

![Uzaktan hata ayıklama bileşenleri](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Bu kılavuz, Visual Studio ASP.NET Core'u nasıl kurup yapılandırışla, IIS'ye nasıl dağıtılanın ve Visual Studio'dan uzaktan hata ayıklama nın nasıl eklenebildiğini açıklar. 4.5.2 ASP.NET uzaktan hata ayıklama için, [Bir IIS Bilgisayarında Uzaktan Hata Ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)bakın. Azure'u kullanarak IIS'de dağıtabilir ve hata ayıklayabilirsiniz. Azure Uygulama Hizmeti için, Anlık Görüntü Alıcısı'nı kullanarak veya Sunucu [Gezgini'nden](../debugger/remote-debugging-azure.md)hata [Snapshot Debugger](../debugger/debug-live-azure-applications.md) ayıklayıcıyı takarak önceden yapılandırılmış bir IIS örneğinde ve uzaktan hata ayıklayıcıda kolayca dağıtabilir ve hata ayıklayabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

::: moniker range=">=vs-2019"
Visual Studio 2019 bu makalede gösterilen adımları takip etmek için gereklidir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 bu makalede gösterilen adımları takip etmek için gereklidir.
::: moniker-end

Bu yordamlar bu sunucu yapılandırmalarında sınanmıştır:
* Windows Server 2012 R2 ve IIS 8
* Windows Server 2016 ve IIS 10

## <a name="network-requirements"></a>Ağ gereksinimleri

Proxy üzerinden bağlanan iki bilgisayar arasında hata ayıklama desteklenmez. Çevirmeli Internet gibi yüksek gecikmeli veya düşük bant genişliğine sahip bir bağlantı üzerinden veya ülkeler arasında Internet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya kabul edilemez derecede yavaş olabilir. Gereksinimlerin tam listesi için [Gereksinimler](../debugger/remote-debugging.md#requirements_msvsmon)bölümüne bakın.

## <a name="app-already-running-in-iis"></a>Uygulama zaten IIS çalışan?

Bu makalede, Windows sunucusunda Temel Bir IIS yapılandırması kurma ve uygulamayı Visual Studio'dan dağıtma adımları yer almaktadır. Bu adımlar, sunucunun yüklü bileşenleri olduğundan, uygulamanın doğru şekilde çalıştırabilmesini ve uzaktan hata ayıklama için hazır olduğundan emin olmak için dahildir.

* Uygulamanız IIS'de çalışıyorsa ve uzaktan hata ayıklamayı indirip hata ayıklamaya başlamak istiyorsanız, [Windows Server'daki uzak araçları indirip yükleyin.](#BKMK_msvsmon)

* Hata ayıklama yapabilmeniz için uygulamanızın IIS'de ayarlanıp dağıtıldığınızdan ve doğru şekilde çalıştırdığından emin olmak için yardım istiyorsanız, bu konuyla ilgili tüm adımları izleyin.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarında ASP.NET Core uygulamasını oluşturma

1. Yeni bir ASP.NET Core web uygulaması oluşturun. 

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'da, arama kutusunu açmak için **Ctrl + Q** yazın, **asp.net**yazın, **Şablonlar'ı**seçin, ardından **yeni ASP.NET Core Web Uygulaması oluştur'u**seçin. Görünen iletişim kutusunda, proje **MyASPApp**adını ve sonra **Oluştur'u**seçin. Ardından, **Web Uygulaması (Model-View-Controller) seçeneğini**belirleyin ve ardından **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de **Dosya > Yeni > Projesi'ni**seçin, ardından Visual **C# > Web > ASP.NET Core Web Application'ı**seçin. ASP.NET Çekirdek şablonları bölümünde **Web Uygulaması (Model-View-Controller)** seçeneğini belirleyin. Core 2.1 ASP.NET seçildiğinden, **Docker Desteğini Etkinleştir'in** seçilmediğinden ve **Kimlik Doğrulamanın** **Kimlik Doğrulama yok**olarak ayarlandıklarına emin olun. Proje **MyASPApp**adı .
    ::: moniker-end

4. About.cshtml.cs dosyasını açın ve `OnGet` yöntemde bir kesme noktası ayarlayın (eski şablonlarda, bunun `About()` yerine HomeController.cs açın ve yöntemde kesme noktasını ayarlayın).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Windows Server'da IIS Yükleme ve Yapılandırma

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server'da tarayıcı güvenlik ayarlarını güncelleştirme

Gelişmiş Güvenlik Yapılandırması Internet Explorer'da etkinleştirilmişse (varsayılan olarak etkinleştirilir), bazı web sunucusu bileşenlerini karşıdan yükleyebilmeniz için bazı etki alanlarını güvenilir siteler olarak eklemeniz gerekebilir. **Güvenilen siteleri, Güvenlik > > Güvenilir Siteler > Siteler>e**giderek güvenilir siteleri ekleyin. Aşağıdaki etki alanlarını ekleyin.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Yazılımı karşıdan yüklediğinizde, çeşitli web sitesi komut dosyalarını ve kaynaklarını yüklemek için izin verme isteği alabilirsiniz. Bu kaynaklardan bazıları gerekli değildir, ancak işlemi basitleştirmek için istendiğinde **Ekle'yi** tıklatın.

## <a name="install-aspnet-core-on-windows-server"></a>Windows Server'da ASP.NET Core'u yükleme

1. Barındırma sistemine [.NET Core Windows Server Hosting](https://aka.ms/dotnetcore-2-windowshosting) paketini yükleyin. Pakette .NET Core Runtime, .NET Core Library ve ASP.NET Çekirdek Modülü yüklenir. Daha ayrıntılı talimatlar için [IIS'ye Yayımlama'ya](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)bakın.

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

1. Windows Gezgini'ni açın ve daha sonra ASP.NET Core projesini dağıtacağınız **C:\Yayımla**, yeni bir klasör oluşturun.

2. Zaten açık değilse, **Internet Information Services (IIS) Yöneticisi'ni**açın. (Server Manager'ın sol bölmesinde **IIS'yi**seçin. Sunucuya sağ tıklayın ve **Internet Information Services (IIS) Yöneticisi'ni**seçin.)

3. Sol bölmedeki **Bağlantılar** altında **Siteler'e**gidin.

4. Varsayılan **Web Sitesi'ni**seçin, **Temel Ayarlar'ı**seçin ve **Fiziksel yolu** **C:\Publish'e**ayarlayın.

4. Varsayılan Web **Sitesi** düğümüne sağ tıklayın ve **Uygulama Ekle'yi**seçin.

5. Diğer **Ad** alanını **MyASPApp**olarak ayarlayın, varsayılan Uygulama Havuzunu **(DefaultAppPool)** kabul edin ve **Fiziksel yolu** **C:\Publish'e**ayarlayın.

6. **Bağlantılar** **altında, Uygulama Havuzları'nı**seçin. **DefaultAppPool'u** açın ve Uygulama havuzu alanını **Yönetilen Kod Yok**olarak ayarlayın.

7. IIS Yöneticisi'ndeki yeni siteye sağ tıklayın, **İzinleri Edit'i**seçin ve Web uygulamasına erişmek için yapılandırılan IUSR, IIS_IUSRS veya kullanıcının Oku & Yürüt haklarına sahip yetkili bir kullanıcı olduğundan emin olun.

    Bu kullanıcılardan birini erişimi olan görmüyorsanız, Okuma & Yürüt haklarına sahip bir kullanıcı olarak IUSR eklemek için adımları izleyin.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Visual Studio'dan yerel bir klasöre yayınlayarak uygulamayı yayımlayın ve dağıtın

Ayrıca, dosya sistemini veya diğer araçları kullanarak uygulamayı yayımlayabilir ve dağıtabilirsiniz.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Windows Server'daki uzak araçları indirin ve yükleyin

Visual Studio sürümünüzle eşleşen uzak araçların sürümünü indirin.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Windows Server'da uzaktan hata ayıklama yı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Ek kullanıcılar için izin eklemeniz, kimlik doğrulama modunu veya uzak hata ayıklayıcının bağlantı noktası numarasını değiştirmeniz gerekiyorsa, [bkz.](../debugger/remote-debugging.md#configure_msvsmon)

Uzaktan hata ayıklamayı bir hizmet olarak çalıştırma hakkında bilgi için, [uzaktan hata ayıklamayı hizmet olarak çalıştır'a](../debugger/remote-debugging.md#bkmk_configureService)bakın.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Visual Studio bilgisayarından ASP.NET uygulamasına ekleme

1. Visual Studio bilgisayarında hata ayıklamaya çalıştığınız çözümü açın (Bu makaledeki tüm adımları takip ediyorsanız**MyASPApp).**
2. Visual Studio'da **Hata Ayıklama > İşleme Ekle 'yi** (Ctrl + Alt + P) tıklatın.

    > [!TIP]
    > Visual Studio 2017 ve sonraki sürümlerinde, **Hata Ayıklama > İşleme Yeniden Bağlanma...** (Shift + Alt + P) kullanarak daha önce eklediğiniz aynı işleme yeniden bağlanabilirsiniz.

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

    * IIS'de [uygulama içi barındırma modelini](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) kullanıyorsanız, doğru **w3wp.exe** işlemini seçin. .NET Core 3'ten başlayarak varsayılan değerdir.

    * Aksi takdirde, **dotnet.exe** işlemini seçin. (Bu, işlem dışı barındırma modelidir.)

    *w3wp.exe* veya *dotnet.exe'yi*gösteren birden çok işlem varsa, **Kullanıcı Adı** sütununa bakın. Bazı senaryolarda, **Kullanıcı Adı** sütunu **IIS APPPOOL\DefaultAppPool**gibi uygulama havuzu adınızı gösterir. Uygulama Havuzu'nu görüyorsanız, ancak benzersiz değilse, hata ayıklamak istediğiniz uygulama örneği için yeni bir Adlandırılmış Uygulama Havuzu oluşturun ve ardından **kullanıcı adı** sütununda kolayca bulabilirsiniz.

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

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Sorun giderme: Windows Server'da gerekli bağlantı noktalarını açma

Çoğu kurulumda, gerekli bağlantı noktaları ASP.NET ve uzaktan hata ayıklama nın yüklenmesiyle açılır. Ancak, bağlantı noktalarının açık olduğunu doğrulamanız gerekebilir.

> [!NOTE]
> Azure VM'de, Ağ güvenlik [grubu](/azure/virtual-machines/windows/nsg-quickstart-portal)aracılığıyla bağlantı noktalarını açmanız gerekir.

Gerekli bağlantı noktaları:

* 80 - IIS için gerekli
::: moniker range=">=vs-2019"
* 4024 - Visual Studio 2019'dan uzaktan hata ayıklama için gereklidir (daha fazla bilgi için [Uzaktan Hata Ayıklama Bağlantı Noktası Atamaları'na](../debugger/remote-debugger-port-assignments.md) bakın).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Visual Studio 2017'den uzaktan hata ayıklama için gereklidir (daha fazla bilgi için [Uzaktan Hata Ayıklama Bağlantı Noktası Atamaları'na](../debugger/remote-debugger-port-assignments.md) bakın).
::: moniker-end
* UDP 3702 - (İsteğe bağlı) Discovery bağlantı noktası, Visual Studio'daki uzaktan hata ayıklamaya takarken **Bul** düğmesine basmanızı sağlar.

1. Windows Server'da bir bağlantı noktası açmak için **Başlat** menüsünü açın, **Gelişmiş Güvenlikli Windows Güvenlik Duvarı'nı**arayın.

2. Ardından **Gelen Kurallar > Yeni Kural > Bağlantı Noktası'nı**seçin ve sonra **İleri'yi**tıklatın. (UDP 3702 için, Bunun yerine **Giden Kurallar'ı** seçin.)

3. **Belirli yerel bağlantı noktaları**altında, bağlantı noktası numarasını girin, **İleri'yi**tıklatın.

4. **Bağlantıya İzin Ver'i**tıklatın, **İleri'yi**tıklatın.

5. Bağlantı noktasını etkinleştirmek için bir veya daha fazla ağ türü seçin ve **İleri'yi**tıklatın.

    Seçtiğiniz tür, uzak bilgisayarın bağlı olduğu ağı içermelidir.
6. Gelen Kural için adı (örneğin, **IIS,** **Web Dağıtımı**veya **msvsmon)** ekleyin ve **Bitiş'i**tıklatın.

    Gelen Kurallar veya Giden Kurallar listesinde yeni kuralınızı görmeniz gerekir.

    Windows Güvenlik Duvarı'nı yapılandırma hakkında daha fazla ayrıntı istiyorsanız, [Uzaktan Hata Ayıklama için Windows Güvenlik Duvarını Yapılandır'a](../debugger/configure-the-windows-firewall-for-remote-debugging.md)bakın.

3. Diğer gerekli bağlantı noktaları için ek kurallar oluşturun.
