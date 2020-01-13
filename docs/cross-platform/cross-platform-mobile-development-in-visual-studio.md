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
ms.openlocfilehash: 15c4d31c8cc835884f1093dc78083bbfa9448bc3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916875"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio 'da platformlar arası mobil geliştirme

Visual Studio kullanarak Android, iOS ve Windows cihazlar için uygulamalar oluşturabilirsiniz.  Uygulamanızı tasarlarken, araçları Visual Studio'da bağlı hizmetler Application ınsights'ı Office 365 ve Azure App Service gibi kolayca eklemek için kullanın.

C# ve .NET Framework, HTML ve JavaScript veya C++ kullanarak uygulamalarınızı oluşturun. Kod, dizeler, resimleri paylaşın ve kullanıcı arabiriminin bazı durumlarda bile.

Oyun veya derinlikli bir grafik uygulaması oluşturmak istiyorsanız, Unity için Visual Studio Araçları'nı yükleyin ve tüm Visual Studio ile Unity uygulamaları için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı, güçlü üretkenlik özellikleri keyfini çıkarın, iOS, Android, Windows ve diğer platformlarda çalıştırın.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Android, iOS ve Windows için uygulama oluşturma (.NET Framework)

![Cihazlar](../cross-platform/media/homedevices.png "HomeDevices")

Xamarin için Visual Studio Araçları, aynı çözümde Android, iOS ve Windows 'u hedefleyebilir, kod ve hatta Kullanıcı arabirimini de kullanabilirsiniz.

