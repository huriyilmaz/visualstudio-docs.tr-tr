---
title: Azure App Service bir ASP.NET Core Docker kapsayıcısı dağıtın | Microsoft Docs
description: ASP.NET Core Web uygulamasını dağıtmak için Visual Studio kapsayıcı araçlarını kullanmayı öğrenin Azure App Service
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 43bd06fba795c09bfa341ce7b61a3ced0fe15214
ms.sourcegitcommit: 510a928153470e2f96ef28b808f1d038506cce0c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86454169"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Visual Studio kullanarak Azure App Service ASP.NET Core kapsayıcısını dağıtma

Bu öğretici, Kapsayıcılı ASP.NET Core Web uygulamanızı bir [Azure App Service](/azure/app-service)yayımlamak Için Visual Studio 'yu kullanma konusunda size kılavuzluk eder. Azure App Service, Azure 'da barındırılan tek kapsayıcılı bir Web uygulaması için uygun bir hizmettir.

Azure aboneliğiniz yoksa başlamadan önce [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) oluşturun.

## <a name="prerequisites"></a>Ön koşullar

Bu öğreticiyi tamamlamak için:

::: moniker range="vs-2017"
- "ASP.NET and Web Development" iş yüküne sahip [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ' in en son sürümünü yükler
::: moniker-end
::: moniker range=">=vs-2019"
- *ASP.net ve Web geliştirme* iş yüküyle [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) .
::: moniker-end
- [Docker Desktop](https://docs.docker.com/docker-for-windows/install/) 'ı yükler

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core web uygulaması oluşturma

Aşağıdaki adımlar, bu öğreticide kullanılacak temel bir ASP.NET Core uygulaması oluştururken size rehberlik eder.

::: moniker range="vs-2017"
1. Visual Studio menüsünden **dosya > yeni > proje**' yi seçin.
2. **Yeni proje** Iletişim kutusunun **Şablonlar** bölümünde, **Visual C# > Web**' i seçin.
3. **ASP.NET Core Web uygulaması**' nı seçin.
4. Yeni uygulamanıza bir ad verin (veya varsayılanı alın) ve **Tamam**' ı seçin.
5. **Web uygulaması**' nı seçin.
6. **Docker desteğini etkinleştir** onay kutusunu işaretleyin.
7. **Linux** kapsayıcı türünü seçin ve **Tamam**' a tıklayın. Windows kapsayıcıları bir kapsayıcı olarak Azure App Service dağıtmak için desteklenmez.
::: moniker-end
::: moniker range=">= vs-2019"
1. Visual Studio başlangıç penceresinde **Yeni proje oluştur**' u seçin.
1. **ASP.NET Core Web uygulaması**' nı seçin ve **İleri**' yi seçin.
1. Yeni uygulamanıza bir ad verin (veya varsayılanı alın) ve **Oluştur**' a tıklayın.
1. **Web uygulaması**' nı seçin.
1. SSL desteğini **https Için Yapılandır** onay kutusunu kullanarak isteyip istemediğinizi seçin.
1. **Docker desteğini etkinleştir** onay kutusunu işaretleyin.
1. Kapsayıcı türünü seçin ve **Oluştur**' a tıklayın.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Kapsayıcıyı Azure 'a dağıtma

::: moniker range="vs-2017"

1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. Hedef Yayımla iletişim kutusunda **App Service Linux** veya **App Service**öğesini seçin. Bu, Web sunucusunu barındıracak olan işletim sistemidir.
1. Yalnızca App Service yayımlayabilirsiniz veya App Service ve Azure Container Registry (ACR) ' de yayımlayabilirsiniz. Kapsayıcıyı bir Azure Container Registry (ACR) içinde yayımlamak için, **kapsayıcılar için yeni App Service oluştur**' u seçin ve **Yayımla**' ya tıklayın.

   ![Yayımla iletişim kutusunun ekran görüntüsü](media/deploy-app-service/publish-app-service-linux.PNG)

   Yalnızca Azure Container Registry kullanmadan Azure App Service yayımlamak için **Yeni oluştur**' u seçin ve **Yayımla**' ya tıklayın.

1. Azure aboneliğinizle ilişkili hesapla oturum açtığınızdan emin olun ve benzersiz bir ad, abonelik, kaynak grubu, barındırma planı ve kapsayıcı kayıt defteri (varsa) seçin veya Varsayılanları kabul edin.

   ![Yayımlama ayarlarının ekran görüntüsü](media/deploy-app-service/publish-app-service-linux2.png)

1. **Oluştur**' a tıklayın. Kapsayıcınız, seçtiğiniz kaynak grubu ve kapsayıcı kayıt defterinde Azure 'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında, **Yayımla** sekmesi, SITE URL 'si dahil olmak üzere yayımlandıklarınız hakkındaki bilgileri gösterir.

   ![Yayımla sekmesinin ekran görüntüsü](media/deploy-app-service/publish-succeeded.PNG)

1. Uygulamanızın Azure 'da beklendiği gibi çalıştığını doğrulamak için site bağlantısına tıklayın.

   ![Web uygulamasının ekran görüntüsü](media/deploy-app-service/web-application-running.png)

1. Yayımlama profili, kaynak grubu ve kapsayıcı kayıt defteri gibi, seçtiğiniz tüm ayrıntılarla birlikte kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak için **Yayımla** düğmesini, **Web yayımlama etkinliği** penceresinde **Yayımla** düğmesini veya **Çözüm Gezgini** ' de projeye sağ tıklayıp içerik menüsünde **Yayımla** öğesini seçin.
:::moniker-end
:::moniker range=">=vs-2019"
1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. **Yayımla** Iletişim kutusunda **Azure** hedefini seçin.

   ![Yayımlama sihirbazının ekran görüntüsü](media/deploy-app-service/publish-choices.png)

1. **Belirli hedef** sekmesinde, kapsayıcı türüne göre **App Service (Windows)** veya **App Service (Linux)** gibi uygun dağıtım hedefini seçin.

   ![Yayımlama sihirbazının belirli hedef sekmesinin ekran görüntüsü](media/deploy-app-service/publish-app-service-windows.png)

1. Kullanmak istediğiniz abonelikle doğru Azure hesabında oturum açmadıysanız, **Yayımla** penceresinin sol üst kısmındaki düğmeyi kullanarak oturum açın.

1. **Yeni Azure App Service oluştur** bağlantısına tıklayarak mevcut bir App Service 'i kullanabilir veya yeni bir tane oluşturabilirsiniz. Kaynak grubunu genişleterek mevcut App Service 'i TreeView 'da bulun ya da türe göre sıralamak için **Görünüm** ayarını **kaynak türü** olarak değiştirin.

   ![App Service seçmeyi gösteren ekran görüntüsü](media/deploy-app-service/publish-app-service-windows2.png)

1. Yeni bir tane oluşturursanız, Azure 'da bir kaynak grubu ve App Service oluşturulur. İsterseniz, benzersiz oldukları sürece adları değiştirebilirsiniz.

   ![App Service oluşturmayı gösteren ekran görüntüsü](media/deploy-app-service/publish-app-service-windows3.png)

1. Varsayılan barındırma planını kabul edebilir veya barındırma planını şimdi veya Azure portal daha sonra değiştirebilirsiniz. Varsayılan değer, `S1` desteklenen bölgelerden birinde (küçük). Barındırma planı oluşturmak için **barındırma planı** açılan listesinin yanındaki **Yeni** ' yi seçin. **Barındırma planı** penceresi görüntülenir.

   ![Barındırma planı seçeneklerini gösteren ekran görüntüsü](media/deploy-app-service/hosting-plan.png)

   Bu seçeneklerle ilgili ayrıntıları [Azure App Service plana genel bakış](/azure/app-service/overview-hosting-plans)' da görüntüleyebilirsiniz.

1. Bu kaynakları seçmeyi veya oluşturmayı tamamladıktan sonra **son**' u seçin. Kapsayıcınız, seçtiğiniz kaynak grubu ve App Service 'te Azure 'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında, **Yayımla** sekmesi, SITE URL 'si dahil olmak üzere yayımlandıklarınız hakkındaki bilgileri gösterir.

   ![Yayımla sekmesinin ekran görüntüsü](media/deploy-app-service/publish-succeeded-windows.png)

1. Uygulamanızın Azure 'da beklendiği gibi çalıştığını doğrulamak için site bağlantısına tıklayın.

   ![Web uygulamasının ekran görüntüsü](media/deploy-app-service/web-application-running2.png)

1. Yayımlama profili, seçtiğiniz tüm ayrıntılarla (örneğin, kaynak grubu ve App Service) kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak için **Yayımla** düğmesini, **Web yayımlama etkinliği** penceresinde **Yayımla** düğmesini veya **Çözüm Gezgini** ' de projeye sağ tıklayıp içerik menüsünde **Yayımla** öğesini seçin.
:::moniker-end

## <a name="view-container-settings"></a>Kapsayıcı ayarlarını görüntüle

[Azure Portal](https://portal.azure.com), dağıtılan App Service açabilirsiniz.

Dağıtılan App Service ayarlarını, **kapsayıcı ayarları** menüsünü açarak görüntüleyebilirsiniz (Visual Studio 2019 sürüm 16,4 veya üstünü kullanırken).

![Azure portal kapsayıcı Ayarları menüsünün ekran görüntüsü](media/deploy-app-service/container-settings-menu.png)

Buradan, kapsayıcı bilgilerini görüntüleyebilir, günlükleri görüntüleyebilir veya indirebilir veya sürekli dağıtımı ayarlayabilirsiniz. Bkz. [Azure App Service sürekli DAĞıTıM CI/CD](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğreticiyle ilişkili tüm Azure kaynaklarını kaldırmak için [Azure Portal](https://portal.azure.com)kullanarak kaynak grubunu silin. Yayımlanmış bir Web uygulamasıyla ilişkili kaynak grubunu bulmak için, **View**  >  **diğer Windows**  >  **Web yayımlama etkinliğini**görüntüle ' yi seçin ve ardından dişli simgesini seçin. Kaynak grubunu içeren **Yayımla** sekmesi açılır.

Azure portal, **kaynak grupları**' nı seçin, Ayrıntılar sayfasını açmak için kaynak grubunu seçin. Bunun doğru kaynak grubu olduğunu doğrulayıp **kaynak grubunu Kaldır**' ı seçin, adı yazın ve **Sil**' i seçin.

## <a name="next-steps"></a>Sonraki adımlar

[Azure App Service](/azure/app-service/overview)hakkında daha fazla bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

[Azure Container Registry’ye dağıtma](hosting-web-apps-in-docker.md)