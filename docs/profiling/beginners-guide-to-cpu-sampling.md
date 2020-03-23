---
title: Yeni başlayanlar CPU örnekleme kılavuzu
ms.custom: seodec18
ms.date: 02/27/2017
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- performance tools, wizard
- Performance Wizard
ms.assetid: 85161cc4-18ee-49b3-9487-33680e687597
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c6a5a0eb84e4f06fd1b4dd248a1bce952b2c7197
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779811"
---
# <a name="beginners-guide-to-cpu-sampling"></a>Yeni başlayanlar CPU örnekleme kılavuzu
Uygulamanızdaki performans sorunlarını çözümlemek için Visual Studio profil oluşturma araçlarını kullanabilirsiniz. Bu yordam, **Örnekleme** verilerinin nasıl kullanılacağını gösterir.

> [!NOTE]
> Enstrümantasyon desteği gibi özel özelliklere ihtiyacınız olmadığı sürece, eski CPU örnekleme aracı yerine Tanılama Araçları penceresinde [CPU Kullanım](../profiling/beginners-guide-to-performance-profiling.md) aracını kullanmanızı öneririz.

 **Örnekleme,** uygulamada kullanıcı modu çalışmasının çoğunu yapan işlevleri gösteren istatistiksel bir profil oluşturma yöntemidir. Örnekleme, uygulamanızı hızlandıracak alanlar aramaya başlamak için iyi bir yerdir.

 Örnekleme **yöntemi,** belirli aralıklarla uygulamanızda çalıştırılabilen işlevler hakkında bilgi toplar. Profil oluşturma çalışmasını tamamladıktan sonra, profil oluşturma verilerinin **Özet** görünümü, uygulamadaki çalışmaların çoğunun gerçekleştirildiği **Sıcak Yol**adı verilen en etkin işlev çağrı ağacını gösterir. Görünüm ayrıca en bireysel çalışmayı gerçekleştiren işlevleri listeler ve örnekleme oturumunun belirli kesimlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar.

 **Örnekleme** size ihtiyacınız olan verileri vermiyorsa, diğer profil oluşturma araçları toplama yöntemleri size yardımcı olabilecek farklı türde bilgiler sağlar. Bu diğer yöntemler hakkında daha fazla bilgi için [bkz.](../profiling/how-to-choose-collection-methods.md)

> [!TIP]
> Windows işlevlerini çağıran profil kodu varsa, en güncel . *pdb* dosyaları. Bu dosyalar olmadan, rapor görünümleriniz şifreli ve anlaşılması zor Windows işlev adlarını listeler. İhtiyacınız olan dosyalara sahip olduğundan emin olmak için [bkz.](../profiling/how-to-reference-windows-symbol-information.md)

## <a name="create-and-run-a-performance-session"></a>Performans oturumu oluşturma ve çalıştırma
 Çözümlemeniz gereken verileri almak için önce bir performans oturumu oluşturmanız ve sonra oturumu çalıştırmanız gerekir. **Performans Sihirbazı** her ikisini de yapmanızı sağlar.

 Bir Windows masaüstü uygulamasının veya ASP.NET uygulamanın profilini çıkarmıyorsanız, diğer profil oluşturma araçlarından birini kullanmanız gerekir. Profil [oluşturma araçlarına ilk bakışı](../profiling/profiling-feature-tour.md)görün.

#### <a name="to-create-and-run-a-performance-session"></a>Performans oturumu oluşturmak ve çalıştırmak için

1. Çözümü Visual Studio'da açın. Yapılandırmayı Release olarak ayarlayın. (Varsayılan olarak **hata ayıklama** olarak ayarlanmış araç çubuğundaki **Çözüm Yapılandırmaları** kutusunu bulun. **Yayımla**olarak değiştirin .)

    > [!IMPORTANT]
    > Kullandığınız bilgisayarda yönetici değilseniz, profil oluşturucuyu kullanırken Visual Studio'yu yönetici olarak çalıştırmalısınız. (Visual Studio uygulama simgesine sağ tıklayın ve ardından **yönetici olarak Çalıştır'ı**tıklatın.

2. Hata **Ayıklama** menüsünde **Profiler'ı**seçin ve ardından **Performans Profiloluştur'u**seçin.

