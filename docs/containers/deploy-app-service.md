---
title: Azure Uygulama Hizmetine ASP.NET Core Docker kapsayıcısı dağıtma | Microsoft Dokümanlar
description: ASP.NET Core web uygulamasını Azure Uygulama Hizmetine dağıtmak için Visual Studio Container Tools'u nasıl kullanacağınızı öğrenin
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 6c1d56f788294826853ad441313597255308bb39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027285"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Visual Studio'ASP.NET kullanarak Azure Uygulama Hizmetine ASP.NET Core kapsayıcısı dağıtma

Bu öğretici, konteynırlaştırılmış ASP.NET Core web uygulamanızı azure [uygulama hizmetinde](/azure/app-service)yayınlamak için Visual Studio'yu kullanmanızı kolaylaştırır. Azure Uygulama Hizmeti, Azure'da barındırılan tek konteynerli bir web uygulaması için uygun bir hizmettir.

Azure aboneliğiniz yoksa, başlamadan önce [ücretsiz](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) bir hesap oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

::: moniker range="vs-2017"
- [Visual Studio 2017'nin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) en son sürümünü "ASP.NET ve web geliştirme" iş yüküyle yükleyin
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) *ASP.NET ve web geliştirme* iş yükü ile.
::: moniker-end
- [Docker Masaüstü'nü](https://docs.docker.com/docker-for-windows/install/) Yükle

## <a name="create-an-aspnet-core-web-app"></a>ASP.NET Core web uygulaması oluşturma

Aşağıdaki adımlar, bu öğreticide kullanılacak temel bir ASP.NET Core uygulaması oluşturmada size yol gösterecektir.

::: moniker range="vs-2017"
1. Visual Studio menüsünden **Dosya > Yeni > Projesi'ni**seçin.
2. **Yeni Proje** iletişim kutusunun **Şablonlar** bölümünde Visual **C# > Web'i**seçin.
3. **Core Web Uygulaması ASP.NET**seçin.
4. Yeni uygulamanıza bir ad verin (veya varsayılanı alın) ve **Tamam'ı**seçin.
5. **Web Uygulamasını**Seçin.
6. Docker **Destek'i Etkinleştir** onay kutusunu işaretleyin.
7. **Linux** kapsayıcı türünü seçin ve **Tamam'ı**tıklatın. Windows kapsayıcıları, Azure Uygulama Hizmeti'ne kapsayıcı olarak dağıtılmak üzere desteklenmez.
::: moniker-end
::: moniker range=">= vs-2019"
1. Visual Studio başlangıç penceresinden **yeni bir proje oluştur'u**seçin.
1. **Core Web Uygulaması ASP.NET**seçin ve **İleri'yi**seçin.
1. Yeni uygulamanıza bir ad verin (veya varsayılanı alın) ve **Oluştur'u**seçin.
1. **Web Uygulaması**seçin.
1. HTTPS onay kutusunu **yapılandırmayı** kullanarak SSL desteği isteyip istemediğinizi seçin.
1. Docker **Destek'i Etkinleştir** onay kutusunu işaretleyin.
1. Kapsayıcı türünü seçin ve **Oluştur'u**tıklatın. Windows kapsayıcıları, Azure Uygulama Hizmeti'ne kapsayıcı olarak dağıtılmak üzere desteklenmez.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Kapsayıcıyı Azure'a dağıtma

1. **Çözüm Gezgini'nde** projenize sağ tıklayın ve **Yayımla'yı**seçin.
1. Yayımlama hedef iletişim kutusunda App **Service Linux** veya App **Service'i**seçin. Bu, web sunucusunu barındıracak işletim sistemidir.
1. Yalnızca Uygulama Hizmeti'nde yayımlayabilir veya hem Uygulama Hizmeti'nde hem de Azure Kapsayıcı Kayıt Defteri'nde (ACR) yayımlayabilirsiniz. Kapsayıcıyı Azure Kapsayıcı Kayıt Defteri'nde (ACR) yayımlamak **için kapsayıcılar için yeni Uygulama Hizmeti Oluştur'u**seçin ve **Yayımla'yı**tıklatın.

   ![Yayımlama iletişim kutusunun ekran görüntüsü](media/deploy-app-service/publish-app-service-linux.PNG)

   Azure Kapsayıcı Kayıt Defteri'ni kullanmadan yalnızca bir Azure Uygulama Hizmetinde yayımlamak için **yeni Oluştur'u**seçin ve **Yayımla'yı**tıklatın.

1. Azure aboneliğinizle ilişkili hesapla oturum unuzu kaplayıp imzalamadığınızı kontrol edin ve benzersiz bir ad, abonelik, kaynak grubu, barındırma planı ve konteyner kayıt defteri (varsa) seçin veya varsayılanları kabul edin.

   ![Yayımlama ayarlarının ekran görüntüsü](media/deploy-app-service/publish-app-service-linux2.png)

1. **Oluştur**’u seçin. Kapsayıcınız seçtiğiniz kaynak grubunda ve kapsayıcı kayıt defterinde Azure'a dağıtılır. Bu işlem biraz zaman alır. Tamamlandığında, **Yayımla** sekmesi site URL'si de dahil olmak üzere ne yayımlandığı hakkında bilgi gösterir.

   ![Yayımlama sekmesinin ekran görüntüsü](media/deploy-app-service/publish-succeeded.PNG)

1. Uygulamanızın Azure'da beklendiği gibi çalıştığını doğrulamak için site bağlantısını tıklayın.

   ![Web uygulamasının ekran görüntüsü](media/deploy-app-service/web-application-running.png)

1. Yayımlama profili, kaynak grubu ve kapsayıcı kayıt defteri gibi seçtiğiniz tüm ayrıntılarla birlikte kaydedilir.

1. Aynı yayımlama profiliyle yeniden dağıtmak için, **Etkinliği Yayımla** düğmesini, **Web Yayımlama Etkinliği** **penceresindeyayım** düğmesini kullanın veya **Solution Explorer'daki** projeye sağ tıklayın ve bağlam menüsünde **Yayımla** öğesini seçin.

## <a name="view-container-settings"></a>Kapsayıcı ayarlarını görüntüleme

Azure [portalında,](https://portal.azure.com)dağıtılan Uygulama Hizmetinizi açabilirsiniz.

**Konteyner ayarları* menüsünü açarak dağıtılan Uygulama Hizmetinizin ayarlarını görüntüleyebilirsiniz (Visual Studio 2019 sürüm 16.4 veya sonrası kullanırken).

![Azure portalında Kapsayıcı Ayarları menüsünün ekran görüntüsü](media/deploy-app-service/container-settings-menu.png)

Buradan, kapsayıcı bilgilerini görüntüleyebilir, günlükleri görüntüleyebilir veya indirebilir veya sürekli dağıtım ayarlayabilirsiniz. Bkz. [Azure Uygulama Hizmeti Sürekli Dağıtım CI/CD.](/azure/app-service/containers/app-service-linux-ci-cd)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğreticiyle ilişkili tüm Azure kaynaklarını kaldırmak [için, Azure portalını](https://portal.azure.com)kullanarak kaynak grubunu silin. Yayımlanmış bir web uygulamasıyla ilişkili kaynak grubunu bulmak için**Diğer Windows** > **Web Yayımlama Etkinliğini** **Görüntüle'yi** > ve ardından dişli simgesini seçin. Kaynak grubunu içeren **Yayımla** sekmesi açılır.

Azure portalında **Kaynak gruplarını**seçin, ayrıntılar sayfasını açmak için kaynak grubunu seçin. Bunun doğru kaynak grubu olduğunu doğrulayın ve ardından **kaynak grubunu kaldır'ı**seçin, adı yazın ve **Sil'i**seçin.

## <a name="next-steps"></a>Sonraki adımlar

[Azure App Service Linux](/azure/app-service/containers/app-service-linux-intro)hakkında daha fazla bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

[Azure Container Registry’ye dağıtma](hosting-web-apps-in-docker.md)