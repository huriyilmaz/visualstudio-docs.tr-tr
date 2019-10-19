---
title: Android ve iOS üzerinde OpenGL ES uygulaması oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: a15902278e9a73488b315729a2db6e8fb5d53935
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588918"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Android ve iOS üzerinde OpenGL ES uygulaması oluşturma

İOS uygulamaları ve ortak kod paylaşan android uygulamalar için Visual Studio çözümleri ve projeleri oluşturabilirsiniz. Bu makale, hem basit bir iOS uygulaması hem de Android yerel etkinlik uygulaması oluşturan bir çözüm şablonunda size rehberlik eder. Uygulamalar, her C++ platformda aynı animasyonlu döndürme küpünü göstermek IÇIN OpenGL ES kullanan ortak koda sahiptir. OpenGL ES (katıştırılmış sistemler veya GLES için OpenGL), birçok mobil cihazda desteklenen 2B ve 3B bir grafik API 'sidir.

## <a name="requirements"></a>Gereksinimler

İOS ve Android için bir OpenGL ES uygulaması oluşturabilmeniz için önce tüm sistem gereksinimlerini karşıladığınızdan emin olun. Henüz yapmadıysanız, Visual Studio Yükleyicisi C++ iş yüküyle mobil geliştirmeyi yükleyebilirsiniz. OpenGL ES şablonlarını almak ve iOS için derlemek için isteğe bağlı C++ iOS geliştirme araçları 'nı dahil edin. Android için derlemek için Android geliştirme araçları C++ 'nı ve gerekli üçüncü taraf araçlarını yüklemek Için: Android NDK, Apache Ant ve Google Android Emulator. Intel platformlarında daha iyi öykünücü performansı için, ayrıca Intel Hardware Accelerated Execution Manager (HAXM) yüklemenizi öneririz. Ardından, Intel HAXM ve Android Emulator sisteminizde çalıştırılacak şekilde yapılandırın. Daha fazla bilgi ve ayrıntılı yönergeler için, bkz. [ile C++platformlar arası mobil geliştirmeyi çalıştırma ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md).

