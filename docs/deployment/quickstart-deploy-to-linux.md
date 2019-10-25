---
title: Linux üzerinde App Service yayımlayın
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
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806865"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Visual Studio kullanarak Linux 'ta App Service için ASP.NET Core uygulaması yayımlama

Visual Studio 2017 sürüm 15,7 ' den başlayarak, aşağıdaki yöntemlerden birini kullanarak Linux Azure App Service Linux (kapsayıcılar kullanarak) ASP.NET Core uygulamalar yayımlayabilirsiniz.

* Uygulamaların sürekli (veya otomatik) dağıtımı için [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops)Ile Azure DevOps kullanın.

* Uygulamaların tek seferlik (veya el ile) dağıtımı için, Visual Studio 'daki **Yayımla** aracını kullanarak Linux için App Service ASP.NET Core uygulamalar yayımlayın (kapsayıcılar kullanarak).

Bu makalede, tek seferlik dağıtım için **Yayımla** aracının nasıl kullanılacağı açıklanır.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Linux üzerinde App Service yayımlayın

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla** ' yı seçin (veya **derleme** > **Yayımla** menü öğesini kullanın).

    ![Çözüm Gezgini içindeki proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla ' yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** bölmesi görüntülenir ve bu durumda **Yeni Profil oluştur**' u seçin.

1. **Bir yayımlama hedefi seç** Iletişim kutusunda **Linux App Service**seçin.

    ![Azure App Service seçin](../deployment/media/quickstart-publish-linux.png "Azure App Service seçin")

1. **Yayımla**' yı seçin. **App Service oluştur** iletişim kutusu görüntülenir. Gerekirse Azure hesabınızla oturum açın, ardından varsayılan App Service ayarları alanları doldurun.

    ![App Service oluştur](../deployment/media/quickstart-publish-settings-app-service-linux.png "Azure App Service oluştur")

1. **Oluştur**' u seçin. Visual Studio uygulamayı Azure App Service dağıtır ve Web uygulaması tarayıcınıza yüklenir. Proje özellikleri **Yayımlama** bölmesi, site URL 'sini ve diğer ayrıntıları gösterir.

    ![Profil özetini gösteren özellik bölmesini Yayımla](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Kaynakları Temizleme

Yukarıdaki adımlarda, bir kaynak grubunda Azure kaynakları oluşturdunuz. Gelecekte bu kaynaklara ihtiyaç duymazsanız, kaynak grubunu silerek bunları silebilirsiniz.
Azure portal sol menüden **kaynak grupları** ' nı seçin ve ardından **myresourcegroup**' ı seçin.
Kaynak grubu sayfasında, listelenen kaynakların silmek istedikleriniz olduğundan emin olun.
**Sil**' i seçin, metin kutusuna **myresourcegroup** yazın ve ardından **Sil**' i seçin.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, Linux üzerinde App Service dağıtım için bir yayımlama profili oluşturmak üzere Visual Studio 'Yu nasıl kullanacağınızı öğrendiniz. Azure kullanarak Linux 'a yayımlama hakkında daha fazla bilgi isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
