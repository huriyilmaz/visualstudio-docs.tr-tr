---
title: Yayımlama ayarlarını içeri aktararak IIS 'de yayımlayın
description: Visual Studio bir uygulamayı IIS 'ye dağıtmak için Yayımlama profili oluşturma ve içeri aktarma
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
ms.openlocfilehash: ca5aac87838ad52aee0432a6430f74d35281b063ad2ae94c92f1c2baca3476d3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403847"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Visual Studio yayımlama ayarlarını içeri aktararak IIS 'de uygulama yayımlama

**Yayımla aracını kullanarak** yayınlama ayarlarını içeri aktarabilir ve ardından uygulamanızı dağıtabilirsiniz. Bu makalede, IIS için yayımlama ayarlarını kullanırız, ancak [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md)yayımlama ayarlarını içeri aktarmak için de benzer adımları kullanabilirsiniz. Bazı senaryolarda, bir yayımlama ayarları profili kullanımı, her bir Visual Studio yüklemesi için IIS 'e dağıtımı el ile yapılandırmadan daha hızlı olabilir.

bu adımlar Visual Studio ' de ASP.NET, ASP.NET Core ve .net Core uygulamaları için geçerlidir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Bir yayımlama ayarları dosyası oluşturabilmeniz için IIS 'yi yapılandırma
> * Yayımlama ayarları dosyası oluşturma
> * Yayımlama ayarları dosyasını Visual Studio içine aktarın
> * Uygulamayı IIS 'ye dağıtma

Bir yayımlama ayarları dosyası (*\* . publishsettings*) Visual Studio oluşturulan yayımlama profilinden (*\* . pubxml*) farklıdır. Bir yayımlama ayarları dosyası IIS veya Azure App Service tarafından oluşturulur veya el ile oluşturulabilir ve sonra Visual Studio içeri aktarılabilir.

> [!NOTE]
> bir Visual Studio yayımlama profilini ( \* . pubxml dosyası) bir Visual Studio yüklemesinden diğerine kopyalamanız gerekiyorsa, yönetilen proje türleri için *\\<projectname \> \Properties\PublishProfiles* klasöründe, *\<profilename\> . pubxml* yayımlama profilini bulabilirsiniz. Web siteleri için *\ App_Data* klasörü altına bakın. yayımlama profilleri MSBuild XML dosyalarıdır.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* Visual Studio 2019 yüklü ve **ASP.NET ve web geliştirme** iş yüküne sahip olmanız gerekir.

    Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz yükleme yapın.
::: moniker-end

::: moniker range="vs-2017"

* Visual Studio 2017 yüklü ve **ASP.NET ve web geliştirme** iş yüküne sahip olmanız gerekir.

    Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz yükleme yapın.
::: moniker-end

* sunucunuzda Windows Server 2012, Windows Server 2016 veya Windows server 2019 ' i çalıştırıyor olmanız gerekir ve [ııs Web sunucusu rolünün](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) doğru bir şekilde yüklenmiş olması gerekir (yayımlama ayarları dosyası (*\* . publishsettings*) oluşturmak için gereklidir). ASP.NET 4,5 ya da ASP.NET Core de sunucuda yüklü olmalıdır. ASP.NET 4,5 ayarlamak için [ASP.NET 3,5 ve 4,5 ASP.NET kullanarak ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)' e bakın. ASP.NET Core ayarlamak için, bkz. [ııs ile Windows konak ASP.NET Core](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). ASP.NET Core için uygulama havuzunu makalede açıklandığı gibi, **yönetilen kod olmadan** kullanmak üzere yapılandırdığınızdan emin olun.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio yeni ASP.NET projesi oluşturma

1. Visual Studio çalıştıran bilgisayarda yeni bir proje oluşturun.

    Doğru şablonu seçin. bu örnekte, **ASP.NET web uygulaması (.NET Framework)** veya (yalnızca C# için) **web uygulaması ASP.NET Core** seçin ve ardından **tamam**' ı seçin.

    belirtilen proje şablonlarını görmüyorsanız, **yeni Project** iletişim kutusunun sol bölmesindeki **aç Visual Studio Yükleyicisi** bağlantısına gidin. Visual Studio Yükleyicisi başlatılır. **ASP.NET ve web geliştirme** iş yükünü yükler.

    seçtiğiniz proje şablonu (ASP.NET veya ASP.NET Core), web sunucusunda yüklü ASP.NET sürümüne karşılık gelmelidir.

1. **MVC** (.NET Framework) veya **Web uygulaması (Model-View-Controller)** ' ı (.net Core için) seçin ve **kimlik doğrulamasının** seçili olmadığından emin olun ve ardından **tamam**' ı seçin.

1. **MyWebApp** gibi bir ad yazın ve **Tamam**' ı seçin.

    Visual Studio projeyi oluşturur.

1.   >  Projeyi derlemek için Build **Build Solution** (veya **CTRL**  +  **SHIFT**  +  **B** tuşlarına basın) öğesini seçin.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Windows sunucusuna Web Dağıtımı yükleyip yapılandırın

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows sunucuda ııs 'de yayımlama ayarları dosyası oluşturma

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio yayımlama ayarlarını içeri aktarın ve dağıtın

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Uygulama başarıyla dağıtıldıktan sonra otomatik olarak başlamalıdır. Visual Studio başlamadıysanız, uygulamayı ııs 'de başlatın. ASP.NET Core için, **DefaultAppPool** için uygulama havuzu alanının **yönetilen kod yok** olarak ayarlandığından emin olmanız gerekir.

## <a name="next-steps"></a>Sonraki adımlar

bu öğreticide, bir yayımlama ayarları dosyası oluşturdunuz, onu Visual Studio içeri aktardınız ve ııs 'ye bir ASP.NET uygulaması dağıttınız. Visual Studio ' deki diğer yayımlama seçeneklerine genel bir bakış istemeniz gerekebilir.

> [!div class="nextstepaction"]
> [Dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md)
