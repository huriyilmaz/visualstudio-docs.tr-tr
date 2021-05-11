---
title: Yayımlama ayarlarını içeri aktararak IIS'de yayımlama
description: Bir uygulamayı IIS'ye dağıtmak için yayımlama profili oluşturma Visual Studio içeri aktarma
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aeaaff68ab0abe85838456e8c8b69e2520295689
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729279"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Visual Studio'de yayımlama ayarlarını içeri aktararak bir uygulamayı IIS'Visual Studio

Yayımlama ayarlarını içeri **aktarın** ve ardından uygulamanızı dağıtmak için Yayımla aracını kullanabilirsiniz. Bu makalede IIS için yayımlama ayarlarını kullanacağız ancak yayımlama ayarlarını içeri aktarmaya benzer adımları [Azure App Service.](../deployment/tutorial-import-publish-settings-azure.md) Bazı senaryolarda, yayımlama ayarları profilinin kullanımı, her bir yayımlama profili yüklemesi için IIS'ye dağıtımı el ile yapılandırmaktan Visual Studio.

Bu adımlar ASP.NET, ASP.NET Core ve .NET Core uygulamaları için Visual Studio.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Yayımlama ayarları dosyası oluşturamıyorsanız IIS'yi yapılandırma
> * Yayımlama ayarları dosyası oluşturma
> * Yayımlama ayarları dosyasını Visual Studio
> * Uygulamayı IIS'ye dağıtma

Yayımlama ayarları dosyası (*\* .publishsettings*) bir yayımlama profilinden (*\* .pubxml*) farklı Visual Studio. Yayımlama ayarları dosyası IIS veya Azure App Service tarafından oluşturulur ya da el ile oluşturulabilir ve ardından Visual Studio.

> [!NOTE]
> Visual Studio yayımlama profilini (.pubxml dosyası) Visual Studio yüklemelerinden diğerine kopyalamanız gerekirse, yönetilen proje türleri için \* *\\<projeadı \> \Properties\PublishProfiles* klasöründe yayımlama profilini *\<profilename\> (.pubxml)* bulabilirsiniz. Web siteleri için *\App_Data klasörünün altına* bakın. Yayımlama profilleri MSBuild XML dosyalarıdır.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* Visual Studio 2019'un yüklü olması ve ASP.NET **web geliştirme iş yükünüz olması** gerekir.

    Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz yükleyin.
::: moniker-end

::: moniker range="vs-2017"

* 2017 Visual Studio ve web geliştirme iş ASP.NET **yüklü olması** gerekir.

    Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz yükleyin.
::: moniker-end

* Sunucunuzda, Windows Server 2012, Windows Server 2016 veya Windows Server 2019 çalıştırıyor olmanız gerekir ve [IIS Web sunucusu rolünün](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) doğru şekilde yüklenmiş olması gerekir (yayımlama ayarları dosyası (*\* . publishsettings*) oluşturmak için gereklidir). ASP.NET 4,5 veya ASP.NET Core da sunucuda yüklü olmalıdır. ASP.NET 4,5 'yi ayarlamak için bkz. [ASP.NET 3,5 ve ASP.NET 4,5 kullanarak ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). ASP.NET Core ayarlamak için bkz. [IIS Ile Windows üzerinde konak ASP.NET Core](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). ASP.NET Core için uygulama havuzunu makalede açıklandığı gibi, **yönetilen kod olmadan** kullanmak üzere yapılandırdığınızdan emin olun.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio 'da yeni bir ASP.NET projesi oluşturma

1. Visual Studio çalıştıran bilgisayarda yeni bir proje oluşturun.

    Doğru şablonu seçin. Bu örnekte, **ASP.NET Web uygulaması (.NET Framework)** veya (yalnızca C# için **ASP.NET Core) Web uygulaması**' nı seçin ve ardından **Tamam**' ı seçin.

    Belirtilen proje şablonlarını görmüyorsanız, **Yeni proje** iletişim kutusunun sol bölmesindeki **Aç Visual Studio yükleyicisi** bağlantısına gidin. Visual Studio Yükleyicisi başlatılır. **ASP.net ve Web geliştirme** iş yükünü yükler.

    Seçtiğiniz proje şablonu (ASP.NET veya ASP.NET Core), Web sunucusunda yüklü ASP.NET sürümüne karşılık gelmelidir.

1. **MVC** (.NET Framework) veya **Web uygulaması (Model-View-Controller)** ' ı (.NET Core Için) seçin ve **kimlik doğrulamasının** seçili olmadığından emin olun ve ardından **Tamam**' ı seçin.

1. **MyWebApp** gibi bir ad yazın ve **Tamam**' ı seçin.

    Visual Studio projeyi oluşturur.

1.   >  Projeyi derlemek için Build **Build Solution** (veya **CTRL**  +  **SHIFT**  +  **B** tuşlarına basın) öğesini seçin.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Windows Server 'da Web Dağıtımı yükleyip yapılandırma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server 'da IIS 'de yayımlama ayarları dosyası oluşturma

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio 'da yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlatılır. Bu, uygulamanın başlangıç Visual Studio IIS'de başlatabilirsiniz. ASP.NET Core için **DefaultAppPool** için Uygulama havuzu alanı'nın Yönetilen Kod Yok olarak ayarlanmış **olduğundan emin olun.**

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide bir yayımlama ayarları dosyası oluşturdunız, dosyayı Visual Studio aktardınız ve IIS'ye ASP.NET uygulama dağıttınız. Aşağıdaki diğer yayımlama seçeneklerine genel bir bakış Visual Studio.

> [!div class="nextstepaction"]
> [Dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md)
