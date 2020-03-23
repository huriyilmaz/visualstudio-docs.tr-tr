---
title: Program hatalarını düzeltme ve kodu iyileştirme
description: Bu makalede, Visual Studio'nun yapı hataları, kod çözümlemesi, hata ayıklama araçları ve birim testleri gibi kodunuzdaki sorunları bulmanıza ve düzeltmenize yardımcı olabileceği bazı temel yöntemler açıklanmaktadır.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48fa03dec65bcdc1e6c3af94200cfb6c46907e49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77476865"
---
# <a name="make-code-work-in-visual-studio"></a>Visual Studio'da kod çalışması yapma

Visual Studio, güçlü bir entegre proje oluşturma ve hata ayıklama araçları seti sağlar. Bu makalede, Visual Studio'nun yapı çıktısı, kod analizi, hata ayıklama araçları ve birim testlerini kullanarak kodunuzdaki sorunları bulmanıza nasıl yardımcı olabileceğini öğrenin.

Editörü çözdün ve bir kod oluşturdun. Şimdi, kodun düzgün çalıştığından emin olmak istiyorsun. Visual Studio'da, çoğu IDA'da olduğu gibi, kod çalışması için iki aşama vardır: proje ve derleyici hatalarını yakalamak ve çözmek için kodu oluşturmak ve çalışma zamanı ve dinamik hataları bulmak için kodu çalıştırmak.

## <a name="build-your-code"></a>Kodunuzu oluşturma

Yapı yapılandırmasının iki temel türü vardır: **Hata Ayıklama** ve **Sürüm.** **Hata Ayıklama** yapılandırması, daha zengin bir etkileşimli çalışma süresi hata ayıklama deneyimine olanak tanıyan daha yavaş ve daha büyük bir yürütülebilir lik üretir. **Hata Ayıklama** asla sevk edilmemelidir. **Sürüm** yapılandırması, gönderiye uygun daha hızlı ve optimize edilmiş bir çalıştırılabilir oluşturur (en azından derleyicinin perspektifinden). Varsayılan yapı **yapılandırması Hata Ayıklama'dır.**

Projenizi oluşturmanın en kolay yolu **F7**tuşuna basmaktır, ancak ana menüden **Yapı** > **Çözümü'nü** seçerek yapıyı da başlatabilirsiniz.

