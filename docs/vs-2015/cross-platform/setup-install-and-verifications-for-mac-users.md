---
title: Mac kullanıcıları için kurulum, yükleme ve doğrulama | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 703ee752a9f16f0abc5e4813707890a6d17947af
ms.sourcegitcommit: 08105865a9643fb20dce9b8b7580452cfbbe7ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74538934"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Mac kullanıcıları için kurulum, yükleme ve doğrulamalar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, birincil olarak Visual Studio 'Yu Mac üzerinde bir Windows sanal makinesi içinde kullanacak bir Mac üzerinde çalışan geliştiriciler için tasarlanmıştır. Birincil olarak bir Windows bilgisayarında çalışan bir geliştirici iseniz ve iOS hedeflemek için ikincil Mac ayarlamanız gerekiyorsa, ana [Kurulum ve yükleme](../cross-platform/setup-and-install.md) konusuna bakın.  
  
 Mac 'te Xamarin ile çalışmak için şunlar gerekir:  
  
- Bir Xamarin hesabı. [https://www.xamarin.com/](https://www.xamarin.com/) gidin ve sayfanın sağ üst köşesinde bulunan **oturum aç** ' a tıklayın, ardından görüntülenen sayfada **Yeni hesap oluştur ' a** tıklayın. Xamarin hesabınız için bir e-posta adresi ve parola seçin.  
  
- Xcode 7 ve Xamarin 4 yüklü olarak OSX Yosemite (10,10) veya üzeri bir Mac.  
  
- Aşağıdaki yapılandırmalardan biri:  
  
  - **Doğrudan Mac üzerinde Xamarin Studio çalıştırmak için:** Xamarin Studio, kullanarak C#Android, IOS ve Windows uygulamaları oluşturmayı destekleyen Xamarin 'in geliştirme ortamıdır.  Xamarin Studio hızlı bir genel bakış almak için, [Xamarin Studio genel bakış](https://xamarin.com/studio) (Xamarin.com) bölümüne bakın.  
  
  - **Mac 'inizde zaten Parallels veya VMware 'niz varsa:** Windows 'U Visual Studio 2015 ve Xamarin 4 Içinde Parallels veya VMware içinde çalıştırın.  Bu yapılandırmayla, Xamarin, Visual Studio ile yüklenen ve kullanarak C#Android, IOS ve WinPhone uygulamaları oluşturmaya yönelik geliştirme ortamınız olarak Visual Studio 'yu kullanma olanağı sağlayan bir uzantıdır.  Visual Studio Geliştirici Essentials programının bir parçası olarak ücretsiz 3 aylık Parallels aboneliği edinebileceğinizi unutmayın. Bkz. [Microsoft Visual Studio Dev Essentials, Parallels Desktop Pro ve Parallels erişimi](https://www.parallels.com/blogs/) (Parallels blogu) içerir.  
  
  Bu konu, bu gereksinimlere ilişkin yönergeler sağlar.  Yükleme işlemi çalışırken, gereken arka plan malzemesini okumak ve izlemek için [Xamarin ile mobil geliştirme hakkında bilgi edinin](../cross-platform/learn-about-mobile-development-with-xamarin.md) konusunu gözden geçirebilirsiniz.  
  
  **Bu konuda:**  
  
- [Mac Kurulumu (Apple KIMLIĞI, Xcode ve Xamarin)](#mac)  
  
- [Paralells içinde Windows kurulumu (Visual Studio ve Xamarin)](#windows)  
  
- [Ortamınızı doğrulayın](#verify)  
  
## <a name="mac"></a>Mac Kurulumu (Apple KIMLIĞI, Xcode ve Xamarin)  
  
1. Henüz bir tane yoksa [Apple Kimliğinizle](https://appleid.apple.com/) ücretsiz BIR Apple Kimliği oluşturun. Bu, Xcode 'a yükleme ve oturum açmada gereklidir.  
  
2. [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/)'Den Xcode indirin ve yükleyin.  
  
3. [Xamarin. iOS (Xamarin.com) yükleme ve yapılandırma](https://docs.microsoft.com/xamarin/ios/get-started/installation/mac) yönergelerini izleyerek Xamarin 'i indirin ve yükleyin.  
  
4. Xamarin 'i hem Windows hem de Mac bilgisayarlara yüklemeyi tamamladıktan sonra, Windows bilgisayarında Visual Studio 'dan iOS ve Mac ile çalışabilmek [için XMA kullanarak Mac 'e bağlanma](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (Xamarin.com) yönergelerini izleyin.  
  
## <a name="windows"></a>Paralells içinde Windows kurulumu (Visual Studio ve Xamarin)  
  
1. Parallels/VMWare içinde yapılandırdığınız Windows Masaüstü 'nü kullanarak, herhangi bir Visual Studio 2015 (Community, Professional veya Enterprise) [sürümüne ait yükleyiciyi indirin ve başlatın](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) . Visual Studio 2015 Community, ücretsiz sürümdür; Profesyonel ve kurumsal sürümler 30 gün boyunca deneme süresi boyunca kullanılabilir.  
  
2. Yükleyici içinde **özel** yükleme ' yi seçin:  
  
     ![Visual Studio yüklemesinde özel seçeneği seçme](../cross-platform/media/cross-plat-xamarin-setup-1.png "Çapraz Plat Xamarin Kurulum 1")  
  
3. Aşağıdaki kutuları işaretleyin/temizleyin:  
  
    1. **Platformlar arası mobil geliştirme > C#/.net (Xamarin) seçeneğini**işaretleyin. Ayrıca, ortak araçlar ve yazılım geliştirme setleri altında çeşitli Android araçları da otomatik olarak seçilecek.  
  
         ![Platformlar arası&#45;mobil geliştirme altında Xamarin seçeneğini belirleyin](../cross-platform/media/cross-plat-xamarin-setup-2.png "Çapraz Plat Xamarin Kurulum 2")  
  
    2. **Platformlar arası mobil geliştirme > Android için Microsoft Visual Studio öykünücüsü**temizleyin.  
  
4. Install düğmesine tıklayın ve işlemin çalışmasına izin verin. Bu konunun tamamlanması biraz zaman alır, bu konuyla devam edebilirsiniz ve [Xamarin ile mobil geliştirme hakkında bilgi edinebilirsiniz](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Yükleme tamamlandıktan sonra Visual Studio 'Yu başlatın ve istenirse Microsoft hesabı ile oturum açın (Bu, Windows ile kullandığınız hesaptır). Daha sonra, **> > Xamarin** veya **tools > > > Seçenekler**aracılığıyla **Xamarin güncelleştirmelerini kontrol** edin.  
  
     ![Visual Studio seçeneklerinde Xamarin güncelleştirmelerini denetleme](../cross-platform/media/cross-plat-xamarin-setup-3.png "Çapraz Plat Xamarin kurulumu 3")  
  
    > [!NOTE]
    > Daha önceki Xamarin lisanslarıyla ilgili sorunlardan kaçınmak için Xamarin 'i 4.0.3.214 veya üzeri bir sürüme güncelleştirdiğinizden emin olun.  Güncelleştirmeleri denetlemeye çalışırsanız ve Microsoft derleme araçları hakkında bir hata görürseniz, [Xamarin 'in forumlarındaki](https://forums.xamarin.com/discussion/69015/xamarin-update-on-vs-2013-says-i-need-the-build-tools-for-vs-2015)iş parçacığına bakın.
  
6. Xamarin 'i hem Windows hem de Mac bilgisayarlara yüklemeyi tamamladıktan sonra, Visual Studio 'dan iOS ile çalışabilmek [için XMA (Xamarin.com) kullanarak Mac 'e bağlanma](/xamarin/ios/get-started/installation/windows/connecting-to-mac) yönergelerini izleyin.  
  
## <a name="verify"></a>Ortamınızı doğrulayın  
 Yükleyiciler tamamlandığında, her şeyin Xamarin geliştirmeyi deneymeye hazırlandığını doğrulamak için birkaç dakikanızı ayırın.  
  
### <a name="xamarin-studio"></a>Xamarin Studio  
 İlk olarak, belirtilen bağlantılara gittiğinizde, Xamarin belgelerinin doğru sürümünü görebilmeniz için sağ üst köşede **Xamarin Studio** seçtiğinizden emin olun:  
  
 ![Xamarin.com üzerinde doğru belgeleri görmek için Xamarin Studio seçme](../cross-platform/media/crossplat-xamarin-mac-1.png "Çapraz Splat Xamarin Mac 1")  
  
 **Outlook Web Access (OWA)**  
  
1. [Android projesi oluşturma](https://github.com/xamarin/docs-archive/tree/master/Recipes/android/general/projects/create_an_android_project) (Xamarin.com) yönergelerini Izleyerek bir Android projesi oluşturmayı doğrulayın.  
  
2. Android Player ile Android Player 'da hata ayıklamayı doğrulamak [> Xamarin Studio belgeleriyle tümleştirme](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (Xamarin.com).  
  
   **Android**  
  
3. [IOS oluşturma](https://github.com/xamarin/docs-archive/tree/master/Recipes/ios/general/projects/create_an_ios_project) (Xamarin.com) yönergelerini Izleyerek bir iOS projesi oluşturmayı doğrulayın.  
  
4. [Simülatör belgelerindeki hata ayıklama](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) yoluyla iOS benzeticisinde hata ayıklamayı doğrulayın (Xamarin.com).  
  
### <a name="visual-studio"></a>{1&gt;Visual Studio&lt;1}  
 İlk olarak, Xamarin belgelerinin doğru sürümünü görmeniz için sağ üst köşede **Visual Studio** 'nun seçili olduğundan emin olun, ancak  
  
 ![Xamarin.com üzerinde doğru belgeleri görmek için Visual Studio 'Yu seçme](../cross-platform/media/crossplat-xamarin-mac-2.png "Çapraz Splat Xamarin Mac 2")  
  
 Xamarin hesabındaki **araçlar > Xamarin**hesabı aracılığıyla da oturum açın...  
  
 **Outlook Web Access (OWA)**  
  
1. [Android projesi oluşturma](https://github.com/xamarin/docs-archive/tree/master/Recipes/android/general/projects/create_an_android_project) (Xamarin.com) yönergelerini Izleyerek bir Android projesi oluşturmayı doğrulayın.  
  
2. Android tasarımcısını doğrulama: Çözüm Gezgini Android projesinde, **ana. axml dosyasını > kaynaklar > düzeni** ' ni açın.  
  
   - "Yüklü Android SDK çok eski olduğunu" belirten bir hata alırsanız, bu iletideki **Android SDK aç** ' a tıklayın ve kullanılabilir en yeni SDK sürümünü seçin. SDK 'Yı güncelleştirmek için Visual Studio 'Yu yönetici olarak çalıştırıyor olmanız gerektiğini unutmayın.  
  
3. Visual Studio 'dan Mac 'inizde yüklü olan öykünücüsüne bağlanabildiğini doğrulayın.  Bunun sonucunda, Xamarin Player 'ı Visual Studio içinden hata ayıklama için seçebileceğiniz Öykünücüler listesinde görecaksınız.  Bunu yapmak için, [Visual Studio 'yu Xamarin Android Player bağlama](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) yönergelerini izleyin (Xamarin.com).  
  
   **Android**  
  
4. Mac 'nizin ağda kullanılabilir olduğundan ve Visual Studio ile eşlenmiş olduğundan, [XMA kullanarak Mac 'e bağlanma](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (Xamarin.com) bölümünde açıklandığı gibi.  
  
5. [IOS oluşturma](https://github.com/xamarin/docs-archive/tree/master/Recipes/ios/general/projects/create_an_ios_project) (Xamarin.com) yönergelerini Izleyerek bir iOS projesi oluşturmayı doğrulayın.  
  
6. Görsel taslak tasarımcısını doğrulayın: Çözüm Gezgini iOS projesinde, **MainStoryboard. Storyboard** dosyasını açın. Burada, Visual Studio, Mac üzerinde uzaktan çalışan tasarımcıyı barındırıyor.  
  
7. Derleme ve hata ayıklamayı doğrula:  
  
   1. Çözüm Gezgini ' de iOS projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.  
  
   2. Aşağıda gösterildiği gibi, Visual Studio 'nun Build açılır listesinden **iPhoneSimulator** hedefini seçin. Bir simülatörleri listelenmiyorsa, Mac 'inizde Xcode 'u başlatın, **Xcode-> tercihleri**' ni seçin ve **İndir**' e tıklayın. **Bileşenler** altında, indirileceği simülatör sürümlerini görmeniz gerekir. Hata ayıklama için ek yönergeler Xamarin 'in [hata ayıklama](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) sayfasında (Xamarin.com) bulunabilir.  
  
        ![İPhoneSimulator Build hedefini seçme](../cross-platform/media/crossplat-xamarin-verify-5.png "Çapraz Splat Xamarin Verify 5")  
  
   3. Aşağıda gösterildiği gibi, Visual Studio 'nun hata ayıklama açılan listesinden bir iPhone hedefi seçin ve F5 'e basarak hata ayıklayıcıyı başlatın. Bu, Visual Studio 'da hata ayıklama gerçekleştiğinde, uygulama ile etkileşim kuracak olan Mac üzerinde simülatörünü başlatır.  
  
        ![İPhone hata ayıklama hedefini seçme](../cross-platform/media/crossplat-xamarin-verify-6.png "Çapraz Splat Xamarin doğrulama 6")
