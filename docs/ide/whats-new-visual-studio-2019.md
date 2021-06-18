---
title: Visual Studio 2019’daki yenilikler
titleSuffix: ''
description: Visual Studio 2019'daki yeni özellikler hakkında bilgi.
ms.date: 06/17/2021
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
ms.openlocfilehash: d34c3a3b4d808b1f4e24051763f1c0876a175a3a
ms.sourcegitcommit: a9526ab1556c47570286c7a7d3314af67fd1dcf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2021
ms.locfileid: "112365475"
---
# <a name="whats-new-in-visual-studio-2019"></a>Visual Studio 2019’daki yenilikler

**16.10 sürümü için güncelleştirildi.** Tüm [sürüm notlarına bakın |](/visualstudio/releases/2019/release-notes/) Ürün [yol haritasını görüntüleme](/visualstudio/productinfo/vs-roadmap)

>[!div class="button"]
>[Visual Studio 2019’u İndirin](https://visualstudio.microsoft.com/downloads)

2019'Visual Studio tüm geliştirici, uygulama ve platformlar için sınıfının en iyisi araçlar ve hizmetler elde edeceksiniz. İster ilk kez Visual Studio ister yıllardır kullanıyor olun, en son sürümde olduğu gibi birçok şey vardır!

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

**16.9'daki** yeniler: Bulut destekli teknoloji, yapay zeka ve makine öğrenmesi kullanarak arama sonuçlarımızı iyileştirildik. Artık yalnızca daha ilgili sonuçlar Visual Studio arama değil, aynı zamanda ürün özelliklerini daha kolay keşfetmenize de yardımcı olabilir.

Daha fazla bilgi için Intelligent [Visual Studio arama hizmeti](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) blog gönderisi'ne bakın.

### <a name="refactorings"></a>Yeniden düzenlemeler

C# içinde kodunuzu düzenlemeyi kolaylaştıran çok sayıda yeni ve son derece kullanışlı yeniden düzenleme vardır. Bunlar ampulde öneri olarak görünür ve üyeleri arabirime veya temel sınıfa taşıma, ad alanlarını klasör yapısıyla eş olacak şekilde ayarlama, foreach döngülerini Linq sorgularına dönüştürme gibi eylemleri içerir.

   ![Visual Studio 2019'daki yeniden düzenleme deneyiminin animasyonu](media/vs-2019/refactorings.gif "Visual Studio 2019 ' de yeniden düzenlemeler deneyimi.")

Ctrl+ tuşlarına basarak yeniden **düzenlemelerini çağırmanız gerekir.** ve yapmak istediğiniz eylemi seçin.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode,](/visualstudio/intellicode/) yapay zeka (AI) kullanarak yazılım geliştirme çalışmalarınızı geliştirmektedir. IntelliCode, GitHub'da her biri 100'den fazla yıldıza sahip 2.000 açık kaynak proje üzerinde eğitimler ve &mdash; &mdash; önerilerde bulunmalıdır.

![Visual Studio 2019'da IntelliCode animasyonu](media/vs-2019/IntelliCode.gif "Visual Studio 2019 ' de ıntellicode.")

IntelliCode'a sahip Visual Studio üretkenliğinizi artırmanıza yardımcı olabilir:

* Bağlama göre kod tamamlamaları teslimi
* Geliştiricileri ekiplerinin desenlerine ve stillerine bağlı kalmaları için yönlendirin
* Yakalanması zor kod sorunlarını bulma
* Dikkati gerçekten önemli alanlara çekerek kod incelemelerini odakla

Başlangıçta IntelliCode'ın önizlemesini yalnızca C# için uzantı olarak ilk kez Visual Studio. **16.1'de** yeni olan C# ve XAML "in-the-box" desteği ekledik. (C++ ve TypeScript/JavaScript desteği hala önizlemededir.)

Ayrıca C# kullanıyorsanız kendi kodunuz üzerinde özel model eğitebilme özelliği ekledik.

IntelliCode hakkında daha fazla bilgi için IntelliCode'un genel kullanılabilirliği hakkında daha fazla bilgi için [Bkz. IntelliCode'un](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) genel kullanılabilirliğinin yanı sıra bir göz atma ve Daha fazla kodla daha fazla [bilgi Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) blog gönderileri.

### <a name="code-cleanup"></a>Kod temizleme

Yeni bir belge durumu göstergesiyle eşleştirilmiş yeni bir kod temizleme komutudur. Bu yeni komutu kullanarak hem uyarıları hem de önerileri tek bir eylemle tanımlayabilir ve düzeltebilirsiniz (veya bir düğmeye tıklayabilirsiniz).

Temizleme işlemi kodu biçimlendirecek ve geçerli ayarlar ve [](code-styles-and-code-cleanup.md) .editorconfig dosyaları tarafından önerilen kod [düzeltmelerini uygulayacak.](create-portable-custom-editor-options.md)

   ![Visual Studio 2019'da yeni kod temizleme denetimi ekran görüntüsü](media/vs-2019/code-cleanup-profile.png "Visual Studio 2019 ' de yeni kod temizleme denetimi.")

Ayrıca, düzeltici koleksiyonlarını profil olarak kaydedebilirsiniz. Örneğin, kod sırasında sık sık uygulayan küçük bir hedefli düzeltici kümeniz varsa ve bir kod incelemeden önce uygulayacak başka kapsamlı çözümciler kümeniz varsa, profilleri bu farklı görevleri ele alan şekilde yapılandırabilirsiniz.

   ![Visual Studio 2019'da kod temizlemeyi yapılandırma denetimi ekran görüntüsü](media/vs-2019/code-cleanup-profile-configure.png "Visual Studio 2019 ' de kod temizleme denetimini yapılandırma.")

### <a name="per-monitor-aware-pma-rendering"></a>Monitör başına farkında (PMA) işleme

Farklı ekran ölçek faktörleriyle yapılandırılmış monitörler kullanıyorsanız veya ana cihazınızın farklı görüntü ölçek faktörlerine sahip bir makineye uzaktan bağlanıyorsanız, Visual Studio bulanık göründüğünü veya yanlış ölçekte işleniyor olduğunu fark edebilirsiniz.

Visual Studio 2019'un sürümüyle, izleyici başına Visual Studio (PMA) uygulaması yapıyoruz. Artık Visual Studio ölçek faktörlerine bakılmaksızın doğru şekilde işleniyor.

   ![Visual Studio 2019'da monitör başına işleme (PMA)](media/vs-2019/pma-dpi-scaling.png "Visual Studio 2019 ' de monitöre duyarlı (PMA) işleme.")

Daha fazla bilgi için Visual Studio [2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) blog gönderisi ile daha iyi çoklu izleme deneyimine bakın.

### <a name="test-explorer"></a>Test Gezgini

**16.2'de** yeni sürümü: Test Gezgini'ni, büyük test kümelerinin daha iyi işlenmesini, daha kolay filtrelemeyi, daha fazla keşfedilebilir komutları, sekmeli oynatma listesi görünümlerini ve hangi test bilgisinin görüntülendiğinde hassas ayarlamalar yapmak için özelleştirilebilir sütunlar sağlayacak şekilde güncelleştirildi.

   ![Test Gezgini'nde kullanıcı arabirimi geliştirmelerini gösteren ekran görüntüsü](media/vs-2019/test-explorer-ui.png "Test Gezgini 'ndeki Kullanıcı arabirimi geliştirmeleri.")

### <a name="net-core"></a>.NET Core

**16.3'te yeni:**.NET Core 3.0 desteği dahil edildi. Platformlar arası, açık kaynak &mdash; ve Microsoft tarafından tam olarak desteklenen.

Daha fazla bilgi için [.NET Core 3.0'ın announcing blog gönderisi'ne](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) bakın.

## <a name="collaborate"></a>İşbirliği

Sorunları çözmek için ekipte nasıl bir ekip olduğunu öğrenmek için aşağıdaki videoyu izleyin. <br><br>*Video uzunluğu: 4,22 dakika*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Git-first iş akışı

2019'da Visual Studio yeni başlangıç penceresi olduğunu fark edeceksiniz.

   ![Visual Studio 2019'da yeni başlangıç penceresinin ekran görüntüsü](media/vs-2019/start-window-dark.png "Visual Studio 2019 ' deki yeni başlangıç penceresi.")

Başlangıç penceresi, hızlı bir şekilde koda başlamaya yardımcı olacak çeşitli seçenekler sunar. Öncelikle bir repodan kod kopyalama veya denetleme seçeneğini kullandık.

   ![Visual Studio 2019'daki 'Git-first' deneyiminin animasyonu](media/vs-2019/git-first.gif "Visual Studio 2019 ' de ' git-First ' deneyimi.")

Başlangıç penceresi ayrıca bir proje veya çözüm açma, yerel klasör açma veya yeni proje oluşturma seçeneklerini de içerir.

Daha fazla bilgi için [Koda al: Yeni kodu nasıl tasarladık? Visual Studio penceresi blog gönderisi.](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/)

### <a name="git-productivity"></a>Git üretkenliği

**16.8 sürümündeki yeni** sürüm: Git artık 2019'da varsayılan Visual Studio denetimi deneyimidir. Özellik kümesi yerleşik olarak ve son iki sürümde geri bildiriminiz temel alarak bu kümeyi de temel aldık. Yeni deneyim artık herkes için varsayılan olarak açıktır. Yeni Git menüsünden depoları kopya açabilir, oluşturabilir veya açabilirsiniz. Tümleşik Git aracı pencerelerini kullanarak kodunıza değişiklikleri işip itin, dalları yönetin, uzak depolarınızı güncel kalın ve birleştirme çakışmalarını giderin.

Daha fazla bilgi için bkz. [Git deneyimi Visual Studio.](../version-control/git-with-visual-studio.md)

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

Hata ayıklarken kesin hedefleme ile nasıl tam olarak izin sağlayacağınız hakkında daha fazla bilgi edinmek için aşağıdaki videoyu görüntüleyin. <br><br>*Video uzunluğu: 3,54 dakika*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Performans kazançları

Bir kez özel C++ veri kesme noktası aldık ve bunları .NET Core uygulamaları için uyartık.

   ![Visual Studio 2019 ' de hata ayıklama veri kesme noktalarını gösteren bir animasyon](media/vs-2019/debug-data-breakpoints.gif "Visual Studio 2019 ' de hata ayıklama veri kesme noktaları.")

C++ veya .NET Core 'da kodlama yapıp etmeksizin, veri kesme noktaları yalnızca normal kesme noktaları yerleştirilerek iyi bir alternatif olabilir. Veri kesme noktaları, bir genel nesnenin nerede değiştirildiğini veya bir listeden eklendiğini veya kaldırılacağını bulma gibi senaryolar için de idealdir.

Ve, büyük uygulamalar geliştiren bir C++ geliştiriciyseniz, Visual Studio 2019, bu uygulamaları bellekle ilgili sorunlarla karşılaşmadan hata ayıklamanıza olanak sağlayan bir dizi sembolü yaptı.

### <a name="search-while-debugging"></a>Hata ayıklarken ara

Büyük olasılıkla bir değer kümesi arasında bir dize izleme penceresi arayarak daha önce vardı. Visual Studio 2019 ' de, aradığınız nesneleri ve değerleri bulmanıza yardımcı olmak için Watch, Yereller ve oto pencerelerinde arama ekledik.

   ![Visual Studio 2019 'de hata ayıklama arama penceresini gösteren bir animasyon](media/vs-2019/debug-window-search.gif "Visual Studio 2019 ' de hata ayıklama arama penceresi.")

Ayrıca, bir değerin Izleme, Yereller ve oto pencereleri içinde nasıl görüntüleneceğini de biçimlendirebilirsiniz. Herhangi bir Windows 'daki öğelerden birini (çift tıklayarak) seçin ve olası biçim Belirticilerinin açılan listesine erişmek için bir virgül (",") ekleyin (her biri amaçlanan efektinin açıklamasını içerir).

   ![Visual Studio 2019 ' de yeni izleme penceresi ve biçim değerleri özelliği](media/search-watch-window.png "Visual Studio 2019 ' deki yeni izleme penceresi ve biçim değerleri özelliği.")

Daha fazla bilgi için bkz. [Visual Studio 2019 ' de geliştirildi: Watch, oto ve Yereller Windows blog gönderide nesneleri ve özellikleri arama](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) .

### <a name="snapshot-debugger"></a>Anlık Görüntü Hata Ayıklayıcı

Tam olarak neler olduğunu görmek için, bulutta uygulamanın yürütmesinin bir anlık görüntüsünü alın. (Bu özellik yalnızca Visual Studio Enterprise ' de kullanılabilir.)

   ![Visual Studio 2019 Enterprise Snapshot Debugger gösteren bir animasyon](media/vs-2019/snapshot-debugger.gif "Visual Studio 2019 Enterprise Snapshot Debugger.")

Azure VM 'de çalışan ASP.NET (çekirdek ve Masaüstü) uygulamalarını hedefleme desteği ekledik. Azure Kubernetes hizmetinde çalışan uygulamalar için de destek ekledik. Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için geçen süreyi önemli ölçüde düşürmeye yardımcı olabilir.

Daha fazla bilgi için bkz. [Snapshot Debugger sayfasını kullanarak canlı ASP.net Azure uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md) ve [giriş süresi, Visual Studio Enterprise 2019 blog gönderisi için hata ayıklama](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) .

### <a name="microsoft-edge-insider-support"></a>Microsoft Edge Insider desteği

**16,2 ' deki yenilikler**: bir JavaScript uygulamasında bir kesme noktası ayarlayabilir ve [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) tarayıcısını kullanarak bir hata ayıklama oturumu başlatabilirsiniz. Bunu yaptığınızda, Visual Studio, hata ayıklama etkinken yeni bir tarayıcı penceresi açar. Bu, daha sonra Visual Studio 'da uygulama JavaScript 'i aracılığıyla ilerlemek için kullanabilirsiniz.

   ![Tarayıcıda JavaScript kod işlemeyi gösteren ekran görüntüsü](media/vs-2019/edge-chromium-breakpoint.png "Tarayıcıda JavaScript kod işleme.")

### <a name="pinnable-properties-tool"></a>Pinleştir Özellikler aracı

**16,4 ' de yeni**: artık, yeni pinalgıladığında Özellikler aracıyla hata ayıklarken nesneleri özelliklerine göre belirlemek daha kolay. İmleci, gözcü, oto ve Yereller pencerelerinin hata ayıklayıcı penceresinde görüntülemek istediğiniz bir özelliğin üzerine getirin, PIN simgesini seçin ve pencerenin en üstünde aradığınız bilgileri hemen görün!

   ![Visual Studio hata ayıklayıcısında, Pinilik özellikleri aracını kullanarak özelliklerin nasıl sabitlenebilmesini gösteren bir animasyon](media/vs-2019/debugger-pinnable-properties.gif "Visual Studio hata ayıklayıcısındaki özellikleri, Pinilik özellikleri aracını kullanarak sabitleyin.")

Daha fazla bilgi için bkz. [Pintuma özellikleri: Debug & yönetilen nesneleri blog GÖNDERINIZDE görüntüleme](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) .

## <a name="whats-next"></a>Sırada ne var?

Visual Studio 'Yu genellikle geliştirme deneyiminizi daha da iyi hale getirebileceğiniz yeni özelliklerle güncelleştiririz. En son yeniliklerimiz hakkında daha fazla bilgi edinmek için [Visual Studio bloguna](https://devblogs.microsoft.com/visualstudio/)göz atın. Önizleme tarihine kadar yayımladığımız bir kayıt için [Önizleme sürüm notlarına](/visualstudio/releases/2019/release-notes-preview/)göz atın. Ve daha sonra yayınlanmasını planladığımızı bir liste için bkz. [Visual Studio yol haritası](/visualstudio/productinfo/vs-roadmap).

Bu sırada şu anda işte geçerli olan çalışmalar şunlardır:

- **Visual Studio 2019 'de gelişmiş git deneyimi (Önizleme)**

   Git sürüm denetimi aracı, Visual Studio 2019 [sürüm 16,8](/visualstudio/releases/2019/release-notes-history/) ve sonraki sürümlerde varsayılan deneyimse de, deneyimi en yeni visual Studio 2019 önizleme sürümü olan [sürüm 16,11](/visualstudio/releases/2019/release-notes-preview/)' de geliştirmeye yönelik özellikler eklemeye devam ediyoruz.

   Daha fazla bilgi için bkz. [Visual Studio 'Da sürüm denetimi](/visualstudio/version-control/) sayfası.

- **Visual Studio 2022 (Önizleme) ilk genel sürümü artık kullanılabilir**

    Sonraki büyük yayınımızın genel önizlemesi, [Visual Studio 2022](/visualstudio/releases/2022/release-notes-preview/)artık kullanıma sunuldu. Yeni sürüm daha hızlıdır, daha ulaşılabilir ve daha hafif. Visual Studio ilk kez 64 bit olur. İndirme bağlantısı ve daha fazla bilgi için bkz. **[Visual Studio 2022 Preview 1 şimdi kullanılabilir!](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/)** blog gönderisi.

## <a name="give-us-feedback"></a>Geri bildirimde bulunun

Visual Studio ekibine neden geri bildirim gönderilsin? Müşteri geri bildirimlerine önem veriyoruz. Yaptığımız kadar çok şey vardır.

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
