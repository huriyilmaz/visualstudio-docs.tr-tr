---
title: Bir Web sitesine yayımlama
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89d8acfa4bf0f5dd9f1f387389b9f7f523c153a7
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036411"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Web uygulamasını Visual Studio kullanarak Web sitesinde yayımlama

**Yayımla** aracını, ASP.NET, ASP.NET Core, .NET Core ve Python uygulamalarını Visual Studio 'daki bir Web sitesine yayımlamak için kullanabilirsiniz. Node.js, adımlar desteklenir, ancak kullanıcı arabirimi farklıdır.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Bir Windows masaüstü uygulamasını bir ağ dosya paylaşımında yayımlamanız gerekiyorsa bkz. [ClickOnce kullanarak masaüstü uygulaması dağıtma](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# veya Visual Basic). C++/CLR için bkz. [ClickOnce kullanarak yerel uygulama dağıtma](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) veya C/C++ için bkz. [Kurulum projesi kullanarak yerel uygulama dağıtma](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Web sitesinde yayımlama

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla** ' yı seçin (veya **Yapı**  >  **Yayımla** menü öğesini kullanın).

    ![Çözüm Gezgini içindeki proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla ' yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** bölmesi görüntülenir. **Yeni**’yi seçin.

1. **Yayımla** penceresinde **Web sunucusu (IIS)** öğesini seçin.

    ![Yayımlama hedefini seçin](../deployment/media/quickstart-publish-iis.png "IIS, FTP, vb. seçin.")

1. Dağıtım yöntemi olarak **Web dağıtımı** seçin. Web Dağıtımı, Web uygulamalarının ve Web sitelerinin IIS sunucularına dağıtımını basitleştirir ve sunucuda bir uygulama olarak yüklenmelidir. Yüklemek için [Web Platformu Yükleyicisi](https://www.microsoft.com/web/downloads/platform.aspx) 'ni kullanın.

    ![Dağıtım yöntemini seçin](../deployment/media/quickstart-publish-iis-web-deploy.png "IIS, FTP, vb. seçin.")

1. Yayımla yöntemi için gerekli ayarları yapılandırın ve **son**' u seçin. 

    ![Web Dağıtımı bağlantı ayrıntıları](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Yayımlamak için Özet sayfasında **Yayımla** ' yı seçin. Çıkış penceresinde dağıtım ilerleme durumu ve sonuçları gösterilir.

   IIS 'de ASP.NET Core sorun giderme konusunda yardıma ihtiyacınız varsa bkz. [Azure App Service ve IIS 'de ASP.NET Core sorunlarını giderme](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, bir yayımlama profili oluşturmak için Visual Studio 'Yu nasıl kullanacağınızı öğrendiniz. Yayımlama ayarlarını içeri aktararak de bir yayımlama profili yapılandırabilirsiniz.

> [!div class="nextstepaction"]
> [Yayımlama ayarlarını içeri aktarma ve IIS’ye dağıtma](tutorial-import-publish-settings-iis.md)
