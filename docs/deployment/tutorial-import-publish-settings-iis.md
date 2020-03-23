---
title: Yayımlama ayarlarını içe aktararak IIS'ye yayımlama
description: Visual Studio'dan IIS'ye bir uygulama dağıtmak için bir yayımlama profili oluşturma ve alma
ms.date: 01/31/2019
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e0c7309f52fbc8056f09e5a59afcfdefaa8d0bf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "65680134"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Visual Studio'da yayımlama ayarlarını içe aktararak IIS'ye bir uygulama yayımlama

Yayımlama ayarlarını içe aktarıp uygulamanızı dağıtmak için **Yayımla** aracını kullanabilirsiniz. Bu makalede, IIS için yayımlama ayarlarını kullanıyoruz, ancak [Azure Uygulama Hizmeti](../deployment/tutorial-import-publish-settings-azure.md)için yayımlama ayarlarını almak için benzer adımları kullanabilirsiniz. Bazı senaryolarda, yayımlama ayarları profilinin kullanımı, Visual Studio'nun her kurulumu için dağıtımı IIS'e el ile yapılandırmaktan daha hızlı olabilir.

Bu adımlar Visual Studio'daki ASP.NET, ASP.NET Core ve .NET Core uygulamaları için geçerlidir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Yayımlama ayarları dosyası oluşturabilmeniz için IIS'yi yapılandır
> * Yayımlama ayarları dosyası oluşturma
> * Yayımlama ayarları dosyasını Visual Studio'ya alma
> * Uygulamayı IIS'ye dağıtın

Yayımlama ayarları dosyası (*\*.publishsettings*) Visual Studio'da oluşturulan yayımlama profilinden*\*(.pubxml)* farklıdır. Yayımlama ayarları dosyası IIS veya Azure Uygulama Hizmeti tarafından oluşturulur veya el ile oluşturulabilir ve visual studio'ya aktarılabilir.

> [!NOTE]
> Visual Studio'nun bir yüklemesinden diğerine\*visual studio yayımlama profili (.pubxml dosyası) kopyalamanız gerekirse, yönetilen proje türleri için * \\<\>proje adı \Properties\PublishProfiles* klasöründe yayımlama profilini, * \<profilename\>.pubxml'ı*bulabilirsiniz. Web siteleri için *\App_Data* klasörüne bakın. Yayımlama profilleri MSBuild XML dosyalarıdır.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* Visual Studio 2019 yüklü ve **ASP.NET ve web geliştirme** iş yükünü olmalıdır.

    Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
::: moniker-end

::: moniker range="vs-2017"

* Visual Studio 2017'yi ve **ASP.NET ve web geliştirme** iş yükünü yüklemelisiniz.

    Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
::: moniker-end

* Sunucunuzda Windows Server 2012 veya Windows Server 2016'yı çalıştırıyor olmalısınız ve [IIS Web Server rolünü](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) doğru yüklü yormalısınız (yayımlama ayarları dosyasını oluşturmak için gereklidir (*\*.publishsettings*)). Sunucuya 4,5 veya ASP.NET Core ASP.NET de yüklenmesi gerekir. 4,5 ASP.NET ayarlamak için bkz: [IIS 8.0 ASP.NET 3.5 ve ASP.NET 4.5 kullanarak](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). CoreASP.NET ayarlamak için, [IIS ile Windows'ta Ana Bilgisayar ASP.NET Core'a](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)bakın.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio'da yeni bir ASP.NET projesi oluşturun

1. Visual Studio'yu çalıştıran bilgisayarda yeni bir proje oluşturun.

    Doğru şablonu seçin. Bu örnekte, **ASP.NET Web Uygulaması (.NET Framework)** veya (yalnızca C# için) **ASP.NET Core Web Application'ı**seçin ve ardından **Tamam'ı**tıklatın.

    Belirtilen proje şablonlarını görmüyorsanız, **Yeni Proje** iletişim kutusunun sol bölmesinde Görsel **Stüdyo Yükleyiciaç'ı Aç** bağlantısını tıklatın. Visual Studio Installer başlattı. ASP.NET ve web geliştirme iş yükünü **yükleyin.**

    Seçtiğiniz proje şablonu (ASP.NET veya ASP.NET Core) web sunucusunda yüklü ASP.NET sürümüne karşılık gelmelidir.

1. **MVC** (.NET Framework) veya **Web Uygulaması (Model-View-Controller) (.NET** Core için) seçeneğini belirleyin ve Kimlik **Doğrulama'nın seçilmediğinden** emin olun ve **ardından Tamam'ı**tıklatın.

1. **MyWebApp** gibi bir ad yazın ve **Tamam'ı**tıklatın.

    Visual Studio projeyi oluşturur.

1. Projeyi oluşturmak için **Yapı** > **Çözüm'u** seçin.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Windows Server'da Web Dağıtımı'nı yükleme ve yapılandırma

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server'da IIS'de yayımlama ayarları dosyasını oluşturma

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio'da yayımlama ayarlarını içe aktarma ve dağıtma

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlamalıdır. Visual Studio'dan başlamazsa, uygulamayı IIS'de başlatın. ASP.NET Core için, **DefaultAppPool'un** Uygulama havuzu alanının Yönetilen **Kod Yok**olarak ayarlandığınızdan emin olmanız gerekir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir yayımlama ayarları dosyası oluşturdunuz, Visual Studio'ya aktardın ve iIS'ye bir ASP.NET uygulaması dağıttınız. Visual Studio'daki diğer yayımlama seçeneklerine genel bir bakış isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md)