3. Performans **Sihirbazı** seçeneğini işaretleyin ve **Başlat'ı**tıklatın.

4. CPU **Örneklemesi (önerilen)** seçeneğini işaretleyin ve **Bitir'i**tıklatın.

5. Uygulamanız başlar ve profil oluşturucu veri toplamaya başlar.

6. Performans sorunları içerebilecek işlevselliği egzersiz.

7. Uygulamayı her zaman olduğu gibi kapatın.

     Uygulamayı çalıştırmayı bitirdikten sonra, profil oluşturma verilerinin **Özet** görünümü ana Visual Studio penceresinde görünür ve performans **gezgini** penceresinde yeni oturum için bir simge görüntülenir.

## <a name="step-2-analyze-sampling-data"></a>Adım 2: Örnekleme verilerini analiz edin
 Performans oturumunu çalıştırmayı bitirdiğinizde, profil oluşturma raporunun **Özet** görünümü Visual Studio'daki ana pencerede görüntülenir.

 **Sıcak Yol'u,** ardından en çok iş yapan işlevlerin listesini ve son olarak **Özet Zaman Çizelgesi'ni**kullanarak diğer işlevlere odaklanarak verilerinizi analiz etmeye başlamanızı öneririz. Profil oluşturma önerilerini ve uyarılarını **Hata Listesi** penceresinde de görüntüleyebilirsiniz.

 Örnekleme yönteminin size ihtiyacınız olan bilgileri vermeyebilir. Örneğin, örnekler yalnızca uygulama kullanıcı modu kodunu yürütürken toplanır. Bu nedenle, giriş ve çıktı işlemleri gibi bazı işlevler örnekleme tarafından yakalanmaz. Profil Oluşturma Araçları, önemli verilere odaklanmanızı sağlayacak çeşitli toplama yöntemleri sağlar. Diğer yöntemler hakkında daha fazla bilgi için [bkz.](../profiling/how-to-choose-collection-methods.md)

 Şekildeki her numaralanmış alan yordamdaki bir adımla ilgilidir.

 ![Örnekleme için özet rapor görünümü](../profiling/media/summary_sampling.png "Summary_Sampling")

#### <a name="to-analyze-sampling-data"></a>Örnekleme verilerini analiz etmek için

1. **Özet** görünümünde, **Hot Path** uygulamanızın arama ağacının dalını en yüksek kapsayıcı örneklerle gösterir. Bu, veriler toplandığında en etkin olan yürütme yoludur. Yüksek kapsayıcı değerler, çağrı ağacını oluşturan algoritmanın en iyi duruma getirebileceğini gösterebilir. Kodunuzda, yolda en düşük işlevi bulun. Yolun dış modüllerde sistem işlevlerini veya işlevlerini de içerebileceğine dikkat edin.

     ![Profiler Sıcak Yol](../profiling/media/profiler_hotpath.png "Profiler_HotPath")

    1. **Kapsayıcı Örnekler,** işlev ve çağrılan işlevler tarafından ne kadar iş yapıldığını gösterir. Yüksek kapsayıcı sayımlar genel olarak en pahalı işlevleri işaret eder.

    2. **Özel Örnekler,** işlev gövdesindeki kod tarafından ne kadar iş yapıldığını gösterir, bu nedenle çağrılan işlevler tarafından yapılan iş hariç. Yüksek özel sayımlar, işlevin kendi içinde bir performans darboğazına işaret edebilir.

2. Profil oluşturma verilerinin **İşlev Ayrıntıları** görünümünü görüntülemek için işlev adını tıklatın. **İşlev Ayrıntıları** görünümü, seçili işlevin profil oluşturma verilerinin grafik görünümünü sunarak, bu işlevi çağıran tüm işlevleri ve seçili işlev tarafından çağrılan tüm işlevleri gösterir.

    - Çağrı ve çağrı işlevleri bloklarının boyutu, çağrılan veya çağrılan işlevlerin göreli sıklığını temsil eder.

    - İşlev Ayrıntıları görünümünün seçili işlevi yapmak için bir arama veya çağrılan işlevin adını tıklatabilirsiniz.

    - **İşlev Ayrıntıları** pencerelerinin alt bölmesi işlev kodunun kendisini görüntüler. Kodu inceler ve performansını en iyi duruma getirmek için bir fırsat bulursanız, Visual Studio düzenleyicisinde dosyayı açmak için kaynak dosya adını tıklatın.

