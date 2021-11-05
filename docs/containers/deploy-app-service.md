---
title: ASP.NET Core kapsayıcısı Azure App Service
description: Visual Studio Kapsayıcı Araçları'ASP.NET Core docker kapsayıcısı içinde bir web uygulaması dağıtmak için Azure App Service
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 10/28/2021
ms.author: ghogen
ms.openlocfilehash: 68902c071b2b76de4fcb36a6f1c2461d838bc1e9
ms.sourcegitcommit: aff49629012f4d5fa07c75ea0ca5bf53d28aa173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2021
ms.locfileid: "131662772"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>ASP.NET Core kullanarak Azure App Service kapsayıcısı Visual Studio

Bu öğreticide, kapsayıcılı Visual Studio web uygulamanızı bir ASP.NET Core için yayımlamak için [Azure App Service.](/azure/app-service) Azure App Service, Azure'da barındırılan tek kapsayıcılı bir web uygulaması için uygun bir hizmettir.

Azure aboneliğiniz yoksa başlamadan önce [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

::: moniker range="vs-2017"
- "ASP.NET ve web geliştirme" [iş yüküyle Visual Studio 2017'nin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) en son sürümünü yükleyin
::: moniker-end
::: moniker range="vs-2019"
- Visual Studio ve web geliştirme iş yükü ASP.NET [2019'un](https://visualstudio.microsoft.com/downloads) *ilk günü.*
::: moniker-end
::: moniker range=">=vs-2022"
- [Visual Studio web geliştirme iş yüküyle 2022](https://visualstudio.microsoft.com/downloads) RC ASP.NET i *kullanabilirsiniz.*
::: moniker-end

- [Docker Desktop'ı yükleme](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core web uygulaması oluşturma

Aşağıdaki adımlar, bu öğreticide kullanılacak temel ASP.NET Core uygulama oluşturma konusunda size yol sağlar.

::: moniker range="vs-2017"
1. Yeni Visual Studio Yeni **dosya'ya >'ı > Project.**
2. Yeni Uygulama **iletişim kutusunun** Şablonlar bölümünde **Visual C# Project** **Web'i > seçin.**
3. Web **ASP.NET Core'ı seçin.**
4. Yeni uygulamanıza bir ad girin (veya varsayılan değeri alır) ve Tamam'ı **seçin.**
5. **Web Uygulaması'ı seçin.**
6. **Docker Desteğini Etkinleştir onay** kutusunu işaretleyin.
7. Linux kapsayıcı **türünü seçin** ve Tamam'a **tıklayın.** Windows kapsayıcıların kapsayıcı olarak Azure App Service desteklanmaz.
::: moniker-end
::: moniker range=">= vs-2019"
1. Başlangıç Visual Studio Yeni proje **oluştur'a tıklayın.**
1. Web **ASP.NET Core'yi ve** ardından Sonraki'yi **seçin.**
1. Yeni uygulamanıza bir ad girin (veya varsayılanı seçin) ve Ardından'ı **seçin.**
1. Hedeflemek istediğiniz .NET sürümünü seçin. Emin değilsanız uzun süreli destek (LTS) sürümünü seçin.
1. HTTPS için yapılandır onay kutusunu kullanarak SSL desteği isteyip **istemeycenizi** seçin.
1. **Docker Desteğini Etkinleştir onay** kutusunu işaretleyin.
1. Kapsayıcı türünü seçin ve Oluştur'a **tıklayın.**
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Kapsayıcıyı Azure'a dağıtma

::: moniker range="vs-2017"

1. Çözüm Gezgini'da **projenize sağ tıklayın ve** Yayımla'yı **seçin.**
1. Yayımlama hedefi iletişim kutusunda Linux veya **App Service'yi** **App Service.** Bu, web sunucusunu barındıracak işletim sistemidir.
1. Yalnızca App Service veya hem App Service hem de Azure Container Registry (ACR) yayımlarsınız. Kapsayıcıyı bir Azure Container Registry (ACR) içinde yayımlamak için Kapsayıcılar **için yeni App Service oluştur'u** seçin ve Yayımla'ya **tıklayın.**

   ![Yayımla iletişim kutusunun ekran görüntüsü.](media/deploy-app-service/publish-app-service-linux-1.png)

   Yeni oluştur'u Azure App Service bir Azure Container Registry yayımlamak için **Yayımla'ya** **tıklayın.**

1. Azure aboneliğiniz ile ilişkili hesapta oturum açın ve benzersiz bir ad, abonelik, kaynak grubu, barındırma planı ve kapsayıcı kayıt defteri (varsa) seçin veya varsayılan değerleri kabul edin.

   ![Yayımlama ayarlarının ekran görüntüsü.](media/deploy-app-service/publish-app-service-linux-2.png)

1. **Oluştur'a seçin.** Kapsayıcınız, seçtiğiniz kaynak grubunda ve kapsayıcı kayıt defterinde Azure'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında Yayımla sekmesi,  site URL'si dahil olmak üzere nelerin yayımladığı hakkında bilgi gösterir.

   ![Yayımla sekmesinin ekran görüntüsü.](media/deploy-app-service/publish-succeeded.PNG)

1. Uygulamanın Azure'da beklendiği gibi çalıştığını doğrulamak için site bağlantısına tıklayın.

   ![Web uygulamasının ekran görüntüsü.](media/deploy-app-service/web-application-running.png)

1. Yayımlama profili, kaynak grubu ve kapsayıcı kayıt defteri gibi seçtiğiniz tüm ayrıntılarla birlikte kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak  için Yayımla  düğmesini, **Web** Yayımlama Etkinliği penceresindeki Yayımla düğmesini kullanın veya **Çözüm Gezgini'de** projeye sağ tıklayın ve bağlam menüsünde Yayımla öğesini seçin. 
:::moniker-end

:::moniker range="vs-2019"

1. Çözüm Gezgini'da **projenize sağ tıklayın ve** Yayımla'yı **seçin.**
1. Yayımla **iletişim** kutusunda **Azure hedefini** seçin.

   ![Yayımla sihirbazının ekran görüntüsü.](media/deploy-app-service/publish-choices.png)

1. Belirli **hedef sekmesinde,** kapsayıcı türünüze bağlı olarak **App Service (Windows)** veya **App Service (Linux)** gibi uygun dağıtım hedefini seçin.

   ![Yayımla sihirbazının Belirli hedef sekmesinin ekran görüntüsü.](media/deploy-app-service/publish-app-service-windows.png)

1. Kullanmak istediğiniz abonelikle doğru Azure hesabında oturum açmadıysanız Yayımla penceresinin sol üst kısmında yer alan düğmeyi **kullanarak oturum** açın.

1. Mevcut bir uygulama hizmetini kullanabilir veya Yeni uygulama oluştur bağlantısına tıklayarak **yeni bir uygulama Azure App Service** oluşturabilirsiniz. Kaynak grubunu genişleterek mevcut uygulama hizmetinizi ağaç görünümünde  bulun veya Türe göre sıralamak için Görünüm ayarını **Kaynak türü** olarak değiştirebilirsiniz.

   ![Örnek seçmeyi gösteren App Service.](media/deploy-app-service/publish-app-service-windows2.png)

1. Yeni bir tane oluşturmanız, Azure'da bir kaynak grubu ve uygulama hizmeti oluşturulur. İsterseniz adları benzersiz olduğu sürece değiştirebilirsiniz.

   ![Uygulama oluşturmanın ekran App Service.](media/deploy-app-service/publish-app-service-windows3.png)

1. Varsayılan barındırma planını kabul etmek veya barındırma planını şimdi veya daha sonraki bir süre içinde Azure portal. Desteklenen `S1` bölgelerden biri varsayılan değerdir (küçük). Barındırma planı oluşturmak için Barındırma **Planı açılan** listesinden **Yeni'yi** seçin. Barındırma **Planı penceresi** görüntülenir.

   ![Barındırma planı seçeneklerini gösteren ekran görüntüsü.](media/deploy-app-service/hosting-plan.png)

   Bu seçeneklerle ilgili ayrıntıları planına genel bakış [Azure App Service görüntüebilirsiniz.](/azure/app-service/overview-hosting-plans)

1. Bu kaynakları seçmeyi veya oluşturmayı bitirip Bitir'i **seçin.** Kapsayıcınız, seçtiğiniz kaynak grubunda ve uygulama hizmette Azure'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında Yayımla sekmesi,  site URL'si dahil olmak üzere nelerin yayımladığı hakkında bilgi gösterir.

   :::image type="content" source="media/deploy-app-service/publish-succeeded-windows.png" alt-text="Yayımla sekmesinin ekran görüntüsü." lightbox="media/deploy-app-service/publish-succeeded-windows.png":::

1. Uygulamanın Azure'da beklendiği gibi çalıştığını doğrulamak için site bağlantısına tıklayın.

   ![Web uygulamasının ekran görüntüsü.](media/deploy-app-service/web-application-running2.png)

1. Yayımlama profili, kaynak grubu ve uygulama hizmeti gibi seçtiğiniz tüm ayrıntılarla birlikte kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak  için Yayımla  düğmesini, **Web** Yayımlama Etkinliği penceresindeki Yayımla düğmesini kullanın veya **Çözüm Gezgini'de** projeye sağ tıklayın ve bağlam menüsünde Yayımla öğesini seçin. 

:::moniker-end

:::moniker range=">=vs-2022"

1. Çözüm Gezgini'da **projenize sağ tıklayın ve** Yayımla'yı **seçin.**
1. Yayımla **iletişim** kutusunda **Azure hedefini** seçin.

   ![Yayımla sihirbazının ekran görüntüsü.](media/deploy-app-service/vs-2022/publish-choices.png)

1. Belirli **hedef sekmesinde,** kapsayıcı türünüze bağlı olarak **App Service (Windows)** veya **App Service (Linux)** gibi uygun dağıtım hedefini seçin.

   ![Yayımla sihirbazının Belirli hedef sekmesinin ekran görüntüsü.](media/deploy-app-service/vs-2022/publish-app-service-linux.png)
   
1. Kullanmak istediğiniz abonelikle doğru Azure hesabında oturum açmadıysanız Yayımla penceresinin sol üst kısmında yer alan düğmeyi **kullanarak oturum** açın.

1. Mevcut bir uygulama hizmetini kullanabilir veya Yeni uygulama oluştur bağlantısına tıklayarak **yeni bir uygulama Azure App Service** oluşturabilirsiniz. Kaynak grubunu genişleterek mevcut uygulama hizmetinizi ağaç görünümünde  bulun veya Türe göre sıralamak için Görünüm ayarını **Kaynak türü** olarak değiştirebilirsiniz.

   ![Örnek seçmeyi gösteren App Service.](media/deploy-app-service/vs-2022/publish-app-service-linux-2.png)

1. Yeni bir tane oluşturmanız, Azure'da bir kaynak grubu ve uygulama hizmeti oluşturulur. İsterseniz adları benzersiz olduğu sürece değiştirebilirsiniz.

   ![Uygulama oluşturmanın ekran App Service.](media/deploy-app-service/vs-2022/publish-app-service-linux-3.png)

1. Varsayılan barındırma planını kabul etmek veya barındırma planını şimdi veya daha sonraki bir süre içinde Azure portal. Desteklenen `S1` bölgelerden biri varsayılan değerdir (küçük). Barındırma planı oluşturmak için Barındırma **Planı açılan** listesinden **Yeni'yi** seçin. Barındırma **Planı penceresi** görüntülenir.

   ![Barındırma planı seçeneklerini gösteren ekran görüntüsü.](media/deploy-app-service/vs-2022/hosting-plan.png)

   Bu seçeneklerle ilgili ayrıntıları planına genel bakış [Azure App Service görüntüebilirsiniz.](/azure/app-service/overview-hosting-plans)

1. Bu kaynakları seçmeyi veya oluşturmayı bitirip Bitir'i **seçin.** Kapsayıcınız, seçtiğiniz kaynak grubunda ve uygulama hizmette Azure'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında Yayımla sekmesi,  site URL'si dahil olmak üzere nelerin yayımladığı hakkında bilgi gösterir.

   :::image type="content" source="media/deploy-app-service/vs-2022/publish-succeeded-linux.png" alt-text="Yayımla sekmesinin ekran görüntüsü." lightbox="media/deploy-app-service/vs-2022/publish-succeeded-linux.png":::

1. Uygulamanın Azure'da beklendiği gibi çalıştığını doğrulamak için site bağlantısına tıklayın.

   ![Web uygulamasının ekran görüntüsü.](media/deploy-app-service/web-application-running2.png)

1. Yayımlama profili, seçtiğiniz tüm ayrıntılarla (örneğin, kaynak grubu ve App Service) kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak için **Yayımla** düğmesini, **Web yayımlama etkinliği** penceresinde **Yayımla** düğmesini veya **Çözüm Gezgini** ' de projeye sağ tıklayıp içerik menüsünde **Yayımla** öğesini seçin.

:::moniker-end

## <a name="view-container-settings"></a>Kapsayıcı ayarlarını görüntüle

[Azure Portal](https://portal.azure.com), dağıtılan App Service açabilirsiniz.

dağıtılan App Service ayarlarını, **kapsayıcı ayarları** menüsünü açarak görüntüleyebilirsiniz (Visual Studio 2019 sürüm 16,4 veya sonraki bir sürümünü kullanırken).

![Azure portal kapsayıcı Ayarlar menüsünün ekran görüntüsü.](media/deploy-app-service/container-settings-menu.png)

Buradan, kapsayıcı bilgilerini görüntüleyebilir, günlükleri görüntüleyebilir veya indirebilir veya sürekli dağıtımı ayarlayabilirsiniz. Bkz. [Azure App Service sürekli DAĞıTıM CI/CD](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğreticiyle ilişkili tüm Azure kaynaklarını kaldırmak için [Azure Portal](https://portal.azure.com)kullanarak kaynak grubunu silin. yayımlanmış bir web uygulamasıyla ilişkili kaynak grubunu bulmak için   >  **diğer Windows**  >  **web yayımlama etkinliğini** görüntüle ' yi seçin ve ardından dişli simgesini seçin. Kaynak grubunu içeren **Yayımla** sekmesi açılır.

Azure portal, **kaynak grupları**' nı seçin, Ayrıntılar sayfasını açmak için kaynak grubunu seçin. Bunun doğru kaynak grubu olduğunu doğrulayıp **kaynak grubunu Kaldır**' ı seçin, adı yazın ve **Sil**' i seçin.

## <a name="next-steps"></a>Sonraki adımlar

[Azure App Service](/azure/app-service/overview)hakkında daha fazla bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

[Azure Container Registry’ye dağıtma](hosting-web-apps-in-docker.md)