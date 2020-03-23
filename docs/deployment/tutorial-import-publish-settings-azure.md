---
title: Yayımlama ayarlarını içe aktararak Azure'da yayımlama
description: Visual Studio'dan Azure Uygulama Hizmeti'ne uygulama dağıtmak için yayımlama profili oluşturma ve alma
ms.date: 05/07/2018
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd040b613a5b982050d651f341456c5fafc2954b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "65679183"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Visual Studio'da yayımlama ayarlarını içe aktararak bir uygulamayı Azure Uygulama Hizmetine yayımlama

Yayımlama ayarlarını içe aktarıp uygulamanızı dağıtmak için **Yayımla** aracını kullanabilirsiniz. Bu makalede, Azure Uygulama Hizmeti için yayımlama ayarlarını kullanıyoruz, ancak Yayımlama ayarlarını [IIS'den](../deployment/tutorial-import-publish-settings-iis.md)almak için benzer adımları kullanabilirsiniz. Bazı senaryolarda, yayımlama ayarları profilinin kullanımı, Visual Studio'nun her kurulumu için dağıtımın hizmete el ile yapılandırılmasından daha hızlı olabilir.

Bu adımlar Visual Studio'daki ASP.NET, ASP.NET Core ve .NET Core uygulamaları için geçerlidir. [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) uygulamaları için yayımlama ayarlarını da içe aktarabilirsiniz.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Azure Uygulama Hizmeti'nden yayımlama ayarları dosyası oluşturma
> * Yayımlama ayarları dosyasını Visual Studio'ya alma
> * Uygulamayı Azure Uygulama Hizmetine dağıtma

Yayımlama ayarları dosyası (*\*.publishsettings*) Visual Studio'da oluşturulan yayımlama profilinden*\*(.pubxml)* farklıdır. Bir yayımlama ayarları dosyası Azure App Service tarafından oluşturulur ve daha sonra Visual Studio'ya aktarılabilir.

> [!NOTE]
> Visual Studio'nun bir yüklemesinden diğerine visual studio yayın profili*\*(.pubxml* dosyası) kopyalamanız gerekirse, yönetilen proje türleri için * \\<\>proje adı \Properties\PublishProfiles* klasöründe yayımlama profilini, * \<profilename\>.pubxml'ı*bulabilirsiniz. Web siteleri için *\App_Data* klasörüne bakın. Yayımlama profilleri MSBuild XML dosyalarıdır.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* Visual Studio 2019 yüklü ve **ASP.NET ve web geliştirme** iş yükünü olmalıdır.

    Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
::: moniker-end

::: moniker range="vs-2017"

* Visual Studio 2017'yi ve **ASP.NET ve web geliştirme** iş yükünü yüklemelisiniz.

    Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
::: moniker-end

* Azure Uygulama Hizmeti oluşturun. Ayrıntılı talimatlar için Visual [Studio'ASP.NET Core web uygulamasını Azure'a dağıt'a](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)bakın.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio'da yeni bir ASP.NET projesi oluşturun

1. Visual Studio'yu çalıştıran bilgisayarda yeni bir proje oluşturun.

    Doğru şablonu seçin. Bu örnekte, **ASP.NET Web Uygulaması (.NET Framework)** veya (yalnızca C# için) **ASP.NET Core Web Application'ı**seçin ve ardından **Tamam'ı**tıklatın.

    Belirtilen proje şablonlarını görmüyorsanız, **Yeni Proje** iletişim kutusunun sol bölmesinde Görsel **Stüdyo Yükleyiciaç'ı Aç** bağlantısını tıklatın. Visual Studio Installer başlattı. ASP.NET ve web geliştirme iş yükünü **yükleyin.**

    Seçtiğiniz proje şablonu (ASP.NET veya ASP.NET Core) web sunucusunda yüklü ASP.NET sürümüne karşılık gelmelidir.

1. **MVC** (.NET Framework) veya **Web Uygulaması (Model-View-Controller) (.NET** Core için) seçeneğini belirleyin ve Kimlik **Doğrulama'nın seçilmediğinden** emin olun ve **ardından Tamam'ı**tıklatın.

1. **MyWebApp** gibi bir ad yazın ve **Tamam'ı**tıklatın.

    Visual Studio projeyi oluşturur.

1. Projeyi oluşturmak için **Yapı** > **Çözüm'u** seçin.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Azure Uygulama Hizmeti'nde yayımlama ayarları dosyasını oluşturma

1. Azure portalında Azure Uygulama Hizmeti'ni açın.

1. **Profili yayımla'yı** ve profili yerel olarak kaydet'i tıklatın.

    ![Yayımlama profilini alın](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Kaydettiğiniz konumda *.publishsettings* dosya uzantısı içeren bir dosya oluşturuldu. Aşağıdaki kod, dosyanın kısmi bir örneğini (daha okunabilir bir biçimlendirmede) gösterir.

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```

    Genellikle, önceki *.publishsettings dosyası Visual Studio'da kullanabileceğiniz iki yayımlama profili, biri Web Dağıtımı'nı kullanarak dağıtmak için ve diğeri ftp kullanarak dağıtmak için. Önceki kod Web Dağıtımı profilini gösterir. Profili içe aktardığınızda her iki profil de daha sonra alınır.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio'da yayımlama ayarlarını içe aktarma ve dağıtma

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, bir yayımlama ayarları dosyası oluşturdunuz, Visual Studio'ya aktardın ve Azure Uygulama Hizmeti'ne bir ASP.NET uygulaması dağıttınız. Visual Studio'daki yayımlama seçeneklerine genel bir bakış isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md)