3. Çözümlemenize devam etmek için, **Görünüm** açılır listesinden **Özet'i** seçerek **Özet** görünümüne dönün. Daha sonra **En Bireysel İş yapan fonksiyonlarda**işlevleri inceleyin. Bu liste, en yüksek özel örneklere sahip işlevleri görüntüler. Bu işlevlerin işlev gövdesindeki kod önemli işler yaptı ve bunu en iyi duruma getirebilirsiniz. Belirli bir işlevi daha fazla çözümlemek için, **Işlev Ayrıntıları** görünümünde görüntülemek için işlev adını tıklatın.

     ![En çok işi yapan işlevlerin listesi](../profiling/media/functions_mostwork.png "Functions_MostWork")

     Profil oluşturma çalışması yla ilgili araştırmanıza devam etmek için, seçilen bir segmentten En Çok Bireysel İş Yapan **Sıcak Yol** ve **İşlevleri** göstermek için **Özet** görünümündeki zaman çizelgesini kullanarak profil oluşturma verilerinin bir kesimini yeniden çözümleyebilirsiniz. Örneğin, zaman çizelgesinde daha küçük bir tepeye odaklanmak, tüm profil oluşturma çalışmasının analizinde gösterilmeyen pahalı çağrı ağaçlarını ve işlevleri ortaya çıkarabilir.

     Bir kesimi yeniden çözümlemek **için, Özet Zaman Çizelgesi** kutusunun içindeki bir segmentseçin ve ardından **Seçime Göre Filtrele'yi**tıklatın.

     ![Performans Özeti izleme zaman çizelgesi](../profiling/media/performancesummary.png "Performans Özeti")

4. Profil oluşturma çalışmasını geliştirmenin yollarını önermek ve olası performans sorunlarını belirlemek için bir dizi kural da kullanır. Bir sorun bulunursa, **Hata Listesi** penceresinde bir uyarı görüntülenir. **Hata Listesi** penceresini açmak için Görünüm **menüsünde** **Hata Listesi'ni**tıklatın.

    - **İşlev Ayrıntıları** görünümünü bir uyarı yükselten işlevi görmek için uyarıyı çift tıklatın.

    - Uyarı yla ilgili ayrıntılı bilgileri görüntülemek için hataya sağ tıklayın ve ardından **Hata Yardımını Göster'i** tıklatın

## <a name="step-3-revise-code-and-rerun-a-session"></a>Adım 3: Kodu gözden geçirin ve oturumu yeniden çalıştırın
 Bir veya daha fazla işlevi bulup optimize ettikten sonra profil oluşturma çalışmasını yineleyebilir ve değişikliklerinizin uygulamanızın performansıyla yaptığı farkı görmek için verileri karşılaştırabilirsiniz.

#### <a name="to-revise-code-and-rerun-the-profiler"></a>Kodu gözden geçirmek ve profil oluşturucuyu yeniden çalıştırmak için

1. Kodunuzu değiştirin.

2. Hata **Ayıklama** menüsünde **Performans Gezgini'ni**açmak için **Profiler'ı**tıklatın, ardından **Performans Gezgini'ni** tıklatın ve ardından **Performans Gezgini'ni göster'i**tıklatın.

3. Performans **Gezgini'nde,** yeniden çalıştırmak istediğiniz oturumu sağ tıklatın ve ardından **Profil Oluşturma ile Başlat'ı tıklatın.**

4. Oturumu yeniden çalıştırdıktan sonra, **Performans Gezgini'ndeki**oturum için *Raporlar* klasörüne başka bir veri dosyası eklenir. Hem özgün hem de yeni profil oluşturma verilerini seçin, seçimi sağ tıklatın ve ardından **Performans Raporlarını Karşılaştır'ı**tıklatın.

     Karşılaştırma sonuçlarını gösteren yeni bir rapor penceresi açılır. Karşılaştırma görünümünün nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](../profiling/how-to-compare-performance-data-files.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
- [Başlarken](../profiling/getting-started-with-performance-tools.md)
- [Genel bakış](../profiling/overviews-performance-tools.md)
- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
