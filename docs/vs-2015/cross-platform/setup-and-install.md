---
title: Kurulum ve yükleme | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 19
ms.author: crdun
manager: crdun
ms.openlocfilehash: dbdeeab49da1a63562bb9a4188a264a8d3d99da2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917042"
---
# <a name="setup-and-install"></a>Kurulum ve yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin kullanarak ortak bir C#/.NET kod tabanından Yerel iOS, Android ve Windows uygulamaları derlemek için şunlar gerekir:  
  
- Windows ve Android uygulamalarıyla çalışma için: Visual Studio 2015 ve Xamarin 4 yüklü bir Windows geliştirme bilgisayarı (aşağıdaki nota bakın). (Ayrıca, [doğrudan Xamarin install](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (Xamarin.com) yönergelerini izleyerek Visual Studio 2013 de kullanabilirsiniz.)   
  
- İOS uygulamalarıyla çalışma için: OS X Yosemite (10.10.5) veya üzeri, XCode ve Xamarin yüklü bir Mac.  
  
  Windows ve Mac bilgisayarlarını aynı anda ayarlayabilirsiniz ve bu yükleyiciler çalışırken, gereken arka plan malzemesini okumak ve izlemek için [Xamarin ile mobil geliştirme hakkında bilgi](../cross-platform/learn-about-mobile-development-with-xamarin.md) edinebilirsiniz.  
 
Bu kurulumu yaptıktan ve yükledikten sonra Xamarin kullanarak sorunlarla karşılaşırsanız, sorunuzu [forums.Xamarin.com](https://forums.xamarin.com/)'ye gönderin.
  
> [!NOTE]
> 31 Mart 2016 itibariyle tüm Xamarin, tüm Visual Studio sürümlerinde ek maliyet olmadan dahildir ve ayrı bir lisansa gerek kalmaz. Mac için Xamarin Studio Community, öğrenciler, OSS geliştiricileri ve küçük takımlar için de ücretsizdir. Visual Studio 'nun önceki Xamarin lisanslarıyla yapılandırılmış mevcut yüklemeleri için Xamarin ile sürüm 4.0.3.214 veya üstünü güncelleştirmeniz gerektiğini unutmayın. Bunu yapmak için, **Xamarin > ' > araçlar > seçenekler**' e gidin, **Şimdi Denetle** bağlantısına tıklayın ve 4.0.3.214 güncelleştirmesini indirin. Visual Studio 'Yu yeniden başlattığınızda, **> Xamarin Account... Araçlar** ' a gidin ve güncelleştirilmiş durumu görmeniz gerekir.  
  
 **Bu konuda:**  
  
- [Önkoşulların önkoşulları](#prereq)  
  
- [Windows kurulumu (Visual Studio ve Xamarin)](#windows)  
  
- [Mac Kurulumu (Apple KIMLIĞI, Xcode ve Xamarin)](#mac)  
  
## <a name="pre-requisites"></a><a name="prereq"></a> Önkoşulların önkoşulları  
  
1. Windows ve Android 'i hedeflemek için:  
  
    1. Önerilir: Android cihazınız yoksa, Android için hızlı, Hyper-V tabanlı Visual Studio öykünücüsü kullanılmasına izin veren Windows 8 veya üzerini çalıştıran fiziksel bir Windows bilgisayarı (VM değil). (Bir VM 'ye değil fiziksel bir bilgisayar mı gerektiğini bahsettik mi?)  
  
    1. Windows 7 veya daha önceki bir sürümü olan bir bilgisayar kullanabilirsiniz; Bu durumda, öykünücü olarak Android için Xamarin Player 'ı kullanırsınız. 
    
    1. Her iki yapılandırma için, uygulamaları her zaman doğrudan bağlı fiziksel cihazlarda çalıştırabilirsiniz.  
  
1. İOS hedeflemek için:  
  
    1. OS x 10.10.5 veya üstünü çalıştıran (Xcode 7,1 için gereklidir), OS X Yosemite ile ağa bağlı bir Mac veya Mac mini.  
  
    1. Birincil geliştirme ortamınız olarak bir Windows (7 +) bilgisayarında Visual Studio kullanırken, ağ bağlantılı bir Mac yalnızca iOS uygulamalarını derlemek ve hata ayıklamak, iOS simülatörü veya tethered cihazlarına eklemek ve Kullanıcı arabirimini tasarlamak için Visual Studio 'daki görsel taslak tasarımcısını kullanmak için gereklidir. Daha eski Mac modelleri bu ikincil rol için tamamen yeterlidir.  
  
## <a name="windows-setup-visual-studio-and-xamarin"></a><a name="windows"></a> Windows kurulumu (Visual Studio ve Xamarin)  
  
> [!TIP]
> Bu yönergeler Visual Studio 2015 için geçerlidir. Xamarin 'i Visual Studio 2013 kullanmak için (güncelleştirme 2 gereklidir), [doğrudan Xamarin install](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (Xamarin.com) yönergelerini izleyin.  
  
1. Herhangi bir Visual Studio 2015 (Community, Professional veya Enterprise) [sürümü için yükleyiciyi indirin ve başlatın](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) . Visual Studio 2015 Community, ücretsiz sürümdür; Profesyonel ve kurumsal sürümler, bir lisans satın almanız gereken 30 gün sonra deneme süresi boyunca kullanılabilir.  
  
   1. Zaten Visual Studio yüklüyse, **Denetim masası > programlar ve Özellikler**' i açın, **Visual Studio 2015** öğesini seçin ve **Değiştir**' e tıklayın. Yükleyici açıldığında **Değiştir** ' e tıklayın ve aşağıdaki 3. adıma atlayın.  
  
2. (Yalnızca yeni yüklemeler) Yükleyici içinde **özel** yükleme ' yi seçin:  
  
    ![Visual Studio yüklemesinde özel seçeneği seçme](../cross-platform/media/cross-plat-xamarin-setup-1.png "Çapraz Plat Xamarin Kurulum 1")  
  
3. Aşağıdaki kutuları işaretleyin:  
  
   1. **Platformlar arası mobil geliştirme > C#/.net (Xamarin)**. Ayrıca, ortak araçlar ve yazılım geliştirme setleri altında çeşitli Android araçları da otomatik olarak seçilecek. Bu seçenek ayrıca var olan Xamarin yüklemesini de güncelleştirmelidir.  
  
        ![&#45;platformlar arası Platform mobil geliştirme altında Xamarin seçeneğini belirleyin](../cross-platform/media/cross-plat-xamarin-setup-2.png "Çapraz Plat Xamarin Kurulum 2")  
  
   2. Windows 8 + için: **platformlar arası mobil geliştirme > Android için Microsoft Visual Studio öykünücüsü**. Note: bir Windows 7 veya daha önceki bir bilgisayar kullanıyorsanız veya Windows 'u bir Mac üzerinde çalıştırıyorsanız, bunun *işaretinin kaldırıldığından*emin olun. 5. adımdan sonra "Windows bilgisayarlarda Öykünücüler hakkında" bölümüne bakın. Ayrıca, yalnızca fiziksel Android cihazlarda hata ayıklamak istiyorsanız bu seçeneği işaretlenmemiş olarak bırakabilirsiniz.  
  
   3. Seçim Windows cihazlarını hedeflemeyi planlıyorsanız **Windows ve Web geliştirme > Evrensel Windows uygulaması geliştirme araçları** ve/veya **Windows 8.1 ve Windows Phone 8.0/8.1 araçları**' nı da denetleyin. Bunlar, indirmesi daha uzun sürecek olan öykünücü görüntülerini yüklemeye yönelik seçenekleri içerir; daha sonra eklemek için her zaman Visual Studio yükleyicisi 'ne dönebilirsiniz.  
  
4. Install düğmesine tıklayın ve işlemin çalışmasına izin verin. Bu işlem biraz zaman alabilir, bu sırada Mac kurulum yönergelerine devam edebilir ve [Xamarin ile mobil geliştirme hakkında bilgi edinebilirsiniz](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Yükleme tamamlandıktan sonra Visual Studio 'Yu başlatın ve istenirse Microsoft hesabı ile oturum açın (Bu, Windows ile kullandığınız hesaptır). Daha sonra, **> > Xamarin** veya **tools > > > seçenekler**aracılığıyla **Xamarin güncelleştirmelerini kontrol** edin.  
  
    ![Visual Studio seçeneklerinde Xamarin güncelleştirmelerini denetleme](../cross-platform/media/cross-plat-xamarin-setup-3.png "Çapraz Plat Xamarin kurulumu 3")  
  
   > [!NOTE]
   > Daha önce belirtildiği gibi, daha önce Xamarin lisanslarıyla ilgili sorunlardan kaçınmak için Xamarin 'i 4.0.3.214 veya üzeri bir sürüme güncelleştirdiğinizden emin olun.  

   **Araçlar > seçeneklerinde**Xamarin için bir seçenek görmüyorsanız, yüklemenizi iki kez kontrol edin veya Visual Studio 'yu yeniden başlatmayı deneyin. Ayrıca Seçenekler iletişim kutusunda Xamarin araması yapabilirsiniz.
      
6. Windows 7 ve önceki sürümlerde veya bir Mac üzerinde Windows 'u çalıştırmak için fiziksel cihazlarınız yoksa [Android SDK öykünücüsü](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) kullanın. Aşağıdaki nota bakın.  
  
   **Windows bilgisayarlarda Öykünücüler hakkında bilgi:** Her seferinde yalnızca bir sanallaştırma teknolojisini desteklediği için, yalnızca bir geliştirme bilgisayarında kullanılması en iyisidir. Hyper-V (Android için Visual Studio öykünücüsü ve Windows Phone öykünücüsü tarafından kullanılır), sanal kutu (Genymotion tarafından kullanılan) ve Intel HAXM (Android SDK öykünücü tarafından kullanılan) için üç ana virtualtıs teknolojisi vardır. Hyper-V ve sanal kutu arasındaki çeşitli sorunlar nedeniyle, belirli bir bilgisayarda yalnızca bir tür öykünücüleri kullanmak en iyisidir. bu nedenle, Yukarıdaki öneriler, Windows 8 ve üzeri bilgisayarlarda Hyper-V ' y i ve Windows 7 ve daha önceki sürümlerde Intel HAXM öykünücüleri ve Windows 'un bir Mac üzerinde çalıştırıldığı durumlarda kullanılır.  
  
## <a name="mac-setup-apple-id-xcode-and-xamarin"></a><a name="mac"></a> Mac Kurulumu (Apple KIMLIĞI, Xcode ve Xamarin)  
  
1. Henüz bir tane yoksa, ücretsiz bir Apple KIMLIĞI oluşturun [https://appleid.apple.com](https://appleid.apple.com/) . Bu, Xcode 'a yükleme ve oturum açmada gereklidir.  
  
2. Xcode ' u indirip yükleyin ve  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) Apple Kimliğinizi, [Hesabınızı Xcode 'a ekleme](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Apple.com) bölümünde açıklandığı gibi ekleyin.  
  
3. [Xamarin. iOS (Xamarin.com) yükleme ve yapılandırma](/xamarin/ios/get-started/installation/mac) yönergelerini izleyerek Xamarin 'i indirin ve yükleyin.  
  
4. Hem Windows hem de Mac bilgisayarlara Xamarin 'i yüklemeyi tamamladıktan sonra, Windows bilgisayarında Visual Studio 'dan iOS ve Mac ile çalışabilmek [Için Mac 'e bağlanma](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) (Xamarin.com) yönergelerini izleyin.  
  
     Her iki bilgisayarın da aynı yerel ağda olması gerektiğini unutmayın.
