---
title: Azure App Service’e yayımlama
ms.date: 01/17/2019
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.custom: video
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: daebef8fdaa2d22fd5eef7171113354136d29e0f
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861107"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak Azure App Service bir Web uygulaması yayımlama

Azure App Service için ASP.NET Core uygulamaları yayımlamak üzere Yayımla aracını kullanabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

- ASP.NET Core etkinken [Mac Için Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) yüklendi.
- Bir Azure aboneliği. Henüz bir aboneliğiniz yoksa [ücretsiz kaydolun](https://azure.microsoft.com/free/dotnet/)ve 30 gün boyunca kredi olarak $200, popüler ücretsiz hizmet için 12 ay.
- Bir ASP.NET Core projesi. Zaten bir projeniz yoksa [Yeni bir tane oluşturabilirsiniz](./create-new-projects.md?view=vsmac-2017).

## <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

 1. Çözüm Bölmesi projeye sağ tıklayın ve **Yayımla**' yı seçin.

    ![Yayımla bağlam menüsü](media/publish-context-menu.png)

 2. Bu projeyi daha önce Azure App Service yayımladıysanız, menüden Yayımla profilini görürsünüz. Yayımlama işlemini başlatmak için bu profili Yayımla ' yı seçin.

 3. Bu projeyi ilk kez App Service yayımlamak için **Azure 'Da Yayımla** ' yı seçin.

    ![App Service bağlam menüsünde Yayımla](media/publish-to-azure-context-menu.png)

 4. **Azure App Service Yayımla** iletişim kutusu görünür ve var olan tüm uygulama hizmetleri gösterilir. Mevcut bir App Service yayımlamak için, listeden App Service seçin ve ardından **Yayımla**' ya tıklayın.

    ![Azure App Service 'de Yayımla iletişim kutusu](media/publish-to-app-service-dialog.png)

 5. Yeni bir App Service oluşturmak için **Yeni** düğmesine tıklayın.

    ![App Service 'de Yayımla Iletişim kutusu](media/publish-to-app-service-dialog-new-selected.png)

 6. **Yeni App Service** iletişim kutusu görüntülenir. Bu iletişim kutusunda, yeni App Service ayarlarını yapılandırabilirsiniz.

    ![Yeni App Service iletişim kutusu](media/publish-new-app-service.png)

    Burada özelleştirmeyi göz önünde bulundurmanız gereken birkaç seçenek vardır. App Service adı, varsayılan olarak proje adı olacaktır. Ad yoksa, giriş alanının sağ tarafında bir uyarı işareti görüntülenir. App Service adı, Web sitenizin URL 'sinde kullanılır, bu nedenle ad bir URL 'de kullanılmak üzere geçerli olmalıdır.

    App Service **abonelik açılan listesini** kullanarak ilişkilendirilecektir.

    Açılır menüyü kullanarak var olan bir **kaynak grubunu** seçebilirsiniz veya düğmeyle yeni bir tane oluşturabilirsiniz **+** .

    App Service planı için, var olan bir seçim seçin veya **özel** radyo düğmesini seçerek yeni bir tane oluşturun.

    Yeni App Service oluşturup projenizi yayımlamak için **Oluştur**' a tıklayın.

    **Oluştur** ' a tıkladıktan sonra **Yeni App Service** iletişim kutusu kapatılır ve App Service oluşturmanın başlatıldığını belirten aşağıdaki iletiyi görmeniz gerekir.

      ![App Service Iletisi oluştur](media/publish-create-app-service-message.png)

    **Tamam** ' a tıkladıktan sonra ileti kapatılır ve projenizde çalışmaya devam edebilirsiniz. Yayımla işleminin durumunu IDE 'nin en üstündeki durum çubuğuyla izleyebilirsiniz. Web uygulamanız başarıyla yayımlandıktan sonra, site varsayılan tarayıcınızla açılır.

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]