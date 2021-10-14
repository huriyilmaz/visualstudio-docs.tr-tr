---
title: Yeni başlayanlar için CPU örneklemesi Kılavuzu
description: Visual Studio profil oluşturma araçlarının uygulamanızdaki işlevler tarafından ne kadar süre kullanıldığını ortaya çıkarmanın, uygulamayı hızlandırmaya yönelik alanlara kılavuzluk ediyor olduğunu öğrenin.
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
ms.openlocfilehash: 99024c3a7d214ebb0f494689972f36e0d240c392
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969079"
---
# <a name="beginners-guide-to-cpu-sampling"></a>Yeni başlayanlar için CPU örneklemesi Kılavuzu
uygulamanızdaki performans sorunlarını analiz etmek için Visual Studio profil oluşturma araçları ' nı kullanabilirsiniz. Bu yordamda **örnekleme** verilerinin nasıl kullanılacağı gösterilmektedir.

> [!NOTE]
> İzleme desteği gibi özelleştirilmiş özelliklere ihtiyaç duymadığınız sürece, eski CPU örnekleme aracı yerine Tanılama Araçları penceresinde [CPU kullanımı](../profiling/beginners-guide-to-performance-profiling.md) aracını kullanmanızı öneririz.

 **Örnekleme** , uygulamada Kullanıcı modu işinin çoğunu yapan işlevleri gösteren istatistiksel bir profil oluşturma yöntemidir. Örnekleme, uygulamanızı hızlandırmak için alanlara bakmak üzere başlamak için iyi bir yerdir.

 Belirtilen aralıklarda **örnekleme** yöntemi, uygulamanızda yürütülen işlevlerle ilgili bilgiler toplar. Profil oluşturma çalıştırmasını tamamladıktan sonra, profil oluşturma verilerinin **Özet** görünümü, uygulamadaki çalışmanın büyük bir kısmında gerçekleştirilen etkin **yol** olarak adlandırılan en etkin işlev çağrı ağacını gösterir. Görünüm Ayrıca en bireysel çalışmayı gerçekleştiren işlevleri listeler ve örnekleme oturumunun belirli kesimlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar.

 **Örnekleme** size ihtiyacınız olan verileri sağlamıyorsa, diğer profil oluşturma araçları koleksiyon yöntemleri sizin için yararlı olabilecek farklı türde bilgiler sağlar. Bu diğer yöntemler hakkında daha fazla bilgi için bkz. [nasıl yapılır: koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md).

> [!TIP]
> Windows işlevleri çağıran kodu profilleriniz, en güncel olduğundan emin olmanız gerekir. *pdb* dosyaları. bu dosyalar olmadan rapor görünümleriniz, şifreli ve anlaşılması zor Windows işlev adlarını listeler. ihtiyacınız olan dosyalara sahip olduğunuzdan emin olmak hakkında daha fazla bilgi için bkz. [nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md).

## <a name="create-and-run-a-performance-session"></a>Performans oturumu oluşturma ve çalıştırma
 Analiz etmeniz gereken verileri almak için, önce bir performans oturumu oluşturmanız ve ardından oturumu çalıştırmanız gerekir. **Performans Sihirbazı** her ikisini de yapmanızı sağlar.

 Windows masaüstü uygulamasının veya ASP.NET uygulamasının profilini oluşturmak istemiyorsanız, diğer profil oluşturma araçlarından birini kullanmalısınız. Bkz. [profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md).

#### <a name="to-create-and-run-a-performance-session"></a>Bir performans oturumu oluşturmak ve çalıştırmak için

