---
title: ASP.NET web uygulaması yayımlama
description: Yayımlama aracını kullanarak web sitelerinden bir ASP.NET ASP.NET Core yayımlamayı Visual Studio.
ms.date: 10/22/2021
ms.topic: quickstart
helpviewer_keywords:
- deployment, web app
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: c829f0f4e2d0b541f84f7f0a4c2cc3e5204163b3
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131130465"
---
# <a name="quickstart-publish-an-aspnet-web-app"></a>Hızlı Başlangıç: ASP.NET web uygulaması yayımlama

Bu makalede, iis gibi yerel bir web sunucusu ve Azure App Service gibi uzak bir bulut ortamı dahil olmak üzere çeşitli konumlarda ilk ASP.NET web uygulamanızı yayımlamayı Azure App Service.

Bu makaledeki adımlar, ASP.NET ve ASP.NET Core.

## <a name="prerequisites"></a>Önkoşullar

Web [Visual Studio](https://www.visualstudio.com/downloads) iş yüküyle ASP.NET gerekir.

Önceden yükleme yaptıysanız Visual Studio:

* Güncelleştirmeler için Yardım Denetimi'Visual Studio seçerek en **son**  >  **güncelleştirmeleri Visual Studio'ye yükleyin.**
* Araçlar Araçları ve Özellikleri Al'ı  >  **seçerek iş yükünü ekleyin.**

## <a name="get-started"></a>başlarken

Bu Çözüm Gezgini projenize sağ tıklayın ve Yayımla'yı **seçin.**

![sağ tıklayın ve yayımlayın](./media/right-click-publish.png)

Bu web uygulamasını ilk kez yayımlayacaksanız Yayımla sihirbazını görüyor olursanız.

![yayımlama sihirbazı - hedefleri yayımlama](./media/publish-targets-general.png)

> [!NOTE]
> Visual Studio web uygulamasının türüne bağlı olarak hedef listesini filtreler.

## <a name="azure"></a>[Azure](#tab/azure)
## <a name="publish-your-web-app-to-azure"></a>Web uygulamanızı Azure’a yayımlama

Ayrıntılı adımlar için [bkz. Hızlı Başlangıç: Web uygulaması ASP.NET dağıtma.](/azure/app-service/quickstart-dotnetcore?tabs=netcore31&pivots=development-environment-vs#publish-your-web-app)

## <a name="docker"></a>[Docker](#tab/docker)
## <a name="publish-your-web-app-to-docker-container-registry"></a>Web uygulamalarınızı Docker Container Registry

Web uygulamalarınızı herhangi bir uyumlu Docker kapsayıcısı için Docker kapsayıcısı olarak Container Registry.

![Docker'da yayımlama Container Registry vurgulanmış](./media/publish-docker-container-registry-highlighted.png)

**Sonraki'ye** tıklayın ve kullanılabilir seçenekler (örneğin, Azure Container Registry veya Docker Hub.

![Docker'da yayımlama Container Registry seçenekleri](./media/publish-docker-container-registry-options.png)

### <a name="azure-container-registry"></a>Azure Container Registry

Ardından, Azure Container Registry örneği seçin veya yeni bir örnek oluşturun.

![Azure Container Registry'de yayımlama](./media/publish-acr-select-instance.png)

### <a name="docker-hub"></a>Docker Hub

Ardından, Docker Hub kimlik bilgilerini girin.

![Docker Hub'de yayımlama](./media/publish-dockerhub-details.png)

### <a name="other-docker-container-registry"></a>Diğer Docker Container Registry

Ardından, diğer Docker kapsayıcısı kayıt defterleri için URI'yi girin ve kimlik bilgilerini yayımlayın.

![diğer Docker Container Registry](./media/publish-custom-docker-registry-details.png)

### <a name="finish-the-publish-wizard"></a>Yayımla sihirbazını tamamlayın

Ardından, Yayımla sihirbazını kullanarak yeni [oluşturduğunuz](./publish-overview.md) yeni yayımlama profilinin özet sayfasını görebilirsiniz. **Yayımla'Visual Studio** tıklarsanız web uygulamanızı belirtilen Docker uygulamasına Container Registry.

![Docker Container Registry yayımlama - özet sayfası](./media/publish-docker-container-registry-summary-page.png)

> [!NOTE]
> Yukarıdaki ekran görüntüsünde Azure Docker Kayıt Defteri'ni hedef alan bir yayımlama profili gösteriliyor, ancak üç Docker kayıt defteri seçeneği için de aynı Container Registry kullanılabilir.

## <a name="folder"></a>[Klasör](#tab/folder)
## <a name="publish-your-web-app-to-a-folder"></a>Web uygulamasını bir klasörde yayımlama

Web uygulamalarınızı hem yerel hem de ağ klasörlerinde yayımlayın.

![klasöre yayımlama vurgulanmış](./media/publish-folder-highlighted.png)

İlk olarak, yolu sağlayın ve **Yayımla sihirbazını** tamamlamak için Son'a tıklayın.

![klasöre yayımlama](./media/publish-folder.png)

Ardından, Yayımla sihirbazını kullanarak yeni [oluşturduğunuz](./publish-overview.md) yeni yayımlama profilinin özet sayfasını görebilirsiniz. **Yayımla'Visual Studio** web uygulamanızı sağlanan yola dağıtın.

![klasöre yayımlama - özet sayfası](./media/publish-folder-summary-page.png)

Kapatarak bu özet sayfasına dönebilirsiniz. Sağ tıklar ve Yayımla'yı bir **sonraki Visual Studio** bu özet sayfasını açar. (Yayımla sihirbazına geri dönmek için özet **sayfasında Yeni'ye** tıklamanız gerekir.)

## <a name="ftpftps"></a>[FTP/FTPS](#tab/ftp-ftps)
## <a name="publish-your-web-app-to-an-ftpftps-server"></a>Web uygulamasını FTP/FTPS sunucusunda yayımlama

FTP veya FTPS kullanarak web uygulamalarınızı yayımlayın.

![FTP veya FTPS Sunucusuna yayımlama](./media/publish-ftp.png)

Gerekli bağlantı ayrıntılarını sip Son'a **tıklayın.**

![FTP veya FTPS Sunucusuna yayımlama - ayrıntılar](./media/publish-ftp-details.png)

Ardından, Yayımla sihirbazını kullanarak yeni [oluşturduğunuz](./publish-overview.md) yeni yayımlama profilinin özet sayfasını görebilirsiniz. **Yayımla'Visual Studio** tıklayın ve web uygulamanızı sağlanan FTP veya FTPS Sunucusuna dağıtır.

![FTP veya ftps sunucusuna yayımlama - özet sayfası](./media/publish-ftp-summary-page.png)

Kapatarak bu özet sayfasına dönebilirsiniz. Sağ tıklar ve yayımlarken bir sonraki Visual Studio bu özet sayfası açılır. (Yayımla sihirbazına geri dönmek için özet **sayfasında Yeni'ye** tıklamanız gerekir.)

## <a name="web-server"></a>[Web Sunucusu](#tab/web-server)
## <a name="publish-your-web-app-to-web-server-iis"></a>Web uygulamasını Web Server'da yayımlama (IIS)

Web uygulamalarınızı IIS'de yayımlayın.

![IIS'de yayımlama](./media/publish-iis.png)

İstediğiniz dağıtım modunu seçin (emin değilseniz varsayılanı kullanın).

![IIS'de yayımlama - dağıtım modu](./media/publish-iis-deployment-mode.png)

### <a name="web-deploy"></a>Web Dağıtımı

Gerekli bağlantı ayrıntılarını sip Son'a **tıklayın.**

![IIS'de yayımlama - Web Dağıtımı](./media/publish-iis-web-deploy.png)

### <a name="web-deploy-package"></a>Web Dağıtımı Paketi

Gözat... **seçeneğine** tıklar ve Paket Konumu Seç iletişim kutusunu açın ve dosya adı da dahil olmak üzere *paketin.zip* girin.

![IIS'de yayımlama - Web Dağıtımı Paketi](./media/publish-iis-web-deploy-package.png)

### <a name="finish-the-publish-wizard"></a>Yayımla sihirbazını tamamlayın

Ardından, Yayımla sihirbazını kullanarak yeni [oluşturduğunuz](./publish-overview.md) yeni yayımlama profilinin özet sayfasını görebilirsiniz. **Yayımla'Visual Studio** web uygulamanızı belirtilen IIS sunucusuna dağıtın.

![IIS'de yayımlama - özet sayfası](./media/publish-iis-web-deploy-package-summary-page.png)

## <a name="import-profile"></a>[Profili içeri aktarma](#tab/import-profile)
## <a name="import-profile"></a>Profili İçeri Aktar

Yayımlama ayarlarını [IIS](./tutorial-import-publish-settings-iis.md) ve [](./tutorial-import-publish-settings-azure.md#create-the-publish-settings-file-in-azure-app-service) Azure App Service

---
