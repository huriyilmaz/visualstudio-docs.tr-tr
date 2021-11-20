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
ms.openlocfilehash: d1736de4811873e6ec081a7f89e69321a50c72b5
ms.sourcegitcommit: 932cf0f653c6258b73f42102d134cbaf50b8f20c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "132880109"
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

   ![Visual Studio 2019 ' de yeni arama deneyimine yönelik bir animasyon](media/vs-2019/new-search-feature.gif "Visual Studio 2019 ' deki yeni arama deneyimi.")

Yeni benzer arama mantığı, yazım hatalarını ne olursa olsun ihtiyacınız olan her şeyi bulur. Bu nedenle, komutları, ayarları, belgeleri veya diğer yararlı şeyleri arıyorsanız, yeni arama özelliği aradığınızı bulmayı kolaylaştırır.

daha fazla bilgi için bkz. [Visual Studio arama kullanma](visual-studio-search.md).

#### <a name="intelligent-search-service"></a>Akıllı arama hizmeti

**16,9 ' de yeni**: bulut destekli teknoloji, yapay zeka ve makine öğrenimi kullanarak arama sonuçlarımızı geliştirdik. artık Visual Studio arama yalnızca daha ilgili sonuçlar üretmiyor, ancak aynı zamanda ürün özelliklerini daha kolay bulmanıza de yardımcı olabilir.

daha fazla bilgi için bkz. [akıllı Visual Studio arama hizmeti](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) blog gönderisi.

### <a name="refactorings"></a>Yeniden düzenlemeler

C# ' de kodunuzun düzenlenmesine daha kolay olan çok sayıda yeni ve son derece yararlı yeniden düzenlemeler vardır. Hafif ampulde öneriler olarak görünür ve üyeleri arabirim veya temel sınıfa taşıma, ad alanlarını klasör yapısıyla eşleşecek şekilde ayarlama, Foreach-döngülerini LINQ Sorgularına dönüştürme ve daha fazlasını içeren eylemleri içerir.

   ![Visual Studio 2019 ' de yeniden düzenlemeler deneyiminin animasyonu](media/vs-2019/refactorings.gif "Visual Studio 2019 ' deki yeniden düzenlemeler deneyimi.")

Yalnızca **CTRL +** tuşlarına basarak yeniden düzenlemeler çağırın. ve gerçekleştirmek istediğiniz eylemi seçin.

### <a name="intellicode"></a>IntelliCode

[Visual Studio ıntellicode](/visualstudio/intellicode/) , yapay zeka (aı) kullanarak yazılım geliştirme çabalarınızı geliştirir. ıntellicode, GitHub üzerinde &mdash; her biri 100 yıldız ile &mdash; , önerilerini oluşturmak için 2.000 açık kaynaklı projeler arasında gezinir.

![Visual Studio 2019 ' de ıntellicode animasyonu](media/vs-2019/IntelliCode.gif "Visual Studio 2019 ' de ıntellicode.")

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

   ![Visual Studio 2019 ' de yeni kod temizleme denetiminin ekran görüntüsü](media/vs-2019/code-cleanup-profile.png "Visual Studio 2019 ' deki yeni kod temizleme denetimi.")

Ayrıca, armanesnelerin koleksiyonlarını bir profil olarak kaydedebilirsiniz. Örneğin, kodlarken sıkça uyguladığınız bir dizi hedeflenmiş sabit listesi varsa ve daha sonra bir kod incelemesinin önüne uygulamak üzere daha kapsamlı bir sabit listesi varsa, profilleri bu farklı görevleri ele almak için yapılandırabilirsiniz.

   ![Visual Studio 2019 ' de kod temizleme denetimini yapılandırma ekran görüntüsü](media/vs-2019/code-cleanup-profile-configure.png "Visual Studio 2019 ' deki kod temizleme denetimini yapılandır.")

### <a name="per-monitor-aware-pma-rendering"></a>Monitör başına duyarlı (PMA) işleme

farklı görüntü ölçeği faktörlerine sahip olan veya ana cihazınızdan farklı olan görüntüleme ölçeği faktörleri olan bir makineye uzaktan bağlanmak için kullanılan izleyicileri kullanıyorsanız, Visual Studio bulanık göründüğünü veya yanlış ölçekte işlediğini fark edebilirsiniz.

Visual Studio 2019 ' nin yayınlanmasıyla birlikte, izleme için duyarlı (pma) bir uygulama Visual Studio veriyoruz. şimdi, kullandığınız görüntü ölçeği faktörlerine bakılmaksızın Visual Studio doğru şekilde işler.

   ![Visual Studio 2019 ' de monitöre duyarlı (pma) işleme başına](media/vs-2019/pma-dpi-scaling.png "Visual Studio 2019 ' de monitör tanıma (pma) işleme başına.")

daha fazla bilgi için, [Visual Studio 2019 blog gönderisinde daha iyi bir çoklu izleme deneyimine](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) bakın.

### <a name="test-explorer"></a>Test Gezgini

**16,2 ' de yeni**: Test Gezgini ' ni, büyük test kümelerinin daha iyi işlenmesini, daha kolay filtrelenmesini, daha keşfedilebilir komutları, sekmeli çalma listesi görünümlerini ve özelleştirilebilir sütunları, hangi test bilgilerinin görüntülendiğini ayarlamanıza olanak sağlayacak şekilde güncelleştirdik.

   ![Test Gezgininde Kullanıcı arabirimi geliştirmelerini gösteren ekran görüntüsü](media/vs-2019/test-explorer-ui.png "Test Gezgini 'ndeki Kullanıcı arabirimi geliştirmeleri.")

### <a name="net-core"></a>.NET Core

**16,3 ' de yeni** eklendi: .net Core 3,0 için destek ekledik. Platformlar arası, açık kaynak &mdash; ve Microsoft tarafından tam olarak desteklenmektedir.

Daha fazla bilgi için bkz. [.NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) blog gönderisi duyurusu.

## <a name="collaborate"></a>İşbirliği

Sorunları çözmek için nasıl ekip sağlayabileceğiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 4,22 dakika*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Git-ilk iş akışı

Visual Studio 2019 ' i açtığınızda yeni başlangıç penceresi olduğunu fark edersiniz.

   ![Visual Studio 2019 ' deki yeni başlangıç penceresinin ekran görüntüsü](media/vs-2019/start-window-dark.png "Visual Studio 2019 ' deki yeni başlangıç penceresi.")

Başlangıç penceresi size hızlı bir şekilde kod almanızı sağlamak için çeşitli seçenekler sunar. Önce bir depodan kod kopyalama veya kullanıma alma seçeneğini yerleştirdik.

   ![Visual Studio 2019 ' de ' Git-first ' deneyiminin animasyonu](media/vs-2019/git-first.gif "Visual Studio 2019 ' deki ' Git-first ' deneyimi.")

Başlangıç penceresi ayrıca bir proje veya çözüm açma, yerel bir klasör açma veya yeni bir proje oluşturma seçeneklerini de içerir.

daha fazla bilgi için bkz. [Get to code: yeni Visual Studio başlat pencere blog gönderisini nasıl tasarlıyoruz](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) .

### <a name="git-productivity"></a>Git verimliliği

**16,8 ' deki yenilikler**: Git artık Visual Studio 2019 ' de varsayılan sürüm denetimi deneyimidir. Son iki yayın sırasında geri bildirimlerinizi temel alarak, özellik kümesini geliştirdik ve bu, yineleyecek şekilde serbest bırakıldı. Yeni deneyim artık herkes için varsayılan olarak açıktır. Yeni Git menüsünde depoları kopyalayabilir, oluşturabilir veya açabilirsiniz. Kodunuzda değişiklikleri yürütmek ve göndermek, dalları yönetmek, uzak depolarınızda güncel kalmak ve birleştirme çakışmalarını çözmek için tümleşik git araç pencerelerini kullanın.

daha fazla bilgi için Visual Studio sayfasındaki [Git deneyimine](../version-control/git-with-visual-studio.md) bakın.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) , bir kod temeli ve bağlamını bir ekiple paylaşmanıza ve doğrudan Visual Studio içinden doğrudan çift yönlü işbirliği yapmanıza olanak tanıyan bir geliştirici hizmetidir. Live Share, bir ekip mate kendileriyle paylaştığınız bir projeyi okuyabilir, gezinmiş, düzenleyebilir ve hata ayıklamanızı ve sorunsuz ve güvenli bir şekilde yapabilmesini sağlayabilir.

Visual Studio 2019 ile, bu hizmet varsayılan olarak yüklenir.

![Visual Studio 2019 ' de Live Share işbirliği özelliğini gösteren bir animasyon](media/vs-2019/live-share.gif "Visual Studio 2019 ' deki Live Share işbirliği özelliği.")

daha fazla bilgi için bkz. [gerçek zamanlı kod incelemeleri ve etkileşimli eğitim](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) blog gönderisi ve [Live Share artık Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) blog gönderisine dahil Visual Studio Live Share.

### <a name="integrated-code-reviews"></a>Tümleşik kod İncelemeleri

Visual Studio 2019 ile kullanmak üzere indirebileceğiniz yeni bir uzantı sunuyoruz. Bu yeni uzantıyla birlikte Visual Studio olmadan takımınızdan çekme isteklerini gözden geçirebilir, çalıştırabilir ve hatta hata ayıklayabilirsiniz. GitHub ve Azure DevOps depolarındaki kodu destekliyoruz.

   ![Visual Studio 2019 ' de yeni çekme istekleri uzantısının ekran görüntüsü](media/vs-2019/pr-experience.png "Visual Studio 2019 ' deki yeni çekme istekleri uzantısı.")

daha fazla bilgi için [Visual Studio çekme istekleri uzantısı blog gönderisini kullanarak kod incelemelerine](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) bakın.

## <a name="debug"></a>Hata Ayıklama

Hata ayıklarken kesin hedefleme ile nasıl tam olarak izin sağlayacağınız hakkında daha fazla bilgi edinmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 3,54 dakika*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Performans kazançları

Bir kez özel C++ veri kesme noktası aldık ve bunları .NET Core uygulamaları için uyartık.

   ![Visual Studio 2019 ' de hata ayıklama verisi kesme noktalarını gösteren bir animasyon](media/vs-2019/debug-data-breakpoints.gif "Visual Studio 2019 ' deki hata ayıklama verileri kesme noktaları.")

C++ veya .NET Core 'da kodlama yapıp etmeksizin, veri kesme noktaları yalnızca normal kesme noktaları yerleştirilerek iyi bir alternatif olabilir. Veri kesme noktaları, bir genel nesnenin nerede değiştirildiğini veya bir listeden eklendiğini veya kaldırılacağını bulma gibi senaryolar için de idealdir.

büyük uygulamalar geliştiren bir C++ geliştiricisiyseniz, Visual Studio 2019, bu uygulamalarda, bellekle ilgili sorunlarla karşılaşmadan bu uygulamalarda hata ayıklamanıza olanak sağlayan, sembolleri proc 'dan dışarı yaptı.

### <a name="search-while-debugging"></a>Hata ayıklarken ara

Büyük olasılıkla bir değer kümesi arasında bir dize izleme penceresi arayarak daha önce vardı. Visual Studio 2019 ' de, aradığınız nesneleri ve değerleri bulmanıza yardımcı olmak için Watch, yereller ve oto pencerelerinde arama ekledik.

   ![Visual Studio 2019 ' de hata ayıklama arama penceresini gösteren bir animasyon](media/vs-2019/debug-window-search.gif "Visual Studio 2019 ' deki hata ayıklama arama penceresi.")

Ayrıca, bir değerin Izleme, Yereller ve oto pencereleri içinde nasıl görüntüleneceğini de biçimlendirebilirsiniz. Herhangi bir Windows 'daki öğelerden birini (çift tıklayarak) seçin ve olası biçim Belirticilerinin açılan listesine erişmek için bir virgül (",") ekleyin (her biri amaçlanan efektinin açıklamasını içerir).

   ![Visual Studio 2019 ' deki yeni izleme penceresi ve biçim değerleri özelliği](media/search-watch-window.png "Visual Studio 2019 ' deki yeni izleme penceresi ve biçim değerleri özelliği.")

daha fazla bilgi için bkz. [Visual Studio 2019 ' de geliştirildi: izleme, oto ve yereller Windows blog gönderinizde nesneleri ve özellikleri arama](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) .

### <a name="snapshot-debugger"></a>Anlık Görüntü Hata Ayıklayıcı

Tam olarak neler olduğunu görmek için, bulutta uygulamanın yürütmesinin bir anlık görüntüsünü alın. (bu özellik yalnızca Visual Studio Enterprise ' de kullanılabilir.)

   ![Visual Studio 2019 ' de Snapshot Debugger gösteren bir animasyon Enterprise](media/vs-2019/snapshot-debugger.gif "Visual Studio 2019 Enterprise Snapshot Debugger.")

Azure VM 'de çalışan ASP.NET (çekirdek ve masaüstü) uygulamalarını hedeflemek için destek ekledik. Azure Kubernetes hizmetinde çalışan uygulamalar için de destek ekledik. Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için geçen süreyi önemli ölçüde düşürmeye yardımcı olabilir.

daha fazla bilgi için bkz. [Snapshot Debugger sayfasını kullanarak Azure uygulamaları ASP.NET hata ayıklama](../debugger/debug-live-azure-applications.md) ve [giriş süresi Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) blog gönderisine katılın.

### <a name="microsoft-edge-insider-support"></a>Microsoft Edge Insider desteği

**16,2 ' de yeni**: bir JavaScript uygulamasında bir kesme noktası ayarlayabilir ve [Microsoft Edge ınsider](https://www.microsoftedgeinsider.com/) tarayıcısını kullanarak bir hata ayıklama oturumu başlatabilirsiniz. bunu yaptığınızda Visual Studio, hata ayıklama etkinken yeni bir tarayıcı penceresi açar ve bu, Visual Studio içindeki uygulama JavaScript 'i adım adım ilerlemek için kullanabilirsiniz.

   ![Tarayıcıda JavaScript kod işlemeyi gösteren ekran görüntüsü](media/vs-2019/edge-chromium-breakpoint.png "Tarayıcıda JavaScript kod işleme.")

### <a name="pinnable-properties-tool"></a>Pinleştir Özellikler aracı

**16,4 ' de yeni**: artık, yeni pinalgıladığında Özellikler aracıyla hata ayıklarken nesneleri özelliklerine göre belirlemek daha kolay. İmleci, gözcü, oto ve Yereller pencerelerinin hata ayıklayıcı penceresinde görüntülemek istediğiniz bir özelliğin üzerine getirin, PIN simgesini seçin ve pencerenin en üstünde aradığınız bilgileri hemen görün!

   ![Visual Studio hata ayıklayıcıdaki özelliklerin, pindlik özellikleri aracını kullanarak nasıl sabitlenebilmesini gösteren bir animasyon](media/vs-2019/debugger-pinnable-properties.gif "Visual Studio hata ayıklayıcıdaki özellikleri, pindlik özellikleri aracını kullanarak sabitleyin.")

Daha fazla bilgi için bkz. [Pintuma özellikleri: Debug & yönetilen nesneleri blog GÖNDERINIZDE görüntüleme](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) .

## <a name="whats-next"></a>Sırada ne var?

Visual Studio genellikle geliştirme deneyiminizi daha da iyi hale getirebileceğiniz yeni özelliklerle güncelleştiririz. en son yeniliklerimiz hakkında daha fazla bilgi edinmek için [Visual Studio bloguna](https://devblogs.microsoft.com/visualstudio/)göz atın. Önizleme tarihine kadar yayımladığımız bir kayıt için [Önizleme sürüm notlarına](/visualstudio/releases/2019/release-notes-preview/)göz atın. ayrıca, daha sonra yayınlanmasını planladığımızı bir liste için [Visual Studio yol haritasını](/visualstudio/productinfo/vs-roadmap)inceleyin.

Bu sırada şu anda işte geçerli olan çalışmalar şunlardır:

- **Visual Studio 2019 ' de geliştirilmiş Git deneyimi**

   Git sürüm denetimi aracı Visual Studio 2019 [sürüm 16,8](/visualstudio/releases/2019/release-notes-history/) ve sonraki sürümlerde varsayılan deneyimse de, deneyimi Visual Studio 2019, [sürüm 16,11](/visualstudio/releases/2019/release-notes-preview/)' in en yeni sürümünde geliştirmeye yönelik özellikler eklemeye devam ediyoruz.

   daha fazla bilgi için Visual Studio sayfasındaki [sürüm denetimine](/visualstudio/version-control/) bakın.

- **Visual Studio 2022 artık kullanılabilir**

    en yeni sürümümüzü [Visual Studio 2022](/visualstudio/releases/2022/release-notes/) daha hızlıdır, daha ulaşılabilir ve daha hafif. ve ilk kez Visual Studio 64 bit olur.

    bir indirme bağlantısı ve daha fazla bilgi için, [Visual Studio 2022 vision](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/) blog gönderisine ve [**Visual Studio 2022 Preview 3 ' te artık kullanılabilir**](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/) blog gönderisine bakın.

## <a name="give-us-feedback"></a>Geri bildirimde bulunun

Visual Studio ekibine neden geri bildirim gönderilsin? Müşteri geri bildirimlerine önem veriyoruz. Yaptığımız kadar çok şey vardır.

* Visual Studio nasıl geliştirebileceğimizi gösteren bir öneride bulunmak isterseniz, [özellik öner](suggest-a-feature.md) aracını kullanarak bunu yapabilirsiniz.

* Visual Studio yanıt vermeyi, kilitlenmeleri veya diğer performans sorunlarını durdurduğu bir sorunla karşılaşırsanız, [sorun bildir](how-to-report-a-problem-with-visual-studio.md) aracını kullanarak yeniden üretme adımlarını ve destekleyici dosyaları bizimle paylaşabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2022 ' deki yenilikler (önizleme)](whats-new-visual-studio-2022.md)
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
