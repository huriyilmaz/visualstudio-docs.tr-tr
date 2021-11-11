---
title: Mac için Visual Studio 2017 'yi yükler
description: platformlar arası geliştirme için gereken Mac için Visual Studio ve ek bileşenlerin nasıl yükleneceğine ilişkin yönergeler.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/10/2021
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: a1a6c7760d32801a41dd13d78143ad4674eedf7c
ms.sourcegitcommit: abfcccf63234819c75a61bf2c4c7f710a9d23cdb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132250627"
---
# <a name="install-visual-studio-2017-for-mac"></a>Mac için Visual Studio 2017 'yi yükler

> [!NOTE]
> Mac için Visual Studio 2019 [artık kullanılabilir](installation.md?view=vsmac-2019&preserve-view=true). daha eski Mac için Visual Studio sürümleri için, Visual Studio [indirmeleri sayfasına](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)bakın.

## <a name="downgrading-from-visual-studio-2019-for-mac"></a>Mac için Visual Studio 2019 ' den eski sürüme düşürme mi?

en iyi deneyim için, önce, Mac için Visual Studio 2019 ' yi [kaldırmanızı](uninstall.md) öneririz.
 
## <a name="requirements"></a>Gereksinimler

Mac için Visual Studio karşıdan yüklerken yerel, platformlar arası uygulamalar geliştirmeye başlamak için, hazırlık aşamasında ve ayarlamanız gereken birkaç şey vardır.

Visual Studio ' de iOS ile çalışma için aşağıdaki parçalara ihtiyacınız vardır:

- MacOS High Sierra 10,13 veya üzeri bir Mac.
- Xcode 9,3 veya üzeri. En son kararlı sürüm genellikle önerilir.
- Bir Apple KIMLIĞI. Zaten bir Apple KIMLIĞINIZ yoksa, üzerinde yeni bir tane oluşturabilirsiniz https://appleid.apple.com . Xcode 'a yükleme ve oturum açma için bir Apple KIMLIĞI olması gerekir.

## <a name="install"></a>Yükleme

1. [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac) 'dan Mac için Visual Studio indirin

2. Yükleyici paketi indirildikten sonra, yükleyiciyi bağlamak için **VisualStudioForMacInstaller. dmg** dosyasını tıklatın ve ardından aşağıdaki görüntüde gösterildiği gibi logoyu çift tıklayarak çalıştırın:

   ![Yükleyici iletişim kutusu](media/installer-image1.png)

3. Aşağıdaki görüntüye benzer bir uyarı iletişim kutusu istenebilir. Bu durumda **Aç**' a tıklayın:

   ![Uyarı iletişim kutusu](media/installer-image2.png)

4. Yükleyici, hangi bileşenlerin yüklenmesi veya güncellenmesi gerektiğini doğrulamak için sisteminizi inceler:

   ![Sisteminizi değerlendirme](media/installer-image3.png)

5. Bundan sonra Gizlilik ve lisans koşullarını kabul etmeniz için bir uyarı iletişim kutusu görüntülenir. Koşulları onaylamak için **devam** düğmesine basın:

   ![Lisans iletişim kutusu](media/installer-image4.png)

