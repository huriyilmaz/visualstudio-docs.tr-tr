---
title: Visual Studio 2019’daki yenilikler
titleSuffix: ''
description: Visual Studio 2019'daki yeni özellikler hakkında bilgi.
ms.date: 08/10/2021
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: aaa3ad227fcd42295db0835cad637862df850df9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078108"
---
# <a name="whats-new-in-visual-studio-2019"></a>Visual Studio 2019’daki yenilikler

**16.11 sürümü için güncelleştirildi.** Tüm [sürüm notlarına bakın |](/visualstudio/releases/2019/release-notes/) Ürün [yol haritasını görüntüleme](/visualstudio/productinfo/vs2019-roadmap)

>[!div class="button"]
>[Visual Studio 2019’u İndirin](https://visualstudio.microsoft.com/downloads/)

2019'Visual Studio tüm geliştirici, uygulama ve platformlar için sınıfının en iyisi araçlara ve hizmetlere sahip oluruz. İster ilk kez Visual Studio ister yıllardır kullanıyor olun, geçerli sürümde olduğu gibi birçok şey vardır!

İşte yeni ve her şey ile ilgili üst düzey bir özet:

* **[Geliştirme:](#develop)** Gelişmiş performans, anında kod temizleme ve daha iyi arama sonuçları ile odaklanmış ve üretken kalın.
* **[İşbirliği](#collaborate)** yapma: Git'in ilk iş akışı, gerçek zamanlı düzenleme ve hata ayıklama ve kod incelemeleri aracılığıyla doğal işbirliğinin Visual Studio.
* **[Hata ayıklama:](#debug)** Belirli değerleri vurgulayın ve bu değerlere gidin, bellek kullanımını iyileştirin ve uygulama yürütmenizin otomatik anlık görüntülerini alın.

Bu sürümde yeni olan her şeyin tam listesi için sürüm [notlarına bakın.](/visualstudio/releases/2019/release-notes/) 16.11 sürümüyle ilgili yeni bilgiler için bkz. [Visual Studio 2019 v16.11](https://devblogs.microsoft.com/visualstudio/visual-studio-16-11/) artık blog gönderisi.

## <a name="develop"></a>Geliştirme

Yeni özelliklerle nasıl zaman tasarrufu yapabilirsiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu izleyin. <br><br>*Video uzunluğu: 3,00 dakika*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Geliştirilmiş arama

Eski adıyla Hızlı Başlat, yeni arama deneyimimiz daha hızlı ve daha etkili. Artık siz yazıldığında arama sonuçları dinamik olarak görüntülenir. Ayrıca, arama sonuçları genellikle komutların klavye kısayollarını içerebilir, böylece bunları daha sonra kullanmak üzere ezberlersiniz.

   ![Visual Studio 2019'daki yeni arama deneyiminin animasyonu](media/vs-2019/new-search-feature.gif "Visual Studio 2019'daki yeni arama deneyimi.")

Yeni belirsiz arama mantığı, yazım hatasına bakılmaksızın ihtiyacınız olan her şeyi bulur. Bu nedenle komutlar, ayarlar, belgeler veya diğer yararlı şeyleri arıyor olun, yeni arama özelliği arayabilirsiniz.

Daha fazla bilgi için [bkz. Arama Visual Studio kullanma.](visual-studio-search.md)

#### <a name="intelligent-search-service"></a>Akıllı arama hizmeti

**16.9'daki** yeniler: Bulut destekli teknoloji, yapay zeka ve makine öğrenmesi kullanarak arama sonuçlarımızı iyileştirildik. Artık yalnızca daha ilgili sonuçlar Visual Studio arama değil, aynı zamanda ürün özelliklerini daha kolay bir şekilde keşfetmenize de yardımcı olabilir.

Daha fazla bilgi için Intelligent [Visual Studio arama hizmeti](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) blog gönderisi'ne bakın.

### <a name="refactorings"></a>Yeniden düzenlemeler

C# içinde kodunuzu düzenlemeyi kolaylaştıran çok sayıda yeni ve son derece kullanışlı yeniden düzenleme vardır. Bunlar ampulde öneri olarak görünür ve üyeleri arabirime veya temel sınıfa taşıma, ad alanlarını klasör yapısıyla eş olacak şekilde ayarlama, foreach döngülerini Linq sorgularına dönüştürme gibi eylemleri içerir.

   ![Visual Studio 2019'da yeniden düzenleme deneyiminin animasyonu](media/vs-2019/refactorings.gif "Visual Studio 2019'da yeniden düzenleme deneyimi.")

Ctrl+ tuşlarına basarak yeniden **düzenlemelerini çağırmanız gerekir.** ve yapmak istediğiniz eylemi seçin.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode,](/visualstudio/intellicode/) yapay zeka (AI) kullanarak yazılım geliştirme çalışmalarınızı geliştirmektedir. IntelliCode, her biri 100'den fazla yıldıza sahip olan GitHub 2.000 açık kaynak proje üzerinde eğitimler ve &mdash; &mdash; önerilerde bulunmalıdır.

![Visual Studio 2019'da IntelliCode animasyonu](media/vs-2019/IntelliCode.gif "Visual Studio 2019'da IntelliCode.")

IntelliCode'a Visual Studio yardımcı olmak için birkaç yol:

* Bağlama göre kod tamamlamaları teslimi
* Geliştiricilere ekiplerinin desenlerine ve stillerine uymaları için yol
* Yakalanması zor kod sorunlarını bulma
* Dikkati gerçekten önemli alanlara çekerek kod incelemelerini odakla

Başlangıçta IntelliCode'ın önizlemesini yalnızca C# için uzantı olarak ilk kez Visual Studio. **16.1'de** yeni olan C# ve XAML "in-the-box" desteği ekledik. (C++ ve TypeScript/JavaScript desteği hala önizlemededir.)

Ayrıca C# kullanıyorsanız kendi kodunuz üzerinde özel model eğitebilme özelliği ekledik.

IntelliCode hakkında daha fazla bilgi için IntelliCode'un genel kullanılabilirliği hakkında daha fazla bilgi için [Bkz. IntelliCode'un](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) genel kullanılabilirliğinin yanı sıra bir göz atma ve Daha fazla kodla daha fazla [bilgi Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) blog gönderileri.

### <a name="code-cleanup"></a>Kod temizleme

Yeni bir belge durumu göstergesiyle eşleştirilmiş yeni bir kod temizleme komutudur. Bu yeni komutu kullanarak hem uyarıları hem de önerileri tek bir eylemle tanımlayabilir ve düzeltebilirsiniz (veya bir düğmeye tıklayabilirsiniz).

Temizleme işlemi kodu biçimlendirecek ve geçerli ayarlar ve .editorconfig dosyaları tarafından önerilen [kod](code-styles-and-code-cleanup.md) [düzeltmelerini uygulayacak.](create-portable-custom-editor-options.md)

   ![Visual Studio 2019'da yeni kod temizleme denetimi ekran görüntüsü](media/vs-2019/code-cleanup-profile.png "Visual Studio 2019'daki yeni kod temizleme denetimi.")

Ayrıca, düzeltici koleksiyonlarını profil olarak kaydedebilirsiniz. Örneğin, kod sırasında sık sık uygulayan küçük bir hedefli düzeltici kümeniz varsa ve bir kod incelemeden önce uygulayacak başka kapsamlı çözümciler kümeniz varsa, profilleri bu farklı görevleri ele alan şekilde yapılandırabilirsiniz.

   ![Visual Studio 2019'da kod temizlemeyi yapılandırma denetimi ekran görüntüsü](media/vs-2019/code-cleanup-profile-configure.png "Visual Studio 2019'da kod temizleme denetimi yapılandırma.")

### <a name="per-monitor-aware-pma-rendering"></a>Monitör başına farkında (PMA) işleme

Farklı ekran ölçek faktörleriyle yapılandırılmış monitörler kullanıyorsanız veya ana cihazınızın farklı görüntü ölçek faktörlerine sahip bir makineye uzaktan bağlanıyorsanız, Visual Studio bulanık göründüğünü veya yanlış ölçekte işleniyor olduğunu fark edebilirsiniz.

Visual Studio 2019'un sürümüyle, izleyici başına Visual Studio (PMA) uygulaması yapıyoruz. Artık Visual Studio ölçek faktörlerine bakılmaksızın doğru şekilde işleniyor.

   ![Visual Studio 2019'da monitör başına (PMA) işleme](media/vs-2019/pma-dpi-scaling.png "2019'da monitör başına Visual Studio (PMA) işleme.")

Daha fazla bilgi için Visual Studio [2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) blog gönderisi ile daha iyi çoklu izleme deneyimine bakın.

### <a name="test-explorer"></a>Test Gezgini

**16.2'de** yeni sürümü: Test Gezgini'ni, büyük test kümelerinin daha iyi işlenmesini, daha kolay filtrelemeyi, daha fazla keşfedilebilir komutları, sekmeli oynatma listesi görünümlerini ve hangi test bilgisinin görüntülendiğinde hassas ayarlamalar yapmak için özelleştirilebilir sütunlar sağlayacak şekilde güncelleştirildi.

   ![Test Gezgini'nde kullanıcı arabirimi geliştirmelerini gösteren ekran görüntüsü](media/vs-2019/test-explorer-ui.png "Test Gezgini'nde kullanıcı arabirimi geliştirmeleri.")

### <a name="net-core"></a>.NET Core

**16.3'te yeni:**.NET Core 3.0 desteği dahil edildi. Platformlar arası, açık kaynak &mdash; ve Microsoft tarafından tam olarak desteklenen.

Daha fazla bilgi için [.NET Core 3.0'ın announcing blog gönderisi'ne](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) bakın.

## <a name="collaborate"></a>İşbirliği

Sorunları çözmek için ekipte nasıl bir ekip olduğunu öğrenmek için aşağıdaki videoyu izleyin. <br><br>*Video uzunluğu: 4,22 dakika*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Git-first iş akışı

2019'da Visual Studio yeni başlangıç penceresi olduğunu fark edeceksiniz.

   ![Visual Studio 2019'da yeni başlangıç penceresinin ekran görüntüsü](media/vs-2019/start-window-dark.png "Visual Studio 2019'daki yeni başlangıç penceresi.")

Başlangıç penceresi, hızlı bir şekilde koda başlamaya yardımcı olacak çeşitli seçenekler sunar. Öncelikle bir repodan kod kopyalama veya denetleme seçeneğini kullandık.

   ![Visual Studio 2019'da 'Git-first' deneyiminin animasyonu](media/vs-2019/git-first.gif "Visual Studio 2019'daki 'Git-first' deneyimi.")

Başlangıç penceresi ayrıca bir proje veya çözüm açma, yerel klasör açma veya yeni proje oluşturma seçeneklerini de içerir.

Daha fazla bilgi için [Koda al: Yeni kodu nasıl tasarladık? Visual Studio penceresi blog gönderisi.](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/)

### <a name="git-productivity"></a>Git üretkenliği

**16.8 sürümündeki** yeni sürüm: Git artık 2019'da Visual Studio denetim deneyimidir. Özellik kümesi yerleşik olarak ve son iki sürümde geri bildiriminiz temel alarak bu kümeyi de temel aldık. Yeni deneyim artık herkes için varsayılan olarak açıktır. Yeni Git menüsünden depoları kopya açabilir, oluşturabilir veya açabilirsiniz. Tümleşik Git aracı pencerelerini kullanarak değişiklikleri kodunuza işip itme, dalları yönetme, uzak depolarınızı güncel kalma ve birleştirme çakışmalarını çözme.

Daha fazla bilgi için Visual Studio [sayfasındaki Git deneyimine](../version-control/git-with-visual-studio.md) bakın.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share,](https://visualstudio.microsoft.com/services/live-share/) bir kod tabanını ve bağlamını bir ekip arkadaşı ile paylaşmanız ve doğrudan bir ekip arkadaşı ile anında çift yönlü işbirliği elde etmenizi sağlayan bir geliştirici Visual Studio. Ekip Live Share ekip arkadaşlarınız, kendileriyle paylaştığım bir projeyi okuyabilir, gezin, düzenleyebilir ve hata ayıklar ve bunu sorunsuz ve güvenli bir şekilde yapar.

Ayrıca Visual Studio 2019'da bu hizmet varsayılan olarak yüklenir.

![Visual Studio 2019'daki işbirliği Live Share gösteren animasyon](media/vs-2019/live-share.gif "Live Share 2019'daki Visual Studio işbirliği özelliği.")

Daha fazla bilgi için [gerçek zamanlı Visual Studio Live Share](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) incelemeleri ve etkileşimli eğitim blog gönderisi ile ilgili bilgilere ve Live Share [2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) blog gönderisine Visual Studio bakın.

### <a name="integrated-code-reviews"></a>Tümleşik kod incelemeleri

Visual Studio 2019 ile birlikte kullanmak üzere indir Visual Studio tanıtacak. Bu yeni uzantıyla, takımdan ayrılmadan çekme isteklerini gözden geçir, çalıştır ve hatta hata Visual Studio. Hem depolarda hem de GitHub kod Azure DevOps destekliyoruz.

   ![Visual Studio 2019'da yeni Çekme İstekleri uzantısının ekran görüntüsü](media/vs-2019/pr-experience.png "Visual Studio 2019'daki yeni Çekme İstekleri uzantısı.")

Daha fazla bilgi için Çekme [İstekleri uzantısının Visual Studio kod incelemeleri](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) blog gönderisi'ne bakın.

## <a name="debug"></a>Hata Ayıklama

Hata ayıklarken hassas hedefleme ile nasıl sıfırlayabilirsiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu izleyin. <br><br>*Video uzunluğu: 3,54 dakika*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Performans kazançları

Bir kerelik özel C++ veri kesme noktalarına sahip ve bunları .NET Core uygulamaları için uyarlamış olduk.

   ![2019'da hata ayıklama veri kesme Visual Studio gösteren animasyon](media/vs-2019/debug-data-breakpoints.gif "Visual Studio 2019'daki hata ayıklama veri kesme noktaları.")

Bu nedenle ister C++ ister .NET Core'da kodlamaya karar ver, veri kesme noktaları yalnızca düzenli kesme noktaları yerleştirmeye iyi bir alternatif olabilir. Veri kesme noktaları, genel bir nesnenin nerede değiştiril olduğunu, listeye ekli veya listeden kaldırıldığı yeri bulma gibi senaryolar için de harikadır.

Ayrıca, büyük uygulamalar geliştiren bir C++ geliştiricisiyseniz Visual Studio 2019'un, bellekle ilgili sorunları yaşamadan bu uygulamalarda hata ayıklamaya olanak sağlayan bir yordamdan semboller yaptığına dikkat edin.

### <a name="search-while-debugging"></a>Hata ayıklama sırasında arama

Büyük olasılıkla daha önce bir dizenin izleme penceresi bir dizi değere bakarak orada bulundun. Bu Visual Studio 2019'da, aramakta olduğunu nesneleri ve değerleri bulanıza yardımcı olmak için İzleme, Yereller ve Otomatikler pencerelerine arama ekledik.

   ![Visual Studio 2019'da hata ayıklama arama penceresini gösteren animasyon](media/vs-2019/debug-window-search.gif "Visual Studio 2019'da hata ayıklama arama penceresi.")

Ayrıca, bir değerin İzleme, Yereller ve Otomatikler pencerelerinde nasıl görüntülendiğinden de biçimlendirebilirsiniz. Herhangi bir penceredeki öğelerden birini çift tıklayarak seçin ve her biri amaçlanan etkisinin açıklamasını içeren olası biçim belirleyicilerinin açılan listesine erişmek için virgül (",") ekleyin.

   ![Visual Studio 2019'daki yeni izleme penceresi ve biçim değerleri özelliği](media/search-watch-window.png "Izleme penceresi 2019'daki yeni Visual Studio ve biçim değerleri özelliği.")

Daha fazla bilgi için İzleme, Otomatikler ve Yereller blog gönderisinde [Visual Studio 2019'](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) da Gelişmiş: Nesne ve Özellikler için Arama Windows bakın.

### <a name="snapshot-debugger"></a>Anlık Görüntü Hata Ayıklayıcı

Tam olarak neler olduğunu görmek için buluttaki uygulama yürütmenin anlık görüntüsünü alın. (Bu özellik yalnızca Visual Studio Enterprise kullanılabilir.)

   ![Visual Studio 2019'da Snapshot Debugger gösteren animasyon Enterprise](media/vs-2019/snapshot-debugger.gif "Snapshot Debugger 2019 Visual Studio'daki Enterprise.")

Azure VM'sinde çalıştıran ASP.NET (Çekirdek ve masaüstü) uygulamaları hedefleme desteği ekledik. Ayrıca bir uygulama içinde çalıştıran uygulamalar için destek Azure Kubernetes Service. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

Daha fazla bilgi için Snapshot Debugger sayfasını [kullanarak Canlı](../debugger/debug-live-azure-applications.md) ASP.NET Azure uygulamalarının hata ayıklaması sayfasına ve [Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) için Zaman Yolculuğu Hata Ayıklamaya Giriş blog gönderisi'ne bakın.

### <a name="microsoft-edge-insider-support"></a>Microsoft Edge Insider desteği

**16.2'de** yeni: Bir JavaScript uygulamasında kesme noktası ayarlayabilirsiniz ve [Microsoft Edge Insider tarayıcısını](https://www.microsoftedgeinsider.com/) kullanarak bir hata ayıklama oturumu başlatabilirsiniz. Bunu yapmak için Visual Studio hata ayıklamanın etkinleştirildiğinde yeni bir tarayıcı penceresi açılır. Bu pencereyi kullanarak uygulama JavaScript'i Visual Studio.

   ![Tarayıcıda JavaScript kod işlemeyi gösteren ekran görüntüsü](media/vs-2019/edge-chromium-breakpoint.png "Tarayıcıda JavaScript kodu işleme.")

### <a name="pinnable-properties-tool"></a>Sabitlenebilir Özellikler aracı

**16.4'te** yeni bir özellik: Yeni Sabitlenebilir Özellikler aracıyla hata ayıklarken nesneleri özelliklerine göre tanımlamak artık daha kolay. İmleci İzleme, Otomatikler ve Yereller pencerelerinin hata ayıklayıcısı penceresinde görüntülemek istediğiniz bir özelliğin üzerine gelmeniz, sabitleme simgesini seçmeniz ve pencerenin en üstünde gördüğünüz bilgileri hemen görmeniz gerekir!

   ![Sabitlenebilir Özellikler aracını kullanarak hata ayıklayıcısında Visual Studio sabitlemeyi gösteren animasyon](media/vs-2019/debugger-pinnable-properties.gif "Sabitlenebilir Özellikler aracını Visual Studio hata ayıklayıcısında özellikleri sabitler.")

Daha fazla bilgi için Sabitlenebilir Özellikler: Yönetilen Nesneleri Görüntüleme & Hata Ayıklama [blog gönderisi'ne](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) bakın.

## <a name="whats-next"></a>Sırada ne var?

Geliştirme Visual Studio daha da iyi hale gelen yeni özelliklerle güncelleştirmeler sağlıyoruz. En son yeniliklerimiz hakkında daha fazla bilgi edinmek için Visual Studio [göz atabilirsiniz.](https://devblogs.microsoft.com/visualstudio/) Önizlemede bugüne kadar yayımlanaların bir kaydı için Önizleme Sürüm [Notları'ne göz atabilirsiniz.](/visualstudio/releases/2019/release-notes-preview/) Bir sonraki sürüme neleri yayınlayacağız? listesi için yol [haritasına Visual Studio bakın.](/visualstudio/productinfo/vs-roadmap)

Bu arada, çalışmalarda şu anda neler var:

- **Visual Studio 2019'da geliştirilmiş Git deneyimi**

   Git sürüm denetimi aracı Visual Studio 2019 sürüm [16.8](/visualstudio/releases/2019/release-notes-history/) ve sonraki sürümlerde varsayılan deneyim olsa da, Visual Studio 2019 sürüm [16.11'in](/visualstudio/releases/2019/release-notes-preview/)en yeni sürümünde deneyimi geliştirmek için özellikler eklemeye devam edeceğiz.

   Daha fazla bilgi için [bkz. Sürüm denetimi Visual Studio.](/visualstudio/version-control/)

- **Visual Studio 2022 (Önizleme) kullanılabilir**

    En yeni sürüm olan [Visual Studio 2022 (Önizleme)](/visualstudio/releases/2022/release-notes-preview/) daha hızlı, daha kolay ve daha basit. İlk kez 64 bit Visual Studio için.

    İndirme bağlantısı ve daha fazla bilgi için [Visual Studio 2022](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/) vision blog gönderisinin yanı [**sıra Visual Studio 2022 Preview 3'e**](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/) de ulaşabilirsiniz.

## <a name="give-us-feedback"></a>Geri bildirimde bulunun

Neden Visual Studio ekibine geri bildirim gönderebilirsiniz? Çünkü müşteri geri bildirimlerini ciddiye alıyoruz. Bu, yapacaklarının büyük bir fazlasını yapar.

* Bu özelliği nasıl geliştirebiliriz konusunda bir öneride Visual Studio, Özellik Öneri aracını [kullanarak bunu yapabiliriz.](suggest-a-feature.md)

* Sorun Bildirme aracını kullanarak Visual Studio, kilitleniyor veya başka bir performans sorunuyla karşımıza çıkarsanız yeniden verme adımlarını ve destek dosyalarını bizimle kolayca [paylaşabilirsiniz.](how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2022 'de (Önizleme) yapılan yeniler](whats-new-visual-studio-2022.md)
* [Visual Studio docs'daki yeniler](whats-new-visual-studio-docs.md)
* [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes/)
* [Visual Studio Mac için 2019 sürüm notları](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Visual Studio 2019 SDK'daki yeniler](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Visual Studio 2017’deki C++ yenilikleri](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio/)
* [C# 9.0'da yapılan yeniler](/dotnet/csharp/whats-new/csharp-9)
* [.NET 5’teki yenilikler](/dotnet/core/dotnet-five)
* [.NET Framework'daki .NET Framework](/dotnet/framework/whats-new/)
* [Microsoft Build konferansı](https://www.microsoft.com/build)
* [Microsoft Ignite konferansı](https://www.microsoft.com/ignite)
