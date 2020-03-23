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
ms.workload:
- azure
ms.openlocfilehash: 97964589b832b05f4d528a801a1899eeb8385883
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714466"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Mac için Visual Studio'u kullanarak Azure Uygulama Hizmeti'ne web uygulaması yayınlama

Azure Uygulama Hizmeti'ne ASP.NET Çekirdek uygulamalarını yayınlamak için Yayımla aracını kullanabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 Mac için](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) ASP.NET Core özellikli yüklü.
- Azure Aboneliği. Zaten bir aboneliğiniz yoksa, 30 gün ve 12 aylık popüler ücretsiz hizmetler için 200 $ kredi içeren ücretsiz olarak [kaydolun.](https://azure.microsoft.com/free/dotnet/)
- Bir ASP.NET Core projesi. Zaten bir projeniz yoksa, yeni [bir](/visualstudio/mac/create-new-projects?view=vsmac-2017)proje oluşturabilirsiniz.

## <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

 1. Çözüm Defteri'nde projeyi sağ tıklatın ve **Yayımla'yı**seçin.

    ![Bağlam menüsünü yayımla](media/publish-context-menu.png)

 2. Bu projeyi daha önce Azure Uygulama Hizmeti'nde yayımladıysanız, menüde yayımlama profilini görürsünüz. Yayımlama işlemini başlatmak için yayımlama profilini seçin.

 3. Bu projeyi ilk kez Uygulama Hizmeti'nde yayımlamak için **Azure'a Yayımla'yı** seçin

    ![Uygulama Hizmeti bağlam menüsünde yayımla](media/publish-to-azure-context-menu.png)

 4. **Azure Uygulama Hizmetine Yayımla** iletişim kutusu görüntülenir ve varolan Tüm Uygulama Hizmetleri gösterilir. Varolan bir Uygulama Hizmetinde yayımlamak için, listedeki Uygulama Hizmeti'ni seçin ve ardından **Yayımla'yı**tıklatın.

    ![Azure Uygulama Hizmeti iletişim kutusunda yayımlama](media/publish-to-app-service-dialog.png)

 5. Yeni bir Uygulama Hizmeti oluşturmak için **Yeni** düğmesini tıklatın.

    ![Uygulama Hizmeti İletişim Kutusu'nda yayımla](media/publish-to-app-service-dialog-new-selected.png)

 6. **Yeni Uygulama Hizmeti** iletişim kutusu görüntülenir. Bu iletişim kutusunda, yeni Uygulama Hizmetinizin ayarlarını yapılandırabilirsiniz.

    ![Yeni Uygulama Hizmeti iletişim kutusu](media/publish-new-app-service.png)

    Burada özelleştirmeyi göz önünde bulundurmak için birkaç seçenek vardır. Uygulama Hizmeti'nin adı varsayılan olarak proje adı için kullanılacaktır. Ad kullanılamıyorsa, giriş alanının sağ tarafında bir uyarı işareti görüntülenir. Uygulama Hizmetinin adı web sitenizin URL'sinde kullanılacaktır, bu nedenle bir URL'de kullanılmak üzere adın geçerli olması gerekir.

    App Service'in **Abonelik** açılır düşüşünü kullanarak ilişkili olacağı aboneliği değiştirebilirsiniz.

    Açılır dosyayı kullanarak varolan bir **Kaynak Grubu'nu** seçebilir **+** veya düğmeyle yeni bir Kaynak Grubu oluşturabilirsiniz.

    Uygulama Hizmeti planı için varolan bir tane seçin veya **Özel** radyo düğmesini seçerek yeni bir tane oluşturun.

    Yeni Uygulama Hizmetinizi oluşturmak ve projenizi bu şekilde yayınlamak için **Oluştur'u**tıklatın.

    **Yeni Uygulama Hizmeti** **Oluştur** iletişim kutusunu tıklattıktan sonra kapatılır ve Uygulama Hizmeti oluşturmanın başladığını belirten aşağıdaki iletiyi görmeniz gerekir.

      ![Uygulama Hizmeti İletisi Oluştur](media/publish-create-app-service-message.png)

    **Tamam'ı** tıklattıktan sonra ileti kapatılır ve projeniz üzerinde çalışmaya devam edebilirsiniz. IDE'nin üst kısmındaki durum çubuğuyla yayımlama işleminin durumunu izleyebilirsiniz. Web uygulamanız başarıyla yayımlandıktan sonra, varsayılan tarayıcınızla site açılır.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]
