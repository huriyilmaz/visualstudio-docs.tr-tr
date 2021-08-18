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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 53b7a6d482573b0eec4f3357c839b651a93fd282
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035598"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Visual Studio'de yayımlama ayarlarını içeri aktararak bir uygulamayı IIS'Visual Studio

Yayımlama ayarlarını içeri **aktarın** ve ardından uygulamanızı dağıtmak için Yayımla aracını kullanabilirsiniz. Bu makalede, IIS için yayımlama ayarlarını kullanacağız, ancak yayımlama ayarlarını içeri aktarmaya benzer adımları [Azure App Service.](../deployment/tutorial-import-publish-settings-azure.md) Bazı senaryolarda, yayımlama ayarları profilinin kullanımı, her bir yayımlama profili yüklemesi için IIS'ye dağıtımı el ile yapılandırmaktan Visual Studio.

Bu adımlar, ASP.NET, ASP.NET Core ve .NET Core uygulamaları için Visual Studio.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Yayımlama ayarları dosyası oluşturamıyorsanız IIS'yi yapılandırma
> * Yayımlama ayarları dosyası oluşturma
> * Yayımlama ayarları dosyasını Visual Studio
> * Uygulamayı IIS'ye dağıtma

Yayımlama ayarları dosyası (*\* .publishsettings*), bir yayımlama profilinden (*\* .pubxml*) farklı Visual Studio. Yayımlama ayarları dosyası IIS veya Azure App Service tarafından oluşturulur ya da el ile oluşturulabilir ve daha sonra Visual Studio.

> [!NOTE]
> Visual Studio yayımlama profilini (.pubxml dosyası) Visual Studio yüklemelerinden diğerine kopyalamanız gerekirse, yönetilen proje türleri için \* *\\<projeadı \> \Properties\PublishProfiles* klasöründe yayımlama profilini *\<profilename\> (.pubxml)* bulabilirsiniz. Web siteleri için *\App_Data klasörünün altına* bakın. Yayımlama profilleri XML MSBuild için kullanılır.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* Visual Studio 2019'un yüklü olması ve ASP.NET **web geliştirme iş yükünüz olması** gerekir.

    Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz yükleyin.
::: moniker-end

::: moniker range="vs-2017"

* Visual Studio 2017'nin yüklü olması ve ASP.NET **web geliştirme iş yükünüz olması** gerekir.

    Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz yükleyin.
::: moniker-end

* Sunucunuzda Windows Server 2012, Windows Server 2016 veya Windows Server 2019 çalıştırmanız ve [IIS Web Sunucusu](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) rolünün doğru yüklenmiş olması gerekir (yayımlama ayarları dosyasını oluşturmak için gereklidir (*\* .publishsettings*)). 4 ASP.NET 4.5 veya ASP.NET Core sunucuya da yüklü olması gerekir. 4.5 ASP.NET ayarlamak için bkz. [IIS 8.0 ASP.NET 3.5 ve ASP.NET 4.5 kullanma.](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) Yapılandırmayı ayarlamak ASP.NET Core bkz. [IIS ile ASP.NET Core konak Windows üzerinde konak oluşturma.](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) Daha ASP.NET Core için, Uygulama Havuzunu makalede açıklandığı gibi Yönetilen Kod **Yok**'yi kullanmak üzere yapılandırıldığından emin olun.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio'ASP.NET yeni bir Visual Studio

1. Visual Studio çalıştıran bilgisayarda yeni bir proje oluşturun.

    Doğru şablonu seçin. Bu örnekte, Web Uygulaması **ASP.NET (.NET Framework)** veya (yalnızca C# için) seçeneğini ASP.NET Core **tamam'ı** **seçin.**

    Belirtilen proje şablonlarını görmüyorsanız, Yeni Visual Studio Yükleyicisi  iletişim kutusunun sol bölmesindeki **Aç bağlantısına** Project gidin. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET yüklerini** yükleyin.

    Seçtiğiniz proje şablonunun (ASP.NET veya ASP.NET Core) web sunucusunda yüklü ASP.NET sürümüne karşılık olması gerekir.

1. **MVC** (.NET Framework) veya Web Uygulaması **(Model-View-Controller) (.NET** Core için)  öğesini seçin ve Kimlik Doğrulaması Yok seçeneğinin seçili olduğundan emin olun ve tamam'ı **seçin.**

1. **MyWebApp** gibi bir ad yazın ve Tamam'ı **seçin.**

    Visual Studio projeyi oluşturur.

1. Projeyi   >  **derlemek için Derleme** Çözümü'lerini seçin **(veya Ctrl**  +  **Shift**  +  **B** tuşlarına basın).

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Windows Server'Web Dağıtımı yükleme ve yapılandırma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server'da IIS'de yayımlama ayarları dosyasını oluşturma

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Yayımlama ayarlarını içeri aktarma Visual Studio dağıtma

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlatılır. Bu, uygulamanın başlangıç Visual Studio IIS'de başlatabilirsiniz. Daha ASP.NET Core için **DefaultAppPool** için Uygulama havuzu alanı'nın Yönetilen Kod Yok olarak ayarlanmış **olduğundan emin olun.**

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide bir yayımlama ayarları dosyası oluşturdunız, bu dosyayı Visual Studio aktardınız ve IIS'ye ASP.NET uygulama dağıttınız. Uygulama içinde diğer yayımlama seçeneklerine genel bir bakış Visual Studio.

> [!div class="nextstepaction"]
> [Dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md)
