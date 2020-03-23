---
title: Docker Hub'a ASP.NET Core Docker konteyneri dağıtın | Microsoft Dokümanlar
description: ASP.NET Core web uygulamasını Docker Hub'a dağıtmak için Visual Studio Container Tools'u nasıl kullanacağınızı öğrenin
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: b033825bbe8facbeae3dcdee6a5b563461921522
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188754"
---
# <a name="deploy-to-docker-hub"></a>Docker Hub’a dağıtma

Docker Hub, görüntü depolarınız için kullanışlı bir barındırma hizmeti sunar. Visual Studio'dan Docker Hub'a el ile kolayca dağıtabilirsiniz.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Docker hesabı ve Docker Hub deposu oluşturma

Zaten bir Docker hesabınız yoksa, Docker hesabı için [kaydolun.](https://hub.docker.com/signup)

Docker Hub deponuz yoksa, [Docker Hub'da](https://hub.docker.com/)bir tane oluşturun.

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Tek bir proje için resmi Docker Hub'a yayımla

1. Proje düğümüne sağ tıklayın ve **Yayımla'yı seçin...**. Dağıtım seçeneklerini gösteren bir ekran görüntülenir.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. **Yayımlama hedefini seç**altında, **Konteyner Kayıt Defteri'ni**seçin ve ardından **Docker Hub'ı**seçin. THe **Docker Hub** iletişim kutusu görüntülenir.

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Kendi deponuza (kuruluşun parçası değil) bağlanıyorsanız, onay kutusunu yayımlama için **kişisel bir depoya** bırakın. Depo bir kuruluşa aitse, onay kutusunu temizleyin ve kuruluş adını girin. Bağlandığınız depoya erişim izni olan Docker hesabınız için Docker kullanıcı adınızı ve parolanızı girin ve ardından **Kaydet'i**seçin.  

   Visual Studio, resminizi Docker Hub'a dağıtmaya çalışır.  Başarılı olursa, **Yayımlama** ekranı depo görüntüsü, görüntü etiketi, depo ve yapı yapılandırması** (örneğin, **Release)** için URL ile görünür.

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Bu sayfadaki **Yayımla** düğmesine tıklayarak istediğiniz zaman resmi güncelleyebilirsiniz.  Veya URL'nin altındaki bağlantıları kullanarak profili değiştirebilir veya kaldırabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Azure [Kapsayıcı Kayıt Defterine](/azure/container-registry/) Dağıt'taki adımları izleyerek Azure [Kapsayıcı Kayıt Defteri'nde](hosting-web-apps-in-docker.md)yayımlayın.

[Azure Pipelines](/azure/devops/pipelines/?view=azure-devops)ile sürekli tümleştirme ve teslim (CI/CD) ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

[Azure App Service](deploy-app-service.md)
[Visual Studio Konteyner Araçlarına](/visualstudio/containers/)dağıtın.