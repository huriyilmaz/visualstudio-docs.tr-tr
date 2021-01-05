---
title: Program hatalarını giderme ve kodu geliştirme
description: Bu makalede, Visual Studio 'Nun kodunuzda derleme hataları, kod analizi, hata ayıklama araçları ve birim testleri gibi sorunları bulmanıza ve düzeltmenize yardımcı olabilecek bazı temel yollar açıklanmaktadır.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49da1f46ee5e182741d3aaa56432faac39bfe0f1
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2020
ms.locfileid: "97833292"
---
# <a name="make-code-work-in-visual-studio"></a>Visual Studio 'da kod çalışmasını sağlama

Visual Studio, güçlü tümleşik bir proje derleme ve hata ayıklama araçları kümesi sağlar. Bu makalede, Visual Studio 'Nun kodunuzda derleme çıkışı, kod analizi, hata ayıklama araçları ve birim testleri kullanarak sorunları bulmanıza nasıl yardımcı olduğunu öğrenin.

Düzenleyiciyi iletişime ve bazı kodlar oluşturdunuz. Artık kodun düzgün çalıştığından emin olmak istiyorsunuz. Visual Studio 'da, çoğu IDE 'de olduğu gibi, kod çalışması yapmak için iki aşama vardır: proje ve derleyici hatalarını yakalamak ve çözümlemek için kod oluşturma ve çalışma zamanı ve dinamik hataları bulmak için kodu çalıştırma.

## <a name="build-your-code"></a>Kodunuzu oluşturma

İki temel tür derleme yapılandırması vardır: **hata ayıklama** ve **yayın**. **Hata ayıklama** yapılandırması, daha zengin bir etkileşimli çalışma zamanı hata ayıklama deneyimine olanak sağlayan daha yavaş ve daha büyük bir yürütülebilir dosya üretir. **Hata ayıklama** yürütülebilir dosyası asla gönderilmemelidir. **Yayın** yapılandırması, sevk etmek için uygun olan daha hızlı, iyileştirilmiş bir yürütülebilir dosya oluşturur (en azından derleyicinin perspektifinden). Varsayılan derleme yapılandırması **hata ayıklaması**.

Projenizi oluşturmanın en kolay yolu **F7** tuşuna basmanız, ancak   >  ana menüden Build **Build çözümünü** seçerek derlemeyi de başlatabilirsiniz.

