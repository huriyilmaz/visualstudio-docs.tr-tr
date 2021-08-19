---
title: Docker Hub |'ASP.NET Core docker kapsayıcısı dağıtma Microsoft Docs
description: Visual Studio Container Tools'ASP.NET Core web uygulamasını Docker Hub
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 2fe4c9a1ac39ed090eae657c02ea8417002a2473
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059339"
---
# <a name="deploy-to-docker-hub"></a>Docker Hub’a dağıtma

Docker Hub, görüntü depolarınız için kullanışlı bir barındırma hizmeti sağlar. Bu sanal ağdan el Docker Hub kolayca Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Docker hesabı oluşturma ve Docker Hub oluşturma

[Henüz](https://hub.docker.com/signup) bir Docker hesabınız yoksa, bir Docker hesabına kaydolabilirsiniz.

Yeni bir depoya sahip Docker Hub, [Docker Hub.](https://hub.docker.com/)

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Görüntüyü tek bir proje için yayımlayın ve Docker Hub

1. Proje düğümüne sağ tıklayın ve **Yayımla... öğesini seçin.** Dağıtım seçeneklerini gösteren bir ekran görüntülenir.

   ![Dağıtım seçeneklerinin ekran görüntüsü](media/container-tools/vs-2019/docker-container-registry.png)

1. **Docker Container Registry'yi** seçin ve sonra **da** Docker Hub.

   ![Yayımla iletişim kutusunun ekran görüntüsü - Docker Hub](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Docker kimlik bilgilerinizi girin.

   ![Docker Hub ekran görüntüsü](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Kendi deponıza bağlanıyorsanız (bir kuruluşun parçası değil), Kişisel depoda yayımla **onay kutusunu işaretli** bırakın. Depo bir kuruluşa aitse onay kutusunu temizleyin ve kuruluş adını girin. Bağlanmakta olduğu depoya erişim izni olan Docker hesabınız için Docker kullanıcı adınızı ve parolanızı girin ve kaydet'i **seçin.**

   Visual Studio, görüntünizi dağıtıma Docker Hub.  Başarılı olursa, **yayımla** ekranı depo görüntüsünün URL'sini, görüntü etiketini, depoyu ve derleme yapılandırmasını (örneğin, **Sürüm) görüntüler.**

   ![Yayımla ekran görüntüsü](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Bu sayfada Yayımla düğmesine tıklayarak görüntüyü istediğiniz **zaman** güncelleştirebilirsiniz.  Veya URL'nin altındaki bağlantıları kullanarak profili değiştirebilir veya kaldırabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

[Azure Container Registry'a](/azure/container-registry/) dağıtma makalesinde verilen adımları [Azure Container Registry.](hosting-web-apps-in-docker.md)

ile sürekli tümleştirme ve teslim (CI/CD) [Azure Pipelines.](/azure/devops/pipelines/?view=azure-devops&preserve-view=true)

## <a name="see-also"></a>Ayrıca bkz.

[Azure App Service'a dağıtma](deploy-app-service.md) 
 [Visual Studio Kapsayıcı Araçları.](./index.yml)