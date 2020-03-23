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
ms.openlocfilehash: 862310c8c763ce366798bfacd4f4759d606bb33c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128205"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Visual Studio'u kullanarak uygulamayı yerel bir klasöre dağıtma

ASP.NET, ASP.NET Core, .NET Core ve Python uygulamalarını Visual Studio'dan yerel bir klasöre yayımlamak için **Yayımla** aracını kullanabilirsiniz. Node.js için adımlar desteklenir, ancak kullanıcı arabirimi farklıdır.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Bir Windows masaüstü uygulamasını yerel bir klasörde yayımlamanız gerekiyorsa, ClickOnce (C# veya Visual Basic) [kullanarak bir masaüstü uygulamasını dağıt'a](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) bakın. C++/CLI için [ClickOnce kullanarak yerel bir uygulama dağıt'a](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) bakın veya C/C++ için Kurulum projesini kullanarak yerel bir uygulamayı [dağıt'a](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)bakın.

## <a name="deploy-to-a-local-folder"></a>Yerel klasöre dağıtma

1. Çözüm Gezgini'nde projeyi sağ tıklatın ve **Yayımla'yı** seçin (veya **Yapı** > **Yayımla** menüsü öğesini kullanın).

    ![Çözüm Gezgini'nde proje bağlamı menüsünde Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla'yı Seçin")

1. Yayımlama profillerini daha önce yapılandırmışsanız, **Yayımla** bölmesi görüntülenir. **Yeni profil oluştur'u**seçin.

1. **Yayımlama hedef** iletişim kutusunda **Klasör'ü**seçin.

    ![Yayımlama hedefi olarak yerel klasörü seçin](../deployment/media/quickstart-publish-folder.png "Klasör Seçin")

1. Bir yol girin veya yerel bir klasör belirtmek için **Gözat'ı** seçin.

1. **Yayımla**’yı seçin. Visual Studio projeyi oluşturur ve belirtilen klasöre yayınlar. Proje özellikleri Profil özetini gösteren **Yayımlama** bölmesi görüntülenir.

    ![Profil özetini gösteren özellik bölmesi yayımlama](../deployment/media/quickstart-publish-folder-summary.png)

1. Dağıtım ayarlarını yapılandırmak için profil özetinde **Yapılandır'ı** seçin ve **Ayarlar** sekmesini seçin.

    ![Profil ayarları](../deployment/media/quickstart-profile-settings.png "Profil ayarları")

1. Hata Ayıklama veya Sürüm yapılandırmasını dağıtıp dağıtmamak gibi seçenekleri yapılandırın ve ardından **Kaydet'i**seçin.

1. Yeniden yayımlamak için **Yayımla'yı**seçin.

Yayımlanmış dosyaları istediğiniz şekilde dağıtın. Örneğin, bunları bir *.zip* dosyasında paketleyebilir, basit bir kopyalama komutu kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [Yayımlama aracıyla bir .NET Çekirdek Uygulaması dağıtma](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Bir masaüstü uygulamasını Microsoft Store için paketleme (Masaüstü Köprüsü)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [.NET Çerçevesini ve uygulamalarını dağıtma](/dotnet/framework/deployment/)
