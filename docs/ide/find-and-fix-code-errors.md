---
title: Program hatalarını düzeltme ve kodu geliştirme
description: Bu makalede derleme hataları, kod Visual Studio, hata ayıklama araçları ve birim testleri dahil olmak üzere kodundaki sorunları bulamanıza ve düzeltmenize yardımcı olacak bazı temel yöntemler açıklanmıştır.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5af76de5dbcc7a70722acf0ee01cfed93dbad761
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308265"
---
# <a name="make-code-work-in-visual-studio"></a>Kodun Visual Studio

Visual Studio, güçlü bir tümleşik proje derleme ve hata ayıklama araçları kümesi sağlar. Bu makalede derleme çıkışı, Visual Studio, hata ayıklama araçları ve birim testlerini kullanarak kodundaki sorunları bulamanıza nasıl yardımcı olduğunu bulabilirsiniz.

Düzenleyiciyi çözdün ve bazı kodlar oluşturdun. Şimdi kodun düzgün bir şekilde çalışır hale geldi. Bu Visual Studio çoğu IDE'de olduğu gibi kodun çalışması için iki aşama vardır: proje ve derleyici hatalarını yakalayacak ve çözümleyecek kodu derleme ve çalışma zamanı ile dinamik hataları bulmak için kodu çalıştırma.

## <a name="build-your-code"></a>Kodunuzu oluşturma

derleme yapılandırmasının iki temel türü vardır: **Hata Ayıklama ve** **Sürüm.** Hata **ayıklama yapılandırması,** daha zengin etkileşimli bir çalışma zamanı hata ayıklama deneyimi sağlayan daha yavaş, daha büyük bir yürütülebilir dosya üretir. Hata **ayıklama yürütülebilir** dosyası hiçbir zaman gönderilebeğil. Yayın **yapılandırması,** (en azından derleyicinin perspektifinden) daha hızlı ve iyileştirilmiş bir yürütülebilir dosya derler. Varsayılan derleme yapılandırması Hata **Ayıklama'dır.**

Projenizi oluşturmanın en kolay yolu **F7** tuşuna basmanızdır, ancak ana menüden Derleme Çözümü'yü seçerek  >   de derlemeyi başlatabilirsiniz.

