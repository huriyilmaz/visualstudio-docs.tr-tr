---
title: Yayımlama ayarlarını içeri aktararak IIS 'de yayımlayın
description: Visual Studio 'dan IIS 'e uygulama dağıtmak için Yayımlama profili oluşturma ve içeri aktarma
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fff3ded8607f7faf534e6e61a27bd4d3e38d9e38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88247560"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Visual Studio 'da yayımlama ayarlarını içeri aktararak IIS 'de uygulama yayımlama

**Yayımla aracını kullanarak** yayınlama ayarlarını içeri aktarabilir ve ardından uygulamanızı dağıtabilirsiniz. Bu makalede, IIS için yayımlama ayarlarını kullanırız, ancak [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md)yayımlama ayarlarını içeri aktarmak için de benzer adımları kullanabilirsiniz. Bazı senaryolarda, bir yayımlama ayarları profili kullanımı, Visual Studio 'nun her yüklemesi için IIS 'e dağıtımı el ile yapılandırmadan daha hızlı olabilir.

Bu adımlar, Visual Studio 'da ASP.NET, ASP.NET Core ve .NET Core uygulamaları için geçerlidir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Bir yayımlama ayarları dosyası oluşturabilmeniz için IIS 'yi yapılandırma
> * Yayımlama ayarları dosyası oluşturma
> * Yayımlama ayarları dosyasını Visual Studio 'ya aktarma
> * Uygulamayı IIS 'ye dağıtma

Yayımlama ayarları dosyası (* \* . publishsettings*), Visual Studio 'da oluşturulan yayımlama profilinden (* \* . pubxml*) farklıdır. Bir yayımlama ayarları dosyası IIS veya Azure App Service tarafından oluşturulur veya el ile oluşturulabilir ve sonra Visual Studio 'ya aktarılabilir.

> [!NOTE]
> Visual Studio yayımlama profilini ( \* . pubxml dosyası) bir Visual Studio yüklemesinden diğerine kopyalamanız gerekiyorsa, yönetilen proje türleri için * \\<ProjectName \> \Properties\PublishProfiles* klasöründe yayımlama profilini * \<profilename\> . pubxml*bulabilirsiniz. Web siteleri için *\ App_Data* klasörü altına bakın. Yayımlama profilleri MSBuild XML dosyalarıdır.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* Visual Studio 2019 ' nin yüklü olması ve **ASP.net ve Web geliştirme** iş yüküne sahip olmanız gerekir.

    Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.
::: moniker-end

::: moniker range="vs-2017"

* Visual Studio 2017 ' nin yüklü olması ve **ASP.net ve Web geliştirme** iş yüküne sahip olmanız gerekir.

    Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.
::: moniker-end

* Sunucunuzda, Windows Server 2012, Windows Server 2016 veya Windows Server 2019 çalıştırıyor olmanız gerekir ve [IIS Web sunucusu rolünün](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) doğru şekilde yüklenmiş olması gerekir (yayımlama ayarları dosyası (* \* . publishsettings*) oluşturmak için gereklidir). ASP.NET 4,5 veya ASP.NET Core da sunucuda yüklü olmalıdır. ASP.NET 4,5 'yi ayarlamak için bkz. [ASP.NET 3,5 ve ASP.NET 4,5 kullanarak ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). ASP.NET Core ayarlamak için bkz. [IIS Ile Windows üzerinde konak ASP.NET Core](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). ASP.NET Core için uygulama havuzunu makalede açıklandığı gibi, **yönetilen kod olmadan**kullanmak üzere yapılandırdığınızdan emin olun.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio 'da yeni bir ASP.NET projesi oluşturma

1. Visual Studio çalıştıran bilgisayarda yeni bir proje oluşturun.

    Doğru şablonu seçin. Bu örnekte, **ASP.NET Web uygulaması (.NET Framework)** veya (yalnızca C# için **ASP.NET Core) Web uygulaması**' nı seçin ve ardından **Tamam**' ı seçin.

    Belirtilen proje şablonlarını görmüyorsanız, **Yeni proje** iletişim kutusunun sol bölmesindeki **Aç Visual Studio yükleyicisi** bağlantısına gidin. Visual Studio Yükleyicisi başlatılır. **ASP.net ve Web geliştirme** iş yükünü yükler.

    Seçtiğiniz proje şablonu (ASP.NET veya ASP.NET Core), Web sunucusunda yüklü ASP.NET sürümüne karşılık gelmelidir.

1. **MVC** (.NET Framework) veya **Web uygulaması (Model-View-Controller)** ' ı (.NET Core Için) seçin ve **kimlik doğrulamasının** seçili olmadığından emin olun ve ardından **Tamam**' ı seçin.

1. **MyWebApp** gibi bir ad yazın ve **Tamam**' ı seçin.

    Visual Studio projeyi oluşturur.

1. **Build**  >  Projeyi derlemek için derleme**Yapı çözümünü** seçin.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Windows Server 'da Web Dağıtımı yükleyip yapılandırma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server 'da IIS 'de yayımlama ayarları dosyası oluşturma

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio 'da yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlamalıdır. Visual Studio 'dan başlamazsa uygulamayı IIS 'de başlatın. ASP.NET Core için, **DefaultAppPool** için uygulama havuzu alanının **yönetilen kod yok**olarak ayarlandığından emin olmanız gerekir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir yayımlama ayarları dosyası oluşturdunuz, Visual Studio 'ya içeri aktardınız ve IIS 'e bir ASP.NET uygulaması dağıttınız. Visual Studio 'daki diğer yayımlama seçeneklerine genel bir bakış da isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md)
