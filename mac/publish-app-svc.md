---
title: Azure App Service’e yayımlama
description: Mac için Visual Studio'da yayımlama araçlarını kullanarak web uygulaması yayımlama.
ms.date: 04/02/2019
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
ms.openlocfilehash: 89ef1be831db8383a960d480ac8dceffa7e8f1460708c37e4764d9533876c2d9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121349458"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak web Azure App Service yayımlama

Yayımlama aracını kullanarak uygulamalarınızı ASP.NET Core yayım Azure App Service.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2019'un yüklü](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) olduğu mac için ASP.NET Core.
- Azure Aboneliği. Henüz bir aboneliğiniz [yoksa,](https://azure.microsoft.com/free/dotnet/)30 gün boyunca 200 ABD doları kredi ve popüler ücretsiz hizmetlerden 12 ay boyunca ücretsiz olarak kaydolabilirsiniz.
- Bir ASP.NET Core projesi. Henüz bir projeniz yoksa yeni bir [tane oluşturabilirsiniz.](~/create-new-projects.md)

## <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

 1. Çözüm Penceresinde projeye sağ tıklayın ve Yayımla'yı **seçin.**

    ![Yayımla bağlam menüsü](media/publish-context-menu.png)

 2. Daha önce bu projeyi Azure App Service yayımlamak için menüde yayımlama profilinin olduğunu görüyorsunuz. Yayımlama işlemini başlatmak için bu yayımlama profilini seçin.

 3. Bu projeyi ilk kez App Service için **Azure'da yayımla'yı seçin**

    ![App Service'da yayımla bağlam menüsü](media/publish-to-azure-context-menu.png)

 4. **Azure App Service'da** yayımla iletişim kutusu görüntülenir ve mevcut Tüm App Services gösterilir. Var olan bir App Service yayımlamak için, App Service'yi seçin ve ardından Yayımla'ya **tıklayın.**

    ![Bir Azure App Service yayımla iletişim kutusu](media/publish-to-app-service-dialog.png)

 5. Yeni bir App Service için Yeni **düğmesine** tıklayın.

    ![App Service'da Yayımla İletişim Kutusu](media/publish-to-app-service-dialog-new-selected.png)

 6. Yeni **App Service** iletişim kutusu görüntülenir. Bu iletişim kutusunda, yeni uygulamanıza App Service.

    ![Yeni App Service iletişim kutusu](media/publish-new-app-service.png)

    Burada özelleştirmeyi göz önünde bulundurabilirsiniz. Varsayılan olarak App Service proje adı kullanılır. Ad kullanılamıyorsa, giriş alanı sağ tarafında bir uyarı işareti görünür. Bu App Service web sitenizin URL'sinde kullanılacaktır, bu nedenle adın BIR URL'de kullanılacak şekilde geçerli olması gerekir.

    Abonelik açılan listesinden App Service ilişkilendirilecek aboneliği **değiştirebilirsiniz.**

    Açılan liste kullanarak var **olan bir** Kaynak Grubunu seçerek veya düğmeyle yeni bir tane **+** oluşturabilirsiniz.

    Yeni App Service mevcut planı seçin veya Özel radyo düğmesini seçerek yeni **bir tane** oluşturun.

    Yeni projenizi oluşturmak App Service projenizi yayımlamak için Oluştur'a **tıklayın.**

    Create  the **New App Service** (Yeni Uygulama Oluştur) iletişim kutusu görüntülenir ve aşağıdaki iletiyle App Service gerekir.

      ![İleti App Service Oluşturma](media/publish-create-app-service-message.png)

    **Tamam'a** tıklarsanız ileti çıkar ve projeniz üzerinde çalışmaya devam edersiniz. Yayımlama işleminin durumunu IDE'nin üst kısmında durum çubuğuyla izleyebilirsiniz. Web uygulaması başarıyla yayımlandıktan sonra site varsayılan tarayıcınızla açılır.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]
