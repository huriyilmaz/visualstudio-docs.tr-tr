---
title: Linux üzerinde App Service'da yayımlama
description: Kapsayıcıları kullanarak ASP.NET Core ve tek Azure App Service dahil olmak üzere Linux'a uygulama yayımlama yöntemleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- azure
ms.openlocfilehash: 7cb62fe0ac4725d035cb46e894ae10da70f0e541217254c81b2a649f4f571724
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418303"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Linux üzerinde App Service kullanarak ASP.NET Core Visual Studio

2017 Visual Studio 15.7 sürümünden başlayarak, ASP.NET Core uygulamalarını aşağıdaki yöntemlerden birini kullanarak Azure App Service Linux'ta (kapsayıcıları kullanarak) yayımlayın.

* Uygulamaların sürekli (veya otomatik) dağıtımı için Azure DevOps ile [Azure Pipelines.](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true)

* Uygulamaların tek kullanımlık (veya el ile)  dağıtımı için Visual Studio'daki Yayımla aracını kullanarak Linux ASP.NET Core 'de App Service uygulamaları yayımlayın (kapsayıcıları kullanarak).

Bu makalede, tek kullanımlık dağıtım **için Yayımla** aracının nasıl kullanımı açıklanmıştır.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>Linux üzerinde Azure App Service'de yayımlama

1. Bu Çözüm Gezgini projeye sağ tıklayın ve Yayımla'yı **seçin** (veya Yayımla **menü**  >  **öğesini** kullanın).

    ![Çözüm Gezgini'de proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla'yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız **Yayımla** penceresi görüntülenir. **Yeni**'yi seçin.

1. Yayımla **penceresinde** **Azure'ı seçin.**

    ![Yayımlama hedefi seçme](../deployment/media/quickstart-publish-azure-new.png)

1. Azure App Service **(Linux) ve Sonraki'yi** **seçin.**

    ![Yeni bir Linux üzerinde Azure App Service](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. Gerekirse Azure hesabınızla oturum açın. Yeni **bir dosya oluştur... Azure App Service**

    ![Yeni örnek oluşturma bağlantısı Azure App Service](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. Azure App Service **(Linux)** iletişim kutusunda Uygulama **Adı,** **Kaynak Grubu** ve App Service **Planı giriş** alanları doldurulur. Bu adları saklayarak veya değiştirebilirsiniz. Hazır olduğunda **Oluştur'a seçin.**

    ![Ad, Abonelik, Kaynak Azure App Service ve Barındırma Planı alanlarının doldurulmasıyla Birlikte Yeni Kaynak Oluştur (Linux) iletişim kutusunun ekran görüntüsü.](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. Yayımla **iletişim** kutusunda, yeni oluşturulan örnek otomatik olarak seçilmiştir. Hazır olduğunda Son'a **tıklayın.**

    ![Yayımlama için yeni oluşturulan MyASpCoreWebAppOnAzure hizmetinin yayımlanabilecek hizmet olarak seç App Service ekran görüntüsü.](../deployment/media/quickstart-publish-linux-select-instance.png)

1. **Yayımla**’yı seçin. Visual Studio uygulama uygulamanıza Azure App Service web uygulaması tarayıcınızda yüklenir. Proje özellikleri **Yayımla** bölmesinde site URL'si ve diğer ayrıntılar gösterilir.

    ![Profil özetini gösteren Özellik yayımlama bölmesi](../deployment/media/quickstart-publish-linux-summary-page.png)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Önceki adımlarda, bir kaynak grubunda Azure kaynakları oluşturdunuz. İleride bu kaynaklara ihtiyaç duymayacağınızı düşünüyorsanız kaynakları silmek için kaynak grubunu silebilirsiniz.
Azure portalında sol taraftaki menüden **Kaynak grupları**'nı seçin ve ardından **myResourceGroup** seçeneğini belirleyin.
Kaynak grubu sayfasındaki listede yer alan kaynakların silmek istediğiniz kaynaklar olduğundan emin olun.
**Sil**'i seçin, metin kutusuna **myResourceGroup** yazın ve ardından **Sil**'e tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, Visual Studio'a dağıtım için yayımlama profili oluşturmak üzere Linux üzerinde App Service. Azure kullanarak Linux'ta yayımlama hakkında daha fazla bilgi almak istiyor olabilir.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)