1. Çözümü Visual Studio açın. Yapılandırmayı serbest olarak ayarlayın. (Varsayılan olarak **Hata Ayıkla** olarak ayarlanan araç çubuğunda **çözüm konfigürasyonları** kutusunu bulun. **Yayın** olarak değiştirin.)

    > [!IMPORTANT]
    > kullanmakta olduğunuz bilgisayarda yönetici değilseniz, profil oluşturucuyu kullanırken Visual Studio yönetici olarak çalıştırmanız gerekir. (Visual Studio uygulama simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın.

2. **Hata Ayıkla** menüsünde **Profil Oluşturucu**' yı seçin ve ardından **performans profili Oluşturucu**' yı seçin.

3. **Performans Sihirbazı** seçeneğini denetleyip **Başlat**' a tıklayın.

4. **CPU örnekleme (önerilen)** seçeneğini denetleyip **son**' a tıklayın.

5. Uygulamanız başlar ve profil oluşturucu veri toplamaya başlar.

6. Performans sorunları içerebilecek işlevselliği alıştırın.

7. Uygulamayı genellikle yaptığınız gibi kapatın.

     uygulamayı çalıştırmayı bitirdikten sonra, profil oluşturma verilerinin **özet** görünümü ana Visual Studio penceresinde görüntülenir ve yeni oturum için bir simge **Performans Gezgini** penceresinde görüntülenir.

## <a name="step-2-analyze-sampling-data"></a>2. Adım: örnekleme verilerini çözümleme
 Bir performans oturumu çalıştırmayı tamamladığınızda, profil oluşturma raporunun **Özet** görünümü Visual Studio ana penceresinde görüntülenir.

 **Sık kullanılan yolu inceleyerek,** en çok iş yapan işlevlerin listesini ve son olarak **Özet zaman çizelgesini** kullanarak diğer işlevlere odaklanarak verilerinizi analiz etmeye başlamanızı öneririz. Ayrıca, **hata listesi** penceresinde profil oluşturma önerilerini ve uyarıları görüntüleyebilirsiniz.

 Örnekleme yönteminin size ihtiyacınız olan bilgileri sunmayabilir. Örneğin, örnekler yalnızca uygulama kullanıcı modu kodu yürütürken toplanır. Bu nedenle, giriş ve çıkış işlemleri gibi bazı işlevler, örneklemeye göre yakalanmaz. Profil Oluşturma Araçları, önemli verilere odaklanabilmenizi sağlayan birkaç koleksiyon yöntemi sağlar. Diğer yöntemler hakkında daha fazla bilgi için bkz. [nasıl yapılır: koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md).

 Şekildeki her numaralanmış alan, yordamdaki adımla ilgilidir.

 ![Örnekleme için Özet rapor görünümü](../profiling/media/summary_sampling.png "Summary_Sampling")

#### <a name="to-analyze-sampling-data"></a>Örnekleme verilerini analiz etmek için

1. **Özet** görünümünde, **etkin yol** , en yüksek kapsamlı örneklerle uygulamanızın çağrı ağacının dalını gösterir. Bu, veriler toplandığında en etkin olan yürütme yoludur. Yüksek kapsamlı değerler, çağrı ağacını üreten algoritmanın iyileştirilemeyeceğini gösterebilir. Kodunuzda en düşük olan işlevi bulun. Yolun, dış modüllerdeki sistem işlevlerini veya işlevlerini de içerebileceğini unutmayın.

     ![Profil Oluşturucu etkin yolu](../profiling/media/profiler_hotpath.png "Profiler_HotPath")

    1. **Kapsamlı örnekler** , işlev tarafından ne kadar iş yapıldığını ve onun tarafından çağrılan işlevleri gösterir. Yüksek kapsamlı sayılar, genel olarak en pahalı işlevlere işaret edilir.

    2. **Dışlamalı örnekler** , işlev gövdesinde kod tarafından yapılan çalışmanın ne kadar iş olduğunu belirtir, bu, tarafından çağrılan işlevler tarafından gerçekleştirilen iş hariç. Yüksek dışlamalı sayımlar işlevin kendisinde bir performans sorununa işaret edebilir.

2. Profil oluşturma verilerinin **Işlev ayrıntıları** görünümünü görüntülemek için işlev adına tıklayın. **Işlev ayrıntıları** görünümü seçili işlev için profil oluşturma verilerinin grafik bir görünümünü gösterir ve bu işlevi çağıran tüm işlevleri ve seçilen işlev tarafından çağrılan tüm işlevleri gösterir.

    - Çağıran ve çağrılan işlevlerin blokları, çağrılan veya çağrılan işlevlerin göreli sıklığını temsil eder.

    - Işlev ayrıntıları görünümünün seçili işlevini yapmak için, çağıran veya çağrılan bir işlevin adına tıklayabilirsiniz.

    - **Işlev ayrıntıları** pencerelerinin alt bölmesi işlev kodunun kendisini görüntüler. kodu inceleyerek ve performansını iyileştirmek için bir fırsat bulursanız, dosyayı Visual Studio düzenleyicisinde açmak için kaynak dosya adına tıklayın.

3. Analize devam etmek için **Görünüm** açılır listesinden **Özet** ' i seçerek **Özet** görünümüne geri dönün. Ardından, **en bireysel Işleri yapan işlevlerdeki** işlevleri inceleyin. Bu liste, en yüksek dışlamalı örneklere sahip işlevleri görüntüler. Bu işlevlerin işlev gövdesindeki kod önemli çalışmalar gerçekleştiriyor ve onu iyileştirebiliyor olabilirsiniz. Belirli bir işlevi daha fazla analiz etmek için işlev adına tıklayarak işlevin **Ayrıntılar** görünümünde görüntüleyin.

     ![En çok iş yapan işlevlerin listesi](../profiling/media/functions_mostwork.png "Functions_MostWork")

     Profil oluşturma çalıştırmasını araştırmanıza devam etmek için, **Özet** görünümündeki zaman çizelgesini kullanarak profil oluşturma verilerinin bir segmentini yeniden analiz edebilirsiniz. böylece, seçilen bir kesimden **en bireysel Işleri yapan** **etkin yol** ve işlevleri gösterebilirsiniz. Örneğin, zaman çizelgesinde daha küçük bir tepe üzerine odaklanmak, tüm profil oluşturma çalıştırmasının analizinde görünmeyen, pahalı çağrı ağaçları ve işlevleri ortaya çıkarmayabilir.

     Bir segmenti yeniden analiz etmek için **Özet zaman çizelgesi** kutusunda bir segment seçin ve sonra **seçime göre filtrele**' ye tıklayın.

     ![Performans Özeti Görünümü zaman çizelgesi](../profiling/media/performancesummary.png "Performanslı gün")

4. Profil Oluşturucu Ayrıca profil oluşturma çalıştırmasını geliştirme ve olası performans sorunlarını belirleme yollarını önermek için bir kurallar kümesi kullanır. Bir sorun bulunursa, **hata listesi** penceresinde bir uyarı görüntülenir. **Hata listesi** penceresini açmak Için, **Görünüm** menüsünde **hata listesi**' a tıklayın.

    - **Işlev ayrıntıları** görünümü uyarısını veren işlevi görmek için, uyarıya çift tıklayın.

    - Uyarıyla ilgili ayrıntılı bilgileri görüntülemek için hataya sağ tıklayın ve ardından **hatayı göster yardım** ' a tıklayın.

## <a name="step-3-revise-code-and-rerun-a-session"></a>Adım 3: kodu gözden geçirin ve bir oturumu yeniden çalıştırın
 Bir veya daha fazla işlevi bulduktan ve iyileştirdikten sonra, yaptığınız değişikliklerin uygulamanızın performansına göre yaptığı farkı görmek için profil oluşturma çalıştırmasını yineleyebilir ve verileri karşılaştırabilirsiniz.

#### <a name="to-revise-code-and-rerun-the-profiler"></a>Kodu gözden geçirmek ve profil oluşturucuyu yeniden çalıştırmak için

1. Kodunuzu değiştirin.

2. **Performans Gezgini** açmak Için, **hata ayıklama** menüsünde **profil oluşturucu**' ya ve ardından **Performans Gezgini** **Performans Gezgini göster**' e tıklayın.

3. **Performans Gezgini**, yeniden çalıştırmak istediğiniz oturuma sağ tıklayın ve ardından **profil oluşturma ile Başlat** ' a tıklayın.

4. Oturumu yeniden çalıştırdıktan sonra, **Performans Gezgini** oturum için *raporlar* klasörüne başka bir veri dosyası eklenir. Hem özgün hem de yeni profil oluşturma verilerini seçin, seçime sağ tıklayın ve ardından **performans raporlarını karşılaştır**' a tıklayın.

     Karşılaştırma sonuçlarını görüntüleyen yeni bir rapor penceresi açılır. Karşılaştırma görünümünü kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: performans veri dosyalarını karşılaştırma](../profiling/how-to-compare-performance-data-files.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
- [Başlarken](../profiling/getting-started-with-performance-tools.md)
- ['a Genel Bakış](../profiling/overviews-performance-tools.md)
- [Visual Studio profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
