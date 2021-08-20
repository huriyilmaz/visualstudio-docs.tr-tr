---
title: Bir Web sitesine yayımlama
description: ASP.NET, ASP.NET Core, .net Core ve Python uygulamalarını Visual Studio bir web sitesine yayımlamak için yayımla aracını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 17cd220c3c04c36f0870f6644b63a3abb190f81a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127850"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Bir Web uygulamasını Visual Studio kullanarak Web sitesinde yayımlama

**yayımla** aracını, Visual Studio ' den bir web sitesine ASP.NET, ASP.NET Core, .net Core ve Python uygulamaları yayımlamak için kullanabilirsiniz. Node.js, adımlar desteklenir, ancak kullanıcı arabirimi farklıdır.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> bir Windows masaüstü uygulamasını bir ağ dosya paylaşımında yayımlamanız gerekiyorsa, bkz. [ClickOnce kullanarak masaüstü uygulaması dağıtma](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# veya Visual Basic). C++/clr için bkz. [ClickOnce kullanarak yerel uygulama dağıtma](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) veya C/C++ için bkz. [kurulum projesi kullanarak yerel uygulama dağıtma](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Web sitesinde yayımlama

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla** ' yı seçin (veya **Yapı**  >  **Yayımla** menü öğesini kullanın).

    ![Çözüm Gezgini içindeki proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla ' yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** bölmesi görüntülenir. **Yeni**'yi seçin.

1. **Yayımla** penceresinde **Web sunucusu (IIS)** öğesini seçin.

    ![Yayımlama hedefini seçin](../deployment/media/quickstart-publish-iis.png "IIS, FTP, vb. seçin.")

1. Dağıtım yöntemi olarak **Web dağıtımı** seçin. Web Dağıtımı, Web uygulamalarının ve Web sitelerinin IIS sunucularına dağıtımını basitleştirir ve sunucuda bir uygulama olarak yüklenmelidir. Yüklemek için [Web Platformu Yükleyicisi](https://www.microsoft.com/web/downloads/platform.aspx) 'ni kullanın.

    ![Dağıtım yöntemini seçin](../deployment/media/quickstart-publish-iis-web-deploy.png "IIS, FTP, vb. seçin.")

1. Yayımla yöntemi için gerekli ayarları yapılandırın ve **son**' u seçin. 

    ![Web Dağıtımı bağlantı ayrıntıları](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Yayımlamak için Özet sayfasında **Yayımla** ' yı seçin. Çıkış penceresinde dağıtım ilerleme durumu ve sonuçları gösterilir.

   ııs 'de ASP.NET Core sorun giderme konusunda yardıma ihtiyacınız varsa bkz. [Azure App Service ve ııs 'de ASP.NET Core sorunlarını giderme](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="next-steps"></a>Sonraki adımlar

bu hızlı başlangıçta, bir yayımlama profili oluşturmak için Visual Studio kullanmayı öğrendiniz. Yayımlama ayarlarını içeri aktararak de bir yayımlama profili yapılandırabilirsiniz.

> [!div class="nextstepaction"]
> [Yayımlama ayarlarını içeri aktarma ve IIS’ye dağıtma](tutorial-import-publish-settings-iis.md)
