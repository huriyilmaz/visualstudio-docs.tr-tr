---
title: Platformlar arası mobil geliştirme 'yi C++ | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: bda6d8e20064ab2197408db6b9a55a86325515e8
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846730"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>C++ ile platformlar arası mobil geliştirmeyi yükleme

Visual Studio 'da C++ , Windows Masaüstü uygulamaları, evrensel WINDOWS platformu (UWP) uygulamaları, Linux uygulamaları ve artık Android ve iOS uygulamaları oluşturmak için kullanabilirsiniz. İş yüküyle **Mobil C++ geliştirme** , Visual Studio 'da platformlar arası iOS, Android ve UWP Visual Studio şablonlarını içeren, yüklenebilir bir bileşen kümesidir. Hızlı bir şekilde kullanmaya başlamak için ihtiyacınız olan platformlar arası araçları ve SDK 'Ları yükler. Bu araçları, Visual Studio 'da, platformlar arası projelerinizi kolayca oluşturmak, düzenlemek, hatalarını ayıklamak ve test etmek için kullanabilirsiniz. Bu makalede, Visual Studio 'Yu C++ kullanarak platformlar arası uygulamalar geliştirmek için gereken araçların ve üçüncü taraf yazılımların nasıl yükleneceği açıklanır. Genel bakış için bkz. [Visual C++ platformlar arası mobil](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)

## <a name="requirements"></a>Gereksinimler

::: moniker range="vs-2017"

