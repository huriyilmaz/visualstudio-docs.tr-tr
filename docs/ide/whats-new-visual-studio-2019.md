---
title: Visual Studio 2019’daki yenilikler
titleSuffix: ''
description: Visual Studio 2019 ' deki yeni özellikler hakkında bilgi edinin.
ms.date: 03/19/2021
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
ms.openlocfilehash: 72b97b87a7edd8fdba46b755b7253af62f6de39f
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973472"
---
# <a name="whats-new-in-visual-studio-2019"></a>Visual Studio 2019’daki yenilikler

**[16,9 sürümü](/visualstudio/releases/2019/release-notes/) için güncelleştirildi**

>[!div class="button"]
>[Visual Studio 2019’u İndirin](https://visualstudio.microsoft.com/downloads)

Visual Studio 2019 ile herhangi bir geliştirici, uygulama ve herhangi bir platform için sınıfının en iyisi araçları ve hizmetleri elde edersiniz. Visual Studio 'Yu ilk kez kullanıyor veya yıllarca kullandıysanız, en son sürümümüzden hoşlanıyoruz!

İşte yenilikler ve hepsi için yüksek düzey bir üst sınır aşağıda verilmiştir:

* **[Geliştirme](#develop)**: gelişmiş performans, anlık kod temizleme ve daha iyi arama sonuçlarıyla odaklanmış ve üretken olun.
* **[İşbirliği](#collaborate)**: git-ilk iş akışı, gerçek zamanlı Düzenle ve hata ayıklama ve Visual Studio 'da kod İncelemeleri aracılığıyla doğal işbirliğinden yararlanın.
* **[Hata Ayıkla](#debug)**: belirli değerleri vurgulayın ve bu değerlere gidin, bellek kullanımını iyileştirin ve uygulamanızın yürütmesinin otomatik anlık görüntülerini alın.

Bu sürümdeki tüm yenilikleri içeren tüm liste için [sürüm notlarına](/visualstudio/releases/2019/release-notes/)bakın.

## <a name="develop"></a>Geliştirme

Yeni özelliklerle zamanı nasıl kaydedebileceğinizi öğrenmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 3,00 dakika*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>İyileştirilmiş arama

Daha önce Hızlı Başlat olarak bilinen yeni arama deneyimimiz daha hızlı ve daha etkilidir. Şimdi, yazarken arama sonuçları dinamik olarak görünür. Ve arama sonuçları genellikle komutlar için klavye kısayolları içerebilir, böylece daha sonra kullanmak üzere bunları yeniden deneyebilirsiniz.

   ![Visual Studio 2019 'de yeni arama deneyimine yönelik bir animasyon](media/vs-2019/new-search-feature.gif "Visual Studio 2019'daki yeni arama deneyimi.")

Yeni benzer arama mantığı, yazım hatalarını ne olursa olsun ihtiyacınız olan her şeyi bulur. Bu nedenle, komutları, ayarları, belgeleri veya diğer yararlı şeyleri arıyorsanız, yeni arama özelliği aradığınızı bulmayı kolaylaştırır.

Daha fazla bilgi için bkz. [Visual Studio Search kullanma](visual-studio-search.md).

#### <a name="intelligent-search-service"></a>Akıllı arama hizmeti

**16.9'daki** yeniler: Bulut destekli teknoloji, yapay zeka ve makine öğrenmesi kullanarak arama sonuçlarımızı iyileştirildik. Artık yalnızca daha ilgili sonuçlar Visual Studio arama değil, aynı zamanda ürün özelliklerini daha kolay keşfetmenize de yardımcı olabilir.

Daha fazla bilgi için Intelligent [Visual Studio arama hizmeti](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) blog gönderisi'ne bakın.

### <a name="refactorings"></a>Yeniden düzenlemeler

C# içinde kodunuzu düzenlemeyi kolaylaştıran çok sayıda yeni ve son derece kullanışlı yeniden düzenleme vardır. Bunlar ampulde öneri olarak görünür ve üyeleri arabirime veya temel sınıfa taşıma, ad alanlarını klasör yapısıyla eş olacak şekilde ayarlama, foreach döngülerini Linq sorgularına dönüştürme gibi eylemleri içerir.

   ![Visual Studio 2019'daki yeniden düzenleme deneyiminin animasyonu](media/vs-2019/refactorings.gif "Visual Studio 2019'da yeniden düzenleme deneyimi.")

Ctrl+ tuşlarına basarak yeniden **düzenlemelerini çağırmanız gerekir.** ve yapmak istediğiniz eylemi seçin.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode,](/visualstudio/intellicode/) yapay zeka (AI) kullanarak yazılım geliştirme çalışmalarınızı geliştirmektedir. IntelliCode, GitHub'da her biri 100'den fazla yıldıza sahip 2.000 açık kaynak proje üzerinde eğitimler ve &mdash; &mdash; önerilerde bulunmalıdır.

![Visual Studio 2019'da IntelliCode animasyonu](media/vs-2019/IntelliCode.gif "Visual Studio 2019'da IntelliCode.")

IntelliCode'a sahip Visual Studio üretkenliğinizi artırmanıza yardımcı olabilir:

* Bağlama göre kod tamamlamaları teslimi
* Geliştiricilere ekiplerinin desenlerine ve stillerine uymaları için yol
* Yakalanması zor kod sorunlarını bulma
* Dikkati gerçekten önemli alanlara çekerek kod incelemelerini odakla

Başlangıçta IntelliCode'ın önizlemesini yalnızca C# için uzantı olarak ilk kez Visual Studio. **16.1'de** yeni olan C# ve XAML "in-the-box" desteği ekledik. (C++ ve TypeScript/JavaScript desteği hala önizlemededir.)

Ayrıca C# kullanıyorsanız kendi kodunuz üzerinde özel model eğitebilme özelliği ekledik.

Intellicode hakkında daha fazla bilgi için bkz. [ıntellicode 'un genel kullanılabilirliğini duyuruyor](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) ve daha fazla gizli gözlem ve [kod, Visual Studio ıntellicode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) blog gönderileriyle daha az kaydırma.

### <a name="code-cleanup"></a>Kod temizleme

Yeni bir belge durumu göstergesi ile eşleştirilmiş yeni bir kod temizleme komutu. Bu yeni komutu, hem uyarıları hem de önerileri tek bir eylemle (veya bir düğmeye tıklayarak) tanımlayıp onarmak için kullanabilirsiniz.

Temizleme kodu biçimlendirir ve [geçerli ayarlar](code-styles-and-code-cleanup.md) ve [. editorconfig dosyaları](create-portable-custom-editor-options.md)tarafından önerildiği şekilde kod düzeltmelerini uygular.

   ![Visual Studio 2019 ' de yeni kod temizleme denetiminin ekran görüntüsü](media/vs-2019/code-cleanup-profile.png "Visual Studio 2019'daki yeni kod temizleme denetimi.")

Ayrıca, armanesnelerin koleksiyonlarını bir profil olarak kaydedebilirsiniz. Örneğin, kodlarken sıkça uyguladığınız bir dizi hedeflenmiş sabit listesi varsa ve daha sonra bir kod incelemesinin önüne uygulamak üzere daha kapsamlı bir sabit listesi varsa, profilleri bu farklı görevleri ele almak için yapılandırabilirsiniz.

   ![Visual Studio 2019 'de kod temizleme denetimini yapılandırma ekran görüntüsü](media/vs-2019/code-cleanup-profile-configure.png "Visual Studio 2019'da kod temizleme denetimi yapılandırma.")

### <a name="per-monitor-aware-pma-rendering"></a>Monitör başına duyarlı (PMA) işleme

Farklı görüntü ölçeği faktörlerine sahip veya ana cihazınızdan farklı görüntü ölçeği faktörleri olan bir makineye uzaktan bağlandığınızda, Visual Studio 'Nun bulanık göründüğünü veya yanlış ölçekte işlediğini fark edebilirsiniz.

Visual Studio 2019 ' in piyasaya çıkmasıyla birlikte, Visual Studio 'Yu ekran uyumlu (PMA) uygulaması olarak yapıyoruz. Artık, kullandığınız görüntü ölçeği çarpanlarından bağımsız olarak Visual Studio doğru şekilde işler.

   ![Visual Studio 2019 ' de monitöre duyarlı (PMA) işleme](media/vs-2019/pma-dpi-scaling.png "2019'da monitör başına Visual Studio (PMA) işleme.")

Daha fazla bilgi için bkz. [Visual Studio 2019 blog gönderisi Ile daha iyi çoklu izleme deneyimi](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) .

### <a name="test-explorer"></a>Test Gezgini

**16,2 ' de yeni**: Test Gezgini ' ni, büyük test kümelerinin daha iyi işlenmesini, daha kolay filtrelenmesini, daha keşfedilebilir komutları, sekmeli çalma listesi görünümlerini ve özelleştirilebilir sütunları, hangi test bilgilerinin görüntülendiğini ayarlamanıza olanak sağlayacak şekilde güncelleştirdik.

   ![Test Gezgininde Kullanıcı arabirimi geliştirmelerini gösteren ekran görüntüsü](media/vs-2019/test-explorer-ui.png "Test Gezgini'nde kullanıcı arabirimi geliştirmeleri.")

### <a name="net-core"></a>.NET Core

**16.3'te yeni:**.NET Core 3.0 desteği dahil edildi. Platformlar arası, açık kaynak &mdash; ve Microsoft tarafından tam olarak desteklenen.

Daha fazla bilgi için [.NET Core 3.0'ın announcing blog gönderisi'ne](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) bakın.

## <a name="collaborate"></a>İşbirliği

Sorunları çözmek için ekip olarak nasıl bir ekipte yer alayabilirsiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu izleyin. <br><br>*Video uzunluğu: 4,22 dakika*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Git-first iş akışı

2019'da Visual Studio yeni başlangıç penceresi olduğunu fark edeceksiniz.

   ![Visual Studio 2019'da yeni başlangıç penceresinin ekran görüntüsü](media/vs-2019/start-window-dark.png "Visual Studio 2019'daki yeni başlangıç penceresi.")

Başlangıç penceresi, hızlı bir şekilde koda başlamaya yardımcı olacak çeşitli seçenekler sunar. Öncelikle bir repodan kod kopyalama veya denetleme seçeneğini kullandık.

   ![Visual Studio 2019'da 'Git-first' deneyiminin animasyonu](media/vs-2019/git-first.gif "Visual Studio 2019'daki 'Git-first' deneyimi.")

Başlangıç penceresi ayrıca bir proje veya çözüm açma, yerel klasör açma veya yeni proje oluşturma seçeneklerini de içerir.

Daha fazla bilgi için [Koda al: Yeni kodu nasıl tasarladık? Visual Studio penceresi blog gönderisi.](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/)

### <a name="git-productivity"></a>Git üretkenliği

**16.8 sürümündeki yeni** sürüm: Git artık 2019'da varsayılan Visual Studio denetimi deneyimidir. Özellik kümesi yerleşik olarak ve son iki sürümde geri bildiriminize dayanarak bu kümeyi de temel aldık. Yeni deneyim artık herkes için varsayılan olarak açıktır. Yeni Git menüsünden depoları kopya açabilir, oluşturabilir veya açabilirsiniz. Tümleşik Git aracı pencerelerini kullanarak değişiklikleri kodunuza işip itme, dalları yönetme, uzak depolarınızı güncel kalma ve birleştirme çakışmalarını çözme.

Daha fazla bilgi için Visual Studio [sayfasındaki Git deneyimine](../version-control/git-with-visual-studio.md) bakın.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) , bir kod temeli ve bağlamını bir ekiple paylaşmanıza ve doğrudan Visual Studio içinden çift yönlü işbirliği yapmanıza olanak tanıyan bir geliştirici hizmetidir. Live Share, bir ekip Mate kendileriyle paylaştığınız bir projeyi okuyabilir, gezinmiş, düzenleyebilir ve hata ayıklamanızı ve sorunsuz ve güvenli bir şekilde yapabilmesini sağlayabilir.

Visual Studio 2019 ile bu hizmet varsayılan olarak yüklenir.

![Visual Studio 2019 ' de Live Share işbirliği özelliğini gösteren bir animasyon](media/vs-2019/live-share.gif "Live Share 2019'daki Visual Studio işbirliği özelliği.")

Daha fazla bilgi için, bkz. [gerçek zamanlı kod İncelemeleri ve etkileşimli eğitim](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) blog gönderisi ve [live share artık Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) blog gönderisine dahil Visual Studio Live Share.

### <a name="integrated-code-reviews"></a>Tümleşik kod İncelemeleri

Visual Studio 2019 ile kullanmak üzere indirebileceğiniz yeni bir uzantı sunuyoruz. Bu yeni uzantıyla, Visual Studio 'dan çıkmadan takımınızın çekme isteklerini gözden geçirebilir, çalıştırabilir ve hatta hata ayıklayabilirsiniz. Hem GitHub hem de Azure DevOps depolarındaki kodu destekliyoruz.

   ![Visual Studio 2019 ' de yeni çekme Istekleri uzantısının ekran görüntüsü](media/vs-2019/pr-experience.png "Visual Studio 2019'daki yeni Çekme İstekleri uzantısı.")

Daha fazla bilgi için [Visual Studio çekme istekleri uzantısı blog gönderisini kullanarak kod incelemelerine](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) bakın.

## <a name="debug"></a>Hata Ayıklama

Hata ayıklarken kesin hedefleme ile nasıl tam olarak izin sağlayacağınız hakkında daha fazla bilgi edinmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 3,54 dakika*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Performans kazançları

Bir kez özel C++ veri kesme noktası aldık ve bunları .NET Core uygulamaları için uyartık.

   ![Visual Studio 2019 ' de hata ayıklama veri kesme noktalarını gösteren bir animasyon](media/vs-2019/debug-data-breakpoints.gif "Visual Studio 2019'daki hata ayıklama veri kesme noktaları.")

C++ veya .NET Core 'da kodlama yapıp etmeksizin, veri kesme noktaları yalnızca normal kesme noktaları yerleştirilerek iyi bir alternatif olabilir. Veri kesme noktaları, bir genel nesnenin nerede değiştirildiğini veya bir listeden eklendiğini veya kaldırılacağını bulma gibi senaryolar için de idealdir.

Ve, büyük uygulamalar geliştiren bir C++ geliştiriciyseniz, Visual Studio 2019, bu uygulamaları bellekle ilgili sorunlarla karşılaşmadan hata ayıklamanıza olanak sağlayan bir dizi sembolü yaptı.

### <a name="search-while-debugging"></a>Hata ayıklama sırasında arama

Büyük olasılıkla daha önce bir dizeyi bir dizi izleme penceresi dizeye bakarak bu dizeye bakmıştık. Bu Visual Studio 2019'da, aramakta olduğunu nesneleri ve değerleri bulanıza yardımcı olmak için İzleme, Yereller ve Otomatikler pencerelerine arama ekledik.

   ![Visual Studio 2019'da hata ayıklama arama penceresini gösteren animasyon](media/vs-2019/debug-window-search.gif "Visual Studio 2019'da hata ayıklama arama penceresi.")

Bir değerin İzleme, Yereller ve Otomatikler pencerelerinde nasıl görüntülendiğinden de biçimlendirebilirsiniz. Herhangi bir penceredeki öğelerden birini çift tıklayarak seçin ve her biri hedeflenen etkisinin açıklamasını içeren olası biçim belirleyicilerinin açılan listesine erişmek için virgül (",") ekleyin.

   ![Visual Studio 2019'daki yeni izleme penceresi ve biçim değerleri özelliği](media/search-watch-window.png "Izleme penceresi 2019'daki yeni Visual Studio ve biçimlendir özelliği.")

Daha fazla bilgi için İzleme, Otomatikler ve Yereller Windows blog gönderisinde [Visual Studio 2019:](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) Nesne ve Özellik Arama'ya bakın.

### <a name="snapshot-debugger"></a>Anlık Görüntü Hata Ayıklayıcı

Tam olarak neler olduğunu görmek için buluttaki uygulama yürütmenin anlık görüntüsünü alın. (Bu özellik yalnızca Visual Studio Enterprise kullanılabilir.)

   ![Visual Studio 2019 Enterprise'daki Snapshot Debugger gösteren animasyon](media/vs-2019/snapshot-debugger.gif "Snapshot Debugger 2019 Enterprise Visual Studio da yer alan uygulama.")

Azure VM'sinde çalıştıran ASP.NET (Çekirdek ve masaüstü) uygulamaları hedefleme desteği ekledik. Ayrıca, bir uygulama içinde çalıştıran uygulamalar için destek Azure Kubernetes Service. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

Daha fazla bilgi için Snapshot Debugger sayfasını [kullanarak Canlı ASP.NET Azure](../debugger/debug-live-azure-applications.md) uygulamalarının hata ayıklaması sayfasına ve Visual Studio Enterprise [2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) için Zaman Yolculuğu Hata Ayıklamaya Giriş blog gönderisi'ne bakın.

### <a name="microsoft-edge-insider-support"></a>Microsoft Edge Insider desteği

**16.2'de** yeni: Bir JavaScript uygulamasında kesme noktası ayarlayabilirsiniz ve [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) tarayıcısını kullanarak bir hata ayıklama oturumu başlatabilirsiniz. Bunu yapmak için Visual Studio hata ayıklamanın etkinleştirildiğinde yeni bir tarayıcı penceresi açılır. Bu pencereyi kullanarak uygulama JavaScript'i Visual Studio.

   ![Tarayıcıda JavaScript kod işlemeyi gösteren ekran görüntüsü](media/vs-2019/edge-chromium-breakpoint.png "Tarayıcıda JavaScript kodu işleme.")

### <a name="pinnable-properties-tool"></a>Pinleştir Özellikler aracı

**16,4 ' de yeni**: artık, yeni pinalgıladığında Özellikler aracıyla hata ayıklarken nesneleri özelliklerine göre belirlemek daha kolay. İmleci, gözcü, oto ve Yereller pencerelerinin hata ayıklayıcı penceresinde görüntülemek istediğiniz bir özelliğin üzerine getirin, PIN simgesini seçin ve pencerenin en üstünde aradığınız bilgileri hemen görün!

   ![Visual Studio hata ayıklayıcısında, Pinilik özellikleri aracını kullanarak özelliklerin nasıl sabitlenebilmesini gösteren bir animasyon](media/vs-2019/debugger-pinnable-properties.gif "Sabitlenebilir Özellikler aracını Visual Studio hata ayıklayıcısında özellikleri sabitler.")

Daha fazla bilgi için bkz. [Pintuma özellikleri: Debug & yönetilen nesneleri blog GÖNDERINIZDE görüntüleme](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) .

## <a name="whats-next"></a>Sırada ne var?

Visual Studio 2019 ' i genellikle geliştirme deneyiminizi daha da iyi hale getirebileceğiniz yeni özelliklerle güncelleştiririz. En son yeniliklerimiz hakkında daha fazla bilgi edinmek için [Visual Studio bloguna](https://devblogs.microsoft.com/visualstudio/)göz atın. Önizleme tarihine kadar yayımladığımız bir kayıt için [Önizleme sürüm notlarına](/visualstudio/releases/2019/release-notes-preview/)göz atın. Ve daha sonra yayınlanmasını planladığımızı bir liste için bkz. [Visual Studio yol haritası](/visualstudio/productinfo/vs-roadmap).

Bu sırada, şu anda çalışmadaki yeni bir özellik aşağıda verilmiştir.

- **Visual Studio 2019 'de gelişmiş git deneyimi (Önizleme)**

   Yeni git sürüm denetimi deneyimi artık Visual Studio 2019 [sürüm 16,8](/visualstudio/releases/2019/release-notes/)' de varsayılan olarak açık olsa da, deneyimi en yeni önizleme sürümünde iyileştirmek için özellikler eklemeye devam ediyoruz.

   Daha fazla bilgi için bkz. [Visual Studio 'Da sürüm denetimi](/visualstudio/version-control/) sayfası.

Önizleme sürümü ve bir indirme bağlantısı hakkında daha fazla bilgi için &mdash; &mdash; bkz. **[Visual Studio önizleme](https://aka.ms/vspreview/)** sayfası.

## <a name="give-us-feedback"></a>Geri bildirimde bulunun

Visual Studio ekibine neden geri bildirim gönderilsin? Müşteri geri bildirimlerine önem veriyoruz. Yaptığımız kadar çok şey vardır.

* Visual Studio 'Yu nasıl geliştirebileceğimizi gösteren bir öneride bulunmak isterseniz, [bir özellik öner](suggest-a-feature.md) aracını kullanarak bunu yapabilirsiniz.

* Sorun Bildirme aracını kullanarak Visual Studio, kilitleniyor veya başka bir performans sorunuyla karşımıza çıkarsanız, yeniden verme adımlarını ve destek dosyalarını bizimle kolayca [paylaşabilirsiniz.](how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

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
