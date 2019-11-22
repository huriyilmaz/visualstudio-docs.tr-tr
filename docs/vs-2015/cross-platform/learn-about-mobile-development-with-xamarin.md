---
title: Xamarin ile mobil geliştirme hakkında bilgi edinin | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 9924eee661f917334aed586506a107486cd5be0f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299772"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Xamarin ile mobil geliştirme hakkında bilgi edinin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, Xamarin ile platformlar arası mobil uygulamalar geliştirmeyi anlamanıza yardımcı olan malzemeye genel bakış sunmaktadır. Visual Studio ve Xamarin 'i henüz yüklemediyseniz, önce [Kurulum ve yükleme](../cross-platform/setup-and-install.md) işlemini başlatın, sonra yükleyiciler çalışırken bu kaynaklar aracılığıyla çalışmak için buraya geri dönün.  
  
> [!NOTE]
> Aksi belirtilmediği takdirde, başlangıçta yalnızca buradan bağlantılı olan sayfaları ve yan kuruluş sayfalarını okumayı öneririz. Bu liste tamamlandıktan sonra yükleme işlemi çalışmaya devam ediyorsa, geri dönüp ek konuları araştırmaya başlayabilirsiniz.  
>   
> Ayrıca "Essentials" olarak işaretlenmiş konuları gözden geçirmek ve daha sonra "daha derin izleme" konularına geri dönebilirsin.  
  
## <a name="essentials-introduction-to-xamarin"></a>Temel bilgiler: Xamarin 'e giriş  
 *10-20 dakika*  
  
