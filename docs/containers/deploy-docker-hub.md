---
title: ASP.NET Core'a bir Docker kapsayıcısı Docker Hub | Microsoft Docs
description: Visual Studio Container Tools'ASP.NET Core web uygulamasını Docker Hub
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 10/28/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 528a6624b698753e606cbc8ad6a06b619fd9cdca
ms.sourcegitcommit: aff49629012f4d5fa07c75ea0ca5bf53d28aa173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2021
ms.locfileid: "131662655"
---
# <a name="deploy-to-docker-hub"></a>Docker Hub’a dağıtma

Docker Hub, görüntü depolarınız için kullanışlı bir barındırma hizmeti sağlar. Bir sanal ağdan Docker Hub kolayca Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Docker hesabı oluşturma ve Docker Hub oluşturma

[Henüz](https://hub.docker.com/signup) bir Docker hesabınız yoksa, bir Docker hesabına kaydolabilirsiniz.

Yeni bir depoya sahip değil Docker Hub, [Docker Hub.](https://hub.docker.com/)

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Görüntüyü tek bir proje için yayımlayın Docker Hub

1. Proje düğümüne sağ tıklayın ve **Yayımla... öğesini seçin.** Dağıtım seçeneklerini gösteren bir ekran görüntülenir.

   :::moniker range="vs-2019"
   ![Dağıtım seçeneklerinin ekran görüntüsü.](media/container-tools/vs-2019/docker-container-registry.png)
   :::moniker-end
   :::moniker range=">=vs-2022"
   ![Dağıtım seçeneklerinin ekran görüntüsü.](media/container-tools/vs-2022/docker-container-registry.png)
   :::moniker-end

1. **Docker Container Registry'ı** seçin ve sonra **da** Docker Hub.

   :::moniker range="vs-2019"
   ![Yayımla iletişim kutusunun ekran görüntüsü - Docker Hub.](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)
   :::moniker-end
   :::moniker range=">=vs-2022"
   ![Yayımla iletişim kutusunun ekran görüntüsü - Docker Hub.](media/deploy-docker-hub/vs-2022/container-tools-docker-hub-deploy.png)
   :::moniker-end

1. Docker kimlik bilgilerinizi girin.

   :::moniker range="vs-2019"
   ![Docker Hub ekran görüntüsü.](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)
   :::moniker-end
   :::moniker range=">=vs-2022"
   ![Docker Hub ekran görüntüsü.](media/deploy-docker-hub/vs-2022/container-tools-docker-hub-credentials.png)
   :::moniker-end

1. Kendi deponıza bağlanıyorsanız (bir kuruluşun parçası değil), Kişisel depoda yayımla **onay kutusunu işaretli** bırakın. Depo bir kuruluşa aitse onay kutusunu temizleyin ve kuruluş adını girin. Bağlanmakta olduğu depoya erişim izni olan Docker hesabınız için Docker kullanıcı adınızı ve parolanızı girin ve kaydet'i **seçin.**

   Visual Studio, görüntülerinizi dağıtıma Docker Hub.  Başarılı olursa, **yayımla** ekranı depo görüntüsünün URL'sini, görüntü etiketini, depoyu ve derleme yapılandırmasını (örneğin, **Sürüm) görüntüler.**

   :::moniker range="vs-2019"
   ![Yayımla ekran görüntüsü.](media/deploy-docker-hub/container-tools-docker-hub-finished.png)
   :::moniker-end
   :::moniker range=">=vs-2022"
   :::image type="content" source="media/deploy-docker-hub/vs-2022/container-tools-docker-hub-finished.png" alt-text="Yayımla ekran görüntüsü." lightbox="media/deploy-docker-hub/vs-2022/container-tools-docker-hub-finished.png":::
   :::moniker-end

1. Bu sayfada Yayımla düğmesine tıklayarak görüntüyü **istediğiniz zaman** güncelleştirebilirsiniz.  Veya URL'nin altındaki bağlantıları kullanarak profili değiştirebilir veya kaldırabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

[Azure Container Registry'a](/azure/container-registry/) dağıtma makalesinde verilen adımları [Azure Container Registry.](hosting-web-apps-in-docker.md)

ile sürekli tümleştirme ve teslim (CI/CD) [Azure Pipelines.](/azure/devops/pipelines/?view=azure-devops&preserve-view=true)

## <a name="see-also"></a>Ayrıca bkz.

[Azure App Service'a dağıtma](deploy-app-service.md) 
 [Visual Studio Kapsayıcı Araçları.](./index.yml)