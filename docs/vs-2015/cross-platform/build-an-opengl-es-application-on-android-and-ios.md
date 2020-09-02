---
title: Android ve iOS üzerinde OpenGL ES uygulaması oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b9f5db4ccd70136b711f5bd221244418cf843485
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151191"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Android ve iOS Üzerinde OpenGL ES Uygulaması Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çoklu Platform Mobil Uygulama Geliştirme için Visual C++ seçeneğini yüklediğinizde, ortak kod paylaşan iOS uygulamaları ve Android uygulamaları için Visual Studio çözümleri ve projeleri oluşturabilirsiniz. Bu konu, hem basit bir iOS uygulaması hem de Android yerel etkinlik uygulaması oluşturan bir çözüm şablonunda size rehberlik eder. Uygulamalar, her platformda aynı animasyonlu döndürme küpünü göstermek için OpenGL ES kullanan ortak C++ koduna sahiptir. OpenGL ES (katıştırılmış sistemler veya GLES için OpenGL), birçok mobil cihazda desteklenen 2B ve 3B bir grafik API 'sidir.  
  
 [Gereklilik](#req)   
 [Yeni bir OpenGLES uygulama projesi oluşturma](#Create)   
 [Android uygulamasını derleme ve çalıştırma](#BuildAndroid)   
 [İOS uygulamasını derleme ve çalıştırma](#BuildIOS)   
 [Uygulamalarınızı özelleştirme](#Customize)  
  
## <a name="requirements"></a><a name="req"></a> Gereklilik  
 İOS ve Android için bir OpenGL ES uygulaması oluşturabilmeniz için önce tüm sistem gereksinimlerini karşıladığınızdan emin olmanız gerekir. Çoklu Platform Mobil Uygulama Geliştirme için Visual C++ seçeneğini Visual Studio 2015 ' de yüklemelisiniz. Yüklemede gerekli olan üçüncü taraf araçların ve SDK 'ların eklendiğinden ve Android için Visual Studio öykünücüsü ' nin yüklü olduğundan emin olun. Daha fazla bilgi ve ayrıntılı yönergeler için bkz. [ınstall çoklu platform mobil uygulama geliştirme için Visual C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). İOS uygulamasını derlemek ve test etmek için, yükleme yönergelerine göre ayarlanmış bir Mac bilgisayar olması gerekir. İOS geliştirme için ayarlama hakkında daha fazla bilgi için bkz. [iOS kullanarak derlemek Için araçları kurma ve yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
## <a name="create-a-new-opengles-application-project"></a><a name="Create"></a> Yeni bir OpenGLES uygulama projesi oluşturma  
 Bu öğreticide, önce yeni bir OpenGL ES uygulaması projesi oluşturun ve ardından Android için Visual Studio öykünücüsü içinde varsayılan uygulamayı derleyin ve çalıştırın. Ardından, iOS için uygulamayı derleyin ve uygulamayı iOS simülatöründe çalıştırın.  
  
#### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1. Visual Studio'yu açın. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.  
  
2. **Yeni proje** iletişim kutusunda, **Şablonlar**altında **Visual C++**, **platformlar arası**' ı seçin ve **OpenGLES uygulaması (Android, iOS)** şablonunu seçin.  
  
3. Uygulamaya benzer bir ad verin `MyOpenGLESApp` ve ardından **Tamam**' ı seçin.  
  
    ![Yeni OpenGLES uygulama projesi](../cross-platform/media/cppmdd-opengles-newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
    Visual Studio yeni çözümü oluşturur ve Çözüm Gezgini açar.  
  
    ![Çözüm Gezgini Myopengtasapp](../cross-platform/media/cppmdd-opengles-solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
   Yeni OpenGL ES uygulama çözümü, üç kitaplık projesi ve iki uygulama projesi içerir. Kitaplıklar klasörü, Paylaşılan koda başvuran, paylaşılan bir kod projesi ve platforma özel iki proje içerir:  
  
- **Myopengtasapp. Android. NativeActivity** , uygulamanızı Android 'de yerel bir etkinlik olarak uygulayan başvuruları ve birleştirici kodu içerir. Birleştirme kodundan gelen giriş noktalarının uygulanması, Myopengtasapp. Shared dosyasındaki ortak paylaşılan kodu içeren Main. cpp ' dir. Önceden derlenmiş üstbilgiler pch. h içinde. Bu yerel etkinlik uygulaması projesi, Myopenginsapp. Android. paketleme projesi tarafından seçilen paylaşılan bir kitaplık (. so) dosyasında derlenir.  
  
- **Myopengtasapp. iOS. StaticLibrary** , Myopenglisapp. Shared dosyasındaki paylaşılan kodu Içeren bir iOS statik kitaplık (. a) dosyası oluşturur. Bu, Myopengtasapp. iOS. Application projesi tarafından oluşturulan uygulamayla bağlantılıdır.  
  
- **Myopengtasapp. Shared** , platformlar arasında çalışacak paylaşılan kodu içerir. Platforma özgü kodun koşullu derlenmesi için Önişlemci makrolarını kullanır. Paylaşılan kod hem Myopengkasapp. Android. NativeActivity hem de Myopenglisapp. iOS. StaticLibrary içinde proje başvurusu tarafından alınır.  
  
  Çözüm, Android ve iOS platformları için uygulamalar oluşturmak üzere iki projeye sahiptir:  
  
- **Myopenglesapp. Android. paketleme** , bir Android cihazında veya öykünücüsünde dağıtım için. apk dosyası oluşturur. Bu, bildirim özelliklerini ayarladığınız kaynakları ve AndroidManifest.xml dosyasını içerir. Ayrıca, ant yapı sürecini denetleyen build.xml dosyasını da içerir. Varsayılan olarak, doğrudan Visual Studio 'dan dağıtılabilmesi ve çalıştırmak için başlangıç projesi olarak ayarlanır.  
  
- **Myopengtasapp. iOS. Application** , Myopengpersapp. IOS. StaticLibrary içindeki C++ statik kitaplık koduna bağlanan bir iOS uygulaması oluşturmak için kaynaklar ve hedef-C birleştirici kodunu içerir. Bu proje, Visual Studio ve uzak aracı tarafından Mac 'e aktarılan bir yapı paketi oluşturur. Bu projeyi yapılandırdığınızda, Visual Studio uygulamanızı derlemek ve Mac 'te dağıtmak için dosyaları ve komutları gönderir.  
  
## <a name="build-and-run-the-android-app"></a><a name="BuildAndroid"></a> Android uygulamasını derleme ve çalıştırma  
 Şablon tarafından oluşturulan çözüm, Android uygulamasını varsayılan proje olarak ayarlar.  Yükleme ve kurulumunuzu doğrulamak için bu uygulamayı derleyip çalıştırabilirsiniz. İlk test için, uygulamayı Android için Visual Studio öykünücüsü tarafından yüklenen cihaz profillerinden birinde çalıştırın. Uygulamanızı başka bir hedefte test etmek isterseniz, hedef öykünücüsünü yükleyebilir veya cihazı bilgisayarınıza bağlayabilirsiniz.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Android yerel etkinlik uygulamasını derlemek ve çalıştırmak için  
  
1. Henüz seçili değilse, **çözüm platformları** açılan listesinden **x86** ' yı seçin.  
  
    ![Çözüm platformunu x86 olarak ayarlama](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    Windows için Android Emulator hedeflemek için x86 kullanın. Bir cihazı hedefliyorsanız, cihaz işlemcisini temel alan çözüm platformunu seçin. **Çözüm platformları** listesi görüntülenmiyorsa, **Düğme Ekle/Kaldır** listesinden **çözüm platformları** ' nı seçin ve ardından platformunuzu seçin.  
  
2. **Çözüm Gezgini**' de, Myopengtasapp. Android. paketleme projesi için kısayol menüsünü açın ve ardından **Oluştur**' u seçin.  
  
    ![Android paketleme projesi oluştur](../cross-platform/media/cppmdd-opengles-andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
    Çıkış penceresi, Android paylaşılan kitaplığı ve Android uygulaması için yapı işleminin çıkışını görüntüler.  
  
    ![Android projeleri için derleme çıkışı](../cross-platform/media/cppmdd-opengles-andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3. Dağıtım hedefleriniz olarak VS öykünücüsü Android Phone (x86) profillerinden birini seçin.  
  
    ![Dağıtım hedefini seçin](../cross-platform/media/cppmdd-opengles-pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
    Başka öykünücüleri yüklediyseniz veya bir Android cihazı bağladıysanız, bunları dağıtım hedefi açılır listesinden seçebilirsiniz. Uygulamayı çalıştırmak için, oluşturulan çözüm platformunun hedef cihazın platformuyla eşleşmesi gerekir.  
  
4. Hata ayıklamayı başlatmak için F5 'e veya hata ayıklama olmadan başlamak için SHIFT + F5 'e basın.  
  
    Visual Studio, kodunuzu yüklemek ve dağıtmak için birkaç saniye geçen öykünücüyü başlatır. Uygulamanın Android için Visual Studio öykünücüsü 'nde nasıl göründüğü aşağıda verilmiştir.  
  
    ![Android Emulator 'de çalışan uygulama](../cross-platform/media/cppmdd-opengles-andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
    Uygulamanız başlatıldıktan sonra, kesme noktaları ayarlayabilir ve kod içinde ilerlemek, Yereller incelemek ve değerleri izlemek için hata ayıklayıcıyı kullanabilirsiniz.  
  
5. Hata ayıklamayı durdurmak için SHIFT + F5 tuşlarına basın.  
  
    Öykünücü çalışmaya devam eden ayrı bir işlemdir. Kodunuzu aynı öykünücüye birden çok kez düzenleyebilir, derleyebilir ve dağıtabilirsiniz. Uygulamanız öykünücü üzerindeki uygulama koleksiyonunda görünür ve doğrudan buradan başlatılabilir.  
  
   Oluşturulan Android yerel etkinlik uygulaması ve kitaplık projeleri, C++ paylaşılan kodunu, Android platformuyla arabirime "tutkalla" kodu içeren dinamik bir kitaplığa koyar. Bu, uygulama kodunun büyük bir kısmının kitaplıkta olduğu ve bildirim, kaynak ve derleme yönergelerinin paketleme projesinde olduğu anlamına gelir. Paylaşılan kod, NativeActivity projesindeki Main. cpp öğesinden çağrılır. Android yerel etkinliğinin nasıl programgörüntüleneceği hakkında daha fazla bilgi için bkz. Android Geliştirici NDK [kavramları](https://developer.android.com/ndk/guides/concepts.html) sayfası.  
  
   Visual Studio, platform araç takımı olarak Clang kullanan Android NDK 'yi kullanarak Android yerel etkinlik projelerini oluşturur. Visual Studio, NativeActivity projesindeki özellikleri hedef platformda derlemek, bağlamak ve hata ayıklamak için kullanılan komut satırı anahtarlarına ve seçeneklere eşler. Ayrıntılar için, Myopengtasapp. Android. NativeActivity projesi için **Özellik sayfaları** iletişim kutusunu açın. Komut satırı anahtarları hakkında daha fazla bilgi için bkz. [Clang derleyicisi Kullanıcı el kitabı](http://clang.llvm.org/docs/UsersManual.html).  
  
## <a name="build-and-run-the-ios-app"></a><a name="BuildIOS"></a> İOS uygulamasını derleme ve çalıştırma  
 İOS uygulama projesi Visual Studio 'da oluşturulur ve düzenlenir, ancak lisanslama kısıtlamaları nedeniyle bir Mac 'ten oluşturulup dağıtılması gerekir. Visual Studio, proje dosyalarını aktarmak ve derleme, dağıtım ve hata ayıklama komutlarını yürütmek için Mac üzerinde çalışan bir uzak aracı ile iletişim kurar. İOS uygulamasını oluşturmadan önce, Mac ve Visual Studio 'Yu iletişim kuracak şekilde ayarlamanız ve yapılandırmanız gerekir. Ayrıntılı yönergeler için bkz. [iOS kullanarak derlemek Için araçları yükleyip yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Uzak aracı çalışmaya başladıktan ve Visual Studio Mac ile eşleştirildikten sonra, yükleme ve kurulumunuzu doğrulamak için iOS uygulamasını derleyip çalıştırabilirsiniz.  
  
#### <a name="to-build-and-run-the-ios-app"></a>İOS uygulamasını derlemek ve çalıştırmak için  
  
1. Mac 'inizde uzak aracının çalıştığını ve Visual Studio 'Nun uzak aracıyla eşleştirildiğini doğrulayın. Uzak aracıyı başlatmak için bir Terminal uygulaması penceresi açın ve girin `vcremote` . Daha fazla bilgi için bkz. [Visual Studio 'da uzak Aracıyı yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).  
  
    ![Vcremote çalıştıran Mac Terminal penceresi](../cross-platform/media/cppmdd-common-vcremote.png "CPPMDD_common_vcremote")  
  
2. Henüz seçili değilse, **çözüm platformları** açılan listesinden **x86** ' yı seçin.  
  
    ![Çözüm platformunu x86 olarak ayarlama](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    İOS simülatörünü hedeflemek için x86 kullanın. Bir iOS cihazını hedefliyorsanız, cihaz işlemcisini temel alan çözüm platformunu (genellikle ARM işlemcisi) seçin. **Çözüm platformları** listesi görüntülenmiyorsa, **Düğme Ekle/Kaldır** listesinden **çözüm platformları** ' nı seçin ve ardından platformunuzu seçin.  
  
3. Çözüm Gezgini ' de, Myopengtasapp. iOS. Application projesinin kısayol menüsünü açın ve **Build**' ı seçin.  
  
    ![İOS uygulama projesi oluştur](../cross-platform/media/cppmdd-opengles-iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
    Çıkış penceresinde iOS statik kitaplığı ve iOS uygulaması için yapı işleminin çıktısı görüntülenir. Mac üzerinde, uzak aracıyı çalıştıran Terminal penceresinde, komut ve dosya aktarımı etkinliği görüntülenir.  
  
    Mac bilgisayarınızda, bir kod imzalama isteğini kabul etmeniz istenebilir. Devam etmek için Izin ver ' i seçin.  
  
4. Uygulamayı Mac 'inizde iOS Benzeticisinde çalıştırmak için araç çubuğunda **IOS simülatörü** ' ni seçin. Simülatörü başlatmak biraz zaman alabilir. Çıktısını görmek için simülatörünü Mac 'inizde ön plana getirmeniz gerekebilir.  
  
    ![İOS simülatörü üzerinde çalışan uygulama](../cross-platform/media/cppmdd-opengles-iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
    Uygulamanız başlatıldıktan sonra, kesme noktaları ayarlayabilir ve Visual Studio hata ayıklayıcısını kullanarak yerelleri inceleyebilir, çağrı yığınına bakın ve değerleri izleyin.  
  
    ![İOS uygulamasında kesme noktasında hata ayıklayıcı](../cross-platform/media/cppmdd-opengles-iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5. Hata ayıklamayı durdurmak için SHIFT + F5 tuşlarına basın.  
  
    İOS simülatörü Mac 'inizde çalışmaya devam eden ayrı bir işlemdir. Kodunuzu aynı iOS simülatörü örneğine birden çok kez düzenleyebilir, derleyebilir ve dağıtabilirsiniz. Ayrıca, kodunuzu dağıtıldıktan sonra doğrudan simülatörde çalıştırabilirsiniz.  
  
   Oluşturulan iOS uygulaması ve kitaplık projeleri, C++ kodunu yalnızca paylaşılan kodu uygulayan bir statik kitaplığa koyar. Uygulama kodunun çoğu uygulama projem. Bu şablon projesindeki Paylaşılan kitaplık koduna yapılan çağrılar GameViewController. d dosyasında yapılır. İOS uygulamanızı derlemek için, Visual Studio, Mac üzerinde çalışan bir uzak istemciyle iletişim gerektiren Xcode platform araç takımını kullanır.  
  
   Visual Studio, proje dosyalarını aktarır ve Xcode kullanarak uygulamayı oluşturmak için uzak istemciye komutlar gönderir. Uzak istemci, derleme durum bilgilerini Visual Studio 'ya geri gönderir. Uygulama başarıyla derlenmiştir ve uygulamayı çalıştırmak ve uygulamada hata ayıklamak için komut göndermek üzere Visual Studio 'Yu kullanabilirsiniz. Visual Studio 'daki hata ayıklayıcı, Mac 'inizde çalışan iOS Benzeticisinde veya iliştirilmiş bir iOS cihazında çalıştırılan uygulamayı denetler. Visual Studio, StaticLibrary projesindeki özellikleri, hedef iOS platformunda derlemek, bağlamak ve hata ayıklamak için kullanılan komut satırı anahtarları ve seçenekleriyle eşler. Derleyici komut satırı seçeneği ayrıntıları için, Myopengtasapp. iOS. StaticLibrary projesi için **Özellik sayfaları** iletişim kutusunu açın.  
  
## <a name="customize-your-apps"></a><a name="Customize"></a> Uygulamalarınızı özelleştirme  
 Ortak işlevselliği eklemek veya değiştirmek için paylaşılan C++ kodunu değiştirebilirsiniz. Eşleşmesi için Myopengyesapp. Android. NativeActivity ve Myopenginsapp. iOS. Application projelerindeki Paylaşılan koda yapılan çağrıları değiştirmelisiniz. Ön işlemci makrolarını, ortak kodunuzda platforma özgü bölümler belirtmek için kullanabilirsiniz. Ön işlemci makrosu, `__ANDROID__` Android için derleme yaptığınızda önceden tanımlanmıştır. Ön işlemci makrosu, `__APPLE__` iOS için derleme yaptığınızda önceden tanımlanmıştır.  
  
 Belirli bir proje platformu için IntelliSense 'i görmek üzere düzenleyici penceresinin en üstündeki gezinti çubuğunda bulunan bağlam değiştirici açılan menüsünde projeyi seçin.  
  
 ![Düzenleyicide proje bağlamı değiştirici açılan menüsü](../cross-platform/media/cppmdd-opengles-contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 Geçerli projedeki IntelliSense sorunları kırmızı dalgalı bir çizgiyle işaretlenir. Diğer projelerdeki sorunlar mor dalgalı bir çizgiyle işaretlenir. Varsayılan olarak Visual Studio, Java veya amaç-C dosyaları için kod renklendirme veya IntelliSense 'i desteklemez. Ancak, yine de kaynak dosyalarını değiştirebilir ve Uygulama adınızı, simgenizi ve diğer uygulama ayrıntılarını ayarlamak için kaynakları değiştirebilirsiniz.
