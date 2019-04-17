---
title: Mac için Visual Studio 2019 yükleyin
description: Mac ve platformlar arası geliştirme için gereken ek bileşenleri için Visual Studio 2019'ı yükleme hakkında yönergeler.
author: conceptdev
ms.author: crdun
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 52f9e5f5d21fe69cde613d8e05b365fc8d795dd8
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857326"
---
# <a name="install-visual-studio-2019-for-mac"></a>Mac için Visual Studio 2019 yükleyin

MacOS üzerinde yerel, platformlar arası .NET uygulamalarını geliştirmeye başlamak için aşağıdaki adımları izleyerek Mac için Visual Studio 2019'ı yükleyin.

## <a name="requirements"></a>Gereksinimler

- Mac ile macOS Sierra 10.12 yüksek veya üzeri.

İOS veya Mac OS x için Xamarin uygulamaları oluşturmak için ayrıca gerekir:

- Xcode 11.0 veya üstü. En son kararlı sürüme genellikle önerilir.
- Bir Apple kimliği Bir Apple kimliği yoksa, yeni bir hesap oluşturabilirsiniz https://appleid.apple.com. Yükleme ve Xcode ile imzalamak için bir Apple Kimliği gereklidir.

## <a name="installation-instructions"></a>Yükleme yönergeleri

1. Yükleyici'den indirin [indirme sayfasında Mac için Visual Studio](https://aka.ms/vsmac).
2. İndirme tamamlandıktan sonra tıklayın **VisualStudioforMacInstaller.dmg** yükleyici bağlamak için çalıştırın ve ok logosu çift tıklayarak:

    [![Cyüklemeye başlamak için büyük bir ok'yi tıklatın](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Internet'ten yüklenen uygulama hakkında bir uyarı ile sunulan. Tıklayın **açık**.
4. Yükleyicinin sisteminizi denetlerken bekleyin:

    [![THe yükleyici sisteminiz için yüklü bileşenlerin denetler](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Gizlilik ve lisans koşullarını kabul etmek isteyen bir uyarı görüntülenir. Bunları okuyun ve sonra basın için bağlantıları izleyin **devam** kabul ediyorsanız:

    [![Follow koşullarını ve gizlilik bağlantılarını devam kabul etmiyorsanız](media/install-privacy-sml.png)](media/install-privacy.png#lightbox)

6. Kullanılabilir iş yüklerinin listesi görüntülenir. Kullanmak için istediklerinizi seçin:

    [![Cİsteğe bağlı hangi iş yükü özelliklerine toplanmasını yüklemek istiyorsunuz](media/install-selection-sml.png)](media/install-selection.png#lightbox)

7. Seçimlerinizi yaptıktan sonra basın **yükleme** düğmesi.
8. İndirir ve Mac ve seçilen iş yükleri için Visual Studio'yu yükler yükleyici ilerleme durumunu görüntüler. Yükleme için gerekli ayrıcalıklara vermek için parolanızı girmeniz istenebilir.

Bir Kurumsal ortamda yüklenirken ağ bulmakta güçlük çekiyorsanız, gözden [bir güvenlik duvarı veya proxy yüklemeye](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) yönergeleri.

Değişiklikleri hakkında daha fazla bilgi [sürüm notları](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Seçtiğiniz bir platform veya aracı özgün yükleme sırasında (bunu #6. adımda seçimini tarafından) değil yüklerseniz, bileşen daha sonra eklemek istiyorsanız, yükleyici yeniden çalıştırmanız gerekir.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Visual Studio Mac için bir güvenlik duvarı veya proxy sunucusunun arkasına yükleme

Güvenlik duvarının arkasında Mac için Visual Studio'yu yüklemek için belirli uç noktaları, yazılım güncelleştirmeleri ve gerekli araçları indirmeye izin ver için erişilebilir yapılması gerekir.

Şu konumlardan erişime izin vermek için ağ yapılandırın:

- [Visual Studio uç noktaları](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Sonraki adımlar

Mac için Visual Studio yükleme, uygulamalarınız için kod yazmaya olanak tanır. Aşağıdaki kılavuzlarda yazma ve projelerinizi dağıtma sonraki adımlarda size rehberlik sağlanmaktadır.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Cihaz sağlama](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(cihazda uygulamanızı çalıştırmak için).

### <a name="android"></a>Android

1. [Xamarin Android SDK Yöneticisi'ni kullanma](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Android SDK öykünücüsü](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Geliştirme için cihazı ayarlama](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET core uygulamaları, ASP.NET Core web uygulamaları, Unity oyun geliştirme

Diğer iş yükleri için başvurmak [iş yükleri](/visualstudio/mac/workloads) sayfası.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Ayrıca bkz.

- [(Windows üzerinde) Visual Studio'yu yükleyin](/visualstudio/install/install-visual-studio)