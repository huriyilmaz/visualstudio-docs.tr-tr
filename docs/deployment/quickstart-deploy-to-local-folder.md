---
title: Yerel klasöre dağıtma
description: Yayımlama aracını kullanarak ASP.NET, ASP.NET Core, .NET Core ve Python uygulamalarını Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 9b74a5e7c8153b7896d5ee59f2284baaa8b11d31
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146270"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Visual Studio kullanarak bir uygulamayı klasöre Visual Studio

Yayımlama aracını kullanarak **ASP.NET,** ASP.NET Core, .NET Core ve Python uygulamalarını Visual Studio. Daha Node.js adımlar destekleniyor ancak kullanıcı arabirimi farklıdır.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]
::: moniker range=">=vs-2017"
> [!NOTE]
> Bir klasöre bir Windows masaüstü uygulaması yayımlamanız [](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) gerekirse bkz. ClickOnce (C# veya Visual Basic) kullanarak masaüstü uygulaması dağıtma. C++/CLR için bkz. [ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) kullanarak yerel uygulama dağıtma veya C/C++ için bkz. Kurulum projesi kullanarak [yerel uygulama dağıtma.](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)

::: moniker-end

::: moniker range=">=vs-2019"
> [!NOTE]
> Bir .NET Core 3.1 veya daha yeni bir sürümü, Windows masaüstü uygulamasını bir klasöre yayımlamanız gerekirse, bkz. ClickOnce kullanarak [.NET Windows uygulaması dağıtma.](quickstart-deploy-using-clickonce-folder.md)

::: moniker-end

## <a name="deploy-to-a-local-folder"></a>Yerel klasöre dağıtma

1. Bu Çözüm Gezgini projeye sağ tıklayın ve Yayımla'yı **seçin** (veya Yayımla **menü**  >  **öğesini** kullanın).

    ![Çözüm Gezgini'de proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla'yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız **Yayımla** penceresi görüntülenir. **Yeni**'yi seçin.

1. Yayımla **penceresinde** Klasör'e **tıklayın.**

   ![Yayımlama hedefi olarak klasör seçme](../deployment/media/quickstart-publish-folder-new.png "Klasör Seç")

   ::: moniker range=">=vs-2019"

   Bir .NET Core 3.1 veya daha yeni bir sürümü dağıtıyorsanız  Windows Uygulama'ya Özel hedef penceresinde **Klasör'ü seçmeniz** gerekir.

   ![Klasörü belirli bir hedef olarak seçme](../deployment/media/quickstart-publish-folder-targets.png "Belirli Bir Hedef Seçin")

   ClickOnce ile bir .NET Core 3.1 veya daha yeni bir Windows uygulaması yayımlamak isterseniz bkz. ClickOnce kullanarak [.NET Windows uygulaması dağıtma.](quickstart-deploy-using-clickonce-folder.md)
   ::: moniker-end

1. Bir yol girin veya **Gözat'ı** seçerek bir klasör belirtin.

   ![Klasörün yolunu belirtme](../deployment/media/quickstart-publish-folder-path.png "Klasör Seç")

   ::: moniker range=">=vs-2019"
   Profili **kaydetmek** için Son'a tıklayın.

   ![Profil özetini gösteren Özellik yayımlama bölmesi](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. **Yayımla**’yı seçin. Visual Studio projeyi oluşturur ve belirtilen klasöre yayımlar.

   ::: moniker range="vs-2017"
   Profil özetini **gösteren** Proje özellikleri Yayımla bölmesi görüntülenir.

   ![Profil özetini gösteren Özellik yayımlama bölmesi](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. Dağıtım ayarlarını yapılandırmak için yayımlama **profili özetini** Düzenle'yi seçin ve **Ayarlar** seçin.

   Gördüğünüz ayarlar uygulama türünüze bağlıdır. Aşağıdaki çizimde, bir uygulamanın ASP.NET Core gösterilmiştir.

    ![Profil ayarları](../deployment/media/quickstart-profile-settings.png "Profil ayarları")

    .NET'te ayarları seçmeye yardımcı olmak için aşağıdakilere bakın:

    - [Çerçeveye bağımlı ve kendi içinde dağıtım karşılaştırması](/dotnet/core/deploying/)
    - [Hedef çalışma zamanı tanımlayıcıları (taşınabilir RID, ve diğer)](/dotnet/core/rid-catalog)
    - [Hata ayıklama ve sürüm yapılandırmaları](../ide/understanding-build-configurations.md)

1. Hata Ayıklama veya Sürüm yapılandırması dağıtma gibi seçenekleri yapılandırıp Kaydet'i **seçin.**

1. Yeniden yayımlamak için Yayımla'yı **seçin.**

Yayımlanan dosyaları, herhangi bir şekilde dağıtın. Örneğin, bunları bir.zip dosyası içinde paketleyebilirsiniz, basit bir kopyalama komutu kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

.NET uygulamaları için:

- [Yayımla aracıyla bir .NET Core Uygulaması dağıtma](/dotnet/core/deploying/deploy-with-vs)
- [.NET Core uygulama yayımlama (çerçeveye bağımlı ve kendi içinde dağıtımlar)](/dotnet/core/deploying/)
- [Uygulama ve .NET Framework dağıtma](/dotnet/framework/deployment/)
::: moniker range=">=vs-2019"
- [ClickOnce kullanarak bir .NET Windows uygulaması ClickOnce.](quickstart-deploy-using-clickonce-folder.md)
 ::: moniker-end
