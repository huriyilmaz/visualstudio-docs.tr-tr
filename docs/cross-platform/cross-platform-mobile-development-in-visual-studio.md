---
title: Visual Studio |'de Platformlar Arası Mobil Visual Studio | Microsoft Docs
description: Bu makalede, android, iOS ve Windows cihazları için Visual Studio.
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
ms.openlocfilehash: f2ce02467a43fc71a0e6e352a9a31a9ccfe810bf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631677"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio'de platformlar arası mobil Visual Studio

Visual Studio kullanarak Android, iOS ve Windows cihazlar için uygulama Visual Studio.  Uygulamayı tasarlarken Visual Studio, Microsoft 365 ve Application Azure App Service gibi bağlı hizmetleri kolayca eklemek için Analizler.

C# ve .NET Framework, HTML ve JavaScript veya C++ kullanarak uygulamalarınızı oluşturun. Kod, dize, görüntü ve hatta bazı durumlarda kullanıcı arabirimini paylaşın.

Oyun veya tam ekran grafik uygulaması oluşturmak için Unity için Visual Studio araçlarını yükleyin ve iOS, Android, Windows ve diğer platformlarda çalışan uygulamalar için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı Unity ile Visual Studio'nin tüm güçlü üretkenlik özelliklerinden keyif anın.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Android, iOS ve Windows için uygulama oluşturma (.NET Framework)

![Cihazlar](../cross-platform/media/homedevices.png "HomeDevices")

