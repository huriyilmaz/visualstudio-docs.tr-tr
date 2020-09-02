---
title: Visual Studio 'da hata ayıklamaya Başlarken 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca3f3806f9097082d71dd80e74ccf48cd78c951b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386894"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Visual Studio 2015'te Hata Ayıklamaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015, güçlü tümleşik bir proje derleme ve hata ayıklama araçları kümesi sağlar. Bu konu başlığında, en temel hata ayıklama Kullanıcı arabirimi özelliklerini kullanmaya nasıl başlayabileceğinizi öğrenin.

 Note: bu sayfanın en altında daha gelişmiş özelliklere ve platforma veya özelliklere özgü konulara bağlantılar bulunur.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Kodum çalışmıyor. Yardım, Visual Studio 2015!
 Bu nedenle düzenleyiciyi iletişime ve bazı kodlar oluşturdunuz. Şimdi bu kodun hata ayıklamasını başlatmak istiyorsunuz. Visual Studio 2015 ' de, çoğu IDE 'de olduğu gibi, hata ayıklama için iki aşama vardır: proje ve derleyici hatalarını yakalamak ve çözümlemek için kod oluşturma; ve çalışma zamanı ve dinamik hataları yakalamak ve çözümlemek için bu kodu ortamda çalıştırmak.

