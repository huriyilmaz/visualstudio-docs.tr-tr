---
title: Azure App Service ASP.NET Core kapsayıcısını dağıtma
description: bir docker kapsayıcısında bir ASP.NET Core web uygulamasını dağıtmak için Visual Studio kapsayıcı araçlarını kullanmayı öğrenin Azure App Service
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 10/28/2021
ms.author: ghogen
ms.openlocfilehash: 0ce25161031c3634b1e244af9bb3428180b807d6
ms.sourcegitcommit: 0b949fd7bb38d784ff66edec4725de55d57e76fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "133219293"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Visual Studio kullanarak Azure App Service ASP.NET Core kapsayıcısını dağıtma

bu öğretici, kapsayıcılı ASP.NET Core web uygulamanızı bir [Azure App Service](/azure/app-service)yayımlamak için Visual Studio kullanma konusunda size kılavuzluk eder. Azure App Service, Azure 'da barındırılan tek kapsayıcılı bir Web uygulaması için uygun bir hizmettir.

Azure aboneliğiniz yoksa başlamadan önce [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

::: moniker range="vs-2017"
- "ASP.NET ve web geliştirme" iş yüküyle [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ' nin en son sürümünü yükler
::: moniker-end
::: moniker range="vs-2019"
- *ASP.NET ve web geliştirme* iş yüküyle [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) .
::: moniker-end
::: moniker range=">=vs-2022"
- *ASP.NET ve web geliştirme* iş yüküyle [Visual Studio 2022](https://visualstudio.microsoft.com/downloads) .
::: moniker-end

- [Docker Desktop](https://docs.docker.com/docker-for-windows/install/) 'ı yükler

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core web uygulaması oluşturma

aşağıdaki adımlar, bu öğreticide kullanılacak temel bir ASP.NET Core uygulaması oluştururken size rehberlik eder.

::: moniker range="vs-2017"
1. Visual Studio menüsünden **dosya > yeni > Project**' i seçin.
2. **yeni Project** iletişim kutusunun **şablonlar** bölümünde, **Visual C# > Web**' i seçin.
3. **ASP.NET Core Web uygulaması**' nı seçin.
4. Yeni uygulamanıza bir ad verin (veya varsayılanı alın) ve **Tamam**' ı seçin.
5. **Web uygulaması**' nı seçin.
6. **Docker desteğini etkinleştir** onay kutusunu işaretleyin.
7. **Linux** kapsayıcı türünü seçin ve **Tamam**' a tıklayın. 
::: moniker-end
::: moniker range=">= vs-2019"
1. Visual Studio başlat penceresinde **yeni proje oluştur**' u seçin.
1. **ASP.NET Core Web uygulaması**' nı seçin ve **ileri**' yi seçin.
1. Yeni uygulamanıza bir ad verin (veya varsayılanı alın) ve **İleri ' yi** seçin.
1. Hedeflemek istediğiniz .NET sürümünü seçin. Emin değilseniz, uzun süreli destek (LTS) sürümünü seçin.
1. SSL desteğini **https Için Yapılandır** onay kutusunu kullanarak isteyip istemediğinizi seçin.
1. **Docker desteğini etkinleştir** onay kutusunu işaretleyin.
1. Kapsayıcı türünü seçin ve **Oluştur**' a tıklayın.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Kapsayıcıyı Azure 'a dağıtma

::: moniker range="vs-2017"

1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. Hedef Yayımla iletişim kutusunda **App Service Linux** veya **App Service** öğesini seçin. Bu, Web sunucusunu barındıracak olan işletim sistemidir.
1. Yalnızca App Service yayımlayabilirsiniz veya App Service ve Azure Container Registry (ACR) ' de yayımlayabilirsiniz. Kapsayıcıyı bir Azure Container Registry (ACR) içinde yayımlamak için, **kapsayıcılar için yeni App Service oluştur**' u seçin ve **Yayımla**' ya tıklayın.

   ![Yayımla iletişim kutusunun ekran görüntüsü.](media/deploy-app-service/publish-app-service-linux-1.png)

   Yalnızca Azure Container Registry kullanmadan Azure App Service yayımlamak için **Yeni oluştur**' u seçin ve **Yayımla**' ya tıklayın.

1. Azure aboneliğinizle ilişkili hesapla oturum açtığınızdan emin olun ve benzersiz bir ad, abonelik, kaynak grubu, barındırma planı ve kapsayıcı kayıt defteri (varsa) seçin veya Varsayılanları kabul edin.

   ![Yayımlama ayarlarının ekran görüntüsü.](media/deploy-app-service/publish-app-service-linux-2.png)

1. **Oluştur**' a tıklayın. Kapsayıcınız, seçtiğiniz kaynak grubu ve kapsayıcı kayıt defterinde Azure 'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında, **Yayımla** sekmesi, SITE URL 'si dahil olmak üzere yayımlandıklarınız hakkındaki bilgileri gösterir.

   ![Yayımla sekmesinin ekran görüntüsü.](media/deploy-app-service/publish-succeeded.PNG)

1. Uygulamanızın Azure 'da beklendiği gibi çalıştığını doğrulamak için site bağlantısına tıklayın.

   ![Web uygulamasının ekran görüntüsü.](media/deploy-app-service/web-application-running.png)

1. Yayımlama profili, kaynak grubu ve kapsayıcı kayıt defteri gibi, seçtiğiniz tüm ayrıntılarla birlikte kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak için **Yayımla** düğmesini, **Web yayımlama etkinliği** penceresinde **Yayımla** düğmesini veya **Çözüm Gezgini** ' de projeye sağ tıklayıp içerik menüsünde **Yayımla** öğesini seçin.
:::moniker-end

:::moniker range="vs-2019"

1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. **Yayımla** Iletişim kutusunda **Azure** hedefini seçin.

   ![Yayımlama sihirbazının ekran görüntüsü.](media/deploy-app-service/publish-choices.png)

1. **belirli hedef** sekmesinde, kapsayıcı türüne bağlı olarak **App Service (Windows)** veya **App Service (Linux)** gibi uygun dağıtım hedefini seçin.

   ![Yayımlama sihirbazının belirli hedef sekmesinin ekran görüntüsü.](media/deploy-app-service/publish-app-service-windows.png)

1. Kullanmak istediğiniz abonelikle doğru Azure hesabında oturum açmadıysanız, **Yayımla** penceresinin sol üst kısmındaki düğmeyi kullanarak oturum açın.

1. **Yeni Azure App Service oluştur** bağlantısına tıklayarak mevcut bir App Service 'i kullanabilir veya yeni bir tane oluşturabilirsiniz. Kaynak grubunu genişleterek mevcut App Service 'i TreeView 'da bulun ya da türe göre sıralamak için **Görünüm** ayarını **kaynak türü** olarak değiştirin.

   ![App Service seçmeyi gösteren ekran görüntüsü.](media/deploy-app-service/publish-app-service-windows2.png)

1. Yeni bir tane oluşturursanız, Azure 'da bir kaynak grubu ve App Service oluşturulur. İsterseniz, benzersiz oldukları sürece adları değiştirebilirsiniz.

   ![App Service oluşturmayı gösteren ekran görüntüsü.](media/deploy-app-service/publish-app-service-windows3.png)

1. Varsayılan barındırma planını kabul edebilir veya barındırma planını şimdi veya Azure portal daha sonra değiştirebilirsiniz. Varsayılan değer, `S1` desteklenen bölgelerden birinde (küçük). Barındırma planı oluşturmak için **barındırma planı** açılan listesinin yanındaki **Yeni** ' yi seçin. **Barındırma planı** penceresi görüntülenir.

   ![Barındırma planı seçeneklerini gösteren ekran görüntüsü.](media/deploy-app-service/hosting-plan.png)

   Bu seçeneklerle ilgili ayrıntıları [Azure App Service plana genel bakış](/azure/app-service/overview-hosting-plans)' da görüntüleyebilirsiniz.

1. Bu kaynakları seçmeyi veya oluşturmayı tamamladıktan sonra **son**' u seçin. Kapsayıcınız, seçtiğiniz kaynak grubu ve App Service 'te Azure 'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında, **Yayımla** sekmesi, SITE URL 'si dahil olmak üzere yayımlandıklarınız hakkındaki bilgileri gösterir.

   :::image type="content" source="media/deploy-app-service/publish-succeeded-windows.png" alt-text="Yayımla sekmesinin ekran görüntüsü." lightbox="media/deploy-app-service/publish-succeeded-windows.png":::

1. Uygulamanızın Azure 'da beklendiği gibi çalıştığını doğrulamak için site bağlantısına tıklayın.

   ![Web uygulamasının ekran görüntüsü.](media/deploy-app-service/web-application-running2.png)

1. Yayımlama profili, seçtiğiniz tüm ayrıntılarla (örneğin, kaynak grubu ve App Service) kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak için **Yayımla** düğmesini, **Web yayımlama etkinliği** penceresinde **Yayımla** düğmesini veya **Çözüm Gezgini** ' de projeye sağ tıklayıp içerik menüsünde **Yayımla** öğesini seçin.

:::moniker-end

:::moniker range=">=vs-2022"

1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. **Yayımla** Iletişim kutusunda **Azure** hedefini seçin.

   ![Yayımlama sihirbazının ekran görüntüsü.](media/deploy-app-service/vs-2022/publish-choices.png)

1. **belirli hedef** sekmesinde, kapsayıcı türüne bağlı olarak **App Service (Windows)** veya **App Service (Linux)** gibi uygun dağıtım hedefini seçin.

   ![Yayımlama sihirbazının belirli hedef sekmesinin ekran görüntüsü.](media/deploy-app-service/vs-2022/publish-app-service-linux.png)
   
1. Kullanmak istediğiniz abonelikle doğru Azure hesabında oturum açmadıysanız, **Yayımla** penceresinin sol üst kısmındaki düğmeyi kullanarak oturum açın.

1. **Yeni Azure App Service oluştur** bağlantısına tıklayarak mevcut bir App Service 'i kullanabilir veya yeni bir tane oluşturabilirsiniz. Kaynak grubunu genişleterek mevcut App Service 'i TreeView 'da bulun ya da türe göre sıralamak için **Görünüm** ayarını **kaynak türü** olarak değiştirin.

   ![App Service seçmeyi gösteren ekran görüntüsü.](media/deploy-app-service/vs-2022/publish-app-service-linux-2.png)

1. Yeni bir tane oluşturursanız, Azure 'da bir kaynak grubu ve App Service oluşturulur. İsterseniz, benzersiz oldukları sürece adları değiştirebilirsiniz.

   ![App Service oluşturmayı gösteren ekran görüntüsü.](media/deploy-app-service/vs-2022/publish-app-service-linux-3.png)

1. Varsayılan barındırma planını kabul edebilir veya barındırma planını şimdi veya Azure portal daha sonra değiştirebilirsiniz. Varsayılan değer, `S1` desteklenen bölgelerden birinde (küçük). Barındırma planı oluşturmak için **barındırma planı** açılan listesinin yanındaki **Yeni** ' yi seçin. **Barındırma planı** penceresi görüntülenir.

   ![Barındırma planı seçeneklerini gösteren ekran görüntüsü.](media/deploy-app-service/vs-2022/hosting-plan.png)

   Bu seçeneklerle ilgili ayrıntıları [Azure App Service plana genel bakış](/azure/app-service/overview-hosting-plans)' da görüntüleyebilirsiniz.

1. Bu kaynakları seçmeyi veya oluşturmayı tamamladıktan sonra **son**' u seçin. Kapsayıcınız, seçtiğiniz kaynak grubu ve App Service 'te Azure 'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında, **Yayımla** sekmesi, SITE URL 'si dahil olmak üzere yayımlandıklarınız hakkındaki bilgileri gösterir.

   :::image type="content" source="media/deploy-app-service/vs-2022/publish-succeeded-linux.png" alt-text="Yayımla sekmesinin ekran görüntüsü." lightbox="media/deploy-app-service/vs-2022/publish-succeeded-linux.png":::

1. Uygulamanızın Azure 'da beklendiği gibi çalıştığını doğrulamak için site bağlantısına tıklayın.

   ![Web uygulamasının ekran görüntüsü.](media/deploy-app-service/web-application-running2.png)

1. Yayımlama profili, kaynak grubu ve uygulama hizmeti gibi seçtiğiniz tüm ayrıntılarla birlikte kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak  için Yayımla  düğmesini, **Web** Yayımlama Etkinliği penceresindeki Yayımla düğmesini kullanın veya **Çözüm Gezgini'de** projeye sağ tıklayın ve bağlam menüsünde Yayımla öğesini seçin. 

:::moniker-end

## <a name="view-container-settings"></a>Kapsayıcı ayarlarını görüntüleme

uygulama [Azure portal,](https://portal.azure.com)dağıtılan kaynaklarınızı App Service.

Kapsayıcı ayarları menüsünü açarak (App Service 2019 sürüm 16.4 veya sonraki bir sürümü kullanırken) dağıtılan Visual Studio ayarları görüntüebilirsiniz. 

![Azure portal'Ayarlar Container Azure portal.](media/deploy-app-service/container-settings-menu.png)

Buradan kapsayıcı bilgilerini görüntüleyebilirsiniz, günlükleri indirebilirsiniz veya sürekli dağıtım kurabilirsiniz. Bkz. [Azure App Service Dağıtım CI/CD.](/azure/app-service/containers/app-service-linux-ci-cd)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğreticiyle ilişkili tüm Azure kaynaklarını kaldırmak için kaynak grubunu silmek için [Azure portal.](https://portal.azure.com) Yayımlanmış bir web uygulamasıyla ilişkilendirilmiş kaynak grubunu bulmak için Web Yayımlama Etkinliği'Windows DiğerNini  >    >  Görüntüle'yi **seçin** ve ardından dişli simgesini seçin. Kaynak **grubunu** içeren Yayımla sekmesi açılır.

Kaynak **Azure portal'yi seçin,** kaynak grubunu seçerek ayrıntılar sayfasını açın. Bunun doğru kaynak grubu olduğunu doğrulayın, sonra Kaynak grubunu **kaldır'ı seçin,** adı yazın ve Sil'i **seçin.**

## <a name="next-steps"></a>Sonraki adımlar

hakkında daha fazla bilgi [Azure App Service.](/azure/app-service/overview)

## <a name="see-also"></a>Ayrıca bkz.

[Azure Container Registry’ye dağıtma](hosting-web-apps-in-docker.md)