Xamarin Visual Studio Araçları ile android, iOS ve Windows aynı çözümde, paylaşım kodunda ve hatta kullanıcı arabiriminde hedefleyebilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Yükleme Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Visual Studio'de Xamarin](https://visualstudio.microsoft.com/xamarin/) hakkında bilgi VisualStudio.com|
|[Xamarin mobil uygulama geliştirme belgeleri](/xamarin/) |
|[Xamarin uygulamaları ile DevOps](/xamarin/tools/ci/devops/) |
|[Visual Studio'de Universal Windows uygulamaları (VisualStudio.com)](https://visualstudio.microsoft.com/vs/universal-windows-platform/) hakkında bilgi edinin|
|[Swift ile C# arasındaki benzerlikler hakkında bilgi download.microsoft.com](https://aka.ms/scposter)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a>Android, iOS ve Windows tek bir kod tabanından hedefle

 C# veya F# kullanarak Android, iOS ve Windows için yerel uygulamalar Visual Basic (şu anda desteklenmiyor).  İlkeyi yüklemek Visual Studio yükleyicide **.NET ile** Mobil Geliştirme seçeneğini belirleyin.

 Zaten yüklü bir Visual Studio varsa, Visual Studio Yükleyicisi yeniden  çalıştırın ve Xamarin için **.NET** ile Mobil Geliştirme seçeneğini (yukarıda olduğu gibi) seçin.

 Bitirin, proje şablonları Yeni Uygulama iletişim **Project** görünür. Xamarin şablonlarını bulmanın en kolay yolu yalnızca "Xamarin" araması yapmaktır.

 Xamarin, Android, iOS ve Windows .NET sınıfları ve yöntemleri olarak yerel işlevselliğini ortaya çıkarır. Bu, uygulamalarınızı yerel API'lere ve yerel denetimlere tam erişime sahip olduğu ve yerel platform dillerinde yazılan uygulamalar kadar hızlı yanıt veren uygulamalar olduğu anlamına gelir.

 Bir proje oluşturdukta, bu projenin tüm üretkenlik özelliklerinden Visual Studio. Örneğin, sayfalarınızı oluşturmak için tasarımcıyı ve mobil platformların yerel API'lerini keşfetmek için IntelliSense'i kullanabilirsiniz. Uygulamanızı çalıştırmaya ve nasıl göründüğünü görmeye hazırsanız, Android SDK öykünücüsünü kullanabilir ve Windows çalıştırabilirsiniz. Ayrıca, cihazları doğrudan kullanmak için tethered Android Windows kullanabilirsiniz. iOS projeleri için ağa bağlı bir Mac'e bağlanarak iOS öykünücüsünü Visual Studio veya bağlı bir cihaza bağlanabilirsiniz.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Xamarin.Forms kullanarak tüm cihazlarda işleme alan bir sayfa kümesi tasarlama

 Uygulama tasarımının karmaşıklığına bağlı olarak, proje şablonları grubu içinde *Xamarin.Forms* **şablonlarını Mobile Apps** oluşturabilirsiniz. Xamarin.Forms, Android, iOS ve android cihazlarda paylaşabilirsiniz tek bir arabirim oluşturmanıza olanak sağlayan bir kullanıcı arabirimi araç Windows.  Bir Xamarin.Forms çözümünü derleyene bir Android uygulaması, bir iOS uygulaması ve bir Windows elde edin. Diğer ayrıntılar için [bkz. Xamarin ile mobil geliştirme hakkında bilgi](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) ve [Xamarin.Forms belgeleri.](/xamarin/xamarin-forms/)

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a>Android, iOS ve Windows uygulamaları arasında kod paylaşma

 Xamarin.Forms'u kullanmayacaksanız ve her platform için ayrı ayrı tasarlamayı seçerseniz, kullanıcı arabirimi olmayan kodunuzun çoğunu platform projeleri (Android, iOS ve Windows) arasında paylaşabilirsiniz. Buna iş mantığı, bulut tümleştirmesi, veritabanı erişimi veya veri tabanını hedef alan diğer .NET Framework. Paylaşamayabilirsiniz tek kod, belirli bir platformu hedef alan koddur.

 ![Windows, iOS ve Android KULLANıCı'ları arasında kod paylaşma](../cross-platform/media/sharecode.png "ShareCode")

 Paylaşılan bir proje, Taşınabilir Sınıf Kitaplığı projesi veya her ikisini kullanarak kodunuzu paylaşabilirsiniz. Bazı kodun paylaşılan bir projeye en uygun olduğunu ve bazı kodun Taşınabilir Sınıf Kitaplığı projesi içinde daha anlamlı olduğunu farkabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Kod Seçeneklerini Paylaşma](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[.NET ile kod paylaşma seçenekleri](/dotnet/standard/cross-platform/) |

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Hedef Windows 10 cihazları

 ![Windows Aygıtları](../cross-platform/media/windowsdevices.png "Windows Aygıtları")

 Windows 10 cihazlarının tamamını hedef alan tek bir uygulama oluşturmak Windows oluşturun. Uygulamayı tek bir proje kullanarak tasarlarsanız, sayfalarınız bunları görüntülemek için hangi cihaz kullanılırsa kullanın düzgün bir şekilde işler.

 Universal Windows Platform (UWP) uygulama projesi şablonuyla çalışmaya başlama. Sayfalarınızı görsel olarak tasarlar ve ardından çeşitli cihaz türleri için nasıl görüneceklerini görmek için bunları bir önizleme penceresinde açın. Bir sayfanın cihazda nasıl göründüğüne bakmıyorsanız, sayfayı ekran boyutuna, çözünürlüğüne veya yatay veya dikey mod gibi çeşitli yönlere daha iyi uyacak şekilde iyileyebilirsiniz. Sezgisel araç pencerelerini ve kolayca erişilebilen menü seçeneklerini kullanarak bunların hepsini Visual Studio. Uygulamalarınızı çalıştırmaya ve kodunuz üzerinde adım adım ilerlerken, farklı cihaz türleri için tüm cihaz öykünücülerini ve simülatörlerini Standart araç çubuğunda bulunan bir açılan listede **birlikte** bulabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Universal Windows Platform'a Giriş](/windows/uwp/get-started/universal-application-platform-guide)|
|[İlk uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app)|
|[Evrensel Windows Platformu (UWP) için uygulama geliştirme](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|

::: moniker range="vs-2017"

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Android, iOS ve Windows için uygulama oluşturma (HTML/JavaScript)

 ![Windows, iOS ve Android cihazları](../cross-platform/media/homedevices.png "Windows, iOS ve Android cihazları")

 Web geliştiricisiyseniz ve HTML ve JavaScript hakkında bilgi sahibiyseniz, Visual Studio Araçları for Apache Cordova kullanarak Windows, Android ve iOS'u Apache Cordova. Bu uygulamalar üç platformu da hedefleyenin ve en çok aşina olunan becerileri ve süreçleri kullanarak bunları geliştirebilirsiniz.

 Apache Cordova, eklenti modeli içeren bir çerçevedir. Bu eklenti modeli, üç platformun da (Android, iOS ve Windows) yerel cihaz özelliklerine erişmek için kullanabileceğiniz tek bir JavaScript API'si Windows.

 Bu API'ler platformlar arası olduğundan, üç platform arasında da yazacaklarının çoğunu paylaşabilirsiniz. Bu, geliştirme ve bakım maliyetlerinizi azaltır. Ayrıca sıfırdan başlamaya gerek yoktur. Başka tür web uygulaması oluşturduysanız, bu dosyaları herhangi bir şekilde değiştirmek veya yeniden tasarlamak zorunda kalmadan Cordova uygulamayla paylaşabilirsiniz.

 ![JavaScript ile çok cihazlı karma uygulamalar](../cross-platform/media/multidevicehybridapps.png "JavaScript ile çok cihazlı karma uygulamalar")

 Çalışmaya başlamanız için, Visual Studio ve kurulum sırasında **Javascript ile** Mobil Geliştirme özelliğini seçin. Cordova araçları, çok platformlu uygulamanızı derlemek için gereken tüm üçüncü taraf yazılımları otomatik olarak yüklenir.

 Uzantıyı yükledikten sonra, Visual Studio'i açın ve boş uygulama **(Apache Cordova) projesi** oluşturun. Ardından, JavaScript veya Typescript kullanarak uygulama geliştirebilirsiniz. Ayrıca, uygulamanın işlevselliğini genişletmek için eklentiler eklersiniz ve siz kod yazarken eklentilerden API'ler IntelliSense'te görünür.

 Kodunuzu çalıştırmaya ve kodunuzu adım adım uygulamaya hazır olduğunuzda Apache Ripple öykünücüsü veya Android Emulator, tarayıcı veya doğrudan bilgisayarınıza bağlı bir cihaz gibi bir öykünücü seçin. Ardından, uygulamanıza başlayabilirsiniz. Uygulamalarınızı bir Windows bilgisayarınızda geliştiriyorsanız, bunun üzerinde bile çalıştırabilirsiniz. Bu seçeneklerin hepsi, Visual Studio bir parçası olarak Visual Studio Araçları yerleşik Apache Cordova.

 Project Windows Platform (UWP) uygulamaları oluşturmaya yönelik şablonlar Visual Studio'da hala kullanılabilir. Bu nedenle, yalnızca Windows cihazları hedeflemeyi planlıyorsanız bunları kullanabilirsiniz. Android ve iOS'u daha sonra hedeflemeye karar verdiyebilirsiniz, kodunuzu her zaman bir Cordova projesine taşınabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Yükleme Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Kullanmaya başlayın için Visual Studio Araçları ile Apache Cordova](/previous-versions/visualstudio/cross-platform/tools-for-cordova/)|
|[Android için Visual Studio Emulator hakkında bilgi (VisualStudio.com)](https://visualstudio.microsoft.com/vs/msft-android-emulator/)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Android, iOS ve Windows (C++) için uygulama oluşturma

![Android, iOS ve&#43;&#43; derlemek için C Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 İlk olarak, Visual Studio **ve C++ ile Mobil Geliştirme iş yükünü** yükleyin. Daha sonra, Android için yerel bir etkinlik uygulaması ya da android ya da iOS'u Windows bir uygulama derlemeniz gerekir. Ekleyebilirsiniz Android, iOS ve Windows aynı çözümde ve ardından platformlar arası statik veya dinamik paylaşılan kitaplık kullanarak kod aralarında paylaşabilirsiniz.

 Android için oyun gibi herhangi bir tür gelişmiş grafik işlemesi gerektiren bir uygulama derlemeniz gerekirse, bunu yapmak için C++ kullanabilirsiniz. Yerel Etkinlik Uygulaması **(Android) projesiyle çalışmaya** başlama. Bu proje Clang araçlık için tam destek sağlar.

 ![Yerel etkinlik projesi şablonu](../cross-platform/media/cross-plat_cpp_native.png "Yerel etkinlik projesi şablonu")

 Uygulamanızı çalıştırmaya ve nasıl göründüğünü görmeye hazırsanız Android Emulator. Hızlı, güvenilir ve yüklemesi ve yapılandırılması kolaydır.

 Ayrıca C++ ve Universal Windows Platform (UWP) uygulama proje şablonunu kullanarak Windows 10 cihazların tamamını hedef alan bir uygulama oluşturabilirsiniz. Bu konuda daha önce görünen [Hedef Windows 10 cihazlar](#WindowsHTML) bölümünde bu konu hakkında daha fazla bilgi edinebilirsiniz.

 Statik veya dinamik paylaşılan kitaplık oluşturarak C++ kodunu Android, iOS ve Windows arasında paylaşabilirsiniz.

 ![Statik ve dinamik paylaşılan kitaplıklar](../cross-platform/media/cross_plat_cpp_libraries.png "Statik ve dinamik paylaşılan kitaplıklar")

 Bu kitaplığı bu bölümün önceki Windows gibi bir Windows, iOS veya Android projesinde tüketebilirsiniz. Ayrıca, Xamarin, Java veya bir dil kullanarak derlemek için bir uygulamada veya bir unmanaged DLL'de işlevleri çağırmaya olanak sağlayan herhangi bir dilde de bunu tüketebilirsiniz.

 Bu kitaplıklarda kod yazarken, Android ve Windows platformlarının yerel API'lerini keşfetmek için IntelliSense'i kullanabilirsiniz. Bu kitaplık projeleri Visual Studio hata ayıklayıcısıyla tamamen tümleşiktir. Bu nedenle kesme noktaları ayarlayın, kodda adım atabilir ve hata ayıklayıcının tüm gelişmiş özelliklerini kullanarak sorunları bulup giderebilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[İndirme Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com)|
|[C++ ile platformlar arası mobil geliştirmeyi yükleme](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[Birden çok platformu hedeflemek için C++ kullanma](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) hakkında daha fazla bilgi VisualStudio.com|
|[Gerekenleri yükleyin ve ardından Android için bir C++ yerel etkinlik uygulaması oluşturun](/cpp/cross-platform/create-an-android-native-activity-app)|
|[C++ kodunu Android ve Windows uygulamalarıyla paylaşma](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) hakkında daha fazla bilgi edinin (VisualStudio.com)|
|[C++ için platformlar arası mobil geliştirme örnekleri](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Unity için farklı araçlar kullanarak Android, iOS ve Windows platformlar Visual Studio oyun oluşturma

 Unity için Visual Studio Araçları, Visual Studio Visual Studio' ın güçlü kod düzenleme, üretkenlik ve hata ayıklama araçlarını Unity ile tümleştirerek Windows, iOS, Android ve web dahil olmak üzere diğer platformları hedef alan çevreleyici uygulamalara yönelik popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı *Unity* ile tümleştiren ücretsiz bir uzantıdır.

 ![VSTU geliştirme ortamı](../cross-platform/media/vstu_overview.png "Unity için Visual Studio Araçları genel bakış")

 Unity için Visual Studio Araçları (VSTU) ile C# Visual Studio oyun ve düzenleyici betikleri yazmak ve ardından güçlü hata ayıklayıcısını kullanarak hataları bulup düzeltin. VSTU'nun en son sürümü Unity 2018.1 desteği getirir ve Unity'nin GölgelendiriciLab gölgelendirici dili için söz dizimi renklendirmesi, Unity ile daha iyi eşitleme, daha zengin hata ayıklama ve MonoBehavior sihirbazı için geliştirilmiş kod oluşturma içerir. VSTU ayrıca Unity proje dosyalarınızı, konsol iletilerinizi ve oyununuzu Visual Studio'a başlatarak kod yazarken Unity Düzenleyicisi'ne ve Unity Düzenleyicisi'ne geçiş yapmaya daha az zaman harcayabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio ile Unity oyunları Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Unity için Visual Studio Araçları hakkında daha fazla bilgi Unity için Visual Studio Araçları](/visualstudio/gamedev/unity/get-started/visual-studio-tools-for-unity) |
|[Unity için Visual Studio Araçları'ı kullanmaya başlama](/visualstudio/gamedev/unity/get-started/getting-started-with-visual-studio-tools-for-unity) |
|[Unity için Visual Studio Araçları 2.0 Preview 'da](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) yapılan en son geliştirmeler hakkında bilgi edinebilirsiniz (Visual Studio blog)|
|[Unity için Visual Studio Araçları 2.0 Önizlemesi'ne giriş videosunu](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408&preserve-view=true) izleyin (Video)|
|[Unity hakkında bilgi edinmek](https://unity.com/) (Unity web sitesi)|

## <a name="see-also"></a>Ayrıca bkz.

- [Bir Microsoft 365 api'leri Visual Studio ekleme](/office/developer-program/office-365-developer-program)
- [Azure App Services - Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