1. [Xamarin Ile Visual Studio 'daki Mobile Apps](https://www.visualstudio.com/explore/xamarin-vs) (VisualStudio.com) Xamarin 'in birincil özelliklerinin çok kısa bir özetini sağlar.  
  
2. [Visual Studio C# ](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9, 15m16s) kullanarak ve Xamarin Evangelist, James Montemagno Ile platformlar arası Mobile Apps oluşturma. İlk üç dakika, bir Xamarin genel bakıştır ve ardından kod gösterileri izler.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Essentials: Visual Studio ve Xamarin ortamına genel bakış  
 *5-15 dakika*  
  
- Visual Studio ve Xamarin ile Windows bilgisayarı, çalışmanızın büyük bir kısmını nerede yapacaksınız. Bu bilgisayarda, doğrudan Windows ve Android uygulamaları oluşturup bunları bir cihazda veya Öykünücüde hata ayıkladığınızda çalıştırın. Ayrıca, Mac aracılığıyla iOS uygulamalarını uzaktan oluşturur, çalıştırır ve hatalarını ayıklayın. Windows bilgisayarındaki Visual Studio, iOS görsel taslak tasarımcısına ve iOS simülatörünü de bağlanabilir.  
  
- Xcode ve Xamarin ile Mac, iOS uygulamaları için yapı/imzalama Konağı ve çalışma zamanı ortamı olarak hizmet verir. Windows bilgisayarında Visual Studio 'dan iOS için derlemeler bu Mac için temsilci olarak atanır; Visual Studio 'dan bir iOS uygulamasında hata ayıklarken, Mac 'teki iOS benzeticisinde veya doğrudan Mac 'e bağlı bir tethered cihazında çalışır. Bu durumda, Mac üzerinde veya yakınında uygulamayla etkileşime geçmeniz ve Visual Studio 'da hata ayıklama deneyiminizi yapmanız gerekir.  
  
  Bu ilişkiler aşağıda gösterilmektedir ve [Visual Studio Için Xamarin. iOS 'A giriş bölümünde](https://docs.microsoft.com/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio) iOS uygulamalarıyla çalışma hakkında daha fazla bilgi edinebilirsiniz (Xamarin.com).  
  
  ![Xamarin ortamında Windows ve Mac dev bilgisayarları arasındaki ilişki](../cross-platform/media/crossplat-xamarin-learn-1.png "Çapraz Splat Xamarin öğrenme 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Essentials: projeler nasıl yapılandırılır?  
 *10-30 dakika*  
  
1. [Kod seçeneklerini paylaşma](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin.com). Yalnızca tüm hedef platformlarda desteklenen .NET API 'Lerini kullanmayı en iyi şekilde desteklediği için taşınabilir sınıf kitaplıkları seçeneğini kullanmanızı öneririz. Çoğu iş mantığı kodu, veritabanlarına erişim, REST API çağrılarına çağrı ve taşınabilir Xamarin bileşenlerine çağrı dahil olmak üzere PCL 'de yer alır (Bu konunun sonunda bkz. daha [derin bakış: Xamarin bileşenleri](#components) ). Xamarin. Forms ile yazılan ortak kullanıcı arabirimi kodu ayrıca bir PCL 'de bulunabilir.  
  
2. Seçim [Örnek olay incelemesi: Tasky](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky) (Xamarin.com), projeyi, verileri, veri erişimini ve iş katmanlarını ayıran paylaşılan kod IÇIN bir PCL ile yapılandırma gibi tam özellikli bir uygulamanın tasarım ve yapısına yönelik bazı en iyi yöntemleri açıklar.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Essentials: yerel ve Xamarin. Forms Kullanıcı arabirimi katmanları  
 *10-40 dakika*  
  
 Xamarin, harika yerel uygulamalar oluşturmak için iki yol sunar: Xamarin Native ve Xamarin. Forms.  
  
 Xamarin Native ile her hedef platform için ayrı kullanıcı arabirimi kodu yazarsınız: iOS, Android ve Windows.  Bu yaklaşımda platforma özgü API 'lere doğrudan erişim sahibi olursunuz ve bu, platform başına özelleştirilmiş bir kullanıcı arabirimi deneyimine izin verir.  Ayrıca, ilgili Kullanıcı arabirimini oluşturmaya yardımcı olmak üzere her platform için yerel tasarımcı ve denetimlere tam erişime sahip olursunuz.  
  
 Xamarin. Forms, taşınabilir bir sınıf kitaplığındaki tüm platformlar için paylaşılan bir UI katmanı yazmanıza imkan tanıyan genelleştirilmiş bir API kümesi sağlar.  Xamarin. Forms, yerel bir görünüm sağlamak için her bir hedef platformda yerel denetimler oluşturur.  Xamarin. Forms ile tasarımcı kullanmak yerine, ve XAML kullanarak C# Kullanıcı arabiriminizi derleyebilirsiniz.  
  
 En baştan gerçekleştirilecek yaklaşımı belirlemeniz gerekmez; uygulamalar, Xamarin Native ve Xamarin. Forms öğelerinin bir birleşimi kullanılarak uygulanabilir:  
  
- Oturum açma bilgileri, iletişim formları ve arama sonuçları gibi platformlar arasında benzer kullanıcı arabirimi ve yetenekler sağlayan genel amaçlı ekranlar oluşturmak için Xamarin. Forms kullanın.  
  
- Kullanıcı arabirimini platform temelinde ayarlamak için Xamarin. Forms içindeki çeşitli özelleştirme yeteneklerini kullanın. Bunlar hem koddan hem XAML 'den kullanılabilen OnPlatform API 'sini, özel bir görünüm oluşturmayı, var olan bir oluşturucuyu genişletmeyi ve özel bir işleyici oluşturmayı içerir.  
  
- Gerekirse, her platformun benzersiz kullanıcı arabirimi özelliklerini kullanan ekranlar oluşturmak için Xamarin Native kullanın, örneğin, yerel kamera yakalama ve görüntü işleme kullanan bir ekran.  
  
  Platformlar arasında UI kodu paylaşımı ayarlamak ve platforma özgü ayarlamalar yapmak için özelleştirme yeteneklerini kullanmak için her zaman bir Xamarin. Forms çözümüyle başlamasını öneririz. Tek başına platforma özgü ekranlar gerekiyorsa, Xamarin Native kullanarak bunları ayrı ayrı ekleyebilirsiniz.  
  
  Daha fazla bilgi için:  
  
1. [Xamarin. Forms](https://docs.microsoft.com/xamarin/xamarin-forms/) (Xamarin.com), Xamarin. Forms ve yerel UI katmanlarının (yani, Xamarin. IOS ve Xamarin. Android) genel bir genel bakış ve olumlu yönleri sağlar.  
  
2. James Montemagno 'ın video [Xamarin. Forms: Native iOS, Android & & xaml Ile C# Windows uygulamaları](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9, 13m3s), başka bir genel bakış sağlar ve tanıtımlar için izlemeye devam edebilirsiniz.  
  
3. Seçim [Xamarin. Forms 'A giriş](https://docs.microsoft.com/xamarin/get-started/quickstarts/deepdive?pivots=windows) (Xamarin.com)  
  
4. Seçim [Cihaz sınıfı](https://docs.microsoft.com/xamarin/xamarin-forms/platform/device) belgelerinde özelleştirme Için onplatform kullanma örneklerine bakın (Xamarin.com)  
  
5. Seçim Jason Smith (MSDN Magazine) ile [Xamarin. Forms Ile mobil platformlar arasında platformlar arası paylaşılan kullanıcı arabirimi kodu](https://msdn.microsoft.com/magazine/dn904669.aspx) , Xamarin. Forms içinde farklı özelleştirme seçeneklerini özetler ve bu sayede ayrıntılar, [her platformda denetimleri özelleştirme](https://docs.microsoft.com/xamarin/xamarin-forms/app-fundamentals/custom-renderer/) konusunda ele alınmıştır (Xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Daha derin bakış: Öykünücülerle hata ayıklama  
 *10-15 dakika*  
  
 Fiziksel bir cihaz kullanmak zorunda kalmadan platformlar arası uygulamalarınızda hata ayıklamak için aşağıdakileri kullanmanız gerekir:  
  
1. **Android öykünücüsü.** Kullandığınız Windows sürümüne bağlı olarak, her ikisi de hızlı performans sunan ve çeşitli cihaz yeteneklerini destekleyen, Microsoft 'un Android için Visual Studio öykünücüsü veya Xamarin Player önerilir:  
  
    - **Windows 8 + makineler:** Visual Studio ile birlikte yüklenen [Android Için Microsoft 'un Visual Studio öykünücüsü](https://www.visualstudio.com/features/msft-android-emulator-vs.aspx)' nü kullanmanızı kesinlikle öneririz.  [Android Için Visual Studio öykünücüsü](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) videosu (Channel9, 5m55s) bir genel bakış ve tanıtım sağlar.  
  
    - **Windows 7 veya önceki sürümleri/Mac OS X çalışıyor**: [Xamarin Android Player](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (Xamarin.com) kullanın.  
  
2. **Apple 'ın iOS simülatörü.** Daha fazla bilgi edinmek için [IOS simülatörü](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (Apple.com) ile çalışmaya başlama makalesini okuyun.  
  
3. **Microsoft 'un Windows Phone öykünücüsü.** Daha fazla bilgi edinmek için [Windows Phone 8 için Windows Phone öykünücüsü](https://msdn.microsoft.com/library/dn632391.aspx)makalesini okuyun.  
  
## <a name="components"></a>Daha derin bakış: Xamarin bileşenleri  
 *10 dakika*  
  
 Xamarin bileşenleri aracılığıyla Xamarin uygulamaları için çok sayıda genişletilmiş özellik mevcuttur. Ek kullanıcı arabirimi denetimleri, kimlik doğrulaması, Microsoft Azure gibi çeşitli bulut hizmetleri ve çok daha fazlası için bileşenleri içeren [http://components.xamarin.com/](https://docs.microsoft.com/xamarin/cross-platform/troubleshooting/component-nuget?tabs=windows)' de indirilebilir şekilde kullanılabilecek tam kataloğu bulabilirsiniz.
