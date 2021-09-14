---
title: CPU örneklemeye yeni başlayanlar için kılavuz
description: Profil oluşturma Visual Studio işlevlerin uygulamanıza ne kadar süre kullandığını nasıl ortaya çıkararak uygulamayı hızlandırmak için size yol gösteren nasıl bir yol olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/27/2017
ms.topic: how-to
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- performance tools, wizard
- Performance Wizard
ms.assetid: 85161cc4-18ee-49b3-9487-33680e687597
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8187b7543ba603cd23239a463b1ae9875e46c09e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628394"
---
# <a name="beginners-guide-to-cpu-sampling"></a>CPU örneklemeye yeni başlayanlar için kılavuz
Uygulamanıza ilişkin Visual Studio analiz etmek için profil oluşturma araçlarını kullanabilirsiniz. Bu yordam, Örnekleme verilerini **kullanmayı** gösterir.

> [!NOTE]
> Ölçüm izleme desteği gibi özel özelliklere ihtiyacınız yoksa, ESKI CPU örnekleme aracı yerine Tanılama Araçları penceresinde [CPU](../profiling/beginners-guide-to-performance-profiling.md) Kullanımı aracını öneririz.

 **Örnekleme,** uygulamada kullanıcı modu işinin çoğunu yapan işlevleri gösteren istatistiksel bir profil oluşturma yöntemidir. Örnekleme, uygulamanızı hızlandırmak için alanlara bakmak için iyi bir yerdir.

 Belirtilen aralıklarda **Örnekleme** yöntemi, uygulamanıza yürütülen işlevler hakkında bilgi toplar. Profil oluşturma çalıştırmasını tamamladikten sonra profil oluşturma verilerinin Özet görünümü, uygulamada yapılan çalışmaların çoğunun gerçekleştiriliyor olduğu Etkin Yol adlı en etkin işlev çağrı ağacını gösterir.  Görünüm ayrıca en fazla işi gerçekleştiren işlevleri listeler ve örnekleme oturumunun belirli segmentlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar.

 Örnekleme  size ihtiyacınız olan verileri vermezse, diğer profil oluşturma araçları toplama yöntemleri size yardımcı olacak farklı türlerde bilgiler sağlar. Bu diğer yöntemler hakkında daha fazla bilgi için [bkz. Nasıl yapılacaklar: Koleksiyon yöntemlerini seçme.](../profiling/how-to-choose-collection-methods.md)

> [!TIP]
> İşlevleri çağıran kodun Windows, en güncel koduna sahip olduğundan emin olun. *pdb* dosyaları. Bu dosyalar olmadan rapor görünümleriniz, Windows zor olan işlev adlarını listelemektedir. Size gereken dosyalara sahip olduğundan emin olmak için bkz. Nasıl kullanılır: Başvuru Windows [simgesi bilgileri.](../profiling/how-to-reference-windows-symbol-information.md)

## <a name="create-and-run-a-performance-session"></a>Performans oturumu oluşturma ve çalıştırma
 Analiz etmeniz gereken verileri almak için önce bir performans oturumu oluşturmanız ve ardından oturumu çalıştırmamız gerekir. Performans **Sihirbazı her ikisini** de yapmanizi sağlar.

 Bir masaüstü uygulaması veya Windows profili ASP.NET profil oluşturma ASP.NET diğer profil oluşturma araçlarından birini kullansanız gerekir. Bkz. [Profil oluşturma araçlarına ilk bakış.](../profiling/profiling-feature-tour.md)

#### <a name="to-create-and-run-a-performance-session"></a>Performans oturumu oluşturmak ve çalıştırmak için

