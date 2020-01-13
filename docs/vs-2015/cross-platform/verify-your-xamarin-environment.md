---
title: Xamarin ortamınızı doğrulayın | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: 15
ms.author: crdun
manager: crdun
ms.openlocfilehash: 98925402b91bea62e10b47312e7834ed92a1a178
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918749"
---
# <a name="verify-your-xamarin-environment"></a>Xamarin ortamınızı doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yükleyiciler tamamlandığında (bkz. [Kurulum ve yükleme](../cross-platform/setup-and-install.md)), her şeyin Xamarin geliştirmeyi deneymeye hazırlandığını doğrulamak için birkaç dakika harcaın.  
  
 Bu doğrulamaları tamamladıktan sonra, aşağıdaki yönergelerden birini ya da her ikisini de yapabilirsiniz:  
  
- [Visual Studio'da Xamarin.Forms ile uygulama oluşturmaya yönelik temel bilgileri öğrenin](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)  
  
- [Visual Studio’da Xamarin kullanarak yerel kullanıcı arabirimi ile uygulama oluşturma](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)  
  
## <a name="all-platforms"></a>Tüm platformlar  
 İlk olarak **araçlar > seçenekler**' i seçin, **Xamarin > diğer**' i genişletin ve güncelleştirmeler için **Şimdi Denetle** bağlantısına tıklayın. Önceki lisanslama sorunlarından kaçınmak için Xamarin 4.0.3.214 veya üstünü kullanmanız gerekir.  
  
 Daha sonra Visual Studio 'da **Yeni proje > dosya**kullanarak yeni bir Xamarin çözümü oluşturun, ardından Iletişim kutusunda **Şablonlar > diğer diller > Visual C# > platformlar arası**' ı genişletin, **boş uygulama (yerel taşınabilir)** seçeneğini belirleyip Tamam ' a tıklayın. Bu, paylaşılan bir taşınabilir sınıf kitaplığı projesiyle ve Android, iOS ve Windows için bireysel projelerle bir çözüm oluşturur:  
  
 ![Boş uygulama &#40;yerel taşınabilir&#41; şablonundan yeni bir proje oluşturma sonuçları](../cross-platform/media/crossplat-xamarin-verify-1.png "Çapraz Splat Xamarin Verify 1")  
  
> [!NOTE]
> Şablonlar orada yoksa, [Xamarin proje şablonları eksik mi? ](#missing)Bu sayfanın en altında bunu deneyin.  
  
## <a name="android"></a>Android  
  
1. **Araçlar > Android > Android SDK Manager** ' a giderek en son Android SDK araçlarına sahip olup olmadığınızı denetleyin ve Android SDK Tools, Android SDK platform-araçlar ve Android SDK yapı araçları bileşenlerinin en yeni sürümünü yükleyebilirsiniz. En son Android API düzeyini her zaman yüklemek gerekli değildir; ihtiyacınız olan API, hedeflemek istediğiniz platform düzeyine bağlıdır. Genel olarak, Xamarin 'in yüklenmesi gereken platform düzeyini yükler.  

2. Android tasarımcısını doğrulama: Çözüm Gezgini Android projesinde, **ana. axml dosyasını > kaynaklar > düzeni** ' ni açın. (Bu dosyayı doğrudan görmüyorsanız, Çözüm Gezgini aramayı deneyin; iOS projesinde değil yalnızca Android projesinde bulunur.)  
  
    - "Yüklü Android SDK çok eski olduğunu" belirten bir hata alırsanız Yukarıdaki 1. adımda bulunan en yeni SDK sürümü araçlarını seçip yüklemek için bu iletideki **Android SDK aç** ' a tıklayın. 
  
3. Öykünücüsünde (veya cihazda) derleme ve hata ayıklamayı doğrulama:  
  
    - Çözüm Gezgini Android projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.  
  
         ![Visual Studio başlangıç projesi olarak ayarla seçeneği](../cross-platform/media/crossplat-xamarin-verify-2.png "Çapraz Splat Xamarin Verify 2")  
  
    - Hedef Android sürümünüzü temel alan uygun bir öykünücü seçin; bilgisayarınıza bağlı bir Android geliştirme cihazınız varsa, bu aygıtı öykünücülerin yanı sıra burada da göreceksiniz:  
  
        - Windows 8 +: Visual Studio 'nun hata ayıklama açılan penceresinde aşağıda gösterildiği gibi bir **vs öykünücü** hedefi seçin ve **F5**'e basarak hata ayıklayıcıyı başlatın. Daha fazla ayrıntı için bkz. [Android Için Visual Studio öykünücüsü](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/) (VISUAL Studio ALM blogu) tanıtımı. Öykünücüyü çalışırken sorunlarla karşılaşırsanız bkz. [Android Için Visual Studio öykünücüsü sorunlarını giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Ayrıca **araçlar > Android Için Visual Studio öykünücüsü**' nü seçerek öykünücü için yeni cihaz profilleri oluşturabilirsiniz...  
  
             ![Android için Visual Studio öykünücüsü 'nü hata ayıklama hedefi olarak seçme](../cross-platform/media/crossplat-xamarin-verify-3.png "Çapraz Splat Xamarin Verify 3")  
  
             Not: **Android Için Visual Studio öykünücüsü... menü seçeneğinin araçlar >** görmüyorsanız, öykünücü 'nın kendisi yüklü olmayabilir. **Denetim masası > programlar ve Özellikler**' e gidin, **Microsoft Visual Studio**' i seçin ve yükleyiciyi yeniden çalıştırmak için **Değiştir** ' i tıklatın. Yükleyicide **Değiştir** ' e tıklayın, **platformlar arası mobil geliştirme > Android için Microsoft Visual Studio öykünücüsü**kutusunu işaretleyin ve **Güncelleştir**' e tıklayın.  
  
        - Windows 7 ve öncesi için: açılan kutuda Android için Xamarin Player ' ı seçin ve çalıştırmak için F5 ' e basın. Xamarin Player, Cihaz Yöneticisi ve sorun giderme ipuçları hakkında daha fazla bilgi için [Xamarin Android Player](/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) okuyun (Xamarin.com).  
  
> [!NOTE]
> Visual Studio 'da, Google Android öykünücüsü 'nü yapılandırmak için özel olarak kullanılan cihaz yöneticisini açan araç çubuğunda (aşağıda göster) Android Emulator Manager (AVD) düğmesinin varlığını fark edebilirsiniz.  Bu, Android için Visual Studio öykünücüsü veya Xamarin Player üzerinde hiçbir etkisi yoktur, her birinin profilleri yapılandırmak için kendi cihaz yöneticisi vardır.  Ayrıntılar için bkz. [Android Için Visual Studio öykünücüsü](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/) (VISUAL Studio ALM blogu) ve [Xamarin Android Player](/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (Xamarin.com) tanıtımı.  
> ![Çapraz Splat Xamarin doğrulama 7](../cross-platform/media/crossplat-xamarin-verify-7.png "Çapraz Splat Xamarin doğrulama 7")  
  
## <a name="windows-phone"></a>Windows Phone  
  
1. Windows Phone tasarımcısını doğrulayın: Çözüm Gezgini Windows Phone projesinde, **MainPage. xaml** dosyasını açın.  
  
2. Öykünücüsünde veya bir cihazda derleme ve hata ayıklamayı doğrulama (Note: Bu adım için Visual Studio Kurulumu veya bir tethered cihazı aracılığıyla Windows Phone öykünücüsü yüklemiş olmanız gerekir):  
  
    - Çözüm Gezgini Windows Phone projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.  
  
    - Aşağıda gösterildiği gibi, Visual Studio 'nun hata ayıklama açılan penceresinde bir **öykünücü 8,1** hedefi veya bağlı bir cihaz seçin ve F5 'e basarak hata ayıklayıcıyı başlatın.  
  
         ![Hata ayıklama hedefi olarak Windows Phone öykünücü seçme](../cross-platform/media/crossplat-xamarin-verify-4.png "Çapraz Splat Xamarin Verify 4")  
  
    - Öykünücüyü çalışırken sorunlarla karşılaşırsanız [Windows Phone 8 öykünücüsünün sorunlarını giderme](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx)makalesini okuyun.  
  
## <a name="ios"></a>iOS  
  
1. Mac 'nizin ağda kullanılabilir ve [Mac 'e bağlanma](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) (Xamarin.com) bölümünde açıklandığı gibi Visual Studio ile eşleştirilmiş olduğundan emin olun.  
  
2. Görsel taslak tasarımcısını doğrulayın: Çözüm Gezgini iOS projesinde, **ana. görsel taslak** dosyasını açın. Burada, Visual Studio, Mac üzerinde uzaktan çalışan tasarımcıyı barındırıyor.  
  
3. Derleme ve hata ayıklamayı doğrula:  
  
    1. Çözüm Gezgini ' de iOS projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.  
  
    2. Aşağıda gösterildiği gibi, Visual Studio 'nun Build açılır listesinden **iPhoneSimulator** hedefini veya bir tethered cihazınız varsa **iPhone** hedefini seçin. Bir simülatörleri listelenmiyorsa, Mac 'inizde Xcode 'u başlatın, **Xcode-> tercihleri**' ni seçin ve **İndir**' e tıklayın. **Bileşenler** altında, indirileceği simülatör sürümlerini görmeniz gerekir. Hata ayıklama için ek yönergeler Xamarin 'in [hata ayıklama](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) sayfasında (Xamarin.com) bulunabilir.  
  
         ![İPhoneSimulator Build hedefini seçme](../cross-platform/media/crossplat-xamarin-verify-5.png "Çapraz Splat Xamarin Verify 5")  
  
    3. Aşağıda gösterildiği gibi, Visual Studio 'nun hata ayıklama açılan listesinden bir iPhone hedefi seçin ve F5 'e basarak hata ayıklayıcıyı başlatın. Bu, Visual Studio 'da hata ayıklama gerçekleştiğinde, uygulama ile etkileşim kuracak olan Mac üzerinde simülatörünü başlatır. Mac 'e bağlı bir fiziksel iPhone veya iPad varsa, burada görünür ve bunun yerine seçebilirsiniz. Listelenmiş herhangi bir cihaz veya simülatörleri görmüyorsanız, yukarıdaki 1. adımda bağlantılı konuyu inceleyerek veya **araçlar** >**IOS** >**Xamarin Mac Aracısı** ' na giderek Mac 'e bağlantıyı denetleyin  
  
         ![İPhone hata ayıklama hedefini seçme](../cross-platform/media/crossplat-xamarin-verify-6.png "Çapraz Splat Xamarin doğrulama 6")  
  
    4. Mac 'e bağlanırken sorunlarla karşılaşırsanız [bağlantı sorunlarını giderme](/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting) (Xamarin.com) makalesini okuyun.  
  
    5. "Yüklü sağlama profili yüklü iOS imzalama anahtarlarıyla eşleşmediğinden bir hata görürseniz şunları yapın:  
  
        - Apple Kimliği hesabınızın, [Hesabınızı Xcode 'A ekleme](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Apple.com) bölümünde açıklandığı gibi Mac 'Inizde Xcode 'a eklendiğinden emin olun.  Hesabınızı ekledikten sonra, hem Visual Studio hem de Xcode 'u yeniden başlattığınızdan emin olun.  
  
             ![Çapraz Splat Xamarin Verify 8](../cross-platform/media/crossplat-xamarin-verify-8.png "Çapraz Splat Xamarin Verify 8")  
  
        - İOS paket imzalama sekmesindeki iOS proje özelliklerinde, etkin hata ayıklama yapılandırması için özel yetkilendirme alanının boş olduğunu doğrulayın.  Note: Bu ayarı yalnızca yukarıdaki hata iletisiyle karşılaştıysanız kaldırmayı denemelisiniz.  
  
## <a name="missing"></a>Xamarin proje şablonları eksik mi? Şunu deneyin  
 Xamarin 'i doğrudan Xamarin Web sitesinden yüklerseniz ve Visual Studio 2013 ve Visual Studio 2015 yan yana yüklüyse şablonlar eksik olabilir. Daha kolay bir çözüm vardır, ancak Xamarin Kurulum programındaki **Visual Studio Için xamarin 2015** özelliğini etkinleştirmeniz yeterlidir.  
  
1. Denetim Masası 'nda **Programlar ve Özellikler**' i açın, **Xamarin** öğesini seçin ve **Değiştir**' e tıklayın.  
  
2. Görüntülenen Xamarin Kurulum sihirbazında, **İleri** ' ye tıklayın ve ardından öğesini **değiştirin**.  
  
3. Yüklenecek isteğe bağlı özellikler listesinde, **Visual Studio 2015 Için Xamarin**' i genişletin, **yerel sürücüde yüklenecek**' ı seçin ve sonra özelliği eklemeye devam etmek için **İleri** ' ye tıklayın.
