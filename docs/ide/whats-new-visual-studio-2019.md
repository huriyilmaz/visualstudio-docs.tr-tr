---
title: Visual Studio 2019’daki yenilikler
titleSuffix: ''
description: Visual Studio 2019'daki yeni özellikler hakkında bilgi edinin.
ms.date: 03/16/2020
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: bf251ade250a466cefe02db6f5cc709a0c18837b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79437737"
---
# <a name="whats-new-in-visual-studio-2019"></a>Visual Studio 2019’daki yenilikler

**[16.5 sürümü](/visualstudio/releases/2019/release-notes/) için güncellendi**

>[!div class="button"]
>[Visual Studio 2019’u İndirin](https://visualstudio.microsoft.com/downloads)

Visual Studio 2019 ile, herhangi bir geliştirici, herhangi bir uygulama ve herhangi bir platform için sınıfının en iyisi araçlar alabilirsiniz. Visual Studio'yu ilk kez kullanıyor olun, yıllardır kullanıyor olun, bu yeni sürümde beğenecek çok şey var!

İşte yeniliklerin üst düzey bir özeti:

* **[Geliştirme](#develop)**: Gelişmiş performans, anlık kod temizleme ve daha iyi arama sonuçları yla odaklanmış ve üretken kalın.
* **[İşbirliği](#collaborate)**: Visual Studio'da git-ilk iş akışı, gerçek zamanlı düzenleme ve hata ayıklama ve kod incelemeleri yoluyla doğal işbirliğinin keyfini çıkarın.
* **[Hata Ayıklama](#debug)**: Belirli değerleri vurgulayın ve gidin, bellek kullanımını optimize edin ve uygulamanızın yürütülmesinin otomatik anlık görüntülerini alın.

Bu sürümde yeni olan her şeyin tam listesi için [sürüm notlarına](/visualstudio/releases/2019/release-notes/)bakın.

## <a name="develop"></a>Geliştirme

Yeni özelliklerle nasıl zaman kazanabileceğiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 3.00 dakika*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Geliştirilmiş arama

Eskiden Hızlı Başlatma olarak bilinen yeni arama deneyimimiz daha hızlı ve daha etkilidir. Şimdi, siz yazarken arama sonuçları dinamik olarak görünür. Ayrıca, arama sonuçları genellikle komutlar için klavye kısayollarını içerebilir, böylece ileride kullanmak üzere daha kolay ezberleyebilirsiniz.

   ![Visual Studio 2019'daki yeni arama deneyiminin animasyonu](media/vs-2019/new-search-feature.gif)

Yeni bulanık arama mantığı, yazım hataları ne olursa olsun, ihtiyacınız olan her şeyi bulur. Bu nedenle, komutlar, ayarlar, belgeler veya diğer yararlı şeyler arıyorsanız, yeni arama özelliği aradığınızı bulmanızı kolaylaştırır.

### <a name="refactorings"></a>Refactorings

C#'da kodunuzu düzenlemeyi kolaylaştıran birçok yeni ve son derece kullanışlı yeniden faktörleme vardır. Bunlar ampulde öneri olarak gösterir ve üyeleri arabirim veya taban sınıfa taşıma, ad alanlarını klasör yapısıyla eşleşecek şekilde ayarlama, foreach döngülerini Linq sorgularına dönüştürme ve daha fazlası gibi eylemleri içerir.

   ![Visual Studio 2019'da refactorings deneyiminin animasyonu](media/vs-2019/refactorings.gif)

**Ctrl+** tuşuna basarak refactoringleri çağırmanız yeterlidir. ve yapmak istediğiniz eylemi seçmek.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) yapay zeka (AI) kullanarak yazılım geliştirme çabalarınızı geliştirir. IntelliCode, github'da&mdash;2.000 açık kaynak projesinde her&mdash;biri 100'den fazla yıldızla kendi önerilerini oluşturmak için eğitmektedir.

![Visual Studio 2019'da IntelliCode animasyonu](media/vs-2019/IntelliCode.gif)

Visual Studio IntelliCode'un üretkenliğinizi artırmanıza yardımcı olabileceği birkaç yol şunlardır:

* İçerime duyarlı kod tamamlamaları sağlama
* Geliştiricileri, takımlarının desen ve stillerine uymaları için yönlendirin
* Yakalanması zor kod sorunlarını bulma
* Gerçekten önemli alanlara dikkat çekerek kod incelemelerine odaklanın

IntelliCode'u Visual Studio'nun uzantısı olarak ilk öngösterimde sadece C# olarak destekledik. Şimdi, **16.1 yeni**, biz C # ve XAML için destek ekledik "in-the-box". (Ancak C++ ve TypeScript/JavaScript desteği hala önizlemededir.)

C# kullanıyorsanız, kendi kodunuzla özel bir model yetiştirme özelliğini de ekledik.

IntelliCode hakkında daha fazla bilgi için, [IntelliCode'un genel kullanılabilirliğini duyurmaya bakın artı sneak peek](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) ve Code daha [fazlası, Visual Studio IntelliCode blog gönderileriyle daha az kaydırın.](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/)

### <a name="code-cleanup"></a>Kod temizleme

Yeni bir belge sistem durumu göstergesi ile eşleştirilmiş yeni bir kod temizleme komutudur. Bu yeni komutu kullanarak bir düğmeyi tıklatarak hem uyarıları hem de önerileri belirleyebilir ve düzeltebilirsiniz.

Temizleme kodu biçimlendirecek ve [geçerli ayarlar](code-styles-and-code-cleanup.md) ve [.editorconfig dosyaları](create-portable-custom-editor-options.md)tarafından önerilen herhangi bir kod düzeltmeleri uygulayacak.

   ![Visual Studio 2019'da yeni kod temizleme denetiminin ekran görüntüsü](media/vs-2019/code-cleanup-profile.png)

Ayrıca, düzeltici koleksiyonlarını profil olarak da kaydedebilirsiniz. Örneğin, kod larken sık sık uyguladığınız küçük bir hedefli sabitleyici kümeniz varsa ve ardından kod gözden geçirmeden önce uygulayacak başka kapsamlı bir sabitleyici kümeniz varsa, profilleri bu farklı görevleri ele alacak şekilde yapılandırabilirsiniz.

   ![Visual Studio 2019'da yapılandırma kodu temizleme denetiminin ekran görüntüsü](media/vs-2019/code-cleanup-profile-configure.png)

### <a name="per-monitor-aware-pma-rendering"></a>Monitör başına farkında (PMA) oluşturma

Farklı ekran ölçeği etkenleriyle yapılandırılan monitörler kullanıyorsanız veya ana aygıtınızdan farklı ekran ölçeği faktörlerine sahip bir makineye uzaktan bağlanıyorsanız, Visual Studio'nun bulanık göründüğünü veya yanlış ölçekte görüntülendiğini fark edebilirsiniz.

Visual Studio 2019'un piyasaya sürülmesiyle Visual Studio'yu monitör başına bilinçli (PMA) bir uygulama haline getiriyoruz. Şimdi, Visual Studio kullandığınız ekran ölçeği faktörleri ne olursa olsun doğru işler.

   ![Visual Studio 2019'da monitör başına farkında (PMA) oluşturma](media/vs-2019/pma-dpi-scaling.png)

Daha fazla bilgi için [Visual Studio 2019 blog gönderisiyle daha iyi çoklu monitör deneyimine](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) bakın.

### <a name="test-explorer"></a>Test Gezgini

**16.2'de Yeni**: Test Gezgini'ni, büyük test kümelerini, daha kolay filtreleme, daha kolay keşfedilebilir komutları, sekmeli çalma listesi görünümlerini ve hangi test bilgilerinin görüntülendiğini hassas bir şekilde ayarlamanızı sağlayan özelleştirilebilir sütunları daha iyi işlemek için güncelledik.

   ![Test Gezgini'ndeki kullanıcı arabirimi iyileştirmelerini gösteren bir ekran görüntüsü](media/vs-2019/test-explorer-ui.png)

### <a name="net-core"></a>.NET Core

**16.3'te yeni**: .NET Core 3.0 desteğini de dahil ettik. Çapraz platform, açık&mdash;kaynak ve tamamen Microsoft tarafından desteklenir.

Daha fazla bilgi için [Duyuru .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) blog gönderisi için bkz.

## <a name="collaborate"></a>İşbirliği

Sorunları çözmek için nasıl takım olabileceğiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu izleyin. <br><br>*Video uzunluğu: 4.22 dakika*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Git-ilk iş akışı

Visual Studio 2019'u açtığınızda fark edeceksiniz ki yeni başlangıç penceresi.

   ![Visual Studio 2019'da yeni başlangıç penceresinin ekran görüntüsü](media/vs-2019/start-window-dark.png)

Başlangıç penceresi, hızlı bir şekilde kod lamanızı sağlamak için çeşitli seçenekler sunar. Önce bir repodan kodu klonlama veya kontrol etme seçeneğini yerleştirdik.

   ![Visual Studio 2019'da 'Git-first' deneyiminin animasyonu](media/vs-2019/git-first.gif)

Başlangıç penceresi, proje veya çözüm açmak, yerel bir klasör açmak veya yeni bir proje oluşturmak için seçenekler de içerir.

Daha fazla bilgi [için koda al: Yeni Visual Studio başlangıç penceresi blog gönderisini nasıl tasarladık.](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/)

### <a name="live-share"></a>Live Share

[Visual Studio Live Share,](https://visualstudio.microsoft.com/services/live-share/) bir kod tabanını ve içeriğini bir takım arkadaşıyla paylaşmanızı ve doğrudan Visual Studio içinden anında çift yönlü işbirliği elde etmenizi sağlayan bir geliştirici hizmetidir. Live Share ile, bir ekip arkadaşı onlarla paylaştığınız bir projeyi okuyabilir, gezinebilir, düzeltebilir ve hata ayıklayabilir ve sorunsuz ve güvenli bir şekilde yapabilir.

Visual Studio 2019 ile bu hizmet varsayılan olarak yüklenir.

![Visual Studio 2019'da Live Share işbirliği özelliğini gösteren animasyon](media/vs-2019/live-share.gif)

Daha fazla bilgi [için visual-time kod incelemeleri ve etkileşimli eğitim](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) blog gönderisi için Visual Studio Live Share'e ve [Visual Studio 2019 blog gönderisiyle birlikte yer alan Live Share'e](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) bakın.

### <a name="integrated-code-reviews"></a>Entegre kod incelemeleri

Visual Studio 2019 ile indirmek için indirebileceğiniz yeni bir uzantı yı sıyoruz. Bu yeni uzantı yla Visual Studio'dan ayrılmadan ekibinizden gelen çekme isteklerini inceleyebilir, çalıştırabilir ve hatta hata ayıklayabilirsiniz. Hem GitHub hem de Azure DevOps depolarında kodu destekliyoruz.

   ![Visual Studio 2019'da yeni başlangıç penceresinin ekran görüntüsü](media/vs-2019/pr-experience.png)

Daha fazla bilgi için [Visual Studio Pull Requests uzantılı blog gönderisini kullanarak Kod incelemelerini](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) görün.

## <a name="debug"></a>Hata ayıklama

Hata ayıklama sırasında hassas hedeflemeile nasıl sıfırlayabildiğiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 3.54 dakika*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Performans kazançları

Bir zamanlar özel olan C++ veri kesme noktalarını aldık ve .NET Core uygulamalarına uyarladık.

   ![Visual Studio 2019'da hata ayıklama veri kesme noktalarını gösteren animasyon](media/vs-2019/debug-data-breakpoints.gif)

İster C++ veya .NET Core'da kodlarken, veri kesme noktaları yalnızca normal kesme noktaları yerleştirmek için iyi bir alternatif olabilir. Veri kesme noktaları, genel bir nesnenin değiştirildiği veya bir listeden eklendiği veya kaldırıldığı nı bulma gibi senaryolar için de harikadır.

Ve büyük uygulamalar geliştiren bir C++ geliştiricisiyseniz, Visual Studio 2019 proc'tan semboller yaptı ve bu da bellekle ilgili sorunlar yaşamadan bu uygulamaları hata ayıklamanızı sağlıyor.

### <a name="search-while-debugging"></a>Hata ayıklama sırasında arama

Muhtemelen daha önce orada bulundunuz, bir dizi değer arasında bir dize için Watch penceresinden baktınız. Visual Studio 2019'da, aradığınız nesneleri ve değerleri bulmanıza yardımcı olmak için Watch, Locals ve Autos pencerelerine arama ekledik.

   ![Visual Studio 2019'da hata ayıklama arama penceresini gösteren animasyon](media/vs-2019/debug-window-search.gif)

Ayrıca, Saat, Yerel ler ve Otomatik ler pencerelerinde bir değerin nasıl görüntüleneceğini de biçimlendirebilirsiniz.  Pencerelerden herhangi birinde öğelerden birini çift tıklatın ve her biri amaçlanan efektin açıklamasını içeren olası biçim belirteçlerinin açılır listesine erişmek için bir virgül (",") ekleyin.

   ![Visual Studio 2019'da yeni Watch penceresi ve biçim değerleri özelliği](media/search-watch-window.png)

Daha fazla bilgi için [Visual Studio 2019'da Geliştirilmiş: Watch, Autos ve Locals Windows](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) blog gönderisinde Nesneleri ve Özellikleri Ara konusuna bakın.

### <a name="snapshot-debugger"></a>Anlık Görüntü Hata Ayıklayıcı

Tam olarak neler olduğunu görmek için uygulamanızın yürütünün bulutta anlık görüntüsünü alın. (Bu özellik Visual Studio Enterprise'da kullanılabilir, yalnızca.)

   ![Visual Studio 2019 Enterprise'da Snapshot Debugger'ı gösteren animasyon](media/vs-2019/snapshot-debugger.gif)

Azure VM'de çalışan ASP.NET (Çekirdek ve masaüstü) uygulamaları hedeflemek için destek ekledik. Ayrıca, bir Azure Kubernetes Hizmetinde çalışan uygulamalar için destek ekledik. Anlık Görüntü Hata Ayıklama, üretim ortamlarında oluşan sorunları çözmek için gereken süreyi önemli ölçüde azaltmanıza yardımcı olabilir.

Daha fazla bilgi için, Snapshot Hata Ayıklama sayfasını [kullanarak Hata Ayıklama ASP.NET Azure uygulamalarına](../debugger/debug-live-azure-applications.md) ve [Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) blog gönderisini tanıtan Zaman Yolculuğu Hata Ayıklama'ya bakın.

### <a name="microsoft-edge-insider-support"></a>Microsoft Edge Insider desteği

**16.2'de Yeni**: Bir JavaScript uygulamasında bir kesme noktası ayarlayabilir ve [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) tarayıcısını kullanarak hata ayıklama oturumu başlatabilirsiniz. Bunu yaptığınızda, Visual Studio hata ayıklama etkin yeni bir tarayıcı penceresi açar, daha sonra Visual Studio içinde uygulama JavaScript üzerinden adım kullanabilirsiniz.

   ![Tarayıcıda JavaScript kod oluşturmayı gösteren ekran görüntüsü](media/vs-2019/edge-chromium-breakpoint.png)

### <a name="pinnable-properties-tool"></a>Sabitlenebilir Özellikler aracı

**16.4'te Yeni**: Şimdi, nesneleri özelliklerine göre tanımlamak, yeni Pinnable Properties aracıyla hata ayıklarken daha kolay. İmleci, Saat, Otomatik ler ve Locals pencerelerinin hata ayıklayıcı penceresinde görüntülemek istediğiniz bir özelliğin üzerinde gezin, pin simgesini seçin ve aradığınız bilgileri pencerenin üst kısmında hemen görün!

   ![Sabitlenebilir Özellikler aracını kullanarak Visual Studio hata ayıklamasında özelliklerin nasıl sabitlenebildiğini gösteren animasyon](media/vs-2019/debugger-pinnable-properties.gif)

Daha fazla bilgi için, [Sabitlenebilir Özellikler: Hata Ayıklama & Yönetilen Nesneleri SN.](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/)

## <a name="whats-next"></a>Sırada ne var?

Visual Studio 2019'u geliştirme deneyiminizi daha da iyi hale getirebilecek yeni özelliklerle sık sık güncelliyoruz. En son yeniliklerimiz hakkında daha fazla bilgi edinmek için [Visual Studio Blog'a](https://devblogs.microsoft.com/visualstudio/)göz atın. Bugüne kadar önizlemede yayımladıklarının kaydı için, [Önizleme Yayın Notları'na](/visualstudio/releases/2019/release-notes-preview/)bir göz atın. Ve bir sonraki yayınlayacağımız şeyin listesi için [Visual Studio Yol Haritası'na](/visualstudio/productinfo/vs-roadmap)bakın.

Visual Studio 2019 için başka neler inanacağını öğrenmek ister misiniz? Visual [Studio Yol Haritası'na](/visualstudio/productinfo/vs-roadmap/)bakın.

## <a name="give-us-feedback"></a>Geri bildirimde bulunun

Visual Studio ekibine neden geri bildirim göndermissin? Çünkü müşteri geri bildirimlerini ciddiye alıyoruz. Yaptığımız şeyin çoğunu kullanıyor.

* Visual Studio'yu nasıl geliştirebileceğimiz hakkında bir öneride bulunmak istiyorsanız, [bunu Özellik Öner](suggest-a-feature.md) aracını kullanarak yapabilirsiniz.

* Bir askı, kilitlenme veya başka bir performans sorunuyla karşılaşırsanız, [Sorun Bildir](how-to-report-a-problem-with-visual-studio.md) aracını kullanarak repro adımlarını ve dosyaları destekleyerek kolayca bizimle paylaşabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes/)
* [Mac sürüm notları için Visual Studio 2019](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Visual Studio 2019 SDK'daki yenilikler](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Microsoft Build konferansı](https://www.microsoft.com/build)
* [Microsoft Ignite konferansı](https://www.microsoft.com/ignite)
