---
title: Web sitesinde yayımlama
description: ASP.NET, ASP.NET Core, .NET Core ve Python uygulamalarını Visual Studio web sitesinde yayımlamak için Yayımlama aracını Visual Studio.
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
ms.openlocfilehash: 825908633e12727d3c792cfa9793486f2d9f005203a8e17646fdbf1b349d7d85
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453044"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Web uygulamasını kullanarak bir web sitesinde Visual Studio

Yayımlama aracını  kullanarak ASP.NET, ASP.NET Core, .NET Core ve Python uygulamalarını Visual Studio. Daha Node.js adımlar destekleniyor ancak kullanıcı arabirimi farklıdır.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Bir ağ dosya paylaşımına Windows masaüstü uygulaması yayımlamanız gerekirse bkz. [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# veya Visual Basic) kullanarak masaüstü uygulaması dağıtma. C++/CLR için bkz. [ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) kullanarak yerel uygulama dağıtma veya C/C++ için bkz. Kurulum projesi kullanarak [yerel uygulama dağıtma.](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)

## <a name="publish-to-a-web-site"></a>Web sitesinde yayımlama

1. Bu Çözüm Gezgini projeye sağ tıklayın ve Yayımla'yı **seçin** (veya **Yayımla'yı**  >  **Derleme menü** öğesini kullanın).

    ![Çözüm Gezgini'de proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla'yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız Yayımla **bölmesi** görüntülenir. **Yeni**'yi seçin.

1. Yayımla **penceresinde** Web Sunucusu **(IIS) 'yi seçin.**

    ![Yayımlama hedefi seçme](../deployment/media/quickstart-publish-iis.png "IIS, FTP vb. seçin.")

1. Dağıtım **Web Dağıtımı** Olarak Seç'i seçin. Web Dağıtımı web uygulamalarının ve Web sitelerinin IIS sunucularına dağıtımını basitleştirerek sunucuda bir uygulama olarak yüklü olması gerekir. Yüklemek [için Web platformu yükleyicisini](https://www.microsoft.com/web/downloads/platform.aspx) kullanın.

    ![Dağıtım yöntemini seçme](../deployment/media/quickstart-publish-iis-web-deploy.png "IIS, FTP vb. seçin.")

1. Yayımlama yöntemi için gerekli ayarları yapılandırarak Son'a **tıklayın.** 

    ![Web Dağıtımı ayrıntıları](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Yayımlamak için özet **sayfasında Yayımla'yı** seçin. Çıkış penceresinde dağıtım ilerleme durumu ve sonuçları gösterilir.

   IIS'de sorun giderme ASP.NET Core yardıma ihtiyacınız varsa, bkz. ASP.NET Core [ve IIS Azure App Service sorunlarını giderme.](/aspnet/core/test/troubleshoot-azure-iis)

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta yayımlama profili oluşturmak için Visual Studio kullanmayı öğrendiniz. Yayımlama ayarlarını içeri aktararak bir yayımlama profili de yapılandırabilirsiniz.

> [!div class="nextstepaction"]
> [Yayımlama ayarlarını içeri aktarma ve IIS’ye dağıtma](tutorial-import-publish-settings-iis.md)
