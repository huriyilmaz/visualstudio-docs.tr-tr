---
title: Visual Studio 'da platformlar arası mobil geliştirme | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: 5e82828296234b13e36b7d3eabf071071ebb708d
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589011"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio 'da platformlar arası mobil geliştirme

Visual Studio 'Yu kullanarak Android, iOS ve Windows cihazları için uygulamalar oluşturabilirsiniz.  Uygulamanızı tasarlarken, Office 365, Azure App Service ve Application Insights gibi bağlı hizmetleri kolayca eklemek için Visual Studio 'daki araçları kullanın.

Ve .NET Framework, HTML ve C# JavaScript ya C++da kullanarak uygulamalarınızı oluşturun. Kod, dizeler, görüntüler ve bazı durumlarda kullanıcı arabiriminden bile paylaşabilirsiniz.

Bir oyun veya derinlikli grafik uygulaması oluşturmak istiyorsanız, Unity için Visual Studio Araçları 'nı yükler ve Unity ile Visual Studio 'nun güçlü üretkenlik özelliklerinin tümünden yararlanın ve bu uygulamalar için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı iOS, Android, Windows ve diğer platformlarda çalıştırın.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Android, iOS ve Windows için uygulama oluşturma (.NET Framework)

![Cihazlarınız](../cross-platform/media/homedevices.png "HomeDevices")

