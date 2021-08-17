---
title: Kapsayıcıya ASP.NET Core kapsayıcı Azure App Service
description: Visual Studio Kapsayıcı Araçları'ASP.NET Core docker kapsayıcısı içinde bir web uygulaması dağıtmak için Azure App Service
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 02/21/2021
ms.author: ghogen
ms.openlocfilehash: 8609c0888662a5fb0609da641e1dfb86510b8797deeeb1a79709cd36174d0936
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121348276"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>ASP.NET Core kullanarak Azure App Service kapsayıcı Visual Studio

Bu öğretici, kapsayıcılı web Visual Studio yayımlamak için ASP.NET Core bir web uygulamasına yayımlamak için [Azure App Service.](/azure/app-service) Azure App Service, Azure'da barındırılan tek kapsayıcılı bir web uygulaması için uygun bir hizmettir.

Azure aboneliğiniz yoksa başlamadan önce [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

::: moniker range="vs-2017"
- "ASP.NET ve web geliştirme" [iş yüküyle Visual Studio 2017'nin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) en son sürümünü yükleyin
::: moniker-end
::: moniker range=">=vs-2019"
- Visual Studio ve web geliştirme iş yükü ASP.NET [2019'un](https://visualstudio.microsoft.com/downloads) *ilk günü.*
::: moniker-end
- [Docker Desktop'ı yükleme](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core web uygulaması oluşturma

Aşağıdaki adımlar, bu öğreticide kullanılacak temel ASP.NET Core uygulama oluşturma konusunda size yol sağlar.

::: moniker range="vs-2017"
1. Yeni Visual Studio Yeni **dosya'>'ı > Project.**
2. Yeni Uygulama **iletişim kutusunun** Şablonlar bölümünde **Visual C# Project** Web'i > **seçin.**
3. Web **ASP.NET Core'ı seçin.**
4. Yeni uygulamanıza bir ad girin (veya varsayılan değeri alır) ve Tamam'ı **seçin.**
5. **Web Uygulaması'ı seçin.**
6. **Docker Desteğini Etkinleştir onay** kutusunu işaretleyin.
7. Linux kapsayıcı **türünü seçin** ve Tamam'a **tıklayın.** Windows kapsayıcıların kapsayıcı olarak Azure App Service dağıtımı desteklenmiyor.
::: moniker-end
::: moniker range=">= vs-2019"
1. Yeni Visual Studio **oluştur'a tıklayın.**
1. Web **ASP.NET Core'ı ve** ardından Sonraki'yi **seçin.**
1. Yeni uygulamanıza bir ad girin (veya varsayılan değeri alır) ve Ardından'ı **seçin.**
1. Hedeflemek istediğiniz .NET sürümünü seçin. Emin değilsanız uzun süreli destek (LTS) sürümünü seçin.
1. HTTPS için yapılandır onay kutusunu kullanarak SSL desteği isteyip **istemeycenizi** seçin.
1. **Docker Desteğini Etkinleştir onay** kutusunu işaretleyin.
1. Kapsayıcı türünü seçin ve Oluştur'a **tıklayın.**
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Kapsayıcıyı Azure'a dağıtma

::: moniker range="vs-2017"

1. Içinde projenize sağ tıklayın ve **Çözüm Gezgini'yi** **seçin.**
1. Yayımlama hedefi iletişim kutusunda Linux veya **App Service seçeneğini** **App Service.** Bu, web sunucusunu barındıracak işletim sistemidir.
1. Yalnızca App Service veya hem App Service hem de Azure Container Registry (ACR) yayımlarsınız. Kapsayıcıyı bir kapsayıcıda (ACR Azure Container Registry yayımlamak için Kapsayıcılar için **yeni App Service oluştur'u** seçin ve Yayımla'ya **tıklayın.**

   ![Yayımla iletişim kutusunun ekran görüntüsü](media/deploy-app-service/publish-app-service-linux-1.png)

   Yeni oluştur'u Azure App Service bir Azure Container Registry yayımlamak için **Yayımla'ya** **tıklayın.**

1. Azure aboneliğiniz ile ilişkili hesapta oturum açın ve benzersiz bir ad, abonelik, kaynak grubu, barındırma planı ve kapsayıcı kayıt defteri (varsa) seçin veya varsayılan değerleri kabul edin.

   ![Yayımlama ayarlarının ekran görüntüsü](media/deploy-app-service/publish-app-service-linux-2.png)

1. **Oluştur'a seçin.** Kapsayıcınız, seçtiğiniz kaynak grubunda ve kapsayıcı kayıt defterinde Azure'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında Yayımla sekmesi,  site URL'si dahil olmak üzere nelerin yayımladığı hakkında bilgi gösterir.

   ![Yayımla sekmesinin ekran görüntüsü](media/deploy-app-service/publish-succeeded.PNG)

1. Uygulamanın Azure'da beklendiği gibi çalıştığını doğrulamak için site bağlantısına tıklayın.

   ![Web uygulamasının ekran görüntüsü](media/deploy-app-service/web-application-running.png)

1. Yayımlama profili, kaynak grubu ve kapsayıcı kayıt defteri gibi seçtiğiniz tüm ayrıntılarla birlikte kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak  için Yayımla  düğmesini, **Web** Yayımlama Etkinliği penceresindeki Yayımla düğmesini kullanın veya **Çözüm Gezgini'de** projeye sağ tıklayın ve bağlam menüsünde Yayımla öğesini seçin. 
:::moniker-end
:::moniker range=">=vs-2019"
1. Içinde projenize sağ tıklayın ve **Çözüm Gezgini'yi** **seçin.**
1. Yayımla **iletişim** kutusunda **Azure hedefini** seçin.

   ![Yayımla sihirbazının ekran görüntüsü](media/deploy-app-service/publish-choices.png)

1. Belirli **hedef sekmesinde,** kapsayıcı türünüze bağlı olarak **App Service (Windows)** veya App Service **(Linux)** gibi uygun dağıtım hedefini seçin.

   ![Yayımla sihirbazının Belirli hedef sekmesinin ekran görüntüsü](media/deploy-app-service/publish-app-service-windows.png)

1. Kullanmak istediğiniz abonelikle doğru Azure hesabında oturum açmadıysanız Yayımla penceresinin sol üst kısmında yer alan düğmeyi **kullanarak oturum** açın.

1. Mevcut bir uygulama hizmetini kullanabilir veya Yeni uygulama oluştur bağlantısına tıklayarak **yeni bir uygulama Azure App Service** oluşturabilirsiniz. Kaynak grubunu genişleterek mevcut uygulama hizmetinizi ağaç görünümünde  bulun veya Türe göre sıralamak için Görünüm ayarını **Kaynak** türü olarak değiştirebilirsiniz.

   ![Örnek seçmeyi gösteren ekran App Service](media/deploy-app-service/publish-app-service-windows2.png)

1. Yeni bir tane oluşturmanız, Azure'da bir kaynak grubu ve uygulama hizmeti oluşturulur. İsterseniz adları benzersiz olduğu sürece değiştirebilirsiniz.

   ![Örnek oluşturmayı gösteren ekran App Service](media/deploy-app-service/publish-app-service-windows3.png)

1. Varsayılan barındırma planını kabul etmek veya barındırma planını şimdi veya daha sonraki bir süre içinde Azure portal. Desteklenen `S1` bölgelerden biri için varsayılan değer (küçük) değeridir. Barındırma planı oluşturmak için Barındırma **Planı açılan** listesinden **Yeni'yi** seçin. Barındırma **Planı penceresi** görüntülenir.

   ![Barındırma planı seçeneklerini gösteren ekran görüntüsü](media/deploy-app-service/hosting-plan.png)

   Bu seçeneklerle ilgili ayrıntıları planına genel bakış [Azure App Service görüntüebilirsiniz.](/azure/app-service/overview-hosting-plans)

1. Bu kaynakları seçmeyi veya oluşturmayı bitirip Bitir'i **seçin.** Kapsayıcınız, seçtiğiniz kaynak grubunda ve uygulama hizmette Azure'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında Yayımla sekmesi,  site URL'si dahil olmak üzere nelerin yayımladığı hakkında bilgi gösterir.

   ![Yayımla sekmesinin ekran görüntüsü](media/deploy-app-service/publish-succeeded-windows.png)

1. Uygulamanın Azure'da beklendiği gibi çalıştığını doğrulamak için site bağlantısına tıklayın.

   ![Web uygulamasının ekran görüntüsü](media/deploy-app-service/web-application-running2.png)

1. Yayımlama profili, kaynak grubu ve uygulama hizmeti gibi seçtiğiniz tüm ayrıntılarla birlikte kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak  için Yayımla  düğmesini, **Web** Yayımlama Etkinliği penceresindeki Yayımla düğmesini kullanın veya **Çözüm Gezgini'de** projeye sağ tıklayın ve bağlam menüsünde Yayımla öğesini seçin. 
:::moniker-end

## <a name="view-container-settings"></a>Kapsayıcı ayarlarını görüntüleme

uygulama [Azure portal,](https://portal.azure.com)dağıtılan kaynaklarınızı App Service.

Kapsayıcı ayarları menüsünü açarak (App Service 2019 sürüm 16.4 veya sonraki bir sürümü Visual Studio) dağıtılan uygulamanıza yönelik ayarları görüntüebilirsiniz. 

![Uygulamanın kapsayıcı Ayarlar menüsünün ekran Azure portal](media/deploy-app-service/container-settings-menu.png)

Buradan kapsayıcı bilgilerini görüntüleyebilirsiniz, günlükleri indirebilirsiniz veya sürekli dağıtım kurabilirsiniz. Bkz. [Azure App Service Sürekli Dağıtım CI/CD](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğreticiyle ilişkili tüm Azure kaynaklarını kaldırmak için kaynak grubunu silmek için [Azure portal.](https://portal.azure.com) Yayımlanmış bir web uygulamasıyla ilişkilendirilmiş kaynak grubunu bulmak için Web Yayımlama Etkinliği'Windows DiğerNini  >    >  Görüntüle'yi **seçin** ve ardından dişli simgesini seçin. Kaynak **grubunu** içeren Yayımla sekmesi açılır.

Kaynak **Azure portal'ı seçin,** kaynak grubunu seçerek ayrıntılar sayfasını açın. Bunun doğru kaynak grubu olduğunu doğrulayın, sonra Kaynak grubunu **kaldır'ı seçin,** adı yazın ve Sil'i **seçin.**

## <a name="next-steps"></a>Sonraki adımlar

hakkında daha fazla bilgi [Azure App Service.](/azure/app-service/overview)

## <a name="see-also"></a>Ayrıca bkz.

[Azure Container Registry’ye dağıtma](hosting-web-apps-in-docker.md)