1. Çözümü Visual Studio. Yapılandırmayı Yayın olarak ayarlayın. (Varsayılan olarak **Hata Ayıklama** olarak ayarlanmış araç çubuğunda Çözüm **Yapılandırmaları** kutusunu bulun. Yayın olarak **değiştirme.)**

    > [!IMPORTANT]
    > Kullanmakta olduğu bilgisayarda yönetici değilseniz, profil Visual Studio yönetici olarak çalıştırabilirsiniz. (Uygulama simgesine sağ Visual Studio ve ardından Yönetici olarak **çalıştır'a tıklayın.**

2. Hata **Ayıkla menüsünde** **Profiler'ı ve** sonra da Profil **Performans Profili Oluşturucu.**

3. Performans Sihirbazı **seçeneğini işaretleyin** ve Başlat'a **tıklayın.**

4. CPU Örnekleme **(önerilen) seçeneğini işaretleyin ve** Son'a **tıklayın.**

5. Uygulama başlatılır ve profil işleyici veri toplamaya başlar.

6. Performans sorunları içerebilir işlevselliği alıştırma.

7. Uygulamayı her zaman olduğu gibi kapatın.

     Uygulamayı çalıştırmayı bitirdikten  sonra profil oluşturma verilerini özet görünümü ana Visual Studio penceresinde, yeni oturum için de Performans Gezgini **görünür.**

## <a name="step-2-analyze-sampling-data"></a>2. Adım: Örnekleme verilerini analiz etme
 Bir performans oturumu çalıştırmayı tamamlarken profil **oluşturma** raporunun Özet görünümü, profil oluşturma raporunun ana penceresinde Visual Studio.

 Sık Erişim Yolunu, ardından en çok işi  yapan işlevlerin listesini ve son olarak Özet Zaman Çizelgesi'ni kullanarak diğer işlevlere odaklanarak verilerinizi analize **başlamanızı öneririz.** Hata Listesi penceresinde profil oluşturma önerilerini ve **uyarılarını da görüntüebilirsiniz.**

 Örnekleme yönteminin size ihtiyacınız olan bilgileri vermeyebilirsiniz. Örneğin, örnekler yalnızca uygulama kullanıcı modu kodu yürütürken toplanır. Bu nedenle, giriş ve çıkış işlemleri gibi bazı işlevler örnekleme tarafından yakalanmaz. Bu Profil Oluşturma Araçları önemli verilere odaklanmanız için çeşitli toplama yöntemleri sağlar. Diğer yöntemler hakkında daha fazla bilgi için [bkz. Nasıl yapılacaklar: Koleksiyon yöntemlerini seçme.](../profiling/how-to-choose-collection-methods.md)

 Şekilde numaralı her alan, yordamda bir adımla ilgilidir.

 ![Örnekleme için özet rapor görünümü](../profiling/media/summary_sampling.png "Summary_Sampling")

#### <a name="to-analyze-sampling-data"></a>Örnekleme verilerini analiz etmek için

1. Özet **görünümünde,** Hot **Path en** yüksek kapsayıcı örneklerle birlikte uygulama çağrı ağacının dalını gösterir. Bu, veriler toplanmışken en etkin olan yürütme yoludur. Yüksek kapsayıcı değerler, çağrı ağacını oluşturan algoritmanın iyileştirilmiş olduğunu gösterir. Kodunda, yolun en düşük olduğu işlevini bulun. Yolun dış modüllerde sistem işlevlerini veya işlevlerini de içerebilir.

     ![Profil Oluşturma Hot Path](../profiling/media/profiler_hotpath.png "Profiler_HotPath")

    1. **Kapsayıcı Örnekler,** işlevin ne kadar iş tamamla olduğunu ve işlev tarafından çağrılan işlevleri gösterir. Yüksek kapsamlı sayımlar, genel olarak en pahalı işlevleri işaret eder.

    2. **Özel Örnekler,** işlevin çağıran işlevler tarafından yapılan işler hariç olmak üzere işlev gövdesinde kod tarafından ne kadar iş yap gerektiğini gösterir. Özel sayıların yüksek olması, işlevin içinde bir performans sorunu olduğunu gösteriyor olabilir.

2. Profil oluşturma verilerine ilişkin İşlev **Ayrıntıları görünümünü** görüntülemek için işlev adına tıklayın. İşlev **Ayrıntıları görünümü,** seçilen işlev için profil oluşturma verilerine ilişkin bir grafik görünümü sunar ve bu işleve çağrı yapan tüm işlevleri ve seçilen işlev tarafından çağrılan tüm işlevleri gösterir.

    - Çağıran ve çağıran işlevlerin bloklarının boyutu, veya çağrılarak çağrılan işlevlerin göreli sıklığını temsil eder.

    - İşlev Ayrıntıları görünümünün seçili işlevi yapmak için bir çağrıyı veya çağrıyı çağıran işlevin adına tıkabilirsiniz.

    - İşlev Ayrıntıları penceresinin **alt bölmesinde** işlev kodunun kendisi görüntülenir. Kodu inceler ve performansını iyileştirme fırsatı bulursanız kaynak dosya adına tıklar ve dosyayı dosyanın Visual Studio açın.

3. Analizinize devam etmek için Görünüm **açılan** listesinden **Özet'i** **seçerek Özet** görünümüne geri dönebilirsiniz. Ardından İşlevler En Bireysel **İş Yapıyor'daki işlevleri inceler.** Bu listede en yüksek özel örneklere sahip işlevler görüntülenir. Bu işlevlerin işlev gövdesinde yer alan kod önemli bir çalışma gerçekleştirdi ve bunu iyileştirebilirsiniz. Belirli bir işlevi daha fazla analiz etmek için işlev adına tıklar ve işlevi İşlev Ayrıntıları **görünümünde** görüntüler.

     ![En çok işi yapan işlevlerin listesi](../profiling/media/functions_mostwork.png "Functions_MostWork")

     Profil oluşturma çalıştırması ile ilgili araştırmanıza devam etmek için Özet görünümündeki zaman çizelgesini kullanarak profil oluşturma  verilerinden  bir segmenti yeniden analiz eder ve seçilen segmentten Sık Erişimli Yol ve İşlevlerin En Çok Bireysel Çalışma Yaptığını görebilirsiniz.  Örneğin, zaman çizelgesinde daha küçük bir zirveye odaklanmak, profil oluşturma çalıştırması tamamının analizinde gösterilmez pahalı çağrı ağaçlarını ve işlevlerini ortaya çıkarabilirsiniz.

     Bir segmenti yeniden yeniden kullanmak için Özet Zaman Çizelgesi kutusundan bir kesim **seçin** ve ardından Seçime Göre **Filtrele'ye tıklayın.**

     ![Performans Özeti görünümü zaman çizelgesi](../profiling/media/performancesummary.png "PerformansSummary")

4. Profil oluşturma çalıştırması geliştirmenin yollarını önermek ve olası performans sorunlarını belirlemek için de bir kural kümesi kullanır. Bir sorun bulunursa Hata Listesi penceresinde bir **uyarı** görüntülenir. Hata Listesi **penceresini açmak için** Görünüm menüsünde Hata **Listesi'ne** **tıklayın.**

    - İşlev Ayrıntıları görünümünde uyarıya neden **olan işlevi görmek** için uyarıya çift tıklayın.

    - Uyarıyla ilgili ayrıntılı bilgileri görüntülemek için hataya sağ tıklayın ve ardından Hata Yardımlarını **Göster'e tıklayın.**

## <a name="step-3-revise-code-and-rerun-a-session"></a>3. Adım: Kodu düzeltme ve oturumu yeniden çalıştırma
 Bir veya daha fazla işlevi bulup en iyi duruma getirmenizin ardından profil oluşturma çalıştırması tekrarlanabilir ve değişikliklerinizin uygulama performansında yaptığı farkları görmek için verileri karşılaştırabilirsiniz.

#### <a name="to-revise-code-and-rerun-the-profiler"></a>Kodu gözden geçirmek ve profilleyiciyi yeniden çalıştırma

1. Kodunuzu değiştirme.

2. Öğesini açmak **Performans Gezgini,** Hata **Ayıkla** menüsünde ProfilLeyici'ye **tıklayın,** **sonra Performans Gezgini'a** tıklayın ve ardından **Performans Gezgini.**

3. Oturum **Performans Gezgini,** yeniden çalıştırmayı istediğiniz oturuma sağ tıklayın ve ardından Profil Oluşturma ile **Başlat'a tıklayın.**

4. Oturumu yeniden çalıştırdıktan sonra, Performans Gezgini'da  oturum için Raporlar **klasörüne başka bir veri Performans Gezgini.** Hem özgün hem de yeni profil oluşturma verilerini seçin, seçime sağ tıklayın ve ardından Performans Raporlarını **Karşılaştır'a tıklayın.**

     Karşılaştırmanın sonuçlarını görüntüleyen yeni bir rapor penceresi açılır. Karşılaştırma görünümünü kullanma hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Performans veri dosyalarını karşılaştırma.](../profiling/how-to-compare-performance-data-files.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
- [Başlarken](../profiling/getting-started-with-performance-tools.md)
- ['a Genel Bakış](../profiling/overviews-performance-tools.md)
- [Visual Studio'de profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
