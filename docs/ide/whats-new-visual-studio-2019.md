---
title: Visual Studio 2019’daki yenilikler
titleSuffix: ''
description: Visual Studio 2019'daki yeni özellikler hakkında bilgi.
ms.date: 05/28/2021
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 8664606877f5393a98a78e32c6d396e1a5bcf4c1
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687694"
---
# <a name="whats-new-in-visual-studio-2019"></a>Visual Studio 2019’daki yenilikler

**[16.10 sürümü için güncelleştirildi](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Visual Studio 2019’u İndirin](https://visualstudio.microsoft.com/downloads)

2019'Visual Studio ile tüm geliştirici, uygulama ve platformlar için sınıfının en iyisi araçlara ve hizmetlere sahip oluruz. İster ilk kez Visual Studio ister yıllardır kullanıyor olun, en son sürümde olduğu gibi birçok şey vardır!

İşte yeni ve her şey ile ilgili üst düzey bir özet:

* **[Geliştirme:](#develop)** Gelişmiş performans, anında kod temizleme ve daha iyi arama sonuçları ile odaklanmış ve üretken kalın.
* **[İşbirliği](#collaborate)** yapma: Git'in ilk iş akışı, gerçek zamanlı düzenleme ve hata ayıklama ve kod incelemeleri aracılığıyla doğal işbirliğinin Visual Studio.
* **[Hata ayıklama:](#debug)** Belirli değerleri vurgulayın ve bu değerlere gidin, bellek kullanımını iyileştirin ve uygulamanın yürütülmesinin otomatik anlık görüntülerini alın.

Bu sürümde yeni olan her şeyin tam listesi için sürüm [notlarına bakın.](/visualstudio/releases/2019/release-notes/)

## <a name="develop"></a>Geliştirme

Yeni özelliklerle nasıl zaman tasarrufu yapabilirsiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu izleyin. <br><br>*Video uzunluğu: 3,00 dakika*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Geliştirilmiş arama

Eski adıyla Hızlı Başlat, yeni arama deneyimimiz daha hızlı ve daha etkili. Artık siz yazıldığında arama sonuçları dinamik olarak görüntülenir. Ayrıca, arama sonuçları genellikle komutların klavye kısayollarını içerebilir, böylece bunları daha sonra kullanmak üzere ezberlersiniz.

   ![Visual Studio 2019'daki yeni arama deneyiminin animasyonu](media/vs-2019/new-search-feature.gif "Visual Studio 2019 ' deki yeni arama deneyimi.")

Yeni belirsiz arama mantığı, yazım hatasına bakılmaksızın ihtiyacınız olan her şeyi bulur. Bu nedenle komutlar, ayarlar, belgeler veya diğer yararlı şeyleri arıyor olun, yeni arama özelliği, arayabilirsiniz.

Daha fazla bilgi için [bkz. Arama Visual Studio kullanma.](visual-studio-search.md)

#### <a name="intelligent-search-service"></a>Akıllı arama hizmeti

**16,9 ' de yeni**: bulut destekli teknoloji, yapay zeka ve makine öğrenimi kullanarak arama sonuçlarımızı geliştirdik. Artık yalnızca Visual Studio 'da arama yapmak daha ilgili sonuçlar üretmez, ancak aynı zamanda ürün özelliklerini daha kolay keşfetmenize de yardımcı olabilir.

Daha fazla bilgi için bkz. [akıllı Visual Studio Search hizmeti](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) blog gönderisi.

### <a name="refactorings"></a>Yeniden düzenlemeler

C# ' de kodunuzun düzenlenmesine daha kolay olan çok sayıda yeni ve son derece yararlı yeniden düzenlemeler vardır. Hafif ampulde öneriler olarak görünür ve üyeleri arabirim veya temel sınıfa taşıma, ad alanlarını klasör yapısıyla eşleşecek şekilde ayarlama, Foreach-döngülerini LINQ Sorgularına dönüştürme ve daha fazlasını içeren eylemleri içerir.

   ![Visual Studio 2019 yeniden düzenlemeler deneyiminin animasyonunu](media/vs-2019/refactorings.gif "Visual Studio 2019 ' de yeniden düzenlemeler deneyimi.")

Yalnızca **CTRL +** tuşlarına basarak yeniden düzenlemeler çağırın. ve gerçekleştirmek istediğiniz eylemi seçin.

### <a name="intellicode"></a>IntelliCode

[Visual Studio ıntellicode](/visualstudio/intellicode/) yapay zeka (AI) kullanarak yazılım geliştirme çabalarınızı geliştirir. Intellicode &mdash; , her birinin &mdash; önerilerini oluşturmak için her biri 100 yıldız ile 2.000 açık kaynaklı projeler arasında gezinir.

![Visual Studio 2019 ' de ıntellicode animasyonu](media/vs-2019/IntelliCode.gif "Visual Studio 2019 ' de ıntellicode.")

Visual Studio ıntellicode 'un üretkenliğinizi artırmaya yardımcı olabilecek birkaç yol aşağıda verilmiştir:

* Bağlama duyarlı kod tamamlama sunma
* Geliştiricilere takımınızın desenlerine ve stillerine uyacak şekilde rehberlik edin
* Zor kod sorunlarını bulma
* Gerçekten oluşan alanlara dikkat çekmek için kod incelemelerini odaklayın

Başlangıçta yalnızca Visual Studio için bir uzantı olarak ıntellicode önizlendiğinde C# ' i destekliyoruz. Artık **16,1 ' de yeni** eklendi, C# ve xaml "yerleşik" için destek ekledik. (C++ ve TypeScript/JavaScript desteği hala önizlemededir, ancak.)

C# kullanıyorsanız, kendi kodunuzda özel bir modeli eğitme özelliği de ekledik.

IntelliCode hakkında daha fazla bilgi için IntelliCode'un genel kullanılabilirliği hakkında daha fazla bilgi için [Bkz. IntelliCode'un](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) genel kullanılabilirliğinin yanı sıra bir göz atma ve Daha fazla kodla daha fazla [bilgi Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) blog gönderileri.

### <a name="code-cleanup"></a>Kod temizleme

Yeni bir belge durumu göstergesiyle eşleştirilmiş yeni bir kod temizleme komutudur. Bu yeni komutu kullanarak hem uyarıları hem de önerileri tek bir eylemle tanımlayabilir ve düzeltebilirsiniz (veya bir düğmeye tıklayabilirsiniz).

Temizleme işlemi kodu biçimlendirecek ve geçerli ayarlar ve [](code-styles-and-code-cleanup.md) .editorconfig dosyaları tarafından önerilen kod [düzeltmelerini uygulayacak.](create-portable-custom-editor-options.md)

   ![Visual Studio 2019'da yeni kod temizleme denetimi ekran görüntüsü](media/vs-2019/code-cleanup-profile.png "Visual Studio 2019 ' de yeni kod temizleme denetimi.")

Ayrıca, düzeltici koleksiyonlarını profil olarak kaydedebilirsiniz. Örneğin, kod sırasında sık sık uygulayan küçük bir hedefli düzeltici kümeniz varsa ve bir kod incelemeden önce uygulayacak başka kapsamlı çözümciler kümeniz varsa, profilleri bu farklı görevleri ele alan şekilde yapılandırabilirsiniz.

   ![Visual Studio 2019'da kod temizlemeyi yapılandırma denetimi ekran görüntüsü](media/vs-2019/code-cleanup-profile-configure.png "Visual Studio 2019 ' de kod temizleme denetimini yapılandırma.")

### <a name="per-monitor-aware-pma-rendering"></a>Monitör başına farkında (PMA) işleme

Farklı ekran ölçek faktörleriyle yapılandırılmış monitörler kullanıyorsanız veya ana cihazınızın farklı görüntü ölçek faktörlerine sahip bir makineye uzaktan bağlanıyorsanız, Visual Studio bulanık göründüğünü veya yanlış ölçekte işleniyor olduğunu fark edebilirsiniz.

Visual Studio 2019'un sürümüyle, izleyici başına Visual Studio (PMA) bir uygulama yapıyoruz. Artık Visual Studio ölçek faktörlerine bakılmaksızın doğru şekilde işleniyor.

   ![Visual Studio 2019'da monitör başına işleme (PMA)](media/vs-2019/pma-dpi-scaling.png "Visual Studio 2019 ' de monitöre duyarlı (PMA) işleme.")

Daha fazla bilgi için Visual Studio [2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) blog gönderisi ile daha iyi çoklu izleme deneyimine bakın.

### <a name="test-explorer"></a>Test Gezgini

**16.2'de** yeni sürümü: Test Gezgini'ni, büyük test kümelerinin daha iyi işlenmesini, daha kolay filtrelemeyi, daha fazla keşfedilebilir komutları, sekmeli oynatma listesi görünümlerini ve hangi test bilgisinin görüntülendiğinde hassas ayarlamalar yapmak için özelleştirilebilir sütunlar sağlayacak şekilde güncelleştirildi.

   ![Test Gezgini'nde kullanıcı arabirimi geliştirmelerini gösteren ekran görüntüsü](media/vs-2019/test-explorer-ui.png "Test Gezgini 'ndeki Kullanıcı arabirimi geliştirmeleri.")

### <a name="net-core"></a>.NET Core

**16,3 ' de yeni** eklendi: .net Core 3,0 için destek ekledik. Platformlar arası, açık kaynak &mdash; ve Microsoft tarafından tam olarak desteklenmektedir.

Daha fazla bilgi için bkz. [.NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) blog gönderisi duyurusu.

## <a name="collaborate"></a>İşbirliği

Sorunları çözmek için nasıl ekip sağlayabileceğiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 4,22 dakika*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Git-ilk iş akışı

Visual Studio 2019 ' i açtığınızda yeni başlangıç penceresi olduğunu fark edeceksiniz.

   ![Visual Studio 2019 ' de yeni başlangıç penceresinin ekran görüntüsü](media/vs-2019/start-window-dark.png "Visual Studio 2019 ' deki yeni başlangıç penceresi.")

Başlangıç penceresi size hızlı bir şekilde kod almanızı sağlamak için çeşitli seçenekler sunar. Önce bir depodan kod kopyalama veya kullanıma alma seçeneğini yerleştirdik.

   ![Visual Studio 2019 ' de ' git-First ' deneyiminin animasyonu](media/vs-2019/git-first.gif "Visual Studio 2019 ' de ' git-First ' deneyimi.")

Başlangıç penceresi ayrıca bir proje veya çözüm açma, yerel bir klasör açma veya yeni bir proje oluşturma seçeneklerini de içerir.

Daha fazla bilgi için bkz. [Get to Code: yeni Visual Studio başlangıç penceresini nasıl tasarlıyoruz](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) blog gönderisi.

### <a name="git-productivity"></a>Git verimliliği

**16,8 ' deki yenilikler**: git artık Visual Studio 2019 ' de varsayılan sürüm denetimi deneyimidir. Son iki yayın sırasında geri bildirimlerinizi temel alarak, özellik kümesini geliştirdik ve bu, yineleyecek şekilde serbest bırakıldı. Yeni deneyim artık herkes için varsayılan olarak açıktır. Yeni Git menüsünde depoları kopyalayabilir, oluşturabilir veya açabilirsiniz. Kodunuzda değişiklikleri yürütmek ve göndermek, dalları yönetmek, uzak depolarınızda güncel kalmak ve birleştirme çakışmalarını çözmek için tümleşik git araç pencerelerini kullanın.

Daha fazla bilgi için bkz. [Visual Studio 'Da git deneyimi](../version-control/git-with-visual-studio.md) sayfası.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share,](https://visualstudio.microsoft.com/services/live-share/) bir kod tabanını ve bağlamını bir ekip arkadaşı ile paylaşmanız ve doğrudan bir ekip arkadaşı ile anında çift yönlü işbirliği elde etmenizi sağlayan bir geliştirici Visual Studio. Ekip Live Share ekip arkadaşlarınız, kendileriyle paylaştığım bir projeyi okuyabilir, gezin, düzenleyebilir ve projede hata ayıklar ve bunu sorunsuz ve güvenli bir şekilde yapar.

Ayrıca Visual Studio 2019'da bu hizmet varsayılan olarak yüklenir.

![Visual Studio 2019'daki Live Share özelliğini gösteren animasyon](media/vs-2019/live-share.gif "Visual Studio 2019 Live Share işbirliği özelliği.")

Daha fazla bilgi için [Visual Studio Live Share](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) kod incelemeleri ve etkileşimli eğitim blog gönderisi için Live Share ve [Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) blog gönderisine bakın.

### <a name="integrated-code-reviews"></a>Tümleşik kod incelemeleri

Visual Studio 2019 ile birlikte kullanmak üzere indir Visual Studio tanıtacak. Bu yeni uzantıyla, takımdan ayrılmadan çekme isteklerini gözden geçir, çalıştır ve hatta hata Visual Studio. Hem GitHub hem de Azure DevOps destekliyoruz.

   ![Visual Studio 2019'da yeni Çekme İstekleri uzantısının ekran görüntüsü](media/vs-2019/pr-experience.png "Visual Studio 2019 ' de yeni çekme Istekleri uzantısı.")

Daha fazla bilgi için Çekme [İstekleri uzantısının Visual Studio kod incelemeleri](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) blog gönderisi'ne bakın.

## <a name="debug"></a>Hata Ayıklama

Hata ayıklarken hassas hedefleme ile nasıl sıfırlayabilirsiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu izleyin. <br><br>*Video uzunluğu: 3,54 dakika*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Performans kazançları

Bir kerelik özel C++ veri kesme noktalarına sahip ve bunları .NET Core uygulamaları için uyarlamış olduk.

   ![2019'da hata ayıklama veri kesme Visual Studio gösteren animasyon](media/vs-2019/debug-data-breakpoints.gif "Visual Studio 2019'daki hata ayıklama veri kesme noktaları.")

Bu nedenle, C++ veya .NET Core'da kod yazmadan önce veri kesme noktaları yalnızca normal kesme noktaları yerleştirmeye iyi bir alternatif olabilir. Veri kesme noktaları, genel bir nesnenin nerede değiştiril olduğunu, listeye ekli veya listeden kaldırıldığı yeri bulma gibi senaryolar için de harikadır.

Ayrıca, büyük uygulamalar geliştiren bir C++ geliştiricisiyseniz Visual Studio 2019' da, bellekle ilgili sorunlar yaşamadan bu uygulamalarda hata ayıklamaya olanak sağlayan bir yordamdan semboller yaptı.

### <a name="search-while-debugging"></a>Hata ayıklarken ara

Büyük olasılıkla bir değer kümesi arasında bir dize izleme penceresi arayarak daha önce vardı. Visual Studio 2019 ' de, aradığınız nesneleri ve değerleri bulmanıza yardımcı olmak için Watch, Yereller ve oto pencerelerinde arama ekledik.

   ![Visual Studio 2019 'de hata ayıklama arama penceresini gösteren bir animasyon](media/vs-2019/debug-window-search.gif "Visual Studio 2019'da hata ayıklama arama penceresi.")

Ayrıca, bir değerin Izleme, Yereller ve oto pencereleri içinde nasıl görüntüleneceğini de biçimlendirebilirsiniz. Herhangi bir Windows 'daki öğelerden birini (çift tıklayarak) seçin ve olası biçim Belirticilerinin açılan listesine erişmek için bir virgül (",") ekleyin (her biri amaçlanan efektinin açıklamasını içerir).

   ![Visual Studio 2019 ' de yeni izleme penceresi ve biçim değerleri özelliği](media/search-watch-window.png "Izleme penceresi 2019'daki yeni Visual Studio ve biçimlendir özelliği.")

Daha fazla bilgi için bkz. [Visual Studio 2019 ' de geliştirildi: Watch, oto ve Yereller Windows blog gönderide nesneleri ve özellikleri arama](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) .

### <a name="snapshot-debugger"></a>Anlık Görüntü Hata Ayıklayıcı

Tam olarak neler olduğunu görmek için, bulutta uygulamanın yürütmesinin bir anlık görüntüsünü alın. (Bu özellik yalnızca Visual Studio Enterprise ' de kullanılabilir.)

   ![Visual Studio 2019 Enterprise Snapshot Debugger gösteren bir animasyon](media/vs-2019/snapshot-debugger.gif "Snapshot Debugger 2019 Enterprise'Visual Studio'daki şirket.")

Azure VM 'de çalışan ASP.NET (çekirdek ve Masaüstü) uygulamalarını hedefleme desteği ekledik. Azure Kubernetes hizmetinde çalışan uygulamalar için de destek ekledik. Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için geçen süreyi önemli ölçüde düşürmeye yardımcı olabilir.

Daha fazla bilgi için bkz. [Snapshot Debugger sayfasını kullanarak canlı ASP.net Azure uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md) ve [giriş süresi, Visual Studio Enterprise 2019 blog gönderisi için hata ayıklama](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) .

### <a name="microsoft-edge-insider-support"></a>Microsoft Edge Insider desteği

**16,2 ' deki yenilikler**: bir JavaScript uygulamasında bir kesme noktası ayarlayabilir ve [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) tarayıcısını kullanarak bir hata ayıklama oturumu başlatabilirsiniz. Bunu yaptığınızda, Visual Studio, hata ayıklama etkinken yeni bir tarayıcı penceresi açar. Bu, daha sonra Visual Studio 'da uygulama JavaScript 'i aracılığıyla ilerlemek için kullanabilirsiniz.

   ![Tarayıcıda JavaScript kod işlemeyi gösteren ekran görüntüsü](media/vs-2019/edge-chromium-breakpoint.png "Tarayıcıda JavaScript kodu işleme.")

### <a name="pinnable-properties-tool"></a>Sabitlenebilir Özellikler aracı

**16.4'te** yeni bir özellik: Yeni Sabitlenebilir Özellikler aracıyla hata ayıklarken nesneleri özelliklerine göre tanımlamak artık daha kolay. İmleci İzleme, Otomatikler ve Yereller pencerelerinin hata ayıklayıcısı penceresinde görüntülemek istediğiniz bir özelliğin üzerine gelmeniz, sabitleme simgesini seçmeniz ve pencerenin en üstünde gördüğünüz bilgileri hemen görmeniz gerekir!

   ![Sabitlenebilir Özellikler aracını kullanarak hata ayıklayıcısında Visual Studio sabitlemeyi gösteren animasyon](media/vs-2019/debugger-pinnable-properties.gif "Sabitlenebilir Özellikler aracını Visual Studio hata ayıklayıcısında özellikleri sabitler.")

Daha fazla bilgi için Sabitlenebilir Özellikler: Yönetilen Nesneleri Görüntüleme & Hata Ayıklama [blog gönderisi'ne](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) bakın.

## <a name="whats-next"></a>Sırada ne var?

2019'Visual Studio geliştirme deneyiminizi daha da iyi hale Visual Studio yeni özelliklerle güncelleştirin. En son yeniliklerimiz hakkında daha fazla bilgi edinmek için Visual Studio [göz atabilirsiniz.](https://devblogs.microsoft.com/visualstudio/) Önizlemede bugüne kadar yayımlanaların bir kaydı için Önizleme Sürüm [Notları'ne göz atabilirsiniz.](/visualstudio/releases/2019/release-notes-preview/) Bir sonraki sürüme neleri yayınlayacağız? listesi için yol [haritasına Visual Studio bakın.](/visualstudio/productinfo/vs-roadmap)

Bu arada, şu anda çalışmalara devam ediyor olan yeni bir özellik de burada ve burada yer alan yeni bir özelliktir.

- **Visual Studio 2019'da geliştirilmiş Git deneyimi (Önizleme)**

   Yeni Git sürüm denetimi deneyimi artık Visual Studio 2019 sürüm [16.8'de](/visualstudio/releases/2019/release-notes/)varsayılan olarak açık olsa da, en yeni Önizleme sürümünde deneyimi geliştirmek için özellikler eklemeye devam edeceğiz.

   Daha fazla bilgi için [bkz. Sürüm denetimi Visual Studio.](/visualstudio/version-control/)

Visual Studio 2019'un Önizleme sürümü ve denemek istediğiniz indirme bağlantısı hakkında daha fazla bilgi için &mdash; &mdash; bkz. **[Visual Studio Preview.](https://aka.ms/vspreview/)**

> [!TIP]
> Sonraki sürüm hakkında daha fazla bilgi edinmek için **[Visual Studio 2022](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)** blog gönderisi'ne bakın.

## <a name="give-us-feedback"></a>Geri bildirimde bulunun

Neden Visual Studio ekibine geri bildirim gönderebilirsiniz? Çünkü müşteri geri bildirimlerini ciddiye alıyoruz. Bu, yapacaklarının büyük bir fazlasını yapar.

* Visual Studio 'Yu nasıl geliştirebileceğimizi gösteren bir öneride bulunmak isterseniz, [bir özellik öner](suggest-a-feature.md) aracını kullanarak bunu yapabilirsiniz.

* Visual Studio 'Nun yanıt vermeyi, kilitlenmeleri veya diğer performans sorunlarını durdurduğu bir sorunla karşılaşırsanız [sorun bildir](how-to-report-a-problem-with-visual-studio.md) aracını kullanarak yeniden üretme adımlarını ve destekleyici dosyaları bizimle paylaşabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio docs 'taki yenilikler](whats-new-visual-studio-docs.md)
* [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes/)
* [Mac için Visual Studio 2019 sürüm notları](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Visual Studio 2019 SDK 'daki yenilikler](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Visual Studio 2017’deki C++ yenilikleri](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio/)
* [C# 9,0 yenilikleri](/dotnet/csharp/whats-new/csharp-9)
* [.NET 5’teki yenilikler](/dotnet/core/dotnet-five)
* [.NET Framework yenilikleri](/dotnet/framework/whats-new/)
* [Microsoft derleme Konferansı](https://www.microsoft.com/build)
* [Microsoft Ignite konferansı](https://www.microsoft.com/ignite)