![Visual Studio yapı proje menü seçimi](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Visual Studio UI'nin altındaki **Çıkış** penceresinde yapı işlemini gözlemleyebilirsiniz. Hatalar, uyarılar ve yapı işlemleri burada görüntülenir. Hatalarınız varsa (veya yapılandırılmış bir düzeyin üzerinde uyarılarınız varsa), yapınız başarısız olur. Oluştukları satıra gitmek için hataları ve uyarıları tıklatabilirsiniz. **Projenizi f7** tuşuna tekrar basarak (yalnızca hataları olan dosyaları yeniden derlemek için) veya **Ctrl**+**Alt**+**F7** 'ye (temiz ve tam yeniden oluşturma için) basarak yeniden yeniden oluşturabilirsiniz.

Düzenleyicinin altındaki sonuç penceresinde iki sekmeli pencere vardır: ham derleyici çıktısını (hata iletileri dahil) içeren **Çıkış** penceresi; ve tüm hataların ve uyarıların sıralanabilir ve filtrelenebilir bir listesini sağlayan **Hata Listesi** penceresi.

Yapı başarılı olduğunda, **Çıktı** penceresinde aşağıdaki gibi sonuçlar görürsünüz:

![Visual Studio başarılı yapı çıkışı](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Hata Listesini Gözden Geçirin

Daha önce ve başarıyla derlediğiniz kodda herhangi bir değişiklik yapmadıysanız, büyük olasılıkla bir hatanız vardır. Kodlamada yeniyseniz, muhtemelen bunlardan çok var. Basit bir sözdizimi hatası veya yanlış değişken adı gibi hatalar bazen açıktır ve bazen yalnızca size rehberlik edecek şifreli bir kodla anlaşılması zordur. Sorunların daha temiz bir görünümü için, yapı **Çıktıpenceresinin** altına gidin ve **Hata Listesi** sekmesini tıklatın. Bu, sizi projeniz için hataların ve uyarıların daha düzenli bir görünümünü sağlar ve size bazı ekstra seçenekler de sunar.

![Visual Studio Çıktı ve Hata Listesi](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

**Hatanın** oluştuğu satıra atlamak için Hata Listesi penceresindeki hata satırına tıklayın. (Veya **Ctrl**+**Q**tuşuna basarak satır numaralarını açın , **satır numaralarını**yazarak ve ardından sonuçlardan satır numaralarını açıp **kapatarak.** Bu, satır numaralarını açabileceğiniz **Seçenekler** iletişim kutusuna gitmenin en hızlı yoludur.)

![Çizgi numaraları ile Visual Studio editörü](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Visual Studio satır numaraları seçeneği](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Hatanın oluştuğu satır numarasına hızla atlamak için **Ctrl**+**G** tuşuna basın.

Hata kırmızı bir "squiggle" alt vurgulamak ile tanımlanır. Ek ayrıntılar için üzerine oturun. Düzeltme ile yeni bir hata tanıtmak olsa da, düzeltme yapmak ve uzağa gidecek. (Buna "gerileme" denir.)

![Visual Studio hata hover](../ide/media/vs_ide_gs_debug_error_hover1.png)

Hata listesini gözden geçirin ve kodunuzdaki tüm hataları giderin.

![Visual Studio Hata Ayıklama hataları penceresi](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Hataları ayrıntılı olarak gözden geçirme

Birçok hata, derleyici açısından olduğu gibi ifade, size hiçbir anlam ifade edebilir. Bu gibi durumlarda, ek bilgilere ihtiyacınız olacak. Hata **Listesi** penceresinden, hata veya uyarı hakkında daha fazla bilgi için otomatik Bing araması yapabilirsiniz. İlgili giriş satırına sağ tıklayın ve bağlam menüsünden **Hata Yardımını Göster'i** seçin veya Hata **Listesi'nin** **Kod** sütunundaki köprülü hata kodu değerine tıklayın.

![Visual Studio hata listesi Bing arama](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

Ayarlarınıza bağlı olarak, web tarayıcınız hata kodu ve metniiçin arama sonuçlarını görüntüler veya Visual Studio'da bir sekme açılır ve Bing aramasının sonuçlarını gösterir. Sonuçlar Internet'teki birçok farklı kaynaktan gelir ve hepsi yararlı olmayabilir.

## <a name="use-code-analysis"></a>Kod analizini kullanma

Kod çözümleyicileri, kod yönetiminde çalışma zamanı hatalarına veya sorunlara yol açabilecek yaygın kod sorunları arar.

### <a name="c-and-visual-basic-code-analysis"></a>C# ve Visual Basic kod analizi

Visual Studio, yazarken C# ve Visual Basic kodunu inceleyen [bir .NET Derleyici Platformu çözümleyicileri](../code-quality/roslyn-analyzers-overview.md) kümesi içerir. Visual Studio uzantısı olarak veya NuGet paketi olarak ek çözümleyiciler yükleyebilirsiniz. Kural ihlalleri bulunursa, bunlar hem Hata Listesinde hem de kod düzenleyicisinde rahatsız edici kod altında bir kıvrım olarak bildirilir.

### <a name="c-code-analysis"></a>C++ kod analizi

C++ kodunu çözümlemek için [statik kod çözümlemesi](/cpp/code-quality/quick-start-code-analysis-for-c-cpp)çalıştırın. Başarılı bir yapıyı engelleyen bariz hataları temizledikten sonra çalıştırma alışkanlığı edinin ve üretebileceği uyarıları gidermek için biraz zaman ayırın. Kendinizi yolda bazı baş ağrısı kaydedeceğiz, ve birkaç kod tarzı teknikleri öğrenebilirsiniz.

Statik kod analizini başlatmak için **Alt**+**F11'e** (veya üst menüden**Çözümde Çalıştır Kod Analizini** **Analiz** > Et'i seçin) basın.

![Visual Studio Kod Analizi menü öğesi](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Yeni veya güncelleştirilmiş uyarılar IDE'nin altındaki **Hata Listesi** sekmesinde görünür. Kod olarak onlara atlamak için uyarılar tıklayın.

![Uyarılar ile Visual Studio Hata Listesi](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Kodu düzeltmek veya yeniden düzenlemek için Hızlı Eylemler'i kullanma

[Hızlı İşlemler,](../ide/quick-actions.md)ampul veya tornavida simgesinden edinilebilir, kod satırlarını yeniden düzenlemenize izin verin. Bunlar, C#, C++ve Visual Basic kodlarında sık karşılaşılan uyarıları hızlı ve etkili bir şekilde düzeltmenin kolay bir yoludur. Bunlara erişmek için, bir uyarı dalgalı sağ tıklayın ve **Hızlı Eylemler ve refactorings**seçin. Veya imleciniz renkli dalgalı çizgideyken **Ctrl**+tuşuna**basın.** veya kenar boşluğundaki ampulü, hata ampulünü veya tornavida simgesini seçin. Bu kod satırına uygulayabileceğiniz olası düzeltmelerin veya yeniden faktörlerin bir listesini görürsünüz.

![Visual Studio ampul önizleme](../ide/media/quick-actions-options.png)

Hızlı Eylemler, kod çözümleyicilerinin kodunuzu düzeltme, yeniden düzenleme veya geliştirme fırsatı olduğunu belirlediği her yerde kullanılabilir. Herhangi bir kod satırına tıklayın, bağlam menüsünü açmak için sağ tıklatın ve **Hızlı Eylemler ve yeniden düzenleme seçeneğini**seçin. Yeniden düzenleme veya iyileştirme seçenekleri varsa, bunlar görüntülenir. Aksi takdirde, ileti **Burada kullanılabilir hızlı eylemler IDE'nin** sol alt köşesinde görüntülenir.

![Hızlı eylem yok metin](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Deneyim ile, hızlı bir şekilde ok tuşları ve **Ctrl**+kullanabilirsiniz.**.** kolay yeniden düzenleme fırsatlarını kontrol etmek ve kodunuzu temizlemek için!

::: moniker range="vs-2019"

## <a name="run-code-cleanup"></a>Kod Temizleme yi Çalıştır

Visual Studio, düzenleyicinin altındaki **Kod Temizleme** düğmesi aracılığıyla kod stili tercihleri de dahil olmak üzere [C# kod dosyanızın isteğe bağlı biçimlendirmesini](code-styles-and-code-cleanup.md#apply-code-styles)sağlar.

![Visual Studio 2019'da Kod Temizleme düğmesi](media/execute-code-cleanup.png)

Dosyanızı boşluklar, girintiler ve saire için biçimlendirmenin yanı **sıra, Code Cleanup** tanımladığınız bir dizi kod stili kuralı da uygular. Her kod stili için tercihleriniz [EditorConfig dosyasından](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), proje için varsa veya **Seçenekler** iletişim kutusundaki kod [stili ayarlarından](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) okunur.

::: moniker-end

## <a name="debug-your-running-code"></a>Çalışan kodunuzu hata ayıklama

Artık kodunuzu başarıyla oluşturup biraz temizleme gerçekleştirdiğinize göre, **F5** tuşuna basarak veya **Hata Ayıklama** > **Hata Ayıklama'yı**seçerek çalıştırın. Bu, uygulamanızın davranışını ayrıntılı olarak gözlemleyebilmeniz için hata ayıklama ortamında başlar. Uygulamanız çalışırken Visual Studio IDE değişir: **Çıkış** penceresi iki yenipencereyle değiştirilir (varsayılan pencere yapılandırmasında), **Otomatik/Locals/Watch** sekmeli penceresi ve **Çağrı Yığını/Kesme Noktaları/Özel Durum Ayarları/Çıkış** sekmeli penceresi. Bu pencereler, uygulamanızın değişkenlerini, iş parçacıklarını, çağrı yığınlarını ve çalışırken diğer çeşitli davranışları incelemenize ve değerlendirmenize olanak tanıyan birden çok sekmeye sahiptir.

![Visual Studio Autos ve Çağrı Yığını Windows](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

**Shift**+**F5** tuşuna basarak veya **Durdur** düğmesine tıklayarak uygulamanızı durdurun. Veya, uygulamanın ana penceresini (veya komut satırı iletişim kutusunu) kapatabilirsiniz.

Kodunuz mükemmel ve tam olarak beklendiği gibi koştu, tebrikler! Ancak, asılı, ya da çöktü, ya da bazı garip sonuçlar verdi, bu sorunların kaynağını bulmak ve hataları düzeltmek gerekir.

### <a name="set-simple-breakpoints"></a>Basit kesme noktaları ayarlama

[Kesme noktaları,](../debugger/using-breakpoints.md) güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio'nun çalışan kodunuzu nerede askıya alması gerektiğini gösterir, böylece değişkenlerin değerlerine veya belleğin davranışına veya bir kod dalının çalıştırılıp çalıştırılmayacağına göz atabilirsiniz. Kesme noktalarını ayarladıktan ve kaldırdıktan sonra projeyi yeniden oluşturmanız gerekmez.

Kesmenin gerçekleşmesini istediğiniz çizginin uzak kenar boşluğuna tıklayarak bir kesme noktası ayarlayın veya geçerli kod satırında bir kesme noktası ayarlamak için **F9** tuşuna basın. Kodunuzu çalıştırdığınızda, bu kod satırının yönergeleri yürütülmeden önce duraklar (veya *kırılır).*

![Visual Studio kesme noktası](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Kesme noktaları için yaygın kullanımalanları şunlardır:

- Bir kilitlenmenin kaynağını daraltmak veya asmak için, arızaya neden olduğunu düşündüğünüz yöntemin kodunun boyunca ve çevresinde kesme noktaları dağıtın. Hata ayıklayıcıda kod çalıştırırken, rahatsız edici kod satırını bulana kadar kesme noktalarını kaldırın ve sonra birbirine yaklaştırın. Hata ayıklayıcıda kodun nasıl çalıştırılabildiğini öğrenmek için sonraki bölüme bakın.

- Yeni kod tanıttığınızda, bunun başında bir kesme noktası ayarlayın ve beklendiği gibi davrandığından emin olmak için kodu çalıştırın.

- Karmaşık bir davranış uyguladıysanız, program bozulduğunda değişkenlerin ve verilerin değerlerini inceleyebilmeniz için algoritmik kod için kesme noktaları ayarlayın.

- C veya C++ kodu yazıyorsanız, bellekle ilgili hatalar için hata ayıklama yaparken adres değerlerini (NULL'u arayın) ve başvuru sayılarını incelemek için kodu durdurmak için kesme noktalarını kullanın.

Kesme noktalarını kullanma hakkında daha fazla bilgi için [kesme noktalarını kullanma'yı](../debugger/using-breakpoints.md)okuyun.

### <a name="inspect-your-code-at-run-time"></a>Çalışma zamanında kodunuzu inceleyin

Çalışan kodunuz bir kesme noktasına uyup duraklatıldığında, sarı (geçerli deyim) olarak işaretlenmiş kod satırı henüz yürütülmedi. Bu noktada, geçerli deyimi yürütmek ve sonra değiştirilen değerleri incelemek isteyebilirsiniz. Hata ayıklayıcıda kodu yürütmek için birkaç *adım* komutu kullanabilirsiniz. İşaretli kod bir yöntem çağrısıysa, **F11**tuşuna basarak bu koda adım atabilirsiniz. Ayrıca **F10**tuşuna basarak kod satırının *üzerine basabilirsiniz.* Kodda nasıl adım atılanın, hata [ayıklayıcıyla kodu gezin'i](../debugger/navigating-through-code-with-the-debugger.md)okuyun.

![Visual Studio çalışma süresi değer denetimi](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Önceki resimde, hata ayıklayıcı bir deyimi **F10** veya **F11** tuşuna basarak ilerletebilirsiniz (burada yöntem çağrısı olmadığından, her iki komut da aynı sonuca sahiptir).

Hata ayıklama duraklatılmış olsa da, neler olup bittiğini belirlemek için değişkenlerinizi inceleyebilir ve yığınları arayabilirsiniz. Görmeyi beklediğiniz aralıklarda değerler var mı? Aramalar doğru sırada mı yapılıyor?

![Visual Studio çalışma süresi değer denetimi](../ide/media/vs_ide_gs_debug_inspect_value.png)

Geçerli değerini ve referanslarını görmek için bir değişkenin üzerine titreyin. Beklemediğiniz bir değer görürseniz, büyük olasılıkla önceki veya arama kodunda bir hata nız vardır. Daha ayrıntılı hata ayıklama bilgileri için hata ayıklama yı kullanma hakkında [daha fazla bilgi edinin.](../debugger/debugger-feature-tour.md)

Ayrıca Visual Studio, uygulamanızın CPU'sunu ve bellek kullanımını zaman içinde gözlemleyebileceğiniz **Tanılama Araçları** penceresini görüntüler. Uygulama geliştirmenin ilerleyen saatlerinde, bu araçları beklenmeyen ağır CPU kullanımını veya bellek ayırmayı aramak için kullanabilirsiniz. Beklenmeyen ağır kullanıma veya yayımlanmamış kaynaklara neyin neden olduğunu belirlemek için **Watch** penceresi ve kesme noktalarıyla birlikte kullanın. Daha fazla bilgi için [Profil oluşturma özellik turuna](../profiling/profiling-feature-tour.md)bakın.

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

Birim testleri kod hatalarına karşı ilk savunma hattınızdır, çünkü doğru yapıldığında, genellikle tek bir işlev olan tek bir kod "birimini" sınarlar ve hata ayıklama ları tam programınızdan daha kolaydır. Visual Studio, hem yönetilen hem de yerel kod için Microsoft birim sınayı çerçevelerini yükler. Birim testleri oluşturmak, çalıştırmak ve bu testlerin sonuçlarını raporlamak için bir birim test çerçevesi kullanın. Kodunuzu hala doğru çalıştığını test etmek için değişiklik yaptığınızda birim testleri yeniden çalıştırın. Visual Studio Enterprise sürümü ile, her yapıdan sonra testleri otomatik olarak çalıştırabilirsiniz.

Başlamak [için IntelliTest ile kodunuz için birim testleri oluştur'u](../test/generate-unit-tests-for-your-code-with-intellitest.md)okuyun.

Visual Studio'daki birim testleri ve daha iyi kalite kodu oluşturmanıza nasıl yardımcı olabilecekleri hakkında daha fazla bilgi edinmek için [Birim test temellerini](../test/unit-test-basics.md)okuyun.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklama yı kullanma hakkında daha fazla bilgi edinin](../debugger/index.yml)
- [Kod oluşturma ve düzeltme](../ide/code-generation-in-visual-studio.md)
