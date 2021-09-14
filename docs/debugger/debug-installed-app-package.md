---
title: Yüklü UWP uygulama paketinde hata ayıklama | Microsoft Docs
description: Windows 10 computers, Xbox ve Nesnelerin İnterneti (ıot) cihazlarındaki Visual Studio yüklü Evrensel Windows Platformu (UWP) uygulama paketinin hatalarını ayıklayın.
ms.custom: SEO-VS-2020
ms.date: 11/07/2018
ms.topic: how-to
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 3d398dd937bad3af548f1a32a4b9a5964ddb31fb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630789"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Visual Studio yüklü bir UWP uygulama paketinin hatalarını ayıklama

Visual Studio, Windows 10 bilgisayarlarda ve Xbox, HoloLens ve ıot cihazlarındaki yüklü Evrensel Windows Platformu (UWP) uygulama paketlerinde hata ayıklayabilirler.

>[!NOTE]
>telefonlarda yüklü UWP uygulamaları için Visual Studio hata ayıklaması desteklenmiyor.

UWP uygulamalarında hata ayıklama hakkında daha fazla bilgi için bkz. [yüklü uygulama paketlerinde hata ayıklama](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) ve [evrensel Windows uygulamaları oluşturma (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Yerel makinede yüklü bir UWP uygulamasında hata ayıklama

1. Visual Studio ' de,   >  **diğer hata ayıklama hedeflerini** hata ayıkla  >  **yüklü uygulama paketi**' ni seçin.

1. **Yüklü uygulama paketi hatalarını ayıkla** iletişim kutusunda, **bağlantı türü** altında **yerel makine**' yi seçin.

1. **Yüklü uygulama paketleri** altında, hata ayıklamak istediğiniz uygulamayı seçin veya arama kutusuna adını yazın. Çalışır olmayan yüklü uygulama paketleri **çalışmıyor** **ve çalışan uygulamalar çalışıyor.**

   ![Debugınstaltadapppackage](../debugger/media/debug-installed-app-pkg.png "Debugınstaltadapppackage")

1. Gerekirse, **Bu kod türünde hata ayıkla** altındaki kod türünü değiştirin ve diğer seçenekleri belirleyin.
   - Başlatma, ancak uygulama başladığında hata ayıklamayı başlatmaya **başladığında kodumdaki Hata Ayıkla ' yı** seçin. Uygulama başlatıldığında hata ayıklamanın başlatılması, özel parametrelerle protokol etkinleştirme gibi [farklı başlatma yöntemlerinden](/windows/uwp/xbox-apps/automate-launching-uwp-apps)denetim yollarının hata ayıklamanın etkili bir yoludur.

1. **Başlat**' ı seçin veya uygulama çalışıyorsa, **Ekle**' yi seçin.

> [!NOTE]
> ayrıca, Visual Studio ' de **hata ayıklama**  >  **ekle** ' ye tıklayarak çalışan UWP veya diğer uygulama işlemlerini de iliştirebilirsiniz. çalışan bir işleme eklemek için özgün Visual Studio projesi gerekmez, ancak uygulamanın simgelerini yüklemek, için özgün koda sahip olmadığınız bir işlemde hata ayıklamanın önemli ölçüde sağlanmasına yardımcı olur. Bkz. [hata ayıklayıcıda sembol ve kaynak dosyaları belirtme](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a> Uzak bilgisayarda veya cihazda yüklü bir UWP uygulamasında hata ayıklama

ilk kez, bir Windows 10 cihazında veya uzak bir oluşturucunun güncelleştirme Windows 10 bilgisayarında yüklü bir UWP uygulamasını Visual Studio hata ayıkladığında, uzaktan hata ayıklama araçlarını hedef cihaza yüklenir.

1. Visual Studio bilgisayarda ve uzak cihazda veya bilgisayarda [geliştirici modunu etkinleştirin](/windows/uwp/get-started/enable-your-device-for-development) .

1. önceden oluşturucunun güncelleştirme Windows 10 çalıştıran bir uzak bilgisayara bağlanıyorsanız, uzaktan [hata ayıklayıcıyı uzak bilgisayara el ile yükleyip başlatın](../debugger/remote-debugging.md) .

1. Visual Studio bilgisayarda, **hata** ayıkla  >  **diğer hata ayıklama hedefleri**  >  **yüklü uygulama paketi hatalarını** ayıkla ' yı seçin.

1. **Yüklü uygulama paketi hatalarını ayıkla** iletişim kutusunda, **bağlantı türü** altında **uzak makine** veya **cihaz**' ı seçin.

   **cihaz**' ı seçerseniz, bilgisayarınızın Windows 10 bir cihaza fiziksel olarak bağlı olması gerekir.

   Uzak makine için, bilgisayar adresi **Adres** seçeneğinin yanında görünmezse, **Değiştir**' i seçin.

   1. **Uzaktan bağlantı** Iletişim kutusunda **Adres**' in yanında, bağlanmak ISTEDIĞINIZ bilgisayarın adını veya IP adresini yazın.

      ![Loseremotecomputer](../debugger/media/debug-remote-app-pkg.png "Loseremotecomputer")

      Hata ayıklayıcı, bilgisayar adını kullanarak uzak bir bilgisayara bağlanamıyorsa bunun yerine IP adresini kullanın. Xbox, HoloLens veya ıot cihazları için ıp adresini kullanın.
   1. **Kimlik doğrulama modu**' nun yanındaki bir kimlik doğrulama seçeneğini belirleyin.

      Çoğu uygulama için varsayılan değeri **Evrensel (şifrelenmemiş protokol)** tutun.
   1. **Seç**’i seçin.

1. **Yüklü uygulama paketleri** altında, hata ayıklamak istediğiniz uygulamayı seçin veya arama kutusuna adını yazın. Çalışır olmayan yüklü uygulama paketleri **çalışmıyor** **ve çalışan uygulamalar çalışıyor.**

1. Gerekirse, **Bu kod türünde hata ayıkla** altındaki kod türünü değiştirin ve diğer seçenekleri belirleyin.
   - Başlatma, ancak uygulama başladığında hata ayıklamayı başlatmaya **başladığında kodumdaki Hata Ayıkla ' yı** seçin. Uygulama başlatıldığında hata ayıklamanın başlatılması, özel parametrelerle protokol etkinleştirme gibi [farklı başlatma yöntemlerinden](/windows/uwp/xbox-apps/automate-launching-uwp-apps)denetim yollarının hata ayıklamanın etkili bir yoludur.

1. **Başlat**' ı seçin veya uygulama çalışıyorsa, **Ekle**' yi seçin.

bağlı bir Xbox, HoloLens veya ıot cihazında, yüklü bir uygulama paketinin hata ayıklamasını ilk kez başlattığınızda, Visual Studio hedef cihazınız için uzak hata ayıklayıcının doğru sürümünü yüklüyor. Uzaktan hata ayıklayıcı 'nın yüklenmesi biraz zaman alabilir ve **Uzaktan hata ayıklayıcı 'Nın başlatılması** sırasında ileti görüntülenir.

>[!NOTE]
>şu anda, bir Xbox veya HoloLens cihazı, zaten çalışıyorsa bir hata ayıklayıcı ekli olarak uygulamayı yeniden başlatır.

UWP uygulamalarının uzaktan dağıtımı hakkında daha fazla bilgi için bkz. [UWP uygulamalarını dağıtma ve hata ayıklama](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) ve [uzak makinelerde UWP uygulamalarında hata](run-windows-store-apps-on-a-remote-machine.md)ayıklama.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
- [Windows Güvenlik Duvarı’nı uzaktan hata ayıklama için yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)