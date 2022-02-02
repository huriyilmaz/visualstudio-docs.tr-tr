---
title: ASP.NET web uygulaması yayımlama
description: yayımla aracını kullanarak Visual Studio bir web sitesine ASP.NET ve ASP.NET Core yayımlayın.
ms.date: 01/30/2022
ms.topic: quickstart
ms.custom: devdivchpfy22
helpviewer_keywords:
- deployment, web app
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 4ad4c0a5b9c663f4daf02dbe8de8826ac31926dd
ms.sourcegitcommit: 3766c051f9a8b35106b16f751db7fecde0b92254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137951637"
---
# <a name="quickstart-publish-an-aspnet-web-app"></a>hızlı başlangıç: ASP.NET web uygulaması yayımlama

bu makalede, ilk ASP.NET web uygulamanızı ııs gibi yerel bir web sunucusu ve Azure App Service gibi uzak bir bulut ortamı gibi çeşitli konumlara nasıl yayımlayacağınızı öğreneceksiniz.

bu makale ASP.NET ve ASP.NET Core destekler.

## <a name="prerequisites"></a>Önkoşullar

ASP.NET ve web geliştirme iş yüküyle yüklenmiş [Visual Studio](https://www.visualstudio.com/downloads) gerekir.

Visual Studio zaten yüklüyse:

* **güncelleştirmeler için** **yardım**  >  denetle 'yi seçerek en son güncelleştirmeleri Visual Studio.
* **Araçlar**  >  **Al araçlar ve Özellikler '** i seçerek iş yükünü ekleyin.

## <a name="get-started"></a>Başlarken

Çözüm Gezgini, projenize sağ tıklayın ve **Yayımla**' yı seçin.

![sağ tıklayıp Yayımla](./media/right-click-publish.png)

Bu Web uygulamasını ilk kez yayınlıyorsanız, daha sonra Yayımla Sihirbazı ' nı görürsünüz.

![Yayımlama Sihirbazı-hedefleri Yayımla](./media/publish-targets-general.png)

> [!NOTE]
> Visual Studio, web uygulamasının türüne bağlı olarak hedeflerin listesini filtreler.

## <a name="azure"></a>[Azure](#tab/azure)
## <a name="publish-your-web-app-to-azure"></a>Web uygulamanızı Azure’a yayımlama

web uygulamanızı yayımlama hakkında ayrıntılı adımlar için bkz. [hızlı başlangıç: ASP.NET web uygulaması dağıtma](/azure/app-service/quickstart-dotnetcore?tabs=netcore31&pivots=development-environment-vs#publish-your-web-app).

## <a name="docker"></a>[Docker](#tab/docker)
## <a name="publish-your-web-app-to-docker-container-registry"></a>Web uygulamanızı Docker Container Registry yayımlayın

Web uygulamanızı, uyumlu herhangi bir Docker Container Registry için bir Docker kapsayıcısı olarak yayımlayabilirsiniz.

![Docker Container Registry vurgulanmış olarak Yayımla](./media/publish-docker-container-registry-highlighted.png)

**İleri** ' ye tıklayın ve Azure Container Registry veya Docker Hub gibi kullanılabilir seçenekler arasından seçim yapın.

![Docker Container Registry seçeneklerinde Yayımla](./media/publish-docker-container-registry-options.png)

### <a name="azure-container-registry"></a>Azure Container Registry

Daha sonra, Azure Container Registry için mevcut bir örneği seçin veya yeni bir tane oluşturun.

![Azure Container Registry yayımlama](./media/publish-acr-select-instance.png)

### <a name="docker-hub"></a>Docker Hub

Ardından, Docker Hub için yayımlama kimlik bilgilerini sağlayın.

![Docker Hub 'a Yayımla](./media/publish-dockerhub-details.png)

### <a name="other-docker-container-registry"></a>Diğer Docker Container Registry

Ardından, diğer Docker kapsayıcı kayıt defterleri için URI ve yayımlama kimlik bilgilerini sağlayın.

![diğer Docker Container Registry yayımlayın](./media/publish-custom-docker-registry-details.png)

### <a name="finish-the-publish-wizard"></a>Yayımlama Sihirbazı 'nı tamamlama

Daha sonra, Yayımlama Sihirbazı 'nı kullanarak yeni oluşturduğunuz [Yayımlama profili](./publish-overview.md) için Özet sayfasını görürsünüz. **yayımla** ' ya tıklayın ve Visual Studio web uygulamanızı belirtilen docker Container Registry dağıtır.

![Docker Container Registry yayımlama-Özet sayfası](./media/publish-docker-container-registry-summary-page.png)

> [!NOTE]
> Yukarıdaki ekran görüntüsü, Azure Docker kayıt defteri 'ni hedefleyen bir yayımlama profili gösterir, ancak üç Docker Container Registry seçeneği için de aynı Yayımla düğmesi bulunur.

## <a name="folder"></a>[Klasör](#tab/folder)
## <a name="publish-your-web-app-to-a-folder"></a>Web uygulamanızı bir klasöre yayımlayın

Web uygulamanızı hem yerel hem de ağ klasörlerinde yayımlayabilirsiniz.

![klasöre yayınla vurgulanmış](./media/publish-folder-highlighted.png)

İlk olarak, yolu belirtin ve **son** ' a tıklayarak Yayımlama Sihirbazı 'nı doldurun.

![klasöre Yayımla](./media/publish-folder.png)

Daha sonra, Yayımlama Sihirbazı 'nı kullanarak yeni oluşturduğunuz [Yayımlama profili](./publish-overview.md) için Özet sayfasını görürsünüz. **yayımla** ' ya tıklayın ve web uygulamanızı belirtilen yola dağıtır Visual Studio.

![klasöre Yayımla-Özet sayfası](./media/publish-folder-summary-page.png)

Bu özet sayfasına kapattıktan sonra geri dönebilirsiniz. daha sonra sağ tıklayıp **yayımla**' yı seçtiğinizde Visual Studio bu özet sayfasını açar. (Yayımla sihirbazına geri dönmek için, Özet sayfasında **Yeni** ' ye tıklamanız yeterlidir.)

## <a name="ftpftps"></a>[FTP/FTPS](#tab/ftp-ftps)
## <a name="publish-your-web-app-to-an-ftpftps-server"></a>Web uygulamanızı bir FTP/FTPS sunucusunda yayımlayın

FTP veya FTPS kullanarak Web uygulamanızı yayımlayabilirsiniz.

![FTP veya FTPS sunucusunda Yayımla](./media/publish-ftp.png)

Gerekli bağlantı ayrıntılarını girip **son**' a tıklayın.

![FTP veya FTPS sunucusunda Yayımla-Ayrıntılar](./media/publish-ftp-details-latest.png)

Daha sonra, Yayımlama Sihirbazı 'nı kullanarak yeni oluşturduğunuz [Yayımlama profili](./publish-overview.md) için Özet sayfasını görürsünüz. **yayımla** ' ya tıklayın ve web uygulamanızı belirtilen FTP veya ftps sunucusuna dağıtır Visual Studio.

![FTP veya FTPS sunucusunda Yayımla-Özet sayfası](./media/publish-ftp-summary-page.png)

Bu özet sayfasına kapattıktan sonra geri dönebilirsiniz. daha sonra sağ tıkladığınızda ve yayımladığınızda Visual Studio, bu özet sayfasını açar. (Yayımla sihirbazına geri dönmek için, Özet sayfasında **Yeni** ' ye tıklamanız yeterlidir.)

## <a name="web-server"></a>[Web sunucusu](#tab/web-server)
## <a name="publish-your-web-app-to-web-server-iis"></a>Web uygulamanızı Web sunucusuna yayımlama (IIS)

Web uygulamanızı IIS 'de yayımlayabilirsiniz.

![IIS 'de Yayımla](./media/publish-iis.png)

İstenen dağıtım modunu seçin (emin değilseniz, Varsayılanı kullanın).

![IIS dağıtım modunda Yayımla](./media/publish-iis-deployment-mode.png)

### <a name="web-deploy"></a>Web Dağıtımı

Gerekli bağlantı ayrıntılarını girip **son**' a tıklayın.

![IIS 'de Yayımla-Web Dağıtımı](./media/publish-iis-web-deploy-latest.png)

### <a name="web-deploy-package"></a>Web Dağıtımı Paketi

Bir paket konumu Seç iletişim kutusunu açmak ve *.zip* dosya adı da dahil olmak üzere paketin oluşturulmasını istediğiniz yolu girmek Için, **araştır...** ' a tıklayın.

![IIS-Web Dağıtımı Paketi 'ne yayımlama](./media/publish-iis-web-deploy-package.png)

### <a name="finish-the-publish-wizard"></a>Yayımlama Sihirbazı 'nı tamamlama

Daha sonra, Yayımlama Sihirbazı 'nı kullanarak yeni oluşturduğunuz [Yayımlama profili](./publish-overview.md) için Özet sayfasını görürsünüz. **yayımla** ' ya tıklayın ve web uygulamanızı belirtilen ııs sunucusuna dağıtır Visual Studio.

![IIS 'de Yayımla-Özet sayfası](./media/publish-iis-web-deploy-package-summary-page.png)

## <a name="import-profile"></a>[Profili içeri aktar](#tab/import-profile)
## <a name="import-profile"></a>Profili içeri aktar

Yayımlama ayarlarını [IIS 'den](./tutorial-import-publish-settings-iis.md) ve [Azure App Service](./tutorial-import-publish-settings-azure.md#create-the-publish-settings-file-in-azure-app-service) içeri aktarabilirsiniz

---