### <a name="configuring-a-build"></a>Bir derlemeyi yapılandırma
 İki temel tür derleme yapılandırması vardır: **hata ayıklama** ve **yayın**. İlk yapılandırma, daha zengin bir etkileşimli çalışma zamanı hata ayıklama deneyimine izin veren, ancak hiçbir zaman gönderilmemesi gereken daha yavaş, daha büyük bir yürütülebilir dosya oluşturur. İkincisi, sevk etmek için uygun olan daha hızlı, daha iyileştirilmiş bir yürütülebilir dosya oluşturur (en azından derleyicinin perspektifinden).

 Varsayılan derleme yapılandırması **hata ayıklaması**.

 ![Visual Studio hata ayıklama derleme düğmesi](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 Ayrıca, hedef için **x86** (32 bit Intel CPU), **x64** (64 bit Intel CPU) ve **ARM** (ARM CPU 'lar) gibi belirli bir yapı platformunu da belirtebilirsiniz. Yönetilen ve yerel projeler için varsayılan değer  **x86** ' dır. Bunu değiştirmek için, oluştur Platform açılan menüsüne tıklayın ve farklı bir platform veya **Configuration Manager..** . seçin.

 ![Visual Studio yapılandırma Dosya Yöneticisi penceresi](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 **Configuration Manager**kullanarak hedeflenen bir yapı yapılandırması belirleyebilirsiniz. Başlatın, **yapılandırma** veya **CPU** açılan listesine tıklayın ve **yeni...** seçeneğini belirleyin. Yeni bir yapı veya platform oluşturmak için.

 ![Visual Studio Configuration Manager penceresi](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 Başlarken, sırasıyla derleme yapılandırması ve platform olarak **hata ayıklama** ve **x86** kullanmanız yeterlidir. Kodlama ve hata ayıklamayı tamamladığınızda, yapılandırmayı **serbest** bırakmak ve belirli bir platformu hedeflemek için değiştirin. (Visual Studio 'nun eski sürümleri, .NET kod projeleri için bir **anycpu** varsayılan platformu sağlamıştır.)

 Note: projenizi oluşturduğunuzda, çalıştırılabilir dosyayı depolamak için hangi proje dizin yolunun oluşturulduğunu belirlemek için yapılandırma ve platform değerleri de kullanılır. Genellikle bu ** \<path-to-project> \\<proje adı \> \\<yapılandırma \> \\<platformudur \> **. Örneğin, yapılandırması ve platformu olan bir proje `Debug` `x86` altında bulunur `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86` . Bu derlenmiş yürütülebilir dosyaları yöneten kendi araçlarınız veya betikleriniz varsa, bu yararlı olabilir.

### <a name="building-your-code"></a>Kodunuzu oluşturma
 Derlemeniz yapılandırıldıktan sonra, projenizi gerçekten derlemek zaman alabilir. F7 tuşuna basmanız için bunu yapmanın en kolay yolu, ancak ana menüden **Build->Build Solution** öğesini seçerek derlemeyi de başlatabilirsiniz.

 ![Visual Studio derleme projesi menü seçimi](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 Yapı sürecini, Visual Studio Kullanıcı arabiriminin altındaki **Çıkış** durumu penceresinde gözlemleyebilirsiniz. Hatalar, uyarılar ve derleme işlemleri burada görüntülenir. Hatalar varsa (veya yapılandırılmış bir düzeyin üzerinde bir uyarılarınız varsa), derlemeniz başarısız olur. Oluşan satıra gitmek için hatalara ve uyarılara tıklayabilirsiniz. Bir kez **F7** tuşuna basarak (yalnızca hataları olan dosyaları yeniden derlemek için) veya **Ctrl + Alt + F7** (temiz ve tamamen yeniden oluşturma için), projenizi yeniden derleyin.

 Düzenleyicinin altındaki sonuçlar penceresinde iki derleme sekmeli pencere vardır: ham derleyici çıkışını (hata iletileri dahil) içeren **Çıkış** penceresi; ve tüm hataların ve uyarıların sıralanabilir ve filtrelenebilir bir listesini sağlayan **hata listesi** pencere.

 Başarılı olduğunda, **Çıkış** penceresinde bunun gibi sonuçlar görürsünüz.

 ![Visual Studio başarılı derleme çıkışı](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>Hata Listesi gözden geçiriliyor
 Daha önce ve başarıyla derlediğiniz kodda herhangi bir değişiklik yapmadığınız takdirde muhtemelen bir hata oluştu. Kodlamadan yeni başladıysanız büyük olasılıkla çok sayıda ihtiyacınız vardır. Hatalar bazen basit bir sözdizimi hatası ya da yanlış değişken adı gibi belirgin bir şekilde görünür ve bazı durumlarda size rehberlik etmek için yalnızca şifreli kodla anlaşılması zordur. Sorunların temizleyici bir görünümü için, yapı **Çıkış** penceresinin alt kısmına gidin ve **hata listesi** sekmesine tıklayın. Böylece projeniz için hataların ve uyarıların daha ayrıntılı bir görünümüne gidersiniz ve bazı ek seçenekler de sunulur.

 ![Visual Studio 2015 çıktı ve Hata Listesi](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 **Hata listesi** penceresindeki hata satırına tıklayın ve hatanın oluştuğu satıra atlayın. (Veya satır numaralarını açmak için sağ üst köşedeki **Hızlı Başlat** çubuğuna tıklayıp "satır numaraları" yazın ve ENTER tuşuna basın. Bu, satır numaralarını açmak için **Seçenekler** penceresi girişini almanın en hızlı yoludur. **Hızlı başlatma** çubuğunu kullanmayı öğrenin ve kendinize çok sayıda kullanıcı arabirimi tıklamasına sahip olun!)

 ![Satır numaralarıyla Visual Studio Düzenleyicisi](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Visual Studio satır numaraları seçeneği](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Hatanın oluştuğu satır numarasına hızlıca gitmek için CTRL + G tuşlarını kullanın.

 Hata kırmızı bir "dalgalı çizgi" alt çizgi ile tanımlanır. Ek ayrıntılar için üzerine gelin. Düzeltmeyi yapın ve düzeltme ile yeni bir hata ortaya çıkabilir. (Bu, "gerileme" olarak adlandırılır.)

 ![Visual Studio hatası üzerine gelme](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 Hata listesini gözden geçir ve kodunuzdaki tüm hataları çözün.

 ![Visual Studio hata ayıklama hataları penceresi](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>Hataları ayrıntılı olarak gözden geçirme
 Birçok hata, derleyici koşullarında olduğu gibi phrased, size hiçbir fikir vermeyebilir. Bu gibi durumlarda ek bilgilere ihtiyacınız olacaktır. **Hata listesi** penceresinden, ilgili giriş satırına sağ tıklayıp bağlam menüsünden **hata yardımını göster** ' i seçerek hata (veya uyarı) hakkında daha fazla bilgi için otomatik Bing araması yapabilirsiniz.

 ![Visual Studio hata listesi Bing arama](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 Bu, Visual Studio 2015 içinde hata kodu ve metin için Bing aramasının sonuçlarını barındıran bir sekme başlatır. Sonuçlar Internet 'teki birçok farklı kaynaktan alınır ve hepsi yararlı olmayabilir.

 Alternatif olarak, **hata listesi** **kod** sütunundaki köprülü hata kodu değerine tıklayabilirsiniz. Bu, yalnızca hata kodu için Bing aramasını başlatır.

### <a name="performing-static-code-analysis"></a>Statik kod analizi gerçekleştirme
 "Statik kod analizi", "kod yönetiminde çalışma zamanı hatalarına veya sorunları ortaya çıkarmaya neden olan genel sorunlar için kodumu otomatik olarak denetle" diyen bir yoldur. Derlemeyi engellediği açık hataları temizledikten sonra bu uygulamayı çalıştırmanın habitine ulaşın ve üreteme uyarılarını ele almanız biraz zaman kazanın. Biraz daha fazla bilgi edinmek ve birkaç kod stili tekniği öğrenmek isteyeceksiniz.

 Statik kod analizini başlatmak için Alt + F11 tuşuna basın (veya üst menüden **Çözümle Kod analizini çalıştır >** seçin. Çok sayıda kodunuz varsa bu işlem biraz zaman alabilir.

 ![Visual Studio 2015 kod analizi menü öğesi](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 Tüm yeni veya güncelleştirilmiş uyarılar, IDE 'nin altındaki **hata listesi** sekmesinde görüntülenir. Bunlara gitmek için uyarılara tıklayın.

 ![Visual Studio 2015 uyarılarla Hata Listesi](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")

 Uyarılar, kırmızı bir şekilde değil, parlak sarı yeşil renkli bir çizgi ile belirlenir. Daha fazla ayrıntı için bunların üzerine gelin ve düzeltmeler veya yeniden düzenleme seçeneklerinde yardımcı olacak bağlam menüsünü almak için bunlara sağ tıklayın.

 ![Visual Studio Code çözümleme uyarısı üzerine gelme](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Kodu onarmak veya yeniden düzenleme için hafif bulbs kullanma
 Hafif bulbs, Visual Studio 2015 için kod satır içi yeniden düzenleme yapmanızı sağlayan yeni bir özelliktir. Yaygın uyarıları hızla ve etkili bir şekilde gidermenin kolay bir yoludur. Bunlara erişmek için, bir uyarı dalgalı çizgi öğesine sağ tıklayın (veya CTRL + tuşlarına basın. dalgalı çizgi üzerine geldiğinizde) ve sonra **hızlı işlemler**' i seçin.

 ![Visual Studio 2015 ampul hızlı seçenekleri](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 Bu kod satırına uygulayabileceğiniz olası düzeltmelerin veya şunların listesini görürsünüz.

 ![Visual Studio 2015 ampul Önizleme](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 Açık bulbs, kod çözümleyicilerinin kodunuzun düzeltilmesi, yeniden düzenlenmesi veya geliştirilmesi için bir fırsat olduğunu tespit eden her yerde kullanılabilir. Herhangi bir kod satırına tıklayın, bağlam menüsünü açmak için sağ tıklayın ve **hızlı seçenekler** ' i seçin (veya verimlilik tercih ediyorsanız, CTRL +.) tuşuna basın. Kullanılabilir alan yeniden düzenleme veya geliştirme seçenekleri varsa, bunlar görüntülenir; Aksi takdirde ileti, `No quick options available here` IDE 'nin sol alt köşesinde görüntülenir.

 ![Visual Studio 2015 ampul ' seçenek yok ' metin](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 Deneyimle, ok tuşlarını ve CTRL + tuşlarını hızlıca kullanabilirsiniz. Hızlı seçenek yeniden düzenleme fırsatlarını denetlemek ve kodunuzu temizlemek için!

 Hafif bulbs hakkında daha fazla bilgi edinmek için [hafif bulbs ile hızlı eylemler gerçekleştirin](../ide/perform-quick-actions-with-light-bulbs.md).

### <a name="debugging-your-running-code"></a>Çalışan kodunuzda hata ayıklama
 Kodunuzu başarıyla oluşturduğunuza ve az bir temizlik gerçekleştirdiniz, F5 tuşuna basarak veya **hata ayıklamayı >Başlat**' ı seçerek çalıştırın. Bu işlem, uygulamanızı ayrıntılı bir şekilde gözlemleyebileceğiniz bir hata ayıklama ortamında başlatacak. Visual Studio 2015 IDE, uygulamanız çalışırken değişir: **Çıkış** penceresi iki yeni durumla (varsayılan pencere yapılandırmasında), **oto s/Yereller/modüller/izle** sekmeli pencere ve **çağrı yığını/kesme noktaları/özel durum ayarları/çıkış** sekmeli penceresinde değiştirilir. Bu pencerelerin, uygulamanın değişkenlerini, iş parçacıklarını, çağrı yığınlarını ve çalışırken çeşitli diğer davranışları incelemenizi ve değerlendirmenizi sağlayan birden çok sekme vardır.

 ![VS2015 oto ve çağrı yığını pencereleri](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 Uygulamanız ile ilgili çeşitli eylemleri deneyin ve değişiklikleri gözlemleyin. Olağan dışı bir şey görünürse, Ctrl + Alt + Break tuşlarına basarak uygulamayı duraklatın (veya **Duraklat** düğmesine tıklayın).

 ![Visual Studio tümünü Kes düğmesi](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 Uygulamayı çalıştırmaya devam etmek için F5 tuşuna basın (veya **devam** düğmesine tıklayın).

 ![Visual Studio hata ayıklama devam düğmesi](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 SHIFT + F5 tuşlarına basarak veya **Durdur** düğmesine tıklayarak uygulamanızı durdurabilirsiniz. Ya da yalnızca uygulamanın ana penceresini (veya komut satırı iletişim kutusunu) kapatabilirsiniz.

 Kodunuz mükemmel bir şekilde ve tam olarak beklendiği gibi çalışırsa, tebrikler! Derleme yapılandırmasını **yayın** olarak değiştirin ve dağıtım için yeniden derleyin! (Uzmanlar, en sonunda birim testinde bit 'e geçmek isteyebilir, ancak.) Ancak, yanıt vermeyi durdurursa veya kilitlenirse ya da bazı garip sonuçlar verdiyse, bu sorunların kaynağını bulmanız ve hataları çözmeniz gerekir.

### <a name="setting-simple-breakpoints"></a>Basit kesme noktalarını ayarlama
 Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Bir kesme noktası, Visual Studio 'Nun çalışan kodunuzu askıya alması gerektiğini gösterir; böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz. Kesme noktalarını ayarlayıp kaldırdıktan sonra bir projeyi yeniden oluşturmanız gerekmez.

 Kesmenin gerçekleşmesini istediğiniz çizginin uzak kenar boşluğuna tıklayarak bir kesme noktası ayarlayın veya kod satırını seçip F9 tuşuna basın. Kodunuzu çalıştırdığınızda bu kod satırıyla ilgili yönergelerin yürütülmesi durdurulur.

 ![Visual Studio kesme noktası](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 Kod kesildiğinde, işaretlenen kod satırı henüz yürütülmemiştir. Bu noktada, kesme noktası tarafından işaretlenen kod satırıyla ilgili yönergeleri çalıştırmak ve değiştirilen değerleri incelemek isteyebilirsiniz. Bu, kodu "Adımlama" olarak adlandırılır. İşaretlenen kod bir yöntem çağrısý ise, F11 tuşuna basarak buna adım adım ekleyebilirsiniz. Ayrıca, F10 tuşuna basarak kod satırını "adımla" de yapabilirsiniz. Kesme noktası adımı eylemleri hakkında daha fazla bilgi için, [hata ayıklayıcıyla kod aracılığıyla gezinme](../debugger/navigating-through-code-with-the-debugger.md)makalesini okuyun.

 Kesme noktaları için genel kullanımlar şunları içerir:

1. Bir kilitlenme veya programın kaynağını daraltmak için, yanıt vermeyen yöntem çağrısının tamamında ve çevresinde bu hataya neden olduğunu düşündüz. Kodda ilerlediklerinde, sorunlu kod satırını bulana kadar kesme noktalarını kaldırın ve daha sonra sıfırlayın.

2. Yeni kod aldığınızda, bunun başlangıcında bir kesme noktası ayarlayın ve beklenen şekilde davrandığından emin olmak için kodda ilerleyin.

3. Karmaşık bir davranış uyguladıysanız, algoritmik kodu için kesme noktaları ayarlayın, böylece program kesildiğinde değişkenlerin ve verilerin değerlerini inceleyebilirsiniz.

4. C veya C++ kodu yazıyorsanız, kodu durdurmak için kesme noktaları kullanın, böylece bellekle ilgili hatalarda hata ayıklarken adres değerlerini (NULL ara) ve başvuru sayılarını inceleyebilirsiniz.

   Kesme noktaları kullanma hakkında daha fazla bilgi için [kesme noktaları kullanarak](../debugger/using-breakpoints.md) okuyun

### <a name="setting-conditional-breakpoints"></a>Koşullu kesme noktaları ayarlanıyor
 Bir döngüde veya özyinelemedeki bir kesme noktası varsa veya sık sık adımtığınız çok sayıda kesme noktasına sahipseniz, kodunuzun yalnızca belirli koşullar karşılandığında askıya alındığından emin olmak için koşullu bir kesme noktası kullanın. Aksi takdirde, F11 tuşuna basan çok büyük.

 Bir değişken belirli bir değere ayarlandığında veya belirli bir eşiği geçtiğinde, koşullu bir kesme noktası ayarlamak ve kodunuzu askıya almak için, bir kesme noktası ayarlamak için kenar boşluğuna tıklayın ve sonra görüntülenen vurgulu menüden "COG" yi seçin.

 ![Visual Studio 2015 kesme noktası ayarları](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 Aşağıdaki gibi görünen bir iletişim kutusu görürsünüz. bu şekilde, kesmenin gerçekleşmesi için belirli koşullar ayarlayabilirsiniz.

 ![Visual Studio 2015 koşullu kesme noktası](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 Koşullu kesme noktalarını değerlendirmek için kullanılan ifadelerin nasıl bildirildiği hakkında daha fazla bilgi için [Visual Studio 2015 ' de Channel9 video kesme noktası yapılandırma deneyimine](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)göz atın.

### <a name="inspecting-your-code-at-run-time"></a>Çalışma zamanında kodunuzu İnceleme
 Çalışan kodunuz bir kesme noktası ve halden sonra ziyaret edildiğinde, değişkenlerinizi inceleyebilir ve neler olduğunu belirlemek için yığınları çağırabilirsiniz. Görmeyi düşündüğünüz aralıklardaki değerler mi? Çağrılar doğru sırada yapılıyor mu?

 ![Visual Studio 2015 çalışma&#45;zaman değeri incelemesi](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")

 Şu anda içerdiği değerleri ve başvuruları görmek için bir değişkenin üzerine gelin. Beklemediğiniz bir değer görürseniz, büyük olasılıkla kodun önceki veya arama satırlarındaki bir hata olabilir. Aramanızı daha da daraltmak için kesme noktalarını yukarı taşıyın veya mevcut kesme noktalarına koşullar ekleyin.

 Ayrıca, Visual Studio 2015, uygulamanızın CPU ve bellek kullanımını zaman içinde gözlemleyebileceğiniz Tanılama Araçları penceresini görüntüler. Tahmin edilemeyen ağır CPU kullanımı veya bellek ayırmayı aramak için bunları kullanın. Beklenmedik ağır kullanım veya yayınlanmamış kaynaklara neden olduğunu belirlemek için **izleme** penceresi ve kesme noktaları ile birlikte kullanın.

 ![Visual Studio 2015 Tanılama Araçları penceresi](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>Birim testlerini çalıştırma
 Birim testleri, uygulamanızda veya hizmetinizde kod yolları sunan programlardır. Visual Studio 2015 hem yönetilen hem de yerel kod için Microsoft birim testi çerçevelerini yüklüyor. Birim testleri oluşturmak, çalıştırmak ve bu testlerin sonuçlarını raporlamak için bir birim test çerçevesi kullanın. Kodunuzun doğru şekilde çalışmaya devam ettiğinden testte değişiklik yaptığınızda birim testlerini yeniden çalıştırın. Visual Studio 2015 Enterprise kullandığınızda, her derlemeden sonra testleri otomatik olarak çalıştırabilirsiniz.

 Başlamak için, [IntelliTest ile kodunuz için birim testleri oluşturma](../test/generate-unit-tests-for-your-code-with-intellitest.md)makalesini okuyun.

 Visual Studio 2015 ' de birim testleri hakkında daha fazla bilgi edinmek ve bunların daha iyi kalite kodu oluşturmanıza nasıl yardımcı olabileceğini öğrenmek için [birim testi temel bilgilerini](../test/unit-test-basics.md)okuyun.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio](../debugger/debugging-in-visual-studio.md) [hata ayıklayıcı ayarlarında hata ayıklama ve hazırlık](../debugger/debugger-settings-and-preparation.md) [hata ayıklama 64-bit uygulamalar](../debugger/debug-64-bit-applications.md) [hata ayıklayıcı temelleri](../debugger/debugger-basics.md)
