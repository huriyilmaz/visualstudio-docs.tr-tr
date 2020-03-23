---
title: Mac için Visual Studio 2017'yi yükleyin
description: Mac için Visual Studio'nun nasıl yüklenirve platform ötesi geliştirme için gerekli ek bileşenlerle ilgili talimatlar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: dfc9f7469f5954aaac56b5d45bb5ae722110dfcc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984915"
---
# <a name="install-visual-studio-2017-for-mac"></a>Mac için Visual Studio 2017'yi yükleyin

> [!NOTE]
> Mac için Visual Studio 2019 [artık mevcuttur.](installation.md?view=vsmac-2019) Mac için Visual Studio'nun eski sürümleri için Visual Studio [indirme sayfasına](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)bakın.

## <a name="downgrading-from-visual-studio-2019-for-mac"></a>Mac için Visual Studio 2019'dan aşağı mı?

En iyi deneyim için, düşürmeden önce Visual Studio 2019'u Mac için [kaldırdığınızdan](uninstall.md) emin olmalısınız. İndirmenize neden olan sorunlarınız varsa, [bir sorunu bildirerek](report-a-problem.md)bize bildirin.
 
## <a name="requirements"></a>Gereksinimler

Mac için Visual Studio'yı indirdiğinizde yerel, platformlar arası uygulamalar geliştirmeye başlamak için yüklemeniz ve hazırlık aşamasında kurmanız gereken birkaç şey vardır.

Visual Studio'da iOS ile çalışmak için aşağıdaki parçalara ihtiyacınız var:

- macOS Sierra 10.12 veya üzeri bir Mac
- Xcode 9.3 veya üzeri. En son kararlı sürümü genellikle önerilir.
- Bir Apple kimliği. Zaten bir Apple Kimliğiniz yoksa, 'de https://appleid.apple.comyeni bir kimlik oluşturabilirsiniz. Xcode'u yüklemek ve imzalamak için bir Apple Kimliği'ne sahip olmak gerekir.

## <a name="install"></a>Yükleme

1. Mac için Visual [Studio'my.visualstudio.com'dan](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac) indirin

2. Yükleyici paketi indirildikten sonra, yükleyiciyi takmak için **VisualStudioForMacInstaller.dmg** dosyasına tıklayın ve aşağıdaki resimde gösterildiği gibi logoyu çift tıklayarak çalıştırın:

   ![Yükleyici iletişim kutusu](media/installer-image1.png)

3. Aşağıdaki resme benzer bir uyarı iletişim kutusu yla istenebilir. Bu durumda **Aç'ı**tıklatın:

   ![uyarı iletişim kutusu](media/installer-image2.png)

4. Yükleyici, hangi bileşenlerin yüklenmesi veya güncellenmesi gerektiğini doğrulamak için sisteminizi denetler:

   ![Sisteminizi değerlendirme](media/installer-image3.png)

5. Daha sonra, Gizlilik ve Lisans koşullarını kabul etmenizi isteyen bir uyarı iletişim kutusu sunulur. Koşulları kabul etmek için **Continue** düğmesine basın:

   ![Lisans iletişim kutusu](media/installer-image4.png)

6. Yükleyici, eksik olan ve indirilmesi ve yüklenmesi gereken gerekli bileşenlerin bir listesini sunar. İndirmek istediğiniz ürünleri buradan seçin:

   ![Öğeleri Seçin](media/installer-image5.png)

   Tüm platformları yüklemek istemiyorsanız, hangi platformları yükleyeceğimize karar vermenize yardımcı olmak için aşağıdaki kılavuzu kullanın:

   * **Xamarin kullanan uygulamalar:**
      - Xamarin.Forms – **Android** ve **iOS** platformlarını seçin.
      - Yalnızca **iOS** ' u seçin – iOS platformunu seçin [**(Xcode'u**](https://developer.apple.com/xcode/)yüklemeniz gerekeceğini unutmayın).
      - Yalnızca Android - **Android** platformunu seçin (İlgili bağımlılıkları da seçmeniz gerektiğini unutmayın).
      - Yalnızca Mac – **macOS** platformunu seçin [**(Xcode'u**](https://developer.apple.com/xcode/)yüklemeniz gerekeceğini unutmayın).
      - Tamamen çapraz platform Xamarin uygulamaları – **Android,** **iOS**ve **macOS** platformlarını seçin.
   * **.NET Core uygulamaları** – **.NET Core** platformünü seçin.
   * **ASP.NET Çekirdek Web Uygulamaları** – **.NET Core platformünü** seçin.
   * **Platformlar arası Unity Game Development** – Mac için Visual Studio dışında ek platformlar yüklenmenize gerek yoktur. Unity uzantısını yükleme hakkında daha fazla bilgi için [Birlik kurulum kılavuzuna](/visualstudio/mac/setup-vsmac-tools-unity) bakın.

   Bu yükleme ekranı, her bir bileşenin sürümünü ve boyutunu görüntüler. Bu bileşene (Android için) bağımlılıklistesini görüntülemek için her bileşeni tıklatabilir, karşıdan yükettiği ek paketleri görebilir (.NET Core için) veya gerekli ek uygulamaları görüntüleyebilirsiniz (iOS ve macOS için):

   ![Android ek bağımlılıkları](media/installer-image6.png)

7. Seçimden memnun kaldıktan sonra yükleme işlemini başlatmak için **Yükle ve Güncelleştir** düğmesini seçin.

8. Yükleyici, seçili öğelerin indirme ve yükleme işlemini başlatır:

   ![Yüklemeyi Başlatma](media/installer-image7.png)

   ![Xamarin.Mac İndirme](media/installer-image8.png)

   ![Son İşlem Montajı](media/installer-image9.png)

9. Yüklemeyi tamamlamak için gereken tek tek bileşenler için gerekli izinleri yükseltmeniz istenebilir. Yükleme işlemine devam etmek için yönetici kimlik bilgilerinizi buraya girin:

   ![Yükleyiciyle devam etmek için izinleri girin](media/installer-image10.png)

10. Kurulum başarılı olduktan **sonra, Başlat**tuşuna basarak Visual Studio'da uygulama geliştirmeye başlayabilirsiniz:

    ![Visual Studio’yu açın](media/installer-image11.png)

> [!NOTE]
> Özgün yükleme sırasında bir platform veya araç yüklememeyi seçtiyseniz (#6 adım da seçerek), bileşenleri daha sonra eklemek isterseniz [yükleyiciyi](https://visualstudio.microsoft.com/vs/) yeniden çalıştırmanız gerekir.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Güvenlik duvarı veya proxy sunucusunun arkasına Mac için Visual Studio'u yükleyin

Güvenlik duvarının arkasına Mac için Visual Studio yüklemek için, yazılımınız için gerekli araçların ve güncelleştirmelerin karşıdan yüklenmesi için belirli uç noktaların erişilebilir hale getirilmesi gerekir.

Ağınızı aşağıdaki konumlara erişime izin verecek şekilde yapılandırın:

- [Visual Studio uç noktaları](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

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

Diğer İş Yükleri için [İş Yükleri](/visualstudio/mac/workloads) sayfasına bakın.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017'yi yükle (Windows'da)](/visualstudio/install/install-visual-studio)