İOS uygulamasını derlemek ve test etmek için, yükleme yönergelerine göre ayarlanmış bir Mac bilgisayar olması gerekir. İOS geliştirme için ayarlama hakkında daha fazla bilgi için bkz. [iOS kullanarak derlemek için araçları kurma ve yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="create-a-new-opengles-application-project"></a>Yeni bir OpenGLES uygulama projesi oluşturma

Bu öğreticide, önce yeni bir OpenGL ES uygulama projesi oluşturursunuz. ardından, varsayılan uygulamayı bir Android öykünücüsünde oluşturup çalıştırın. Ardından, iOS için uygulamayı derleyin ve uygulamayı bir iOS cihazında çalıştırırsınız.

::: moniker range="vs-2017"

1. Visual Studio 'da **dosya** > **Yeni** > **Proje**' yi seçin.

1. **Yeni proje** iletişim kutusunda, **Şablonlar**altında  **C++ görsel** > **platformlar arası**' ı seçin ve ardından **OpenGLES uygulaması (Android, iOS)** şablonunu seçin.

1. Uygulamaya *Myopengtasapp*gibi bir ad verin ve ardından **Tamam**' ı seçin.

   ![Yeni OpenGLES uygulama projesi](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")

   Visual Studio yeni çözümü oluşturur ve Çözüm Gezgini açar.

   ![Çözüm Gezgini Myopengtasapp](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio 'da **dosya** > **Yeni** > **Proje**' yi seçin.

1. **Yeni proje oluştur** Iletişim kutusunda **OpenGLES uygulaması (Android, iOS)** şablonunu seçin ve ardından **İleri**' yi seçin.

1. **Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı**alanına *Myopengtasapp* gibi bir ad girin ve ardından **Oluştur**' u seçin.

   Visual Studio yeni çözümü oluşturur ve Çözüm Gezgini açar.

   ![Çözüm Gezgini Myopengtasapp](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

::: moniker-end

Yeni OpenGL ES uygulama çözümü, üç kitaplık projesi ve iki uygulama projesi içerir. Kitaplıklar klasörü, Paylaşılan koda başvuran, paylaşılan bir kod projesi ve platforma özel iki proje içerir:

- `MyOpenGLESApp.Android.NativeActivity`, uygulamanızı Android 'de yerel bir etkinlik olarak uygulayan başvuruları ve birleştirici kodu içerir. Birleştirici kodundan gelen giriş noktaları, `MyOpenGLESApp.Shared` ortak paylaşılan kodu içeren *Main. cpp*' de uygulanır. Önceden derlenmiş üstbilgiler *pch. h*içinde. Bu yerel etkinlik uygulaması projesi, `MyOpenGLESApp.Android.Packaging` projesi tarafından çekilen paylaşılan bir kitaplık ( *. so*) dosyasında derlenir.

- `MyOpenGLESApp.iOS.StaticLibrary`, `MyOpenGLESApp.Shared` paylaşılan kodu içeren bir iOS statik kitaplık ( *. a*) dosyası oluşturur. @No__t_0 projesi tarafından oluşturulan uygulamayla bağlantılıdır.

- `MyOpenGLESApp.Shared` platformlar arasında çalışacak paylaşılan kodu içerir. Platforma özgü kodun koşullu derlenmesi için Önişlemci makrolarını kullanır. Paylaşılan kod hem `MyOpenGLESApp.Android.NativeActivity` hem de `MyOpenGLESApp.iOS.StaticLibrary` proje başvurusu tarafından alınır.

Çözüm, Android ve iOS platformları için uygulamalar oluşturmak üzere iki projeye sahiptir:

- `MyOpenGLESApp.Android.Packaging`, bir Android cihazında veya öykünücüsünde dağıtım için *. apk* dosyası oluşturur. Bu dosya, bildirim özelliklerini ayarladığınız kaynakları ve AndroidManifest. xml dosyasını içerir. Ayrıca, ant yapı sürecini denetleyen *Build. xml* dosyasını da içerir. Varsayılan olarak, doğrudan Visual Studio 'dan dağıtılabilmesi ve çalıştırmak için başlangıç projesi olarak ayarlanır.

- `MyOpenGLESApp.iOS.Application`, `MyOpenGLESApp.iOS.StaticLibrary` içindeki C++ statik kitaplık koduna bağlanan bir iOS uygulaması oluşturmak için kaynaklar ve amaç-C birleştirici kodunu içerir. Bu proje, Visual Studio ve uzak aracı tarafından Mac 'e aktarılan bir yapı paketi oluşturur. Bu projeyi yapılandırdığınızda, Visual Studio uygulamanızı derlemek ve Mac 'te dağıtmak için dosyaları ve komutları gönderir.

## <a name="build-and-run-the-android-app"></a>Android uygulamasını derleme ve çalıştırma

Şablon tarafından oluşturulan çözüm, Android uygulamasını varsayılan proje olarak ayarlar.  Yükleme ve kurulumunuzu doğrulamak için bu uygulamayı derleyip çalıştırabilirsiniz. İlk test için, uygulamayı Android öykünücüsü tarafından yüklenen cihaz profillerinden birinde çalıştırın. Uygulamanızı başka bir hedefte test etmek isterseniz, hedef öykünücüsünü yükleyebilir veya cihazı bilgisayarınıza bağlayabilirsiniz.

### <a name="to-build-and-run-the-android-native-activity-app"></a>Android yerel etkinlik uygulamasını derlemek ve çalıştırmak için

1. Henüz seçili değilse, **çözüm platformları** açılan listesinden **x86** ' yı seçin.

   ![Çözüm platformunu x86 olarak ayarlama](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")

   Öykünücüyü hedeflemek için x86 kullanın. Bir cihazı hedeflemek için cihaz işlemcisini temel alan çözüm platformunu seçin. **Çözüm platformları** listesi görüntülenmiyorsa, **Düğme Ekle/Kaldır** listesinden **çözüm platformları** ' nı seçin ve ardından platformunuzu seçin.

1. **Çözüm Gezgini**' de, `MyOpenGLESApp.Android.Packaging` projesi için kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

   ![Android paketleme projesi oluştur](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")

   Çıkış penceresi, Android paylaşılan kitaplığı ve Android uygulaması için yapı işleminin çıkışını görüntüler.

   ![Android projeleri için derleme çıkışı](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")

1. Dağıtım hedefleriniz olarak öykünülmüş Android cihaz profillerinden birini seçin.

   ![Dağıtım hedefini seçin](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")

   Başka öykünücüleri yüklediyseniz veya bir Android cihazı bağladıysanız, bunları dağıtım hedefi açılır listesinden seçebilirsiniz. Uygulamayı çalıştırmak için, oluşturulan çözüm platformunun hedef cihazın platformuyla eşleşmesi gerekir.

1. Hata ayıklamayı başlatmak için **F5** tuşuna basın veya +**F5** ' **e basarak hata** ayıklamadan başlayın.

   Visual Studio, kodunuzu yüklemek ve dağıtmak için birkaç saniye geçen öykünücüyü başlatır. Uygulamanın Öykünücüde nasıl göründüğü aşağıda verilmiştir:

   ![Android Emulator 'de çalışan uygulama](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")

   Uygulamanız başlatıldıktan sonra, kesme noktaları ayarlayabilir ve kod içinde ilerlemek, Yereller incelemek ve değerleri izlemek için hata ayıklayıcıyı kullanabilirsiniz.

1. Hata ayıklamayı durdurmak için **shıft** +**F5** tuşlarına basın.

   Öykünücü çalışmaya devam eden ayrı bir işlemdir. Kodunuzu aynı öykünücüye birden çok kez düzenleyebilir, derleyebilir ve dağıtabilirsiniz. Uygulamanız öykünücü üzerindeki uygulama koleksiyonunda görünür ve doğrudan buradan başlatılabilir.

   Oluşturulan Android yerel etkinlik uygulaması ve kitaplık projeleri C++ paylaşılan kodu, Android platformuyla arabirime "tutkalla" kodu içeren dinamik bir kitaplığa koyar. Uygulama kodunun çoğu kitaplıkta bulunur ve bildirim, kaynaklar ve derleme yönergeleri paketleme projelerdir. Paylaşılan kod, NativeActivity projesindeki Main. cpp öğesinden çağrılır. Android yerel etkinliğinin nasıl programgörüntüleneceği hakkında daha fazla bilgi için bkz. Android Geliştirici NDK [kavramları](https://developer.android.com/ndk/guides/concepts.html) sayfası.

   Visual Studio, platform araç takımı olarak Clang kullanan Android NDK 'yi kullanarak Android yerel etkinlik projelerini oluşturur. Visual Studio, NativeActivity projesindeki özellikleri hedef platformda derlemek, bağlamak ve hata ayıklamak için kullanılan seçeneklere eşler. Ayrıntılar için, Myopengtasapp. Android. NativeActivity projesi için **Özellik sayfaları** iletişim kutusunu açın. Komut satırı anahtarları hakkında daha fazla bilgi için bkz. [Clang derleyicisi Kullanıcı el kitabı](http://clang.llvm.org/docs/UsersManual.html).

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>İOS cihazında iOS uygulaması oluşturma ve çalıştırma

İOS uygulama projesi Visual Studio 'da oluşturulur ve düzenlenir, ancak lisanslama kısıtlamaları nedeniyle bir Mac 'ten oluşturulup dağıtılması gerekir. Visual Studio, proje dosyalarını aktarmak ve derleme, dağıtım ve hata ayıklama komutlarını yürütmek için Mac üzerinde çalışan bir uzak aracı ile iletişim kurar. İOS uygulamasını oluşturmadan önce, Mac ve Visual Studio 'Yu, iletişim kuracak şekilde ayarlayın ve yapılandırın. Ayrıntılı yönergeler için bkz. [iOS kullanarak derlemek için araçları yükleyip yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Mac 'inizde uzak aracı çalışır ve Visual Studio ile eşleştirdikten sonra, yükleme ve kurulumunuzu doğrulamak için iOS uygulamasını derleyip çalıştırabilirsiniz.

İOS uygulamasını bir iOS cihazına dağıtmak için, Mac üzerinde Xcode 'da otomatik oturum açmayı da ayarlamanız gerekir. Otomatik imzalama, uygulama imzalamayı otomatik olarak yönetir ve uygulamanın bir derlemesini imzalamak için bir sağlama profili oluşturur.

### <a name="to-set-up-automatic-signing-on-xcode"></a>Xcode 'da otomatik imzalamayı ayarlamak için

1. Henüz yapmadıysanız, Mac 'inizde [Xcode](https://developer.apple.com/xcode/) 'u yükleyemezsiniz.

1. Mac 'inizde Xcode uygulamasını açın.

1. Yeni bir **tek görünüm uygulaması** Xcode projesi oluşturun. Proje oluşturma sırasında gerekli alanları girin. Proje yalnızca daha sonra uygulamanın bir derlemesini imzalamak için kullanılan bir sağlama profili oluşturmak için kullanıldığından, değerler rastgele olabilir.

1. [Apple bir geliştirici programı](https://developer.apple.com/programs/) hesabına KAYıTLı Apple Kimliğinizi Xcode 'a ekleyin. Apple KIMLIĞINIZ, uygulamaları imzalamak için imzalama kimliği olarak kullanılır. İmza kimliğinizi Xcode 'a eklemek için **Xcode** menüsünü açın ve **Tercihler**' i seçin. **Hesaplar** ' ı seçin ve Apple Kimliğinizi eklemek için Ekle düğmesine (+) tıklayın. Ayrıntılı yönergeler için bkz. [Apple ID hesabınızı ekleme](https://help.apple.com/xcode/mac/current/#/devaf282080a).

1. Xcode projesinin "genel" ayarlarından, **paket tanımlayıcısı** değerini `com.<NameOfVSProject>` olarak değiştirin; burada `<NameOfVSProject>`, oluşturduğunuz Visual Studio çözüm projesiyle aynı addır. Örneğin, Visual Studio 'da `MyOpenGLESApp` adlı bir proje oluşturduysanız, **paket tanımlayıcısını** `com.MyOpenGLESApp` olarak ayarlayın.

   ![Xcode paket tanımlayıcısı](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "CPPMDD_OpenGLES_iOSXcodeId")

1. Otomatik imzalamayı etkinleştirmek için denetleyin. İmzalamayı otomatik olarak Yönet * *.

   ![Xcode otomatik imzalama](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "CPPMDD_OpenGLES_iOSXcodeSign")

1. Geliştirme **ekibi**olarak EKLEDIĞINIZ Apple kimliğinin ekip adını seçin.

   ![Xcode ekibi](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "CPPMDD_OpenGLES_iOSXcodeTeam")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>İOS uygulamasını bir iOS cihazında derlemek ve çalıştırmak için

1. Mac 'inizde uzak aracıyı çalıştırın ve Visual Studio 'Nun uzak aracıyla eşleştirildiğini doğrulayın. Uzak aracıyı başlatmak için bir Terminal uygulaması penceresi açın ve `vcremote` girin. Daha fazla bilgi için bkz. [Visual Studio 'da uzak Aracıyı yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).

   ![Vcremote çalıştıran Mac Terminal penceresi](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")

1. Mac 'e bir iOS cihazı ekleyin. Cihazınızı bir bilgisayara ilk kez iliştirmeniz durumunda, bir uyarı, cihazınıza erişmek için bilgisayara güvenip güvenmeyeceğinizi sorar. Cihazın Mac bilgisayarına güvenmesini sağlar.

1. Visual Studio 'da zaten seçili değilse, cihaz işlemcinizi temel alan **çözüm platformları** açılan listesinden çözüm platformunu seçin. Bu örnekte, bir **ARM64** işlemcisidir.

   ![Çözüm platformunu ARM64 olarak ayarla](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "CPPMDD_OpenGLES_SolutionPlatARM64")

1. Çözüm Gezgini ' de, Myopengtasapp. iOS. Application projesinin kısayol menüsünü açın ve projeyi kaldırmak için **Projeyi Kaldır** ' ı seçin.

1. Yine, kaldırılan Myopengyesapp. iOS. Application projesi için kısayol menüsünü açın ve proje dosyasını düzenlemek için **projeyi Düzenle. PBXPROJ** öğesini seçin. @No__t_0 dosyasında, `buildSettings` özniteliğini bulun ve Apple ekip KIMLIĞINIZI kullanarak `DEVELOPMENT_TEAM` ekleyin. Aşağıdaki ekran görüntüsünde, Apple takım KIMLIĞI için `123456ABC` örnek bir değeri gösterilmektedir. Apple Team ID 'nizin değerini Xcode 'dan bulabilirsiniz. **Derleme ayarları** ' na gidin ve bir araç ipucu göstermek için geliştirme ekibi adınızın üzerine gelin. Araç ipucu takımınızın KIMLIĞINI gösterir.

   ![Geliştirme ekibini ayarla](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "CPPMDD_OpenGLES_iOSDevelopmentTeam")

1. @No__t_0 dosyasını kapatın, ardından, yüklenmeyen Myopengtasapp. iOS. Application projesinin kısayol menüsünü açın ve projeyi yeniden yüklemek için **projeyi yeniden yükle** ' yi seçin.

1. Şimdi, projenin kısayol menüsünü açarak ve **Build**' i seçerek Myopengtasapp. IOS. Application projesini derleyin.

   ![İOS uygulama projesi oluştur](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")

   Çıkış penceresinde iOS statik kitaplığı ve iOS uygulaması için yapı işleminin çıktısı görüntülenir. Mac üzerinde, uzak aracıyı çalıştıran Terminal penceresinde, komut ve dosya aktarımı etkinliği görüntülenir.

   Mac bilgisayarınızda, ortak tasarımın anahtarınıza erişmesine izin vermeniz istenebilir. Devam etmek için **Izin ver** ' i seçin.

1. Uygulamanızı Mac 'e iliştirilmiş cihazınızda çalıştırmak için araç çubuğunda iOS cihazınızı seçin. Uygulama başlamazsa, cihazın dağıtılan uygulamanızın cihazda yürütülmesi için izin verdiğinden emin olun. Bu izin, cihazdaki**genel**  > **cihaz yönetimine**  >  **Ayarlar** ' a giderek ayarlanabilir. Geliştirici uygulama hesabınızı seçin, hesabınıza güvenin ve uygulamayı doğrulayın. Uygulamayı Visual Studio 'dan yeniden çalıştırmayı deneyin.

   ![iOS cihazında iOS uygulaması](../cross-platform/media/cppmdd-opengles-iosdevice.png "CPPMDD_OpenGLES_iOSDevice")

   Uygulamanız başlatıldıktan sonra, kesme noktaları ayarlayabilir ve Visual Studio hata ayıklayıcısını kullanarak yerelleri inceleyebilir, çağrı yığınına bakın ve değerleri izleyin.

   ![İOS uygulamasında kesme noktasında hata ayıklayıcı](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")

1. Hata ayıklamayı durdurmak için **shıft** +**F5** tuşlarına basın.

   Oluşturulan iOS uygulaması ve kitaplık projeleri, C++ kodu yalnızca paylaşılan kodu uygulayan bir statik kitaplığa koyar. Uygulama kodunun çoğu `Application` projem. Bu şablon projesindeki Paylaşılan kitaplık koduna yapılan çağrılar *Gameviewcontroller. d* dosyasında yapılır. İOS uygulamanızı derlemek için, Visual Studio, Mac üzerinde çalışan bir uzak istemciyle iletişim gerektiren Xcode platform araç takımını kullanır.

   Visual Studio, proje dosyalarını aktarır ve Xcode kullanarak uygulamayı oluşturmak için uzak istemciye komutlar gönderir. Uzak istemci, derleme durum bilgilerini Visual Studio 'ya geri gönderir. Uygulama başarıyla derlenmiştir ve uygulamayı çalıştırmak ve uygulamada hata ayıklamak için komut göndermek üzere Visual Studio 'Yu kullanabilirsiniz. Visual Studio 'daki hata ayıklayıcı, iOS cihazınızda çalışan ve Mac 'nize bağlı uygulamayı denetler. Visual Studio, StaticLibrary projesindeki özellikleri hedef iOS platformunda derlemek, bağlamak ve hata ayıklamak için kullanılan seçeneklere eşler. Derleyici komut satırı seçeneği ayrıntıları için, Myopengtasapp. iOS. StaticLibrary projesi için **Özellik sayfaları** iletişim kutusunu açın.

## <a name="customize-your-apps"></a>Uygulamalarınızı özelleştirme

Ortak işlevselliği eklemek veya değiştirmek C++ için paylaşılan kodu değiştirebilirsiniz. @No__t_0 Paylaşılan koda yapılan çağrıları ve `MyOpenGLESApp.iOS.Application` projeleri eşleşecek şekilde değiştirmeniz gerekir. Ön işlemci makrolarını, ortak kodunuzda platforma özgü bölümler belirtmek için kullanabilirsiniz. Ön işlemci makro `__ANDROID__`, Android için derleme yaptığınızda önceden tanımlanmıştır. Ön işlemci makro `__APPLE__`, iOS için derleme yaptığınızda önceden tanımlanmıştır.

Belirli bir proje platformu için IntelliSense 'i görmek üzere düzenleyici penceresinin en üstündeki gezinti çubuğunda bulunan bağlam değiştirici açılan menüsünde projeyi seçin.

![Düzenleyicide proje bağlamı değiştirici açılan menüsü](../cross-platform/media/cppmdd_opengles_contextswitcher.png)

Geçerli proje tarafından kullanılan koddaki IntelliSense sorunları kırmızı dalgalı bir çizgiyle işaretlenir. Diğer projelerdeki sorunlar mor dalgalı bir çizgiyle işaretlenir. Visual Studio, Java veya amaç-C dosyaları için kod renklendirme veya IntelliSense 'i desteklemez. Ancak, yine de kaynak dosyalarını değiştirebilir ve Uygulama adınızı, simgenizi ve diğer uygulama ayrıntılarını ayarlamak için kaynakları değiştirebilirsiniz.