|**Daha fazla bilgi**|
|--------------------|
|[Visual Studio yükleme](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Visual Studio'da Xamarin hakkında bilgi edinin](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Xamarin mobil uygulama geliştirme belgeleri](/xamarin/) |
|[Xamarin uygulamalarıyla DevOps](/xamarin/tools/ci/devops/) |
|[Visual Studio 'Da Evrensel Windows uygulamaları hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Swift ve C# arasındaki benzerlikleri hakkında bilgi edinin](https://aka.ms/scposter) (download.microsoft.com)|

### <a name="AndroidHTML"></a> Android, iOS ve Windows, bir tek kod tabanından hedef

 Veya C# F# kullanarak Android, iOS ve Windows için yerel uygulamalar oluşturabilirsiniz (Şu anda Visual Basic desteklenmez).  Başlamak için Visual Studio 'yu yükledikten sonra yükleyicideki **.net Ile mobil geliştirme** seçeneğini belirleyin.

 Visual Studio zaten yüklüyse, **Visual Studio yükleyicisi** yeniden çalıştırın ve Xamarin için .net seçeneğiyle aynı **Mobil geliştirmeyi** (yukarıdaki gibi) seçin.

 İşiniz bittiğinde, proje şablonları **Yeni proje** iletişim kutusunda görünür. "Xamarin" üzerinde yalnızca aramak için Xamarin şablonları bulmanın en kolay yolu olan

 Xamarin, Android, iOS ve Windows 'un yerel işlevlerini .NET sınıfları ve yöntemleri olarak kullanıma sunar. Bu, uygulamalarınızın yerel API 'Ler ve yerel denetimler için tam erişimi olduğu ve yalnızca yerel platform dillerinde yazılmış uygulamalar olarak yanıt verdikleri anlamına gelir.

 Bir proje oluşturduktan sonra, Visual Studio 'nun tüm üretkenlik özelliklerinden yararlanabilirsiniz. Örneğin, sayfalarınızı oluşturmak için bir tasarımcı kullanacaksınız ve mobil platformların yerel API 'leri araştırmak için IntelliSense kullanmanız gerekir. Uygulamanızı çalıştırmaya ve nasıl göründüğünü görebilmeniz için, Android SDK öykünücüsünü kullanabilir ve Windows uygulamalarını yerel olarak çalıştırabilirsiniz. Tethered Android ve Windows cihazları doğrudan da kullanabilirsiniz. İOS projeleri için, ağa bağlı bir Mac 'e bağlanın ve Visual Studio 'dan iOS öykünücüsünü başlatın veya bir tethered cihazına bağlanın.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Bir Xamarin.Forms kullanarak tüm cihazlarda oluşturan sayfalar kümesini tasarlama

 Uygulama tasarımınızı karmaşıklığına bağlı olarak, kullanarak oluşturmayı düşünebilirsiniz *Xamarin.Forms* şablonlarında **Mobile Apps** grup proje şablonları. Xamarin.Forms, Android, iOS ve Windows arasında paylaşabilirsiniz tek bir arabirim oluşturmanıza imkan tanıyan bir UI araç takımıdır.  Bir Xamarin. Forms çözümünü derlerken bir Android uygulaması, bir iOS uygulaması ve bir Windows uygulaması alırsınız. Daha fazla ayrıntı için bkz. Xamarin ve [Xamarin. Forms belgeleriyle](/xamarin/xamarin-forms/) [mobil geliştirme hakkında bilgi edinin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) .

#### <a name="ShareHTML"></a> Android, iOS ve Windows uygulamaları arasında kod paylaşma

 Xamarin. Forms kullanmıyorsanız ve her platform için ayrı ayrı tasarlamayı seçerseniz, UI olmayan kodunuzun çoğunu platform projeleri (Android, iOS ve Windows) arasında paylaşabilirsiniz. Bu, iş mantığı, bulut tümleştirme, veritabanı erişimi veya .NET Framework'ü hedefleyen herhangi bir kod içerir. Paylaşabileceğiniz tek kod, belirli bir platformu hedefleyen koddur.

 ![Windows, iOs ve Android kullanıcı arabirimi ile kod paylaşma](../cross-platform/media/sharecode.png "ShareCode")

 Paylaşılan bir proje, taşınabilir sınıf kitaplığı projesi veya her ikisini de kullanarak kodunuzu paylaşabilir. Daha fazla iyi bir paylaşılan projede veya bazı kod yapar bazı kod uygun bir taşınabilir sınıf kitaplığı projesi içinde anlamlıdır bulabilirsiniz.

|**Daha fazla bilgi**|
|--------------------|
|[Paylaşım kod seçeneklerini](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[.NET ile kod paylaşma seçenekleri](/dotnet/standard/cross-platform/) |

### <a name="WindowsHTML"></a> Windows 10 cihazlarını hedefleyin

 ![Windows cihazları](../cross-platform/media/windowsdevices.png "Windows cihazları")

 Windows 10 cihazları olan tüm tekliflerden hedefleyen tek bir uygulama oluşturmak istiyorsanız, bir evrensel Windows uygulaması oluşturun. Uygulamayı tek bir proje kullanarak tasarlayacaksınız ve sayfalar görüntülemek için kullanılan cihaz ne olduğuna göre düzgün şekilde işlenir.

 Evrensel Windows Platformu (UWP) uygulama projesi şablonuyla başlayın. Sayfalarınızı görsel olarak tasarlamanıza ve bunları çeşitli cihaz türleri için görünme görmek için bir önizleme penceresini açın. Bir sayfada bir sayfanın nasıl göründüğünü beğenmezseniz, ekran boyutu, çözünürlüğü veya yatay veya dikey mod gibi çeşitli yönlerin daha iyi sığması için sayfayı en iyi hale getirebilirsiniz. Tüm bu, Visual Studio'da sezgisel araç pencereleri ve kolayca erişilebilen menü seçeneklerini kullanarak yapabilirsiniz. Uygulamanızı çalıştırmaya ve kodunuzda ilerlemenize hazırsanız, **Standart** araç çubuğunda bulunan bir açılan listede farklı cihaz türleri için cihaz öykünücülerini ve simülatörleri tümünü bulacaksınız.

|**Daha fazla bilgi**|
|--------------------|
|[Evrensel Windows Platformu giriş](/windows/uwp/get-started/universal-application-platform-guide)|
|[İlk uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app)|
|[Evrensel Windows Platformu (UWP) için uygulama geliştirme](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Evrensel Windows Platformu (UWP) uygulamaları geçirme](https://msdn.microsoft.com/library/mt148501.aspx)|

::: moniker range="vs-2017"

## <a name="HTML"></a> Android, iOS ve Windows (HTML/JavaScript) için uygulama oluşturma

 ![Windows, iOS ve Android cihazları](../cross-platform/media/homedevices.png "Windows, iOS ve Android cihazları")

 Web geliştiricisiyseniz ve HTML ve JavaScript hakkında bilgi sahibiyseniz, Apache Cordova için Visual Studio Araçları kullanarak Windows, Android ve iOS 'u hedefleyebilirsiniz. Bu uygulamalar üç platformu da hedefleyebilir ve en çok bildiğiniz becerileri ve süreçlerini kullanarak bunları oluşturabilirsiniz.

 Apache Cordova eklenti modeli içeren bir çerçevedir. Bu eklenti modeli, tüm üç platformları (Android, iOS ve Windows), yerel cihaz özelliklerine erişmek için kullanabileceğiniz tek bir JavaScript API'si sağlar.

 Bu API'ler, platformlar arası olduğundan, tüm üç platformlar arasında yazma çoğu paylaşabilirsiniz. Bu, geliştirme ve Bakım maliyetlerinizi azaltır. Ayrıca, sıfırdan başlamak gerekmez. Başka türde Web uygulamaları oluşturduysanız, bunları dilediğiniz şekilde değiştirmek veya yeniden tasarlamanız gerekmeden bu dosyaları Cordova uygulamanızla paylaşabilirsiniz.

 ![JavaScript ile çok cihazlı karma uygulamalar](../cross-platform/media/multidevicehybridapps.png "JavaScript ile çok cihazlı karma uygulamalar")

 Başlamak için Visual Studio 'Yu yükleyip kurulum sırasında **JavaScript Ile mobil geliştirme** özelliğini seçin. Cordova araçları, çok platformlu uygulamanızı derlemek için gereken tüm üçüncü taraf yazılımları otomatik olarak yükler.

 Uzantıyı yükledikten sonra, Visual Studio 'Yu açın ve **boş bir uygulama (Apache Cordova)** projesi oluşturun. Ardından, JavaScript veya Typescript kullanarak uygulamanızı geliştirebilirsiniz. Uygulamanızı genişletmek için eklentilerini da ekleyebilir ve kod yazarken IntelliSense içinde eklentiler API'lerinden görünür.

 Uygulamanızı çalıştırmaya ve kodunuzda ilerledikten sonra, Apache Ripple öykünücüsü veya Android Emulator, tarayıcı veya doğrudan bilgisayarınıza bağladığınız bir cihaz gibi bir öykünücü seçin. Ardından, uygulamanızı başlatın. Uygulamanızı bir Windows bılgısayarda geliştiriyorsanız, hatta bunu da çalıştırabilirsiniz. Bu seçeneklerin tümü Visual Studio Araçları'nın bir parçası olarak Visual Studio ile Apache Cordova için oluşturulur.

 Evrensel Windows Platformu (UWP) uygulamaları oluşturmaya yönelik proje şablonları, Visual Studio 'da kullanılmaya devam etmektedir, ancak yalnızca Windows cihazlarını hedeflemesini planlıyorsanız bunları kullanabilirsiniz. Daha sonra Android ve iOS platformlarını karar verirseniz, her zaman bir Cordova projesi için kod bağlantı noktası.

|**Daha fazla bilgi**|
|--------------------|
|[Visual Studio yükleme](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Apache Cordova için Visual Studio Araçları kullanmaya başlama](/visualstudio/cross-platform/tools-for-cordova/)|
|[Android için Visual Studio öykünücüsü öğrenin](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Android, iOS ve Windows (C++) için uygulama oluşturma

![Android,&#43; &#43; iOS ve Windows için derlemek için C kullanın](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 İlk olarak, iş yüküyle Visual Studio ve **Mobil C++ geliştirme** 'yı yüklemeniz gerekir. Daha sonra, Android için yerel bir etkinlik uygulaması veya Windows ya da iOS 'u hedefleyen bir uygulama oluşturabilirsiniz. İsterseniz Android, iOS ve Windows 'u aynı çözümde hedefleyebilir ve sonra platformlar arası statik veya dinamik Paylaşılan kitaplık kullanarak kod paylaşabilirsiniz.

 Gelişmiş grafik işleme, oyun gibi her türlü gerektiren Android için bir uygulama oluşturmak ihtiyacınız varsa yapmak için C++ kullanabilirsiniz. **Yerel etkinlik uygulaması (Android)** projesi ile başlayın. Bu proje, Clang araç zinciri için tam destek sunar.

 ![Yerel etkinlik proje şablonu](../cross-platform/media/cross-plat_cpp_native.png "Yerel etkinlik proje şablonu")

 Uygulamanızı çalıştırmaya ve nasıl göründüğünü görmek için hazırsanız, Android Emulator kullanın. Hızlı, güvenilir ve kolayca yüklenebilir ve yapılandırılabilir.

 Ayrıca, ve bir Evrensel Windows Platformu (UWP) uygulama projesi şablonu kullanarak C++ Windows 10 cihazlarının tam kapsamını hedefleyen bir uygulama da oluşturabilirsiniz. Bu konuda hakkında daha fazla bilgiyi [hedef Windows 10 cihazları](#WindowsHTML) bu konuda daha önce görünen bölümü.

 Statik veya dinamik C++ bir paylaşılan kitaplık oluşturarak Android, IOS ve Windows arasında kod paylaşabilirsiniz.

 ![Statik ve dinamik paylaşılan kitaplıklar](../cross-platform/media/cross_plat_cpp_libraries.png "Statik ve dinamik paylaşılan kitaplıklar")

 Söz konusu kitaplığı, bu bölümde daha önce açıklananlar gibi bir Windows, iOS veya Android projesinde kullanabilirsiniz. Ayrıca, bir uygulamada, Xamarin, Java veya yönetilmeyen DLL işlevlerini çağırma olanak sağlayan herhangi bir dil kullanarak yapı raporlarını kullanabilirsiniz.

 Bu kitaplıklara kod yazarken, Android ve Windows platformlarını yerel API'leri keşfetmek için IntelliSense'i kullanabilirsiniz. Kesme noktaları, kodu adımlama ve bulabilir ve tüm hata ayıklayıcı'nın Gelişmiş özelliklerine kullanarak sorunları düzeltmek için bu kitaplık projeleri, Visual Studio hata ayıklayıcıyla tamamen tümleştirilmiştir.

|**Daha fazla bilgi**|
|--------------------|
|[Visual Studio 'Yu indirin](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[İle platformlar arası mobil geliştirmeC++](install-visual-cpp-for-cross-platform-mobile-development.md)|
|[Birden çok platformu hedeflemek C++ için kullanma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[İhtiyaç duyduğunuz şeyi yükler ve ardından Android için yerel bir etkinlik uygulaması oluşturun](create-an-android-native-activity-app.md)|
|[C++ kodu ile Android ve Windows uygulamaları paylaşma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Platformlar arası mobil geliştirme örnekleriC++](cross-platform-mobile-development-examples.md)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları 'nı kullanarak Android, iOS ve Windows için platformlar arası bir oyun oluşturun

 Unity için Visual Studio Araçları, Visual Studio 'nun, Web dahil olmak üzere Windows, iOS, Android ve diğer platformları hedefleyen çok yönlü uygulamalar için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı olan *Unity*ile Visual Studio 'nun güçlü kod düzenlemesini, üretkenliğini ve hata ayıklama araçlarını tümleştiren ücretsiz bir uzantıdır.

 ![VSTU geliştirme ortamı](../cross-platform/media/vstu_overview.png "Unity için Visual Studio Araçları genel bakış")

 Visual Studio Araçları ile Unity (VSTU), oyun ve düzenleyici betikleri C# dilinde yazın ve ardından, güçlü bir hata ayıklayıcı hataları bulma ve düzeltme için Visual Studio kullanabilirsiniz. VSTU 'nın en son sürümü Unity 2018,1 için destek sağlar ve Unity 'nin ShaderLab gölgelendirici dili için sözdizimi renklendirme, Unity ile daha zengin hata ayıklama ve tek davranış Sihirbazı için geliştirilmiş kod oluşturma ile daha iyi eşitleme içerir. VSTU, Unity proje dosyalarınızı, konsol iletileri ve daha az zaman için ve Unity Düzenleyicisi'nden kod yazarken geçiş ayırmasına oyununuzu Visual Studio'ya başlatma özelliğini de getirir.

|**Daha fazla bilgi**|
|--------------------|
|[Unity Visual Studio ile oyun oluşturma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Unity için Visual Studio Araçları hakkında daha fazla bilgi edinin](../cross-platform/visual-studio-tools-for-unity.md) |
|[Unity için Visual Studio Araçları kullanmaya başlayın](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Son geliştirmeler hakkında Unity 2.0 önizlemesi için Visual Studio Araçları okuma](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio blogu)|
|[Unity 2.0 önizlemesi için Visual Studio Araçları için bir tanıtım izleyin](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (Video)|
|[Unity hakkında bilgi edinin](https://unity.com/) (Unity Web sitesi)|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projesine Office 365 API 'Leri ekleme](/office/developer-program/office-365-developer-program)
- [Azure Uygulama Hizmetleri-Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
