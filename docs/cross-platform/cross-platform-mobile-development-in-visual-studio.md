---
title: Visual Studio |'da Platformlar Arası Mobil Visual Studio | Microsoft Docs
description: Bu makalede, android, iOS ve Windows cihazları için uygulama derlemeyi öğrenmek için Visual Studio.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: 2f3c611ae157be4f2ea89254856bdd3b6fba448d
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687684"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio'de platformlar arası mobil Visual Studio

Android, iOS ve Windows cihazları için uygulama oluşturmak için Visual Studio.  Uygulamayı tasarlarken, Visual Studio, Microsoft 365 ve Azure App Service gibi bağlı hizmetleri kolayca eklemek için Application Insights.

C# ve .NET Framework, HTML ve JavaScript veya C++ kullanarak uygulamalarınızı oluşturun. Kod, dize, görüntü ve hatta bazı durumlarda kullanıcı arabirimini paylaşın.

Bir oyun veya tam ekran grafik uygulaması oluşturmak için Unity için Visual Studio araçlarını yükleyin ve iOS, Android, Windows ve diğer platformlarda çalışan uygulamalar için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı Olan Unity ile Visual Studio'nin tüm güçlü üretkenlik özelliklerinin keyfini çıkarın.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Android, iOS ve Windows için uygulama oluşturma (.NET Framework)

![Cihazlar](../cross-platform/media/homedevices.png "HomeDevices")

