---
title: Visual Studio'da Platform Ötesi Mobil Gelişim | Microsoft Dokümanlar
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
ms.openlocfilehash: c7f40f656b533949748a7eb2ab88ea3d2b1d5923
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78234988"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio'da platform ötesi mobil geliştirme

Visual Studio'u kullanarak Android, iOS ve Windows cihazları için uygulamalar oluşturabilirsiniz.  Uygulamanızı tasarlarken, Office 365, Azure Uygulama Hizmeti ve Uygulama Öngörüleri gibi bağlantılı hizmetleri kolayca eklemek için Visual Studio'da araçları kullanın.

C# ve .NET Framework, HTML ve JavaScript veya C++'ı kullanarak uygulamalarınızı oluşturun. Kodu, dizeleri, görüntüleri ve hatta bazı durumlarda kullanıcı arabirimini paylaşın.

Bir oyun veya sürükleyici grafik uygulaması oluşturmak istiyorsanız, Unity için Visual Studio araçlarını yükleyin ve iOS, Android, Windows ve diğer platformlarda çalışan uygulamalar için popüler platformlar arası oyun/grafik motoru ve geliştirme ortamı olan Visual Studio with Unity'nin tüm güçlü üretkenlik özelliklerinin keyfini çıkarın.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Android, iOS ve Windows (.NET Framework) için bir uygulama oluşturma

![Cihazlar](../cross-platform/media/homedevices.png "AnasayfaCihazlar")

