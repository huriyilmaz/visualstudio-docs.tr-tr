---
title: Visual Studio 2019’daki yenilikler
titleSuffix: ''
description: Visual Studio 2019 ' deki yeni özellikler hakkında bilgi edinin.
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
ms.openlocfilehash: f809daed713cee441e68a7902a03eeecc364b6eed269548d016ee55da5afec90
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121289367"
---
# <a name="whats-new-in-visual-studio-2019"></a>Visual Studio 2019’daki yenilikler

**16,11 sürümü için güncelleştirildi.** Bkz. [tam sürüm notları](/visualstudio/releases/2019/release-notes/) | [Ürün yol haritasını](/visualstudio/productinfo/vs2019-roadmap) görüntüle

>[!div class="button"]
>[Visual Studio 2019’u İndirin](https://visualstudio.microsoft.com/downloads/)

Visual Studio 2019 ile herhangi bir geliştirici, uygulama ve herhangi bir platform için sınıfının en iyisi araçları ve hizmetleri elde edersiniz. Visual Studio ilk kez mi kullanıyorsunuz, yoksa yıllarca mi kullanıyorsunuz, geçerli sürümümüze kadar çok şey var!

İşte yenilikler ve hepsi için yüksek düzey bir üst sınır aşağıda verilmiştir:

* **[Geliştirme](#develop)**: gelişmiş performans, anlık kod temizleme ve daha iyi arama sonuçlarıyla odaklanmış ve üretken olun.
* **[İşbirliği](#collaborate)**: git-ilk iş akışı, gerçek zamanlı Düzenle ve hata ayıklama ve Visual Studio ' de doğrudan kod İncelemeleri aracılığıyla doğal işbirliğinden yararlanın.
* **[Hata Ayıkla](#debug)**: belirli değerleri vurgulayın ve bu değerlere gidin, bellek kullanımını iyileştirin ve uygulamanızın yürütmesinin otomatik anlık görüntülerini alın.

Bu sürümdeki tüm yenilikleri içeren tüm liste için [sürüm notlarına](/visualstudio/releases/2019/release-notes/)bakın. ayrıca, 16,11 sürümündeki yenilikler hakkında daha fazla bilgi için bkz. [Visual Studio 2019 v 16.11 şimdi](https://devblogs.microsoft.com/visualstudio/visual-studio-16-11/) blog gönderisi.

## <a name="develop"></a>Geliştirme

Yeni özelliklerle zamanı nasıl kaydedebileceğinizi öğrenmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 3,00 dakika*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>İyileştirilmiş arama

Daha önce Hızlı Başlat olarak bilinen yeni arama deneyimimiz daha hızlı ve daha etkilidir. Şimdi, yazarken arama sonuçları dinamik olarak görünür. Ve arama sonuçları genellikle komutlar için klavye kısayolları içerebilir, böylece daha sonra kullanmak üzere bunları yeniden deneyebilirsiniz.

   ![Visual Studio 2019 ' de yeni arama deneyimine yönelik bir animasyon](media/vs-2019/new-search-feature.gif "Visual Studio 2019'daki yeni arama deneyimi.")

Yeni benzer arama mantığı, yazım hatalarını ne olursa olsun ihtiyacınız olan her şeyi bulur. Bu nedenle, komutları, ayarları, belgeleri veya diğer yararlı şeyleri arıyorsanız, yeni arama özelliği aradığınızı bulmayı kolaylaştırır.

daha fazla bilgi için bkz. [Visual Studio arama kullanma](visual-studio-search.md).

#### <a name="intelligent-search-service"></a>Akıllı arama hizmeti

**16,9 ' de yeni**: bulut destekli teknoloji, yapay zeka ve makine öğrenimi kullanarak arama sonuçlarımızı geliştirdik. artık Visual Studio arama yalnızca daha ilgili sonuçlar üretmiyor, ancak aynı zamanda ürün özelliklerini daha kolay bulmanıza de yardımcı olabilir.

daha fazla bilgi için bkz. [akıllı Visual Studio arama hizmeti](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) blog gönderisi.

### <a name="refactorings"></a>Yeniden düzenlemeler

C# ' de kodunuzun düzenlenmesine daha kolay olan çok sayıda yeni ve son derece yararlı yeniden düzenlemeler vardır. Hafif ampulde öneriler olarak görünür ve üyeleri arabirim veya temel sınıfa taşıma, ad alanlarını klasör yapısıyla eşleşecek şekilde ayarlama, Foreach-döngülerini LINQ Sorgularına dönüştürme ve daha fazlasını içeren eylemleri içerir.

   ![Visual Studio 2019 ' de yeniden düzenlemeler deneyiminin animasyonu](media/vs-2019/refactorings.gif "Visual Studio 2019'da yeniden düzenleme deneyimi.")

Yalnızca **CTRL +** tuşlarına basarak yeniden düzenlemeler çağırın. ve gerçekleştirmek istediğiniz eylemi seçin.

### <a name="intellicode"></a>IntelliCode

[Visual Studio ıntellicode](/visualstudio/intellicode/) , yapay zeka (aı) kullanarak yazılım geliştirme çabalarınızı geliştirir. ıntellicode, GitHub üzerinde &mdash; her biri 100 yıldız ile &mdash; , önerilerini oluşturmak için 2.000 açık kaynaklı projeler arasında gezinir.

![Visual Studio 2019 ' de ıntellicode animasyonu](media/vs-2019/IntelliCode.gif "Visual Studio 2019'da IntelliCode.")

Visual Studio ıntellicode 'un üretkenliğinizi artırmaya yardımcı olması için birkaç yol vardır:

* Bağlama duyarlı kod tamamlama sunma
* Geliştiricilere takımınızın desenlerine ve stillerine uyacak şekilde rehberlik edin
* Zor kod sorunlarını bulma
* Gerçekten oluşan alanlara dikkat çekmek için kod incelemelerini odaklayın

Başlangıçta yalnızca Visual Studio için bir uzantı olarak ıntellicode önizlendiğinde yalnızca C# ' i destekliyoruz. Artık **16,1 ' de yeni** eklendi, C# ve xaml "yerleşik" için destek ekledik. (C++ ve TypeScript/JavaScript desteği hala önizlemededir, ancak.)

C# kullanıyorsanız, kendi kodunuzda özel bir modeli eğitme özelliği de ekledik.

ıntellicode hakkında daha fazla bilgi için, bkz. [ıntellicode 'un genel kullanılabilirliğini duyuruyor](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) ve daha fazla gizli gözlem ve [kod, Visual Studio ıntellicode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) blog gönderileriyle daha az kaydırma.

### <a name="code-cleanup"></a>Kod temizleme

Yeni bir belge durumu göstergesi ile eşleştirilmiş yeni bir kod temizleme komutu. Bu yeni komutu, hem uyarıları hem de önerileri tek bir eylemle (veya bir düğmeye tıklayarak) tanımlayıp onarmak için kullanabilirsiniz.

Temizleme kodu biçimlendirir ve [geçerli ayarlar](code-styles-and-code-cleanup.md) ve [. editorconfig dosyaları](create-portable-custom-editor-options.md)tarafından önerildiği şekilde kod düzeltmelerini uygular.

   ![Visual Studio 2019 ' de yeni kod temizleme denetiminin ekran görüntüsü](media/vs-2019/code-cleanup-profile.png "Visual Studio 2019'daki yeni kod temizleme denetimi.")

Ayrıca, armanesnelerin koleksiyonlarını bir profil olarak kaydedebilirsiniz. Örneğin, kodlarken sıkça uyguladığınız bir dizi hedeflenmiş sabit listesi varsa ve daha sonra bir kod incelemesinin önüne uygulamak üzere daha kapsamlı bir sabit listesi varsa, profilleri bu farklı görevleri ele almak için yapılandırabilirsiniz.

   ![Visual Studio 2019 ' de kod temizleme denetimini yapılandırma ekran görüntüsü](media/vs-2019/code-cleanup-profile-configure.png "Visual Studio 2019'da kod temizleme denetimi yapılandırma.")

### <a name="per-monitor-aware-pma-rendering"></a>Monitör başına duyarlı (PMA) işleme

farklı görüntü ölçeği faktörlerine sahip olan veya ana cihazınızdan farklı olan görüntüleme ölçeği faktörleri olan bir makineye uzaktan bağlanmak için kullanılan izleyicileri kullanıyorsanız, Visual Studio bulanık göründüğünü veya yanlış ölçekte işlediğini fark edebilirsiniz.

Visual Studio 2019 ' nin yayınlanmasıyla birlikte, izleme için duyarlı (pma) bir uygulama Visual Studio veriyoruz. şimdi, kullandığınız görüntü ölçeği faktörlerine bakılmaksızın Visual Studio doğru şekilde işler.

   ![Visual Studio 2019 ' de monitöre duyarlı (pma) işleme başına](media/vs-2019/pma-dpi-scaling.png "2019'da monitör başına Visual Studio (PMA) işleme.")

daha fazla bilgi için, [Visual Studio 2019 blog gönderisinde daha iyi bir çoklu izleme deneyimine](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) bakın.

### <a name="test-explorer"></a>Test Gezgini

**16,2 ' de yeni**: Test Gezgini ' ni, büyük test kümelerinin daha iyi işlenmesini, daha kolay filtrelenmesini, daha keşfedilebilir komutları, sekmeli çalma listesi görünümlerini ve özelleştirilebilir sütunları, hangi test bilgilerinin görüntülendiğini ayarlamanıza olanak sağlayacak şekilde güncelleştirdik.

   ![Test Gezgininde Kullanıcı arabirimi geliştirmelerini gösteren ekran görüntüsü](media/vs-2019/test-explorer-ui.png "Test Gezgini'nde kullanıcı arabirimi geliştirmeleri.")

### <a name="net-core"></a>.NET Core

**16,3 ' de yeni** eklendi: .net Core 3,0 için destek ekledik. Platformlar arası, açık kaynak &mdash; ve Microsoft tarafından tam olarak desteklenmektedir.

Daha fazla bilgi için bkz. [.NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) blog gönderisi duyurusu.

## <a name="collaborate"></a>İşbirliği

Sorunları çözmek için nasıl ekip sağlayabileceğiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 4,22 dakika*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Git-ilk iş akışı

Visual Studio 2019 ' i açtığınızda yeni başlangıç penceresi olduğunu fark edersiniz.

   ![Visual Studio 2019 ' deki yeni başlangıç penceresinin ekran görüntüsü](media/vs-2019/start-window-dark.png "Visual Studio 2019'daki yeni başlangıç penceresi.")

Başlangıç penceresi size hızlı bir şekilde kod almanızı sağlamak için çeşitli seçenekler sunar. Önce bir depodan kod kopyalama veya kullanıma alma seçeneğini yerleştirdik.

   ![Visual Studio 2019 ' de ' Git-first ' deneyiminin animasyonu](media/vs-2019/git-first.gif "Visual Studio 2019'daki 'Git-first' deneyimi.")

Başlangıç penceresi ayrıca bir proje veya çözüm açma, yerel bir klasör açma veya yeni bir proje oluşturma seçeneklerini de içerir.

daha fazla bilgi için bkz. [Get to code: yeni Visual Studio başlat pencere blog gönderisini nasıl tasarlıyoruz](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) .

### <a name="git-productivity"></a>Git verimliliği

**16,8 ' deki yenilikler**: Git artık Visual Studio 2019 ' de varsayılan sürüm denetimi deneyimidir. Son iki yayın sırasında geri bildirimlerinizi temel alarak, özellik kümesini geliştirdik ve bu, yineleyecek şekilde serbest bırakıldı. Yeni deneyim artık herkes için varsayılan olarak açıktır. Yeni Git menüsünde depoları kopyalayabilir, oluşturabilir veya açabilirsiniz. Kodunuzda değişiklikleri yürütmek ve göndermek, dalları yönetmek, uzak depolarınızda güncel kalmak ve birleştirme çakışmalarını çözmek için tümleşik git araç pencerelerini kullanın.

daha fazla bilgi için Visual Studio sayfasındaki [Git deneyimine](../version-control/git-with-visual-studio.md) bakın.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) , bir kod temeli ve bağlamını bir ekiple paylaşmanıza ve doğrudan Visual Studio içinden doğrudan çift yönlü işbirliği yapmanıza olanak tanıyan bir geliştirici hizmetidir. Live Share, bir ekip mate kendileriyle paylaştığınız bir projeyi okuyabilir, gezinmiş, düzenleyebilir ve hata ayıklamanızı ve sorunsuz ve güvenli bir şekilde yapabilmesini sağlayabilir.

Visual Studio 2019 ile, bu hizmet varsayılan olarak yüklenir.

![Visual Studio 2019 ' de Live Share işbirliği özelliğini gösteren bir animasyon](media/vs-2019/live-share.gif "Live Share 2019'daki Visual Studio işbirliği özelliği.")

daha fazla bilgi için bkz. [gerçek zamanlı kod incelemeleri ve etkileşimli eğitim](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) blog gönderisi ve [Live Share artık Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) blog gönderisine dahil Visual Studio Live Share.

### <a name="integrated-code-reviews"></a>Tümleşik kod İncelemeleri

Visual Studio 2019 ile kullanmak üzere indirebileceğiniz yeni bir uzantı sunuyoruz. Bu yeni uzantıyla birlikte Visual Studio olmadan takımınızdan çekme isteklerini gözden geçirebilir, çalıştırabilir ve hatta hata ayıklayabilirsiniz. GitHub ve Azure DevOps depolarındaki kodu destekliyoruz.

   ![Visual Studio 2019 ' de yeni çekme istekleri uzantısının ekran görüntüsü](media/vs-2019/pr-experience.png "Visual Studio 2019'daki yeni Çekme İstekleri uzantısı.")

daha fazla bilgi için [Visual Studio çekme istekleri uzantısı blog gönderisini kullanarak kod incelemelerine](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) bakın.

## <a name="debug"></a>Hata Ayıklama

Hata ayıklarken hassas hedefleme ile nasıl sıfırlayabilirsiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu izleyin. <br><br>*Video uzunluğu: 3,54 dakika*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Performans kazançları

Bir kerelik özel C++ veri kesme noktalarına sahip ve bunları .NET Core uygulamaları için uyarlamış olduk.

   ![Visual Studio 2019'da hata ayıklama veri kesme noktaları gösteren animasyon](media/vs-2019/debug-data-breakpoints.gif "Visual Studio 2019'daki hata ayıklama veri kesme noktaları.")

Bu nedenle ister C++ ister .NET Core'da kodlamaya karar ver, veri kesme noktaları yalnızca normal kesme noktaları yerleştirmeye iyi bir alternatif olabilir. Veri kesme noktaları, genel bir nesnenin nerede değiştiril olduğunu, listeye ekleniyor veya listeden kaldırıldığı yeri bulma gibi senaryolar için de harikadır.

Ayrıca, büyük uygulamalar geliştiren bir C++ geliştiricisiyseniz Visual Studio 2019' da, bellekle ilgili sorunları yaşamadan bu uygulamalarda hata ayıklamaya olanak sağlayan, yordamdan semboller yaptı.

### <a name="search-while-debugging"></a>Hata ayıklama sırasında arama

Büyük olasılıkla daha önce bir dizeyi bir dizi izleme penceresi dizeye bakarak orada bulundun. Bu Visual Studio 2019'da, aramakta olduğunu nesneleri ve değerleri bulanıza yardımcı olmak için İzleme, Yereller ve Otomatikler pencerelerine arama ekledik.

   ![Visual Studio 2019'da hata ayıklama arama penceresini gösteren animasyon](media/vs-2019/debug-window-search.gif "Visual Studio 2019'da hata ayıklama arama penceresi.")

Bir değerin İzleme, Yereller ve Otomatikler pencerelerinde nasıl görüntülendiğinden de biçimlendirebilirsiniz. Herhangi bir penceredeki öğelerden birini çift tıklayarak seçin ve her biri amaçlanan etkisinin açıklamasını içeren olası biçim belirleyicilerinin açılan listesine erişmek için virgül (",") ekleyin.

   ![Visual Studio 2019'daki yeni izleme penceresi ve biçim değerleri özelliği](media/search-watch-window.png "Izleme penceresi 2019'daki yeni Visual Studio ve biçim değerleri özelliği.")

Daha fazla bilgi için İzleme, Otomatikler ve Yereller blog gönderisinde [Visual Studio 2019'](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) da Gelişmiş: Nesne ve Özellik Arama Windows bakın.

### <a name="snapshot-debugger"></a>Anlık Görüntü Hata Ayıklayıcı

Tam olarak neler olduğunu görmek için buluttaki uygulama yürütmenin anlık görüntüsünü alın. (Bu özellik yalnızca Visual Studio Enterprise kullanılabilir.)

   ![Visual Studio 2019'da Snapshot Debugger gösteren animasyon Enterprise](media/vs-2019/snapshot-debugger.gif "Snapshot Debugger 2019 Visual Studio'daki Enterprise.")

Azure VM'leri üzerinde ASP.NET (Çekirdek ve masaüstü) uygulamaları hedefleme desteği ekledik. Ayrıca, bir uygulama içinde çalıştıran uygulamalar için destek Azure Kubernetes Service. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

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
