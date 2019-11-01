---
title: Azure App Service bir ASP.NET Core Docker kapsayıcısı dağıtın | Microsoft Docs
description: ASP.NET Core Web uygulamasını dağıtmak için Visual Studio kapsayıcı araçlarını kullanmayı öğrenin Azure App Service
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 03/08/2019
ms.author: ghogen
ms.openlocfilehash: 5d1f160435fd8c62a44d3e5d3192870143558de4
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188783"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Visual Studio kullanarak Azure App Service ASP.NET Core kapsayıcısını dağıtma

Bu öğretici, Kapsayıcılı ASP.NET Core Web uygulamanızı bir [Azure App Service](/azure/app-service)yayımlamak Için Visual Studio 'yu kullanma konusunda size kılavuzluk eder. Azure App Service, Azure 'da barındırılan tek kapsayıcılı bir Web uygulaması için uygun bir hizmettir.

Azure aboneliğiniz yoksa başlamadan önce [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) oluşturun.

## <a name="prerequisites"></a>Prerequisites

Bu öğreticiyi tamamlayabilmeniz için:

::: moniker range="vs-2017"
- "ASP.NET and Web Development" iş yüküne sahip [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ' in en son sürümünü yükler
::: moniker-end
::: moniker range=">=vs-2019"
- *ASP.net ve Web geliştirme* iş yüküyle [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) .
::: moniker-end
- [Docker Desktop](https://docs.docker.com/docker-for-windows/install/) 'ı yükler

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core Web uygulaması oluşturma

Aşağıdaki adımlar, bu öğreticide kullanılacak temel bir ASP.NET Core uygulaması oluştururken size rehberlik eder.

::: moniker range="vs-2017"
1. Visual Studio menüsünden **dosya > yeni > proje**' yi seçin.
2. **Yeni proje** Iletişim kutusunun **Şablonlar** bölümünde,  **C# Visual > Web**' i seçin.
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
1. **Linux** kapsayıcı türünü seçin ve **Oluştur**' a tıklayın. Windows kapsayıcıları bir kapsayıcı olarak Azure App Service dağıtmak için desteklenmez.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Kapsayıcıyı Azure 'a dağıtma

1. **Çözüm Gezgini** ' de projenize sağ tıklayın ve **Yayımla**' yı seçin.
1. Hedefi Yayımla iletişim kutusunda **App Service Linux**' u seçin.
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
1. Aynı yayımlama profiliyle yeniden dağıtmak için **Yayımla** düğmesini, **Web yayımlama etkinliği** penceresinde **Yayımla** düğmesini veya **Çözüm Gezgini** ' de projeye sağ tıklayıp **Yayımla** öğesini seçin. bağlam menüsü.

## <a name="clean-up-resources"></a>Kaynakları Temizleme

Bu öğreticiyle ilişkili tüm Azure kaynaklarını kaldırmak için [Azure Portal](https://portal.azure.com)kullanarak kaynak grubunu silin. Yayımlanmış bir Web uygulamasıyla ilişkili kaynak grubunu bulmak için, **diğer Windows** > **web yayımlama etkinliği** > **görüntüle** ' yi seçin ve ardından dişli simgesini seçin. Kaynak grubunu içeren **Yayımla** sekmesi açılır.

Azure portal, **kaynak grupları**' nı seçin, Ayrıntılar sayfasını açmak için kaynak grubunu seçin. Bunun doğru kaynak grubu olduğunu doğrulayın ve ardından **kaynak grubunu Kaldır**' ı seçin, adı yazın ve **Sil**' i seçin.

## <a name="next-steps"></a>Sonraki adımlar

[Azure Pipelines](/azure/devops/pipelines/?view=azure-devops)ile sürekli tümleştirme ve teslım (CI/CD) ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

[Azure Container Registry dağıtma](hosting-web-apps-in-docker.md)