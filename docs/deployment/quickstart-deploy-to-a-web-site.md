---
title: Bir web sitesinde yayınlama
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1236c3057cd209bd5c7c81304a2168704927c506
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71127931"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Visual Studio'u kullanarak bir web sitesinde Web uygulaması yayınlama

ASP.NET, ASP.NET Core, .NET Core ve Python uygulamalarını Visual Studio'daki bir web sitesinde yayınlamak için **Yayımla** aracını kullanabilirsiniz. Node.js için adımlar desteklenir, ancak kullanıcı arabirimi farklıdır.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Bir Windows masaüstü uygulamasını ağ dosyası paylaşımında yayımlamanız gerekiyorsa, ClickOnce (C# veya Visual Basic) [kullanarak bir masaüstü uygulamasını dağıt'a](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) bakın. C++/CLI için [ClickOnce kullanarak yerel bir uygulama dağıt'a](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) bakın veya C/C++ için Kurulum projesini kullanarak yerel bir uygulamayı [dağıt'a](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)bakın.

## <a name="publish-to-a-web-site"></a>Bir Web sitesinde yayımlama

1. Çözüm Gezgini'nde projeyi sağ tıklatın ve **Yayımla'yı** seçin (veya **Yapı** > **Yayımla** menüsü öğesini kullanın).

    ![Çözüm Gezgini'nde proje bağlamı menüsünde Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla'yı Seçin")

1. Yayımlama profillerini daha önce yapılandırmışsanız, **Yayımla** bölmesi görüntülenir. **Yeni profil oluştur'u**seçin.

1. Bir **yayımlama hedef** iletişim kutusunu seç, **IIS, FTP, vb**seçin.

    ![IIS, FTP, vb seçin.](../deployment/media/quickstart-publish-iis-ftp.png "IIS, FTP, vb seçin.")

1. **Yayımla**’yı seçin. Profil yayımlama ayarları iletişim kutusu açılır.

    ![Klasör Seçin](../deployment/media/quickstart-publish-settings-web.png "Klasör Seçin")

1. **Yayımla yöntemi** alanında, **Web Dağıtımı** veya **FTP**gibi bir yöntem seçin. Bir sonraki gördüğünüz ayarlar yayımlama yönteminize karşılık gelir. Web Dağıtımı, Web uygulamalarının ve Web sitelerinin IIS sunucularına dağıtımını kolaylaştırır ve sunucuya bir uygulama olarak yüklenmesi gerekir. Yüklemek için [Web platformu yükleyicisini](https://www.microsoft.com/web/downloads/platform.aspx) kullanın.

1. Yayımlama yöntemi için gerekli ayarları yapılandırın ve **Bağlantıyı Doğrula'yı**seçin. Sunucu veya hedef kullanılabilirse ve ayarlarınız doğruysa, bağlantıyı belirten bir ileti doğrulanır ve yayımlamaya hazırsınız.

    ![Bağlantınızı doğrulayın](../deployment/media/quickstart-publish-web-deploy.png "Bağlantınızı doğrulayın")

1. Hata Ayıklama veya Sürüm yapılandırması dağıtmak gibi diğer dağıtım ayarlarını yapılandırmak için **Ayarlar'ı** seçin ve ardından **Kaydet'i**seçin. Uzaktan hata ayıklama alıyorsanız, hata ayıklama yapılandırması gereklidir.

1. Yayımlamak için **Yayımla'yı**seçin. Çıktı penceresi dağıtım ilerlemesini ve sonuçlarını gösterir.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, bir yayımlama profili oluşturmak için Visual Studio'nun nasıl kullanılacağını öğrendiniz. Yayımlama ayarlarını içe aktararak yayımlama profilini de yapılandırabilirsiniz.

> [!div class="nextstepaction"]
> [Yayımlama ayarlarını içeri aktarma ve IIS’ye dağıtma](tutorial-import-publish-settings-iis.md)
