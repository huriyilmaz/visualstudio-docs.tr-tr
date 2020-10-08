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
ms.openlocfilehash: 5881e1dfb1842e2a6d85efe73534f8db2e2f734e
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830740"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Visual Studio’yu kullanarak Azure App Service'e Web uygulaması yayımlama

ASP.NET, ASP.NET Core, Node.js ve .NET Core uygulamaları için aşağıdaki yöntemlerden birini kullanarak Azure App Service veya Azure App Service Linux (kapsayıcılar kullanarak) yayımlayın.

* Uygulamaların sürekli (veya otomatik) dağıtımı için [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true)Ile Azure DevOps kullanın.

* Uygulamaların tek seferlik (veya el ile) dağıtımı için, Visual Studio 'daki **Yayımla** aracını kullanarak [Linux için](../deployment/quickstart-deploy-to-linux.md) Azure App Service veya App Service (kapsayıcılar kullanarak) ASP.NET, ASP.NET Core, Node.js ve .NET Core uygulamaları dağıtın. Python uygulamaları için, [Azure App Service Python-Publish](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)üzerindeki adımları izleyin.

Bu makalede, tek seferlik dağıtım için **Yayımla** aracının nasıl kullanılacağı açıklanır.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Windows üzerinde Azure App Service yayımlayın

1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve **Yayımla** ' yı seçin (veya **Yapı**  >  **Yayımla** menü öğesini kullanın).

    ![Çözüm Gezgini içindeki proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla ' yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** penceresi görüntülenir. **Yeni**’yi seçin.

1. **Yayımla** penceresinde **Azure**' ı seçin.

    ![Yayımlama hedefini seçin](../deployment/media/quickstart-publish-azure-new.png)

1. **Azure App Service (Windows)** ve **İleri ' yi**seçin.

    ![Linux üzerinde Azure App Service seçin](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. Gerekirse Azure hesabınızla oturum açın. **Yeni Azure App Service oluştur ' u seçin...**

    ![Azure App Service yeni bir örneğini oluşturmak için bağlantı](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. **Azure App Service oluştur (Windows)** iletişim kutusunda, **uygulama adı**, **kaynak grubu**ve **App Service planı** giriş alanları doldurulur. Bu adları koruyabilir veya değiştirebilirsiniz. Hazırlanıyor, **Oluştur**' u seçin.

    ![Azure App Service seçin](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. **Yayımla** iletişim kutusunda yeni oluşturulan örnek otomatik olarak seçilmiştir. Hazırlanıyor, **son**' u seçin.

    ![Azure App Service seçin](../deployment/media/quickstart-publish-windows-select-instance.png)

1. **Yayımla**’yı seçin. Visual Studio uygulamayı Azure App Service dağıtır ve Web uygulaması tarayıcınıza yüklenir. Proje özellikleri **Yayımlama** bölmesi, site URL 'sini ve diğer ayrıntıları gösterir.

    ![Profil özetini gösteren özellik bölmesini Yayımla](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Önceki adımlarda, bir kaynak grubunda Azure kaynakları oluşturdunuz. İleride bu kaynaklara ihtiyaç duymayacağınızı düşünüyorsanız kaynakları silmek için kaynak grubunu silebilirsiniz.
Azure portalında sol taraftaki menüden **Kaynak grupları**'nı seçin ve ardından **myResourceGroup** seçeneğini belirleyin.
Kaynak grubu sayfasındaki listede yer alan kaynakların silmek istediğiniz kaynaklar olduğundan emin olun.
**Sil**'i seçin, metin kutusuna **myResourceGroup** yazın ve ardından **Sil**'e tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, Azure 'a dağıtım için bir yayımlama profili oluşturmak üzere Visual Studio 'Yu nasıl kullanacağınızı öğrendiniz. Ayrıca, Azure App Service yayımlama ayarlarını içeri aktararak bir yayımlama profili de yapılandırabilirsiniz.

> [!div class="nextstepaction"]
> [Yayımlama ayarlarını içeri aktarma ve Azure’a dağıtma](tutorial-import-publish-settings-azure.md)