![Visual Studio proje menüsü seçimi](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Derleme işlemini, kullanıcı arabiriminin **en** altındaki Çıkış penceresinde Visual Studio görebilirsiniz. Hatalar, uyarılar ve derleme işlemleri burada görüntülenir. Hatalarınız varsa (veya yapılandırılmış bir düzeyin üzerinde uyarılar varsa), derlemeniz başarısız olur. Hataların ve uyarıların bulunduğu satıra gitmek için üzerine tıklarsanız. **F7** tuşuna tekrar basarak (yalnızca hataları olan dosyaları yeniden derlemek için) **veya Ctrl** + **Alt** + **F7** tuşlarına basarak (temiz ve eksiksiz bir yeniden derleme için) projenizi yeniden derleme.

Düzenleyicinin altındaki sonuçlar penceresinde sekmeli iki pencere  vardır: Ham derleyici çıktısını içeren Çıkış penceresi (hata iletileri dahil); ve **tüm hataların** ve uyarıların sıralanabilir ve filtrelenebilir bir listesini sağlayan Hata Listesi penceresi.

Derleme başarılı olduğunda Çıktı penceresinde aşağıdakine benzer **sonuçlar** görüntülenir:

![Visual Studio derleme çıkışı oluşturma](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Hata Listesini Gözden Geçirme

Daha önce derledik ve başarıyla derledik kodda hiçbir değişiklik yapmadıysanız büyük olasılıkla bir hatayla karşılaştısınız. Kodlamaya yeni başladıysanız büyük olasılıkla çok sayıda kodlamaya sahipsinizdir. Basit bir söz dizimi hatası veya yanlış değişken adı gibi hatalar bazen barizdir ve size yol gösterirken yalnızca şifreli bir kodla anlamak zordur. Sorunların daha temiz bir görünümü için derleme Çıkışı penceresinin en **altına** gidin ve Hata Listesi **sekmesine** tıklayın. Bu sizi projeniz için hataların ve uyarıların daha düzenli bir görünümüne alır ve size bazı ek seçenekler de sağlar.

![Visual Studio Çıkış ve Hata Listesi](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Hata Listesi penceresinde hata **satırına** tıklayıp hatanın oluştuğu satıra atlayın. (Veya **Ctrl** tuşuna basarak satır numaralarını aç + **Q**, satır **numaraları yazın** ve sonra sonuçlardan Satır numaralarını aç **veya kapat'ı** seçin. Bu, satır numaralarını açabilirsiniz Seçenekler **iletişim** kutusuna almanın en hızlı yoludur.)

![Visual Studio numaraları olan bir düzenleyici](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Visual Studio numaralarını seç](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Hatanın meydana geldiği satır numarasına hızla atlamak için **Ctrl** + **G** tuşlarına basın.

Hata, kırmızı bir "geçiş" alt çizgiyle tanımlanır. Ek ayrıntılar için üzerine gelin. Düzeltmeyi yapın, ancak düzeltmeyle birlikte yeni bir hatayla karşıdan çıkabilirsiniz. (Buna "regresyon" denir.)

![Visual Studio hatanın üzerine gelin](../ide/media/vs_ide_gs_debug_error_hover1.png)

Hata listesini adım adım takip edin ve kodundaki tüm hataları düzeltin.

![Visual Studio Hata Ayıklama hataları penceresi](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Hataları ayrıntılı olarak gözden geçirme

Derleyici açısından ifade edilen birçok hata sizin için anlamlı değildir. Bu gibi durumlarda ek bilgilere ihtiyacınız vardır. Hata **Listesi penceresinde,** hata veya uyarı hakkında daha fazla bilgi için otomatik bir Bing araması ekleyebilirsiniz. İlgili giriş satırına sağ tıklayın  ve bağlam menüsünden Hata Yardımlarını Göster'i seçin veya Hata Listesi'nin **Kod** sütunundaki köprü hata kodu **değerine tıklayın.**

![Visual Studio listesi Bing araması](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

Ayarlarınıza bağlı olarak, web tarayıcınız hata kodu ve metin için arama sonuçlarını görüntüler veya web tarayıcınızda Visual Studio içinde bir sekme açılır ve Bing arama sonuçlarını gösterir. Sonuçlar İnternet'in birçok farklı kaynağından gelir ve bunların hepsi yararlı olmayacaktır.

## <a name="use-code-analysis"></a>Kod analizini kullanma

Kod çözümleyicileri, çalışma zamanı hatalarına veya kod yönetimi sorunlarına yol açacak yaygın kod sorunlarını ister.

### <a name="c-and-visual-basic-code-analysis"></a>C# ve Visual Basic analizi

Visual Studio C# ve kod yazma [.NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md) inceleyen yerleşik Visual Basic çözümleyici kümesi içerir. Ek çözümleyicileri bir Visual Studio veya NuGet paketi olarak yükleyebilirsiniz. Kural ihlalleri bulunursa, bunlar hem Hata Listesi'nde hem de kod düzenleyicisinde soruna neden olan kodun altında bir geçiş olarak rapor olur.

### <a name="c-code-analysis"></a>C++ kod analizi

C++ kodunu analiz etmek için statik [kod analizini çalıştırın.](/cpp/code-quality/quick-start-code-analysis-for-c-cpp) Başarılı bir derlemeyi önleyen bariz hataları temizledikten sonra çalıştırmayı alışkanlık haline getirme ve ortaya çıkarması gereken uyarıları ele almak için biraz zaman gerekir. Bazı baş ağrıları kendinizden kurtarırsınız ve birkaç kod stili tekniği öğrenebilirsiniz.

Statik **kod analizini** + başlatmak için Alt **F11** tuşuna basın (Code Analysis Çözümde Çalıştır'ı  >   çözümle'yi seçin).

![Visual Studio Code Analizi menü öğesi](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Yeni veya güncelleştirilmiş uyarılar **IDE'nin** en altındaki Hata Listesi sekmesinde görüntülenir. Uyarılara tıklayıp kodda bu uyarılara atlayın.

![Visual Studio Hata Listesi](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Kodu düzeltmek veya yeniden düzenlemek için Hızlı Eylemler'i kullanma

[Ampul veya](../ide/quick-actions.md)tornavida simgesinden kullanılabilen Hızlı Eylemler, kodu satır içinde yeniden düzenlemeyi sağlar. C#, C++ ve kod kodlarında yaygın uyarıları hızlı ve etkili bir şekilde düzeltmenin kolay Visual Basic yoludur. Bu uyarılara erişmek için bir uyarı ikilevına sağ tıklayın ve Hızlı Eylemler ve **yeniden düzenleme'yi seçin.** Veya imleciniz çizginin üzerinde renkli geçiş olduğunda **Ctrl** tuşuna + **basın.** veya kenar boşluğunda ampul, hata ampulü veya tornavida simgesini seçin. Bu kod satırına uygulayabilecek olası düzeltmelerin veya yeniden düzenlemelerin listesini görüntülenir.

![Visual Studio ampul önizlemesi](../ide/media/quick-actions-options.png)

Kod çözümleyicileri kodunuzu düzeltme, yeniden düzenleme veya geliştirme fırsatı bulduğunuzda Hızlı Eylemler kullanılabilir. Herhangi bir kod satırına tıklayın, bağlam menüsünü açmak için sağ tıklayın ve Hızlı Eylemler ve yeniden **düzenleme'yi seçin.** Yeniden düzenleme veya geliştirme seçenekleri varsa bunlar görüntülenir. Aksi takdirde, **IDE'nin sol** alt köşesinde Hızlı eylem yok iletisi görüntülenir.

![Kullanılabilir metin hızlı eylem yok](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Deneyimle, ok tuşlarını ve Ctrl tuşlarını hızlı **bir şekilde kullanabilirsiniz.** +  kolayca yeniden düzenleme fırsatlarını kontrol etmek ve kodunuzu temizlemek için!

::: moniker range=">=vs-2019"

## <a name="run-code-cleanup"></a>Kod Temizlemeyi Çalıştırma

Visual Studio, düzenleyicinin en altındaki Kod Temizleme düğmesi aracılığıyla kod stili tercihleri de dahil olmak üzere [C#](code-styles-and-code-cleanup.md#apply-code-styles)kod dosyanız için isteğe bağlı biçimlendirme sağlar. 

![Visual Studio 2019'da Kod Temizleme düğmesi](media/execute-code-cleanup.png)

Kod Temizleme, dosyanızı boşluklar, girintiler ve cetera için biçimlendirmeye ek **olarak,** tanımladığınız bir dizi kod stili kuralı da uygular. Her kod stiline yönelik tercihleriniz [EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)dosyasından , proje için varsa [](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) veya Seçenekler iletişim kutusundaki kod stili **ayarlarından** okunur.

::: moniker-end

## <a name="debug-your-running-code"></a>Çalışan kodunuzun hata ayıklaması

Kodunuzu başarıyla kurup biraz temizleme işlemi gerçekleştirerek **F5** tuşuna basarak veya Hata Ayıklamayı Başlat hata  >  **ayıklamayı seçerek çalıştırın.** Bu, davranışını ayrıntılı olarak gözlemlemek için uygulamanızı bir hata ayıklama ortamında başlatır. Uygulama Visual Studio çalışırken IDE'nin durumu değişir:  Çıkış penceresi iki yenisi (varsayılan pencere yapılandırmasında), **Otomatik/YerelLer/İzleme** sekmeli penceresi ve **Çağrı Yığını/Kesme Noktaları/Özel Durum Ayarları/Çıkış** sekmeli penceresiyle değiştirilir. Bu pencereler, uygulamanın değişkenlerini, iş parçacıklarını, çağrı yığınlarını ve çalışan diğer davranışları incelemenize ve değerlendirmenize olanak sağlayan birden çok sekmeye sahiptir.

![Visual Studio Otomatikleri ve Çağrı Yığını Pencereleri](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

**Shift** F5 tuşuna + **basarak veya** Durdur düğmesine tıklayarak **uygulamayı** durdurun. Veya yalnızca uygulamanın ana penceresini (veya komut satırı iletişim kutusunu) kapatabilirsiniz.

Kodunuz mükemmel ve tam olarak beklendiği gibi çalıştı, tebrikler! Ancak yanıt vermese veya kilitlenmeye devam ettiyse veya garip sonuçlar verdiyse, bu sorunların kaynağını bulmanız ve hataları düzeltmemiz gerekir.

### <a name="set-simple-breakpoints"></a>Basit kesme noktaları ayarlama

[Kesme noktaları,](../debugger/using-breakpoints.md) güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz. Kesme noktaları ayardan ve kaldırktan sonra projeyi yeniden oluşturmanıza gerek yok.

Kesmenin gerçekleşmesini istediğiniz çizginin sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın veya geçerli kod satırında bir kesme noktası ayarlamak için **F9** tuşuna basın. Kodunuzu çalıştırdığınızda, bu kod satırıyla ilgili yönergeler yürütülmeden önce duraklatılır (veya *keser*).

![Visual Studio kesme noktası](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Kesme noktaları için genel kullanımlar şunları içerir:

- Kilitlenme veya yanıt vermeyen bir programın kaynağını daraltmak için, aradığınız yöntem çağrısının tamamında ve çevresinde dağılım kesme noktaları hataya neden oluyor. Hata ayıklayıcıda kod çalıştırırken, sorunlu kod satırını bulana kadar kesme noktalarını kaldırın ve daha sonra sıfırlayın. Hata ayıklayıcıda kodun nasıl çalıştırılacağını öğrenmek için sonraki bölüme bakın.

- Yeni kod tanıtdığınızda, bunun başlangıcında bir kesme noktası ayarlayın ve beklenen şekilde davrandığından emin olmak için kodu çalıştırın.

- Karmaşık bir davranış uyguladıysanız, algoritmik kodu için kesme noktaları ayarlayın, böylece program kesildiğinde değişkenlerin ve verilerin değerlerini inceleyebilirsiniz.

- C veya C++ kodu yazıyorsanız, kodu durdurmak için kesme noktaları kullanın, böylece, bellekle ilgili hatalarda hata ayıklarken adres değerlerini (NULL ara) ve başvuru sayılarını inceleyebilirsiniz.

Kesme noktaları kullanma hakkında daha fazla bilgi için [kesme noktaları kullanarak](../debugger/using-breakpoints.md)okuyun.

### <a name="inspect-your-code-at-run-time"></a>Çalışma zamanında kodunuzu inceleyin

Çalışan kodunuz bir kesme noktası ve durakladığında, sarı (geçerli ifade) olarak işaretlenen kod satırı henüz yürütülmemiştir. Bu noktada, geçerli ifadeyi yürütmek ve ardından değiştirilen değerleri incelemek isteyebilirsiniz. Hata ayıklayıcıda kod yürütmek için birkaç *adım* komutunu kullanabilirsiniz. İşaretlenen kod bir yöntem çağrısý ise, **F11** tuşuna basarak buna adım adım ekleyebilirsiniz. Ayrıca, **F10** tuşuna basarak kod satırının *üzerinde de adım* aktarabilirsiniz. Kodun nasıl kullanılacağına ilişkin ek komutlar ve Ayrıntılar için [hata ayıklayıcıyla birlikte gezinme kodunu](../debugger/navigating-through-code-with-the-debugger.md)okuyun.

![Visual Studio Code penceresinin ekran görüntüsü. Sol cilt Paydaki kırmızı nokta, sarı renkte işaretlenmiş kod satırında bir kesme noktası gösterir.](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Yukarıdaki çizimde, **F10** veya **F11** tuşlarına basarak hata ayıklayıcı bir deyime ilerleyebilirsiniz (burada hiçbir yöntem çağrısı olmadığından, her iki komut de aynı sonuca sahiptir).

Hata ayıklayıcı duraklatıldığında, ne olduğunu belirlemek için değişkenlerinizi inceleyebilir ve yığınları çağırabilirsiniz. Görmeyi düşündüğünüz aralıklardaki değerler mi? Çağrılar doğru sırada yapılıyor mu?

![Visual Studio Code penceresinin ekran görüntüsü. Sarı olarak işaretlenen kod satırında bir değişken seçilir ve bir açılan pencerede geçerli değeri ve başvuruları gösterilir.](../ide/media/vs_ide_gs_debug_inspect_value.png)

Geçerli değerini ve başvurularını görmek için bir değişkenin üzerine gelin. Beklemediğiniz bir değer görürseniz, muhtemelen önceki veya çağıran kodda bir hata olabilir. Daha ayrıntılı hata ayıklama bilgileri için, hata ayıklayıcıyı kullanma hakkında [daha fazla bilgi edinin](../debugger/debugger-feature-tour.md) .

Ayrıca, Visual Studio, uygulamanızın CPU ve bellek kullanımını zaman içinde gözlemleyebileceğiniz **Tanılama araçları** penceresini görüntüler. Uygulama geliştirmede daha sonra, bu araçları, beklenmeyen ağır CPU kullanımı veya bellek ayırmayı aramak için kullanabilirsiniz. Beklenmedik ağır kullanım veya yayınlanmamış kaynaklara neden olduğunu belirlemek için **izleme** penceresi ve kesme noktaları ile birlikte kullanın. Daha fazla bilgi için bkz. [profil oluşturma Özellik turu](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

Birim testleri, kod hatalarından kaynaklanan ilk savunma hattınızdır çünkü doğru şekilde tamamlandığında, tek bir "Unit" kodu ve genellikle tek bir işlevi test ederler ve tam programınızdaki hata ayıklamanın daha kolay olması gerekir. Visual Studio, hem yönetilen hem de yerel kod için Microsoft birim testi çerçeveleri 'ni kurar. Birim testleri oluşturmak, çalıştırmak ve bu testlerin sonuçlarını raporlamak için bir birim test çerçevesi kullanın. Kodunuzun doğru şekilde çalışmaya devam ettiğinden emin olmak için, değişiklik yaptığınızda birim testlerini yeniden çalıştırın. Visual Studio Enterprise Edition ile, her derlemeden sonra testleri otomatik olarak çalıştırabilirsiniz.

Başlamak için, [IntelliTest ile kodunuz için birim testleri oluşturma](../test/generate-unit-tests-for-your-code-with-intellitest.md)makalesini okuyun.

Visual Studio 'da birim testleri hakkında daha fazla bilgi edinmek ve bunların daha iyi kalite kodu oluşturmanıza nasıl yardımcı olabileceğini öğrenmek için [birim testi temel bilgilerini](../test/unit-test-basics.md)okuyun.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcıyı kullanma hakkında daha fazla bilgi edinin](../debugger/index.yml)
- [Kod oluşturma ve düzeltme](../ide/code-generation-in-visual-studio.md)
