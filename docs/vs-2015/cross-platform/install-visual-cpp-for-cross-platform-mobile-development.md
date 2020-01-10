---
title: Platformlar arası C++ mobil geliştirme için Visual 'i yükler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 70f1266581bb633086fa33a28b43e04befc7e6f9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844324"
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Çoklu Platform Mobil Uygulama Geliştirme için Visual C++’ı yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platformlar C++ arası mobil geliştirme için görsel] (https://go.microsoft.com/fwlink/p/?LinkId=536383), visual Studio 2015 ' in yüklenebilir bir bileşenidir. Platformlar arası Visual Studio şablonları içerir ve platformlar arası araçları ve SDK 'larını, kolayca kullanmaya başlamak için, onları kendiniz bulmaya, indirmeye ve yapılandırmaya gerek kalmadan yükler. Çoklu platform projelerini kolayca oluşturmak, düzenlemek, hatalarını ayıklamak ve test etmek için Visual Studio 'da bu araçları kullanabilirsiniz. Bu konu başlığında, Visual Studio kullanarak platformlar arası uygulamalar geliştirmek için gereken araçların ve üçüncü taraf yazılımların nasıl yükleneceği açıklanır. Bileşene genel bakış için bkz. [Visual C++ platformlar arası mobil](https://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [Gereksinimler](#Requirements)   
 [Araçları  alın](#GetTheTools)  
 [Araçları  yüklemesi](#InstallTheTools)  
 [İOS  için araçları yükler](#InstallForiOS)  
 [Bağımlılıkları el ile yükler veya güncelleştirir](#ThirdParty)  
  
## <a name="Requirements"></a> Gereksinimleri  
  
- Yükleme gereksinimleri için bkz. [Visual Studio 2015 sistem gereksinimleri](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
  > [!IMPORTANT]
  > Windows 7 veya Windows Server 2008 R2 kullanıyorsanız, klasik Windows uygulamaları, Android yerel etkinlik uygulamaları ve kitaplıkları ve iOS için uygulamalar ve kod kitaplıkları için kod geliştirebilirsiniz, ancak Windows Mağazası veya Evrensel Windows uygulamaları kullanamazsınız.  
  
  Belirli cihaz platformları için uygulamalar oluşturmak üzere bazı ek gereksinimler vardır:  
  
- Windows Phone Öykünücüler ve Android için Microsoft Visual Studio Öykünücüsü Hyper-V ' y i çalıştırabilen bir bilgisayar gerektirir. Öykünücüleri yüklemeden ve çalıştırmadan önce Windows 'daki Hyper-V özelliğinin etkinleştirilmesi gerekir. Daha fazla bilgi için öykünücü [sistem gereksinimlerine](https://msdn.microsoft.com/4d5bb438-231a-4cd2-84b7-e9660b0e3baf)bakın.  
  
- Android SDK ile birlikte gelen x86 Android öykünücüleri, Intel HAXM sürücüsünü çalıştırabilirler bilgisayarlarda en iyi şekilde çalışır. Bu sürücü, VT-x ile bir Intel x64 işlemcisi ve devre dışı bırakma bit desteğini gerektirir. Daha fazla bilgi için bkz. [ıntel® Hardware Accelerated Execution Manager Için yükleme yönergeleri-Microsoft Windows](https://github.com/intel/haxm).  
  
- İOS için kod oluşturma, bir Apple KIMLIĞI, bir iOS Geliştirici Programı hesabı ve [Xcode 6](https://go.microsoft.com/fwlink/p/?LinkId=536387) veya sonraki sürümleri Işletim sistemi X Mavericks veya üzeri sürümlerde çalışabilen bir Mac bilgisayar gerektirir. Basit yükleme adımları için bkz. [iOS Için yükleme araçları](#InstallForiOS).  
  
## <a name="GetTheTools"></a>Araçları edinme  
 Platformlar C++ arası mobil geliştirme Için Visual Studio Community, Professional ve Enterprise sürümlerinde yer alan yüklenebilir bir bileşendir. Visual Studio 'yu almak için [Visual studio 2015 İndirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin ve güncelleştirme 2 veya sonraki sürümüyle visual Studio 2015 ' yi indirin.  
  
## <a name="InstallTheTools"></a>Araçları yükler  
 Visual Studio 2015 için yükleyici, platformlar arası mobil geliştirme için Visual C++ yükleme seçeneği içerir. Bu, gerekli C++ dil araçlarını, Visual Studio için şablonları ve bileşenleri, Android derlemeleri ve hata ayıklama için gereken GCC ve Clang araç kümelerini ve iOS geliştirmesi Için bir Mac ile iletişim kurmayı sağlar. Ayrıca iOS ve Android uygulama geliştirmeyi desteklemek için gereken tüm üçüncü taraf araçları ve yazılım geliştirme setleri de yüklenir. Bu üçüncü taraf araçların çoğu, Android Platform desteği için gereken açık kaynaklı yazılımdır.  
  
- Android platformunu hedefleyen kod derlemek C++ Için Android yerel geliştirme SETI (NDK) gereklidir.  
  
- Android SDK, Apache Ant ve Java SE Development Kit Android derleme işlemi için gereklidir.  
  
- Android için Microsoft Visual Studio Öykünücüsü, kodunuzun sınanması ve hata ayıklaması için kullanışlı, isteğe bağlı bir yüksek performanslı öykünücü.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Platformlar arası mobil C++ geliştirme ve üçüncü taraf araçları için Visual yüklemek üzere  
  
1. [Araçları edinme](#GetTheTools)bağlantısındaki bağlantıyı Izleyerek Indirdiğiniz Visual Studio 2015 yükleyicisini çalıştırın. İsteğe bağlı bileşenleri yüklemek için yükleme türü olarak **özel** ' i seçin. Yüklenecek isteğe bağlı bileşenleri seçmek için **İleri** ' yi seçin.  
  
2. Özellikleri Seç bölümünde, **platformlar arası mobil geliştirme** ' ı genişletin **ve C++ görsel mobil geliştirme**' yi inceleyin.  
  
     ![Visual C&#43; &#43; mobil geliştirme 'yi seçin](../cross-platform/media/cppmdd-install-vcmdd.png "CPPMDD_Install_VCMDD")  
  
     Varsayılan olarak, **Visual C++ mobil geliştirme**' yi seçtiğinizde, **programlama dilleri** seçeneği **C++görseli**yükleyecek şekilde ayarlanır ve **ortak araçlar ve yazılım geliştirme setleri** seçenekleri gereken üçüncü taraf bileşenleri yüklenmek üzere ayarlanır. İhtiyacınız varsa ek bileşenleri seçebilirsiniz. Varsayılan olarak **Android için Microsoft Visual Studio öykünücüsü** de seçilidir. Zaten yüklü olan bileşenler listede etkin değil olarak görünür.  
  
     Evrensel Windows uygulamaları oluşturmak ve bunlar arasında, Android ve iOS projeleriniz arasında kod paylaşmak için, **seçme özellikleri**' nde **Windows ve Web geliştirme** ' yi genişletin ve **Evrensel Windows uygulaması geliştirme araçları**' nı işaretleyin. Evrensel Windows uygulamaları oluşturmayı planlamıyorsanız, bu seçeneği atlayabilirsiniz.  
  
     Devam etmek için **İleri**’yi seçin.  
  
3. Üçüncü taraf bileşenlerinin kendi lisans koşulları vardır. Lisans koşullarını her bileşenin yanındaki **Lisans koşulları** bağlantısını seçerek görüntüleyebilirsiniz. Bileşenleri eklemek ve platformlar arası mobil geliştirme Için Visual Studio 'Yu ve C++ Visual Studio 'yu yüklemek için yüklemeyi seçin.  
  
4. Yükleme tamamlandığında, yükleyiciyi kapatın ve bilgisayarınızı yeniden başlatın. Üçüncü taraf bileşenleri için bazı kurulum eylemleri, bilgisayar yeniden başlatılana kadar etkili olmaz.  
  
    > [!IMPORTANT]
    > Her şeyin doğru şekilde yüklendiğinden emin olmak için yeniden başlatmanız gerekir.  
  
     Android için Microsoft Visual Studio Öykünücüsü bileşeni yüklenemediğinde, bilgisayarınızda Hyper-V etkinleştirilmemiş olabilir. Hyper-V ' i etkinleştirmek için **Windows özelliklerini aç veya kapat** Denetim Masası uygulamasını kullanın ve ardından Visual Studio yükleyicisi 'ni yeniden çalıştırın.  
  
    > [!NOTE]
    > Bilgisayarınız veya Windows sürümünüz Hyper-V ' yi desteklemiyorsa Android için Microsoft Visual Studio Öykünücüsü bileşenini kullanamazsınız. Windows Home Edition, Hyper-V desteğini içermez.  
  
5. Visual Studio'yu açın. Visual Studio 'Yu ilk kez çalıştırırsanız, yapılandırmak ve oturum açmak biraz zaman alabilir. Visual Studio hazırlanıyor, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**, **güncelleştirmeler**' i seçin. Platformlar arası mobil geliştirme C++ Için Visual Studio güncelleştirmeleri veya Android için Microsoft Visual Studio öykünücüsü için kullanılabilir.  
  
## <a name="InstallForiOS"></a>İOS için araçları yükler  
 İOS kodu ile iOS C++ simülatörünü veya bir iOS cihazını düzenlemek, hatalarını ayıklamak ve dağıtmak için Visual, platformlar arası mobil geliştirme için kullanabilirsiniz, ancak lisanslama kısıtlamalarından dolayı kodun bir Mac üzerinde uzaktan oluşturulması gerekir. Visual Studio kullanarak iOS uygulamaları derlemek ve çalıştırmak için, Mac 'inizde uzak aracıyı ayarlamanız ve yapılandırmanız gerekir. Ayrıntılı yükleme yönergeleri, Önkoşullar ve yapılandırma seçenekleri için bkz. [iOS kullanarak derlemek Için araçları yükleme ve yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md). İOS için derleme yapıyorsanız, bu adımı atlayabilirsiniz.  
  
## <a name="ThirdParty"></a>Bağımlılıkları el ile yükler veya güncelleştirir  
 Visual Studio yükleyicisi 'ni kullanarak bir veya daha fazla üçüncü taraf bağımlılığı yüklememeye karar verirseniz, Visual C++ mobil geliştirme seçeneğini yüklediğinizde, [araçları yükleme](#InstallTheTools)adımlarını kullanarak bunları daha sonra yükleyebilirsiniz. Ayrıca, bunları Visual Studio 'dan bağımsız olarak yükleyebilir veya güncelleştirebilirsiniz.  
  
> [!CAUTION]
> Bağımlılıkları Java dışında herhangi bir sıraya yükleyebilirsiniz. Android SDK yüklemeden önce JDK 'yi yükleyip yapılandırmanız gerekir.  
  
 Aşağıdaki bilgileri okuyun ve bağımlılıkları el ile yüklemek için bu bağlantıları kullanın.  
  
- [Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
   Varsayılan olarak yükleyici, Java araçlarını C:\Program Files (x86) \Java' ye yerleştirir.  
  
- [Android SDK](https://developer.android.com/sdk/index.html#Other)  
  
   Yükleme sırasında, API 'Leri önerilen şekilde güncelleştirin. Android 5,0 Lollipop (API düzeyi 21) için en azından SDK 'nın yüklü olduğundan emin olun. Varsayılan olarak, yükleyici Android SDK C:\Program Files (x86) \Android\android-SDK. 'e yerleştirir.  
  
   SDK 'yı güncelleştirmek ve isteğe bağlı araçları ve ek API düzeylerini yüklemek için Android SDK dizininde SDK Manager uygulamasını çalıştırabilirsiniz. SDK Yöneticisi uygulamasını çalıştırmak için **yönetici olarak çalıştır** kullanmadığınız sürece güncelleştirmeler yüklenemeyebilir. Android uygulaması oluşturma sorunları yaşıyorsanız, yüklü SDK 'larınıza yönelik güncelleştirmeler için SDK Yöneticisi ' ne bakın.  
  
   Android SDK ile birlikte gelen bazı Android öykünücülerini kullanmak için, isteğe bağlı Intel HAXM sürücülerini yüklemelisiniz. Intel HAXM sürücülerini başarılı bir şekilde yüklemek için Hyper-V özelliğini Windows 'dan kaldırmanız gerekebilir. Windows Phone öykünücüleri ve Android için Microsoft Visual Studio Öykünücüsü kullanmak için Hyper-V özelliğini geri yüklemeniz gerekir.  
  
- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)  
  
   Varsayılan olarak, yükleyici Android NDK 'yi C:\ProgramData\Microsoft\AndroidNDK. 'e koyar. NDK yüklemesini güncelleştirmek için Android NDK 'yi indirebilir ve yükleyebilirsiniz.  
  
- [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
   Varsayılan olarak, yükleyici C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ Apps 'e Apache Ant koyar.  
  
- [Android için Microsoft Visual Studio Öykünücüsü](https://visualstudio.microsoft.com/vs/msft-android-emulator/)  
  
   Android için Microsoft Visual Studio Öykünücüsü Visual Studio Galerisi ' nden yükleyebilir ve güncelleştirebilirsiniz.  
  
  Çoğu durumda, Visual Studio yüklediğiniz üçüncü taraf yazılım için konfigürasyonları algılayabilir ve yükleme yollarını iç ortam değişkenlerine karşı korur. Visual Studio IDE 'de bu platformlar arası geliştirme araçlarının varsayılan yollarını geçersiz kılabilirsiniz.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>Üçüncü taraf araçların yollarını ayarlamak için  
  
1. Visual Studio menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.  
  
2. **Seçenekler** iletişim kutusunda, **platformlar arası**' **C++** ı genişletin ve **Android**' i seçin.  
  
     ![Android araç yolu seçenekleri](../cross-platform/media/cppmdd-options-android.PNG "CPPMDD_Options_Android")  
  
3. Bir araç tarafından kullanılan yolu değiştirmek için yolun yanındaki onay kutusunu işaretleyin ve metin kutusunda klasör yolunu düzenleyin. Klasörü seçmek için bir **Konum Seç** iletişim kutusunu açmak için de ( **...** ) düğmesini kullanabilirsiniz.  
  
4. Özel araç klasörü konumlarını kaydetmek için **Tamam ' ı** seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İOS  kullanarak derlemek Için Araçlar yükleyip yapılandırın](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
 [Visual C++ platformlar arası mobil](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)
