---
title: Yüklü UWP uygulama paketinde hata ayıklama | Microsoft Docs
ms.custom: ''
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: eabc694665bede7d193a360a01c42366568e33c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350738"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Visual Studio 'da yüklü UWP uygulama paketinde hata ayıklama

Visual Studio, Windows 10 bilgisayarlarda ve Xbox, HoloLens ve IoT cihazlarında yüklü Evrensel Windows Platformu (UWP) uygulama paketlerinde hata ayıklayabilirler.

>[!NOTE]
>Yüklü UWP uygulamaları için Visual Studio hata ayıklaması telefonlarda desteklenmez.

UWP uygulamalarında hata ayıklama hakkında daha fazla bilgi için bkz. [yüklü uygulama paketlerinde hata ayıklama](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) ve [evrensel WINDOWS uygulamaları (UWP) oluşturma](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Yerel makinede yüklü bir UWP uygulamasında hata ayıklama

1. Visual Studio 'da hata ayıkla **Debug**  >  **diğer hata ayıklama hedefleri**  >  **yüklü uygulama paketinde**Hata Ayıkla ' yı seçin.

1. **Yüklü uygulama paketi hatalarını ayıkla** iletişim kutusunda, **bağlantı türü**altında **yerel makine**' yi seçin.

1. **Yüklü uygulama paketleri**altında, hata ayıklamak istediğiniz uygulamayı seçin veya arama kutusuna adını yazın. Çalışır olmayan yüklü uygulama paketleri **çalışmıyor** **ve çalışan uygulamalar çalışıyor.**

   ![Debugınstaltadapppackage](../debugger/media/debug-installed-app-pkg.png "Debugınstaltadapppackage")

1. Gerekirse, **Bu kod türünde hata ayıkla**altındaki kod türünü değiştirin ve diğer seçenekleri belirleyin.
   - Başlatma, ancak uygulama başladığında hata ayıklamayı başlatmaya **başladığında kodumdaki Hata Ayıkla ' yı** seçin. Uygulama başlatıldığında hata ayıklamanın başlatılması, özel parametrelerle protokol etkinleştirme gibi [farklı başlatma yöntemlerinden](/windows/uwp/xbox-apps/automate-launching-uwp-apps)denetim yollarının hata ayıklamanın etkili bir yoludur.

1. **Başlat**' ı seçin veya uygulama çalışıyorsa, **Ekle**' yi seçin.

> [!NOTE]
> Ayrıca, Visual Studio 'da **hata ayıklama**  >  **Ekle** ' ye tıklayarak çalışan UWP veya diğer uygulama işlemlerini de iliştirebilirsiniz. Çalışan bir işleme eklemek için özgün Visual Studio projesine ihtiyacınız yoktur, ancak uygulamanın simgelerini yüklemek, için özgün koda sahip olmadığınız bir işlemde hata ayıklamanın önemli ölçüde sağlanmasına yardımcı olur. Bkz. [hata ayıklayıcıda sembol ve kaynak dosyaları belirtme](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a> Uzak bilgisayarda veya cihazda yüklü bir UWP uygulamasında hata ayıklama

Visual Studio 'da bir Windows 10 cihazında veya uzak bir oluşturucunun güncelleştirme Windows 10 bilgisayarında yüklü bir UWP uygulamasını ilk kez yüklerken, uzaktan hata ayıklama araçları 'nı hedef cihaza yüklenir.

1. Visual Studio bilgisayarında ve uzak cihazda veya bilgisayarda [Geliştirici modunu etkinleştirin](/windows/uwp/get-started/enable-your-device-for-development) .

1. Windows 10 ' un ön oluşturanın güncelleştirme çalıştıran bir uzak bilgisayara bağlanıyorsanız uzak bilgisayara [Uzaktan hata ayıklayıcıyı el ile yükleyip başlatın](../debugger/remote-debugging.md) .

1. Visual Studio bilgisayarında, **hata**Ayıkla  >  **diğer hata ayıklama hedefleri**  >  **yüklü uygulama paketi**hatalarını ayıkla ' yı seçin.

1. **Yüklü uygulama paketi hatalarını ayıkla** iletişim kutusunda, **bağlantı türü**altında **uzak makine** veya **cihaz**' ı seçin.

   **Cihaz**' ı seçerseniz, bilgisayarınızın bir Windows 10 cihazına fiziksel olarak bağlı olması gerekir.

   Uzak makine için, bilgisayar adresi **Adres**seçeneğinin yanında görünmezse, **Değiştir**' i seçin.

   1. **Uzaktan bağlantı** Iletişim kutusunda **Adres**' in yanında, bağlanmak ISTEDIĞINIZ bilgisayarın adını veya IP adresini yazın.

      ![Loseremotecomputer](../debugger/media/debug-remote-app-pkg.png "Loseremotecomputer")

      Hata ayıklayıcı, bilgisayar adını kullanarak uzak bir bilgisayara bağlanamıyorsa bunun yerine IP adresini kullanın. Xbox, HoloLens veya IoT cihazları için IP adresini kullanın.
   1. **Kimlik doğrulama modu**' nun yanındaki bir kimlik doğrulama seçeneğini belirleyin.

      Çoğu uygulama için varsayılan değeri **Evrensel (şifrelenmemiş protokol)** tutun.
   1. **Seç**’i seçin.

1. **Yüklü uygulama paketleri**altında, hata ayıklamak istediğiniz uygulamayı seçin veya arama kutusuna adını yazın. Çalışır olmayan yüklü uygulama paketleri **çalışmıyor** **ve çalışan uygulamalar çalışıyor.**

1. Gerekirse, **Bu kod türünde hata ayıkla**altındaki kod türünü değiştirin ve diğer seçenekleri belirleyin.
   - Başlatma, ancak uygulama başladığında hata ayıklamayı başlatmaya **başladığında kodumdaki Hata Ayıkla ' yı** seçin. Uygulama başlatıldığında hata ayıklamanın başlatılması, özel parametrelerle protokol etkinleştirme gibi [farklı başlatma yöntemlerinden](/windows/uwp/xbox-apps/automate-launching-uwp-apps)denetim yollarının hata ayıklamanın etkili bir yoludur.

1. **Başlat**' ı seçin veya uygulama çalışıyorsa, **Ekle**' yi seçin.

Bağlı bir Xbox, HoloLens veya IoT cihazında yüklü bir uygulama paketinin hatasını ilk kez başlattığınızda, Visual Studio hedef cihazınız için uzak hata ayıklayıcının doğru sürümünü yüklüyor. Uzaktan hata ayıklayıcı 'nın yüklenmesi biraz zaman alabilir ve **Uzaktan hata ayıklayıcı 'Nın başlatılması** sırasında ileti görüntülenir.

>[!NOTE]
>Şu anda, bir Xbox veya HoloLens cihazı zaten çalışıyorsa bir hata ayıklayıcı ekli olarak uygulamayı yeniden başlatır.

UWP uygulamalarının uzaktan dağıtımı hakkında daha fazla bilgi için bkz. [UWP uygulamalarını dağıtma ve hata ayıklama](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) ve [uzak makinelerde UWP uygulamalarında hata](run-windows-store-apps-on-a-remote-machine.md)ayıklama.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
- [Uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)