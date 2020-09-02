---
title: Android yerel etkinlik uygulaması oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e554c7b97c2feac031510cfdd0894d29b4ba85eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151075"
---
# <a name="create-an-android-native-activity-app"></a>Android Yerel Etkinlik Uygulaması Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çoklu Platform Mobil Uygulama Geliştirme için Visual C++ seçeneğini yüklediğinizde, Visual Studio 2015, tam işlevli Android yerel etkinlik uygulamaları oluşturmak için kullanılabilir. Android yerel geliştirme seti (NDK), saf C/C++ kodunu kullanarak Android uygulamanızın çoğunluğunu uygulamanıza olanak tanıyan bir araç takımıdır. Bazı Java JNı kodu, C/C++ kodunuzun Android ile etkileşime geçmesini sağlamak için tutkalla işlevi görür. Android NDK, Android API Düzey 9 ile yerel etkinlik uygulamaları oluşturma özelliğini kullanıma sunmuştur. Yerel etkinlik kodu, Unreal Engine veya OpenGL kullanan oyun ve grafik kullanımı yoğun uygulamalar oluşturmak için yaygındır. Bu konu, OpenGL kullanan basit bir yerel etkinlik uygulamasının oluşturulmasında size kılavuzluk eder. Ek konular, yerel etkinlik kodunu düzenlemenin, oluşturmanın, hata ayıklamanın ve dağıtmanın geliştirici yaşam döngüsü boyunca size yol gösterir.  
  
 [Gereklilik](#req)   
 [Yeni bir yerel etkinlik projesi oluştur](#Create)   
 [Varsayılan Android yerel etkinlik uygulamasını derleyin ve çalıştırın](#BuildHello)  
  
## <a name="requirements"></a><a name="req"></a> Gereklilik  
 Android yerel etkinlik uygulaması oluşturabilmeniz için, tüm sistem gereksinimlerini karşıladığınızdan ve Visual Studio 2015 ' de Visual C++ Mobile Development seçeneğini yüklediğinizden emin olmanız gerekir. Daha fazla bilgi için bkz. [ınstall çoklu platform mobil uygulama geliştirme için Visual C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Yükleme sırasında gerekli olan üçüncü taraf araçların ve SDK 'ların eklendiğinden ve Android için Microsoft Visual Studio Öykünücüsü yüklendiğinden emin olun.  
  
## <a name="create-a-new-native-activity-project"></a><a name="Create"></a> Yeni bir yerel etkinlik projesi oluştur  
 Bu öğreticide, önce yeni bir Android yerel etkinlik projesi oluşturup ardından Android için Visual Studio öykünücüsü ' nde varsayılan uygulamayı derleyip çalıştırmalısınız.  
  
#### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1. Visual Studio'yu açın. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.  
  
2. **Yeni proje** iletişim kutusunda, **Şablonlar**altında **Visual C++**, **platformlar arası**' ı seçin ve ardından **yerel etkinlik uygulaması (Android)** şablonunu seçin.  
  
3. Uygulamaya benzer bir ad verin `MyAndroidApp` ve ardından **Tamam**' ı seçin.  
  
    ![Yerel etkinlik projesi oluşturma](../cross-platform/media/cppmdd-newproject.PNG "CppMDD_NewProject")  
  
    Visual Studio yeni çözümü oluşturur ve Çözüm Gezgini açar.  
  
    ![Çözüm Gezgini yerel etkinlik projesi](../cross-platform/media/cppmdd-rc-na-solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")  
  
   Yeni Android yerel etkinlik uygulaması çözümü iki proje içerir:  
  
- **MyAndroidApp. NativeActivity** , uygulamanızın Android üzerinde yerel bir etkinlik olarak çalışması için başvuruları ve birleştirici kodu içerir. Birleştirici kodundan giriş noktalarının uygulanması Main. cpp ' dir. Önceden derlenmiş üstbilgiler pch. h içinde. Bu yerel etkinlik uygulaması projesi, bir paylaşılan kitaplık olarak derlenir. bu nedenle paketleme projesi tarafından çekilir.  
  
- **MyAndroidApp. paketleme** , bir Android cihazında veya öykünücüsünde dağıtım için. apk dosyası oluşturur. Bu, bildirim özelliklerini ayarladığınız kaynakları ve AndroidManifest.xml dosyasını içerir. Ayrıca, ant yapı sürecini denetleyen build.xml dosyasını da içerir. Varsayılan olarak, doğrudan Visual Studio 'dan dağıtılabilmesi ve çalıştırmak için başlangıç projesi olarak ayarlanır.  
  
## <a name="build-and-run-the-default-android-native-activity-app"></a><a name="BuildHello"></a> Varsayılan Android yerel etkinlik uygulamasını derleyin ve çalıştırın  
 Yükleme ve kurulumunuzu doğrulamak için şablon tarafından oluşturulan uygulamayı derleyin ve çalıştırın. Bu ilk test için, uygulamayı Android için Visual Studio öykünücüsü tarafından yüklenen cihaz profillerinden birinde çalıştırın. Uygulamanızı başka bir hedefte test etmek isterseniz, hedef öykünücüsünü yükleyebilir veya cihazı bilgisayarınıza bağlayabilirsiniz.  
  
#### <a name="to-build-and-run-the-default-native-activity-app"></a>Varsayılan yerel etkinlik uygulamasını derlemek ve çalıştırmak için  
  
1. Henüz seçili değilse, **çözüm platformları** açılan listesinden **x86** ' yı seçin.  
  
     ![Çözüm platformları açılan x86 seçimi](../cross-platform/media/cppmdd-rc-na-solution-x86.png "CPPMDD_RC_NA_Solution_x86")  
  
     **Çözüm platformları** listesi görüntülenmiyorsa, **Düğme Ekle/Kaldır** listesinden **çözüm platformları** ' nı seçin ve ardından platformunuzu seçin.  
  
2. Menü çubuğunda **Oluştur**, **çözüm oluştur**' u seçin.  
  
     Çıkış penceresi, çözümdeki iki proje için yapı işleminin çıkışını görüntüler.  
  
3. Dağıtım hedefleriniz olarak VS öykünücüsü Android Phone (x86) profillerinden birini seçin.  
  
     Başka öykünücüleri yüklediyseniz veya bir Android cihazı bağladıysanız, bunları dağıtım hedefi açılan listesinden seçebilirsiniz.  
  
4. Hata ayıklamayı başlatmak için F5 'e veya hata ayıklama olmadan başlamak için SHIFT + F5 'e basın.  
  
     Varsayılan uygulama, Android için Visual Studio öykünücüsü 'nde olduğu gibi görünür.  
  
     ![Uygulamanızı çalıştıran öykünücü](../cross-platform/media/cppmdd-emulator-running-app.PNG "CppMDD_Emulator_Running_App")  
  
     Visual Studio, kodunuzu yüklemek ve dağıtmak için birkaç saniye geçen öykünücüyü başlatır. Uygulamanız başlatıldıktan sonra, kesme noktaları ayarlayabilir ve kod içinde ilerlemek, Yereller incelemek ve değerleri izlemek için hata ayıklayıcıyı kullanabilirsiniz.  
  
5. Hata ayıklamayı durdurmak için SHIFT + F5 tuşlarına basın.  
  
     Öykünücü çalışmaya devam eden ayrı bir işlemdir. Kodunuzu aynı öykünücüye birden çok kez düzenleyebilir, derleyebilir ve dağıtabilirsiniz.
