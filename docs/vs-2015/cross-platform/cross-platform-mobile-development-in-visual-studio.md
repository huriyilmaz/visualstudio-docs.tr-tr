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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312762"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio’da Platformlar Arası Mobil Geliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'Yu kullanarak Android, iOS ve Windows cihazları için uygulamalar oluşturabilirsiniz.  Uygulamanızı tasarlarken, Office 365, Azure App Service ve Application Insights gibi bağlı hizmetleri kolayca eklemek için Visual Studio 'daki araçları kullanın.

 C# ve .NET Framework, HTML ve JavaScript ya da C++ kullanarak uygulamalarınızı oluşturun. Kod, dizeler, görüntüler ve bazı durumlarda kullanıcı arabiriminden bile paylaşabilirsiniz.

 Bir oyun veya derinlikli grafik uygulaması oluşturmak istiyorsanız, Unity için Visual Studio Araçları 'nı yükler ve iOS, Android, Windows ve diğer platformlarda çalışan uygulamalar için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı olan Unity ile Visual Studio 'nun güçlü üretkenlik özelliklerinin tümünden yararlanın.

 **Bu makalede:**

- [Android, iOS ve Windows için uygulama oluşturma (.NET Framework)](#NET)

  - [Tek bir kod tabanında Android, iOS ve Windows 'u hedefleyin](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Hedef Windows 10 cihazları](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Android, iOS ve Windows için uygulama oluşturma (HTML/JavaScript)](#HTML)

- [Android ve Windows için uygulama oluşturma (C++)](#CPP)

- [Unity için Visual Studio Araçları 'nı kullanarak Android, iOS ve Windows için platformlar arası bir oyun oluşturun](#Unity)

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a><a name="NET"></a> Android, iOS ve Windows için uygulama oluşturma (.NET Framework)
 ![Cihazlar](../cross-platform/media/homedevices.png "HomeDevices")

 Xamarin ile Android, iOS ve Windows 'u aynı çözümde, kod paylaşarak ve hatta kullanıcı arabiriminden hedefleyebilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio 'yu](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com) yükler|
|[Visual Studio 'Da Xamarin hakkında bilgi edinin](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio ve Xamarin](../cross-platform/visual-studio-and-xamarin.md) (MSDN Kitaplığı)|
|[Xamarin uygulamalarıyla uygulama yaşam döngüsü yönetimi (ALM)](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (MSDN Kitaplığı)|
|[Visual Studio 'da Evrensel Windows uygulamaları hakkında bilgi edinin](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Swift ve C# arasındaki benzerlikler hakkında bilgi edinin](https://aka.ms/scposter) (download.Microsoft.com)|
|[Android Için Visual Studio öykünücüsü (VisualStudio.com) hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/msft-android-emulator/)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> Tek bir kod tabanında Android, iOS ve Windows 'u hedefleyin
 C# veya F # kullanarak Android, iOS ve Windows için yerel uygulamalar oluşturabilirsiniz (Visual Basic şu anda desteklenmez).  Başlamak için Visual Studio 2015 ' i yükledikten sonra yükleyicideki **özel** seçeneğini belirleyin ve **platformlar arası mobil geliştirme > C#/.net (Xamarin)** altındaki kutuyu işaretleyin. Ayrıca, Visual Studio 2013 için Xamarin 'i yüklemek için gereken [Xamarin yükleyicisi](https://www.xamarin.com/download)ile de başlayabilirsiniz.

 Visual Studio 2015 zaten yüklüyse, yükleyici 'yi **Denetim Masası 'ndan çalıştırın > programlar ve Özellikler** ' den çalıştırın ve yukarıdaki Xamarin Için aynı **özel** seçeneği belirleyin.

 İşiniz bittiğinde, proje şablonları **Yeni proje** iletişim kutusunda görünür. Xamarin şablonlarını bulmanın en kolay yolu yalnızca "Xamarin" üzerinde arama yapmak için kullanılır.

 Xamarin, Android, iOS ve Windows 'un .NET nesneleri olarak yerel işlevlerini kullanıma sunar. Böylece uygulamalarınızın yerel API 'Ler ve yerel kullanıcı denetimlerine tam erişimi vardır ve yalnızca yerel platform dillerinde yazılmış uygulamalar olarak yanıt verir.

 Bir proje oluşturduktan sonra, Visual Studio 'nun tüm üretkenlik özelliklerinden yararlanabilirsiniz. Örneğin, sayfalarınızı oluşturmak için bir tasarımcı kullanacaksınız ve mobil platformların yerel API 'leri araştırmak için IntelliSense kullanmanız gerekir. Uygulamanızı çalıştırmaya ve nasıl göründüğünü görebilmeniz için, Android için Visual Studio öykünücüsü 'nü veya Android SDK öykünücüsünü kullanabilir, Windows uygulamalarını yerel olarak çalıştırabilir veya Windows Phone öykünücü üzerinde Windows uygulamaları çalıştırabilirsiniz. Tethered Android ve Windows cihazlarını doğrudan de kullanabilirsiniz. İOS projeleri için, ağa bağlı bir Mac 'e bağlanın ve Visual Studio 'dan Mac öykünücüsünü başlatın veya bir tethered cihazına bağlanın.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Xamarin. Forms kullanarak tüm cihazlarda işlenen bir sayfa kümesi tasarlama
 Uygulama tasarımınızın karmaşıklığına bağlı olarak, proje şablonlarının **Mobile Apps** grubundaki *Xamarin. Forms* şablonlarını kullanarak oluşturmayı düşünebilirsiniz. Xamarin. Forms, Android, iOS ve Windows arasında paylaşabileceğiniz tek bir arabirim oluşturmanıza olanak sağlayan bir UI araç setidir.  Bir Xamarin. Forms çözümünü derlerken bir Android uygulaması, bir iOS uygulaması ve bir Windows uygulaması alırsınız. Daha fazla ayrıntı için bkz. [Xamarin ile mobil geliştirme hakkında bilgi edinin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> Android, iOS ve Windows uygulamaları arasında kod paylaşma
 Xamarin. Forms kullanmıyorsanız ve her platform için ayrı ayrı tasarlamayı seçerseniz, UI olmayan kodunuzun çoğunu platform projeleri (Android, iOS ve Windows) arasında paylaşabilirsiniz. Bu, herhangi bir iş mantığı, bulut tümleştirmesi, veritabanı erişimi veya .NET Framework hedefleyen herhangi bir kod içerir. Paylaşabileceğiniz tek kod, belirli bir platformu hedefleyen koddur.

 ![Windows, iOs ve Android kullanıcı arabirimi ile kod paylaşma](../cross-platform/media/sharecode.png "ShareCode")

 Kodunuzu paylaşılan bir proje, taşınabilir bir sınıf kitaplığı projesi veya her ikisini kullanarak paylaşabilirsiniz. Bazı kodların paylaşılan bir projede en iyi şekilde uyduğunu fark edebilirsiniz ve bazı kodlar taşınabilir bir sınıf kitaplığı projesi içinde daha anlamlı hale gelir.

|**Daha fazla bilgi edinin**|
|--------------------|
|Paylaşılan projeler, taşınabilir sınıf kitaplığı projeleri veya her ikisini de kullanarak kodunuzun paylaşılıp paylaşılmayacağını seçin.<br /><br /> [Platformlar arasında kod paylaşma](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (blog .NET Framework)<br /><br /> [Kod seçeneklerini paylaşma](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [.NET Framework Ile kod paylaşma seçenekleri](https://msdn.microsoft.com/library/dn720832.aspx) (MSDN Kitaplığı)|

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a> Hedef Windows 10 cihazları
 ![Windows cihazları](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Windows 10 cihazlarının tam kapsamını hedefleyen tek bir uygulama oluşturmak istiyorsanız, bir Evrensel Windows uygulaması oluşturun. Uygulamayı tek bir proje kullanarak tasarlayacaksınız ve sayfalar görüntülemek için kullanılan cihaz ne olduğuna göre düzgün şekilde işlenir.

 Bir Evrensel Windows uygulaması proje şablonuyla başlayın. Sayfalarınızı görsel olarak tasarlayın ve sonra çeşitli cihaz türleri için nasıl göründüğünü görmek için bunları bir önizleme penceresinde açın. Bir sayfada bir sayfanın nasıl göründüğünü beğenmezseniz, ekran boyutu, çözünürlüğü veya yatay veya dikey mod gibi çeşitli yönlerin daha iyi sığması için sayfayı en iyi hale getirebilirsiniz. Tüm bunları, Visual Studio 'da sezgisel araç pencerelerini ve kolayca erişilebilen menü seçeneklerini kullanarak yapabilirsiniz. Uygulamanızı çalıştırmaya ve kodunuzda ilerlemenize hazırsanız, **Standart** araç çubuğunda bulunan bir açılan listede farklı cihaz türleri için cihaz öykünücülerini ve simülatörleri tümünü bulacaksınız.

 Windows 10 oldukça yenidir, bu nedenle Windows 8.1 hedef olan proje şablonlarını da bulacaksınız. İsterseniz ve uygulamanız Windows 10 telefonlarında, tabletlerde ve bilgisayarlarda çalışacak şekilde bu proje şablonlarını kullanabilirsiniz. Ancak, Windows 8.1 çalıştıran tüm cihazlar Windows 10 ' a otomatik olarak yükseltme alır. bu nedenle, Windows 8.1 hedef olarak tercih etmeniz için bazı nedenleriniz yoksa, Windows 10 ' u hedefleyen proje şablonlarını kullanmanızı öneririz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Evrensel Windows uygulamaları](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Geliştirme Merkezi) hakkında bilgi edinin|
|[İlk birini oluşturma](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Geliştirme Merkezi)|
|[Evrensel Windows Platformu (UWP) için uygulama geliştirme](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Uygulamaları Evrensel Windows Platformu’na (UWP) geçirme](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a> Android, iOS ve Windows için uygulama oluşturma (HTML/JavaScript)
 ![Cihazlar](../cross-platform/media/homedevices.png "HomeDevices")

 Web geliştiricisiyseniz ve HTML ve JavaScript hakkında bilgi sahibiyseniz, Apache Cordova için Visual Studio Araçları kullanarak Windows, Android ve iOS 'u hedefleyebilirsiniz. Bu uygulamalar üç platformu da hedefleyebilir ve en çok bildiğiniz becerileri ve süreçlerini kullanarak bunları oluşturabilirsiniz.

 Apache Cordova, eklenti modeli içeren bir çerçevedir. Bu eklenti modeli, üç platformun (Android, iOS ve Windows) yerel cihaz özelliklerine erişmek için kullanabileceğiniz tek bir JavaScript API 'SI sağlar.

 Bu API 'Ler platformlar arası olduğundan, üç platform arasında yazdığınız kadar çoğunu paylaşabilirsiniz. Bu, geliştirme ve bakım maliyetlerinizi azaltır. Ayrıca, sıfırdan başlamak gerekmez. Başka türde Web uygulamaları oluşturduysanız, bunları dilediğiniz şekilde değiştirmek veya yeniden tasarlamanız gerekmeden bu dosyaları Cordova uygulamanızla paylaşabilirsiniz.

 ![Çoklu&#45;cihaz karma uygulamaları](../cross-platform/media/multidevicehybridapps.png "Multidevicehybridaps")

 Başlamak için Visual Studio 2015 ' yi yükleyip kurulum sırasında **HTML/JavaScript (Apache Cordova)** özelliğini seçin. Visual Studio 2013 kullanıyorsanız, Apache Cordova uzantısı için Visual Studio Araçları yükleyebilirsiniz. Her iki durumda da Cordova araçları, çok platformlu uygulamanızı derlemek için gereken tüm üçüncü taraf yazılımları otomatik olarak yükler.

 Uzantıyı yükledikten sonra, Visual Studio 'Yu açın ve **boş bir uygulama (Apache Cordova)** projesi oluşturun. Daha sonra, JavaScript veya TypeScript kullanarak uygulamanızı geliştirebilirsiniz. Ayrıca, uygulamanızın işlevlerini genişletmek için eklentiler ekleyebilirsiniz ve kod yazarken IntelliSense 'de bulunan API 'Ler görüntülenir.

 Uygulamanızı çalıştırmaya ve kodunuzda ilerledikten sonra, Apache Ripple öykünücüsü veya Visual Studio öykünücüsü (Android veya Windows Phone), tarayıcı veya doğrudan bilgisayarınıza bağladığınız bir cihaz gibi bir öykünücü seçin. Ardından, uygulamanızı başlatın. Uygulamanızı bir Windows bılgısayarda geliştiriyorsanız, hatta bunu da çalıştırabilirsiniz. Bu seçeneklerin tümü, Apache Cordova için Visual Studio Araçları bir parçası olarak Visual Studio 'da yerleşik olarak bulunur.

 Evrensel Windows uygulamaları oluşturmaya yönelik proje şablonları, Visual Studio 'da kullanılmaya devam etmektedir, ancak yalnızca Windows cihazlarını hedeflemesini planlıyorsanız bunları kullanabilirsiniz. Android ve iOS 'ı daha sonra hedeflemek isterseniz, kodunuzun her zaman bir Cordova projesine bağlantı noktası oluşturabilirsiniz. WinJS API 'lerinin açık kaynak sürümleri bulunur, bu nedenle bu API 'Leri tüketen tüm kodları yeniden kullanabilirsiniz. Bu şekilde, gelecekte diğer platformları hedeflemesini planlıyorsanız Apache Cordova için Visual Studio Araçları başlatmanız önerilir.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio 'yu](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com) yükler|
|[Apache Cordova için Visual Studio araçları kullanmaya başlama](/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (Taco.VisualStudio.com)|
|[Android Için Visual Studio öykünücüsü (VisualStudio.com) hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/msft-android-emulator/)|

## <a name="build-an-app-for-android-and-windows-c"></a><a name="CPP"></a> Android ve Windows için uygulama oluşturma (C++)
 ![Android, iOS ve Windows için derlemek üzere C&#43;&#43; kullanma](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 İlk olarak, Visual Studio 2015 'yi ve platformlar arası mobil geliştirme araçları 'nı Visual C++. Daha sonra, Android için yerel bir etkinlik uygulaması veya Windows 'u hedefleyen bir uygulama oluşturabilirsiniz. İOS 'ı hedefleyen C++ şablonları henüz kullanılabilir değil. İsterseniz Android ve Windows 'u aynı çözümde hedefleyebilir ve sonra platformlar arası statik veya dinamik Paylaşılan kitaplık kullanarak kod paylaşabilirsiniz.

 Bir oyun gibi gelişmiş grafik düzenlemesi gerektiren Android için bir uygulama derlemeniz gerekiyorsa, bunu yapmak için C++ kullanabilirsiniz. **Yerel etkinlik uygulaması (Android)** projesi ile başlayın. Bu proje, Clang toolzincirine yönelik tam desteğe sahiptir.

 ![Yerel etkinlik proje şablonu](../cross-platform/media/cross-plat-cpp-native.png "Çapraz Plat_CPP_Native")

 Uygulamanızı çalıştırmaya ve nasıl göründüğünü görebilmeniz için, Android için Visual Studio öykünücüsü ' nü kullanın. Hızlı, güvenilir ve kolayca yüklenebilir ve yapılandırılabilir.

 Ayrıca, C++ ve Evrensel Windows uygulaması proje şablonunu kullanarak Windows 10 cihazlarının tam kapsamını hedefleyen bir uygulama da oluşturabilirsiniz. Bu konuda daha önce görünen [hedef Windows 10 cihazları](#WindowsHTML) bölümünde bunun hakkında daha fazla bilgi edinin.

 Statik veya dinamik bir paylaşılan kitaplık oluşturarak, Android ve Windows arasında C++ kodu paylaşabilirsiniz.

 ![Statik ve dinamik paylaşılan kitaplıklar](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Söz konusu kitaplığı, bu bölümde daha önce açıklananlar gibi bir Windows veya Android projesinde kullanabilirsiniz. Bunu, Xamarin, Java veya yönetilmeyen bir DLL içindeki işlevleri çağırmanızı sağlayan herhangi bir dili kullanarak oluşturduğunuz bir uygulamada da kullanabilirsiniz.

 Bu kitaplıklara kod yazarken, Android ve Windows platformlarının yerel API 'Lerini araştırmak için IntelliSense 'i kullanabilirsiniz. Bu kitaplık projeleri Visual Studio hata ayıklayıcıyla tamamen tümleşiktir; böylece kesme noktaları ayarlayabilir, kod içinde adım adım ilerleyerek ve hata ayıklayıcının tüm gelişmiş özelliklerini kullanarak sorunları bulabilir ve giderebilmenizi sağlayabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio 'Yu indirin.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Çoklu Platform Mobil Uygulama Geliştirme için Visual C++ araçlarını yükler.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Kitaplığı)|
|[Birden çok platformu hedeflemek için C++ kullanma hakkında daha fazla bilgi edinin.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[İhtiyaç duyduğunuz şeyi yükleyip Android için yerel bir etkinlik uygulaması oluşturun](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Kitaplığı)|
|[Android Için Visual Studio öykünücüsü (VisualStudio.com) hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/msft-android-emulator/)|
|[Android ve Windows uygulamalarıyla C++ kodu paylaşma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[C++ Için platformlar arası mobil geliştirme örnekleri](https://msdn.microsoft.com/library/dn707596.aspx) (MSDN Kitaplığı)|
|[C++ Için ek platformlar arası mobil geliştirme örnekleri](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (Code. MSDN)|

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a><a name="Unity"></a> Unity için Visual Studio Araçları 'nı kullanarak Android, iOS ve Windows için platformlar arası bir oyun oluşturun
 Unity için Visual Studio Araçları, Visual Studio 'nun, Web dahil olmak üzere Windows, iOS, Android ve diğer platformları hedefleyen çok yönlü uygulamalar için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı olan *Unity*ile Visual Studio 'nun güçlü kod düzenlemesini, üretkenliğini ve hata ayıklama araçlarını tümleştiren ücretsiz bir uzantıdır.

 ![VSTU geliştirme ortamı](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Unity için Visual Studio Araçları (VSTU) ile, Visual Studio 'Yu kullanarak C# dilinde oyun ve düzenleyici betikleri yazabilir ve ardından hataları bulmak ve onarmak için güçlü hata ayıklayıcıyı kullanabilirsiniz. VSTU 'nın en son sürümü Unity 5 desteğini sağlar ve Unity 'nin ShaderLab gölgelendirici dili için sözdizimi renklendirme, Unity ile daha zengin hata ayıklama ve tek davranış Sihirbazı için geliştirilmiş kod oluşturma ile daha iyi eşitleme içerir. VSTU Ayrıca Unity proje dosyalarınızı, konsol iletilerinizi ve oyununuzu Visual Studio 'ya başlatabilmenizi sağlayarak, kod yazarken Unity düzenleyicisine geçiş yapmayı daha az zaman harcamanıza olanak tanır.

 Aboneliğinizi Unity ile oluşturmaya başlayın ve bugün Unity için Visual Studio Araçları.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio ile Unity oyunları oluşturma hakkında daha fazla bilgi edinin](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Unity için Visual Studio Araçları hakkında daha fazla bilgi edinin](../cross-platform/visual-studio-tools-for-unity.md) (MSDN Kitaplığı)|
|[Unity için Visual Studio araçları kullanmaya başlama](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (MSDN Kitaplığı)|
|[Unity için Visual Studio Araçları 2,0 önizlemesine yönelik en son geliştirmeler hakkında bilgi edinin](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio blogu)|
|[Unity için Visual Studio Araçları 2,0 önizlemesine bir video tanıtımı izleyin](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (video)|
|[Unity hakkında bilgi edinin](https://unity.com/) (Unity Web sitesi)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio projesine Office 365 API 'leri ekleme](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure Mobile Hizmetleri](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Uygulama Bilgileri](/azure/application-insights/app-insights-overview)
