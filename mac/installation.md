---
title: Mac için Visual Studio 2019 'yi yükler
description: Mac için Visual Studio 2019 ' i ve platformlar arası geliştirme için gereken ek bileşenleri yüklemek için yönergeler.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 8020106ed189b1b67b7cc2f475784809fc93aa1e
ms.sourcegitcommit: a3edc753c951f317b67ce294cd2fc74f0c45390c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89426908"
---
# <a name="install-visual-studio-2019-for-mac"></a>Mac için Visual Studio 2019 'yi yükler

MacOS 'ta yerel, platformlar arası .NET uygulamaları geliştirmeye başlamak için aşağıdaki adımları izleyerek Mac için Visual Studio 2019 ' yi yüklemelisiniz.

 > [!div class="button"]
 > [Mac için Visual Studio indir](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>Gereksinimler

- MacOS High Sierra 10,13 veya üzeri bir Mac.

İOS veya macOS için Xamarin uygulamaları oluşturmak üzere şunları da yapmanız gerekir:

- Xcode 10,0 veya üzeri. En son kararlı sürüm genellikle önerilir.
- Bir Apple KIMLIĞI. Zaten bir Apple KIMLIĞINIZ yoksa, üzerinde yeni bir tane oluşturabilirsiniz https://appleid.apple.com . Xcode 'a yükleme ve oturum açma için bir Apple KIMLIĞI olması gerekir.

## <a name="installation-instructions"></a>Yükleme yönergeleri

1. Yükleyiciyi [Mac için Visual Studio indirme sayfasından](https://visualstudio.microsoft.com/vs/mac/)indirin.
2. İndirme işlemi tamamlandıktan sonra, yükleyiciyi bağlamak için **VisualStudioforMacInstaller. dmg** ' ye tıklayın ve ardından ok logosunu çift tıklayarak çalıştırın:

    [![Yüklemeyi başlatmak için büyük oka tıklayın](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Internet 'ten indirilen uygulamayla ilgili bir uyarı alabilirsiniz. **Aç**’a tıklayın.
4. Yükleyici sisteminizi denetlerken bekleyin:

    [![Yükleyici, sisteminizde yüklü bileşenleri denetler](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Gizlilik ve lisans şartlarını doğrulamanızı isteyen bir uyarı görüntülenir. Bunları okumak için bağlantıları izleyin ve kabul ediyorsanız **devam** ' a basın:

    [![Gizlilik ve koşullara ilişkin bağlantıları izleyin, ardından kabul ediyorsanız devam edin](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Kullanılabilir iş yüklerinin listesi görüntülenir. Kullanmak istediğiniz bileşenleri seçin:

    [![Yüklemek istediğiniz isteğe bağlı iş yükü özelliklerini seçin](media/install-selection.png)](media/install-selection.png#lightbox)

   Tüm platformları yüklemek istemiyorsanız, hangi platformları yükleyeceğinize karar vermenize yardımcı olması için aşağıdaki kılavuzu kullanın:

   |Uygulama türü  |Hedef  |Seçim  |Notlar  |
   |---------|---------|---------|---------|
   |**Xamarin kullanan uygulamalar**| Xamarin.Forms|**Android** ve **iOS** platformlarını seçin |[ **Xcode** 'u yüklemeniz gerekecektir](https://developer.apple.com/xcode/) |
   ||Yalnızca iOS|**İOS** platformunu seçin|[ **Xcode** 'u yüklemeniz gerekecektir](https://developer.apple.com/xcode/)|
   ||Yalnızca Android|**Android** platformunu seçin|Ayrıca ilgili bağımlılıkları da seçmeniz gerektiğini unutmayın|
   ||Yalnızca Mac|**MacOS (Cocoa)** platformunu seçin|[ **Xcode** 'u yüklemeniz gerekecektir](https://developer.apple.com/xcode/)|
   |**.NET Core Uygulamaları**|         |**.NET Core** platformunu seçin.|         |
   |**ASP.NET Core Web Uygulamaları**|         |**.NET Core** platformunu seçin.|         |
   |**Azure İşlevleri**|         |**.NET Core** platformunu seçin.|         |
   |**Platformlar arası Unity oyun geliştirme**|         |Mac için Visual Studio ötesinde ek platform yüklenmesi gerekmez.| Unity uzantısını yükleme hakkında daha fazla bilgi için [Unity kurulum kılavuzuna](/visualstudio/mac/setup-vsmac-tools-unity) bakın.|

7. Seçimlerinizi yaptıktan sonra, **Install** düğmesine basın.
8. Yükleyici, Mac için Visual Studio ve seçilen iş yüklerini indirdiği ve yükleyen ilerlemeyi görüntüler. Yükleme için gerekli ayrıcalıkları vermek üzere parolanızı girmeniz istenir.:

    [![Yüklemek istediğiniz isteğe bağlı iş yükü özelliklerini seçin](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Mac için Visual Studio, yükledikten sonra oturum açarak ve kullanmak istediğiniz anahtar bağlamalarını seçerek yüklemenizi kişiselleştirmenizi ister:

    [![IDE 'de oturum açın](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Kullanmak istediğiniz klavye kısayollarını seçin](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Şirket ortamında yükleme sırasında ağ sorununuz varsa, [bir güvenlik duvarı veya proxy yönergeleri arkasındaki yüklemeyi](/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) inceleyin.

[Sürüm notlarındaki](/visualstudio/releasenotes/vs2019-mac-relnotes)değişiklikler hakkında daha fazla bilgi edinin.

> [!NOTE]
> Özgün yükleme sırasında bir platform veya araç yüklememeyi seçtiyseniz (#6 adımında bunu seçerek), bileşenleri daha sonra eklemek istiyorsanız yükleyiciyi yeniden çalıştırmalısınız.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Bir güvenlik duvarı veya proxy sunucusunun arkasında Mac için Visual Studio yüklemesi

Bir güvenlik duvarının arkasında Mac için Visual Studio yüklemek için, yazılım için gerekli araçların ve güncelleştirmelerin indirilmelerine izin vermek üzere belirli uç noktalara erişilebilir hale gelmelidir.

Ağınızı aşağıdaki konumlara erişime izin verecek şekilde yapılandırın:

- [Visual Studio uç noktaları](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Sonraki adımlar

Mac için Visual Studio yükleme, uygulamalarınız için kod yazmaya başlayabilmeniz için izin verir. Aşağıdaki kılavuzlar, projelerinizi yazmanın ve dağıtmanın sonraki adımlarında size yol gösterecek şekilde sunulmaktadır.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Cihaz sağlama](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(uygulamanızı cihazda çalıştırmak için).

### <a name="android"></a>Android

1. [Xamarin Android SDK Manager 'ı kullanma](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Android SDK Emulator](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Cihazı Dağıtım için Ayarlama](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET Core Uygulamaları, ASP.NET Core Web Apps, Unity oyun geliştirme

Diğer Iş yükleri için [Iş yükleri](workloads.md) sayfasına bakın.

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'Yu (Windows 'a) yükler](/visualstudio/install/install-visual-studio)
