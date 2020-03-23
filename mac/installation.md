---
title: Mac için Visual Studio 2019'u yükleyin
description: Mac için Visual Studio 2019'un nasıl yüklenirve ek bileşenlere ve platform ötesi geliştirme için gerekli olan ek bileşenlere ilişkin talimatlar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 45f9756607cbb638d1f69f77bdf8cd2ee30953c5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75851946"
---
# <a name="install-visual-studio-2019-for-mac"></a>Mac için Visual Studio 2019'u yükleyin

macOS'ta yerel, çapraz platform .NET uygulamaları geliştirmeye başlamak için aşağıdaki adımları izleyerek Mac için Visual Studio 2019'u yükleyin.

 > [!div class="button"]
 > [Mac için Visual Studio'u İndirin](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>Gereksinimler

- macOS High Sierra 10.12 veya üzeri bir Mac.

iOS veya macOS için Xamarin uygulamaları oluşturmak için şunları yapmanız da gerekir:

- Xcode 10.0 veya üzeri. En son kararlı sürümü genellikle önerilir.
- Bir Apple kimliği. Zaten bir Apple Kimliğiniz yoksa, 'de https://appleid.apple.comyeni bir kimlik oluşturabilirsiniz. Xcode'u yüklemek ve imzalamak için bir Apple Kimliği'ne sahip olmak gerekir.

## <a name="installation-instructions"></a>Yükleme yönergeleri

1. Yükleyicisi Visual [Studio for Mac indirme sayfasından indirin.](https://visualstudio.microsoft.com/vs/mac/)
2. İndirme tamamlandıktan sonra, yükleyiciyi takmak **için VisualStudioforMacInstaller.dmg'yi** tıklatın ve ardından ok logosunu çift tıklayarak çalıştırın:

    [![Yüklemeye başlamak için büyük oku tıklatın](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Internet'ten indirilen uygulama hakkında size bir uyarı sunulabilir. **Aç**'a tıklayın.
4. Yükleyici sisteminizi denetlerken bekleyin:

    [![Yükleyici sisteminizi yüklü bileşenler için denetler](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Gizlilik ve lisans koşullarını kabul etmenizi isteyen bir uyarı görüntülenir. Bunları okumak için bağlantıları izleyin ve kabul ederseniz **Devam** et' tuşuna basın:

    [![Gizlilik ve şartlara bağlantıları izleyin, sonra kabul ederseniz devam edin](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Kullanılabilir iş yükleri listesi görüntülenir. Kullanmak istediğiniz bileşenleri seçin:

    [![Yüklemek istediğiniz isteğe bağlı iş yükü özelliklerini seçin](media/install-selection.png)](media/install-selection.png#lightbox)

   Tüm platformları yüklemek istemiyorsanız, hangi platformları yükleyeceğimize karar vermenize yardımcı olmak için aşağıdaki kılavuzu kullanın:


|Uygulama Türü  |Hedef  |Seçim  |Notlar  |
|---------|---------|---------|---------|
|**Xamarin Kullanan Uygulamalar**| Xamarin.Forms|**Android** ve **iOS** platformlarını seçin |Xcode yüklemeniz gerekir [ **Xcode**](https://developer.apple.com/xcode/) |
||Yalnızca iOS|**iOS platformünü** seçin|Xcode yüklemeniz gerekir [ **Xcode**](https://developer.apple.com/xcode/)|
||Yalnızca Android|**Android** platformünü seçin|İlgili bağımlılıkları da seçmeniz gerektiğini unutmayın|
||Yalnızca Mac|**macOS (Kakao)** platformünü seçin|Xcode yüklemeniz gerekir [ **Xcode**](https://developer.apple.com/xcode/)|
|**.NET Çekirdek uygulamaları**|         |**.NET Core platformünü** seçin.|         |
|**ASP.NET Core Web Uygulamaları**|         |**.NET Core platformünü** seçin.|         |
|**Azure İşlevleri**|         |**.NET Core platformünü** seçin.|         |
|**Platformötesi Unity Oyun Geliştirme**|         |Mac için Visual Studio dışında ek platformlar yüklenmesi gerekmez.| Unity uzantısını yükleme hakkında daha fazla bilgi için [Birlik kurulum kılavuzuna](/visualstudio/mac/setup-vsmac-tools-unity) bakın.|


7. Seçimlerinizi yaptıktan sonra **Yükle** düğmesine basın.
8. Yükleyici, Mac ve seçilen iş yükleri için Visual Studio'yu karşıdan yükler ve yüklerken ilerlemeyi görüntüler. Yükleme için gerekli ayrıcalıkları sağlamak için parolanızı girmeniz istenir.:

    [![Yüklemek istediğiniz isteğe bağlı iş yükü özelliklerini seçin](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Kurulduktan sonra, Mac için Visual Studio oturum açtığınızda ve kullanmak istediğiniz anahtar bağlamaları seçerek yüklemenizi kişiselleştirmenizi ister:

    [![IDE'de oturum açın](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Hangi klavye kısayollarını kullanmak istediğinizi seçin](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Şirket ortamında yükleme yaparken ağ sorunu yaşıyorsanız, güvenlik duvarı nın veya proxy yönergelerinin [arkasındaki yüklemeyi](/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) gözden geçirin.

[Sürüm notlarında](/visualstudio/releasenotes/vs2019-mac-relnotes)yapılan değişiklikler hakkında daha fazla bilgi edinin.

> [!NOTE]
> Özgün yükleme sırasında bir platform veya araç yüklememeyi seçtiyseniz (#6 adım olarak seçerek), bileşenleri daha sonra eklemek isterseniz yükleyiciyi yeniden çalıştırmanız gerekir.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Güvenlik duvarı veya proxy sunucusunun arkasına Mac için Visual Studio'u yükleyin

Güvenlik duvarının arkasına Mac için Visual Studio yüklemek için, yazılımınız için gerekli araçların ve güncelleştirmelerin karşıdan yüklenmesi için belirli uç noktaların erişilebilir hale getirilmesi gerekir.

Ağınızı aşağıdaki konumlara erişime izin verecek şekilde yapılandırın:

- [Visual Studio uç noktaları](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Sonraki adımlar

Mac için Visual Studio'nun yüklenmesi, uygulamalarınız için kod yazmaya başlamanızı sağlar. Aşağıdaki kılavuzlar, projelerinizi yazma ve dağıtma sonraki adımlarında size rehberlik etmek için sağlanmıştır.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Cihaz Sağlama](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(Uygulamanızı cihazda çalıştırmak için).

### <a name="android"></a>Android

1. [Xamarin Android SDK Yöneticisi kullanma](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Android SDK Emulator](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Cihazı Dağıtım için Ayarlama](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET Core uygulamaları, ASP.NET Core web uygulamaları, Unity oyun geliştirme

Diğer İş Yükleri için [İş Yükleri](workloads.md) sayfasına bakın.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'yı yükleyin (Windows'ta)](/visualstudio/install/install-visual-studio)
