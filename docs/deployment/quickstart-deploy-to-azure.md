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
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806904"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Visual Studio 'Yu kullanarak Azure App Service Web uygulaması yayımlama

ASP.NET, ASP.NET Core, Node. js ve .NET Core uygulamaları için aşağıdaki yöntemlerden birini kullanarak Azure App Service veya Azure App Service Linux (kapsayıcılar kullanarak) yayımlayın.

* Uygulamaların sürekli (veya otomatik) dağıtımı için [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops)Ile Azure DevOps kullanın.

* Uygulamaların tek seferlik (veya el ile) dağıtımı için, ASP.NET, ASP.NET Core, Node. js ve .NET Core uygulamalarını Linux için Azure App Service veya App Service dağıtmak üzere Visual Studio 'daki **Yayımla** aracını kullanın (kapsayıcılar kullanarak). Python uygulamaları için, [Azure App Service Python-Publish](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)üzerindeki adımları izleyin.

Bu makalede, tek seferlik dağıtım için **Yayımla** aracının nasıl kullanılacağı açıklanır.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla** ' yı seçin (veya **derleme** > **Yayımla** menü öğesini kullanın).

    ![Çözüm Gezgini içindeki proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla ' yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** bölmesi görüntülenir ve bu durumda **Yeni Profil oluştur**' u seçin.

1. **Bir yayımlama hedefi seç** iletişim kutusunda **App Service**' yi seçin.

    ![Azure App Service seçin](../deployment/media/quickstart-publish-azure.png "Azure App Service seçin")

1. **Yayımla**' yı seçin. **App Service oluştur** iletişim kutusu görüntülenir. Gerekirse Azure hesabınızla oturum açın, ardından varsayılan App Service ayarları alanları doldurun.

    ![App Service oluştur](../deployment/media/quickstart-publish-settings-app-service.png "Azure App Service oluştur")

1. **Oluştur**' u seçin. Visual Studio uygulamayı Azure App Service dağıtır ve Web uygulaması tarayıcınıza yüklenir. Proje özellikleri **Yayımlama** bölmesi, site URL 'sini ve diğer ayrıntıları gösterir.

    ![Profil özetini gösteren özellik bölmesini Yayımla](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Kaynakları Temizleme

Yukarıdaki adımlarda, bir kaynak grubunda Azure kaynakları oluşturdunuz. Gelecekte bu kaynaklara ihtiyaç duymazsanız, kaynak grubunu silerek bunları silebilirsiniz.
Azure portal sol menüden **kaynak grupları** ' nı seçin ve ardından **myresourcegroup**' ı seçin.
Kaynak grubu sayfasında, listelenen kaynakların silmek istedikleriniz olduğundan emin olun.
**Sil**' i seçin, metin kutusuna **myresourcegroup** yazın ve ardından **Sil**' i seçin.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, Azure 'a dağıtım için bir yayımlama profili oluşturmak üzere Visual Studio 'Yu nasıl kullanacağınızı öğrendiniz. Ayrıca, Azure App Service yayımlama ayarlarını içeri aktararak bir yayımlama profili de yapılandırabilirsiniz.

> [!div class="nextstepaction"]
> [Yayımlama ayarlarını içeri aktarma ve Azure’a dağıtma](tutorial-import-publish-settings-azure.md)
