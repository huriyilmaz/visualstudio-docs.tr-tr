---
title: Linux'ta Uygulama Hizmetine Yayımla
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 1e05862aa57c24bfa8f17d551762054278dd6e52
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806865"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Visual Studio'ASP.NET kullanarak Linux'ta App Service'e ASP.NET Core uygulaması yayınlama

Visual Studio 2017 sürüm 15.7'den başlayarak, aşağıdaki yöntemlerden birini kullanarak ASP.NET Core uygulamalarını Azure App Service Linux'a (kapsayıcılar kullanarak) yayınlayabilirsiniz.

* Uygulamaların sürekli (veya otomatik) dağıtımı için [Azure Ardışık Hatları](/azure/devops/pipelines/get-started-yaml?view=azdevops)ile Azure DevOps'leri kullanın.

* Uygulamaların tek seferlik (veya manuel) dağıtımı için Visual Studio'da **Yayımla** aracını kullanarak ASP.NET Core uygulamalarını Linux için Uygulama Hizmetine (kapsayıcıları kullanarak) yayınlayın.

Bu makalede, **yayımlama** aracının tek seferlik dağıtım için nasıl kullanılacağı açıklanmaktadır.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Linux'ta Uygulama Hizmetine Yayımla

1. Çözüm Gezgini'nde projeyi sağ tıklatın ve **Yayımla'yı** seçin (veya **Yapı** > **Yayımla** menüsü öğesini kullanın).

    ![Çözüm Gezgini'nde proje bağlamı menüsünde Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla'yı Seçin")

1. Daha önce yayımlama profillerini yapılandırmışsanız, **Yayımla** bölmesi görüntülenir ve bu durumda **yeni profil oluştur'u**seçin.

1. **Yayımlama hedef** iletişim kutusunu seç'te **App Service Linux'u**seçin.

    ![Azure Uygulama Hizmeti'ni seçin](../deployment/media/quickstart-publish-linux.png "Azure Uygulama Hizmeti'ni seçin")

1. **Yayımla**’yı seçin. **Uygulama Hizmeti Oluştur** iletişim kutusu görüntülenir. Gerekirse Azure hesabınızla oturum açın, ardından varsayılan uygulama hizmeti ayarları alanları doldurur.

    ![App Service oluşturun](../deployment/media/quickstart-publish-settings-app-service-linux.png "Azure Uygulama Hizmeti Oluştur")

1. **Oluştur'u**seçin. Visual Studio uygulamayı Azure Uygulama Hizmetinize dağıtır ve web uygulaması tarayıcınızda yüklenir. Proje özellikleri **Yayımlama** bölmesi site NIN URL'sini ve diğer ayrıntıları gösterir.

    ![Profil özetini gösteren özellik bölmesi yayımlama](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Önceki adımlarda, bir kaynak grubunda Azure kaynakları oluşturdunuz. İleride bu kaynaklara ihtiyaç duymayacağınızı düşünüyorsanız kaynakları silmek için kaynak grubunu silebilirsiniz.
Azure portalında sol taraftaki menüden **Kaynak grupları**'nı seçin ve ardından **myResourceGroup** seçeneğini belirleyin.
Kaynak grubu sayfasındaki listede yer alan kaynakların silmek istediğiniz kaynaklar olduğundan emin olun.
**Sil**'i seçin, metin kutusuna **myResourceGroup** yazın ve ardından **Sil**'e tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, Visual Studio'nun Linux'ta App Service'e dağıtım için bir yayımlama profili oluşturmak için nasıl kullanılacağını öğrendiniz. Azure'u kullanarak Linux'ta yayımlama hakkında daha fazla bilgi isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Linux Uygulama Hizmeti](/azure/app-service/containers/app-service-linux-intro)