Xamarin için Visual Studio Araçları, aynı çözümde Android, iOS ve Windows 'u hedefleyebilir, kod ve hatta Kullanıcı arabirimini de kullanabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio 'yu](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com) yükler|
|[Visual Studio 'Da Xamarin hakkında bilgi edinin](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Xamarin mobil uygulama geliştirme belgeleri](/xamarin/) |
|[Xamarin uygulamalarıyla DevOps](/xamarin/tools/ci/devops/) |
|[Visual Studio 'Da Evrensel Windows uygulamaları hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Swift ve C# (download.Microsoft.com) arasındaki benzerlikler hakkında bilgi edinin](https://aka.ms/scposter)|

### <a name="AndroidHTML"></a>Tek bir kod tabanında Android, iOS ve Windows 'u hedefleyin

 Veya C# F# kullanarak Android, iOS ve Windows için yerel uygulamalar oluşturabilirsiniz (Şu anda Visual Basic desteklenmez).  Başlamak için Visual Studio 'yu yükledikten sonra yükleyicideki **.net Ile mobil geliştirme** seçeneğini belirleyin.

 Visual Studio zaten yüklüyse, **Visual Studio yükleyicisi** yeniden çalıştırın ve Xamarin için .net seçeneğiyle aynı **Mobil geliştirmeyi** (yukarıdaki gibi) seçin.

 İşiniz bittiğinde, proje şablonları **Yeni proje** iletişim kutusunda görünür. Xamarin şablonlarını bulmanın en kolay yolu yalnızca "Xamarin" üzerinde arama yapmak için kullanılır.

 Xamarin, Android, iOS ve Windows 'un yerel işlevlerini .NET sınıfları ve yöntemleri olarak kullanıma sunar. Bu, uygulamalarınızın yerel API 'Ler ve yerel denetimler için tam erişimi olduğu ve yalnızca yerel platform dillerinde yazılmış uygulamalar olarak yanıt verdikleri anlamına gelir.

 Bir proje oluşturduktan sonra, Visual Studio 'nun tüm üretkenlik özelliklerinden yararlanabilirsiniz. Örneğin, sayfalarınızı oluşturmak için bir tasarımcı kullanacaksınız ve mobil platformların yerel API 'leri araştırmak için IntelliSense kullanmanız gerekir. Uygulamanızı çalıştırmaya ve nasıl göründüğünü görebilmeniz için, Android SDK öykünücüsünü kullanabilir ve Windows uygulamalarını yerel olarak çalıştırabilirsiniz. Tethered Android ve Windows cihazlarını doğrudan de kullanabilirsiniz. İOS projeleri için, ağa bağlı bir Mac 'e bağlanın ve Visual Studio 'dan iOS öykünücüsünü başlatın veya bir tethered cihazına bağlanın.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Xamarin. Forms kullanarak tüm cihazlarda işlenen bir sayfa kümesi tasarlama

 Uygulama tasarımınızın karmaşıklığına bağlı olarak, proje şablonlarının **Mobile Apps** grubundaki *Xamarin. Forms* şablonlarını kullanarak oluşturmayı düşünebilirsiniz. Xamarin. Forms, Android, iOS ve Windows arasında paylaşabileceğiniz tek bir arabirim oluşturmanıza olanak sağlayan bir UI araç setidir.  Bir Xamarin. Forms çözümünü derlerken bir Android uygulaması, bir iOS uygulaması ve bir Windows uygulaması alırsınız. Daha fazla ayrıntı için bkz. Xamarin ve [Xamarin. Forms belgeleriyle](/xamarin/xamarin-forms/) [mobil geliştirme hakkında bilgi edinin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) .

#### <a name="ShareHTML"></a>Android, iOS ve Windows uygulamaları arasında kod paylaşma

 Xamarin. Forms kullanmıyorsanız ve her platform için ayrı ayrı tasarlamayı seçerseniz, UI olmayan kodunuzun çoğunu platform projeleri (Android, iOS ve Windows) arasında paylaşabilirsiniz. Bu, herhangi bir iş mantığı, bulut tümleştirmesi, veritabanı erişimi veya .NET Framework hedefleyen herhangi bir kod içerir. Paylaşabileceğiniz tek kod, belirli bir platformu hedefleyen koddur.

 ![Windows, iOs ve Android kullanıcı arabirimi ile kod paylaşma](../cross-platform/media/sharecode.png "ShareCode")

 Kodunuzu paylaşılan bir proje, taşınabilir bir sınıf kitaplığı projesi veya her ikisini kullanarak paylaşabilirsiniz. Bazı kodların paylaşılan bir projede en iyi şekilde uyduğunu fark edebilirsiniz ve bazı kodlar taşınabilir bir sınıf kitaplığı projesi içinde daha anlamlı hale gelir.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Kod seçeneklerini paylaşma](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[.NET ile kod paylaşma seçenekleri](/dotnet/standard/cross-platform/) |

### <a name="WindowsHTML"></a>Hedef Windows 10 cihazları

 ![Windows cihazları](../cross-platform/media/windowsdevices.png "Windows cihazları")

 Windows 10 cihazlarının tam kapsamını hedefleyen tek bir uygulama oluşturmak istiyorsanız, bir Evrensel Windows uygulaması oluşturun. Uygulamayı tek bir proje kullanarak tasarlayacaksınız ve sayfalar görüntülemek için kullanılan cihaz ne olduğuna göre düzgün şekilde işlenir.

 Evrensel Windows Platformu (UWP) uygulama projesi şablonuyla başlayın. Sayfalarınızı görsel olarak tasarlayın ve sonra çeşitli cihaz türleri için nasıl göründüğünü görmek için bunları bir önizleme penceresinde açın. Bir sayfada bir sayfanın nasıl göründüğünü beğenmezseniz, ekran boyutu, çözünürlüğü veya yatay veya dikey mod gibi çeşitli yönlerin daha iyi sığması için sayfayı en iyi hale getirebilirsiniz. Tüm bunları, Visual Studio 'da sezgisel araç pencerelerini ve kolayca erişilebilen menü seçeneklerini kullanarak yapabilirsiniz. Uygulamanızı çalıştırmaya ve kodunuzda ilerlemenize hazırsanız, **Standart** araç çubuğunda bulunan bir açılan listede farklı cihaz türleri için cihaz öykünücülerini ve simülatörleri tümünü bulacaksınız.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Evrensel Windows Platformu giriş](/windows/uwp/get-started/universal-application-platform-guide)|
|[İlk uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app)|
|[Evrensel Windows Platformu (UWP) için uygulama geliştirme](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Uygulamaları Evrensel Windows Platformu geçirme (UWP)](https://msdn.microsoft.com/library/mt148501.aspx)|

::: moniker range="vs-2017"

## <a name="HTML"></a>Android, iOS ve Windows için uygulama oluşturma (HTML/JavaScript)

 ![Windows, iOS ve Android cihazları](../cross-platform/media/homedevices.png "Windows, iOS ve Android cihazları")

 Web geliştiricisiyseniz ve HTML ve JavaScript hakkında bilgi sahibiyseniz, Apache Cordova için Visual Studio Araçları kullanarak Windows, Android ve iOS 'u hedefleyebilirsiniz. Bu uygulamalar üç platformu da hedefleyebilir ve en çok bildiğiniz becerileri ve süreçlerini kullanarak bunları oluşturabilirsiniz.

 Apache Cordova, eklenti modeli içeren bir çerçevedir. Bu eklenti modeli, üç platformun (Android, iOS ve Windows) yerel cihaz özelliklerine erişmek için kullanabileceğiniz tek bir JavaScript API 'SI sağlar.

 Bu API 'Ler platformlar arası olduğundan, üç platform arasında yazdığınız kadar çoğunu paylaşabilirsiniz. Bu, geliştirme ve bakım maliyetlerinizi azaltır. Ayrıca, sıfırdan başlamak gerekmez. Başka türde Web uygulamaları oluşturduysanız, bunları dilediğiniz şekilde değiştirmek veya yeniden tasarlamanız gerekmeden bu dosyaları Cordova uygulamanızla paylaşabilirsiniz.

 ![JavaScript ile çok cihazlı karma uygulamalar](../cross-platform/media/multidevicehybridapps.png "JavaScript ile çok cihazlı karma uygulamalar")

 Başlamak için Visual Studio 'Yu yükleyip kurulum sırasında **JavaScript Ile mobil geliştirme** özelliğini seçin. Cordova araçları, çok platformlu uygulamanızı derlemek için gereken tüm üçüncü taraf yazılımları otomatik olarak yükler.

 Uzantıyı yükledikten sonra, Visual Studio 'Yu açın ve **boş bir uygulama (Apache Cordova)** projesi oluşturun. Daha sonra, JavaScript veya TypeScript kullanarak uygulamanızı geliştirebilirsiniz. Ayrıca, uygulamanızın işlevlerini genişletmek için eklentiler ekleyebilirsiniz ve kod yazarken IntelliSense 'de bulunan API 'Ler görüntülenir.

 Uygulamanızı çalıştırmaya ve kodunuzda ilerledikten sonra, Apache Ripple öykünücüsü veya Android Emulator, tarayıcı veya doğrudan bilgisayarınıza bağladığınız bir cihaz gibi bir öykünücü seçin. Ardından, uygulamanızı başlatın. Uygulamanızı bir Windows bılgısayarda geliştiriyorsanız, hatta bunu da çalıştırabilirsiniz. Bu seçeneklerin tümü, Apache Cordova için Visual Studio Araçları bir parçası olarak Visual Studio 'da yerleşik olarak bulunur.

 Evrensel Windows Platformu (UWP) uygulamaları oluşturmaya yönelik proje şablonları, Visual Studio 'da kullanılmaya devam etmektedir, ancak yalnızca Windows cihazlarını hedeflemesini planlıyorsanız bunları kullanabilirsiniz. Android ve iOS 'ı daha sonra hedeflemek isterseniz, kodunuzun her zaman bir Cordova projesine bağlantı noktası oluşturabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio 'yu](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com) yükler|
|[Apache Cordova için Visual Studio Araçları kullanmaya başlama](/visualstudio/cross-platform/tools-for-cordova/)|
|[Android Için Visual Studio öykünücüsü (VisualStudio.com) hakkında bilgi edinin](http://visualstudio.microsoft.com/explore/msft-android-emulator-vs)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Android, iOS ve Windows (C++) için uygulama oluşturma

![Android,&#43; &#43; iOS ve Windows için derlemek için C kullanın](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 İlk olarak, iş yüküyle Visual Studio ve **Mobil C++ geliştirme** 'yı yüklemeniz gerekir. Daha sonra, Android için yerel bir etkinlik uygulaması veya Windows ya da iOS 'u hedefleyen bir uygulama oluşturabilirsiniz. İsterseniz Android, iOS ve Windows 'u aynı çözümde hedefleyebilir ve sonra platformlar arası statik veya dinamik Paylaşılan kitaplık kullanarak kod paylaşabilirsiniz.

 Bir oyun gibi gelişmiş grafik düzenlemesi gerektiren Android için bir uygulama derlemeniz gerekiyorsa, bunu yapmak için kullanabilirsiniz C++ . **Yerel etkinlik uygulaması (Android)** projesi ile başlayın. Bu proje, Clang toolzincirine yönelik tam desteğe sahiptir.

 ![Yerel etkinlik proje şablonu](../cross-platform/media/cross-plat_cpp_native.png "Yerel etkinlik proje şablonu")

 Uygulamanızı çalıştırmaya ve nasıl göründüğünü görmek için hazırsanız, Android Emulator kullanın. Hızlı, güvenilir ve kolayca yüklenebilir ve yapılandırılabilir.

 Ayrıca, ve bir Evrensel Windows Platformu (UWP) uygulama projesi şablonu kullanarak C++ Windows 10 cihazlarının tam kapsamını hedefleyen bir uygulama da oluşturabilirsiniz. Bu konuda daha önce görünen [hedef Windows 10 cihazları](#WindowsHTML) bölümünde bunun hakkında daha fazla bilgi edinin.

 Statik veya dinamik C++ bir paylaşılan kitaplık oluşturarak Android, IOS ve Windows arasında kod paylaşabilirsiniz.

 ![Statik ve dinamik paylaşılan kitaplıklar](../cross-platform/media/cross_plat_cpp_libraries.png "Statik ve dinamik paylaşılan kitaplıklar")

 Söz konusu kitaplığı, bu bölümde daha önce açıklananlar gibi bir Windows, iOS veya Android projesinde kullanabilirsiniz. Bunu, Xamarin, Java veya yönetilmeyen bir DLL içindeki işlevleri çağırmanızı sağlayan herhangi bir dili kullanarak oluşturduğunuz bir uygulamada da kullanabilirsiniz.

 Bu kitaplıklara kod yazarken, Android ve Windows platformlarının yerel API 'Lerini araştırmak için IntelliSense 'i kullanabilirsiniz. Bu kitaplık projeleri Visual Studio hata ayıklayıcıyla tamamen tümleşiktir; böylece kesme noktaları ayarlayabilir, kod içinde adım adım ilerleyerek ve hata ayıklayıcının tüm gelişmiş özelliklerini kullanarak sorunları bulabilir ve giderebilmenizi sağlayabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio 'Yu indirin](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[İle platformlar arası mobil geliştirmeC++](install-visual-cpp-for-cross-platform-mobile-development.md)|
|[Birden çok platformu hedeflemek C++ için kullanma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[İhtiyaç duyduğunuz şeyi yükler ve ardından Android için yerel bir etkinlik uygulaması oluşturun](create-an-android-native-activity-app.md)|
|[Android ve Windows uygulamalarıyla C++ kod paylaşma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Platformlar arası mobil geliştirme örnekleriC++](cross-platform-mobile-development-examples.md)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları 'nı kullanarak Android, iOS ve Windows için platformlar arası bir oyun oluşturun

 Unity için Visual Studio Araçları, Visual Studio 'nun, popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı olan *Unity*ile güçlü kod düzenlemesini, üretkenliği ve hata ayıklama araçlarını tümleştiren ücretsiz bir uzantısıdır. Web dahil olmak üzere Windows, iOS, Android ve diğer platformları hedefleyen modern uygulamalar için.

 ![VSTU geliştirme ortamı](../cross-platform/media/vstu_overview.png "Unity için Visual Studio Araçları genel bakış")

 Unity için Visual Studio Araçları (VSTU) ile Visual Studio 'Yu kullanarak içindeki C# oyun ve düzenleyici betikleri yazabilir ve ardından hataları bulmak ve onarmak için güçlü hata ayıklayıcıyı kullanabilirsiniz. VSTU 'nın en son sürümü Unity 2018,1 için destek sağlar ve Unity 'nin ShaderLab gölgelendirici dili için sözdizimi renklendirme, Unity ile daha zengin hata ayıklama ve tek davranış Sihirbazı için geliştirilmiş kod oluşturma ile daha iyi eşitleme içerir. VSTU Ayrıca Unity proje dosyalarınızı, konsol iletilerinizi ve oyununuzu Visual Studio 'ya başlatabilmenizi sağlayarak, kod yazarken Unity düzenleyicisine geçiş yapmayı daha az zaman harcamanıza olanak tanır.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio ile Unity oyunları oluşturma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Unity için Visual Studio Araçları hakkında daha fazla bilgi edinin](../cross-platform/visual-studio-tools-for-unity.md) |
|[Unity için Visual Studio Araçları kullanmaya başlayın](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Unity için Visual Studio Araçları 2,0 önizlemesine yönelik en son geliştirmeler hakkında bilgi edinin](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio blogu)|
|[Unity için Visual Studio Araçları 2,0 önizlemesine bir video tanıtımı izleyin](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (video)|
|[Unity hakkında bilgi edinin](http://unity3d.com/) (Unity Web sitesi)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio projesine Office 365 API 'Leri ekleme](https://docs.microsoft.com/office/developer-program/office-365-developer-program)
- [Azure Uygulama Hizmetleri-Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](https://docs.microsoft.com/appcenter)
