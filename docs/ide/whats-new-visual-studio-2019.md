---
title: Visual Studio 2019’daki yenilikler
titleSuffix: ''
description: Visual Studio 2019 ' deki yeni özellikler hakkında bilgi edinin.
ms.date: 12/03/2019
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
ms.openlocfilehash: 975b9ca88a775e08b97cccf1d1580a96ac4d9d65
ms.sourcegitcommit: c222052906362bf1a3762ec4d4623170e4e06702
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810118"
---
# <a name="whats-new-in-visual-studio-2019"></a>Visual Studio 2019’daki yenilikler

**[16,4 sürümü](/visualstudio/releases/2019/release-notes/) için güncelleştirildi**

>[!div class="button"]
>[Visual Studio 2019’u İndirin](https://visualstudio.microsoft.com/downloads)

Visual Studio 2019 ile herhangi bir geliştirici, uygulama ve herhangi bir platform için sınıfının en iyisi araçları ve hizmetleri elde edersiniz. Visual Studio 'Yu ilk kez kullanıyor veya yıllarca kullandıysanız, bu yeni sürümde olduğu kadar çok şey vardır!

Yenilikler için yüksek düzey bir üst sınır aşağıda verilmiştir:

* **[Geliştirme](#develop)** : gelişmiş performans, anlık kod temizleme ve daha iyi arama sonuçlarıyla odaklanmış ve üretken olun.
* **[İşbirliği](#collaborate)** : git-ilk iş akışı, gerçek zamanlı Düzenle ve hata ayıklama ve Visual Studio 'da kod İncelemeleri aracılığıyla doğal işbirliğinden yararlanın.
* **[Hata Ayıkla](#debug)** : belirli değerleri vurgulayın ve bu değerlere gidin, bellek kullanımını iyileştirin ve uygulamanızın yürütmesinin otomatik anlık görüntülerini alın.

Bu sürümdeki tüm yenilikleri içeren tüm liste için [sürüm notlarına](/visualstudio/releases/2019/release-notes/)bakın.

## <a name="develop"></a>Geliştirme

Yeni özelliklerle zamanı nasıl kaydedebileceğinizi öğrenmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 3,00 dakika*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>İyileştirilmiş arama

Daha önce Hızlı Başlat olarak bilinen yeni arama deneyimimiz daha hızlı ve daha etkilidir. Şimdi, yazarken arama sonuçları dinamik olarak görünür. Ve arama sonuçları genellikle komutların klavye kısayollarını içerebilir, böylece daha sonra bunları daha kolay kullanıma almak için daha kolay hale getirebilirsiniz.

   ![Visual Studio 2019 'de yeni arama deneyimine yönelik bir animasyon](media/vs-2019/new-search-feature.gif)

Yeni benzer arama mantığı, yazım hatalarını ne olursa olsun ihtiyacınız olan her şeyi bulur. Bu nedenle, komutları, ayarları, belgeleri veya diğer yararlı şeyleri arıyorsanız, yeni arama özelliği aradığınızı bulmayı kolaylaştırır.

### <a name="refactorings"></a>Yeniden düzenlemeler

Kodunuzun düzenlenmesine daha kolay C# olan çok sayıda yeni ve son derece yararlı yeniden düzenlemeler vardır. Hafif ampulde öneriler olarak görünür ve üyeleri arabirim veya temel sınıfa taşıma, ad alanlarını klasör yapısıyla eşleşecek şekilde ayarlama, Foreach-döngülerini LINQ Sorgularına dönüştürme ve daha fazlasını içeren eylemleri içerir.

   ![Visual Studio 2019 yeniden düzenlemeler deneyiminin animasyonunu](media/vs-2019/refactorings.gif)

Yalnızca **CTRL +** tuşlarına basarak yeniden düzenlemeler çağırın. ve gerçekleştirmek istediğiniz eylemi seçin.

### <a name="intellicode"></a>IntelliCode

[Visual Studio ıntellicode](/visualstudio/intellicode/) yapay zeka (AI) kullanarak yazılım geliştirme çabalarınızı geliştirir. &mdash;, GitHub üzerinde 2.000 açık kaynaklı projeler arasında, her biri 100 yıldız&mdash;ve önerilerini oluşturmak için.

![Visual Studio 2019 ' de ıntellicode animasyonu](media/vs-2019/IntelliCode.gif)

Visual Studio ıntellicode 'un üretkenliğinizi artırmaya yardımcı olabilecek birkaç yol aşağıda verilmiştir:

* Bağlama duyarlı kod tamamlama sunma
* Geliştiricilere takımınızın desenlerine ve stillerine uyacak şekilde rehberlik edin
* Zor kod sorunlarını bulma
* Gerçekten oluşan alanlara dikkat çekmek için kod incelemelerini odaklayın

Başlangıçta yalnızca C# Visual Studio için bir uzantı olarak ıntellicode önizlendiğinde destekliyoruz. Artık **16,1 ' de yeni**eklendi, C# ve xaml "ın-Box" desteğini ekledik. (Ancak TypeScript C++ /JavaScript desteği hala önizlemededir.)

Kullanıyorsanız C#, kendi kodunuzda özel bir modeli eğitme özelliği de ekledik.

Intellicode hakkında daha fazla bilgi için bkz. [ıntellicode 'un genel kullanılabilirliğini duyuruyor](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) ve daha fazla gizli gözlem ve [kod, Visual Studio ıntellicode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) blog gönderileriyle daha az kaydırma.

### <a name="code-cleanup"></a>Kod temizleme

Yeni bir belge durumu göstergesi ile eşleştirilmiş yeni bir kod temizleme komutu. Bu yeni komutu kullanarak, bir düğmeye tıklayarak hem uyarıları hem de önerileri tanımlayabilir ve daha sonra giderebilirsiniz.

Temizleme kodu biçimlendirir ve [geçerli ayarlar](code-styles-and-code-cleanup.md) ve [. editorconfig dosyaları](create-portable-custom-editor-options.md)tarafından önerildiği şekilde kod düzeltmelerini uygular.

   ![Visual Studio 2019 ' de yeni kod temizleme denetiminin ekran görüntüsü](media/vs-2019/code-cleanup-profile.png)

Ayrıca, armanesnelerin koleksiyonlarını bir profil olarak kaydedebilirsiniz. Örneğin, kodlarken sıkça uyguladığınız bir dizi hedeflenmiş sabit listesi varsa ve daha sonra bir kod incelemesinin önüne uygulamak üzere daha kapsamlı bir sabit listesi varsa, profilleri bu farklı görevleri ele almak için yapılandırabilirsiniz.

   ![Visual Studio 2019 'de kod temizleme denetimini yapılandırma ekran görüntüsü](media/vs-2019/code-cleanup-profile-configure.png)

### <a name="per-monitor-aware-pma-rendering"></a>Monitör başına duyarlı (PMA) işleme

Farklı görüntü ölçeği faktörlerine sahip veya ana cihazınızdan farklı görüntü ölçeği faktörleri olan bir makineye uzaktan bağlandığınızda, Visual Studio 'Nun bulanık göründüğünü veya yanlış ölçekte işlediğini fark edebilirsiniz.

Visual Studio 2019 ' in piyasaya çıkmasıyla birlikte, Visual Studio 'Yu ekran uyumlu (PMA) uygulaması olarak yapıyoruz. Artık, kullandığınız görüntü ölçeği çarpanlarından bağımsız olarak Visual Studio doğru şekilde işler.

   ![Visual Studio 2019 ' de monitöre duyarlı (PMA) işleme](media/vs-2019/pma-dpi-scaling.png)

Daha fazla bilgi için bkz. [Visual Studio 2019 blog gönderisi Ile daha iyi çoklu izleme deneyimi](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) .

### <a name="test-explorer"></a>Test Gezgini

**16,2 ' de yeni**: Test Gezgini ' ni, büyük test kümelerinin daha iyi işlenmesini, daha kolay filtrelenmesini, daha keşfedilebilir komutları, sekmeli çalma listesi görünümlerini ve özelleştirilebilir sütunları, hangi test bilgilerinin görüntülendiğini ayarlamanıza olanak sağlayacak şekilde güncelleştirdik.

   ![Test Gezgininde Kullanıcı arabirimi geliştirmelerini gösteren ekran görüntüsü](media/vs-2019/test-explorer-ui.png)

### <a name="net-core"></a>.NET Core

**16,3 ' de yeni**eklendi: .net Core 3,0 için destek ekledik. Platformlar arası, açık kaynak&mdash;ve Microsoft tarafından tam olarak desteklenmektedir.

Daha fazla bilgi için bkz. [.NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) blog gönderisi duyurusu.

## <a name="collaborate"></a>İşbirliği

Sorunları çözmek için nasıl ekip sağlayabileceğiniz hakkında daha fazla bilgi edinmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 4,22 dakika*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="cloud-first-workflow"></a>Bulut-ilk iş akışı

Visual Studio 2019 ' i açtığınızda yeni başlangıç penceresi olduğunu fark edeceksiniz.

   ![Visual Studio 2019 ' de yeni başlangıç penceresinin ekran görüntüsü](media/vs-2019/start-window-dark.png)

Başlangıç penceresi size hızlı bir şekilde kod almanızı sağlamak için çeşitli seçenekler sunar. Önce bir depodan kod kopyalama veya kullanıma alma seçeneğini yerleştirdik.

   ![Visual Studio 2019 ' de ' git-First ' deneyiminin animasyonu](media/vs-2019/git-first.gif)

Başlangıç penceresi ayrıca bir proje veya çözüm açma, yerel bir klasör açma veya yeni bir proje oluşturma seçeneklerini de içerir.

Daha fazla bilgi için bkz. [Get to Code: yeni Visual Studio başlangıç penceresini nasıl tasarlıyoruz](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) blog gönderisi.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) , bir kod temeli ve bağlamını bir ekiple paylaşmanıza ve doğrudan Visual Studio içinden çift yönlü işbirliği yapmanıza olanak tanıyan bir geliştirici hizmetidir. Live Share, bir ekip Mate kendileriyle paylaştığınız bir projeyi okuyabilir, gezinmiş, düzenleyebilir ve hata ayıklamanızı ve sorunsuz ve güvenli bir şekilde yapabilmesini sağlayabilir.

Visual Studio 2019 ile bu hizmet varsayılan olarak yüklenir.

![Visual Studio 2019 ' de Live Share işbirliği özelliğini gösteren bir animasyon](media/vs-2019/live-share.gif)

Daha fazla bilgi için, bkz. [gerçek zamanlı kod İncelemeleri ve etkileşimli eğitim](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) blog gönderisi ve [live share artık Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) blog gönderisine dahil Visual Studio Live Share.

### <a name="integrated-code-reviews"></a>Tümleşik kod İncelemeleri

Visual Studio 2019 ile kullanmak üzere indirebileceğiniz yeni bir uzantı sunuyoruz. Bu yeni uzantıyla, Visual Studio 'dan çıkmadan takımınızın çekme isteklerini gözden geçirebilir, çalıştırabilir ve hatta hata ayıklayabilirsiniz. Hem GitHub hem de Azure DevOps depolarındaki kodu destekliyoruz.

   ![Visual Studio 2019 ' de yeni başlangıç penceresinin ekran görüntüsü](media/vs-2019/pr-experience.png)

Daha fazla bilgi için [Visual Studio çekme istekleri uzantısı blog gönderisini kullanarak kod incelemelerine](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) bakın.

## <a name="debug"></a>Hata ayıklama

Hata ayıklarken kesin hedefleme ile nasıl tam olarak izin sağlayacağınız hakkında daha fazla bilgi edinmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 3,54 dakika*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Performans kazançları

Bir kez dışlamalı C++ veri kesme noktaları aldık ve bunları .NET Core uygulamaları için uyartık.

   ![Visual Studio 2019 ' de hata ayıklama veri kesme noktalarını gösteren bir animasyon](media/vs-2019/debug-data-breakpoints.gif)

Ya da .NET Core 'da C++ kodlama yapıp etmeksizin, veri kesme noktaları yalnızca normal kesme noktaları yerleştirilerek iyi bir alternatif olabilir. Veri kesme noktaları, bir genel nesnenin nerede değiştirildiğini veya bir listeden eklendiğini veya kaldırılacağını bulma gibi senaryolar için de idealdir.

Visual Studio 2019, büyük uygulamalar C++ geliştiren bir geliştiricisiyseniz, bu uygulamalarda bellek ile ilgili sorunlarla karşılaşmadan hata ayıklamanıza olanak sağlayan, sembolleri proc dışında yaptı.

### <a name="search-while-debugging"></a>Hata ayıklarken ara

Büyük olasılıkla bir değer kümesi arasında bir dize izleme penceresi arayarak daha önce vardı. Visual Studio 2019 ' de, aradığınız nesneleri ve değerleri bulmanıza yardımcı olmak için Watch, Yereller ve oto pencerelerinde arama ekledik.

   ![Visual Studio 2019 'de hata ayıklama arama penceresini gösteren bir animasyon](media/vs-2019/debug-window-search.gif)

Ayrıca, bir değerin Izleme, Yereller ve oto pencereleri içinde nasıl görüntüleneceğini de biçimlendirebilirsiniz.  Herhangi bir Windows 'daki öğelerden birine çift tıklayın ve her biri amaçlanan efektinin açıklamasını içeren olası biçim Belirticilerinin açılan listesine erişmek için virgül (",") ekleyin.

   ![Visual Studio 2019 ' de yeni izleme penceresi ve biçim değerleri özelliği](media/search-watch-window.png)

Daha fazla bilgi için bkz. [Visual Studio 2019 ' de geliştirildi: Watch, oto ve Yereller Windows blog gönderide nesneleri ve özellikleri arama](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) .

### <a name="snapshot-debugger"></a>Anlık görüntü hata ayıklayıcısı

Tam olarak neler olduğunu görmek için, bulutta uygulamanın yürütmesinin bir anlık görüntüsünü alın. (Bu özellik yalnızca Visual Studio Enterprise ' de kullanılabilir.)

   ![Visual Studio 2019 Enterprise Snapshot Debugger gösteren bir animasyon](media/vs-2019/snapshot-debugger.gif)

Azure VM 'de çalışan ASP.NET (çekirdek ve Masaüstü) uygulamalarını hedefleme desteği ekledik. Azure Kubernetes hizmetinde çalışan uygulamalar için de destek ekledik. Snapshot Debugger, üretim ortamlarında ortaya çıkan sorunları çözmek için gereken süreyi ciddi ölçüde azaltmaya yardımcı olabilir.

Daha fazla bilgi için bkz. [Snapshot Debugger sayfasını kullanarak canlı ASP.net Azure uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md) ve [giriş süresi, Visual Studio Enterprise 2019 blog gönderisi için hata ayıklama](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) .

### <a name="microsoft-edge-insider-support"></a>Microsoft Edge Insider desteği

**16,2 ' deki yenilikler**: bir JavaScript uygulamasında bir kesme noktası ayarlayabilir ve [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) tarayıcısını kullanarak bir hata ayıklama oturumu başlatabilirsiniz. Bunu yaptığınızda, Visual Studio, hata ayıklama etkinken yeni bir tarayıcı penceresi açar. Bu, daha sonra Visual Studio 'da uygulama JavaScript 'i aracılığıyla ilerlemek için kullanabilirsiniz.

   ![Tarayıcıda JavaScript kod işlemeyi gösteren ekran görüntüsü](media/vs-2019/edge-chromium-breakpoint.png)

### <a name="pinnable-properties-tool"></a>Pinleştir Özellikler aracı

**16,4 ' de yeni**: artık, yeni pinalgıladığında Özellikler aracıyla hata ayıklarken nesneleri özelliklerine göre belirlemek daha kolay. İmleci, gözcü, oto ve Yereller pencerelerinin hata ayıklayıcı penceresinde görüntülemek istediğiniz bir özelliğin üzerine getirin, PIN simgesini seçin ve pencerenin en üstünde aradığınız bilgileri hemen görün!

   ![Visual Studio hata ayıklayıcısında, Pinilik özellikleri aracını kullanarak özelliklerin nasıl sabitlenebilmesini gösteren bir animasyon](media/vs-2019/debugger-pinnable-properties.gif)

## <a name="whats-next"></a>Sırada ne var?

Visual Studio 2019 ' i genellikle geliştirme deneyiminizi daha da iyi hale getirebileceğiniz yeni özelliklerle güncelleştiririz. En son yeniliklerimiz hakkında daha fazla bilgi edinmek için [Visual Studio bloguna](https://devblogs.microsoft.com/visualstudio/)göz atın. Ve önizleme tarihine kadar yayımladığımız bir kayıt için [Önizleme sürüm notlarına](/visualstudio/releases/2019/release-notes-preview/)göz atın.

Visual Studio 2019 için çalışmadaki diğer özellikler hakkında daha fazla bilgi edinmek istiyor musunuz? Bkz. [Visual Studio yol haritası](/visualstudio/productinfo/vs-roadmap/).

## <a name="give-us-feedback"></a>Bize geri bildirimde bulunun

Neden Visual Studio ekibine geri bildirim gönderilsin mi? Size müşteri geri bildirimi ciddiye olduğundan. Yaptığımız kadar çok şey vardır.

* Visual Studio 'Yu nasıl geliştirebileceğimizi gösteren bir öneride bulunmak isterseniz, [bir özellik öner](suggest-a-feature.md) aracını kullanarak bunu yapabilirsiniz.

* Bir askıda kalma, kilitlenme veya başka bir performans sorunuyla karşılaşırsanız [sorun bildir](how-to-report-a-problem-with-visual-studio.md) aracını kullanarak yeniden üretme adımlarını ve destekleyici dosyaları bizimle paylaşabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes/)
* [Visual Studio 2019 SDK 'daki yenilikler](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Mac için Visual Studio 2019 sürüm notları](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Microsoft Build 2019 Konferansı](https://www.microsoft.com/build)
* [Microsoft Connect (); 2018 Konferansı](https://www.microsoft.com/connectevent)
