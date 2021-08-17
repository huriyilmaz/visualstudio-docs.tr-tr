---
title: Program hatalarını düzeltme ve kodu geliştirme
description: Bu makalede derleme hataları, kod Visual Studio, hata ayıklama araçları ve birim testleri dahil olmak üzere kodundaki sorunları bulamanıza ve düzeltmenize yardımcı olacak bazı temel yöntemler açıklanmıştır.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f44d005e9e2170e643c7e27e0b24db4bd822b510c6e8dfe7ef508031d24e662a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121233686"
---
# <a name="make-code-work-in-visual-studio"></a>Kod işlerini Visual Studio

Visual Studio güçlü bir tümleşik proje derleme ve hata ayıklama araçları kümesi sağlar. Bu makalede derleme çıkışı, kod Visual Studio, hata ayıklama araçları ve birim testlerini kullanarak kodundaki sorunları bulamanıza nasıl yardımcı olduğunu bulabilirsiniz.

Düzenleyiciyi çözdün ve bazı kodlar oluşturdun. Şimdi kodun düzgün bir şekilde çalışır hale geldi. Bu Visual Studio çoğu IDE'de olduğu gibi kodun çalışması için iki aşama vardır: proje ve derleyici hatalarını yakalayacak ve çözümleyecek kodu derleme ve çalışma zamanı ile dinamik hataları bulmak için kodu çalıştırma.

## <a name="build-your-code"></a>Kodunuzu oluşturma

İki temel tür derleme yapılandırması vardır: **Hata Ayıklama ve** **Sürüm.** Hata **ayıklama yapılandırması,** daha zengin etkileşimli bir çalışma zamanı hata ayıklama deneyimi sağlayan daha yavaş, daha büyük bir yürütülebilir dosya üretir. Hata **ayıklama yürütülebilir** dosyası hiçbir zaman gönderilebeğil. Yayın **yapılandırması,** (en azından derleyicinin perspektifinden) daha hızlı ve iyileştirilmiş bir yürütülebilir dosya derler. Varsayılan derleme yapılandırması Hata **Ayıklama'dır.**

Projenizi oluşturmanın en kolay yolu **F7** tuşuna basmanızdır, ancak ana menüden Derleme Çözümü'yü seçerek  >   de derlemeyi başlatabilirsiniz.

