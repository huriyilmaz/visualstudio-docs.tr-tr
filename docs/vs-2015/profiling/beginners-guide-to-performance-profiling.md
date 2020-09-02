---
title: Yeni başlayanlar için performans profili oluşturma kılavuzu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- performance tools, wizard
- Performance Wizard
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ecfd329e0e5c096e6e0c2011b60cd97dcd1c2937
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64838036"
---
# <a name="beginners-guide-to-performance-profiling"></a>Performans Profili Oluşturma Başlangıç Kılavuzu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızdaki performans sorunlarını analiz etmek için Visual Studio Profil Oluşturma Araçları kullanabilirsiniz. Bu yordamda **örnekleme** verilerinin nasıl kullanılacağı gösterilmektedir.  
  
 **Örnekleme** , uygulamada Kullanıcı modu işinin çoğunu yapan işlevleri gösteren istatistiksel bir profil oluşturma yöntemidir. Örnekleme, uygulamanızı hızlandırmak için alanlara bakmak üzere başlamak için iyi bir yerdir.  
  
 Belirtilen aralıklarda **örnekleme** yöntemi, uygulamanızda yürütülen işlevlerle ilgili bilgiler toplar. Profil oluşturma çalıştırmasını tamamladıktan sonra, profil oluşturma verilerinin **Özet** görünümü, uygulamadaki çalışmanın büyük bir kısmında gerçekleştirilen etkin **yol**olarak adlandırılan en etkin işlev çağrı ağacını gösterir. Görünüm Ayrıca en bireysel çalışmayı gerçekleştiren işlevleri listeler ve örnekleme oturumunun belirli kesimlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar.  
  
 **Örnekleme** size ihtiyacınız olan verileri sağlamıyorsa, diğer profil oluşturma araçları koleksiyon yöntemleri sizin için yararlı olabilecek farklı türde bilgiler sağlar. Bu diğer yöntemler hakkında daha fazla bilgi için bkz. [nasıl yapılır: koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md).  
  
> [!TIP]
> Windows işlevleri 'ni çağıran kodu profilleriniz varsa, en güncel. pdb dosyalarına sahip olduğunuzdan emin olun. Bu dosyalar olmadan rapor görünümleriniz, şifreli ve anlaşılması zor olan Windows işlev adlarını listeler. İhtiyacınız olan dosyalara sahip olduğunuzdan emin olmak hakkında daha fazla bilgi için bkz. [nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="create-and-run-a-performance-session"></a><a name="Step1"></a> Performans oturumu oluşturma ve çalıştırma  
 Analiz etmeniz gereken verileri almak için, önce bir performans oturumu oluşturmanız ve ardından oturumu çalıştırmanız gerekir. **Performans Sihirbazı** her ikisini de yapmanızı sağlar.  
  
 Bir Windows masaüstü uygulaması veya ASP.NET uygulamasının profilini oluşturmak istemiyorsanız, diğer profil oluşturma araçlarından birini kullanmalısınız. Bkz. [profil oluşturma araçları](../profiling/profiling-tools.md).  
  
#### <a name="to-create-and-run-a-performance-session"></a>Bir performans oturumu oluşturmak ve çalıştırmak için  
  
1. Visual Studio 'da çözümü açın. Yapılandırmayı serbest olarak ayarlayın. (Varsayılan olarak **Hata Ayıkla** olarak ayarlanan araç çubuğunda **çözüm konfigürasyonları** kutusunu bulun. **Yayın**olarak değiştirin.)  
  
    > [!IMPORTANT]
    > Kullandığınız bilgisayarda yönetici değilseniz, profil oluşturucuyu kullanırken Visual Studio 'Yu yönetici olarak çalıştırmalısınız. (Visual Studio uygulaması simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın.  
  
2. **Hata Ayıkla** menüsünde, performans profili **Oluşturucu**' ya tıklayın.  
  
3. **Performans Sihirbazı** seçeneğini denetleyip **Başlat**' a tıklayın.  
  
4. **CPU örnekleme (önerilen)** seçeneğini denetleyip **son**' a tıklayın.  
  
5. Uygulamanız başlar ve profil oluşturucu veri toplamaya başlar.  
  
6. Performans sorunları içerebilecek işlevselliği alıştırın.  
  
