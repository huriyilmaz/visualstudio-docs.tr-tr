---
title: Yerel klasöre dağıtma
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 800059dc8d5a3e6ccfb72c588fbb61423a338cba
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036398"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Visual Studio 'Yu kullanarak bir klasöre uygulama dağıtma

**Yayımla** aracını, Visual Studio 'daki bir klasöre ASP.NET, ASP.NET Core, .NET Core ve Python uygulamaları yayımlamak için kullanabilirsiniz. Node.js, adımlar desteklenir, ancak kullanıcı arabirimi farklıdır.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Bir Windows masaüstü uygulamasını bir klasöre yayımlamanız gerekiyorsa bkz. [ClickOnce kullanarak masaüstü uygulaması dağıtma](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# veya Visual Basic). C++/CLR için bkz. [ClickOnce kullanarak yerel uygulama dağıtma](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) veya C/C++ için bkz. [Kurulum projesi kullanarak yerel uygulama dağıtma](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Yerel klasöre dağıtma

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla** ' yı seçin (veya **Yapı**  >  **Yayımla** menü öğesini kullanın).

    ![Çözüm Gezgini içindeki proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla ' yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** penceresi görüntülenir. **Yeni**’yi seçin.

1. **Yayımla** penceresinde **klasör**' ü seçin.

    ![Yayımla hedefi olarak klasör seçin](../deployment/media/quickstart-publish-folder-new.png "Klasör Seç")

1. Bir yol girin veya bir klasör belirtmek için **Araştır** ' ı seçin.

    ![Klasörün yolunu belirtin](../deployment/media/quickstart-publish-folder-path.png "Klasör Seç")

1. **Yayımla**’yı seçin. Visual Studio projeyi oluşturur ve belirtilen klasöre yayımlar. Bir profil Özeti gösteren proje özellikleri **Yayımla** bölmesi görüntülenir.

    ![Profil özetini gösteren özellik bölmesini Yayımla](../deployment/media/quickstart-publish-folder-summary.png)

1. Dağıtım ayarlarını yapılandırmak için, yayımlama profili özetinde **Düzenle** ' yi seçin ve **Ayarlar** sekmesini seçin.

   Gördüğünüz ayarlar uygulama türüne bağlıdır. Aşağıdaki çizimde bir ASP.NET Core uygulamasının örnek ayarları gösterilmektedir.

    ![Profil ayarları](../deployment/media/quickstart-profile-settings.png "Profil ayarları")

    .NET ' te ayarları seçmek için ek yardım için aşağıdakilere bakın:

    - [Çerçeveye bağımlı ve kendinden bağımsız dağıtım](/dotnet/core/deploying/)
    - [Hedef çalışma zamanı tanımlayıcıları (taşınabilir RID, et)](/dotnet/core/rid-catalog)
    - [Hata ayıklama ve sürüm yapılandırması](../ide/understanding-build-configurations.md)

1. Bir hata ayıklama veya sürüm yapılandırması dağıtıp dağıtmayacağı gibi seçenekleri yapılandırın ve ardından **Kaydet**' i seçin.

1. Yeniden yayımlamak için **Yayımla**' yı seçin.

Yayınlanan dosyaları dilediğiniz gibi dağıtın. Örneğin, bunları bir *. zip* dosyasında paketleyebilir, basit bir kopyalama komutu kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

.NET uygulamaları için:

- [Yayımla aracıyla .NET Core uygulaması dağıtma](/dotnet/core/deploying/deploy-with-vs)
- [.NET Core uygulaması yayımlama (çerçeveye bağlı ve kendinden bağımsız dağıtımlar)](/dotnet/core/deploying/)
- [.NET Framework ve uygulamaları dağıtma](/dotnet/framework/deployment/)
