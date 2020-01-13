---
title: Android için Visual Studio öykünücüsü | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7bda9882a8f46f3b32c658db952a2eaf73d3fb7
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916466"
---
# <a name="visual-studio-emulator-for-android"></a>Android için Visual Studio Öykünücüsü

Android için Visual Studio öykünücüsü, Android cihazına öykünen bir masaüstü uygulamasıdır. Fiziksel bir cihaz olmadan Android uygulamalarında hata ayıklamanıza ve test yapabilmeniz için sanallaştırılmış bir ortam sağlar. Ayrıca, uygulama prototiplerinizi için yalıtılmış bir ortam sağlar.

> [!IMPORTANT]
> Çoğu senaryoda, Android için Visual Studio öykünücüsü yerine Google Android öykünücüsü kullanımı önerilir:
> - Android için Visual Studio öykünücüsü, Visual Studio 2015 sonrasında desteklenmez.
> - Android sürüm 6,0 ' den sonraki öykünücü görüntüleri, Android için Visual Studio öykünücüsü 'nde kullanılamaz.
> - Google Android Emulator artık [Hyper-V](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration#accelerating-with-hyper-v)desteklemektedir.
> - Apache Cordova için Visual Studio Araçları Google Android Emulator ile birlikte kullanılabilir. Daha fazla bilgi için bkz. [Android 'de Apache Cordova uygulamanızı çalıştırma](/visualstudio/cross-platform/tools-for-cordova/run-your-app/run-app-android#google-android-emulator) (artık bu makalede açıklandığı gibi Hyper-V ' ı devre dışı bırakmanız gerektiğini unutmayın).
>
> Google Android Emulator yapılandırma ve kullanma hakkında daha fazla bilgi için, bkz. [Android Emulator kurulum](/xamarin/android/get-started/installation/android-emulator/).

 Android için Visual Studio öykünücüsü, gerçek bir cihaza benzer bir performans sağlamak üzere tasarlanmıştır. Ancak uygulamanızı yayımlamadan önce, uygulamanızı fiziksel bir cihazda sınamanızı öneririz.

 Uygulamanızı, Android için Visual Studio öykünücüsü tarafından desteklenen Android platformları, ekran çözünürlükleri ve diğer donanım özellikleri için benzersiz bir cihaz profilinde test edebilirsiniz.

## <a name="Installing"></a>Yükleme ve kaldırma
 Yükleme

 Android için Visual Studio öykünücüsü, Visual Studio 'da bulunan platformlar arası araçların bir bileşenidir ve platformlar arası mobil geliştirme, ortak araçlar ve yazılım geliştirme setleri ' ni seçtiğinizde özel bir Visual Studio Kurulumu sırasında yüklenir. ve ardından Android için Visual Studio öykünücüsü.

 Kaldırıyor

 Denetim Masası 'ndaki Program Ekle/Kaldır 'ı kullanarak Android için Visual Studio öykünücüsü ' nü kaldırabilirsiniz.

> [!NOTE]
> Visual Studio 'Yu kaldırmak, öykünücüyü kaldırmaz. Öykünücüyü ayrı olarak kaldırmanız gerekir.

 Android için Visual Studio öykünücüsü 'nü kaldırdığınızda, öykünücü için oluşturulan Hyper-V sanal Ethernet bağdaştırıcıları otomatik olarak kaldırılmaz. Hyper-V Yöneticisi 'Ni açıp öykünücü VHD görüntülerinden birini seçerek, ağ sekmesini seçerek ve bu sekmede görünen anahtarların her biri için **Kaldır** ' ı seçerek bu sanal bağdaştırıcıları (kullanımda değilse) el ile kaldırabilirsiniz.

## <a name="Requirements"></a>Sistem gereksinimleri ve geri uyumluluk
 Android için Visual Studio öykünücüsü donanım, yazılım ve yapılandırma gereksinimleriyle ilgili önemli bilgiler için aşağıdaki konuya bakın.

- [Android için Visual Studio öykünücüsü sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

  Android için Visual Studio öykünücüsü, Visual Studio 2015 gerektirir; Visual Studio 'nun önceki sürümleriyle geriye dönük olarak uyumlu değildir.

  Öykünücünün yeni sürümleri eski sürümlerin üzerine yüklenir (ve bazı durumlarda eski görüntülerin yerini alarak, bu görüntülerde yüklü ayarları, uygulamaları ve dosyaları atarak).

## <a name="Networking"></a>Android için Visual Studio öykünücüsü 'nde ağ oluşturma
 Android için Visual Studio öykünücüsü ağ bağlantısı, bu özelliklerle bir masaüstü bilgisayar bağlantısı gibi davranır:

- Öykünücü ağ üzerinde kendi IP adresine sahip ayrı bir cihaz olarak görünür.

- Öykünücü ile henüz yüklenmemiş ek bir ağ yazılımı gerektirmez.

- Bir Windows etki alanına katılmadı.

  Öykünücü ağ bağlantısının yeteneklerini anlamak için, Android telefonunuzdaki bir Wi-Fi bağlantısına aynı ağa benzer şekilde göz önünde bulundurun. Telefonunuzdaki çalışan bir uygulama, Wi-Fi bağlantısı üzerinden bir ağ kaynağına erişebildi, öykünücü üzerinde çalışan bir uygulama aynı ağ kaynağına da erişebilir.

  Ağ gereksinimleriyle ilgili daha fazla bilgi için bkz. [Android Için Visual Studio öykünücüsü Için sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  Ağ sorunlarını giderme hakkında bilgi için bkz. [Android Için Visual Studio öykünücüsü sorunlarını giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

## <a name="Configuring"></a>Android için Visual Studio öykünücüsü 'nü yapılandırma
 Android uygulamanızı kademelendirme çok sayıda Android donanımında uyumluluk için test etmek zor olabilir. Pazardaki Android telefonlar ve tabletler, çok çeşitli sürüm ve ekran boyutlarına sahiptir ve birçok farklı donanım yapılandırmasında (RAM, CPU, mimari, vb.) gelir. Android için Visual Studio öykünücüsü, cihaz profillerini kullanarak bunu basitleştirir. Cihaz profillerimiz, Samsung, Motorola, Sony, LG ve daha fazlasına ait cihazlar dahil olmak üzere pazardaki en popüler donanımı temsil etmektedir.

 Visual Studio 2015 ' de, öykünücü yöneticisi 'Ni kullanarak cihaz profillerini yükleyebilir, kaldırabilir ve başlatabilirsiniz. **Araçlar**' ı ve ardından **Android Için Visual Studio öykünücüsü**' nü seçerek öykünücü yöneticisine erişin.

 ![Android için Visual Studio öykünücüsü yöneticisi](../cross-platform/media/android_emu_manager.png "Android_Emu_Manager")

 Varsayılan olarak, beyaz metin ve simgelerle gösterildiği gibi önceden yüklenmiş dört cihaz profili (KitKat ve Lollipop telefonu/5 "ve tablet/7" yapılandırması) vardır. **Profil yükleme** düğmesini seçinceye ve yükleme tamamlanıncaya kadar listedeki diğer profiller gri görünür. Listeyi API düzeyine göre filtreleyebilir ve tam yapılandırma ayrıntılarını görüntülemek için bir profilin sağ alt tarafındaki Ayrıntılar okuna tıklayabilirsiniz.

 Hedeflemek istediğiniz profil kümesini yükledikten sonra, yeşil **yürütme** düğmesine basarak bu yeni profilleri doğrudan yöneticisinden başlatabilirsiniz. Ayrıca, Visual Studio platformlar arası mobil proje türündeki hata ayıklama hedefi açılan menüsünde de görüntülenir.

## <a name="FeaturesTest"></a>Öykünücüde test edebilirsiniz özellikleri
 Öykünücüde test edebilirsiniz özellikleri hakkında ayrıntılı bilgi için bu [blog gönderisine](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/)bakın.

## <a name="FeaturesNonTest"></a>Öykünücüde test etemiyorum Özellikler
 Aşağıdaki liste, öykünücü içinde test **etemen** Android platformunun özelliklerini açıklar. Bu özellikleri fiziksel bir cihazda test etmeniz gerekir.

- Pusula

- Jiroskop

- Titreşim denetleyicisi

- Parlaklığı. Öykünücünün parlaklık düzeyini değiştirmek, cihazın ekranınızda görünme biçimini görsel olarak etkilemez.

## <a name="Support"></a>Destek kaynakları
 Ana bilgisayarınızın sistem gereksinimlerini karşıladığından ve bu sorun giderme Kılavuzu'nda ele alınmayan bir sorunla karşılaşırsanız varsa:

- [Android-Emulator](https://stackoverflow.com/questions/tagged/android-emulator) ve Visual-Studio etiketini kullanarak StackOverflow 'de soru sorun.

- Visual Studio'da veya öykünücü Yöneticisi'nde gönderme gülümseme aracını kullanarak bir sorun bildirin.

## <a name="see-also"></a>Ayrıca bkz.
 Android için Visual Studio öykünücüsü için [sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) [Android Için Visual Studio öykünücüsü sorunlarını giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
