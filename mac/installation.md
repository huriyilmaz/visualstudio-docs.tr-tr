---
title: Mac Visual Studio 2019'u yükleme
description: Mac için 2019'Visual Studio yükleme yönergeleri ve platformlar arası geliştirme için gereken ek bileşenler.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 03/04/2021
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 653e653a0574da52c0030b06c7a8c13b436ed686
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964781"
---
# <a name="install-visual-studio-2019-for-mac"></a>Mac Visual Studio 2019'u yükleme

macOS üzerinde yerel, platformlar arası .NET uygulamaları geliştirmeye başlamak için aşağıdaki adımları Visual Studio Mac için 2019'u yükleyin.

 > [!div class="button"]
 > [Mac için Visual Studio’yu indirin](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>Gereksinimler

- macOS High Sierra 10.13 veya üzeri bir Mac.

iOS veya macOS için Xamarin uygulamaları oluşturmak için şunları da gerekir:

- Xcode'un en son sürümüyle uyumlu bir Mac. Apple'ın en düşük [gereksinimler belgelerine bakın](https://developer.apple.com/support/xcode/)
- [Xcode'un en son sürümü.](https://developer.apple.com/xcode) Mac'iniz [en son sürümle uyumlu değilse Xcode'un](https://docs.microsoft.com/xamarin/ios/troubleshooting/questions/old-version-xcode) eski bir sürümünü kullanmak mümkün olabilir.
- Apple kimliği. Apple kimliğiniz yoksa, 'de yeni bir tane https://appleid.apple.com oluşturabilirsiniz. Xcode'u yüklemek ve bu kodda oturum a açma için bir Apple kimliğine sahip olmak gerekir.

## <a name="installation-instructions"></a>Yükleme yönergeleri

1. Yükleyiciyi indirme [sayfasından Mac için Visual Studio indirin.](https://visualstudio.microsoft.com/vs/mac/)
2. İndirme işlemi tamamlandıktan sonra **VisualStudioforMacInstaller.dmg'ye** tıklayarak yükleyiciyi çalıştırın ve ardından ok logosuna çift tıklayarak çalıştırın:

    [![Yüklemeye başlamak için büyük oka tıklayın](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. İnternet'den indirilen uygulama hakkında bir uyarıyla karşınız olabilir. **Aç**’a tıklayın.
4. Yükleyici sisteminizi denetlerken bekleyin:

    [![Yükleyici, sisteminizi yüklü bileşenler için denetler](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Gizlilik ve lisans koşullarını kabul etmek isteyen bir uyarı görüntülenir. Bunları okumak için bağlantıları izleyin ve kabul ediyorsanız **Devam'a** basın:

    [![Gizlilik ve koşulların bağlantılarını izleyin ve kabul ediyorsanız devam edin](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Kullanılabilir iş yüklerinin listesi görüntülenir. Kullanmak istediğiniz bileşenleri seçin:

    [![Visual Studio Mac Installer'daki "Neleri yüklemek Visual Studio?" ekranında yükleme için kullanılabilen bileşenlerin listesini gösteren ekran görüntüsü.](media/install-selection.png)](media/install-selection.png#lightbox)

   Tüm platformları yüklemek isterseniz, hangi platformların yüklen karar vermelerine yardımcı olması için aşağıdaki kılavuzu kullanın:

   |Uygulama Türü  |Hedef  |Seçim  |Notlar  |
   |---------|---------|---------|---------|
   |**Xamarin Kullanan Uygulamalar**| Xamarin.Forms|**Android ve** **iOS platformlarını** seçme |[ **Xcode'ı yüklemeniz gerekir**](https://developer.apple.com/xcode/) |
   ||Yalnızca iOS|**iOS platformunu** seçme|[ **Xcode'ı yüklemeniz gerekir**](https://developer.apple.com/xcode/)|
   ||Yalnızca Android|**Android platformunu** seçme|Ayrıca ilgili bağımlılıkları da seçmeniz gerektiğini unutmayın|
   ||Yalnızca Mac|**macOS (Cocoa) platformunu** seçme|[ **Xcode'ı yüklemeniz gerekir**](https://developer.apple.com/xcode/)|
   |**.NET Core uygulamaları**|         |**.NET Core platformu'na** seçin.|         |
   |**ASP.NET Core Web Uygulamaları**|         |**.NET Core platformu'na** seçin.|         |
   |**Azure İşlevleri**|         |**.NET Core platformu'na** seçin.|         |
   |**Platformlar arası Unity Oyun Geliştirme**|         |Diğer platformların ötesinde ek platformların Mac için Visual Studio.| Unity uzantısını [yükleme hakkında daha fazla](./setup-vsmac-tools-unity.md) bilgi için Unity kurulum kılavuzuna bakın.|

7. Seçimlerinizi yaptıktan sonra Yükle **düğmesine** basın.
8. Yükleyici, iş yüklerini ve seçilen iş yüklerini indirdiği Mac için Visual Studio ilerlemeyi görüntüler. Yükleme için gerekli ayrıcalıkları vermek için parolanızı girmeniz istenir:

    [![Mac için .NET Visual Studio araç seti yükleme ilerlemesini gösteren Mac Yükleyicisi'nin ekran görüntüsü.](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Yüklendikten sonra Mac için Visual Studio oturum açın ve kullanmak istediğiniz anahtar bağlamalarını seçerek yüklemenizi kişiselleştirmenizi istenir:

    [![IDE'de oturum açma](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Kullanmak istediğiniz klavye kısayollarını seçin](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Şirket ortamında yüklerken ağ sorunlarınız varsa, güvenlik duvarı veya ara sunucu [yönergelerinin arkasına yükleme adımlarını gözden](#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) geçirebilirsiniz.

Sürüm notlarında değişiklikler hakkında daha fazla [bilgi alın.](/visualstudio/releasenotes/vs2019-mac-relnotes)

> [!NOTE]
> Özgün yükleme sırasında bir platform veya araç yüklememeyi seçtiyebilirsiniz (#6 adım adım seçimini kaldırarak), bileşenleri daha sonra eklemek isterseniz yükleyiciyi yeniden çalıştırmalısınız.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Güvenlik Mac için Visual Studio ara sunucunun arkasına yükleme

Güvenlik duvarının Mac için Visual Studio yüklemek için, yazılımınız için gerekli araç ve güncelleştirmelerin indirilmelerine izin vermek amacıyla belirli uç noktaların erişilebilir hale olması gerekir.

Anızı aşağıdaki konumlara erişime izin verecek şekilde yapılandırma:

- [Visual Studio uç noktaları](./install-behind-a-firewall-or-proxy-server.md)

## <a name="next-steps"></a>Sonraki adımlar

Uygulama Mac için Visual Studio, uygulamalarınız için kod yazmaya başlamanıza olanak sağlar. Aşağıdaki kılavuzlar, projelerinizi yazmaya ve dağıtmaya yönelik sonraki adımlarda size yol gösteren kılavuzlar verilmektedir.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://docs.microsoft.com//xamarin/ios/get-started/hello-ios/)
2. [Cihaz Sağlama](https://docs.microsoft.com/xamarin/ios/get-started/installation/device-provisioning/)(Uygulamanızı cihazda çalıştırmak için).

### <a name="android"></a>Android

1. [Hello, Android](https://docs.microsoft.com/xamarin/android/get-started/hello-android/)
2. [Xamarin Android SDK Yöneticisi](https://docs.microsoft.com/xamarin/android/get-started/installation/android-sdk?tabs=macos)
3. [Android SDK Emulator](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/)
4. [Cihazı Dağıtım için Ayarlama](https://docs.microsoft.com/xamarin/android/get-started/installation/set-up-device-for-development)

### <a name="xamarinforms"></a>Xamarin.Forms

Xamarin.Forms ile yerel platformlar arası uygulamalar derleme:

1. [Xamarin.Forms Hızlı Başlangıçları](https://docs.microsoft.com/xamarin/get-started/quickstarts/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET Core uygulamaları, ASP.NET Core web uygulamaları, Unity oyun geliştirme

Diğer İş Yükleri için İş Yükleri [sayfasına](workloads.md) bakın.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Yükleme Visual Studio (Windows)](/visualstudio/install/install-visual-studio)