- Yükleme gereksinimleri için bkz. [Visual Studio ürün ailesi sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Windows 7 veya Windows Server 2008 R2 kullanıyorsanız, Windows Masaüstü uygulamaları, Android yerel etkinlik uygulamaları ve kitaplıkları ve iOS için uygulamalar ve kod kitaplıkları için kod geliştirebilirsiniz, ancak Windows Mağazası veya UWP uygulamaları kullanamazsınız.

::: moniker-end
::: moniker range=">=vs-2019"

- Yükleme gereksinimleri için bkz. [Visual Studio ürün ailesi sistem gereksinimleri](/visualstudio/releases/2019/system-requirements).

   > [!IMPORTANT]
   > Windows 7 veya Windows Server 2008 R2 kullanıyorsanız, Windows Masaüstü uygulamaları, Android yerel etkinlik uygulamaları ve kitaplıkları ve iOS için uygulamalar ve kod kitaplıkları için kod geliştirebilirsiniz, ancak Windows Phone veya UWP uygulamaları kullanamazsınız.

::: moniker-end

Belirli cihaz platformları için uygulamalar oluşturmak üzere bazı ek gereksinimler vardır:

- Android SDK ile birlikte gelen x86 Android öykünücüleri, Intel Hardware Accelerated Execution Manager (HAXM) gibi donanım hızlandırmasını kullanan bilgisayarlarda en iyi şekilde çalışır. Daha fazla bilgi için bkz. [öykünücü performansı Için donanım hızlandırma (Hyper-V & HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin&pivots=windows).

- İOS için kod oluşturma, bir Apple KIMLIĞI, bir iOS Geliştirici Programı hesabı ve [Xcode](https://developer.apple.com/xcode/) sürüm 10,2 veya sonrakı sürümlerini OS X Mavericks (sürüm 10,9) veya sonraki sürümlerde çalıştıran bir Mac bilgisayar gerektirir. Yükleme adımlarının bağlantısı için bkz. [iOS Için yükleme araçları](#install-tools-for-ios).

- Windows Phone Öykünücüler, Hyper-V ' y i çalıştıran bir bilgisayar gerektirir. Öykünücüleri yüklemeden ve çalıştırmadan önce Windows 'daki Hyper-V özelliğinin etkinleştirilmesi gerekir. Daha fazla bilgi için öykünücü [sistem gereksinimlerine](system-requirements-for-the-visual-studio-emulator-for-android.md)bakın.

## <a name="get-the-tools"></a>Araçları edinin

İle C++ mobil geliştirme, Visual Studio Community, Professional ve Enterprise sürümlerinde kullanılabilir. Visual Studio 'yu almak için [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin. Platformlar arası mobil geliştirme araçları, Visual Studio 2015 ' den itibaren kullanılabilir.

## <a name="install-the-tools"></a>Araçları yükler

Visual Studio yükleyicisi iş yüküne  **C++ sahip bir mobil geliştirme** içerir. Bu iş yükü, C++ Visual Studio 'da Android ve iOS geliştirmesi için gereken dil araçlarını, şablonları ve bileşenleri yüklüyor. Android derlemeleri ve hata ayıklama için gereken GCC ve Clang aracı kümelerini, Android SDK ve bileşenlerini iOS geliştirmesi için bir Mac ile iletişim kuracak şekilde içerir. Ayrıca iOS ve Android uygulama geliştirmeyi desteklemek için gereken diğer tüm üçüncü taraf araçları ve yazılım geliştirme setleri de yüklenir. Bu üçüncü taraf araçların çoğu, Android Platform desteği için gereken açık kaynaklı yazılımdır.

- Android platformunu hedefleyen kod derlemek C++ C++ Için Android yerel geliştirme seti (NDK), Apache Ant ve Android geliştirme araçları gerekir.

- Google Android Emulator ve Intel Hardware Accelerated Execution Manager (HAXM) isteğe bağlıdır, ancak önerilir. (Intel HAXM sürücüleri yalnızca Intel işlemcilerde çalışır ve Hyper-V dahil bazı VM 'lerle uyumsuzdur.) Doğrudan bir Android cihazında geliştirme ve hata ayıklama yapabilirsiniz, ancak hata ayıklama için masaüstünüzde bir öykünücü kullanmak genellikle daha kolay olur.

- C++iOS platformunu hedefleyen kodu derlemek C++ için iOS geliştirme araçları gerekir.

> [!NOTE]
> Visual Studio 2015 kullanıyorsanız bkz. [platformlar arası mobil geliştirme Için C++ Visual Install (Visual Studio 2015)](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015)

### <a name="install-the-mobile-development-with-c-workload"></a>C++ İş yüküyle mobil geliştirme 'yi yükler

1. **Başlangıç** menüsünden **Visual Studio yükleyicisi** çalıştırın.

1. Visual Studio 'Yu zaten yüklediyseniz, değiştirmek istediğiniz Visual Studio 'nun yüklü sürümü için **Değiştir** düğmesini seçin. Aksi halde, Visual Studio 'Yu yüklemek için **Install** ' ı seçin.

1. **İş yükleri** sekmesi seçili olduğunda aşağı kaydırın ve Visual Studio yükleyicisi iş yüküyle **Mobil geliştirmeyi C++**  seçin. Bu iş yükü seçildiğinde, geliştirme için C++ gereken diğer bileşenler de seçilidir. Aynı anda yüklemek için diğer iş yüklerini ve ayrı bileşenleri de seçebilirsiniz. UWP 'yi de hedefleyen platformlar arası kod oluşturmak için **Evrensel Windows platformu geliştirme** iş yükünü seçin.

1. **Yükleme ayrıntıları** bölmesinde, **C++ile mobil geliştirme**' ı genişletin. **Isteğe bağlı** bölümünde, NDK, Google Android Emulator, Intel Hardware Accelerated Execution Manager ve IncrediBuild Build Acceleration aracının ek sürümlerini seçebilirsiniz.

1. Varsayılan olarak, bir veya daha fazla Android SDK Kurulum bileşeni iş yüküne dahildir. Android SDK ek sürümleri mevcuttur. Yüklemenize bir tane eklemek için, **tek tek bileşenler** sekmesini seçin, sonra seçiminizi yapmak için SDK 'lar **, kitaplıklar ve çerçeveler** bölümüne gidin.

1. İş yüküne ve seçtiğiniz diğer iş yüklerinize ve isteğe bağlı bileşenlere **sahip C++ mobil geliştirmeyi** yüklemek için **Değiştir** veya **yüklensin** düğmesini seçin.

   Yükleme tamamlandığında, yükleyiciyi kapatın ve bilgisayarınızı yeniden başlatın. Üçüncü taraf bileşenleri için bazı kurulum eylemleri, bilgisayar yeniden başlatılana kadar etkili olmayacaktır.

   > [!IMPORTANT]
   > Her şeyin doğru şekilde yüklendiğinden emin olmak için yeniden başlatmanız gerekir.

1. Visual Studio'yu açın.

## <a name="install-tools-for-ios"></a>İOS için araçları yükler

İOS kodu düzenlemek, hatalarını ayıklamak ve iOS simülatörü veya bir iOS cihazına dağıtmak için Visual Studio 'Yu kullanabilirsiniz. Ancak lisanslama kısıtlamaları nedeniyle, kod bir Mac üzerinde uzaktan oluşturulmalıdır. Visual Studio kullanarak iOS uygulamaları derlemek ve çalıştırmak için, Mac 'inizde uzak aracıyı ayarlamanız ve yapılandırmanız gerekir. Ayrıntılı yükleme yönergeleri, Önkoşullar ve yapılandırma seçenekleri için bkz. [iOS kullanarak derlemek için araçları yükleme ve yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md). İOS için derleme yapıyorsanız, bu adımı atlayabilirsiniz.

## <a name="install-or-update-dependencies-manually"></a>Bağımlılıkları el ile yükler veya güncelleştirir

Visual Studio yükleyicisini kullanarak bir veya daha fazla üçüncü taraf bağımlılığı yüklememeyi seçerseniz, iş yüküyle (veya Visual Studio 2015, görsel C++ mobil geliştirme seçeneği) **Mobil geliştirmeyi C++**  yüklediğinizde, [araçları yükleme](#install-the-tools)adımlarını kullanarak bunları daha sonra yükleyebilirsiniz. Visual Studio Yükleyicisi, en son üçüncü taraf bileşenlerini yüklemek için düzenli olarak güncelleştirilir. Bu uygulamayı, güncelleştirilmiş SDK 'Ları ve NDKs 'leri yüklemek için kullanabilirsiniz. Ayrıca, bunları Visual Studio 'dan bağımsız olarak yükleyebilir veya güncelleştirebilirsiniz.

SDK 'yı güncelleştirmek ve isteğe bağlı araçları ve ek API düzeylerini yüklemek için Android SDK dizininde SDK Manager uygulamasını çalıştırabilirsiniz. SDK Yöneticisi uygulamasını çalıştırmak için **yönetici olarak çalıştır** kullanmadığınız sürece güncelleştirmeler yüklenemeyebilir. Android uygulaması oluşturma sorunları yaşıyorsanız, yüklü SDK 'larınıza yönelik güncelleştirmeler için SDK Yöneticisi ' ne bakın.

Android SDK gelen bazı Android öykünücülerini kullanmak için donanım hızlandırmayı ayarlamanız gerekebilir. Daha fazla bilgi için bkz. [öykünücü performansı Için donanım hızlandırma (Hyper-V & HAXM)](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

Çoğu durumda, Visual Studio yüklediğiniz üçüncü taraf yazılım için konfigürasyonları algılayabilir ve yükleme yollarını iç ortam değişkenlerine karşı korur. Visual Studio IDE 'de bu platformlar arası geliştirme araçlarının varsayılan yollarını geçersiz kılabilirsiniz.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Üçüncü taraf araçların yollarını ayarlamak için

1. Visual Studio menü çubuğunda **araçlar** > **Seçenekler**' i seçin.

1. **Seçenekler** iletişim kutusunda, **Android** > **platformlar arası** > **C++** seçin.

   ![Android araç yolu seçenekleri](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Bir araç tarafından kullanılan yolu değiştirmek için yolun yanındaki onay kutusunu işaretleyin ve metin kutusunda klasör yolunu düzenleyin. Klasörü seçmek için bir **Konum Seç** iletişim kutusunu açmak için de ( **...** ) düğmesini kullanabilirsiniz.

1. Özel araç klasörü konumlarını kaydetmek için **Tamam ' ı** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [İOS kullanarak derlemek için Araçlar yükleyip yapılandırma](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ platformlar arası mobil](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)