![Visual Studio derleme projesi menü seçimi](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Visual Studio Kullanıcı arabiriminin altındaki **Çıkış** penceresinde yapı sürecini gözlemleyebilirsiniz. Hatalar, uyarılar ve derleme işlemleri burada görüntülenir. Hatalar varsa (veya yapılandırılmış bir düzeyin üzerinde uyarılarınız varsa), derlemeniz başarısız olur. Oluşan satıra gitmek için hatalara ve uyarılara tıklayabilirsiniz. Bir kez **F7** tuşuna basarak (yalnızca hataları olan dosyaları yeniden derlemek için) veya **CTRL** + **alt** + **F7** (temiz ve tamamen yeniden oluşturma için) ' ya tıklayarak projenizi yeniden derleyin.

Sonuç penceresinde düzenleyicinin altında iki sekmeli pencere vardır: ham derleyici çıkışını (hata iletileri dahil) içeren **Çıkış** penceresi; ve tüm hataların ve uyarıların sıralanabilir ve filtrelenebilir bir listesini sağlayan **hata listesi** pencere.

Oluşturma işlemi başarılı olduğunda, **Çıkış** penceresinde şöyle bir sonuç görürsünüz:

![Visual Studio başarılı derleme çıkışı](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Hata Listesi gözden geçirin

Daha önce ve başarıyla derlediğiniz kodda herhangi bir değişiklik yapmadığınız takdirde muhtemelen bir hata oluştu. Kodlamadan yeni başladıysanız büyük olasılıkla çok sayıda ihtiyacınız vardır. Hatalar bazen basit bir sözdizimi hatası veya yanlış değişken adı gibi belirgin bir şekilde görünür ve bazen sizi rehberlik etmek için yalnızca şifreli kodla anlaşılması zordur. Sorunların temizleyici bir görünümü için, yapı **Çıkış** penceresinin alt kısmına gidin ve **hata listesi** sekmesine tıklayın. Böylece projeniz için hataların ve uyarıların daha ayrıntılı bir görünümüne gidersiniz ve bazı ek seçenekler de sunulur.

![Visual Studio çıktısı ve Hata Listesi](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Hatanın oluştuğu satıra gitmek için **hata listesi** penceresindeki hata satırına tıklayın. (Veya **CTRL** + tuşuna basarak satır numaralarını açın **S**, **satır numaralarını** yazın ve ardından sonuçlarda **satır numaralarını aç veya kapat** seçeneğini seçin. Bu, satır numaralarını açmak için kullanabileceğiniz **Seçenekler** iletişim kutusuna almanın en hızlı yoludur.)

![Satır numaralarıyla Visual Studio Düzenleyicisi](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Visual Studio satır numaraları seçeneği](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

 + Hatanın oluştuğu satır numarasına hızlıca gitmek için CTRL **G** tuşuna basın.

Hata kırmızı bir "dalgalı çizgi" alt çizgi ile tanımlanır. Ek ayrıntılar için üzerine gelin. Düzeltmeyi yapın ve düzeltme ile yeni bir hata ortaya çıkabilir. (Bu, "gerileme" olarak adlandırılır.)

![Visual Studio hatası üzerine gelme](../ide/media/vs_ide_gs_debug_error_hover1.png)

Hata listesini gözden geçir ve kodunuzdaki tüm hataları çözün.

![Visual Studio hata ayıklama hataları penceresi](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Hataları ayrıntılı olarak inceleyin

Birçok hata, derleyici koşullarında olduğu gibi phrased, size hiçbir fikir vermeyebilir. Bu gibi durumlarda ek bilgilere ihtiyacınız olacaktır. **Hata listesi** penceresinden, hata veya uyarı hakkında daha fazla bilgi Için otomatik Bing araması yapabilirsiniz. Karşılık gelen giriş satırına sağ tıklayın ve bağlam menüsünden **hata yardımını göster** ' i seçin veya **hata listesi** **kod** sütunundaki köprülü hata kodu değerine tıklayın.

![Visual Studio hata listesi Bing arama](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

Ayarlarınıza bağlı olarak, Web tarayıcınız hata kodu ve metin için arama sonuçlarını görüntüler ya da Visual Studio içinde bir sekme açılır ve Bing aramasının sonuçlarını gösterir. Sonuçlar Internet 'teki birçok farklı kaynaktan alınır ve hepsi yararlı olmayabilir.

## <a name="use-code-analysis"></a>Kod analizini kullanma

Kod Çözümleyicileri, kod yönetiminde çalışma zamanı hatalarına veya problemlere yol açabilecek ortak kod sorunlarına bakar.

### <a name="c-and-visual-basic-code-analysis"></a>C# ve Visual Basic kodu Analizi

Visual Studio, siz yazarken C# ve Visual Basic kodunu inceleyecek yerleşik bir [.net Compiler platform Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md) kümesi içerir. Ek Çözümleyicileri bir Visual Studio uzantısı veya bir NuGet paketi olarak yükleyebilirsiniz. Kural ihlalleri bulunursa, bunlar hem Hata Listesi hem de kod düzenleyicisinde, sorunlu kodun altında bir dalgalı çizgi olarak raporlanır.

### <a name="c-code-analysis"></a>C++ kod analizi

C++ kodunu çözümlemek için [Statik kod analizini](/cpp/code-quality/quick-start-code-analysis-for-c-cpp)çalıştırın. Başarılı bir derlemeyi önleyen açık hataları temizledikten sonra bu uygulamayı çalıştırmanın önleminizi alarak ' ine ulaşın ve üretebilen uyarıları ele almanız biraz zaman atalım. Yolculuğuna giden bir süre sonra tasarruf edersiniz ve birkaç kod stili tekniği öğrenebilirsiniz.

 + Statik kod analizini başlatmak için alt **F11** tuşuna basın (veya   >  üst menüden **çözüm Çalıştır kod analizini Çözümle '** yi seçin).

![Visual Studio Code analiz menü öğesi](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Tüm yeni veya güncelleştirilmiş uyarılar, IDE 'nin altındaki **hata listesi** sekmesinde görüntülenir. Koda gitmek için uyarılara tıklayın.

![Uyarılarla Visual Studio Hata Listesi](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Kodu onarmak veya yeniden düzenleme için hızlı eylemleri kullanma

Ampul veya screwsürücü simgesinde bulunan [hızlı eylemler](../ide/quick-actions.md), kodu satır içi olarak yeniden oluşturmanızı sağlar. C#, C++ ve Visual Basic kodundaki yaygın uyarıları hızla ve etkili bir şekilde gidermenin kolay bir yoludur. Bunlara erişmek için, bir uyarı dalgalı çizgi ' ye sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler**' i seçin. Ya da imlecinizin renkli dalgalı çizgi üzerindeyken, **CTRL** tuşuna basın + **.** ya da kenar boşluğunda ampul, hata ampulü veya screwsürücü simgesini seçin. Bu kod satırına uygulayabileceğiniz olası düzeltmelerin veya yeniden düzenlemeler listesini görürsünüz.

![Visual Studio ampul Önizleme](../ide/media/quick-actions-options.png)

Hızlı Eylemler, kod Çözümleyicileri kodunuzun düzeltilmesi, yeniden düzenlenmesi veya geliştirilmesi için bir fırsat olduğunu tespit eden her yerde kullanılabilir. Herhangi bir kod satırına tıklayın, bağlam menüsünü açmak için sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler**' ı seçin. Yeniden düzenleme veya geliştirme seçenekleri varsa, bunlar görüntülenir. Aksi takdirde, **burada hızlı eylem bulunmayan** ILETI, IDE 'nin sol alt köşesinde görüntülenir.

![Kullanılabilir hızlı eylem yok metin](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Deneyim ile hızlı bir şekilde ok tuşlarını ve **CTRL tuşunu** kullanabilirsiniz + **.** kolay yeniden düzenleme fırsatlarını denetlemek ve kodunuzu temizlemek için!

::: moniker range="vs-2019"

## <a name="run-code-cleanup"></a>Kod temizlemeyi Çalıştır

Visual Studio, kod stili tercihleri de dahil olmak üzere [C# kod dosyası](code-styles-and-code-cleanup.md#apply-code-styles)için, düzenleyicinin alt kısmındaki **kod temizleme** düğmesi aracılığıyla isteğe bağlı biçimlendirme sağlar.

![Visual Studio 2019 ' de kod temizleme düğmesi](media/execute-code-cleanup.png)

Dosyanızı boşluk, girintiler, et cetera için biçimlendirmeye ek olarak, **kod temizleme** de tanımladığınız bir kod stili kuralları kümesi uygular. Her kod stili için tercihleriniz, proje için bir tane varsa veya **Seçenekler** iletişim kutusundaki [kod stili ayarlarından](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) , [editorconfig dosyasından](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)okunurdur.

::: moniker-end

## <a name="debug-your-running-code"></a>Çalışan kodunuzda hata ayıklayın

Kodunuzu başarıyla oluşturduğunuza ve küçük bir temizlik gerçekleştirdiniz, **F5** tuşuna basarak veya **hata** ayıklama  >  **başlatma hata ayıklamayı** seçerek çalıştırın. Bu, uygulamanızı ayrıntılı bir şekilde gözlemleyebileceğiniz bir hata ayıklama ortamında başlatır. Visual Studio IDE, uygulamanız çalışırken değişir: **Çıkış** penceresi iki yeni durumla değiştirilir (varsayılan pencere yapılandırmasında), **oto s/Yereller/izle** sekmeli penceresi ve **çağrı yığını/kesme noktaları/özel durum ayarları/çıkış** sekmeli pencere. Bu pencerelerin, uygulamanın değişkenlerini, iş parçacıklarını, çağrı yığınlarını ve çalışırken çeşitli diğer davranışları incelemenizi ve değerlendirmenizi sağlayan birden çok sekme vardır.

![Visual Studio oto ve çağrı yığını pencereleri](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

**SHIFT** + **F5** tuşuna basarak veya **Durdur** düğmesine tıklayarak uygulamanızı durdurun. Ya da yalnızca uygulamanın ana penceresini (veya komut satırı iletişim kutusunu) kapatabilirsiniz.

Kodunuz mükemmel bir şekilde ve tam olarak beklendiği gibi çalışırsa, tebrikler! Ancak, yanıt vermeyi durdurursa veya kilitlenirse ya da bazı garip sonuçlar verdiyse, bu sorunların kaynağını bulmanız ve hataları çözmeniz gerekir.

### <a name="set-simple-breakpoints"></a>Basit kesme noktaları ayarla

[Kesme noktaları](../debugger/using-breakpoints.md) , güvenilir hata ayıklamanın en temel ve temel özelliğidir. Bir kesme noktası, Visual Studio 'Nun çalışan kodunuzu askıya alması gerektiğini gösterir; böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz. Kesme noktalarını ayarlayıp kaldırdıktan sonra bir projeyi yeniden oluşturmanız gerekmez.

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
