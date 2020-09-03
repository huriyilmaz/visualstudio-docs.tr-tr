---
title: Visual Studio 2015 'deki yenilikler | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
caps.latest.revision: 364
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bdfae6235e7efb833eca0b87631af9204b4a678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387115"
---
# <a name="what39s-new-in-visual-studio-2015"></a>Visual Studio 2015 ' deki yenilikler&#39;
[!INCLUDE[vs2017banner](./includes/vs2017banner.md)]

Visual Studio 2015 ' e hoş geldiniz, tümleşik bir geliştirici üretkenlik araçları, bulut hizmetleri ve uzantıları, Web için harika uygulamalar ve Oyunlar oluşturma, Windows Mağazası, Android için ve iOS için harika uygulamalar ve oyunlar oluşturmalarına olanak tanır.

Bu sayfada, ilk olarak Visual Studio 2013 güncelleştirmelerden birinde sunulan özellikler dahil olmak üzere Visual Studio 2013 RTM 'den beri yeni olan en önemli özelliklerden bazıları vurgulanmıştır. Visual Studio 2015 ' deki yeniliklerin tüm listesi için bkz. [sürüm notları](https://www.visualstudio.com/news/vs2015-vs).

Visual Studio ALM 'deki pek çok geliştirme ve yeni özellik hakkında daha fazla bilgi edinmek için bkz. [TFS 2015](/azure/devops/server/whats-new#tfs-2015)yenilikleri.

## <a name="a-new-setup-experience"></a>Yeni bir kurulum deneyimi
 [!INCLUDE[downloadvs](./includes/downloadvs-md.md)]

 Visual Studio 2015 kurulum deneyimi, yalnızca ihtiyaç duyduğunuz bölümleri yüklemeniz için gereklidir. Bu, .NET veya Web geliştirme ile ilgili birçok yaygın senaryo için yüklemeyi daha hızlı hale getirir. Platformlar arası mobil geliştirme veya C++ ya da F # üzerinde çalışma gibi başka tür geliştirme yaparsanız, **özel** yükleme ' yi seçin ve ardından ihtiyacınız olan bileşenleri ve isteğe bağlı üçüncü taraf SDK 'ları seçin. Ayrıca, daha sonra özel bileşenlerden herhangi birini yükleyebilirsiniz. Örneğin, temel yükleme ' yi seçip yeni bir C++ projesi oluşturmayı denerseniz, C++ geliştirme araçları 'nı indirmeniz istenir.

 ![Visual Studio 2015 Kurulum Iletişim kutusu](./ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

## <a name="sign-in-across-multiple-accounts"></a>Birden çok hesap arasında oturum açın
 Visual Studio 2015 ile, yeni bir çoklu oturum açma deneyimi, birden çok Visual Studio hesabınız olduğunda bile çevrimiçi kaynaklara erişiminizi büyük ölçüde basitleştirmek üzere tasarlanmıştır. Visual Studio 'da oturum açtıktan sonra, tüm Visual Studio 2015 örnekleri ve makinenizde Blend 'yi otomatik olarak açtınız. Oturum açma, ayarlarınızı sizin için otomatik olarak başlatır. Visual Studio 2015 ' de hesabınız özellikler arasında paylaşıldığından, iyi bir belirteç olduğu sürece, Sunucu Gezgini içindeki Microsoft Azure aboneliğinizdeki **Takım Gezgini**ve kaynak ve web sitelerinden Visual Studio Team Services hesabınıza erişebilirsiniz. Ayrıca, Azure kaynaklarınızı Application Insights projeler için yeni proje Iletişim kutusunda görürsünüz ve yeni **bir bağlı hizmet ekle** Iletişim kutusunda Azure Mobile, Azure depolama, [Microsoft Office 365](https://msdn.microsoft.com/office/aa905340.aspx) ve [Saleforce.com geliştirici](https://developer.salesforce.com/) hesaplarınızı görürsünüz.

 Visual Studio 'da, siz veya yeni hesap Yöneticisi aracılığıyla birden çok kullanıcı hesabıyla çalışabilirsiniz. Ardından, hizmetlere bağlanırken veya çevrimiçi kaynaklara erişirken anında bu hesaplar arasında geçiş yapabilirsiniz. Visual Studio, eklediğiniz hesapları anımsar, böylece bunları herhangi bir Visual Studio veya Blend örneğinden kullanabilirsiniz. Ayrıca, aynı zamanda diğer bir cihazdaki bu hesaplardan biriyle çalışmaya başlayabilmeniz için, Visual Studio hesap listesini de (değerli kimlik bilgilerinizi dolaşıyoruz) kişiselleştirme hesabınızla birleştirirsiniz. Kuşkusuz hesap ayarları iletişim kutusundan hesapları dilediğiniz zaman kaldırabilirsiniz. Başlamak için bkz. [birden çok kullanıcı hesabıyla çalışma](./ide/work-with-multiple-user-accounts.md).

 ![Hesap Yöneticisi](./ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="choose-your-target-platforms"></a>Hedef Platformlarınızı seçin
 Visual Studio 2015, platformlar arası mobil cihaz geliştirmeyi destekler. İOS, Android ve Windows 'u hedefleyen uygulamalar ve Oyunlar yazabilir ve tüm Visual Studio IDE içinden ortak bir kod tabanı paylaşabilirsiniz. Dosya, yeni proje iletişim kutusunda tüm bu yeni proje türlerini görürsünüz.

 Kuşkusuz, klasik masaüstü uygulamaları için destek; diller, kitaplıklar ve araçlar için çok sayıda geliştirmelerle her zamankinden daha iyidir.

### <a name="cross-platform-mobile-apps-in-c-with-xamarin-for-visual-studio"></a>Visual Studio için Xamarin Ile C# ' de platformlar arası mobil uygulamalar
 Xamarin, iOS ve Android API 'Lerine yerel olarak bağlanan C# dilinde kod yazmanıza olanak tanıyan bir mobil çerçevedir. Microsoft, Android, iOS ve Windows Phone için, paylaşılan kodla tek bir çözümde geliştirme yapmanızı sağlayan bir uzantıdır ve Visual Studio için Xamarin 'in kendi sürümünde Xamarin ile yakından işbirliği yaptı. Xamarin ile, platformlar arasında en az değişimleri ile bir dil ve bir kod tabanı kullanırsınız.  Visual Studio için Xamarin, Visual Studio 2010 ve üzeri sürümlerde desteklenir. Xamarin 'in Starter sürümü Visual Studio 2015 ' ye dahildir. Başlamak için bkz. [Visual Studio 'Da Xamarin kullanarak yerel kullanıcı arabirimi ile uygulama oluşturma](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md).

### <a name="cross-platform-mobile-apps-in-htmljavascript-with-apache-cordova"></a>Apache Cordova ile HTML/JavaScript 'te platformlar arası mobil uygulamalar
 Apache Cordova için Visual Studio Araçları, Microsoft ile açık kaynak Apache Cordova topluluk arasındaki yakın işbirliğinin sonucudur. Araçlar, HTML, CSS ve JavaScript (veya Typescript) kullanarak platformlar arası mobil geliştirmeyi olanaklı hale sunmaktadır. Android, iOS ve Windows 'u tek bir kod tabanı ile hedefleyebilir ve JavaScript IntelliSense, DOM Gezgini, JavaScript Konsolu, kesme noktaları, izler, Yereller, Yalnızca kendi kodum ve daha fazlasını içeren Visual Studio IDE 'nin zenginliğini yaşayın.  Apache Cordova için Visual Studio Araçları, uygulamalarınızın ortak bir JavaScript API 'SI sağlayan eklentiler aracılığıyla tüm platformlarda yerel cihaz özelliklerine erişimi vardır. Başlamak için bkz. [Apache Cordova için Visual Studio araçları kullanmaya başlama](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42).

### <a name="cross-platform-mobile-games-in-c-with-unity"></a>Unity Ile C# ' de platformlar arası mobil oyunlar
 Unity, çok platformlu 2B ve 3B oyun geliştirme için yaygın olarak kullanılan bir platformdur. Oyununuzu C# dilinde yazabilir ve Android, iOS, Windows Phone ve diğer birçok platformda yerel olarak çalıştırabilirsiniz. Unity için Visual Studio Araçları, Unity 'yi Visual Studio IDE ile tümleştiren bir uzantıdır. Bu uzantıyla birlikte, Unity geliştiricileri için tasarlanan üretkenlik özelliklerinin yanı sıra, Visual Studio IDE ve hata ayıklayıcının tüm özelliklerini edinirsiniz. Unity için Visual Studio Araçları 2,0 Preview 2, Yereller ve Izleme pencerelerinde nesneler için daha iyi görselleştirme gibi birçok yeni özelliğe ek olarak Visual Studio 2015 için destek ekler. Microsoft, Unity için Visual Studio Araçları oluşturucuları olan SyntaxTree son zamanlarda elde etti. Unity için Visual Studio Araçları 2,0 Preview 2 ' yi indirmek için ve Unity için Visual Studio Araçları hakkında daha fazla bilgi için bkz. [Unity için Visual Studio Araçları 2,0](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad).

### <a name="cross-platform-apps-and-libraries-for-native-c"></a>Yerel C++ için platformlar arası uygulamalar ve kitaplıklar
 C++, çoğu mobil cihaz genelinde yerel olarak kullanılabilen bir dildir. Birden çok mobil platform hedefi için derlenebilir platformlar arası paylaşılan kod kitaplıklarını yazmak için bunu kullanabilirsiniz. C++ ' da tüm mobil uygulamaları bile oluşturabilirsiniz. Visual C++, platformlar arası kodunuzu düzenleme, derleme, dağıtma ve hata ayıklama araçları sağlar. Windows uygulamalarının şablonlarının yanı sıra, Xamarin karma uygulamaları içeren birden çok platform için Android yerel etkinlik uygulamaları, iOS uygulamaları veya paylaşılan kod kitaplığı projeleri şablonlarından projeler oluşturabilirsiniz. Platforma özgü IntelliSense, API 'Leri keşfetmenize ve Android, iOS veya Windows hedefleri için doğru kod oluşturmanıza olanak sağlar. Derlemenizi x86 veya ARM yerel platformları için yapılandırabilir, kodunuzu bir iOS simülatörünü veya ağa bağlı bir Mac üzerinde iOS cihazlarına, doğrudan bağlı Android cihazlara dağıtabilir veya test için performanslı Android için Microsoft Visual Studio Öykünücüsü kullanabilirsiniz. Visual Studio hata ayıklayıcısında kesme noktaları ayarlayabilir, değişkenleri izleyebilir, yığını görüntüleyebilir ve C++ kodunu adım adım izleyebilirsiniz. Birden çok uygulama platformunda en platforma özgü kod hariç tümünü paylaşabilir ve bunları Visual Studio 'da tek bir çözümle oluşturabilirsiniz.

 Platformlar arası C++ ' da çalışmaya başlamak için bkz. [Visual C++ platformlar arası mobil uygulamalar oluşturma](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)

### <a name="universal-windows-apps-for-any-windows-10-device"></a>Herhangi bir Windows 10 aygıtı için Evrensel Windows uygulamaları
 Evrensel Windows Platformu ve tek bir Windows çekirdeğiyle aynı uygulamayı telefonlardan masaüstü bilgisayarlardan herhangi bir Windows 10 cihazında çalıştırabilirsiniz. Bu Evrensel Windows uygulamalarını Visual Studio 2015 ve Evrensel Windows uygulama geliştirme araçları ile oluşturun.

 ![Evrensel Windows Platformu](./cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Uygulamanızı bir Windows 10 Phone, Windows 10 Masaüstü veya Xbox üzerinde çalıştırın. Aynı uygulama paketidir! Windows 10 tek ve birleştirilmiş çekirdeği kullanıma sunulmasıyla birlikte, tek bir uygulama paketi tüm platformlarda çalıştırılabilir. Birkaç platformda, platforma özgü davranışlardan yararlanmak üzere uygulamanıza ekleyebileceğiniz Uzantı SDK 'Ları vardır. Örneğin, mobil için bir uzantı SDK 'Sı, bir Windows Phone 'a basıldığında geri düğmesini işler. Projenizde bir uzantı SDK 'sına başvurdıysanız, bu SDK 'nın o platformda kullanılabilir olup olmadığını test etmek için yalnızca çalışma zamanı denetimleri ekleyin. Her platform için aynı uygulama paketine sahip olabilirsiniz!

 Bu [Evrensel Windows uygulamalarını](https://msdn.microsoft.com/library/dn975273.aspx)oluşturmak Için C#, Visual Basic, C++ veya JavaScript kullanın.

### <a name="web"></a>Web
 ASP.NET 5, MVC, WebAPI ve SignalR için önemli bir güncelleştirmedir ve Windows, Mac ve Linux üzerinde çalışır.  ASP.NET 5, modern bulut tabanlı uygulamalar oluşturmaya yönelik yalın ve birleştirilebilir bir .NET yığını sunmak için baştan sona tasarlanmıştır. Visual Studio 2015 araçları, Bower ve Grönlama gibi popüler web geliştirme araçlarıyla daha yakından tümleşiktir. Başlamak için  [net Web geliştirme ve araçlar bloguna](https://devblogs.microsoft.com/aspnet/)ait çok sayıda blog gönderisine bakın.

### <a name="classic-desktop-and-windows-store"></a>Klasik Masaüstü ve Windows Mağazası
 Visual Studio 2015, klasik masaüstü ve Windows Mağazası geliştirmeyi desteklemeye devam etmektedir. Windows geliştikçe, Visual Studio onunla birlikte gelişir.  Visual Studio 2015 ' de, .NET için kitaplıklar ve dillerin yanı sıra C++ ' ın tüm Windows sürümleri için geçerli olan önemli geliştirmeleri yaptı.

#### <a name="the-net-framework"></a>.NET Framework
 Microsoft, [!INCLUDE[net_v46](./includes/net-v46-md.md)] daha fazla senaryoyu etkinleştirmek için 150 yeni API ve 50 güncelleştirilmiş API 'ler sunmaktadır. Örneğin, artık daha fazla koleksiyon daha <xref:System.Collections.Generic.IReadOnlyCollection%601> kolay kullanılmasını sağlar. Ayrıca, daha önce bahsedilen ASP.NET 5, modern bulut tabanlı uygulamalar oluşturmak için yalın bir .NET platformu sunar.

 C# dilinde yazılan ve .NET Framework hedefleyen Windows Mağazası uygulamaları artık, uygulamaları Il yerine yerel koda derleyen ve [!INCLUDE[net_v46](./includes/net-v46-md.md)] Ayrıca, 64 bit tam zamanında (JIT) derleyicisi olan RyuJIT ' i de ekleyen .NET Native faydalanabilir.

 Yeni C# ve VB derleyicileri ("Roslyn") derleme sürelerini önemli ölçüde hızlandırır ve kapsamlı kod analizi API 'Leri sağlar. Visual Studio 2015, satır içi yeniden adlandırma, çözümleyiciler ve hızlı düzeltmeler dahil daha fazla yeniden düzenlemeler sağlamak için Roslyn avantajlarından yararlanır.

 C# ve Visual Basic dillerin her ikisi de çekirdek dilde ve IDE desteği 'nde birçok smalı geliştirmesi içerir. Bu geliştirmelerin hepsi, .NET kodlama deneyiminizi daha sezgisel, kullanışlı ve üretken hale getirmek için eklenir.

 Daha fazla bilgi için bkz. [Yenilikler ve](https://msdn.microsoft.com/library/1d971dd7-10fc-4692-8dac-30ca308fc0fa) [.net blogu](https://devblogs.microsoft.com/dotnet/).

#### <a name="c"></a>C++
 Visual C++, C++ 11/14 dil uyumluluğuna önemli gelişmeler sağlar platformlar arası mobil cihaz geliştirmeye yönelik destek, sürdürülebilir işlevleri ve await için destek (Şu anda C++ 17 ' de standartlaştırma için planlanmış), C çalışma zamanı kitaplığı (CRT) ve C++ standart kitaplığı (STL) uygulamalarında geliştirmeler ve hata düzeltmeleri, MFC 'de daha iyi derleme performansı, yeni tanılama özellikleri ve kod düzenleyicisinde yeni üretkenlik araçları.

 Daha fazla bilgi için bkz. [Visual C++](https://msdn.microsoft.com/library/1cc09fad-85a2-43c2-b022-bb99f5fe0ad7) yenilikler ve [Visual C++ blogu](https://devblogs.microsoft.com/cppblog/).

## <a name="device-preview-menu-bar"></a>Cihaz Önizleme menü çubuğu
 Evrensel Windows Platformu projelerinde, cihaz önizleme menü çubuğu, XAML tabanlı Kullanıcı arabirimlerinizin çeşitli ekran boyutlarında nasıl işleneceğini görmenizi sağlar.

 ![Cihaz Önizleme menüsü](./ide/media/vs2015-device-preview.png "vs2015_device_preview")

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama
 Visual Studio 2013, Visual Studio Grafik Tanılama Çerçeve Analizi, Windows Phone desteği, gölgelendirici düzenleme & Uygula ve komut satırı yakalama araçları gibi birçok yeni özellik eklemiştir. Ayrıca, DirectX12 uygulamalarında hata ayıklama desteği de eklenmiştir. Daha fazla bilgi için bkz. [Visual Studio grafik tanılama](./debugger/visual-studio-graphics-diagnostics.md).

## <a name="connect-to-services"></a>Hizmetlere bağlanma
 Visual Studio 2015, uygulamanızı hizmetlere bağlamayı her zamankinden daha kolay hale getirir.  Yeni bağlı hizmet ekleme Sihirbazı projenizi yapılandırır, gerekli kimlik doğrulama desteğini ekler ve hizmetinize göre hızla ve sorunsuz bir şekilde kodlamaya başlamanıza olanak sağlamak için gerekli NuGet paketlerini indirir. Bağlı hizmet ekleme Sihirbazı, birden çok kullanıcı hesabı ve abonelikle çalışmayı kolaylaştırmak için yeni hesap yöneticisiyle de tümleşir. Visual Studio 2015 ' de, aşağıdaki hizmetler için destek kullanıma sunulmuştur (bir hesabınız olduğunu varsayarak):

1. Azure Mobile Hizmetleri

2. Azure Storage

3. Office 365 (posta, kişiler, takvimler, dosyalar, kullanıcılar & grupları)

4. Salesforce

   Yeni hizmetler sürekli olarak eklenir ve sihirbazda "yeni hizmetleri bul bağlantısına" tıklayarak bunları bulabilirsiniz.

   ![Bağlı hizmetler Ekle Iletişim kutusu](./ide/media/vs2015-addconnectedservicedialog.png "VS2015_AddConnectedServiceDialog")

## <a name="design-your-ui"></a>Kullanıcı arabiriminizi tasarlama
 XAML kullanıcı arabirimlerini tasarlamak için Blend deneyimi önemli ölçüde geliştirilmiştir. Blend, IntelliSense dahil daha sezgisel bir kullanıcı arabirimi, daha güçlü XAML düzenlemesi özellikleri ve Visual Studio ile daha iyi tümleştirme sağlamak için tamamen yeniden tasarlanmıştır. Daha fazla bilgi için bkz. [Visual Studio 'DA xaml tasarlama ve Visual Studio için Blend](./designers/designing-xaml-in-visual-studio.md).

## <a name="cross-platform-debugging-support"></a>Platformlar arası hata ayıklama desteği
 Windows, iOS ve Android cihazlarda çalışan yerel mobil uygulamaları oluşturmak ve hatalarını ayıklamak için Visual Studio 'Yu kullanabilirsiniz. [Android Için Visual Studio öykünücüsü](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/)'nü kullanın veya bir cihazı bağlayın ve doğrudan Visual Studio 'da kodunuzda hata ayıklayın.

- **JavaScript/Cordova**. JavaScript ile Windows, iOS ve Android için yerel uygulamalar oluşturmak üzere [Apache Cordova için Visual Studio Araçları](https://msdn.microsoft.com/library/dn879821\(v=vs.140\).aspx) kullanın.

     MSDN kitaplığındaki uygulamanızda [hata ayıklama](https://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1) , Cordova Için Visual Studio hata ayıklama desteğiyle ilgili ayrıntılı bir bakış.

- **C#/Xamarin**. C# ile Visual Studio 'da Windows, iOS ve Android için yerel uygulamalar derlemek için [Xamarin](https://msdn.microsoft.com/library/dn879698\(v=vs.140\).aspx) kullanın.

     [Xamarin geliştirici kılavuzlarındaki](/xamarin/) cihazda [hata ayıklama (IOS](/xamarin/ios/deploy-test/debugging-in-xamarin-ios?tabs=windows) ) ve [hata](/xamarin/android/deploy-test/debugging/debug-on-device?tabs=windows) ayıklama hata ayıklama deneyimini anlatmaktadır.

- **C++/Android**. Windows ve Android için yerel uygulamalar oluşturmak için [ANDROID NDK](https://developer.android.com/tools/sdk/ndk/index.html) gibi üçüncü taraf araçlarla birlikte [Çoklu platform mobil uygulama geliştirme için Visual C++](cross-platform/visual-cpp-for-cross-platform-mobile-development.md) şablonlarını kullanın.

## <a name="debugging-and-diagnostics"></a>Hata Ayıklama ve Tanılama

Tanılamadaki yenilikler hakkında daha fazla bilgi için bkz. [profil oluşturma araçları](./profiling/what-s-new-in-profiling-tools.md)yenilikleri.

Aşağıda, kodunuzda farklı tanılama ve analiz türleri gerçekleştiren yeni veya geliştirilmiş araçlar verilmiştir:

### <a name="perftips"></a>PerfTips
 PerfTips, hata ayıklama sırasında yöntemlerin yürütme süresini görüntüler ve bu sayede profil oluşturucuyu çağırmak zorunda kalmadan performans sorunlarını hızla belirleyebilmenizi sağlar. Başlamak için bkz [. PerfTips: Visual Studio Ile hata ayıklarken bir bakışta performans bilgileri](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

### <a name="error-list"></a>Hata Listesi
 Hata listesi artık herhangi bir sütunda filtrelemeyi destekler. Ayrıca, bir kod değişikliği binlerce uyarı üretse bile, yazı yazarken C# veya Visual Basic çözümünüzün tamamında hataların, uyarıların ve kod analizinin canlı bir görünümünü de gösterir. Yeni Hata Listesi, mevcut kullanımla birlikte yeniden uyumludur. Daha fazla bilgi için bkz. [hata listesi pencere](./ide/reference/error-list-window.md).

### <a name="gpu-usage-tool"></a>GPU kullanımı aracı
 GPU kullanımı aracı, DirectX uygulamalarında ve oyunlarda GPU kullanım verilerini toplayıp analiz etmenize ve performans sorunlarının CPU veya GPU 'da olup olmadığına ilişkin sorunları gidermenize yardımcı olur. Aracı kullanmaya başlamak için [Visual C++ Team blog gönderisine](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/)bakın.

## <a name="live-code-analysis-light-bulbs"></a>Canlı Kod Analizi (hafif bulbs)
 C# için yeni Roslyn derleyicisi ve Visual Basic yalnızca daha hızlı derleme süreleri sağlamaz; canlı kod analizi gibi tamamen yeni senaryolar da sağlar; bu da, siz yazarken doğrudan kod Düzenleyicisi içinde zengin ve özelleştirilebilir geri bildirim ve öneriler sağlar. Visual Studio 2015 ' de, hafif bulbs, sol kenar boşluğunda (klavye kullanılırken) veya bir araç ipucunda (fareyle bir hata üzerine gelindiğinde) görüntülenir. Ampul, derleyicinin (muhtemelen özel bir kural kümesi kullanan) kodunuzda bir sorun algıladığını ve ayrıca sorunun nasıl çözüleceğini gösteren bir önerisine sahip olduğunu bildirir. Ampul gördüğünüzde, eyleme dönüştürülebilir öneriler için üzerine tıklayın.

 ![Visual Studio Code düzenleyicisinde hafif bulbs](./ide/media/vs2015-lightbulbs.png "VS2015_LightBulbs")

## <a name="enjoy-these-additional-ide-improvements"></a>Bu ek IDE geliştirmelerinden yararlanın

### <a name="synchronized-settings-roaming-settings"></a>Eşitlenmiş Ayarlar (dolaşım ayarları)
 Visual Studio 2013 metin Düzenleyicisi, keybindings, tema & yazı tipleri & renkler, başlangıç ve ortam diğer adları gibi en yaygın olarak yapılandırılmış ayarlardan bazıları için eşitlenmiş ayarları sunmuştur.  Visual Studio 2015, profesyonel, kurumsal, hızlı SKU 'Lar ve Blend gibi Visual Studio uygulamaları genelinde ayarlarınızı ve eşitleme ayarlarını eşitleyerek bu deneyimde gelişir. Visual Studio 2013 ' de kullandığınız hesapla Visual Studio 2015 ' de ilk kez oturum açtığınızda, eşitlenmiş ayarların Visual Studio 2013 uygulandığını görürsünüz. **Hızlı başlatma**bölümünde "Eşitle" yazarak ayarlarınıza erişebilir veya **araçlar > seçenekler > ortam eşitlenmiş ayarlar >**' ne gidin.

### <a name="automatic-extension-updates"></a>Otomatik uzantı güncelleştirmeleri
 Visual Studio Galerisi 'nde yeni bir sürüm kullanılabilir olduğunda, yüklü Visual Studio uzantıları artık otomatik olarak güncelleştirilecektir. Otomatik uzantı güncelleştirmelerini nasıl özelleştirebileceğinizi öğrenmek için bkz. [Visual Studio uzantılarını bulma ve kullanma](./ide/finding-and-using-visual-studio-extensions.md) .

### <a name="title-case-menus"></a>Başlık durumu Menüleri
 Konuştuğuz, dinliyoruz. Visual Studio menüleri bir kez daha, varsayılan olarak bir başlıktır. Ancak, tüm CAPS stilini beğeniyorsa, bu seçeneği başlangıç olarak veya **araçlar > seçenekler > genel** Özellik sayfasında ayarlayabilirsiniz:

 ![Visual Studio 2015 title Case ana menü komutları](./ide/media/vs2015-mainmenu.png "VS2015_MainMenu")

### <a name="high-resolution-images-and-touch-support"></a>Yüksek çözünürlüklü görüntüler ve dokunma desteği
 Visual Studio IDE artık, daha fazla görüntü (menüler, bağlam menüleri, araç penceresi komut çubukları ve Çözüm Gezgini içindeki bazı projelerde) için gerçek yüksek çözünürlüklü görüntülere sahiptir. Visual Studio Code Editor penceresinde bir dokunmatik ekranda artık dokunmatik ve basılı tutma, Pinç, dokunma ve bu gibi hareketleri kullanarak yakınlaştırma, kaydırma, metin seçme ve bağlam menülerini çağırma gibi hareketler de kullanabilirsiniz.

 ![Düzenleyicide dokunma desteği](./ide/media/vs2015-touchsupport.png "VS2015_TouchSupport")

### <a name="custom-layouts"></a>Özel düzenler
 Mağaza ve dolaşım özel pencere düzenleri oluşturabilirsiniz. Örneğin, masaüstü makinenizde kullanılmak üzere bir tercih edilen düzen ve dizüstü veya küçük ekran cihazında kullanılmak üzere farklı düzen tanımlayabilirsiniz. Ya da bir Kullanıcı Arabirimi projesi için bir düzen ve bir veritabanı projesi için bir düzen tercih edebilirsiniz. Anahtar bağlamaları, düzenler arasında hızlıca geçiş yapma olanağı sağlar. Bu düzenler, oturum açtığınızda herhangi bir Visual Studio örneğinde kullanılabilir. Daha fazla bilgi için bkz. [özel pencere düzenleri oluşturma](./misc/create-custom-window-layouts.md).

 ![Visual Studio özel düzen menü öğesi](./ide/media/vs2015-customlayout.png "VS2015_CustomLayout")

### <a name="notification-hub"></a>Bildirim Hub 'ı
 Bildirim Hub 'ı için Kullanıcı arabirimi hızlı bir şekilde taramayı kolaylaştırmak için kolaylaştırılmıştır. Performans sorunları, işleme sorunları ve kilitlenmeler dahil ek bildirim türleri eklenmiştir ve artık Visual Studio 'Nun bir bildirimi göstermeyi durdurmasını söyleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio bildirimleri](./ide/visual-studio-notifications.md).

### <a name="codelens-find-what-happened-to-your-code-enterprise-and-professional-editions-only"></a>CodeLens: kodunuza ne olduğunu bulun (yalnızca Enterprise ve Professional sürümleri)
 Kodunuzla ilgili bilgileri, Düzenleyiciden çıkmadan, kendi işinize odaklanmaya devam edin. Visual Studio Team Services (VSTS) veya Team Foundation Server (TFS) içinde depolanan kod için iş öğeleri, hatalar, kod incelemeleri gibi değişiklikleri ve diğer geçmişi gözden geçirebilirsiniz.

 Visual Studio Enterprise ve Visual Studio Professional, artık şunları yapabilirsiniz:

- Visual Studio düzenleyicisinde bir kod dosyasının tamamına yönelik geçmişi alın.

   ![CodeLens: kod dosyası ayrıntılarını al](./ide/media/codelensfilelevel.png "CodeLensFileLevel")

- Kodunuzu değiştiren kişileri gösteren bir grafiğe bakın. Bu, takımınızın değişikliklerinde desenleri bulmanıza ve etkilerini değerlendirmenize yardımcı olabilir.

   ![CodeLens: grafik olarak kod değişikliği geçmişine bakın](./ide/media/codelens.png "CodeLens")

- Kodunuzun en son ne zaman değiştirildiğini kolayca görün.

- Kodunuzu etkileyen diğer dallardaki değişiklikleri bulun.

  Bkz. [CodeLens](./ide/find-code-changes-and-other-history-with-codelens.md).

### <a name="design-and-modeling-tools-enterprise-edition-only"></a>Tasarım ve modelleme araçları (yalnızca Enterprise Edition)
 **Kod haritaları ve bağımlılık grafikleri**

 Visual Studio Enterprise, kodunuzda belirli bağımlılıkları anlamak istediğinizde kod haritaları oluşturarak bunları görselleştirin. Daha sonra, kodunuzun yanında görüntülenen Haritayı kullanarak bu ilişkilere gidebilirsiniz. Kod haritaları, kod çalışırken veya hata ayıkladığınızda koddaki yerinizi izlemenize yardımcı olabilir, bu nedenle kodunuzun tasarımı hakkında daha fazla bilgi edinirken daha az kod okuyacaksınız.

 Bu sürümde, komutları seçme, düzenleme, yönetme ve grup içeriklerinin yerleşimini değiştirme ile ilgili bölümlere gruplandırarak, kod öğeleri ve bağlantılarının kısayol menülerini kullanımı çok daha kolay hale aldık. Ayrıca, test projelerinin diğer projelerden farklı bir stilde görüntülendiğine ve haritadaki öğelerin simgelerini daha uygun sürümlere güncelleştirdiğine dikkat edin.

 ![Seçili öğeleri yeni kod haritasında göster](./ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Diğer iyileştirmeler şunlardır:

- **İyileştirilmiş yukarıdan aşağı diyagramlar**. Orta ila büyük Visual Studio çözümleri için artık çözümünüze yönelik daha kullanışlı bir kod Haritası almak için basitleştirilmiş bir mimari menüsü kullanabilirsiniz. Çözümünüzün derlemeleri, çözüm klasörlerine göre gruplandırılır, böylece bunları bağlamda görebilir ve çözümü yapılandırırken yerleştirdiğiniz çabadan yararlanabilirsiniz. Proje ve derleme başvurularını hemen görürsünüz, daha sonra bağlantı türleri görüntülenir. Ayrıca, çözümünüzün dışındaki derlemeler daha kompakt bir şekilde gruplandırılır.

- **Test projeleri farklı stillenmiştir ve filtrelenebilir**. Artık farklı stillendirilmiş olduklarından, haritadaki test projelerini daha kolay ve hızlı bir şekilde tanımlayabilirsiniz. Ayrıca, uygulamanın çalışma koduna odaklanabilmeniz için filtrelenebilir.

- **Basitleştirilmiş dış bağımlılık bağlantıları**. Bağımlılık bağlantıları artık System. Object, System. ValueType, System. Enum ve System. Delegate öğesinden devralmayı temsil etmez ve bu da kod haritanızda dış bağımlılıkları görmeyi kolaylaştırır.

- **' Bağımlılık bağlantılarında detaya gitme ', filtreleri hesaba götürür**. Bir bağımlılık bağlantısına katkılarını anlamak için, bu kullanışlı bir diyagramı genişleterek yararlı bir diyagram alırsınız. Diyagram daha az dağınık ve seçtiğiniz bağlantı filtreleme seçeneklerini dikkate alır.

- **Kod öğeleri bağlamlarıyla birlikte bir kod haritasına eklenir**. Diyagramlar artık bağlamlarıyla göründüğünden (gerekirse filtreleyebileceğiniz derleme ve çözüm klasörüne kadar), Çözüm Gezgini, Sınıf Görünümü Nesne Tarayıcısı; öğesinden kod öğelerini Sürükleyip bırakırken daha kullanışlı diyagramlar alırsınız. Çözüm Gezgini öğeleri seçerken veya kod eşlemesinde göster ' i seçerken.

- **Reaktif kod haritalarını daha hızlı alın**. Sürükle ve bırak işlemleri anında sonuç verir ve düğümler arasındaki bağlantılar, düğümü genişletme veya daha fazla düğüm isteme gibi sonraki Kullanıcı tarafından başlatılan işlemleri etkilemeden çok daha hızlı bir şekilde oluşturulur. Çözüm oluşturmadan kod eşlemeleri oluşturduğunuzda, tüm köşe durumları (derlemeler derlenmediği gibi) artık işlenir.

- **Çözümünüzü yeniden oluşturmayı atlayın.** Diyagramlar oluştururken ve düzenlenirken daha iyi performans sağlar.

- **Kod öğesi düğümlerini ve gruplarını filtreleyin**. Kendi kategorilerine göre kod öğelerini göstererek veya gizleyerek ve kod öğelerini çözüm klasörlerine, derlemelere, ad alanlarına, proje klasörlerine ve türlerine göre gruplandırarak haritalarınızı hızlıca kolayca kaldırabilirsiniz.

- **Diyagramları daha kolay okunabilir hale getirmek için Ilişkileri filtreleyin**. Artık bağlantı filtrelemesi, çapraz grup bağlantıları için de geçerlidir. Bu, filtre penceresiyle birlikte çalışarak önceki sürümlerden daha az zorlanmaya neden olur.

- **Sınıf görünümü ve nesne tarayıcısı diyagram oluşturun**. Dosyaları ve derlemeleri Sınıf Görünümü ve Nesne Tarayıcısı Windows ' a yeni veya var olan bir haritaya sürükleyip bırakın.

  Bkz. [çözümlerinizde harita bağımlılıkları](./modeling/map-dependencies-across-your-solutions.md).

  **Bu sürümdeki diğer tasarım ve modelleme değişiklikleri:**

- **Katman diyagramları**. Sınıf Görünümü ve Nesne Tarayıcısı kullanarak bu diyagramları güncelleştirin. Yazılım tasarımı gereksinimlerini karşılamak için, yazılım için istenen bağımlılıkları anlatmak üzere katman diyagramlarını kullanın. Bu kısıtlamalara uymayan kodu bularak ve sonraki kodu bu taban çizgisiyle doğrulayarak kodu bu tasarımla tutarlı tutun.

- **UML diyagramları**. Artık Koddan UML sınıf diyagramları ve sıra diyagramları oluşturamazsınız. Ancak, yeni UML öğelerini kullanarak bu diyagramları yine de oluşturabilirsiniz.

- **Mimari Gezgini**. Artık diyagramlar oluşturmak için Mimari Gezgini 'ni kullanamazsınız. Ancak Çözüm Gezgini kullanmaya devam edebilirsiniz.

## <a name="visual-studio-extensibility-tools"></a>Visual Studio Genişletilebilirlik Araçları
 Artık, kurulum sırasında isteğe bağlı bir bileşen olarak dahil olduklarından Visual Studio Genişletilebilirlik Araçları (VS SDK ve şablonları) yüklemek hiç daha kolay değildir.  Genişletilebilirlik Araçları, geliştiricilerin özelleştirmek ve Visual Studio 'ya özellik eklemek için uzantı yazmasına izin verir. Visual Studio genişletilebilirliği hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK](./extensibility/visual-studio-sdk.md)

 Özel yüklemenize yönelik genişletilebilirlik araçlarını eklemek istiyorsanız, bunları **Özellikler/ortak Araçlar/Visual Studio genişletilebilirlik Araçları**altında bulabilirsiniz.  Ayrıca, **Yeni proje** iletişim kutusunu açıp **Visual C#/genişletilebilirlik**altında **Visual Studio genişletilebilirlik Araçları** öğesini seçerek de genişletilebilirlik Araçları 'nı daha sonra yükleyebilirsiniz.

## <a name="please-give-feedback"></a>Lütfen geri bildirimde bulunun
 Visual Studio ekibine neden geri bildirim gönderilsin? Müşteri geri bildirimlerine önem veriyoruz. Aslında, geri bildirim sistemimize gelen her bir geri bildirim parçasını gözden geçiririz. Geri bildiriminiz yaptığımız çok fazla.

### <a name="send-a-smile"></a>Gülümseme Gönder
 Beklentilerinizi karşıladığımız veya aşdığımızda bize beğendiklerinizi söylememize yardımcı olun. Yeni özellikleri tasarlarken ve uygularken, tasarım kararlarımızla yardım almak istediğiniz özelliklerle ilgili verileri kullanırız. Bu nedenle, Visual Studio 'da bir özelliği beğenmeniz halinde bize bildirin. Bu kolay bir işlemdir ve doğrudan IDE içinden yapabilirsiniz.

 Başlık çubuğundaki sarı gülen yüz düğmesine tıkladıktan sonra neleri beğendiklerinizi söyleyin, sonra **gülümseme Gönder** düğmesine tıklayın.

 Bu kadar! Geri bildiriminizi doğru ekibe yönlendirirler ve daha da çok daha fazla bilgi almak için daha hızlı bir şekilde çalışmaya başlayın.

### <a name="send-a-frown"></a>Kaş çatma Gönder
 Üründe geliştirmeler yapmamız gereken yerde, öncelikle müşterilerimiz için en önemli olan şeylere odaklanarak kapsamımızın yönetilmesine yardımcı olur. Sizi söyleyerek, doğrudan IDE 'nin içinden **kaş çatma Gönder** özelliğini kullanarak bize bunu anlatın. Bu süper basit bir süreç da yaptık:

 Başlık çubuğundaki sarı gülen yüz düğmesine tıklayın ve ardından **kaş çatma Gönder**' e tıklayın. Beğenmediğiniz şeyleri bize söyleyin ve sonra kaş çatma Gönder düğmesine tıklayın. Daha fazla bilgi için bkz. [bizimle Iletişim kurun](./ide/talk-to-us.md).

### <a name="report-crashes-unresponsive-and-performance-issues"></a>Rapor kilitlenmeler, yanıt vermeyen ve performans sorunları
 Bazen, bir kasaydaki hızlı Not, beğenmediğiniz bir şeyin tam etkisini iletmek için yeterli değildir. Visual Studio 'Nun yanıt vermeyi durdurduğu, çöktüğü veya başka bir performans sorunuyla karşılaşacağı zamanlar için, bir kaş n gönderdikten sonra görüntülenen iletişim kutusunu kullanarak yeniden üretme adımlarını, kilitlenme dökümlerini ve izleme dosyalarını kolayca paylaşabilirsiniz.

 İlk olarak, yukarıda açıklandığı gibi bir kaş çatma gönderin. Açılan iletişim kutusunda, geri bildirimlerinizi varsayılan etiketlerden biriyle etiketleyebilir ya da kendi etiketinizi oluşturabilirsiniz. Etiketler, görüşlerinizi uygun özellik ekibine yönlendirmemize yardımcı olur. **Kategori Seç** açılan listesinde, raporladığınız sorunu temsil eden seçeneği belirleyin ve ardından sorunu yeniden oluşturmak için adımları izleyin. Visual Studio 'Yu kullanarak geri bildirim bildirme hakkında ayrıntılı adımlar da mevcuttur. Daha fazla bilgi için bkz. [Visual Studio gülümseme Gönder yönergeleri](https://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b).

## <a name="see-also"></a>Ayrıca Bkz.

* [Apache Cordova platformlar arası uygulamalar oluşturun](https://msdn.microsoft.com/library/34d3c1be-22b3-4812-97fb-10b4e8ad2134)
* [Visual Studio’da Xamarin kullanarak yerel kullanıcı arabirimi ile uygulama oluşturma](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)
* [Visual C++ platformlar arası mobil uygulamalar oluşturun](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)
* [Intellitest ile kodunuz için birim testleri oluşturma](./test/generate-unit-tests-for-your-code-with-intellitest.md)
* [Birden çok kullanıcı hesabıyla çalışma](./ide/work-with-multiple-user-accounts.md)
* [Özel pencere düzenlerini oluşturma](./misc/create-custom-window-layouts.md)
* [Ampullerle hızlı eylemler gerçekleştirme](./ide/perform-quick-actions-with-light-bulbs.md)
* [Visual Studio 2017 ' deki yenilikler](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