![Visual Studio projesini derleme menü seçimi](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Derleme işlemini, kullanıcı arabiriminin **en** altındaki Çıkış penceresinde Visual Studio görebilirsiniz. Hatalar, uyarılar ve derleme işlemleri burada görüntülenir. Hatalarınız varsa (veya yapılandırılmış bir düzeyin üzerinde uyarılar varsa), derlemeniz başarısız olur. Hataların ve uyarıların bulunduğu satıra gitmek için üzerine tıklarsanız. **F7** tuşuna tekrar basarak (yalnızca hataları olan dosyaları yeniden derlemek için) veya **Ctrl** + **Alt** + **F7** tuşlarına basarak (temiz ve eksiksiz bir yeniden derleme için) projenizi yeniden derleme.

Düzenleyicinin altındaki sonuçlar penceresinde sekmeli iki pencere  vardır: Ham derleyici çıktısını içeren Çıkış penceresi (hata iletileri dahil); ve **tüm hataların** ve uyarıların sıralanabilir ve filtrelenebilir bir listesini sağlayan Hata Listesi penceresi.

Derleme başarılı olduğunda Çıktı penceresinde aşağıdakine benzer **sonuçlar** görüntülenir:

![Visual Studio derleme çıkışı oluşturma](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Hata Listesini Gözden Geçirme

Daha önce derledik ve başarıyla derledik kodda hiçbir değişiklik yapmadıysanız büyük olasılıkla bir hatayla karşılaştısınız. Kodlamaya yeni başladıysanız büyük olasılıkla çok sayıda kodlamaya sahipsinizdir. Basit bir söz dizimi hatası veya yanlış değişken adı gibi hatalar bazen barizdir ve size yol gösterirken yalnızca şifreli bir kodla anlamak zordur. Sorunların daha temiz bir görünümü için derleme Çıkışı penceresinin en **altına** gidin ve Hata Listesi **sekmesine** tıklayın. Bu sizi projeniz için hataların ve uyarıların daha düzenli bir görünümüne alır ve size bazı ek seçenekler de sağlar.

![Visual Studio Çıkış ve Hata Listesi](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Hata Listesi penceresinde hata **satırına** tıklayıp hatanın oluştuğu satıra atlayın. (Veya **Ctrl** tuşuna basarak satır numaralarını aç + **Q**, satır **numaralarını yazın** ve sonra sonuçlardan Satır numaralarını aç **veya kapat'ı** seçin. Bu, satır numaralarını açabilirsiniz Seçenekler **iletişim** kutusuna almanın en hızlı yoludur.)

![Visual Studio numaraları olan bir düzenleyici](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Visual Studio numaralarını seç](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Hatanın meydana geldiği satır numarasına hızla atlamak için **Ctrl** + **G** tuşlarına basın.

Hata, kırmızı bir "geçiş" alt çizgiyle tanımlanır. Ek ayrıntılar için üzerine gelin. Düzeltmeyi yapın, ancak düzeltmeyle birlikte yeni bir hatayla karşıdan çıkabilirsiniz. (Buna "regresyon" denir.)

![Visual Studio hatanın üzerine gelme](../ide/media/vs_ide_gs_debug_error_hover1.png)

Hata listesini adım adım takip edin ve kodundaki tüm hataları düzeltin.

![Visual Studio Hata ayıklama hataları penceresi](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Hataları ayrıntılı olarak gözden geçirme

Derleyici açısından ifade edilen birçok hata sizin için anlamlı değildir. Bu gibi durumlarda ek bilgilere ihtiyacınız vardır. Hata **Listesi penceresinde,** hata veya uyarı hakkında daha fazla Bing için otomatik bir arama ekleyebilirsiniz. İlgili giriş satırına sağ tıklayın  ve bağlam menüsünden Hata Yardımlarını Göster'i seçin veya Hata Listesi'nin **Kod** sütunundaki köprü hata kodu **değerine tıklayın.**

![Visual Studio hata listesi Bing arama](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

Ayarlarınıza bağlı olarak, web tarayıcınız hata kodu ve metin için arama sonuçlarını görüntüler veya Visual Studio içinde bir sekme açılır ve aramanın Bing gösterir. Sonuçlar İnternet'in birçok farklı kaynağından gelir ve bunların hepsi yararlı olmayacaktır.

## <a name="use-code-analysis"></a>Kod analizini kullanma

Kod çözümleyicileri, çalışma zamanı hatalarına veya kod yönetimi sorunlarına yol açacak yaygın kod sorunlarını ister.

### <a name="c-and-visual-basic-code-analysis"></a>C# ve Visual Basic analizi

Visual Studio C# ve kod yazma [.NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md) inceleyen yerleşik bir Visual Basic çözümleyici kümesi içerir. Ek çözümleyicileri bir Visual Studio uzantısı olarak veya bir NuGet yükleyebilirsiniz. Kural ihlalleri bulunursa, bunlar hem Hata Listesi'nde hem de kod düzenleyicisinde soruna neden olan kodun altında bir geçiş olarak rapor olur.

### <a name="c-code-analysis"></a>C++ kod analizi

C++ kodunu analiz etmek için statik [kod analizini çalıştırın.](/cpp/code-quality/quick-start-code-analysis-for-c-cpp) Başarılı bir derlemeyi önleyen bariz hataları temizledikten sonra çalıştırmayı alışkanlık haline getirme ve ortaya çıkarması gereken uyarıları ele almak için biraz zaman gerekir. Bazı baş ağrıları kendinizden kurtarırsınız ve birkaç kod stili tekniği öğrenebilirsiniz.

Statik **kod analizini** + başlatmak için Alt **F11** tuşuna basın (veya Code Analysis Çözümde Çalıştır'ı  >   çözümle'yi seçin).

![Visual Studio Code Analiz menü öğesi](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Yeni veya güncelleştirilmiş uyarılar **IDE'nin** en altındaki Hata Listesi sekmesinde görüntülenir. Kodda uyarılara atlamak için uyarılara tıklayın.

![Visual Studio Uyarılarla Birlikte Hata Listesi](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Kodu düzeltmek veya yeniden düzenlemek için Hızlı Eylemler'i kullanma

[Ampul veya](../ide/quick-actions.md)tornavida simgesinden kullanılabilen Hızlı Eylemler, kodu satır içinde yeniden düzenlemeyi sağlar. C#, C++ ve kod kodlarında yaygın uyarıları hızlı ve etkili bir şekilde düzeltmenin kolay Visual Basic yoludur. Bu uyarılara erişmek için bir uyarı ikilevına sağ tıklayın ve Hızlı Eylemler ve **yeniden düzenleme'yi seçin.** Veya imleciniz çizginin üzerinde renkli geçiş olduğunda **Ctrl** tuşuna + **basın.** veya kenar boşluğunda ampul, hata ampulü veya tornavida simgesini seçin. Bu kod satırına uygulayabilecek olası düzeltmelerin veya yeniden düzenlemelerin listesini görüntülenir.

![Visual Studio ampul önizlemesi](../ide/media/quick-actions-options.png)

Kod çözümleyicileri kodunuzu düzeltme, yeniden düzenleme veya geliştirme fırsatı bulduğunuzda Hızlı Eylemler kullanılabilir. Herhangi bir kod satırına tıklayın, bağlam menüsünü açmak için sağ tıklayın ve Hızlı Eylemler ve yeniden **düzenleme'yi seçin.** Yeniden düzenleme veya geliştirme seçenekleri varsa bunlar görüntülenir. Aksi takdirde, **IDE'nin sol** alt köşesinde Hızlı eylem yok iletisi görüntülenir.

![Kullanılabilir metin hızlı eylem yok](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Deneyimle, ok tuşlarını ve Ctrl tuşlarını hızlı **bir şekilde kullanabilirsiniz.** +  kolayca yeniden düzenleme fırsatlarını kontrol etmek ve kodunuzu temizlemek için!

::: moniker range=">=vs-2019"

## <a name="run-code-cleanup"></a>Kod Temizlemeyi Çalıştırma

Visual Studio, düzenleyicinin en altındaki Kod Temizleme düğmesi aracılığıyla kod stili tercihleri  de dahil olmak üzere [C#](code-styles-and-code-cleanup.md#apply-code-styles)kod dosyanızı isteğe bağlı olarak biçimlendirmenizi sağlar.

![Visual Studio 2019'da Kod Temizleme düğmesi](media/execute-code-cleanup.png)

Kod Temizleme, dosyanızı boşluklar, girintiler ve cetera için biçimlendirmeye ek **olarak,** tanımladığınız bir dizi kod stili kuralı da uygular. Her kod stiline yönelik tercihleriniz [EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)dosyasından , proje için varsa [](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) veya Seçenekler iletişim kutusundaki kod stili **ayarlarından** okunur.

::: moniker-end

## <a name="debug-your-running-code"></a>Çalışan kodunuzun hata ayıklaması

Kodunuzu başarıyla kurup biraz temizleme işlemi gerçekleştirerek **F5** tuşuna basarak veya Hata Ayıklamayı Başlat hata  >  **ayıklamayı seçerek çalıştırın.** Bu, davranışını ayrıntılı olarak gözlemlemek için uygulamanızı bir hata ayıklama ortamında başlatır. Uygulama Visual Studio çalışırken IDE değişir: Çıkış penceresi  iki yeni IDE (varsayılan pencere yapılandırmasında), **Otomatik/Yerel/İzleme** sekmeli penceresi ve **Çağrı Yığını/Kesme Noktaları/Özel Durum Ayarlar/Çıkış** sekmeli penceresiyle değiştirilir. Bu pencereler, uygulamanın değişkenlerini, iş parçacıklarını, çağrı yığınlarını ve çalışan diğer davranışları incelemenize ve değerlendirmenize olanak sağlayan birden çok sekmeye sahiptir.

![Visual Studio Otomatikler ve Çağrı Yığını Windows](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

**Shift** F5 tuşuna + **basarak veya** Durdur düğmesine tıklayarak **uygulamayı** durdurun. Veya yalnızca uygulamanın ana penceresini (veya komut satırı iletişim kutusunu) kapatabilirsiniz.

Kodunuz mükemmel bir şekilde ve tam olarak beklendiği gibi çalıştı, tebrikler! Ancak yanıt vermeyer veya kilitlenmesi ya da garip sonuçlar vermesi, bu sorunların kaynağını bulmanız ve hataları düzeltmemiz gerekir.

### <a name="set-simple-breakpoints"></a>Basit kesme noktaları ayarlama

[Kesme noktaları,](../debugger/using-breakpoints.md) güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz. Kesme noktaları ayardan ve kaldırktan sonra projeyi yeniden oluşturmanıza gerek yok.

Kesmenin gerçekleşmesini istediğiniz satırın en uzak kenar boşluğuna tıklayarak bir kesme noktası ayarlayın veya geçerli kod satırı üzerinde bir kesme noktası ayarlamak için **F9** tuşuna basın. Kodunuzu çalıştırarak bu kod satırına yönelik yönergeler *yürütülmeden* önce duraklatılır (veya durdurulabilir).

![Visual Studio kesme noktası](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Kesme noktaları için yaygın kullanımlar şunlardır:

- Kilitlenme veya yanıt vermemeyen bir programın kaynağını daraltmak için, hataya neden olduğunu düşünmeniz yöntem çağrısının kodu boyunca ve çevresinde dağılım kesme noktaları. Hata ayıklayıcıda kod çalıştırarak, rahatsız olan kod satırı bulana kadar kesme noktalarını kaldırın ve sıfırlayın. Hata ayıklayıcısında kod çalıştırmayı öğrenmek için sonraki bölüme bakın.

- Yeni kod tanıtın, başında bir kesme noktası ayarlayın ve beklendiği gibi olduğundan emin olmak için kodu çalıştırın.

- Karmaşık bir davranış kullandıysanız, program bozarsa değişkenlerin ve verilerin değerlerini inceleyebilirsiniz.

- C veya C++ kodu yazıyorsanız, bellekle ilgili hatalarda hata ayıklarken adres değerlerini (NULL'yi ara) ve başvuru sayılarını inceleyesiniz ve kodu durdurmak için kesme noktaları kullanın.

Kesme noktaları kullanma hakkında daha fazla bilgi için, Kesme [noktaları kullanma makalesi'ni okuyun.](../debugger/using-breakpoints.md)

### <a name="inspect-your-code-at-run-time"></a>Çalışma zamanında kodunuzu inceleme

Çalışan kodunuz bir kesme noktasıyla karşıdan geldiğinde ve duraklatılırsa, sarıyla işaretlenmiş kod satırı (geçerli deyim) henüz yürütülmedi. Bu noktada, geçerli deyimini yürütmek ve sonra değiştirilen değerleri incelemek istiyor olabilir. Hata ayıklayıcısında *kod* yürütmek için birkaç adım komutu kullanabilirsiniz. İşaretlenen kod bir yöntem çağrısı ise, F11 tuşuna basarak **bu koda adım atabilirsiniz.** Ayrıca F10 *tuşuna* basarak kod satırı üzerinde **adım atabilirsiniz.** Ek komutlar ve kodun adım adım ayrıntıları için Hata [ayıklayıcısı ile kodda gezinme makalesi okuyun.](../debugger/navigating-through-code-with-the-debugger.md)

![Visual Studio penceresinin ekran görüntüsü. Sol oluk içinde kırmızı bir nokta, sarıyla işaretlenmiş kod satırına bir kesme noktası gösterir.](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Önceki çizimde, **F10 veya F11'e** basarak  hata ayıklayıcısı bir deyimini ilerletebilirsiniz (burada yöntem çağrısı yoktur, her iki komut da aynı sonucu verir).

Hata ayıklayıcı duraklatılmışken, neler olup olmadığını belirlemek için değişkenlerinizi ve çağrı yığınlarınızı inceleyebilirsiniz. Değerleri görmeyi beklediğiniz aralıklarda mı? Çağrılar doğru sırada mı yapılıyor?

![Visual Studio penceresinin ekran görüntüsü. Sarıyla işaretlenmiş kod satırına bir değişken seçilir ve açılan liste geçerli değerini ve başvurularını gösterir.](../ide/media/vs_ide_gs_debug_inspect_value.png)

Geçerli değerini ve başvurularını görmek için bir değişkenin üzerine gelin. Beklemeden bir değer görüyorsanız, büyük olasılıkla önceki kodda veya çağırma kodunda bir hata vardır. Daha ayrıntılı hata ayıklama bilgileri için hata [ayıklayıcıyı kullanma](../debugger/debugger-feature-tour.md) hakkında daha fazla bilgi edinebilirsiniz.

Ayrıca Visual Studio, **Tanılama Araçları** CPU ve bellek kullanımını gözlemlemek için bir pencere görüntüler. Daha sonra uygulama geliştirme aşamasında, bu araçları kullanarak göz atlanmamış yoğun CPU kullanımı veya bellek ayırmayı sızabilirsiniz. Beklenmeyen ağır kullanım veya **verilenmemiş** kaynaklara neyin neden olduğunu belirlemek için İzleme penceresi ve kesme noktalarıyla birlikte kullanın. Daha fazla bilgi için [bkz. Profil oluşturma özelliği turu.](../profiling/profiling-feature-tour.md)

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

Birim testleri, kod hatalarına karşı ilk savunma hattınızdır çünkü doğru şekilde bittiğinde tek bir "birim" kod testi yapar, genellikle tek bir işlevdir ve hata ayıklaması tam programınıza göre daha kolaydır. Visual Studio, hem yönetilen hem de yerel kod için Microsoft birim testi çerçevelerini yüklür. Birim testleri oluşturmak, çalıştırmak ve bu testlerin sonuçlarını rapor etmek için birim testi çerçevesi kullanın. Değişiklik yaptığınız zaman birim testlerini yeniden çalıştırarak kodunuzun düzgün çalıştap çalışmaması gerekir. Visual Studio Enterprise sürümüyle, her derlemeden sonra testleri otomatik olarak çalıştırabilirsiniz.

Çalışmaya başlama için [IntelliTest ile kodunuz için birim testleri oluşturma makalelerini okuyun.](../test/generate-unit-tests-for-your-code-with-intellitest.md)

Testlerde birim testleri hakkında daha fazla Visual Studio ve daha iyi kaliteli kod oluşturmanıza nasıl yardımcı olacakları hakkında daha fazla bilgi edinmek için [Birim testi temelleri makalelerini okuyun.](../test/unit-test-basics.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcıyı kullanma hakkında daha fazla bilgi](../debugger/index.yml)
- [Kod oluşturma ve düzeltme](../ide/code-generation-in-visual-studio.md)