Xamarin Visual Studio Araçları ile android, iOS ve Windows'u aynı çözümde hedefleyebilirsiniz, kod ve hatta kullanıcı arabirimi paylaşabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Yükleme Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Visual Studio'de Xamarin](https://visualstudio.microsoft.com/xamarin/) hakkında bilgi VisualStudio.com|
|[Xamarin mobil uygulama geliştirme belgeleri](/xamarin/) |
|[Xamarin uygulamaları ile DevOps](/xamarin/tools/ci/devops/) |
|[Visual Studio'da Evrensel Windows uygulamaları](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com) hakkında bilgi edinin|
|[Swift ile C# arasındaki benzerlikler hakkında bilgi download.microsoft.com](https://aka.ms/scposter)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> Tek bir kod tabanından Android, iOS ve Windows'u hedefleme

 C# veya F# kullanarak Android, iOS ve Windows için yerel uygulamalar Visual Basic (şu anda desteklenmiyor).  İlkeyi yüklemek Visual Studio yükleyicide **.NET ile** Mobil Geliştirme seçeneğini belirleyin.

 Zaten yüklü bir Visual Studio varsa, Visual Studio Yükleyicisi yeniden  çalıştırın ve Xamarin için **.NET** ile Mobil Geliştirme seçeneğini (yukarıda olduğu gibi) seçin.

 Bitirin, proje şablonları Yeni Proje **iletişim kutusunda** görünür. Xamarin şablonlarını bulmanın en kolay yolu yalnızca "Xamarin" üzerinde arama yapmak için kullanılır.

 Xamarin, Android, iOS ve Windows 'un yerel işlevlerini .NET sınıfları ve yöntemleri olarak kullanıma sunar. Bu, uygulamalarınızın yerel API 'Ler ve yerel denetimler için tam erişimi olduğu ve yalnızca yerel platform dillerinde yazılmış uygulamalar olarak yanıt verdikleri anlamına gelir.

 Bir proje oluşturduktan sonra, Visual Studio 'nun tüm üretkenlik özelliklerinden yararlanabilirsiniz. Örneğin, sayfalarınızı oluşturmak için bir tasarımcı kullanacaksınız ve mobil platformların yerel API 'leri araştırmak için IntelliSense kullanmanız gerekir. Uygulamanızı çalıştırmaya ve nasıl göründüğünü görebilmeniz için, Android SDK öykünücüsünü kullanabilir ve Windows uygulamalarını yerel olarak çalıştırabilirsiniz. Tethered Android ve Windows cihazlarını doğrudan de kullanabilirsiniz. İOS projeleri için, ağa bağlı bir Mac 'e bağlanın ve Visual Studio 'dan iOS öykünücüsünü başlatın veya bir tethered cihazına bağlanın.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Xamarin. Forms kullanarak tüm cihazlarda işlenen bir sayfa kümesi tasarlama

 Uygulama tasarımınızın karmaşıklığına bağlı olarak, proje şablonlarının **Mobile Apps** grubundaki *Xamarin. Forms* şablonlarını kullanarak oluşturmayı düşünebilirsiniz. Xamarin. Forms, Android, iOS ve Windows arasında paylaşabileceğiniz tek bir arabirim oluşturmanıza olanak sağlayan bir UI araç setidir.  Bir Xamarin. Forms çözümünü derlerken bir Android uygulaması, bir iOS uygulaması ve bir Windows uygulaması alırsınız. Daha fazla ayrıntı için bkz. Xamarin ve [Xamarin. Forms belgeleriyle](/xamarin/xamarin-forms/) [mobil geliştirme hakkında bilgi edinin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) .

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> Android, iOS ve Windows uygulamaları arasında kod paylaşma

 Xamarin. Forms kullanmıyorsanız ve her platform için ayrı ayrı tasarlamayı seçerseniz, UI olmayan kodunuzun çoğunu platform projeleri (Android, iOS ve Windows) arasında paylaşabilirsiniz. Bu, herhangi bir iş mantığı, bulut tümleştirmesi, veritabanı erişimi veya .NET Framework hedefleyen herhangi bir kod içerir. Paylaşabileceğiniz tek kod, belirli bir platformu hedefleyen koddur.

 ![Windows, iOS ve Android Usıs arasında kod paylaşma](../cross-platform/media/sharecode.png "ShareCode")

 Paylaşılan bir proje, Taşınabilir Sınıf Kitaplığı projesi veya her ikisini kullanarak kodunuzu paylaşabilirsiniz. Bazı kodun paylaşılan bir projeye en uygun olduğunu ve bazı kodun Taşınabilir Sınıf Kitaplığı projesi içinde daha anlamlı olduğunu farkebilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Kod Seçeneklerini Paylaşma](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[.NET ile kod paylaşma seçenekleri](/dotnet/standard/cross-platform/) |

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a> Hedef Windows 10 cihazları

 ![Windows Cihazları](../cross-platform/media/windowsdevices.png "Windows cihazları")

 Tüm cihazları hedef alan tek bir uygulama oluşturmak Windows 10 evrensel bir Windows uygulaması oluşturun. Uygulamayı tek bir proje kullanarak tasarlarsanız, sayfalarınız bunları görüntülemek için hangi cihaz kullanılırsa kullanın düzgün bir şekilde işler.

 Bir Evrensel Windows Platformu (UWP) uygulama projesi şablonuyla başlama. Sayfalarınızı görsel olarak tasarlar ve ardından çeşitli cihaz türleri için nasıl görüneceklerini görmek için bunları bir önizleme penceresinde açın. Bir sayfanın cihazda nasıl göründüğüne bakmıyorsanız, sayfayı ekran boyutuna, çözünürlüğüne veya yatay veya dikey mod gibi çeşitli yönlere daha iyi uyacak şekilde iyileyebilirsiniz. Bunların hepsini, sezgisel araç pencerelerini ve kolayca erişilebilen menü seçeneklerini kullanarak Visual Studio. Uygulamalarınızı çalıştırmaya ve kodunuz üzerinde adım adım ilerlerken, farklı cihaz türleri için tüm cihaz öykünücülerini ve simülatörlerini Standart araç çubuğunda bulunan bir açılan listede **birlikte** bulabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Evrensel Windows Platformu'a giriş](/windows/uwp/get-started/universal-application-platform-guide)|
|[İlk uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app)|
|[Evrensel Windows Platformu (UWP) için uygulama geliştirme](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|

::: moniker range="vs-2017"

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a> Android, iOS ve Windows için uygulama oluşturma (HTML/JavaScript)

 ![Windows, iOS ve Android cihazlar](../cross-platform/media/homedevices.png "Windows, iOS ve Android cihazlar")

 Web geliştiricisiyseniz ve HTML ve JavaScript hakkında bilgi sahibiyseniz, windows, Android ve iOS için Visual Studio Araçları kullanarak windows Apache Cordova. Bu uygulamalar üç platformu da hedefleyenin ve en çok aşina olunan becerileri ve süreçleri kullanarak bunları geliştirebilirsiniz.

 Apache Cordova, eklenti modeli içeren bir çerçevedir. Bu eklenti modeli, üç platformun da (Android, iOS ve Windows) yerel cihaz özelliklerine erişmek için kullanabileceğiniz tek bir JavaScript API'si sağlar.

 Bu API 'Ler platformlar arası olduğundan, üç platform arasında yazdığınız kadar çoğunu paylaşabilirsiniz. Bu, geliştirme ve bakım maliyetlerinizi azaltır. Ayrıca, sıfırdan başlamak gerekmez. Başka türde Web uygulamaları oluşturduysanız, bunları dilediğiniz şekilde değiştirmek veya yeniden tasarlamanız gerekmeden bu dosyaları Cordova uygulamanızla paylaşabilirsiniz.

 ![JavaScript ile çok cihazlı karma uygulamalar](../cross-platform/media/multidevicehybridapps.png "JavaScript ile çok cihazlı karma uygulamalar")

 Başlamak için Visual Studio 'Yu yükleyip kurulum sırasında **JavaScript Ile mobil geliştirme** özelliğini seçin. Cordova araçları, çok platformlu uygulamanızı derlemek için gereken tüm üçüncü taraf yazılımları otomatik olarak yükler.

 Uzantıyı yükledikten sonra, Visual Studio 'Yu açın ve **boş bir uygulama (Apache Cordova)** projesi oluşturun. Daha sonra, JavaScript veya TypeScript kullanarak uygulamanızı geliştirebilirsiniz. Ayrıca, uygulamanızın işlevlerini genişletmek için eklentiler ekleyebilirsiniz ve kod yazarken IntelliSense 'de bulunan API 'Ler görüntülenir.

 Uygulamanızı çalıştırmaya ve kodunuzda ilerledikten sonra, Apache Ripple öykünücüsü veya Android Emulator, tarayıcı veya doğrudan bilgisayarınıza bağladığınız bir cihaz gibi bir öykünücü seçin. Ardından, uygulamanızı başlatın. Uygulamanızı bir Windows bılgısayarda geliştiriyorsanız, hatta bunu da çalıştırabilirsiniz. Bu seçeneklerin tümü, Apache Cordova için Visual Studio Araçları bir parçası olarak Visual Studio 'da yerleşik olarak bulunur.

 Evrensel Windows Platformu (UWP) uygulamaları oluşturmaya yönelik proje şablonları, Visual Studio 'da kullanılmaya devam etmektedir, ancak yalnızca Windows cihazlarını hedeflemesini planlıyorsanız bunları kullanabilirsiniz. Android ve iOS 'ı daha sonra hedeflemek isterseniz, kodunuzun her zaman bir Cordova projesine bağlantı noktası oluşturabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio 'yu](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com) yükler|
|[Apache Cordova için Visual Studio Araçları kullanmaya başlama](/previous-versions/visualstudio/cross-platform/tools-for-cordova/)|
|[Android Için Visual Studio öykünücüsü (VisualStudio.com) hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/msft-android-emulator/)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Android, iOS ve Windows için uygulama oluşturma (C++)

![Android, iOS&#43;&#43; Windows için derlemek için C&#43;&#43; kullanma](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 İlk olarak, Visual Studio ve **C++ ile Mobil Geliştirme iş yükünü** yükleyin. Ardından, Android için yerel bir etkinlik uygulaması veya Windows ya da iOS'u hedef alan bir uygulama derlemeniz gerekir. Ekleyebilirsiniz Android, iOS ve Windows aynı çözümde ekleyebilirsiniz ve ardından platformlar arası statik veya dinamik paylaşılan kitaplık kullanarak aralarında kod paylaşabilirsiniz.

 Android için oyun gibi herhangi bir tür gelişmiş grafik işlemesi gerektiren bir uygulama derlemeniz gerekirse, bunu yapmak için C++ kullanabilirsiniz. Yerel Etkinlik Uygulaması **(Android) projesiyle çalışmaya** başlama. Bu proje Clang araçlık için tam destek sağlar.

 ![Yerel etkinlik projesi şablonu](../cross-platform/media/cross-plat_cpp_native.png "Yerel etkinlik projesi şablonu")

 Uygulamanızı çalıştırmaya hazırsanız ve nasıl göründüğünü görmek için Android Emulator. Hızlı, güvenilir ve yüklemesi ve yapılandırılması kolaydır.

 Ayrıca C++ ve bir Evrensel Windows Platformu (UWP) uygulama proje şablonu kullanarak Windows 10 tüm cihazları hedef alan bir uygulama oluşturabilirsiniz. Bu konu başlığında daha önce [görünen Hedef Windows 10](#WindowsHTML) cihazlar bölümünde bu konu hakkında daha fazla bilgi edinebilirsiniz.

 Statik veya dinamik bir paylaşılan kitaplık oluşturarak C++ kodunu Android, iOS ve Windows arasında paylaşabilirsiniz.

 ![Statik ve dinamik paylaşılan kitaplıklar](../cross-platform/media/cross_plat_cpp_libraries.png "Statik ve dinamik paylaşılan kitaplıklar")

 Bu kitaplığı bu bölümün önceki kısımlarında açıklananlar gibi bir Windows, iOS veya Android projesinde kullanabilirsiniz. Ayrıca, Xamarin, Java veya bir dil kullanarak derlemek için bir uygulamada veya bir unmanaged DLL'de işlevleri çağırmaya olanak sağlayan herhangi bir dilde de bunu tüketebilirsiniz.

 Bu kitaplıklarda kod yazarak Android ve Windows platformlarının yerel API'lerini keşfetmek için IntelliSense'i kullanabilirsiniz. Bu kitaplık projeleri, Visual Studio hata ayıklayıcısıyla tamamen tümleşiktir. Bu nedenle kesme noktaları ayarlayın, kodda adım atabilir ve hata ayıklayıcının tüm gelişmiş özelliklerini kullanarak sorunları bulup giderebilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[İndirme Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com)|
|[C++ ile platformlar arası mobil geliştirmeyi yükleme](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[Birden çok platformu hedeflemek için C++ kullanma](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) hakkında daha fazla bilgi VisualStudio.com|
|[İhtiyaç duyduğunuz şeyi yükler ve ardından Android için bir C++ yerel etkinlik uygulaması oluşturun](/cpp/cross-platform/create-an-android-native-activity-app)|
|[Android ve Windows uygulamalarıyla C++ kodu paylaşma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[C++ için platformlar arası mobil geliştirme örnekleri](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları 'nı kullanarak Android, iOS ve Windows için platformlar arası bir oyun oluşturun

 Unity için Visual Studio Araçları, Visual Studio 'nun, Web dahil olmak üzere Windows, iOS, Android ve diğer platformları hedefleyen çok yönlü uygulamalar için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı olan *Unity* ile Visual Studio 'nun güçlü kod düzenlemesini, üretkenliğini ve hata ayıklama araçlarını tümleştiren ücretsiz bir uzantıdır.

 ![VSTU geliştirme ortamı](../cross-platform/media/vstu_overview.png "Unity için Visual Studio Araçları genel bakış")

 Unity için Visual Studio Araçları (VSTU) ile, Visual Studio 'Yu kullanarak C# dilinde oyun ve düzenleyici betikleri yazabilir ve ardından hataları bulmak ve onarmak için güçlü hata ayıklayıcıyı kullanabilirsiniz. VSTU 'nın en son sürümü Unity 2018,1 için destek sağlar ve Unity 'nin ShaderLab gölgelendirici dili için sözdizimi renklendirme, Unity ile daha zengin hata ayıklama ve tek davranış Sihirbazı için geliştirilmiş kod oluşturma ile daha iyi eşitleme içerir. VSTU Ayrıca Unity proje dosyalarınızı, konsol iletilerinizi ve oyununuzu Visual Studio 'ya başlatabilmenizi sağlayarak, kod yazarken Unity düzenleyicisine geçiş yapmayı daha az zaman harcamanıza olanak tanır.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio ile Unity oyunları oluşturma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Unity için Visual Studio Araçları hakkında daha fazla bilgi edinin](/gamedev/unity/get-started/visual-studio-tools-for-unity.md) |
|[Unity için Visual Studio Araçları kullanmaya başlayın](/gamedev/unity/get-started/getting-started-with-visual-studio-tools-for-unity.md) |
|[Unity için Visual Studio Araçları 2,0 önizlemesine yönelik en son geliştirmeler hakkında bilgi edinin](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio blogu)|
|[Unity için Visual Studio Araçları 2,0 önizlemesine bir video tanıtımı izleyin](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408&preserve-view=true) (video)|
|[Unity hakkında bilgi edinin](https://unity.com/) (Unity Web sitesi)|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projesine Microsoft 365 API 'Leri ekleme](/office/developer-program/office-365-developer-program)
- [Azure Uygulama Hizmetleri-Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
