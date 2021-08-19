---
title: Azure App Service’e yayımlama
description: ASP.NET, ASP.NET Core, Node.js ve .NET Core uygulamalarını Linux'Azure App Service veya Azure App Service öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- azure
ms.openlocfilehash: 53c14db342e48ceccc7651220ac86c8bcacedcf3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146283"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Visual Studio’yu kullanarak Azure App Service'e Web uygulaması yayımlama

ASP.NET, ASP.NET Core, Node.js ve .NET Core uygulamaları için, aşağıdaki yöntemlerden birini kullanarak Azure App Service veya Azure App Service Linux'da yayımlayın (kapsayıcıları kullanarak).

* Uygulamaların sürekli (veya otomatik) dağıtımı için Azure DevOps ile [Azure Pipelines.](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true)

* Uygulamaların tek kullanımlık (veya el ile)  dağıtımı için, Linux için ASP.NET, ASP.NET Core, Node.js ve .NET Core uygulamalarını Linux için Azure App Service veya App Service'a dağıtmak üzere Visual Studio'daki [Yayımla](../deployment/quickstart-deploy-to-linux.md) aracını kullanın (kapsayıcıları kullanarak). Python uygulamaları için Python - Yayımlama ile [ilgili adımları Azure App Service.](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Bu makalede, tek kullanımlık dağıtım **için Yayımla** aracının nasıl kullanımı açıklanmıştır.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Azure App Service'da Windows

1. Bu Çözüm Gezgini proje düğümüne sağ tıklayın ve Yayımla'yı **seçin** (veya **Yayımla'yı**  >  **Derleme menü** öğesini kullanın).

    ![Çözüm Gezgini'de proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla'yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız **Yayımla** penceresi görüntülenir. **Yeni**'yi seçin.

1. Yayımla **penceresinde** **Azure'ı seçin.**

    ![Yayımlama hedefi seçme](../deployment/media/quickstart-publish-azure-new.png)

1. Azure App Service **(Windows) ve Ardından'ı** **seçin.**

    ![Yeni bir Linux üzerinde Azure App Service](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. Gerekirse Azure hesabınızla oturum açın. Yeni **bir dosya oluştur... Azure App Service**

    ![Yeni örnek oluşturma bağlantısı Azure App Service](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. Create **Azure App Service (Windows)** iletişim kutusunda Uygulama **Adı,** **Kaynak** Grubu ve **App Service Planı giriş** alanları doldurulur. Bu adları saklayarak veya değiştirebilirsiniz. Hazır olduğunda **Oluştur'a seçin.**

    ![Ad, Abonelik, Azure App Service Ve Barındırma Windows alanlarının doldurulmuş olduğu Create Azure App Service (Windows) iletişim kutusunun ekran görüntüsü.](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. Yayımla **iletişim** kutusunda, yeni oluşturulan örnek otomatik olarak seçilmiştir. Hazır olduğunda Son'a **seçin.**

    ![Visual Studio Çözüm Gezgini'dan erişilen Yayımla penceresinin ekran görüntüsü. Yayımlama hedefi olarak Azure seçilir.](../deployment/media/quickstart-publish-windows-select-instance.png)

1. **Yayımla**’yı seçin. Visual Studio uygulama uygulamanıza Azure App Service web uygulaması tarayıcınızda yüklenir. Proje özellikleri **Yayımla** bölmesinde site URL'si ve diğer ayrıntılar gösterilir.

    ![Profil özetini gösteren Özellik yayımlama bölmesi](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Önceki adımlarda, bir kaynak grubunda Azure kaynakları oluşturdunuz. İleride bu kaynaklara ihtiyaç duymayacağınızı düşünüyorsanız kaynakları silmek için kaynak grubunu silebilirsiniz.
Azure portalında sol taraftaki menüden **Kaynak grupları**'nı seçin ve ardından **myResourceGroup** seçeneğini belirleyin.
Kaynak grubu sayfasındaki listede yer alan kaynakların silmek istediğiniz kaynaklar olduğundan emin olun.
**Sil**'i seçin, metin kutusuna **myResourceGroup** yazın ve ardından **Sil**'e tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, Azure'a dağıtım Visual Studio yayımlama profili oluşturmak için Visual Studio kullanmayı öğrendiniz. Yayımlama ayarlarını bir yayımlama profilinden içeri aktararak da Azure App Service.

> [!div class="nextstepaction"]
> [Yayımlama ayarlarını içeri aktarma ve Azure’a dağıtma](tutorial-import-publish-settings-azure.md)
