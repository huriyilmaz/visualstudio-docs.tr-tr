---
title: Yayımlama ayarlarını içeri aktararak Azure 'da yayımlayın
description: Visual Studio 'dan Azure App Service 'e uygulama dağıtmak için Yayımlama profili oluşturma ve içeri aktarma
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd316956f8e6c385cd59c017af50452b07537dc6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183320"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Visual Studio 'da yayımlama ayarlarını içeri aktararak uygulama Azure App Service yayımlayın

**Yayımla aracını kullanarak** yayınlama ayarlarını içeri aktarabilir ve ardından uygulamanızı dağıtabilirsiniz. Bu makalede, Azure App Service için yayımlama ayarlarını kullanırız, ancak yayımlama ayarlarını [IIS](../deployment/tutorial-import-publish-settings-iis.md)'den içe aktarmak için de benzer adımları kullanabilirsiniz. Bazı senaryolarda, bir yayımlama ayarları profili kullanımı, her Visual Studio yüklemesi için hizmete dağıtımı el ile yapılandırmadan daha hızlı olabilir.

Bu adımlar, Visual Studio 'da ASP.NET, ASP.NET Core ve .NET Core uygulamaları için geçerlidir. Ayrıca, [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) uygulamaları için yayımlama ayarlarını içeri aktarabilirsiniz.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Azure App Service bir yayımlama ayarları dosyası oluştur
> * Yayımlama ayarları dosyasını Visual Studio 'ya aktarma
> * Uygulamayı Azure App Service dağıtma

Yayımlama ayarları dosyası (* \* . publishsettings*), Visual Studio 'da oluşturulan yayımlama profilinden (* \* . pubxml*) farklıdır. Bir yayımlama ayarları dosyası Azure App Service tarafından oluşturulur ve ardından Visual Studio 'ya aktarılabilir.

> [!NOTE]
> Visual Studio yayımlama profilini (* \* . pubxml* dosyası) bir Visual Studio yüklemesinden diğerine kopyalamanız gerekiyorsa, yönetilen proje türleri için * \\<ProjectName \> \Properties\PublishProfiles* klasöründe yayımlama profilini * \<profilename\> . pubxml*bulabilirsiniz. Web siteleri için *\ App_Data* klasörü altına bakın. Yayımlama profilleri MSBuild XML dosyalarıdır.

## <a name="prerequisites"></a>Ön koşullar

::: moniker range=">=vs-2019"

* Visual Studio 2019 ' nin yüklü olması ve **ASP.net ve Web geliştirme** iş yüküne sahip olmanız gerekir.

    Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.
::: moniker-end

::: moniker range="vs-2017"

* Visual Studio 2017 ' nin yüklü olması ve **ASP.net ve Web geliştirme** iş yüküne sahip olmanız gerekir.

    Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.
::: moniker-end

* Azure App Service oluşturun. Ayrıntılı yönergeler için bkz. [Visual Studio kullanarak Azure 'da ASP.NET Core Web uygulaması dağıtma](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio 'da yeni bir ASP.NET projesi oluşturma

1. Visual Studio çalıştıran bilgisayarda yeni bir proje oluşturun.

    Doğru şablonu seçin. Bu örnekte, **ASP.NET Web uygulaması (.NET Framework)** veya (yalnızca C# için **ASP.NET Core) Web uygulaması**' nı seçin ve ardından **Tamam**' a tıklayın.

    Belirtilen proje şablonlarını görmüyorsanız, **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** bağlantısına tıklayın. Visual Studio Yükleyicisi başlatılır. **ASP.net ve Web geliştirme** iş yükünü yükler.

    Seçtiğiniz proje şablonu (ASP.NET veya ASP.NET Core), Web sunucusunda yüklü ASP.NET sürümüne karşılık gelmelidir.

1. **MVC** (.NET Framework) veya **Web uygulaması (Model-View-Controller)** seçeneğini belirleyin (.NET Core Için) ve **kimlik doğrulama** olmadığından emin olun ve ardından **Tamam**' a tıklayın.

1. **MyWebApp** gibi bir ad yazın ve **Tamam**' a tıklayın.

    Visual Studio projeyi oluşturur.

1. **Build**  >  Projeyi derlemek için derleme**Yapı çözümünü** seçin.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Azure App Service yayımlama ayarları dosyasını oluşturun

1. Azure portal, Azure App Service açın.

1. **Yayımlama profilini al** ' a tıklayın ve profili yerel olarak kaydedin.

    ![Yayımlama profilini al](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    *. Publishsettings* dosya uzantısına sahip bir dosya, kaydettiğiniz konumda oluşturulmuştur. Aşağıdaki kod, dosyanın kısmi bir örneğini gösterir (daha okunabilir bir biçimlendirmeye).

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

    Genellikle, önceki *. publishsettings dosyası, Visual Studio 'da kullanabileceğiniz iki yayımlama profili içerir, biri Web Dağıtımı kullanarak dağıtılır ve bir FTP kullanarak dağıtabilirsiniz. Yukarıdaki kod Web Dağıtımı profilini gösterir. Profili içeri aktardığınızda, her iki profil de içeri aktarılır.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio 'da yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir yayımlama ayarları dosyası oluşturdunuz, Visual Studio 'ya içeri aktardınız ve Azure App Service için bir ASP.NET uygulaması dağıttınız. Visual Studio 'da yayımlama seçeneklerine genel bir bakış da isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md)