7. Uygulamayı genellikle yaptığınız gibi kapatın.  
  
     Uygulamayı çalıştırmayı bitirdikten sonra, profil oluşturma verilerinin **Özet** görünümü ana Visual Studio penceresinde görünür ve yeni oturum için bir simge **Performans Gezgini** penceresinde görüntülenir.  
  
## <a name="step-2-analyze-sampling-data"></a><a name="Step2"></a> 2. Adım: örnekleme verilerini çözümleme  
 Bir performans oturumu çalıştırmayı bitirdiğinizde, Visual Studio 'da ana pencerede profil oluşturma raporunun **Özet** görünümü görüntülenir.  
  
 **Sık kullanılan yolu inceleyerek,** en çok iş yapan işlevlerin listesini ve son olarak **Özet zaman çizelgesini**kullanarak diğer işlevlere odaklanarak verilerinizi analiz etmeye başlamanızı öneririz. Ayrıca, **hata listesi** penceresinde profil oluşturma önerilerini ve uyarıları görüntüleyebilirsiniz.  
  
 Örnekleme yönteminin size ihtiyacınız olan bilgileri sunmayabilir. Örneğin, örnekler yalnızca uygulama kullanıcı modu kodu yürütürken toplanır. Bu nedenle, giriş ve çıkış işlemleri gibi bazı işlevler, örneklemeye göre yakalanmaz. Profil Oluşturma Araçları, önemli verilere odaklanabilmenizi sağlayan birkaç koleksiyon yöntemi sağlar. Diğer yöntemler hakkında daha fazla bilgi için bkz. [nasıl yapılır: koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md).  
  
 Şekildeki her numaralanmış alan, yordamdaki adımla ilgilidir.  
  
 ![Örnekleme için Özet rapor görünümü](../profiling/media/summary-sampling.png "Summary_Sampling")  
  
#### <a name="to-analyze-sampling-data"></a>Örnekleme verilerini analiz etmek için  
  
1. **Özet** görünümünde, **etkin yol** , en yüksek kapsamlı örneklerle uygulamanızın çağrı ağacının dalını gösterir. Bu, veriler toplandığında en etkin olan yürütme yoludur. Yüksek kapsamlı değerler, çağrı ağacını üreten algoritmanın iyileştirilemeyeceğini gösterebilir. Kodunuzda en düşük olan işlevi bulun. Yolun, dış modüllerdeki sistem işlevlerini veya işlevlerini de içerebileceğini unutmayın.  
  
     ![Profil Oluşturucu etkin yolu](../profiling/media/profiler-hotpath.png "Profiler_HotPath")  
  
    1. **Kapsamlı örnekler** , işlev tarafından ne kadar iş yapıldığını ve onun tarafından çağrılan işlevleri gösterir. Yüksek kapsamlı sayılar, genel olarak en pahalı işlevlere işaret edilir.  
  
    2. **Dışlamalı örnekler** , işlev gövdesinde kod tarafından yapılan çalışmanın ne kadar iş olduğunu belirtir, bu, tarafından çağrılan işlevler tarafından gerçekleştirilen iş hariç. Yüksek dışlamalı sayımlar işlevin kendisinde bir performans sorununa işaret edebilir.  
  
2. Profil oluşturma verilerinin **Işlev ayrıntıları** görünümünü görüntülemek için işlev adına tıklayın. **Işlev ayrıntıları** görünümü seçili işlev için profil oluşturma verilerinin grafik bir görünümünü gösterir ve bu işlevi çağıran tüm işlevleri ve seçilen işlev tarafından çağrılan tüm işlevleri gösterir.  
  
    - Çağıran ve çağrılan işlevlerin blokları, çağrılan veya çağrılan işlevlerin göreli sıklığını temsil eder.  
  
    - Işlev ayrıntıları görünümünün seçili işlevini yapmak için, çağıran veya çağrılan bir işlevin adına tıklayabilirsiniz.  
  
    - **Işlev ayrıntıları** pencerelerinin alt bölmesi işlev kodunun kendisini görüntüler. Kodu inceleyebilir ve performansını iyileştirmek için bir fırsat bulursanız kaynak dosya adına tıklayarak dosyayı Visual Studio düzenleyicisinde açın.  
  
