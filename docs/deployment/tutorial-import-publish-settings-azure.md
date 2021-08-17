---
title: Yayımlama ayarlarını içeri aktararak Azure'da yayımlama
description: Bir uygulamayı Visual Studio'den Azure App Service
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 18231d36d5aef25917dccde045cad739848ef3f19bc840cac76753636c4bfc03
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390946"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Yayımlama ayarlarını Azure App Service içeri aktararak bir uygulamayı Visual Studio

Yayımlama ayarlarını içeri **aktarın** ve ardından uygulamanızı dağıtmak için Yayımla aracını kullanabilirsiniz. Bu makalede, yayımlama ayarlarını Azure App Service, ancak yayımlama ayarlarını IIS'den içeri aktarmaya benzer adımları [kullanabilirsiniz.](../deployment/tutorial-import-publish-settings-iis.md) Bazı senaryolarda, yayımlama ayarları profilinin kullanımı, her bir dağıtım profili yüklemesi için hizmete dağıtımı el ile yapılandırmaktan Visual Studio.

Bu adımlar, ASP.NET, ASP.NET Core ve .NET Core uygulamaları için Visual Studio. Python uygulamaları için yayımlama ayarlarını da içeri [aktarabilirsiniz.](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Dosyadan yayımlama ayarları Azure App Service
> * Yayımlama ayarları dosyasını Visual Studio
> * Uygulamayı Azure App Service

Yayımlama ayarları dosyası (*\* .publishsettings*) bir yayımlama profilinden (*\* .pubxml*) farklı Visual Studio. Yayımlama ayarları dosyası, Azure App Service tarafından oluşturulur ve ardından Visual Studio.

> [!NOTE]
> Bir Visual Studio yayımlama profilini *\* (.pubxml* dosyası) bir Visual Studio yüklemesinde diğerine kopyalamanız gerekirse, yönetilen proje türleri için *\\<projeadı \> \Properties\PublishProfiles* klasöründe *\<profilename\> .pubxml* yayımlama profilini bulabilirsiniz. Web siteleri için *\App_Data klasörünün altına* bakın. Yayımlama profilleri XML MSBuild için kullanılır.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* Visual Studio 2019'un yüklü olması ve ASP.NET **web geliştirme iş yükünüz olması** gerekir.

    Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz yükleyin.
::: moniker-end

::: moniker range="vs-2017"

* Visual Studio 2017'nin yüklü olması ve ASP.NET **web geliştirme iş yükünüz olması** gerekir.

    Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz yükleyin.
::: moniker-end

* Yeni bir Azure App Service. Ayrıntılı yönergeler için [bkz. ASP.NET Core kullanarak Azure'a Visual Studio.](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio'ASP.NET yeni bir Visual Studio

1. Visual Studio çalıştıran bilgisayarda yeni bir proje oluşturun.

    Doğru şablonu seçin. Bu örnekte, Web Uygulaması **ASP.NET (.NET Framework)** veya (yalnızca C# için) seçeneğini ASP.NET Core **tamam'ı** **seçin.**

    Belirtilen proje şablonlarını görmüyorsanız, Yeni Visual Studio Yükleyicisi  iletişim kutusunun sol bölmesindeki Aç **bağlantısına Project** gidin. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET yüklerini** yükleyin.

    Seçtiğiniz proje şablonunun (ASP.NET veya ASP.NET Core) web sunucusunda yüklü ASP.NET sürümüne karşılık olması gerekir.

1. **MVC** (.NET Framework) veya Web Uygulaması **(Model-View-Controller) (.NET** Core için)  öğesini seçin ve Kimlik Doğrulaması Yok seçeneğinin seçili olduğundan emin olun ve tamam'ı **seçin.**

1. **MyWebApp** gibi bir ad yazın ve Tamam'ı **seçin.**

    Visual Studio projeyi oluşturur.

1. Projeyi   >  **derlemek için Derleme** Çözümü'ne seçin.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Azure App Service'de yayımlama ayarları dosyasını oluşturma

1. Aşağıdaki Azure portal açın Azure App Service.

1. Yayımlama profili **al'a gidin** ve profili yerel olarak kaydedin.

    ![Yayımlama profilini al](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    *.publishsettings dosya* uzantısına sahip bir dosya, dosyayı kaydeden konumda oluşturulmuş. Aşağıdaki kod, dosyanın kısmi bir örneğini gösterir (daha okunabilir bir biçimlendirmede).

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

    Genellikle, önceki *.publishsettings dosyası, Visual Studio'de kullanabileceğiniz iki yayımlama profili içerir, biri Web Dağıtımı kullanarak dağıtım yapmak ve biri FTP kullanarak dağıtmak için. Yukarıdaki kod, Web Dağıtımı gösterir. Profili daha sonra içeri aktararak her iki profil de içeri aktarılır.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Yayımlama ayarlarını içeri aktarma Visual Studio dağıtma

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide bir yayımlama ayarları dosyası oluşturdunız, dosyayı Visual Studio aktardınız ve ASP.NET bir Azure App Service. Uygulama içinde yayımlama seçeneklerine genel bir bakış Visual Studio.

> [!div class="nextstepaction"]
> [Dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md)
