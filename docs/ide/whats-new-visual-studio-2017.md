---
title: Visual Studio 2017’deki yenilikler
titleSuffix: ''
description: Visual Studio 2017'deki yeni özellikler hakkında bilgi edinin.
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: de26054894783df283d38223a59741c0500d0bc5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74955042"
---
# <a name="whats-new-in-visual-studio-2017"></a>Visual Studio 2017’deki yenilikler

**[15.9 sürümü](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017) için güncellendi**

Visual Studio'nun önceki sürümünden yükseltme mi arıyorsunuz? Visual Studio 2017'nin size sunabileceği ler: Herhangi bir dev, herhangi bir uygulama ve herhangi bir platform için benzersiz üretkenlik. Android, iOS, Windows, Linux, web ve bulut için uygulamalar geliştirmek için Visual Studio 2017'yi kullanın. Hızlı kod yazın, kolayca hata ayıklama ve tanılama yapın, sık sık test edin ve güvenle kullanıma sunun. Ayrıca, kendi uzantılarınızı oluşturarak Visual Studio’yu özelleştirebilir ve kapsamını genişletebilirsiniz. Sürüm denetimini kullanın, çevik olun ve bu sürümle verimli bir şekilde işbirliği yapın!

>[!div class="button"]
>[Visual Studio’yu İndir](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

Bir önceki sürüm olan Visual Studio 2015'ten bu yana yapılan değişikliklerin üst düzey özeti:

* **[Yeniden tanımlanan temeller](#redefined-fundamentals)**. Yeni bir kurulum deneyimi, daha hızlı yükleyebileceğiniz ve ihtiyacınız olduğunda istediğinizi yükleyebileceğiniz anlamına gelir.
* **[Performans ve üretkenlik.](#performance-and-productivity)** Yeni ve modern mobil, bulut ve masaüstü geliştirme özelliklerine odaklandık. Ve, Visual Studio daha hızlı başlar, daha duyarlı, ve eskisinden daha az bellek kullanır.
* **[Azure ile bulut uygulaması geliştirme.](#cloud-app-development-with-azure)** Yerleşik Azure araçları paketi, Microsoft Azure tarafından desteklenen bulut ilk uygulamaları kolayca oluşturmanıza olanak tanır. Visual Studio, Azure'da uygulamaları ve hizmetleri yapılandırmayı, oluşturmayı, hata ayıklamayı, paketlemeyi ve dağıtmayı kolaylaştırır.
* **[Windows uygulaması geliştirme](#windows-app-development)**. Tüm Windows 10 cihazlar &ndash; pc, tablet, telefon, Xbox, HoloLens, Surface Hub ve daha fazlası için tek bir proje oluşturmak için Visual Studio 2017'deki UWP şablonlarını kullanın.
* **[Mobil uygulama geliştirme](#mobile-app-development)**. Çok platformlu mobil gereksinimlerinizi tek bir temel kod tabanı ve beceri kümesiyle biraraya getiren Xamarin ile hızlı bir şekilde yenilik yapın ve sonuç alın.
* **[Çapraz platform geliştirme](#cross-platform-development)**. Yazılımı hedeflenen herhangi bir platforma sorunsuz bir şekilde teslim edin. Redgate Veri Araçları aracılığıyla DevOps işlemlerini SQL Server'a genişletin ve Visual Studio'daki veritabanı dağıtımlarını güvenli bir şekilde otomatikleştirin. Veya Windows, Linux ve macOS işletim sistemlerinde değiştirilmemiş uygulamalar ve kitaplıklar yazmak için .NET Core'u kullanın.
* **[Oyun geliştirme](#games-development)**. Visual Studio Tools for Unity (VSTU) ile Visual Studio'yu kullanarak C#'da oyun ve editör komut dosyaları yazabilir ve ardından hataları bulmak ve düzeltmek için güçlü hata ayıklama aracını kullanabilirsiniz.
* **[AI geliştirme](#ai-development)**. AI için Visual Studio Tools ile, AI inovasyonunu hızlandırmak için Visual Studio'nun üretkenlik özelliklerini kullanabilirsiniz. Sağlam deneme özellikleri için Azure Machine Learning ile sorunsuz bir şekilde entegre olan Derin Öğrenme / Yapay Eğitim çözümleri oluşturun, test edin ve dağıtın.

> [!NOTE]
> Visual Studio 2017'deki yeni özelliklerin ve işlevlerin tam listesi için [Geçerli sürüm notlarına](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)bakın. Ve gelecekteki özellik teklifleri bir göz için, [Önizleme sürüm notları](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017)bakın.

Visual Studio 2017'nin en önemli gelişmeleri ve yeni özellikleri hakkında daha ayrıntılı bilgiler burada.

## <a name="redefined-fundamentals"></a>Yeniden tanımlanan temeller

### <a name="a-new-setup-experience"></a>Yeni bir kurulum deneyimi

Visual Studio, ihtiyacınız olan özellikleri ihtiyacınız olduğunda yüklemenizi daha kolay ve hızlı hale getirir. Ve, çok temiz bir şekilde uninstalls.

Visual Studio'yu yüklediğinizde dikkat edilmesi gereken en önemli değişiklik yeni kurulum deneyimidir. İş **Yükleri** sekmesinde, ortak çerçeveleri, dilleri ve platformları temsil edecek şekilde gruplanmış yükleme seçeneklerini görürsünüz. .NET masaüstü geliştirmeden Windows, Linux ve iOS'ta C++ uygulama geliştirmeye kadar her şeyi kapsar.

İhtiyacınız olan iş yüklerini seçin ve gerektiğinde değiştirin.

![Visual Studio 2017 kurulum iletişim kutusu](../install/media/install-visual-studio-enterprise.png)

Ayrıca kurulumunuzda ince ayar yapmak için seçenekleriniz de var:

* İş yüklerini kullanmak yerine kendi bileşenlerinizi mi seçmek istiyorsunuz? Yükleyiciden **Bireysel bileşenler** sekmesini seçin.
* Windows dil seçeneğini de değiştirmek zorunda kalmadan Dil Paketleri yüklemek mi istiyorsunuz? Yükleyicinin **Dil paketleri** sekmesini seçin.
* **15.7'de yeni**: Visual Studio'nun yüklendiği yerin konumunu değiştirmek ister misiniz? Yükleyicinin **Yükleme seçenekleri** sekmesini seçin.

Size yol gösteren adım adım talimatlar da dahil olmak üzere yeni yükleme deneyimi hakkında daha fazla bilgi edinmek için [Görsel Stüdyo yükle](../install/install-visual-studio.md) sayfasına bakın.

### <a name="a-focus-on-accessibility"></a>Erişilebilirlik üzerinde odaklanma

**Yeni 15.3**, biz Visual Studio ve birçok müşteri kullandığı yardımcı teknolojiler arasındaki uyumluluğu artırmak için 1.700 hedefli düzeltmeler üzerinde yaptı. Ekran okuyucular, yüksek kontrastlı temalar ve diğer yardımcı teknolojilerle her zamankinden daha uyumlu düzinelerce senaryo vardır. Hata ayıklama, editör ve kabuk da önemli gelişmeler elde etti.

Daha fazla bilgi için [Visual Studio 2017 sürüm 15.3 blog gönderisinde Erişilebilirlik geliştirmelerine](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) bakın.

## <a name="performance-and-productivity"></a>Performans ve üretkenlik

### <a name="sign-in-across-multiple-accounts"></a>Birden çok hesapta oturum açma

Visual Studio'da, Kullanıcı hesaplarını Team Explorer, Azure Araçları, Microsoft Mağazası yayımlama ve daha fazlası arasında paylaşmanıza olanak tanıyan yeni bir kimlik hizmeti sunduk.

Sen de daha uzun süre oturum açabilirsin. Visual Studio her 12 saatte bir tekrar oturum açmanızı istemez. Daha fazla bilgi edinmek için daha az Visual Studio oturum açma komut u blog [gönderisine](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/) bakın.

### <a name="start-visual-studio-faster"></a>Visual Studio'ya daha hızlı başlayın

Yeni Visual Studio Performans Merkezi, IDE başlangıç sürenizi optimize edinmenize yardımcı olabilir. Performans Merkezi, IDE başlatmayı yavaşlatabilecek tüm uzantıları ve araç pencerelerini listeler. Uzantıların ne zaman başlayacağını veya araç pencerelerinin başlangıçta açık olup olmadığını belirleyerek başlangıç performansını artırmak için kullanabilirsiniz.

### <a name="faster-on-demand-loading-of-extensions"></a>Uzantıların daha hızlı isteğe bağlı yüklemesi

Visual Studio uzantılarını hareket ettiriyor (ve üçüncü taraf uzantılarıyla da çalışıyor) böylece IDE'nin başlatılması yerine isteğe bağlı olarak yüklenirler. Hangi uzantıların başlatmayı, çözüm yükünü ve yazma performansını etkilediğini mi merak ediyor musunuz? Bu bilgileri**Görsel Stüdyo Performansını Yönetmeye Yardım'da** **Help** > görebilirsiniz.

  ![Visual Studio 2017'de Seçenekler iletişim kutusu](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Roaming Extensions Manager ile uzantılarınızı yönetme

Visual Studio'da oturum açtığınızda her geliştirme ortamını en sevdiğiniz uzantılarla ayarlamak daha kolaydır. Yeni Roaming Extension Manager, bulutta senkronize bir liste oluşturarak en sevdiğiniz uzantıları izler.

Uzantılarınızın listesini Visual Studio'da görmek **için, Araçlar** > **Uzantıları & Güncelleştirmeleri'ni**tıklatın ve ardından **Dolaşım Uzantısı Yöneticisi'ni**tıklatın.

![Visual Studio 2017 - Uzantılar ve Güncellemeler iletişim kutusu](media/vs2017ide-extensions-and-updates.png)

Dolaşım Uzantısı Yöneticisi yüklediğiniz tüm uzantıları izler, ancak Dolaşım listenize hangilerini eklemek istediğinizi seçebilirsiniz.

![Visual Studio 2017 - Uzantılar ve Güncellemeler iletişim kutusu](media/vs2017ide-RoamingExtensionManager.png)

Dolaşım Uzantısı Yöneticisi'ni kullandığınızda, listenizde üç simge türü vardır:

* ![Roamed](media/vs2017ide-roamedicon.png) simgesi **_Roamed_**: Bu Dolaşım Listesinin bir parçası olan ancak makinenize yüklenmemiş bir uzantı.
  (İndir düğmesini kullanarak **Download** bunları yükleyebilirsiniz.)
* ![Roamed & Installed simgesi](media/vs2017ide-roamedinstalledicon.png) **_Roamed & Installed_**: Bu Dolaşım Listesinin bir parçası olan ve geliştirme ortamınıza yüklenen tüm uzantılar.
  (Gezinmek istemediğiniz karar verirseniz, **Dolaşımı Durdur** düğmesini kullanarak bunları kaldırabilirsiniz.)
* ![Installed](media/vs2017ide-installedicon.png) simgesi **_Installed_**: Bu ortamda yüklü olan ancak Dolaşım Listenizin bir parçası olmayan tüm uzantılar.
  (Dolaşımı **Başlat** düğmesini kullanarak Dolaşım Listesi'ne uzantı ekleyebilirsiniz.)

Oturum açmışken indirdiğiniz tüm uzantılar, **Roamed & Installed**olarak listenize eklenir. Uzantı daha sonra Dolaşım listenizin bir parçası olur ve bu da herhangi bir makineden erişim sağlar.

### <a name="experience-live-unit-testing"></a>Canlı birim testini deneyimle

Visual Studio Enterprise 2017'de canlı ünite testi, kodlama yaparken editörde canlı ünite test sonuçları ve kod kapsamı sağlar. Hem .NET Framework hem de .NET Core için C# ve Visual Basic projeleri ile çalışır ve MSTest, xUnit ve NUnit'in üç test çerçevesini destekler.

![Live Unit Testing](media/lut-codewindow.png)

Daha fazla bilgi için Canlı [Birim Testini Tanıtın'a](../test/live-unit-testing-intro.md)bakın. Visual Studio Enterprise 2017'nin her sürümüne eklenen yeni özelliklerin listesi için [Canlı Birim Testinde yeniliklere](../test/live-unit-testing-whats-new.md)bakın.

### <a name="set-up-a-cicd-pipeline"></a>CI/CD işlem hattı ayarlama

#### <a name="automated-testing"></a>Otomatik test

Otomatik test herhangi bir DevOps boru hattının önemli bir parçasıdır. Çözümünüzü çok daha kısa döngülerde tutarlı ve güvenilir bir şekilde test etmenizi ve serbest bırakmanızı sağlar. CI/CD (Sürekli Tümleştirme ve Sürekli Teslimat) akışları işlemin daha verimli hale getirilmesine yardımcı olabilir.

Otomatik testler hakkında daha fazla bilgi için DevOps blog [gönderisinde otomatik testler için CI/CD ardışık hattına](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) bakın.

Ve, Visual Studio DevLabs uzantısı [için Sürekli teslimat araçlarında](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) yenilikler hakkında daha fazla bilgi için, [güvenle Commit bakın: Commit zaman kodu kalitesi](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/) blog yazısı.

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE geliştirmeleri

#### <a name="multi-caret-editing"></a>Çoklu giriş işareti düzenleme

**15.8'de Yeni**: Bir dosyada aynı anda birden fazla konumu düzenlemek artık kolaydır. Dosyadaki birden çok konumda ekleme noktaları ve seçimler oluşturarak başlayın. Ardından, aynı düzenlemeyi aynı anda iki veya daha fazla yerde yapmak için çok yönlü düzenleme özelliğini kullanın.

Daha fazla bilgi için [Bul ve metin](finding-and-replacing-text.md) sayfasının çok yönlü [seçim](finding-and-replacing-text.md#multi-caret-selection) bölümüne bakın.

#### <a name="keep-keybinding-profiles-consistent"></a>Anahtar bağlama profillerini tutarlı tutun

**15.8'de Yeni**: Şimdi, iki yeni klavye profili yle tuş bağlamalarınızı araçlar arasında tutarlı tutabilirsiniz: Visual Studio Code ve ReSharper (Visual Studio). Bu şemaları **Araçlar** > **Seçenekleri** > **Genel** > **Klavye** ve üst açılır menü altında bulabilirsiniz.

  ![Visual Studio Code ve ReSharper için yeni anahtar bağlama profilleri](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Yeni yeniden düzenleme kullanma

Yeniden düzenleme, kodunuzu yazıldıktan sonra geliştirme işlemidir. Yeniden düzenleme, davranışını değiştirmeden kodun iç yapısını değiştirir. Sık sık yeni refactorings ekleyin; burada sadece birkaçı şunlardır:

* Parametre ekleme (CallSite'den)
* Geçersiz kılmalar oluşturun
* Adlandırılmış bağımsız değişken ekleme
* Parametreler için null-check ekleme
* Sayısal ayırıcıları literals'e ekleme
* Sayısal literaller için temel değiştirme (örneğin, hex ile ikili)
* If-to-switch'i dönüştürme
* Kullanılmayan değişkeni kaldırma

Daha fazla bilgi için [Hızlı Eylemler'e](common-quick-actions.md)bakın.

#### <a name="interact-with-git"></a>Git ile etkileşim

Visual Studio'da bir projeyle çalışırken, kodunuzu bir Git hizmetine ayarlayabilir, hızlı bir şekilde işleyebilir ve yayımlayabilirsiniz. Ayrıca, IDE'nin sağ alt köşesindeki düğmelerden menü tıklamalarını kullanarak Git depolarınızı yönetebilirsiniz.

![Visual Studio 2017 Git iletişim kutusuyla etkileşime giriyor](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Geliştirilmiş navigasyon denetimlerini deneyimleyin

A'dan B'ye daha fazla güven ve daha az dikkat dağıtıcı şeylerle girmenize yardımcı olmak için navigasyon deneyimini yeniledik.

* **15.4'te Yeni**: **Tanıma Git** (**Ctrl**+**tıklayın** veya **F12**) &ndash; Fare kullanıcıları **Ctrl** tuşuna basArak üye tanımına gitmek için daha kolay bir yol vardır ve sonra üyeyi tıklatır. **Ctrl** tuşuna basmak ve bir kod simgesinin üzerinde gezinmek, onu alt çizer ve bir bağlantıya dönüştürür. Daha fazla bilgi [için Tanım ve Peek Tanımına Git'e](go-to-and-peek-definition.md) bakın.

* **Uygulamaya Git** (**Ctrl**+**F12**) &ndash; Herhangi bir taban türünden veya üyeden çeşitli uygulamalarına gidin.

* **Tüme Git** (**Ctrl**+**T** &ndash; veya **Ctrl**+**,**) Doğrudan herhangi bir dosya/tür/üye/sembol bildirimine gidin. Sonuç listenizi filtreleyebilir veya sorgu sözdizimini kullanabilirsiniz (örneğin, dosyalar için "f searchTerm", türler için "t searchTerm" vb.).

  ![Geliştirilmiş Tüme Git](media/vs2017ide-navigation-go-to.png)

* **Tüm Başvuruları Bul** (**Shift**+**F12**) &ndash; Sözdizimi renklendirmeile, Tüm Başvuru sonuçlarını proje, tanım ve yol birleşimine göre gruplandırabilirsiniz. Ayrıca, özgün sonuçlarınızı kaybetmeden diğer başvuruları bulmaya devam edebilmeniz için sonuçları "kilitleyebilirsiniz".

  ![Yeni Tüm Başvuruları Bul aracı](media/vs2017ide-find-all-references.png)

* **Visualizer** &ndash; Noktalı, gri dikey çizgiler (girinti kılavuzları) görünüm çerçeveniz içinde bağlam sağlamak için kodda yer işareti görevi göremez. Bunları popüler Verimlilik Elektrikli El Aletleri'nden tanıyabilirsiniz. Kaydırmak zorunda kalmadan istediğiniz zaman hangi kod bloğunda olduğunuzu görselleştirmek ve keşfetmek için bunları kullanabilirsiniz. Çizgilerin üzerinde gezinmek, o bloğun ve ebeveynlerinin açOlduğunu gösteren bir araç ucu görüntüler. TextMate gramerleri ile desteklenen tüm dillerin yanı sıra C#, Visual Basic ve XAML için de kullanılabilir.

  ![Visual Studio 2017 yapı görselleştiricisi](media/vsIDE-StructureVisualizer.png)

Yeni üretkenlik özellikleri hakkında daha fazla bilgi için [Visual Studio 2017: Verimlilik, Performans ve Ortaklar](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/) blog gönderisi için bkz.

### <a name="visual-c"></a>Visual C++

Visual Studio'da C++ Core Guidelines'ı Visual Studio ile dağıtmak, C++11 ve C++ özellikleri için gelişmiş destek ekleyerek derleyiciyi güncellemek ve C++ kitaplıklarına işlevsellik ekleme ve güncelleme gibi çeşitli iyileştirmeler görürsünüz. Ayrıca C++ IDE'nin performansını, kurulum iş yüklerini ve daha fazlasını geliştirdik.

Ayrıca, 250'den fazla hatayı düzeltdik ve derleyici ve araçlardaki sorunları bildirdik, çoğu müşteriler tarafından [C++ için Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/62/index.html "C++ için Geliştirici Topluluğu")aracılığıyla gönderildi.

Ayrıntılar için Visual [C++ için görsel 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) sayfasında yenilikler sayfasına bakın.

### <a name="debugging-and-diagnostics"></a>Hata ayıklama ve tanılama

#### <a name="run-to-click"></a>Tıklanan Satıra Kadar Çalıştır

Artık, istediğiniz çizgide durmak için bir kesme noktası ayarlamadan hata ayıklama sırasında daha kolay ileri atlayabilirsiniz. Hata ayıklayıcıda durdurulduğunuzda, kod satırının yanında görünen simgeyi tıklatmanız yeterlidir. Kodunuz, kod yolunuza bir sonraki vurulduğunda bu satırda çalışır ve durur.

![Visual Studio 2017 hata ayıklama - Tıkla](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Yeni Özel Durum Yardımcısı

Yeni Özel Durum Yardımcısı, özel durum bilgilerinizi bir bakışta görüntülemenize yardımcı olur. Bilgiler, iç özel durumlara anında erişilen kompakt bir biçimde sunulur. Bir NullReferenceException tanılarken, Özel Durum Yardımcısı'nın içinde ne kadar null olduğunu hızlı bir şekilde görebilirsiniz.

![Visual Studio'da Yeni Özel Durum Yardımcısı iletişim kutusu](media/vs2017ide-ExceptionHelper.png)

Daha fazla bilgi için Visual Studio blog [gönderisinde yeni Özel Durum Yardımcısını Kullanın'a](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) bakın.

#### <a name="snapshots-and-intellitrace-step-back"></a>Anlık Görüntüler ve IntelliTrace adım geri

**15.5'te yeni**: IntelliTrace adım geri otomatik olarak her kesme noktası ve hata ayıklama adım etkinliğinde uygulamanızın anlık görüntüsünü alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenizi ve uygulamanın durumunu geçmişte olduğu gibi görüntülemenizi sağlar. IntelliTrace adım geri önceki uygulama durumunu görmek istediğinizde zaman kazandırabilir, ancak hata ayıklama yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemiyorum.

**Hata Ayıklama** araç çubuğundaki **Geri Adım** ve **İleri Adım** düğmelerini kullanarak anlık görüntüleri gezebilir ve görüntüleyebilirsiniz. Bu düğmeler, **Tanılama Araçları** penceresindeki **Olaylar** sekmesinde görünen olaylarda gezinir. Bir olaya geri veya ileri adım atmak, seçili olaydaki geçmiş hata ayıklamayı otomatik olarak etkinleştirir.

![Visual Studio'da Yeni Özel Durum Yardımcısı iletişim kutusu](../debugger/media/intellitrace-step-back-icons-description.png  "İleri adım ve İleri düğmeleri")

Daha fazla bilgi için [IntelliTrace adım geri sayfasını kullanarak anlık görüntüleri görüntüle'ye](../debugger/view-historical-application-state.md) bakın.

### <a name="containerization"></a>Kapsayıcıyla taşıma

Kapsayıcılar, gelişmiş üretkenlik ve DevOps çevikliğiyle birlikte daha yüksek uygulama yoğunluğu ve daha düşük dağıtım maliyeti sağlar.

#### <a name="docker-container-tooling"></a>Docker Kapsayıcısı Araçları

**Yeni 15.5**:

* Visual Studio, artık çok aşamalı Docker dosyalarını destekleyen ve optimize edilmiş kapsayıcı görüntüleri oluşturmayı kolaylaştıran Docker kapsayıcıları için araçlar içerir.
* Varsayılan olarak Visual Studio, Docker desteği olan bir projeyi açtığınızda gerekli kapsayıcı görüntülerini otomatik olarak çeker, derler ve arka planda çalıştırır. Bunu, Visual Studio'da **Kapsayıcıları arka planda otomatik olarak başlat** ayarı ile devre dışı bırakabilirsiniz.

## <a name="cloud-app-development-with-azure"></a>Azure ile bulut uygulaması geliştirme

### <a name="azure-functions-tools"></a>Azure Fonksiyonları araçları

"Azure geliştirme" iş yükünün bir parçası olarak, önceden derlenmiş C# sınıfı kitaplıkları kullanarak Azure işlevlerini geliştirmenize yardımcı olacak araçlar ekledik. Artık yerel geliştirme makinenizde oluşturabilir, çalıştırabilir ve hata ayıklayabilir ve ardından Visual Studio'dan doğrudan Azure'da yayımlayabilirsiniz.

Daha fazla bilgi için Visual Studio sayfası [için Azure İşlevler araçlarına](/azure/azure-functions/functions-develop-vs) bakın.

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Canlı Azure uygulamalarında anlık noktaları ve günlük noktaları kullanarak uygulamaları ASP.NET hata ayıklama

**15.5'te Yeni**: Snapshot Hata Ayıklayıcı, ilgilendiğiniz kod yürütüldüğünde üretim içi uygulamalarınızın anlık görüntüsünü alır. Hata ayıklayıcıya anlık görüntü almasını söylemek için, kodunuzda anlık noktalar ve günlük noktaları ayarlarsınız. Hata ayıklama, üretim uygulamanızın trafiğini etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Anlık Görüntü Hata Ayıklama, üretim ortamlarında oluşan sorunları çözmek için gereken süreyi önemli ölçüde azaltmanıza yardımcı olabilir.

Anlık görüntü koleksiyonu, Azure Uygulama Hizmeti'nde çalışan aşağıdaki web uygulamaları için kullanılabilir:

* ASP.NET.NET Framework 4.6.1 veya sonraki uygulamalarda çalışır.
* ASP.NET Core uygulamaları .NET Core 2.0 veya daha sonra Windows'da çalışır.

Daha fazla bilgi için, [snappoints ve günlük noktaları kullanarak uygulama ASP.NET Hata Ayıklama'ya](../debugger/debug-live-azure-applications.md)bakın.

## <a name="windows-app-development"></a>Windows uygulaması geliştirme

### <a name="universal-windows-platform"></a>Evrensel Windows Platformu

Evrensel Windows Platformu (UWP), Windows 10 için bir uygulama platformudur. Tüm Windows 10 cihazlarına &ndash; pc, tablet, telefon, Xbox, HoloLens, Surface Hub ve daha fazlasına ulaşmak için tek bir API seti, bir uygulama paketi ve bir mağaza ile UWP uygulamaları geliştirebilirsiniz. UWP, dokunmatik, fare ve klavye, oyun denetleyicisi veya kalem olsun, farklı ekran boyutlarını ve çeşitli etkileşim modellerini destekler. UWP uygulamalarının özünde, kullanıcıların deneyimlerinin TÜM aygıtlarında mobil olmasını istedikleri ve eldeki görev için en uygun veya üretken olan her türlü cihazı kullanmak istedikleri fikri yer almaktır.

![Evrensel Windows Platformu](../cross-platform/media/uwp_coreextensions.png)

Windows 10&mdash;aygıtları için Evrensel Windows Platformu uygulaması&mdash;oluşturmak için C#, Visual Basic, C++veya JavaScript'ten tercih ettiğiniz geliştirme dilini seçin. Visual Studio 2017, tüm cihazlar için tek bir proje oluşturmanıza olanak tanıyan her dil için bir UWP uygulama şablonu sağlar. İşiniz bittiğinde, bir uygulama paketi üretebilir ve uygulamanızı herhangi bir Windows 10 cihazındaki müşterilere sunmak için Visual Studio'nun içinden Microsoft Mağazası'na gönderebilirsiniz.

**Yeni 15.5**: Visual Studio 2017 sürüm 15.5 Windows 10 Fall Creators Update SDK (10.0.16299.0) için en iyi desteği sağlar. Windows 10 Fall Creators Update, UWP geliştiricileri için birçok iyileştirme de getiriyor. En büyük değişikliklerden bazıları şunlardır: 

* **.NET Standard 2.0 desteği**<br/>Windows 10 Fall Creators Update, kolaylaştırılmış uygulama dağıtımına ek olarak, .NET Standard 2.0 desteği sağlayan Windows 10'un ilk sürümüdür. Etkili bir [şekilde,.NET Standardı,](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) herhangi bir .NET platformunun uygulayabileceği taban sınıf kitaplığı bir başvuru uygulamasıdır. .NET Standard'ın amacı, .NET geliştiricilerin insaları üzerinde çalışmayı seçtikleri herhangi bir .NET platformunda kod paylaşmalarını mümkün olduğunca kolaylaştırmaktır.
* **Hem UWP hem de Win32'nin en iyisi**<br/>Şu anda uwp, WPF, Windows Forms veya Xamarin olsun, Windows 10'u tüm .NET geliştiricileri için daha iyi hale getirmek için [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root) ile Windows 10 Platform'u geliştirdik. Visual Studio 2017 sürüm 15.5'teki yeni Uygulama Paketi proje türüyle, UWP projelerinde olduğu gibi WPF veya Windows Forms projeleriniz için Windows Uygulama Paketleri oluşturabilirsiniz. Uygulamanızı paketledikten sonra, tüm Windows 10 uygulama dağıtım avantajlarından yararlanır ve Microsoft Store (tüketici uygulamaları için) veya Microsoft Store for Business and Education üzerinden dağıtım seçeneğine sahip olursunuz. Paket uygulamalar hem tam UWP API yüzeyine hem de masaüstündeki Win32 API'lerine erişebildiklerinden, Artık WPF ve Windows Forms uygulamalarınızı UWP API'leri ve Windows 10 özellikleriyle aşamalı olarak modernize edebilirsiniz. Ayrıca, Win32 bileşenlerinizi tüm Win32 özellikleriyle masaüstünde aydınlatan UWP uygulamalarınıza ekleyebilirsiniz.

UWP hakkında daha fazla bilgi için [Evrensel Windows Platformu (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md) için uygulama geliştir sayfasına bakın.

## <a name="mobile-app-development"></a>Mobil uygulama geliştirme

### <a name="xamarin"></a>Xamarin

".NET" iş yüküyle mobil geliştirmenin bir parçası olarak, C#, .NET ve Visual Studio'ya aşina olan geliştiriciler Xamarin kullanarak yerel Android, iOS ve Windows uygulamaları sunabilir. Geliştiriciler, Objective-C veya Java gibi yerel kodlama dillerini öğrenmek zorunda kalmadan Android, iOS ve Windows&mdash;cihazlarda uzaktan hata ayıklama da dahil olmak üzere mobil uygulamalar için Xamarin ile çalışırken aynı güç ve üretkenliğin keyfini çıkarabilirler.

Daha fazla bilgi için [Visual Studio ve Xamarin sayfasına](/xamarin/) bakın.

### <a name="entitlements-editor"></a>Yetkilendirmeler düzenleyicisi

**15.3'te yeni**: iOS geliştirme ihtiyaçlarınız için tek başına bir Yetkilendirme düzenleyicisi ekledik. Kolayca göz atılabilir bir kullanıcı dostu kullanıcı kullanıcı kullanıcı arası bir kullanıcı aracı içerir. Başlatmak *için, entitlements.plist* dosyanızı çift tıklatın.

![Xamarin için Yetki editörü](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Xamarin için Visual Studio Araçları

**15.4'te yeni**: Xamarin Live, geliştiricilerin uygulamalarını doğrudan iOS ve Android cihazlarda sürekli olarak dağıtmasına, sınamasını ve hata sını ayıklamalarına olanak tanır. App Store'da veya Google&mdash;Play'de&mdash;bulunan Xamarin Live Player'ı indirdikten sonra cihazınızı Visual Studio ile eşleştirebilir ve mobil uygulamalar oluşturma biçiminizde devrim yapabilirsiniz. Bu işlevsellik artık Visual Studio'da yer almaktadır ve **Araçlar** > **Seçenekleri** > **Xamarin** > **Diğer** > Etkinleştir**Xamarin Live Player'a**giderek etkinleştirilebilir.

![Xamarin Live Player çiftinin animasyonu, dağıtım ve canlı düzenleme modları](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Google Android Emülatör desteği

**15.8'de Yeni**: Hyper-V kullandığınızda, artık Hyper-V sanal makineleri, Docker takımlama, HoloLens emülatörü ve daha fazlası gibi Hyper-V'yi temel alan diğer teknolojilerle Google'ın Android Emülatör'ünü yan yana kullanabilirsiniz. (Bu özellik Windows 10 Nisan 2018 Güncelleştirmesi veya daha sonra gerektirir.)

![Hyper-V teknolojileri google Android emülatörü](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Xamarin.Android Designer split-view düzenleyicisi

Ayrıca **yeni 15.8**: Biz Xamarin.Android için tasarımcı deneyimi önemli iyileştirmeler yaptık. Vurgu, mizanpajlarınızı aynı anda oluşturmanıza, düzenlemenize ve önizlemenize olanak tanıyan yeni bölünmüş görünüm düzenleyicisidir.

![Xamarin.Adroid Designer split-view düzenleyicisi](media/android-designer-split-view.png)

Daha fazla bilgi [için emülatör performansı için Donanım hızlandırma](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**15.5'te Yeni**:&mdash;Android, iOS, macOS ve Windows uygulamaları&mdash;için genel olarak kullanılabilen Visual Studio App Center, otomatik yapılar, buluttaki gerçek cihazlarda test etme, beta test cihazlarına ve uygulama mağazalarına dağıtım ve çökme ve analitik verileri aracılığıyla gerçek dünya kullanımının izlenmesi gibi uygulamalarınızın yaşam döngüsünü yönetmek için ihtiyacınız olan her şeye sahiptir. Objective-C, Swift, Java, C#, Xamarin ve React Native ile yazılmış uygulamalar tüm özelliklerde desteklenir.

  ![Visual Studio App Center test ortamı](media/app-center-test-env.png)

Daha fazla bilgi [için, Tanıtım Uygulama Merkezi'ne bakın: Bulut blog gönderisinde uygulamalar oluşturun, test edin, dağıtın ve izleyin.](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/)

## <a name="cross-platform-development"></a>Platformlar arası geliştirme

### <a name="redgate-data-tools"></a> Redgate Veri Araçları

DevOps yeteneklerini SQL Server veritabanı geliştirmeye genişletmek için Redgate Veri Araçları artık Visual Studio'da kullanılabilir.

Visual Studio 2017 Enterprise'a dahil:

* [Redgate ReadyRoll Core,](https://www.red-gate.com/products/sql-development/sql-change-automation/?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) geçiş komut dosyaları geliştirmenize, kaynak denetimini kullanarak veritabanı değişikliklerini yönetmenize ve uygulama değişikliklerinin yanı sıra SQL Server veritabanı değişikliklerinin dağıtımlarını güvenli bir şekilde otomatikleştirmenize yardımcı olur.
* [Redgate SQL Prompt Core,](https://www.red-gate.com/products/sql-development/sql-prompt/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) akıllı kod tamamlama yardımı ile SQL'i daha hızlı ve doğru bir şekilde yazmanıza yardımcı olur. SQL Prompt, veritabanı ve sistem nesnelerinin yanı sıra anahtar sözcükleri de otomatik olarak tamamlar ve yazdığınız sırada sütun önerileri sunar. Her sütun adını veya diğer adını hatırlamak zorunda olmadığınız için daha temiz kod ve daha az hata yla sonuçlanır.

Visual Studio 2017'nin tüm sürümlerine dahil:

* [Redgate SQL Search,](https://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) birden çok veritabanında SQL parçalarını ve nesnelerini hızla bulmanıza yardımcı olarak üretkenliğinizi artırır.

Daha fazla bilgi için [Visual Studio 2017 blog gönderisinde Redgate Veri Araçları'na](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/) bakın.

### <a name="net-core"></a>.NET Core

.NET Core, .NET Standardının genel amacı, modüler, çapraz platform ve açık kaynak uygulamasıdır ve .NET Framework ile aynı API'lerin çoğunu içerir.

.NET Core platformu, yönetilen derleyiciler, çalışma zamanı, taban sınıf kitaplıkları ve ASP.NET Core gibi çok sayıda uygulama modelini içeren çeşitli bileşenlerden oluşur. .NET Core üç ana işletim sistemi destekler: Windows, Linux ve macOS. .NET Core'u aygıt, bulut ve gömülü/IoT senaryolarında kullanabilirsiniz.

Ve şimdi Docker desteğini de içeriyor.

**15.3'te yeni**: Visual Studio 2017 sürüm 15.3 .NET Core 2.0 geliştirmeyi destekler. .NET Core 2.0'ın kullanılması için .NET Core 2.0 SDK'nın ayrı olarak indirilmesi ve yüklenmesi gerekmektedir.

Daha fazla bilgi için [.NET Core kılavuzu](/dotnet/core/index) sayfasına bakın.

## <a name="games-development"></a>Oyun geliştirme

### <a name="visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları

"Birlik için Oyunlar geliştirme" iş yükünün bir parçası olarak, 2D ve 3D oyunlar ve etkileşimli içerik oluşturmak için çapraz platform geliştirmenize yardımcı olacak araçlar ekledik. Visual Studio 2017 ve Unity 5.6'yı kullanarak tüm mobil platformlar, WebGL, Mac, PC ve Linux masaüstü, web veya konsollar dahil olmak üzere 21 platformda bir kez oluşturun ve yayımlayın.

Daha fazla bilgi için [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) sayfasına bakın.

## <a name="ai-development"></a>AI geliştirme

### <a name="visual-studio-tools-for-ai"></a>AI için Visual Studio Araçları

**15.5'te yeni**: Bugün AI inovasyonunu hızlandırmak için Visual Studio'nun üretkenlik özelliklerini kullanın. Sözdizimi vurgulama, IntelliSense ve metin otomatik biçimlendirme gibi yerleşik kod düzenleyici özelliklerini kullanın. Yerel değişkenler ve modeller üzerinde hata ayıklama kullanarak yerel ortamda derin öğrenme uygulamanızı etkileşimli olarak test edebilirsiniz.

  ![Derin Öğrenme IDE](../ai/media/about/ide.png)

Daha fazla bilgi [için, AI](../ai/about-ai-tools.md) için Visual Studio Tools sayfasına bakın.

## <a name="whats-next"></a>Sırada ne var?

Visual Studio 2017'yi geliştirme deneyiminizi daha da iyi hale getirebilecek yeni özelliklerle sık sık güncelliyoruz. Deneysel önizlemede yer alan en önemli güncellemelerimizden bazılarının özetini aşağıda bulabilirsiniz:

* **[Live Share](https://visualstudio.microsoft.com/services/live-share/)**, bir kod tabanını ve içeriğini bir takım arkadaşıyla paylaşmanızı ve doğrudan Visual Studio'dan anlık çift yönlü işbirliği elde etmenizi sağlayan yeni bir araçtır. Live Share ile, bir ekip arkadaşı onlarla paylaştığınız bir projeyi okuyabilir, gezinebilir, düzeltebilir ve hata ayıklayabilir ve sorunsuz ve güvenli bir şekilde yapabilir.<br><br>Daha fazla bilgi için [Canlı Paylaşım SSS'si'ne](/visualstudio/liveshare/faq)bakın.<br><br>
* **[IntelliCode,](https://visualstudio.microsoft.com/services/intellicode/)** daha iyi bağlam farkında kod tamamlamaları sunmak için AI kullanarak yazılım geliştirme geliştirir yeni bir yetenek, kendi ekibinin desen ve stilleri kod geliştiriciler iyönlendirir, zor yakalamak kod sorunları bulmak ve gerçekten önemli alanlarda kod incelemeleri odak. <br><br>Daha fazla bilgi için [IntelliCode SSS](/visualstudio/intellicode/faq)bölümüne bakın.

Visual Studio 2017 için başka neler inanacağını öğrenmek ister misiniz? Visual [Studio Yol Haritası](/visualstudio/productinfo/vs2018-roadmap) sayfasına bakın.

Ve en yeni sürümü, [Visual Studio 2019](whats-new-visual-studio-2019.md)göz atın unutmayın.

## <a name="contact-us"></a>Bizimle iletişim kurun

Visual Studio ekibine neden geri bildirim göndermissin? Çünkü müşteri geri bildirimlerini ciddiye alıyoruz. Yaptığımız şeyin çoğunu kullanıyor.

Visual Studio'yu nasıl geliştirebileceğimiz veya ürün destek seçenekleri hakkında daha fazla bilgi edinebileceğimiz hakkında bir öneride bulunmak istiyorsanız, lütfen [bize geri bildirim gönder](feedback-options.md) sayfasına bakın.

### <a name="report-a-problem"></a>Sorun bildirin

Bazen, bir ileti karşılaştığınız bir sorunun tam etkisini iletmek için yeterli değildir. Bir askı, kilitlenme veya başka bir performans sorunuyla karşılaşırsanız, **Sorun Bildir** aracını kullanarak repro adımlarını ve destekleyici dosyaları (ekran görüntüleri ve izleme ve yığın döküm dosyaları) bizimle kolayca paylaşabilirsiniz. Bu aracın nasıl kullanılacağı hakkında daha fazla bilgi için sorun sayfasını [nasıl bildirin' e](how-to-report-a-problem-with-visual-studio.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017 çıkış notları](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio 2017 SDK’daki Yenilikler](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)
* [Visual C++'da yenilikler](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C'deki yenilikler #](/dotnet/csharp/whats-new)
* [Team Foundation Server için yenilikler](/azure/devops/server/whats-new)
* [Mac için Visual Studio'daki yenilikler](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Visual Studio 2019’daki yenilikler](whats-new-visual-studio-2019.md)
