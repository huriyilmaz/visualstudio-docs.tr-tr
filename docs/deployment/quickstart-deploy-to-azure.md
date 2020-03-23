---
title: Azure App Service’e yayımlama
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 4bbff0c2d149afddc355afe5f6c93e9d0aea54c0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806904"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Visual Studio’yu kullanarak Azure App Service'e Web uygulaması yayımlama

ASP.NET için, ASP.NET Core, Node.js ve .NET Core uygulamaları için aşağıdaki yöntemlerden birini kullanarak Azure Uygulama Hizmeti veya Azure Uygulama Hizmeti Linux'ta (kapsayıcılar kullanarak) yayımlayın.

* Uygulamaların sürekli (veya otomatik) dağıtımı için [Azure Ardışık Hatları](/azure/devops/pipelines/get-started-yaml?view=azdevops)ile Azure DevOps'leri kullanın.

* Uygulamaların tek seferlik (veya manuel) dağıtımı için Visual Studio'da **yayımlama** aracını kullanarak ASP.NET, ASP.NET Core, Node.js ve .NET Core uygulamalarını Azure Uygulama Hizmeti'ne veya Linux için Uygulama Hizmetine (kapsayıcıları kullanarak) dağıtın. Python uygulamaları için Python [- Azure Uygulama Hizmeti'nde yayımla](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)' daki adımları izleyin.

Bu makalede, **yayımlama** aracının tek seferlik dağıtım için nasıl kullanılacağı açıklanmaktadır.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

1. Çözüm Gezgini'nde projeyi sağ tıklatın ve **Yayımla'yı** seçin (veya **Yapı** > **Yayımla** menüsü öğesini kullanın).

    ![Çözüm Gezgini'nde proje bağlamı menüsünde Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla'yı Seçin")

1. Daha önce yayımlama profillerini yapılandırmışsanız, **Yayımla** bölmesi görüntülenir ve bu durumda **yeni profil oluştur'u**seçin.

1. **Yayımlama hedef** iletişim kutusunu seç'te, **Uygulama Hizmeti'ni**seçin.

    ![Azure Uygulama Hizmeti'ni seçin](../deployment/media/quickstart-publish-azure.png "Azure Uygulama Hizmeti'ni seçin")

1. **Yayımla**’yı seçin. **Uygulama Hizmeti Oluştur** iletişim kutusu görüntülenir. Gerekirse Azure hesabınızla oturum açın, ardından varsayılan uygulama hizmeti ayarları alanları doldurur.

    ![App Service oluşturun](../deployment/media/quickstart-publish-settings-app-service.png "Azure Uygulama Hizmeti Oluştur")

1. **Oluştur'u**seçin. Visual Studio uygulamayı Azure Uygulama Hizmetinize dağıtır ve web uygulaması tarayıcınızda yüklenir. Proje özellikleri **Yayımlama** bölmesi site NIN URL'sini ve diğer ayrıntıları gösterir.

    ![Profil özetini gösteren özellik bölmesi yayımlama](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Önceki adımlarda, bir kaynak grubunda Azure kaynakları oluşturdunuz. İleride bu kaynaklara ihtiyaç duymayacağınızı düşünüyorsanız kaynakları silmek için kaynak grubunu silebilirsiniz.
Azure portalında sol taraftaki menüden **Kaynak grupları**'nı seçin ve ardından **myResourceGroup** seçeneğini belirleyin.
Kaynak grubu sayfasındaki listede yer alan kaynakların silmek istediğiniz kaynaklar olduğundan emin olun.
**Sil**'i seçin, metin kutusuna **myResourceGroup** yazın ve ardından **Sil**'e tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, Azure'a dağıtım için bir yayımlama profili oluşturmak için Visual Studio'nun nasıl kullanılacağını öğrendiniz. Yayımlama ayarlarını Azure Uygulama Hizmeti'nden içe aktararak bir yayımlama profilini de yapılandırabilirsiniz.

> [!div class="nextstepaction"]
> [Yayımlama ayarlarını içeri aktarma ve Azure’a dağıtma](tutorial-import-publish-settings-azure.md)
