---
title: Yerel klasöre dağıtma
description: yayımla aracını kullanarak Visual Studio bir klasöre ASP.NET, ASP.NET Core, .net Core ve Python uygulamaları nasıl yayımlayacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/23/2021
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
ms.openlocfilehash: c3df338150c4cf4f72aec310084c32f3db16bcd8
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429075"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Visual Studio kullanarak bir uygulamayı bir klasöre dağıtma

**yayımla** aracını, Visual Studio bir klasöre ASP.NET, ASP.NET Core, .net Core ve Python uygulamaları yayımlamak için kullanabilirsiniz. Node.js, adımlar desteklenir, ancak kullanıcı arabirimi farklıdır.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]
::: moniker range=">=vs-2017"
> [!NOTE]
> bir klasöre Windows masaüstü uygulaması yayımlamanız gerekiyorsa, bkz. [ClickOnce kullanarak .net Windows masaüstü uygulaması dağıtma](quickstart-deploy-using-clickonce-folder.md), [Windows kullanarak bir .NET Framework ClickOnce masaüstü uygulaması dağıtma](how-to-publish-a-clickonce-application-using-the-publish-wizard.md). C++/clr için bkz. [ClickOnce kullanarak yerel uygulama dağıtma](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) veya C/C++ için bkz. [kurulum projesi kullanarak yerel uygulama dağıtma](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

::: moniker-end

::: moniker range=">=vs-2019"
> [!NOTE]
> bir klasöre .net Core 3,1 veya daha yeni bir sürüm Windows yayımlamanız gerekiyorsa, bkz. [ClickOnce kullanarak .net Windows uygulaması dağıtma](quickstart-deploy-using-clickonce-folder.md).

::: moniker-end

## <a name="deploy-to-a-local-folder"></a>Yerel klasöre dağıtma

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla** ' yı seçin (veya **Yapı**  >  **Yayımla** menü öğesini kullanın).

    ![Çözüm Gezgini içindeki proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla ' yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** penceresi görüntülenir. **Yeni**'yi seçin.

1. **Yayımla** penceresinde **klasör**' ü seçin.

   ![Yayımla hedefi olarak klasör seçin](../deployment/media/quickstart-publish-folder-new.png "Klasör Seç")

   ::: moniker range=">=vs-2019"

   bir .net Core 3,1 veya daha yeni bir uygulama dağıtıyorsanız, uygulamayı Windows **belirli hedef** pencerede **klasör** seçmeniz gerekebilir.

   ![Belirli bir hedef olarak klasör seçin](../deployment/media/quickstart-publish-folder-targets.png "Belirli hedef seçin")

   ClickOnce bir .net Core 3,1 veya daha yeni bir uygulama Windows yayımlamak istiyorsanız, bkz. [ClickOnce kullanarak .net Windows uygulaması dağıtma](quickstart-deploy-using-clickonce-folder.md).
   ::: moniker-end

1. Bir yol girin veya bir klasör belirtmek için **Araştır** ' ı seçin.

   ![Klasörün yolunu belirtin](../deployment/media/quickstart-publish-folder-path.png "Klasör Seç")

   ::: moniker range=">=vs-2019"
   Profili kaydetmek için **son** ' a tıklayın.

   ![Profil özetini gösteren özellik bölmesini Yayımla](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. **Yayımla**’yı seçin. Visual Studio projeyi oluşturur ve belirtilen klasöre yayımlar.

   ::: moniker range="vs-2017"
   Bir profil Özeti gösteren proje özellikleri **Yayımla** bölmesi görüntülenir.

   ![Profil özetini gösteren özellik bölmesini Yayımla](../deployment/media/quickstart-publish-folder-summary.png)
   ::: moniker-end

1. dağıtım ayarlarını yapılandırmak için, yayımlama profili özetinde **düzenle** ' yi seçin ve **Ayarlar** sekmesini seçin.

   Gördüğünüz ayarlar uygulama türüne bağlıdır. aşağıdaki çizimde bir ASP.NET Core uygulamasının örnek ayarları gösterilmektedir.

    ![Profil ayarları](../deployment/media/quickstart-profile-settings.png "Profil ayarları")

    .NET ' te ayarları seçmek için ek yardım için aşağıdakilere bakın:

    - [Çerçeveye bağımlı ve kendinden bağımsız dağıtım](/dotnet/core/deploying/)
    - [Hedef çalışma zamanı tanımlayıcıları (taşınabilir RID, et)](/dotnet/core/rid-catalog)
    - [Hata ayıklama ve sürüm yapılandırması](../ide/understanding-build-configurations.md)

1. Bir hata ayıklama veya sürüm yapılandırması dağıtıp dağıtmayacağı gibi seçenekleri yapılandırın ve ardından **Kaydet**' i seçin.

1. Yeniden yayımlamak için **Yayımla**' yı seçin.

Yayınlanan dosyaları dilediğiniz gibi dağıtın. Örneğin, bunları bir *.zip* dosyasında paketleyebilir, basit bir kopyalama komutu kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

.NET uygulamaları için:

- [Yayımla aracıyla .NET Core uygulaması dağıtma](/dotnet/core/deploying/deploy-with-vs)
- [.NET Core uygulaması yayımlama (çerçeveye bağlı ve kendinden bağımsız dağıtımlar)](/dotnet/core/deploying/)
- [.NET Framework ve uygulamaları dağıtma](/dotnet/framework/deployment/)
::: moniker range=">=vs-2019"
- [ClickOnce kullanarak bir .net Windows uygulaması dağıtın](quickstart-deploy-using-clickonce-folder.md).
 ::: moniker-end