3. Analize devam etmek için Görünüm açılır listesinden **Özet** ' i seçerek **Özet** görünümüne geri dönün. Ardından, **en bireysel Işleri yapan işlevlerdeki**işlevleri inceleyin. Bu liste, en yüksek dışlamalı örneklere sahip işlevleri görüntüler. Bu işlevlerin işlev gövdesindeki kod önemli çalışmalar gerçekleştiriyor ve onu iyileştirebiliyor olabilirsiniz. Belirli bir işlevi daha fazla analiz etmek için işlev adına tıklayarak işlevin **Ayrıntılar** görünümünde görüntüleyin.  
  
     ![En çok iş yapan işlevlerin listesi](../profiling/media/functions-mostwork.png "Functions_MostWork")  
  
     Profil oluşturma çalıştırmasını araştırmanıza devam etmek için, **Özet** görünümündeki zaman çizelgesini kullanarak profil oluşturma verilerinin bir segmentini yeniden analiz edebilirsiniz. böylece, seçilen bir kesimden **en bireysel Işleri yapan** **etkin yol** ve işlevleri gösterebilirsiniz. Örneğin, zaman çizelgesinde daha küçük bir tepe üzerine odaklanmak, tüm profil oluşturma çalıştırmasının analizinde görünmeyen, pahalı çağrı ağaçları ve işlevleri ortaya çıkarmayabilir.  
  
     Bir segmenti yeniden analiz etmek için Özet zaman çizelgesi kutusunda bir segment seçin ve sonra **seçime göre filtrele**' ye tıklayın.  
  
     ![Performans Özeti Görünümü zaman çizelgesi](../profiling/media/performancesummary.png "Performanslı gün")  
  
4. Profil Oluşturucu Ayrıca profil oluşturma çalıştırmasını geliştirme ve olası performans sorunlarını belirleme yollarını önermek için bir kurallar kümesi kullanır. Bir sorun bulunursa, **hata listesi** penceresinde bir uyarı görüntülenir. **Hata listesi** penceresini açmak Için, **Görünüm** menüsünde **hata listesi**' a tıklayın.  
  
    - **Işlev ayrıntıları** görünümü uyarısını veren işlevi görmek için, uyarıya çift tıklayın.  
  
    - Uyarıyla ilgili ayrıntılı bilgileri görüntülemek için hataya sağ tıklayın ve ardından **hatayı göster yardım** ' a tıklayın.  
  
## <a name="step-3-revise-code-and-rerun-a-session"></a><a name="Step3"></a> Adım 3: kodu gözden geçirin ve bir oturumu yeniden çalıştırın  
 Bir veya daha fazla işlevi bulduktan ve iyileştirdikten sonra, yaptığınız değişikliklerin uygulamanızın performansına göre yaptığı farkı görmek için profil oluşturma çalıştırmasını yineleyebilir ve verileri karşılaştırabilirsiniz.  
  
#### <a name="to-revise-code-and-rerun-the-profiler"></a>Kodu gözden geçirmek ve profil oluşturucuyu yeniden çalıştırmak için  
  
1. Kodunuzu değiştirin.  
  
2. **Performans Gezgini**açmak Için, **hata ayıklama** menüsünde **profil oluşturucu**' ya ve ardından **Performans Gezgini** **Performans Gezgini göster**' e tıklayın.  
  
3. **Performans Gezgini**, yeniden çalıştırmak istediğiniz oturuma sağ tıklayın ve ardından **profil oluşturma ile Başlat** ' a tıklayın.  
  
4. Oturumu yeniden çalıştırdıktan sonra, **Performans Gezgini**oturum için **raporlar** klasörüne başka bir veri dosyası eklenir. Hem özgün hem de yeni profil oluşturma verilerini seçin, seçime sağ tıklayın ve ardından **performans raporlarını karşılaştır**' a tıklayın.  
  
     Karşılaştırma sonuçlarını görüntüleyen yeni bir rapor penceresi açılır. Karşılaştırma görünümünü kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: performans veri dosyalarını karşılaştırma](../profiling/how-to-compare-performance-data-files.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Gezgini](../profiling/performance-explorer.md)   
 [Başlarken](../profiling/getting-started-with-performance-tools.md)   
 ['a Genel Bakış](../profiling/overviews-performance-tools.md)
