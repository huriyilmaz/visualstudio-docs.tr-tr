---
title: Platformlar Arası Mobil Geliştirme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 1efc8ea7f40c3098e681cc80ac90789b629630a9
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302492"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio’da Platformlar Arası Mobil Geliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'u kullanarak Android, iOS ve Windows cihazları için uygulamalar oluşturabilirsiniz.  Uygulamanızı tasarlarken, Office 365, Azure Uygulama Hizmeti ve Uygulama Öngörüleri gibi bağlantılı hizmetleri kolayca eklemek için Visual Studio'da araçları kullanın.

 C# ve .NET Framework, HTML ve JavaScript veya C++'ı kullanarak uygulamalarınızı oluşturun. Kodu, dizeleri, görüntüleri ve hatta bazı durumlarda kullanıcı arabirimini paylaşın.

 Bir oyun veya sürükleyici grafik uygulaması oluşturmak istiyorsanız, Unity için Visual Studio araçlarını yükleyin ve iOS, Android, Windows ve diğer platformlarda çalışan uygulamalar için popüler platformlar arası oyun/grafik motoru ve geliştirme ortamı olan Visual Studio with Unity'nin tüm güçlü üretkenlik özelliklerinin keyfini çıkarın.

 **Bu makalede:**

- [Android, iOS ve Windows (.NET Framework) için bir uygulama oluşturma](#NET)

  - [Android, iOS ve Windows'u tek bir kod tabanından hedefleme](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Hedef Windows 10 cihazları](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Android, iOS ve Windows (HTML/JavaScript) için bir uygulama oluşturma](#HTML)

- [Android ve Windows (C++) için bir uygulama oluşturma](#CPP)

- [Unity için Visual Studio araçlarını kullanarak Android, iOS ve Windows için bir çapraz platform oyunu oluşturun](#Unity)

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a><a name="NET"></a>Android, iOS ve Windows (.NET Framework) için bir uygulama oluşturma
 ![Cihazlar](../cross-platform/media/homedevices.png "AnasayfaCihazlar")

 Xamarin ile Android, iOS ve Windows'u aynı çözümde, kod paylaşımında ve hatta UI'de hedefleyebilirsiniz.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Visual Studio Yükle](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Visual Studio'da Xamarin hakkında bilgi edinin](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio ve Xamarin](../cross-platform/visual-studio-and-xamarin.md) (MSDN Kütüphanesi)|
|[Xamarin uygulamalarıyla Uygulama Yaşam Döngüsü Yönetimi (ALM)](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (MSDN Kütüphanesi)|
|[Visual Studio'daki evrensel Windows uygulamaları hakkında bilgi edinin](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Swift ve C#](https://aka.ms/scposter) (download.microsoft.com) arasındaki benzerlikler hakkında bilgi edinin|
|[Android için Visual Studio Emülatörü](https://visualstudio.microsoft.com/vs/msft-android-emulator/) hakkında bilgi edinin (VisualStudio.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a>Android, iOS ve Windows'u tek bir kod tabanından hedefleme
 C# veya F# (Visual Basic şu anda desteklenmez) kullanarak Android, iOS ve Windows için yerel uygulamalar oluşturabilirsiniz.  Başlamak için Visual Studio 2015'i yükleyin, yükleyicide **Özel** seçeneğini seçin ve **Çapraz Platform Mobil Geliştirme > C#/.NET (Xamarin)** altındaki kutuyu işaretleyin. Ayrıca Visual Studio 2013 için Xamarin yüklemek için gerekli olan [Xamarin Installer](https://www.xamarin.com/download)ile başlayabilirsiniz.

 Visual Studio 2015 yüklüyse, **Denetim Masası > Program ve Özellikleri'nden** yükleyiciyi çalıştırın ve Xamarin için yukarıdaki gibi aynı **Özel** seçeneği seçin.

 İşi bittiğinde, proje şablonları **Yeni Proje** iletişim kutusunda görünür. Xamarin şablonlarını bulmanın en kolay yolu "Xamarin"de arama yapmaktır.

 Xamarin, Android, iOS ve Windows'un yerel işlevselliğini .NET nesneleri olarak ortaya çıkarır. Böylece uygulamalarınız yerel API'lere ve yerel kullanıcı denetimlerine tam erişime sahiptir ve bunlar da yerel platform dillerinde yazılmış uygulamalar kadar duyarlıdır.

 Bir proje oluşturduktan sonra Visual Studio'nun tüm üretkenlik özelliklerinden yararlanırsınız. Örneğin, sayfalarınızı oluşturmak için bir tasarımcı kullanır sınız ve mobil platformların yerel API'lerini keşfetmek için IntelliSense'i kullanırsınız. Uygulamanızı çalıştırmaya ve nasıl göründüğünü görmeye hazır olduğunuzda, Android veya Android SDK emülatörü için Visual Studio Emülatörü kullanabilir, Windows uygulamalarını yerel olarak çalıştırabilir veya Windows Phone emülatöründe Windows uygulamalarını çalıştırabilirsiniz. Bağlı Android ve Windows cihazlarını doğrudan da kullanabilirsiniz. iOS projeleri için ağa bağlı bir Mac'e bağlanın ve Visual Studio'dan Mac emülatörü başlatın veya bağlı bir aygıta bağlanın.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Xamarin.Forms kullanarak tüm cihazlarda işlenen bir sayfa kümesi tasarla
 Uygulama tasarımınızın karmaşıklığına bağlı olarak, proje şablonları Mobil **Uygulamalar** grubunda *Xamarin.Forms* şablonlarını kullanarak bu tasarımı oluşturmayı düşünebilirsiniz. Xamarin.Forms, Android, iOS ve Windows arasında paylaşabileceğiniz tek bir arabirim oluşturmanıza olanak tanıyan bir Ara bilgi aracı araç setidir.  Bir Xamarin.Forms çözümü derlediğinizde, bir Android uygulaması, bir iOS uygulaması ve bir Windows uygulaması alırsınız. Daha fazla bilgi için [Xamarin ile mobil geliştirme hakkında bilgi](../cross-platform/learn-about-mobile-development-with-xamarin.md)edinin.

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a>Android, iOS ve Windows uygulamaları arasında kod paylaşma
 Xamarin.Forms kullanmıyorsanız ve her platform için ayrı ayrı tasarım yapmayı seçiyorsanız, UI olmayan kodlarınızın çoğunu platform projeleri (Android, iOS ve Windows) arasında paylaşabilirsiniz. Bu, herhangi bir iş mantığını, bulut tümleştirmesini, veritabanı erişimini veya .NET Framework'u hedefleyen diğer kodları içerir. Paylaşamadığınız tek kod, belirli bir platformu hedefleyen koddur.

 ![Windows, iOs ve Android UI arasında kod paylaşma](../cross-platform/media/sharecode.png "Paylaşım Kodu")

 Paylaşılan bir projeyi, Taşınabilir Sınıf Kitaplığı projesini veya her ikisini de kullanarak kodunuzu paylaşabilirsiniz. Paylaşılan bir projede bazı kodların en uygun olduğunu ve bazı kodların Taşınabilir Sınıf Kitaplığı projesinde daha mantıklı olduğunu görebilirsiniz.

|**Daha fazlasını öğrenin**|
|--------------------|
|Paylaşılan projeleri, Taşınabilir Sınıf Kitaplığı projelerini veya her ikisini kullanarak kodunuzu paylaşıp paylaşmayacağınızı seçin.<br /><br /> [Platformlar arasında kod paylaşımı](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (.NET Framework blog)<br /><br /> [Kod Seçeneklerini Paylaşma](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [.NET Framework](https://msdn.microsoft.com/library/dn720832.aspx) (MSDN Kitaplığı) ile kod paylaşım seçenekleri|

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Hedef Windows 10 cihazları
 ![Windows Cihazları](../cross-platform/media/windowsdevices.png "WindowsCihazlar")

 Windows 10 cihazlarının tüm genişliğini hedefleyen tek bir uygulama oluşturmak istiyorsanız, evrensel bir Windows uygulaması oluşturun. Uygulamayı tek bir proje kullanarak tasarlarsınız ve sayfalarınız bunları görüntülemek için hangi cihaz kullanılırsa kullanılsın düzgün bir şekilde işlenir.

 Evrensel bir Windows uygulaması proje şablonuyla başlayın. Sayfalarınızı görsel olarak tasarlayın ve ardından çeşitli aygıt türleri için nasıl göründüklerini görmek için bunları önizleme penceresinde açın. Bir sayfanın aygıtta nasıl göründüğünü beğenmezseniz, sayfayı ekran boyutuna, çözünürlüğe veya yatay veya dikey mod gibi çeşitli yönlendirmelere daha iyi uyacak şekilde optimize edebilirsiniz. Tüm bunları Visual Studio'da sezgisel araç pencerelerini ve kolayca erişilebilen menü seçeneklerini kullanarak yapabilirsiniz. Uygulamanızı çalıştırmaya ve kodunuzu aşmaya hazır olduğunuzda, farklı türdeki aygıtların tüm cihaz emülatörlerini ve simülatörlerini **Standart** araç çubuğunda bulunan tek bir açılır listede bir arada bulabilirsiniz.

 Windows 10 oldukça yeniolduğundan, Windows 8.1'i hedefleyen proje şablonlarını da bulabilirsiniz. İsterseniz bu proje şablonlarını kullanabilirsiniz ve uygulamanız Windows 10 telefonlarda, tabletlerde ve bilgisayarlarında çalışır. Ancak, Windows 8.1 çalıştıran tüm aygıtlar Windows 10'a otomatik yükseltme alır, bu nedenle Windows 8.1'i hedeflemek için belirli nedenlerden önce niz yoksa, Windows 10'u hedefleyen proje şablonlarını kullanmanızı öneririz.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Evrensel Windows uygulamaları hakkında bilgi edinin](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Geliştirme Center)|
|[İlkinizi oluşturun](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Geliştirme Merkezi)|
|[Evrensel Windows Platformu (UWP) için uygulama geliştirme](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Uygulamaları Evrensel Windows Platformu’na (UWP) geçirme](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Android, iOS ve Windows (HTML/JavaScript) için bir uygulama oluşturma
 ![Cihazlar](../cross-platform/media/homedevices.png "AnasayfaCihazlar")

 Bir web geliştiricisiyseniz ve HTML ve JavaScript'e aşinaysanız, Apache Cordova için Visual Studio Araçlarını kullanarak Windows, Android ve iOS'u hedefleyebilirsiniz. Bu uygulamalar üç platformu da hedefleyebilir ve en çok aşina olduğunuz becerileri ve süreçleri kullanarak bunları oluşturabilirsiniz.

 Apache Cordova bir eklenti modeli içeren bir çerçevedir. Bu eklenti modeli, her üç platformun (Android, iOS ve Windows) yerel aygıt özelliklerine erişmek için kullanabileceğiniz tek bir JavaScript API sağlar.

 Bu API'ler çapraz platform olduğundan, yazdıklarının çoğunu üç platform arasında paylaşabilirsiniz. Bu, geliştirme ve bakım maliyetlerinizi azaltır. Ayrıca, sıfırdan başlamaya gerek yok. Başka web uygulamaları oluşturduysanız, bu dosyaları herhangi bir şekilde değiştirmek veya yeniden tasarlamak zorunda kalmadan Cordova uygulamanızla paylaşabilirsiniz.

 ![Çoklu&#45;Cihazı Hibrit Uygulamaları](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Başlamak için Visual Studio 2015'i yükleyin ve kurulum sırasında **HTML/JavaScript (Apache Cordova)** özelliğini seçin. Visual Studio 2013 kullanıyorsanız, Apache Cordova uzantısı için Visual Studio Araçlarını yükleyin. Her iki şekilde de, Cordova araçları çok platformlu uygulamanızı oluşturmak için gereken tüm üçüncü taraf yazılımlarını otomatik olarak yükler.

 Uzantıyı yükledikten sonra Visual Studio'yu açın ve boş bir **uygulama (Apache Cordova)** projesi oluşturun. Ardından, JavaScript veya Typescript kullanarak uygulamanızı geliştirebilirsiniz. Ayrıca uygulamanızın işlevselliğini genişletmek için eklentiler ekleyebilirsiniz ve kod yazarken eklentilerden gelen API'ler IntelliSense'de görünür.

 Uygulamanızı çalıştırmaya ve kodunuzu aşmaya hazır olduğunuzda, Apache Ripple emülatörü veya Visual Studio Emülatörü (Android veya Windows Phone), bir tarayıcı veya doğrudan bilgisayarınıza bağladığınız bir aygıt gibi bir emülatör seçin. Ardından uygulamanızı başlatın. Uygulamanızı bir Windows PC'de geliştiriyorsanız, uygulamanızı bu bilgisayarda bile çalıştırabilirsiniz. Tüm bu seçenekler, Apache Cordova için Visual Studio Tools'un bir parçası olarak Visual Studio'da bulunmaktadır.

 Evrensel Windows uygulamaları oluşturmak için proje şablonları Visual Studio'da hala mevcuttur, bu nedenle yalnızca Windows aygıtlarını hedeflemeyi planlıyorsanız bunları kullanmaktan çekinmeyin. Android ve iOS'u daha sonra hedeflemeye karar verirseniz, kodunuzu her zaman bir Cordova projesine bağlayabilirsiniz. WinJS API'lerinin açık kaynak sürümleri vardır, böylece bu API'leri tüketen tüm kodları yeniden kullanabilirsiniz. Bununla birlikte, gelecekte diğer platformları hedeflemeyi planlıyorsanız, Apache Cordova için Visual Studio Tools ile başlamanızı öneririz.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Visual Studio Yükle](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Apache Cordova için Visual Studio Tools (taco.visualstudio.com) ile başlayın](/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017)|
|[Android için Visual Studio Emülatörü](https://visualstudio.microsoft.com/vs/msft-android-emulator/) hakkında bilgi edinin (VisualStudio.com)|

## <a name="build-an-app-for-android-and-windows-c"></a><a name="CPP"></a>Android ve Windows (C++) için bir uygulama oluşturma
 ![Android, iOS ve Windows için oluşturmak için C&#43;&#43; kullanın](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 İlk olarak, Cross Platform Mobil Geliştirme araçları için Visual Studio 2015 ve Visual C++'ı yükleyin. Ardından, Android için yerel bir etkinlik uygulaması veya Windows'u hedefleyen bir uygulama oluşturabilirsiniz. iOS'u hedefleyen C++ şablonları henüz kullanılamıyor. İsterseniz Android ve Windows'u aynı çözümde hedefleyebilir ve ardından çapraz platform statik veya dinamik paylaşılan kitaplığı kullanarak aralarında kod paylaşabilirsiniz.

 Android için oyun gibi her türlü gelişmiş grafik manipülasyonu gerektiren bir uygulama oluşturmanız gerekiyorsa, bunu yapmak için C++'yı kullanabilirsiniz. **Yerel Etkinlik Uygulaması (Android)** projesiyle başlayın. Bu proje Clang araç zinciri için tam destek vardır.

 ![Yerel etkinlik proje şablonu](../cross-platform/media/cross-plat-cpp-native.png "Çapraz Plat_CPP_Native")

 Uygulamanızı çalıştırmaya ve nasıl göründüğünü görmeye hazır olduğunuzda, Android için Visual Studio Emülatörü kullanın. Hızlı, güvenilir ve kurulumu ve yapılandırılması kolaydır.

 Ayrıca, C++ ve evrensel bir Windows uygulaması proje şablonu kullanarak Windows 10 cihazlarının tüm genişliğini hedefleyen bir uygulama da oluşturabilirsiniz. Bu konuda daha önce bu konuda görünen [Hedef Windows 10 aygıtları](#WindowsHTML) bölümünde daha fazla bilgi edinin.

 Statik veya dinamik paylaşılan kitaplık oluşturarak Android ve Windows arasında C++ kodunu paylaşabilirsiniz.

 ![Statik ve dinamik paylaşılan kitaplıklar](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Bu kitaplığı, bu bölümde daha önce açıklananlar gibi bir Windows veya Android projesinde tüketebilirsiniz. Ayrıca, Xamarin, Java veya yönetilmeyen bir DLL'deki işlevleri çağırmanızı sağlayan herhangi bir dilde kullanarak oluşturduğunuz bir uygulamada da tüketebilirsiniz.

 Bu kitaplıklara kod yazarken, Android ve Windows platformlarının yerel API'lerini keşfetmek için IntelliSense'i kullanabilirsiniz. Bu kitaplık projeleri Visual Studio hata ayıklayıcıile tamamen entegre edilmiştir, böylece kesme noktaları ayarlayabilir, koda adım atabilir ve hata ayıklayıcının tüm gelişmiş özelliklerini kullanarak sorunları bulabilir ve düzeltebilirsiniz.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Visual Studio'yı indirin.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Platformötesi Mobil Geliştirme araçları için Visual C++ 'yı yükleyin.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Kütüphanesi)|
|[Birden çok platformu hedeflemek için C++ kullanma hakkında daha fazla bilgi edinin.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[İhtiyacınız olanı yükleyin ve ardından Android için yerel etkinlik uygulaması oluşturun](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Kitaplığı)|
|[Android için Visual Studio Emülatörü](https://visualstudio.microsoft.com/vs/msft-android-emulator/) hakkında bilgi edinin (VisualStudio.com)|
|[C++ kodunu Android ve Windows uygulamalarıyla paylaşma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[C++](https://msdn.microsoft.com/library/dn707596.aspx) (MSDN Kitaplığı) için platform ötesi mobil geliştirme örnekleri|
|[C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn) için ek çapraz platform mobil geliştirme örnekleri|

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a><a name="Unity"></a>Unity için Visual Studio araçlarını kullanarak Android, iOS ve Windows için bir çapraz platform oyunu oluşturun
 Visual Studio Tools for Unity, Visual Studio'nun güçlü kod düzenleme, üretkenlik ve hata ayıklama araçlarını *Windows,* iOS, Android ve web gibi diğer platformları hedefleyen sürükleyici uygulamalar için popüler platformlar arası oyun/grafik motoru ve geliştirme ortamı yla birleştiren Visual Studio için ücretsiz bir uzantıdır.

 ![VSTU geliştirme ortamı](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Visual Studio Tools for Unity (VSTU) ile Visual Studio'yu kullanarak C#'da oyun ve editör komut dosyaları yazabilir ve ardından hataları bulmak ve düzeltmek için güçlü hata ayıklama aracını kullanabilirsiniz. VSTU'nun en son sürümü Unity 5'e destek getirir ve Unity'nin ShaderLab gölgeli dili için sözdizimi boyama, Unity ile daha iyi senkronizasyon, daha zengin hata ayıklama ve MonoBehavior sihirbazı için geliştirilmiş kod oluşturma içerir. VSTU ayrıca Unity proje dosyalarınızı, konsol mesajlarınızı ve oyununuzu Visual Studio'ya başlatabilme yeteneğinizi de getirir, böylece kod yazarken Unity Editor'a geçiş yapmak için daha az zaman harcayabilirsiniz.

 Birlik ve Görsel Stüdyo Araçları ile oyununuzu bugün oluşturmaya başlayın.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Visual Studio ile Unity oyunları oluşturma hakkında daha fazla bilgi edinin](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) (MSDN Library) hakkında daha fazla bilgi edinin|
|[Unity için Visual Studio Araçlarını kullanmaya başlayın](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (MSDN Kitaplığı)|
|[Unity 2.0 Önizleme için Visual Studio Tools en son geliştirmeleri hakkında bilgi edinin](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio blog)|
|[Unity 2.0 Önizleme için Visual Studio Tools'a bir video girişi izleyin](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (Video)|
|[Unity (Unity](https://unity.com/) web sitesi) hakkında bilgi edinin|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio projesine Office 365 API'lerini ekleme](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure Mobile Hizmetleri](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Uygulama Bilgileri](/azure/application-insights/app-insights-overview)
