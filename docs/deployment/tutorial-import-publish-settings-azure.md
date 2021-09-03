---
title: Yayımlama ayarlarını içeri aktararak Azure 'da yayımlayın
description: Visual Studio Azure App Service ' dan bir uygulama dağıtmak için yayımlama profili oluşturma ve içeri aktarma
ms.date: 08/27/2021
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 7d2807480741ff40df82156eea563843bec07712
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398541"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Visual Studio 'de yayımlama ayarlarını içeri aktararak bir uygulamayı Azure App Service yayımlayın

**Yayımla aracını kullanarak** yayınlama ayarlarını içeri aktarabilir ve ardından uygulamanızı dağıtabilirsiniz. Bu makalede, Azure App Service için yayımlama ayarlarını kullanırız, ancak yayımlama ayarlarını [IIS](../deployment/tutorial-import-publish-settings-iis.md)'den içe aktarmak için de benzer adımları kullanabilirsiniz. Bazı senaryolarda, bir yayımlama ayarları profili kullanımı, her Visual Studio yüklemesi için hizmete dağıtımı el ile yapılandırmadan daha hızlı olabilir.

bu adımlar Visual Studio ' de ASP.NET, ASP.NET Core ve .net Core uygulamaları için geçerlidir. Ayrıca, [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) uygulamaları için yayımlama ayarlarını içeri aktarabilirsiniz.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Azure App Service bir yayımlama ayarları dosyası oluştur
> * Yayımlama ayarları dosyasını Visual Studio içine aktarın
> * Uygulamayı Azure App Service dağıtma

Bir yayımlama ayarları dosyası (*\* . publishsettings*) Visual Studio oluşturulan yayımlama profilinden (*\* . pubxml*) farklıdır. Bir yayımlama ayarları dosyası Azure App Service tarafından oluşturulur ve Visual Studio içine aktarılabilir.

> [!NOTE]
> bir Visual Studio yayımlama profilini (*\* . pubxml* dosyası) bir Visual Studio yüklemesinden diğerine kopyalamanız gerekiyorsa, yönetilen proje türleri için *\\<projectname \> \Properties\PublishProfiles* klasöründe, *\<profilename\> . pubxml* yayımlama profilini bulabilirsiniz. Web siteleri için *\ App_Data* klasörü altına bakın. yayımlama profilleri MSBuild XML dosyalarıdır.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* Visual Studio 2019 yüklü ve **ASP.NET ve web geliştirme** iş yüküne sahip olmanız gerekir.

    Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz yükleme yapın.
::: moniker-end

::: moniker range="vs-2017"

* Visual Studio 2017 yüklü ve **ASP.NET ve web geliştirme** iş yüküne sahip olmanız gerekir.

    Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz yükleme yapın.
::: moniker-end

* Azure App Service oluşturun. ayrıntılı yönergeler için bkz. [Visual Studio kullanarak Azure 'a ASP.NET Core web uygulaması dağıtma](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio yeni ASP.NET projesi oluşturma

1. Visual Studio çalıştıran bilgisayarda yeni bir proje oluşturun.

    Doğru şablonu seçin. bu örnekte, **ASP.NET web uygulaması (.NET Framework)** veya (yalnızca C# için) **web uygulaması ASP.NET Core** seçin ve ardından **tamam**' ı seçin.

    belirtilen proje şablonlarını görmüyorsanız, **yeni Project** iletişim kutusunun sol bölmesindeki **aç Visual Studio Yükleyicisi** bağlantısına gidin. Visual Studio Yükleyicisi başlatılır. **ASP.NET ve web geliştirme** iş yükünü yükler.

    seçtiğiniz proje şablonu (ASP.NET veya ASP.NET Core), web sunucusunda yüklü ASP.NET sürümüne karşılık gelmelidir.

1. **MVC** (.NET Framework) veya **Web uygulaması (Model-View-Controller)** ' ı (.net Core için) seçin ve **kimlik doğrulamasının** seçili olmadığından emin olun ve ardından **tamam**' ı seçin.

1. **MyWebApp** gibi bir ad yazın ve **Tamam**' ı seçin.

    Visual Studio projeyi oluşturur.

1.   >  Projeyi derlemek için derleme **Yapı çözümünü** seçin.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Azure App Service yayımlama ayarları dosyasını oluşturun

1. Azure portal, Azure App Service açın.

1. **Yayımlama profilini al** ' a gidin ve profili yerel olarak kaydedin.

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
        destinationAppUrl="http://deployaspdotnetcore2021.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```

    genellikle, önceki *. publishsettings dosyası Visual Studio kullanabileceğiniz iki yayımlama profili içerir, biri Web Dağıtımı kullanarak dağıtılır ve biri de FTP kullanarak dağıtılır. Yukarıdaki kod Web Dağıtımı profilini gösterir. Profili içeri aktardığınızda, her iki profil de içeri aktarılır.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Sonraki adımlar

bu öğreticide, bir yayımlama ayarları dosyası oluşturdunuz, onu Visual Studio içeri aktardınız ve Azure App Service için bir ASP.NET uygulaması dağıttınız. Visual Studio yayımlama seçeneklerine genel bir bakış isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md)
