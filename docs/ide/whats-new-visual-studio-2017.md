---
title: Visual Studio 2017’deki yenilikler
titleSuffix: ''
description: Visual Studio 2017 ' deki yeni özellikler hakkında bilgi edinin.
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 65ee7d1a1252e4906f291ace121f7c92c889f616
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150930"
---
# <a name="whats-new-in-visual-studio-2017"></a>Visual Studio 2017’deki yenilikler

**[15,9 sürümü](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017) için güncelleştirildi**

Visual Studio önceki bir sürümünden yükseltme mi arıyorsunuz? Visual Studio 2017 size şunları sunabilir: herhangi bir geliştirme, uygulama ve platforma yönelik benzersiz üretkenlik. Android, iOS, Windows, Linux, web ve bulut uygulamaları geliştirmek için Visual Studio 2017 kullanın. Hızlı kod yazın, kolayca hata ayıklama ve tanılama yapın, sık sık test edin ve güvenle kullanıma sunun. Ayrıca, kendi uzantılarınızı oluşturarak Visual Studio’yu özelleştirebilir ve kapsamını genişletebilirsiniz. Sürüm denetimi kullanın, çevik olun ve bu sürümle verimli bir şekilde işbirliği yapın!

>[!div class="button"]
>[Visual Studio’yu indirin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

aşağıda, önceki sürümden bu yana yapılan değişikliklerin yüksek düzey bir üst sınırı olan Visual Studio 2015:

* **[Temelleri yeniden tanımlandı](#redefined-fundamentals)**. Yeni bir kurulum deneyimi sayesinde daha hızlı bir şekilde yükleyebilir ve ihtiyacınız olduğunda istediğiniz şeyi yükleyebilirsiniz.
* **[Performans ve üretkenlik](#performance-and-productivity)**. Yeni ve modern mobil, bulut ve masaüstü geliştirme özelliklerine odaklandık. Visual Studio daha hızlı başlar, daha fazla yanıt verir ve öncesinde daha az bellek kullanır.
* **[Azure Ile bulut uygulaması geliştirme](#cloud-app-development-with-azure)**. Yerleşik bir Azure Araçları Paketi, Microsoft Azure tarafından desteklenen bulut öncelikli uygulamaları kolayca oluşturmanıza olanak tanır. Visual Studio Azure 'da uygulamaları ve hizmetleri yapılandırma, derleme, hata ayıklama, paketleme ve dağıtmayı kolaylaştırır.
* **[uygulama geliştirmeyi Windows](#windows-app-development)**. tüm Windows 10 cihazlar &ndash; PC, tablet, telefon, Xbox, HoloLens, Surface Hub ve daha fazlası için tek bir proje oluşturmak üzere Visual Studio 2017 ' deki UWP şablonlarını kullanın.
* **[Mobil uygulama geliştirme](#mobile-app-development)**. Yenilik yapın ve çok platformlu mobil gereksinimlerinizi bir çekirdek kod temeli ve beceriler kümesiyle birleştiren Xamarin ile sonuçları hızlı bir şekilde alın.
* **[Platformlar arası geliştirme](#cross-platform-development)**. Her türlü hedeflenen platforma sorunsuz bir şekilde yazılım sunun. DevOps işlemlerini redgate veri araçları aracılığıyla SQL Server genişletin ve veritabanı dağıtımlarını Visual Studio güvenle otomatikleştirin. veya, Windows, Linux ve macos işletim sistemlerinde değiştirilmemiş olarak çalışan uygulamalar ve kitaplıklar yazmak için .net Core ' u kullanın.
* **[Oyun geliştirme](#games-development)**. Unity için Visual Studio Araçları (vstu) ile, C# dilinde oyun ve düzenleyici betikleri yazmak için Visual Studio kullanabilir ve sonra hataları bulmak ve onarmak için güçlü hata ayıklayıcıyı kullanabilirsiniz.
* **[AI geliştirme](#ai-development)**. aı için Visual Studio Araçları ile, aı yeniliklerini hızlandırmak için Visual Studio üretkenlik özelliklerini kullanabilirsiniz. güçlü deneme özellikleri için Azure Machine Learning ile sorunsuz bir şekilde tümleştirilen derin Learning/aı çözümleri oluşturun, test edin ve dağıtın.

> [!NOTE]
> Visual Studio 2017 ' deki yeni özelliklerin ve işlevlerin tamamı listesi için bkz. [geçerli sürüm notları](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). Ve gelecekteki Özellik tekliflerinden göz atın, bkz. [Önizleme sürüm notları](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

aşağıda Visual Studio 2017 ' deki en önemli iyileştirmeler ve yeni özelliklerden bazıları hakkında daha ayrıntılı bilgiler verilmiştir.

## <a name="redefined-fundamentals"></a>Temelleri yeniden tanımlandı

### <a name="a-new-setup-experience"></a>Yeni bir kurulum deneyimi

Visual Studio, ihtiyacınız olan özelliklerden yalnızca ihtiyacınız olan özellikleri yüklemeyi kolaylaştırır ve daha hızlı hale getirir. Ayrıca, düzgün bir şekilde kaldırılır.

Visual Studio yüklediğinizde dikkat edilecek en önemli değişiklik, yeni kurulum deneyimidir. **Iş yükleri** sekmesinde, ortak çerçeveleri, dilleri ve platformları temsil edecek şekilde gruplanmış yükleme seçeneklerini görürsünüz. .net masaüstü geliştirmeden Windows, Linux ve iOS 'ta C++ uygulama geliştirmeye kadar her şeyi ele alır.

İhtiyacınız olan iş yüklerini seçin ve gerektiğinde değiştirin.

![Visual Studio 2017 kurulum iletişim kutusu](../install/media/install-visual-studio-enterprise.png)

Ve yüklemenizi hassas şekilde ayarlama seçenekleriniz da var:

* İş yüklerini kullanmak yerine kendi bileşenlerinizi seçmek mı istiyorsunuz? Yükleyiciden **ayrı bileşenler** sekmesini seçin.
* dil paketlerini de Windows dil seçeneğini değiştirmek zorunda kalmadan yüklemek istiyor musunuz? Yükleyicinin **dil paketleri** sekmesini seçin.
* **15,7 ' de yeni**: Visual Studio yüklendiği konumun konumunu değiştirmek istiyor musunuz? Yükleyicinin **yükleme seçenekleri** sekmesini seçin.

yeni yükleme deneyimi hakkında daha fazla bilgi edinmek için adım adım yönergeler de dahil olmak üzere, [Visual Studio yükleme](../install/install-visual-studio.md) sayfasına bakın.

### <a name="a-focus-on-accessibility"></a>Erişilebilirlik üzerinde bir odak

**15,3 ' de yeni** bir deyişle, Visual Studio ve birçok müşterinin kullandığı yardımcı teknolojiler arasındaki uyumluluğun geliştirilmesi için 1.700 hedefli düzeltmeler yaptık. Ekran okuyucular, yüksek karşıtlıklı Temalar ve daha önce hiç olmadığı gibi diğer yardımcı teknolojilerle daha uyumlu olan onlarca senaryo vardır. Hata ayıklayıcı, düzenleyici ve kabuğun hepsi de çok önemli iyileştirmeler içerir.

daha fazla bilgi için [Visual Studio 2017 sürüm 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) blog gönderisine yönelik erişilebilirlik geliştirmeleri bölümüne bakın.

## <a name="performance-and-productivity"></a>Performans ve üretkenlik

### <a name="sign-in-across-multiple-accounts"></a>Birden çok hesap arasında oturum açın

kullanıcı hesaplarını Takım Gezgini, Azure araçları, Microsoft Store yayımlama ve daha fazlasını paylaşmanıza olanak tanıyan Visual Studio yeni bir kimlik hizmeti sunuyoruz.

Daha uzun bir süre içinde oturum açabilirsiniz. Visual Studio, her 12 saatte bir oturum açmanızı istemez. daha fazla bilgi edinmek için, daha [az Visual Studio oturum açma komut istemlerini](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/) blog gönderisine bakın.

### <a name="start-visual-studio-faster"></a>daha hızlı Visual Studio başlatın

yeni Visual Studio performans merkezi, ıde başlangıç zamanını iyileştirmenize yardımcı olabilir. Performans Merkezi, IDE başlangıcını yavaşlatabilecek tüm uzantıları ve araç pencerelerini listeler. Bu uygulamayı, uzantıların ne zaman başlatılacağını belirleyerek veya araç pencerelerinin başlangıçta açık olup olmadığını belirleyerek başlangıç performansını geliştirmek için kullanabilirsiniz.

### <a name="faster-on-demand-loading-of-extensions"></a>Uzantılar için daha hızlı yükleme

Visual Studio uzantılarının taşınması (ve üçüncü taraf uzantılarla çalışma), bu sayede ıde başlatması yerine isteğe bağlı olmaları gerekir. Hangi uzantıların ne kadar etkili olduğunu, çözüm yükünü ve yazma performansını merak ediyor musunuz? bu **bilgileri,**  >  **Visual Studio performansını yönetme**' de görebilirsiniz.

  ![Visual Studio 2017 ' de seçenekler iletişim kutusu](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Uzantılarınızı dolaşım uzantıları Yöneticisi ile yönetme

Visual Studio 'de oturum açtığınızda, her geliştirme ortamını en sevdiğiniz uzantılara göre ayarlamak daha kolay olur. Yeni dolaşım uzantısı Yöneticisi, bulutta eşitlenmiş bir liste oluşturarak en sevdiğiniz uzantıların tamamını izler.

Visual Studio içindeki uzantılarınızın listesini görmek için **araçlar**  >  **uzantılar & güncelleştirmeler**' e tıklayın ve ardından **dolaşım uzantı yöneticisi**' ne tıklayın.

![Visual Studio 2017-uzantılar ve güncelleştirmeler iletişim kutusu](media/vs2017ide-extensions-and-updates.png)

Dolaşım uzantısı Yöneticisi yüklediğiniz tüm uzantıları izler, ancak dolaşım listenize hangi olanları eklemek istediğinizi seçebilirsiniz.

![Visual Studio 2017-dolaşım uzantıları yöneticisi](media/vs2017ide-RoamingExtensionManager.png)

Dolaşım uzantısı yöneticisini kullandığınızda, listenizde üç simge türü vardır:

* ![Dolaşıma açıldı simgesi ](media/vs2017ide-roamedicon.png) **_dolaşıma_** açıldı: bu dolaşım listesinin bir parçası olan, ancak makinenizde yüklü olmayan bir uzantı.
  (Bunları, **İndir** düğmesini kullanarak yükleyebilirsiniz.)
* ![Dolaşıma eklenen & yüklenen simge ](media/vs2017ide-roamedinstalledicon.png) **_& yüklendi_**: bu dolaşım listesinin parçası olan ve geliştirme ortamınıza yüklenen tüm uzantılar.
  (Dolaşımda istemediğinize karar verirseniz, bunu **dolaşımı durdur** düğmesini kullanarak kaldırabilirsiniz.)
* ![Yüklü simge ](media/vs2017ide-installedicon.png) **_yüklendi_**: Bu ortamda yüklü olan, ancak dolaşım listenizin bir parçası olmayan tüm uzantılar.
  ( **Dolaşım Başlat** düğmesini kullanarak dolaşım listesine uzantı ekleyebilirsiniz.)

Oturum açtığınız sırada yüklediğiniz herhangi bir uzantı, **& yüklenirken** listenize eklenir. Daha sonra uzantı, dolaşım listenizin bir parçası haline gelir ve bu, size herhangi bir makineden erişmenizi sağlar.

### <a name="experience-live-unit-testing"></a>Canlı birim testi yaşayın

Visual Studio Enterprise 2017 ' de, canlı birim testi, kodlarken düzenleyicide canlı birim test sonuçları ve kod kapsamı sağlar. hem .NET Framework hem de .net Core için C# ve Visual Basic projeleriyle birlikte çalışarak, MSTest, xunit ve nunit 'in üç test çerçevesini destekler.

![Live Unit Testing](media/lut-codewindow.png)

Daha fazla bilgi için bkz. [tanıtma Live Unit Testing](../test/live-unit-testing-intro.md). Visual Studio Enterprise 2017 ' nin her sürümünde eklenen yeni özelliklerin listesi için, bkz. [Live Unit Testing yenilikleri](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>CI/CD işlem hattı ayarlama

#### <a name="automated-testing"></a>Otomatikleştirilmiş test

otomatikleştirilmiş test, DevOps işlem hattının önemli bir parçasıdır. Çözümünüzü çok daha kısa bir Döngülerde tutarlı ve güvenilir bir şekilde test etmenize ve serbest bırakmanıza olanak tanır. CI/CD (sürekli tümleştirme ve sürekli teslim) akışları, işlemi daha verimli hale getirmenize yardımcı olabilir.

Otomatikleştirilmiş testler hakkında daha fazla bilgi için bkz. Otomatikleştirilmiş testler için [CI/CD](/archive/blogs/visualstudioalmrangers/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently) işlem hattı DevOps blog gönderisi.

Ayrıca DevLabs uzantısı için sürekli teslim araçlarındaki [Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) daha fazla bilgi için Commit [with confidence: Commit time code quality](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/) blog gönderisi'ne bakın.

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE geliştirmeleri

#### <a name="multi-caret-editing"></a>Çoklu giriş işareti düzenleme

**15.8'de yenisi:** Bir dosyada aynı anda birden çok konumu düzenlemek artık kolaydır. Bir dosyada birden çok konumda ekleme noktaları ve seçimler oluşturarak başlayabilirsiniz. Ardından, aynı anda iki veya daha fazla yerde aynı düzenlemeyi yapmak için çoklu imtiyazlı düzenleme özelliğini kullanın.

Daha fazla bilgi [için, Metin bul ve değiştir](finding-and-replacing-text.md#multi-caret-selection) sayfasının Çoklu [giriş-giriş-girişlerini](finding-and-replacing-text.md) seçme bölümüne bakın.

#### <a name="keep-keybinding-profiles-consistent"></a>Tuş bağlama profillerini tutarlı tutma

**15.8'de** yeni: Artık iki yeni klavye profiliyle araçlar arasında tuş bağlamalarınızı tutarlı tutabilirsiniz: Visual Studio Code ve ReSharper (Visual Studio). Bu düzenleri Araçlar Seçenekleri **Genel**  >  **Klavye ve** üst açılan menü altında  >    >   bulabilirsiniz.

  ![Visual Studio Code ve ReSharper için yeni tuş bağlama profilleri](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Yeni yeniden düzenleme kullanma

Yeniden düzenleme, kodunuzu yazdıktan sonra geliştirme işlemidir. Yeniden düzenleme, davranışını değiştirmeden kodun iç yapısını değiştirir. Yeni yeniden düzenlemelerini sıklıkla ekleriz; yalnızca birkaçı:

* Parametre ekleme (CallSite'den)
* Geçersiz kılmalar oluşturma
* Adlandırılmış bağımsız değişken ekleme
* Parametreler için null denetimi ekleme
* Değişmez değerlerin içine basamak ayırıcıları ekleme
* Sayısal değişmez değerler için taban değerini değiştirme (örneğin, hex ile ikili)
* Anahtara dönüştürme
* Kullanılmayan değişkeni kaldırma

Daha fazla bilgi için bkz. [Hızlı Eylemler.](common-quick-actions.md)

#### <a name="interact-with-git"></a>Git ile etkileşim kurma

Visual Studio'da bir projeyle çalışırken, kodunuzu hızla ayarlayacak ve bir Git hizmetine yayımlayacak şekilde işebilirsiniz. Git depolarınızı IDE'nin sağ alt köşesindeki menü tıklamalarını kullanarak da yönetebilirsiniz.

![Visual Studio 2017'nin Git iletişim kutusuyla etkileşim kurması](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Geliştirilmiş gezinti denetimlerini deneyimle

A'dan B'ye daha fazla güvenle ve daha az dikkat dağıtarak aya A'dan A'ya alacazmanıza yardımcı olmak için gezinti deneyimini yenileladık.

* **15.4'te** yeni: Tanıma Git **(** Ctrl tıklaması veya +  **F12**) &ndash; Fare **kullanıcıları, Ctrl** tuşuna basarak ve üyeye tıklayarak üyenin tanımına gitmek için daha kolay bir yol sağlar. **Ctrl tuşlarına** basılarak bir kod simgesinin üzerine gelindiğinde, simgenin altı çizili olur ve bir bağlantıya döner. Daha [fazla bilgi için bkz. Tanıma Git ve Tanıma](go-to-and-peek-definition.md) Göz At.

* **Uygulamaya Git** (**Ctrl** + **F12**) Herhangi bir temel tür veya &ndash; üyeden çeşitli uygulamalarına gidin.

* **Hepsi'ne Git** (**Ctrl** + **T** veya **Ctrl** + **,**) doğrudan herhangi bir &ndash; dosyaya/tür/üye/sembol bildirimine gidin. Sonuç listenizi filtrenin veya sorgu söz dizimini kullanabilirsiniz (örneğin, dosyalar için "f searchTerm", türler için "t searchTerm" vb.).

  ![Geliştirilmiş Tüm Git](media/vs2017ide-navigation-go-to.png)

* **Tüm Başvuruları Bul** (**Shift** F12 ) Söz dizimi renklendirmesi ile Tüm Başvuruları Bul sonuçlarını proje, tanım ve yol birleşimiyle +  &ndash; gruplandırebilirsiniz. Ayrıca, özgün sonuçlarınızı kaybetmeden diğer başvuruları bulmaya devam etmek için sonuçları "kilitler"siniz.

  ![Yeni Tüm Başvuruları Bul aracı](media/vs2017ide-find-all-references.png)

* **Yapı Görselleştirici** &ndash; Noktalı, gri dikey çizgiler (girinti kılavuzları), görünüm çerçeveniz içinde bağlam sağlamak için kodda yer işaretleri olarak davranır. Bunları popüler Productivity Power Tools'tan tanıyabilirsiniz. Herhangi bir zamanda kaydırmaya gerek kalmadan hangi kod bloğunda olduğunu görselleştirin ve keşfedin. Satırların üzerine gelindiğinde, bu bloğun ve onun ebeveynlerinin açılmasını gösteren bir araç ipucu görüntülenir. TextMate dil bilgisi aracılığıyla desteklenen tüm dillerin yanı sıra C#, Visual Basic ve XAML ile kullanılabilir.

  ![Visual Studio 2017 yapı görselleştiricisi](media/vsIDE-StructureVisualizer.png)

Yeni üretkenlik özellikleri hakkında daha fazla bilgi için [Visual Studio 2017: Üretkenlik,](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/) Performans ve İş Ortakları blog gönderisi'ne bakın.

### <a name="visual-c"></a>Visual C++

Visual Studio'de C++ Temel Yönergeleri'yi Visual Studio ile dağıtma, C++11 ve C++ özellikleri için gelişmiş destek ekleyerek derleyiciyi güncelleştirme ve C++ kitaplıklarında işlevsellik ekleme ve güncelleştirme gibi çeşitli geliştirmeler görüyorsunuz. Ayrıca C++ IDE'nin, yükleme iş yüklerinin ve daha fazlasının performansını da iyileştirildi.

Ayrıca, derleyicide ve araçlarda 250'den fazla hata ve bildirilen sorun düzeltilmiştir ve çoğu C++ için Geliştirici Community [müşteriler tarafından gönderilmiştir.](https://aka.ms/feedback/report?space=62 "C++ Community geliştirici hesabı")

Tüm ayrıntılar için [Visual 2017'de Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) için yeniler sayfasına bakın.

### <a name="debugging-and-diagnostics"></a>Hata ayıklama ve tanılama

#### <a name="run-to-click"></a>Tıklanan Satıra Kadar Çalıştır

Artık istediğiniz satırda durdurmak için kesme noktası ayarlamadan hata ayıklama sırasında daha kolay bir şekilde atlayabilirsiniz. Hata ayıklayıcıda durdurulurken, kod satırı yanında görünen simgeye tıklamak gerekir. Kodunuz, kod yolunuzda bir sonraki isabeti üzerine çalıştıracak ve bu satırda duracak.

![Visual Studio 2017 hata ayıklama - Tıklamak için Çalıştır](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Yeni Özel Durum Yardımcı

Yeni Özel Durum Yardımcı, özel durum bilgilerini bir bakışta görüntülemenize yardımcı olur. Bilgiler, iç özel durumlara anında erişimle birlikte sıkıştırılmış bir şekilde sunulmaktadır. NullReferenceException tanılarken, Özel Durum Yardımcı'nın içinde null değerinin ne olduğunu hızlı bir şekilde öğrenilir.

![Visual Studio'daki Yeni Özel Durum Visual Studio](media/vs2017ide-ExceptionHelper.png)

Daha fazla bilgi için [bkz. Yeni Özel Durum Yardımcı'sı kullanma Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) blog gönderisi.

#### <a name="snapshots-and-intellitrace-step-back"></a>Anlık görüntüler ve IntelliTrace geri adımı

**15.5'te** yeni: IntelliTrace geri adım geri adımı, her kesme noktası ve hata ayıklayıcı adımı olayında otomatik olarak uygulamanın anlık görüntüsünü alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenizin yanı sıra uygulamanın geçmişte olduğu gibi durumunu görüntülemeye olanak sağlar. IntelliTrace geri adımı önceki uygulama durumunu görmek istediğiniz ancak hata ayıklamayı yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemeyebilirsiniz.

Hata Ayıklama araç çubuğundaki Geri Adım ve İleri **Adım** düğmelerini **kullanarak** anlık görüntülerde gezinebilirsiniz ve **görüntüleyebilirsiniz.** Bu düğmeler, Tanılama Araçları penceresindeki  Olaylar **sekmesinde görünen Tanılama Araçları** gezinebilirsiniz. Bir olayda geri veya ileri adımlama, seçili olayda geçmiş hata ayıklamayı otomatik olarak etkinleştirir.

![Visual Studio'de IntelliTrace geri adım Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "Geri ve İleri Adım düğmeleri")

Daha fazla bilgi için [IntelliTrace kullanarak anlık görüntüleri görüntüleme geri adım sayfasına](../debugger/view-historical-application-state.md) bakın.

### <a name="containerization"></a>Kapsayıcıyla taşıma

Kapsayıcılar size daha fazla uygulama yoğunluğu ve daha düşük dağıtım maliyeti, gelişmiş üretkenlik ve DevOps sağlar.

#### <a name="docker-container-tooling"></a>Docker Kapsayıcısı Araçları

**15.5'te yeni:**

* Visual Studio, artık çok aşamalı Dockerfile'ları destekleyen ve iyileştirilmiş kapsayıcı görüntüleri oluşturmayı kolaylaştıran Docker kapsayıcıları için araçlar içerir.
* Varsayılan olarak Visual Studio, Docker desteği olan bir projeyi açtığınızda gerekli kapsayıcı görüntülerini otomatik olarak çeker, derler ve arka planda çalıştırır. Bunu, Visual Studio'da **Kapsayıcıları arka planda otomatik olarak başlat** ayarı ile devre dışı bırakabilirsiniz.

## <a name="cloud-app-development-with-azure"></a>Azure ile bulut uygulaması geliştirme

### <a name="azure-functions-tools"></a>Azure İşlevleri araçları

"Azure geliştirme" iş yükünün bir parçası olarak, önceden derlenmiş C# sınıf kitaplıklarını kullanarak Azure işlevleri geliştirmeye yardımcı olacak araçlar ekledik. Artık yerel geliştirme makineniz üzerinde derleme, çalıştırma ve hata ayıklama ve ardından doğrudan yerel makineden Azure'da Visual Studio.

Daha fazla bilgi için Azure İşlevleri [için Visual Studio](/azure/azure-functions/functions-develop-vs) bakın.

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Canlı Azure uygulamalarında ASP.NET noktaları ve logpoint'leri kullanarak canlı uygulamalarda hata ayıklama

**15.5'te** yeni: Snapshot Debugger, ilgilendiğiniz kod yürütülürken üretim uygulamalarınıza anlık görüntü alır. Hata ayıklayıcıya anlık görüntü alma talimatı almak için kodunda anlık görüntü noktaları ve günlük noktaları ayarlayın. Hata ayıklayıcısı, üretim uygulama trafiğinizi etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

Anlık görüntü koleksiyonu, aşağıdaki web uygulamaları için Azure App Service:

* ASP.NET 4.6.1 veya .NET Framework üzerinde çalışan uygulamalar.
* ASP.NET Core .NET Core 2.0 veya sonraki bir üzerinde çalışan uygulamaları Windows.

Daha fazla bilgi için bkz. Anlık ASP.NET ve günlük noktaları kullanarak canlı [uygulamalarda hata ayıklama.](../debugger/debug-live-azure-applications.md)

## <a name="windows-app-development"></a>Windows uygulaması geliştirme

### <a name="universal-windows-platform"></a>Evrensel Windows Platformu

Universal Windows Platformu (UWP), Windows 10. Pc, tablet, telefon, Xbox, HoloLens, Surface Hub ve daha fazlası için tüm Windows 10 cihazlarına ulaşmak için yalnızca bir API kümesi, bir uygulama paketi ve bir mağaza ile UWP için &ndash; uygulamalar geliştirebilirsiniz. UWP dokunmatik, fare ve klavye, oyun denetleyicisi veya kalem gibi farklı ekran boyutlarını ve çeşitli etkileşim modellerini destekler. UWP uygulamalarının özünde, kullanıcıların deneyimlerinin TÜM cihazlarında mobil olarak hareket etmek ve sahip olduğu görev için en kullanışlı veya üretken olan cihazı kullanmak istemeleri fikridir.

![Evrensel Windows Platformu](../cross-platform/media/uwp_coreextensions.png)

C#, Visual Basic, C++ veya JavaScript'te tercih ettiğiniz geliştirme dilini seçen bir Evrensel &mdash; Windows Platform uygulaması Windows 10 &mdash; oluşturun. Visual Studio 2017,tüm cihazlar için tek bir proje oluşturmanıza olanak sağlayan her dil için bir UWP uygulama şablonu sağlar. Çalışmanız tamamlandığında bir uygulama paketi üretebilir ve herhangi bir Microsoft Store cihazdan Visual Studio müşterilerinize sunmak için uygulama paketini Windows 10 gönderebilirsiniz.

**15.5 sürümündeki** yeni sürüm: Visual Studio 2017 sürüm 15.5, Windows 10 Fall Creators Update SDK (10.0.16299.0) için en iyi desteği sağlar. Bu Windows 10 Fall Creators Update, UWP geliştiricileri için birçok geliştirme de sunar. En büyük değişikliklerden bazıları: 

* **.NET Standard 2.0 desteği**<br/>Kolaylaştırılmış uygulama dağıtımına ek olarak Windows 10 Fall Creators Update, Windows 10 2.0 desteği .NET Standard ilk sürümü. Bu, [.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) herhangi bir .NET platformunun uygulaya bir temel sınıf kitaplığı başvuru uygulamasıdır. Bu .NET Standard, .NET geliştiricilerinin üzerinde çalışmak için seçtileri herhangi bir .NET platformunda kod paylaşmalarını mümkün olduğunca kolay hale getirin.
* **Hem UWP hem de Win32'nin en iyisi**<br/>Windows 10 Platformunu tüm .NET Masaüstü Köprüsü [](/windows/uwp/porting/desktop-to-uwp-root) için daha iyi hale Windows 10 için (mevcut odakları UWP, WPF, Windows Forms veya Xamarin) olacak şekilde Windows 10 Platformunu iyileştirdik. Visual Studio 2017 sürüm 15.5'te yeni Uygulama Paketleme proje türüyle, UWP projelerinde olduğu gibi WPF veya Windows Forms projeleriniz için Windows Uygulama Paketleri oluşturabilirsiniz. Uygulamanızı paketledikten sonra tüm Windows 10 avantajlarını elde edin ve Microsoft Store (tüketici uygulamaları için) veya İş İçin Microsoft Store ve Education aracılığıyla dağıtma seçeneğiniz vardır. Paketlenmiş uygulamaların masaüstünde hem tam UWP API yüzeyine hem de Win32 API'lerine erişimi olduğundan, artık WPF ve Windows Forms uygulamalarınızı UWP API'leri ve Windows 10 özellikleriyle kademeli olarak modernleştirebilirsiniz. Ayrıca, win32 bileşenlerinizi tüm Win32 özellikleriyle masaüstünde ışık alan UWP uygulamalarınıza dahil edin.

UWP hakkında daha fazla bilgi için Evrensel Windows [Platformu (UWP) için uygulama geliştirme sayfasına](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md) bakın.

## <a name="mobile-app-development"></a>Mobil uygulama geliştirme

### <a name="xamarin"></a>Xamarin

".NET ile mobil geliştirme" iş yükünün bir parçası olarak, C#, .NET ve Visual Studio tanımayan geliştiriciler Xamarin kullanarak yerel Android, iOS ve Windows uygulamaları teslim ediyor. Geliştiriciler, Objective-C veya Java gibi yerel kodlama dillerini öğrenmek zorunda kalmadan Android, iOS ve Windows cihazlarda uzaktan hata ayıklama da dahil olmak üzere mobil uygulamalar için Xamarin ile çalışırken aynı gücü ve üretkenliği &mdash; kullanabilir.

Daha fazla bilgi için Visual Studio [Xamarin sayfasına](/xamarin/) bakın.

### <a name="entitlements-editor"></a>Yetkilendirmeler düzenleyicisi

**15.3'te** yeni eklendi: iOS geliştirme ihtiyaçlarınız için tek başına Yetkilendirmeler düzenleyicisi ekledik. Kolayca göz atabilirsiniz kullanıcı dostu bir kullanıcı arabirimi içerir. Başlatmak için *entitlements.plist dosyanıza çift* tıklayın.

![Xamarin için yetkilendirme düzenleyicisi](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Xamarin için Visual Studio Araçları

**15.4'te** yeni sürümü: Xamarin Live, geliştiricilerin uygulamalarını doğrudan iOS ve Android cihazlarında sürekli olarak dağıtmasına, test sınamasına ve hata ayıklamasına olanak tanır. App Store veya Xamarin Live Player'Google Play indirdikten sonra cihazınızı Visual Studio ile eşleştirebilirsiniz ve mobil uygulama oluşturma yolunda &mdash; &mdash; devrimler atabilirsiniz. Bu işlevsellik artık Visual Studio’ya eklenmiştir ve **Araçlar** > **Seçenekler** > **Xamarin** > **Diğer** > **Xamarin Live Player’ı Etkinleştir** seçeneği kullanılarak etkinleştirilebilir.

![Xamarin Live Player, dağıtım ve canlı düzenleme modlarının animasyonu](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Google Android Emulator desteği

**15.8'de** yeni sürümü: Hyper-V'nin yeni sürümü: Artık Hyper-V sanal makineleri, Docker aracı, HoloLens öykünücüsü ve daha fazlasını temel alan diğer teknolojilerle Google Android Emulator'ı yan yana kullanabilirsiniz. (Bu özellik nisan 2018 Windows 10 veya sonraki bir güncelleştirmeyi gerektirir.)

![Hyper-V teknolojilerine google Android öykünücüsü](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Xamarin.Android Designer bölünmüş görünüm düzenleyicisi

**Ayrıca 15.8'deki** yeni sürümü: Xamarin.Android için tasarımcı deneyiminde önemli geliştirmeler yaptık. Vurgulama, aynı anda düzenlerinizi oluşturmanıza, düzenlemenize ve önizlemenize olanak sağlayan yeni bölünmüş görünüm düzenleyicisidir.

![Xamarin.Adroid Designer bölünmüş görünüm düzenleyicisi](media/android-designer-split-view.png)

Daha fazla bilgi için [bkz. Öykünücü performansı için donanım hızlandırma](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**15.5** sürümündeki yeni sürüm: Android, iOS, macOS ve Windows uygulamaları için genel kullanıma sunulmuş olan Visual Studio App Center; otomatik derlemeler, buluttaki gerçek cihazlarda test etme, beta test aracılarına ve uygulama mağazalarına dağıtım, kilitlenme ve analiz verileri aracılığıyla gerçek dünya kullanımını izleme dahil olmak üzere uygulama yaşam döngüsünü yönetmek için ihtiyacınız olan her şeye &mdash; &mdash; sahiptir. Objective-C, Swift, Java, C#, Xamarin ve React Native yazılan uygulamalar tüm özelliklerde de kullanılabilir.

  ![Visual Studio App Center test ortamı](media/app-center-test-env.png)

Daha fazla bilgi için [Bkz. App Center: Bulutta uygulama derleme, test,](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) dağıtma ve izleme blog gönderisi.

## <a name="cross-platform-development"></a>Platformlar arası geliştirme

### <a name="redgate-data-tools"></a> Redgate Veri Araçları

Redgate DevOps özelliklerini veritabanı SQL Server için genişletmek için, Redgate Veri Araçları artık Visual Studio.

Visual Studio 2017'ye Enterprise:

* [Redgate ReadyRoll Core,](https://www.red-gate.com/products/sql-development/sql-change-automation/?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) geçiş betikleri geliştirmenize, kaynak denetimi kullanarak veritabanı değişikliklerini yönetmenize ve uygulama değişiklikleriyle birlikte veritabanı SQL Server dağıtımlarını güvenli bir şekilde otomatikleştirmenize yardımcı olur.
* [Redgate SQL Prompt Core,](https://www.red-gate.com/products/sql-development/sql-prompt/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) akıllı kod SQL daha hızlı ve doğru bir şekilde yazmanıza yardımcı olur. SQL Prompt, veritabanı ve sistem nesnelerinin yanı sıra anahtar sözcükleri de otomatik olarak tamamlar ve yazdığınız sırada sütun önerileri sunar. Bunun sonucunda daha temiz kodlar ve daha az hatayla sonuçlandı çünkü her sütun adını veya diğer adını hatırlamaya gerek yok.

Visual Studio 2017'nin tüm sürümlerine dahildir:

* [Redgate SQL Search,](https://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) birden çok veritabanındaki parçaları ve nesneleri hızla bu SQL yardımcı olarak üretkenliğinizi artırır.

Daha fazla bilgi edinmek için bkz. [Visual Studio 2017](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/) blog gönderisinde Redgate Veri Araçları.

### <a name="net-core"></a>.NET Core

.NET Core, uygulamanın genel amaçlı, modüler, platformlar arası ve açık .NET Standard uygulamasıdır ve uygulamayla aynı API'leri .NET Framework.

.NET Core platformu yönetilen derleyiciler, çalışma zamanı, temel sınıf kitaplıkları ve yönetilen derleyiciler gibi çok sayıda uygulama modeli gibi çeşitli bileşenlerden ASP.NET Core. .NET Core üç ana işletim sistemini destekler: Windows, Linux ve macOS. Cihaz, bulut ve katıştırılmış/IoT senaryolarında .NET Core kullanabilirsiniz.

Artık Docker desteği de buna dahildir.

**15.3 sürümündeki** yeni sürüm: Visual Studio 2017 sürüm 15.3, .NET Core 2.0 geliştirmesini destekler. .NET Core 2.0'ın kullanımı için .NET Core 2.0 SDK'sı ayrı ayrı indirilir ve yüklenebilir.

Daha fazla bilgi için [.NET Core kılavuz sayfasına](/dotnet/core/index) bakın.

## <a name="games-development"></a>Oyun geliştirme

### <a name="visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları

"Unity için oyun geliştirme" iş yükünün bir parçası olarak, 2D ve 3D oyunlar ve etkileşimli içerik oluşturmak üzere platformlar arası geliştirmenizi yardımcı olacak araçlar dahil edildi. bir kez oluşturun ve Visual Studio 2017 ve Unity 5.6 kullanarak tüm mobil platformlar, WebGL, Mac, PC ve Linux masaüstü, web veya konsollar dahil olmak üzere 21 platformda yayımlayın.

Daha fazla bilgi için Unity için Visual Studio Araçları [bakın.](/gamedev/unity/get-started/visual-studio-tools-for-unity.md)

## <a name="ai-development"></a>AI geliştirme

### <a name="visual-studio-tools-for-ai"></a>AI için Visual Studio Araçları

**15.5'te yeni** özellikler: Günümüzün Visual Studio yeniliklerini hızlandırmak için bu özelliklerin üretkenlik özelliklerini kullanın. Söz dizimi vurgulama, IntelliSense ve metin otomatik biçimlendirme gibi yerleşik kod düzenleyicisi özelliklerini kullanın. Yerel değişkenler ve modellerde adım adım hata ayıklamayı kullanarak derin öğrenme uygulamanızı yerel ortamınıza etkileşimli olarak test edin.

  ![Derin Learning IDE](../ai/media/about/ide.png)

Daha fazla bilgi için Visual Studio Araçları [sayfasına](../ai/about-ai-tools.md) bakın.

## <a name="whats-next"></a>Sırada ne var?

2017'Visual Studio geliştirme deneyiminizi daha da iyi hale Visual Studio yeni özelliklerle güncelleştirin. Deneysel önizleme aşamasındaki en önemli güncelleştirmelerimizin bir özeti aşağıdadır:

* **[Live Share,](https://visualstudio.microsoft.com/services/live-share/)** bir kod tabanını ve bağlamını bir ekip arkadaşı ile paylaşmaya ve doğrudan iş arkadaşlarınızdan anında çift yönlü işbirliği elde etmenizi sağlayan yeni Visual Studio. Ekip Live Share ekip arkadaşlarınız, kendileriyle paylaştığım bir projeyi okuyabilir, gezin, düzenleyebilir ve hata ayıklar ve bunu sorunsuz ve güvenli bir şekilde yapar.<br><br>Daha fazla bilgi için bkz. [SSS Live Share bakın.](/visualstudio/liveshare/faq)<br><br>
* Daha iyi bağlam kullanan kod tamamlamaları sunmak için yazılım geliştirmeyi geliştiren yeni bir özellik olan **[IntelliCode,](https://visualstudio.microsoft.com/services/intellicode/)** geliştiricilere ekiplerinin desenlerini ve stillerini kodlama, kod sorunlarını yakalama zorluğu bulma ve gerçekten önemli alanlara kod incelemelerine odaklanmaya yardımcı olur. <br><br>Daha fazla bilgi için bkz. [IntelliCode SSS](/visualstudio/intellicode/faq).

2017'de çalışmalarda başka nelerin Visual Studio ister misiniz? Yol [haritası Visual Studio bakın.](/visualstudio/productinfo/vs2018-roadmap)

En yeni sürüm olan [2019'a Visual Studio unutmayın.](whats-new-visual-studio-2019.md)

## <a name="contact-us"></a>Bizimle iletişim kurun

Neden Visual Studio ekibine geri bildirim gönderebilirsiniz? Çünkü müşteri geri bildirimlerini ciddiye alıyoruz. Bu, yapacaklarının büyük bir fazlasını yapar.

Ürün destek seçeneklerini nasıl geliştirebilirsiniz konusunda bir öneride Visual Studio veya ürün desteği seçenekleri hakkında daha fazla bilgi edinmek için lütfen Bize geri bildirim gönderin [sayfasına](feedback-options.md) bakın.

### <a name="report-a-problem"></a>Sorun bildirin

Bazen, karşılaştığınız bir sorunun tam etkisini iletmek için bir ileti yeterli olmaz. Visual Studio yanıt vermesine, kilitlenmesine veya başka bir performans sorunuyla karşımıza çıkarılırsa, Sorun Bildir aracını kullanarak yeniden verme adımlarını ve destek dosyalarını (ekran görüntüleri ve izleme ve yığın döküm dosyaları gibi) bizimle kolayca **paylaşabilirsiniz.** Bu aracın kullanımı hakkında daha fazla bilgi için Sorun [bildirme sayfasına](how-to-report-a-problem-with-visual-studio.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017 sürüm notları](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio 2017 SDK’daki Yenilikler](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)
* [Visual C++'daki Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C# yenilikleri](/dotnet/csharp/whats-new)
* [Team Foundation Server'nin Team Foundation Server](/azure/devops/server/whats-new)
* [Mac için Visual Studio'daki Mac için Visual Studio](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Visual Studio 2019'daki yeniler](whats-new-visual-studio-2019.md)