Xamarin için Visual Studio Tools ile Android, iOS ve Windows'u aynı çözümde, kod paylaşımında ve hatta uI ile hedefleyebilirsiniz.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Visual Studio Yükle](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Visual Studio'da Xamarin hakkında bilgi edinin](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Xamarin mobil uygulama geliştirme belgeleri](/xamarin/) |
|[Xamarin uygulamaları ile DevOps](/xamarin/tools/ci/devops/) |
|[Visual Studio'daki Evrensel Windows uygulamaları hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Swift ve C#](https://aka.ms/scposter) (download.microsoft.com) arasındaki benzerlikler hakkında bilgi edinin|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a>Android, iOS ve Windows'u tek bir kod tabanından hedefleme

 C# veya F# (Visual Basic şu anda desteklenmez) kullanarak Android, iOS ve Windows için yerel uygulamalar oluşturabilirsiniz.  Başlamak için Visual Studio'yu yükleyin, yükleyicide **.NET** seçeneği bulunan Mobil Geliştirme seçeneğini belirleyin.

 Visual Studio zaten yüklüyseniz, **Visual Studio Installer'ı** yeniden çalıştırın ve Xamarin için **.NET seçeneğiyle** aynı Mobil Geliştirmeyi seçin (yukarıdaki gibi).

 İşi bittiğinde, proje şablonları **Yeni Proje** iletişim kutusunda görünür. Xamarin şablonlarını bulmanın en kolay yolu "Xamarin"de arama yapmaktır.

 Xamarin, Android, iOS ve Windows'un yerel işlevselliğini .NET sınıfları ve yöntemleri olarak ortaya çıkarır. Bu, uygulamalarınızın yerel API'lere ve yerel denetimlere tam erişime sahip olduğu ve yerel platform dillerinde yazılmış uygulamalar kadar duyarlı oldukları anlamına gelir.

 Bir proje oluşturduktan sonra Visual Studio'nun tüm üretkenlik özelliklerinden yararlanırsınız. Örneğin, sayfalarınızı oluşturmak için bir tasarımcı kullanır sınız ve mobil platformların yerel API'lerini keşfetmek için IntelliSense'i kullanırsınız. Uygulamanızı çalıştırmaya ve nasıl göründüğünü görmeye hazır olduğunuzda, Android SDK emülatörü kullanabilir ve Windows uygulamalarını yerel olarak çalıştırabilirsiniz. Bağlı Android ve Windows cihazlarını doğrudan da kullanabilirsiniz. iOS projeleri için ağa bağlı bir Mac'e bağlanın ve Visual Studio'dan iOS emülatörü başlatın veya bağlı bir aygıta bağlanın.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Xamarin.Forms kullanarak tüm cihazlarda işlenen bir sayfa kümesi tasarla

 Uygulama tasarımınızın karmaşıklığına bağlı olarak, proje şablonları Mobil **Uygulamalar** grubunda *Xamarin.Forms* şablonlarını kullanarak bu tasarımı oluşturmayı düşünebilirsiniz. Xamarin.Forms, Android, iOS ve Windows arasında paylaşabileceğiniz tek bir arabirim oluşturmanıza olanak tanıyan bir Ara bilgi aracı araç setidir.  Bir Xamarin.Forms çözümü derlediğinizde, bir Android uygulaması, bir iOS uygulaması ve bir Windows uygulaması alırsınız. Daha fazla bilgi için, [Xamarin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) ve [Xamarin.Forms belgeleri](/xamarin/xamarin-forms/)ile mobil geliştirme hakkında bilgi edinin.

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a>Android, iOS ve Windows uygulamaları arasında kod paylaşma

 Xamarin.Forms kullanmıyorsanız ve her platform için ayrı ayrı tasarım yapmayı seçiyorsanız, UI olmayan kodlarınızın çoğunu platform projeleri (Android, iOS ve Windows) arasında paylaşabilirsiniz. Bu, herhangi bir iş mantığını, bulut tümleştirmesini, veritabanı erişimini veya .NET Framework'u hedefleyen diğer kodları içerir. Paylaşamadığınız tek kod, belirli bir platformu hedefleyen koddur.

 ![Windows, iOS ve Android Arabirimi arasında kod paylaşma](../cross-platform/media/sharecode.png "Paylaşım Kodu")

 Paylaşılan bir projeyi, Taşınabilir Sınıf Kitaplığı projesini veya her ikisini de kullanarak kodunuzu paylaşabilirsiniz. Paylaşılan bir projede bazı kodların en uygun olduğunu ve bazı kodların Taşınabilir Sınıf Kitaplığı projesinde daha mantıklı olduğunu görebilirsiniz.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Kod Seçeneklerini Paylaşma](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[.NET ile kod paylaşım seçenekleri](/dotnet/standard/cross-platform/) |

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Hedef Windows 10 cihazları

 ![Windows Cihazları](../cross-platform/media/windowsdevices.png "Windows Cihazları")

 Windows 10 cihazlarının tüm genişliğini hedefleyen tek bir uygulama oluşturmak istiyorsanız, evrensel bir Windows uygulaması oluşturun. Uygulamayı tek bir proje kullanarak tasarlarsınız ve sayfalarınız bunları görüntülemek için hangi cihaz kullanılırsa kullanılsın düzgün bir şekilde işlenir.

 Evrensel Windows Platformu (UWP) uygulama proje şablonuyla başlayın. Sayfalarınızı görsel olarak tasarlayın ve ardından çeşitli aygıt türleri için nasıl göründüklerini görmek için bunları önizleme penceresinde açın. Bir sayfanın aygıtta nasıl göründüğünü beğenmezseniz, sayfayı ekran boyutuna, çözünürlüğe veya yatay veya dikey mod gibi çeşitli yönlendirmelere daha iyi uyacak şekilde optimize edebilirsiniz. Tüm bunları Visual Studio'da sezgisel araç pencerelerini ve kolayca erişilebilen menü seçeneklerini kullanarak yapabilirsiniz. Uygulamanızı çalıştırmaya ve kodunuzu aşmaya hazır olduğunuzda, farklı türdeki aygıtların tüm cihaz emülatörlerini ve simülatörlerini **Standart** araç çubuğunda bulunan tek bir açılır listede bir arada bulabilirsiniz.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Evrensel Windows Platformuna Giriş](/windows/uwp/get-started/universal-application-platform-guide)|
|[İlk uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app)|
|[Evrensel Windows Platformu (UWP) için uygulama geliştirme](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Uygulamaları Evrensel Windows Platformu’na (UWP) geçirme](https://msdn.microsoft.com/library/mt148501.aspx)|

::: moniker range="vs-2017"

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Android, iOS ve Windows (HTML/JavaScript) için bir uygulama oluşturma

 ![Windows, iOS ve Android cihazlar](../cross-platform/media/homedevices.png "Windows, iOS ve Android cihazlar")

 Bir web geliştiricisiyseniz ve HTML ve JavaScript'e aşinaysanız, Apache Cordova için Visual Studio Araçlarını kullanarak Windows, Android ve iOS'u hedefleyebilirsiniz. Bu uygulamalar üç platformu da hedefleyebilir ve en çok aşina olduğunuz becerileri ve süreçleri kullanarak bunları oluşturabilirsiniz.

 Apache Cordova bir eklenti modeli içeren bir çerçevedir. Bu eklenti modeli, her üç platformun (Android, iOS ve Windows) yerel aygıt özelliklerine erişmek için kullanabileceğiniz tek bir JavaScript API sağlar.

 Bu API'ler çapraz platform olduğundan, yazdıklarının çoğunu üç platform arasında paylaşabilirsiniz. Bu, geliştirme ve bakım maliyetlerinizi azaltır. Ayrıca, sıfırdan başlamaya gerek yok. Başka web uygulamaları oluşturduysanız, bu dosyaları herhangi bir şekilde değiştirmek veya yeniden tasarlamak zorunda kalmadan Cordova uygulamanızla paylaşabilirsiniz.

 ![JavaScript ile çok cihazlı karma uygulamalar](../cross-platform/media/multidevicehybridapps.png "JavaScript ile çok cihazlı karma uygulamalar")

 Başlamak için Visual Studio'yu yükleyin ve kurulum sırasında **Javascript özelliğine sahip Mobil Geliştirme** özelliğini seçin. Cordova araçları, çok platformlu uygulamanızı oluşturmak için gereken tüm üçüncü taraf yazılımlarını otomatik olarak yükler.

 Uzantıyı yükledikten sonra Visual Studio'yu açın ve boş bir **uygulama (Apache Cordova)** projesi oluşturun. Ardından, JavaScript veya Typescript kullanarak uygulamanızı geliştirebilirsiniz. Ayrıca uygulamanızın işlevselliğini genişletmek için eklentiler ekleyebilirsiniz ve kod yazarken eklentilerden gelen API'ler IntelliSense'de görünür.

 Uygulamanızı çalıştırmaya ve kodunuzu aşmaya hazır olduğunuzda, Apache Ripple emülatörü veya Android Emülatör, tarayıcı veya doğrudan bilgisayarınıza bağladığınız bir aygıt gibi bir emülatör seçin. Ardından uygulamanızı başlatın. Uygulamanızı bir Windows PC'de geliştiriyorsanız, uygulamanızı bu bilgisayarda bile çalıştırabilirsiniz. Tüm bu seçenekler, Apache Cordova için Visual Studio Tools'un bir parçası olarak Visual Studio'da bulunmaktadır.

 Evrensel Windows Platformu (UWP) uygulamaları oluşturmak için proje şablonları Visual Studio'da hala mevcuttur, bu nedenle yalnızca Windows aygıtlarını hedeflemeyi planlıyorsanız bunları kullanmaktan çekinmeyin. Android ve iOS'u daha sonra hedeflemeye karar verirseniz, kodunuzu her zaman bir Cordova projesine bağlayabilirsiniz.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Visual Studio Yükle](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Apache Cordova için Visual Studio Tools ile başlayın](/visualstudio/cross-platform/tools-for-cordova/)|
|[Android için Visual Studio Emülatörü](https://visualstudio.microsoft.com/vs/msft-android-emulator/) hakkında bilgi edinin (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Android, iOS ve Windows (C++) için bir uygulama oluşturma

![Android, iOS ve Windows için oluşturmak için C&#43;&#43; kullanın](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 İlk olarak Visual Studio'yu ve C++ iş **yüküyle Mobil Geliştirme'yi** yükleyin. Ardından, Android için yerel bir etkinlik uygulaması veya Windows veya iOS'u hedefleyen bir uygulama oluşturabilirsiniz. İsterseniz Android, iOS ve Windows'u aynı çözümde hedefleyebilir ve ardından çapraz platform statik veya dinamik paylaşılan kitaplığı kullanarak aralarında kod paylaşabilirsiniz.

 Android için oyun gibi her türlü gelişmiş grafik manipülasyonu gerektiren bir uygulama oluşturmanız gerekiyorsa, bunu yapmak için C++'yı kullanabilirsiniz. **Yerel Etkinlik Uygulaması (Android)** projesiyle başlayın. Bu proje Clang araç zinciri için tam destek vardır.

 ![Yerel etkinlik proje şablonu](../cross-platform/media/cross-plat_cpp_native.png "Yerel etkinlik proje şablonu")

 Uygulamanızı çalıştırmaya ve nasıl göründüğünü görmeye hazır olduğunuzda Android Emülatör'ünkullanın. Hızlı, güvenilir ve kurulumu ve yapılandırılması kolaydır.

 Ayrıca, C++ ve Evrensel Windows Platformu (UWP) uygulama proje şablonu kullanarak Windows 10 cihazlarının tüm genişliğini hedefleyen bir uygulama da oluşturabilirsiniz. Bu konuda daha önce bu konuda görünen [Hedef Windows 10 aygıtları](#WindowsHTML) bölümünde daha fazla bilgi edinin.

 Statik veya dinamik paylaşılan kitaplık oluşturarak Android, iOS ve Windows arasında C++ kodunu paylaşabilirsiniz.

 ![Statik ve dinamik paylaşılan kitaplıklar](../cross-platform/media/cross_plat_cpp_libraries.png "Statik ve dinamik paylaşılan kitaplıklar")

 Bu kitaplığı, bu bölümde daha önce açıklananlar gibi bir Windows, iOS veya Android projesinde tüketebilirsiniz. Ayrıca, Xamarin, Java veya yönetilmeyen bir DLL'deki işlevleri çağırmanızı sağlayan herhangi bir dilde kullanarak oluşturduğunuz bir uygulamada da tüketebilirsiniz.

 Bu kitaplıklara kod yazarken, Android ve Windows platformlarının yerel API'lerini keşfetmek için IntelliSense'i kullanabilirsiniz. Bu kitaplık projeleri Visual Studio hata ayıklayıcıile tamamen entegre edilmiştir, böylece kesme noktaları ayarlayabilir, koda adım atabilir ve hata ayıklayıcının tüm gelişmiş özelliklerini kullanarak sorunları bulabilir ve düzeltebilirsiniz.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Karşıdan yükleme Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com)|
|[C++ ile platformlar arası mobil geliştirmeyi yükleme](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[Birden çok platformu hedeflemek için C++ kullanma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[İhtiyacınız olanı yükleyin ve Ardından Android için bir C++ yerel etkinlik uygulaması oluşturun](/cpp/cross-platform/create-an-android-native-activity-app)|
|[C++ kodunu Android ve Windows uygulamalarıyla paylaşma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[C++ için platform ötesi mobil geliştirme örnekleri](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Unity için Visual Studio araçlarını kullanarak Android, iOS ve Windows için bir çapraz platform oyunu oluşturun

 Visual Studio Tools for Unity, Visual Studio'nun güçlü kod düzenleme, üretkenlik ve hata ayıklama araçlarını *Windows,* iOS, Android ve web gibi diğer platformları hedefleyen sürükleyici uygulamalar için popüler platformlar arası oyun/grafik motoru ve geliştirme ortamı yla birleştiren Visual Studio için ücretsiz bir uzantıdır.

 ![VSTU geliştirme ortamı](../cross-platform/media/vstu_overview.png "Unity için Visual Studio Tools genel bakış")

 Visual Studio Tools for Unity (VSTU) ile Visual Studio'yu kullanarak C#'da oyun ve editör komut dosyaları yazabilir ve ardından hataları bulmak ve düzeltmek için güçlü hata ayıklama aracını kullanabilirsiniz. VSTU'nun en son sürümü Unity 2018.1'e destek sağlar ve Unity'nin ShaderLab gölgeli dili için sözdizimi boyama, Unity ile daha iyi senkronizasyon, daha zengin hata ayıklama ve MonoBehavior sihirbazı için geliştirilmiş kod oluşturmayı içerir. VSTU ayrıca Unity proje dosyalarınızı, konsol mesajlarınızı ve oyununuzu Visual Studio'ya başlatabilme yeteneğinizi de getirir, böylece kod yazarken Unity Editor'a geçiş yapmak için daha az zaman harcayabilirsiniz.

|**Daha fazlasını öğrenin**|
|--------------------|
|[Visual Studio ile Unity oyunları oluşturma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Unity için Visual Studio Tools hakkında daha fazla bilgi edinin](../cross-platform/visual-studio-tools-for-unity.md) |
|[Unity için Visual Studio Araçlarını kullanmaya başlayın](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Unity 2.0 Önizleme için Visual Studio Tools en son geliştirmeleri hakkında bilgi edinin](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio blog)|
|[Unity 2.0 Önizleme için Visual Studio Tools'a bir video girişi izleyin](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (Video)|
|[Unity (Unity](https://unity.com/) web sitesi) hakkında bilgi edinin|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projesine Office 365 API'leri ekleme](/office/developer-program/office-365-developer-program)
- [Azure Uygulama Hizmetleri - Mobil Uygulamalar](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