6. Yükleyici, eksik olan ve indirilmesi gereken ve yüklenmesi gereken bileşenlerin bir listesini sunar. Buraya indirmek istediğiniz ürünleri seçin:

   ![Öğeleri seç](media/installer-image5.png)

   Tüm platformları yüklemek istemiyorsanız, hangi platformları yükleyeceğinize karar vermenize yardımcı olması için aşağıdaki kılavuzu kullanın:

   * **Xamarin kullanan uygulamalar**:
      - Xamarin. Forms: **Android** ve **iOS** platformları ' nı seçin.
      - yalnızca iOS – **iOS** platformunu seçin ( [**Xcode**](https://developer.apple.com/xcode/)'u yüklemeniz gerekeceğini unutmayın).
      - Yalnızca Android – **Android** platformunu seçin (ilgili bağımlılıkları da seçmeniz gerektiğini unutmayın).
      - Yalnızca Mac – **MacOS** platformunu seçin ( [**Xcode**](https://developer.apple.com/xcode/)'u yüklemeniz gerekeceğini unutmayın).
      - Tam platformlar arası Xamarin uygulamaları – **Android**, **IOS** ve **MacOS** platformları ' nı seçin.
   * **.NET Core uygulamaları** – **.NET Core** platformunu seçin.
   * **Web uygulamalarını ASP.NET Core** – **.net Core** platformunu seçin.
   * **platformlar arası Unity oyun geliştirme** – Mac için Visual Studio dışında hiçbir ek platform yüklenmesi gerekmez.

   Bu yükleme ekranında her bir bileşenin sürümü ve boyutu görüntülenir. Her bir bileşene tıklayarak bu bileşene ait bağımlılıkların bir listesini görüntüleyebilirsiniz (Android için), indirdiği ek paketler (.NET Core için) veya gerekli olan tüm ek uygulamaları (iOS ve macOS için) görüntüleyebilirsiniz:

   ![Android ek bağımlılıklar](media/installer-image6.png)

7. Seçiminizden memnun olduktan sonra yükleme işlemini başlatmak için yükleme **ve güncelleştirme** düğmesini seçin.

8. Yükleyici seçili öğelerin indirme ve yükleme işlemini başlatır:

   ![Yükleme başlatılıyor](media/installer-image7.png)

   ![Xamarin. Mac indiriliyor](media/installer-image8.png)

   ![Yükleme sonlandırılıyor](media/installer-image9.png)

9. Yüklemeyi tamamlaması gereken tek tek bileşenler için gerekli izinleri yükseltme istenebilir. Yükleme işlemine devam etmek için yönetici kimlik bilgilerinizi buraya girin:

   ![Yükleyiciye devam etmek için izinleri girin](media/installer-image10.png)

10. yükleme başarılı olduktan sonra **başlat**'a basarak Visual Studio uygulamalar geliştirmeye başlayabilirsiniz:

    ![Visual Studio’yu açın](media/installer-image11.png)

> [!NOTE]
> Özgün yükleme sırasında bir platform veya araç yüklememeyi seçtiyseniz (#6 adımında bunu seçerek), bileşenleri daha sonra eklemek istiyorsanız [yükleyiciyi](https://visualstudio.microsoft.com/vs/) yeniden çalıştırmalısınız.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>bir güvenlik duvarı veya proxy sunucusunun arkasında Mac için Visual Studio yüklemesi

bir güvenlik duvarının arkasında Mac için Visual Studio yüklemek için, yazılım için gerekli araçların ve güncelleştirmelerin indirilmelerine izin vermek üzere belirli uç noktalara erişilebilir hale gelmelidir.

Ağınızı aşağıdaki konumlara erişime izin verecek şekilde yapılandırın:

- [Visual Studio uç noktaları](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Sonraki adımlar

Mac için Visual Studio yükleme, uygulamalarınız için kod yazmaya başlayabilmeniz için izin verir. Aşağıdaki kılavuzlar, projelerinizi yazmanın ve dağıtmanın sonraki adımlarında size yol gösterecek şekilde sunulmaktadır.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Cihaz sağlama](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(uygulamanızı cihazda çalıştırmak için).

### <a name="android"></a>Android

1. [Xamarin Android SDK Manager 'ı kullanma](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Android SDK Emulator](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Cihazı Dağıtım için Ayarlama](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.net Core uygulamaları, ASP.NET Core web apps, Unity oyun geliştirme

Diğer Iş yükleri için [Iş yükleri](./asp-net-core.md) bölümüne bakın.

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017 'yi (Windows) yükler](/visualstudio/install/install-visual-studio)