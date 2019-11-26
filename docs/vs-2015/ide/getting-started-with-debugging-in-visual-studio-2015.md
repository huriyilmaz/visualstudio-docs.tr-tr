---
title: Visual Studio 2015'te hata ayıklamaya başlama | Microsoft Docs
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
ms.openlocfilehash: fe8b158fd870b83b39b9d316e68582f2726d89bb
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300196"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Visual Studio 2015'te Hata Ayıklamaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 proje derleme ve hata ayıklama araçları, güçlü tümleşik sunmaktadır. Bu konu başlığında, en temel hata ayıklama kullanıcı Arabirimi özellikleri kümesi kullanmaya başlamak nasıl öğrenin.

 Not: Bu sayfanın alt kısmında daha gelişmiş özellikleri ve platform veya özelliğe özgü konulara bağlantılar vardır.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Benim kodumu çalışmaz. Me, Visual Studio 2015 yardımcı olun!
 Böylece düzenleyicisini verdi ve bazı kod oluşturdunuz. Artık, kod hata ayıklamayı başlatmak istediğiniz. Visual Studio 2015'te çoğu ıde'lerle gibi hata ayıklama için iki aşama vardır: yakalayın ve proje ve derleme hatalarını; kod oluşturma Bu kodu yakalamak ve çalışma zamanı ve dinamik hatalarını gidermek için ortamında ve çalıştırma.

### <a name="configuring-a-build"></a>Bir derleme yapılandırma
 İki temel tür derleme yapılandırması vardır: **hata ayıklama** ve **yayın**. İlk Yapılandırma bir daha zengin etkileşimli çalışma zamanı hata ayıklama deneyimi sağlar, ancak hiçbir zaman sevk edilmesi gereken bir yavaş, daha büyük çalıştırılabilir dosyası oluşturur. İkinci göndermeye uygun olan daha hızlı, daha en iyi duruma getirilmiş bir çalıştırılabilir derlemeleri (en az derleyici perspektifinden).

 Varsayılan derleme yapılandırması **hata ayıklaması**.

 ![Visual Studio hata ayıklama derleme düğmesi](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 Ayrıca, hedef için **x86** (32 bit Intel CPU), **x64** (64 bit Intel CPU) ve **ARM** (ARM CPU 'lar) gibi belirli bir yapı platformunu da belirtebilirsiniz. Yönetilen ve yerel projeler için varsayılan değer **x86** ' dır. Bunu değiştirmek için, oluştur Platform açılan menüsüne tıklayın ve farklı bir platform veya **Configuration Manager..** . seçin.

 ![Visual Studio yapılandırma Dosya Yöneticisi penceresi](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 **Configuration Manager**kullanarak hedeflenen bir yapı yapılandırması belirleyebilirsiniz. Başlatın, **yapılandırma** veya **CPU** açılan listesine tıklayın ve **yeni...** seçeneğini belirleyin. Yeni derleme veya platformu oluşturmak için.

 ![Visual Studio Configuration Manager penceresi](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 Başlarken, sırasıyla derleme yapılandırması ve platform olarak **hata ayıklama** ve **x86** kullanmanız yeterlidir. Kodlama ve hata ayıklamayı tamamladığınızda, yapılandırmayı **serbest** bırakmak ve belirli bir platformu hedeflemek için değiştirin. (Visual Studio 'nun eski sürümleri, .NET kod projeleri için bir **anycpu** varsayılan platformu sağlamıştır.)

 Not: projenizi yapılandırdığınızda, yapılandırma ve platform değerler da yürütülebilir dosya depolamak için hangi proje dizin yolu oluşturulup belirlemek için kullanılır. Genellikle bu **\<yolundan projeye >\\< proje-adı\>\\< yapılandırma\>\\< platform\>** . Örneğin, `Debug` yapılandırmasına sahip bir proje ve `x86` platformu `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`altında bulunur. Bu, kendi araçları veya bu yerleşik yürütülebilir dosyaları yönetme betikleriniz varsa yararlı olabilir.

### <a name="building-your-code"></a>Kod oluşturma
 Yapınızı ile yapılandırılmış, aslında derleme zamanı geldi. F7 tuşuna basmanız için bunu yapmanın en kolay yolu, ancak ana menüden **Build-> Build Solution** öğesini seçerek derlemeyi de başlatabilirsiniz.

 ![Visual Studio derleme projesi menü seçimi](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 Yapı sürecini, Visual Studio Kullanıcı arabiriminin altındaki **Çıkış** durumu penceresinde gözlemleyebilirsiniz. Hataları, uyarıları ve yapı işlemleri burada görüntülenir. Hata (veya yapılandırılan bir düzey bir uyarı olup olmadığını) varsa, yapınız başarısız olur. Hataları ve Uyarıları nerede oluştuğunu satıra gitmek için tıklayabilirsiniz. Bir kez **F7** tuşuna basarak (yalnızca hataları olan dosyaları yeniden derlemek için) veya **Ctrl + Alt + F7** (temiz ve tamamen yeniden oluşturma için), projenizi yeniden derleyin.

 Düzenleyicinin altındaki sonuçlar penceresinde iki derleme sekmeli pencere vardır: ham derleyici çıkışını (hata iletileri dahil) içeren **Çıkış** penceresi; ve tüm hataların ve uyarıların sıralanabilir ve filtrelenebilir bir listesini sağlayan **hata listesi** pencere.

 Başarılı olduğunda, **Çıkış** penceresinde bunun gibi sonuçlar görürsünüz.

 ![Visual Studio başarılı derleme çıkışı](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>Hata listesini gözden geçirme
 Daha önce ve başarıyla derlenen kod için herhangi bir değişiklik yapmış olduğunuz sürece, muhtemelen bir hata vardır. Kodlamaya yeniyseniz, muhtemelen bunlardan çok fazla vardır. Hataları bazen belirgin, böyle bir basit söz dizimi hatası veya yanlış bir değişken adı ve bazı durumlarda, size yol göstermesi için yalnızca bir şifreli koduyla anlaşılması zor. Sorunların temizleyici bir görünümü için, yapı **Çıkış** penceresinin alt kısmına gidin ve **hata listesi** sekmesine tıklayın. Böylece projeniz için hataların ve uyarıların daha ayrıntılı bir görünümüne gidersiniz ve bazı ek seçenekler de sunulur.

 ![Visual Studio 2015 çıktı ve Hata Listesi](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 **Hata listesi** penceresindeki hata satırına tıklayın ve hatanın oluştuğu satıra atlayın. (Veya satır numaralarını açmak için sağ üst köşedeki **Hızlı Başlat** çubuğuna tıklayıp "satır numaraları" yazın ve ENTER tuşuna basın. Bu, satır numaralarını açmak için **Seçenekler** penceresi girişini almanın en hızlı yoludur. **Hızlı başlatma** çubuğunu kullanmayı öğrenin ve kendinize çok sayıda kullanıcı arabirimi tıklamasına sahip olun!)

 ![Satır numaralarıyla Visual Studio Düzenleyicisi](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Visual Studio satır numaraları seçeneği](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Hatanın oluştuğu satır numarasına hızla gitmek için CTRL + g'tuşlarını kullanın.

 Hata, kırmızı bir "dalgalı çizgi" alt çizgi ile tanımlanır. Üzerinde ek detaylar için üzerine gelin. Düzeltme yapmak ve yeni bir hata düzeltmesi yükleyebilecek olsa da çalıştırmayı, geçer. (Bu bir "regresyon" olarak adlandırılır.)

 ![Visual Studio hatası üzerine gelme](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 Hata listesi izlemek ve kodunuzda tüm hatalarla ilgilenin.

 ![Visual Studio hata ayıklama hataları penceresi](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>Ayrıntılı hataları gözden geçirme
 Birçok hatayı yok, derleyicinin koşullarını oldukları gibi tümcecik oluşturulmuş mantıklı olabilir. Bu gibi durumlarda ek bilgilere ihtiyacınız olacaktır. **Hata listesi** penceresinden, ilgili giriş satırına sağ tıklayıp bağlam menüsünden **hata yardımını göster** ' i seçerek hata (veya uyarı) hakkında daha fazla bilgi için otomatik Bing araması yapabilirsiniz.

 ![Visual Studio hata listesi Bing arama](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 Bu, Visual Studio 2015 konakları bir Bing sonuçlarının hata kodu ve metin arama içinde bir sekmesinde çalıştırır. Internet'teki birçok farklı kaynaklardan sonuçları olan ve tüm yararlı olabilir.

 Alternatif olarak, **hata listesi** **kod** sütunundaki köprülü hata kodu değerine tıklayabilirsiniz. Bu işlem, Bing arama yalnızca hata kodunu başlatılır.

### <a name="performing-static-code-analysis"></a>Statik kod analizini gerçekleştirme
 "Statik kod analizi", "çalışma zamanı hatalarına neden olabilecek yaygın sorunlar veya kod yönetimi sorunları için kendi kodum otomatik olarak denetle" etkisine başvurmaktan bir yoludur. Derleme önleme belirgin hataları temizledikten sonra çalışan alýþkanlýk alın ve bunu üretebilir uyarıları gidermek için biraz zaman alabilir. Kendiniz yol aşağı bazı zorlukların kaydedin, hem de birkaç kod stili teknikleri öğrenin.

 Statik kod analizini başlatmak için Alt + F11 tuşuna basın (veya üst menüden **Çözümle Kod analizini çalıştır >** seçin. Çok fazla kod varsa bu biraz zaman alabilir.

 ![Visual Studio 2015 kod analizi menü öğesi](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 Tüm yeni veya güncelleştirilmiş uyarılar, IDE 'nin altındaki **hata listesi** sekmesinde görüntülenir. Uyarıların bunlara atlamak için tıklayın.

 ![Visual Studio 2015 uyarılarla Hata Listesi](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")

 Uyarıları parlak bir sarı-yeşil dalgalı kırmızı bir tane yerine ile tanımlanır. Daha fazla ayrıntı için üzerine gelin ve bunları düzeltmeleri veya yeniden düzenleme seçeneklerini yardımcı olmak için bir bağlam menüsü almak için sağ tıklayın.

 ![Visual Studio Code çözümleme uyarısı üzerine gelme](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Ampuller kullanarak düzeltin veya kodu yeniden düzenleyin
 Ampuller olanak tanıyan Visual Studio 2015 için yeni bir özellik olan kod satır içi yeniden düzenleyin. Genel uyarıları gidermek için kolay bir yol oldukları hızla ve etkili bir şekilde. Bunlara erişmek için bir uyarı dalgalı oku üzerinde sağ tıklayın (veya CTRL tuşuna basın. dalgalı çizgi üzerine geldiğinizde) ve sonra **hızlı işlemler**' i seçin.

 ![Visual Studio 2015 ampul hızlı seçenekleri](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 Olası düzeltmeleri veya ilgili kod satırına uygulayabilirsiniz refactors listesini görürsünüz.

 ![Visual Studio 2015 ampul Önizleme](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 Ampuller, kod Çözümleyicileri, yeniden düzenleme, düzeltin veya kodunuzu geliştirmek için bir fırsat olup belirlemek her yerde kullanılabilir. Herhangi bir kod satırına tıklayın, bağlam menüsünü açmak için sağ tıklayın ve **hızlı seçenekler** ' i seçin (veya verimlilik tercih ediyorsanız, CTRL +.) tuşuna basın. Kullanılabilir alan yeniden düzenleme veya geliştirme seçenekleri varsa, bunlar görüntülenir; Aksi takdirde, `No quick options available here` ileti, IDE 'nin sol alt köşesinde görüntülenir.

 ![Visual Studio 2015 ampul ' seçenek yok ' metin](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 Deneyiminiz ok tuşları ve Ctrl + hızlı bir şekilde kullanabilirsiniz. için hızlı fırsatları yeniden düzenleme seçeneği işaretleyin ve kodunuzu oluşturan temizlemek için!

 Hafif bulbs hakkında daha fazla bilgi edinmek için [hafif bulbs ile hızlı eylemler gerçekleştirin](../ide/perform-quick-actions-with-light-bulbs.md).

### <a name="debugging-your-running-code"></a>Çalışan kodunuzun hatalarını ayıklama
 Kodunuzu başarıyla oluşturduğunuza ve az bir temizlik gerçekleştirdiniz, F5 tuşuna basarak veya **hata ayıklamayı > Başlat**' ı seçerek çalıştırın. Ayrıntılı davranışını görebilirsiniz. Bu nedenle bu bir hata ayıklama ortamında uygulamanızı başlatacak. Visual Studio 2015 IDE, uygulamanız çalışırken değişir: **Çıkış** penceresi iki yeni durumla (varsayılan pencere yapılandırmasında), **oto s/Yereller/modüller/izle** sekmeli pencere ve **çağrı yığını/kesme noktaları/özel durum ayarları/çıkış** sekmeli penceresinde değiştirilir. Bu windows inceleyin ve çalıştırdığı gibi uygulamanızın değişkenleri, iş parçacıkları, çağrı yığınları ve diğer çeşitli davranışların değerlendirme olanak tanıyan birden fazla sekme vardır.

 ![VS2015 oto ve çağrı yığını pencereleri](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 Çeşitli eylemler uygulamanızla çalışın ve değişiklikleri gözlemleyin. Olağan dışı bir şey görünürse, Ctrl + Alt + Break tuşlarına basarak uygulamayı duraklatın (veya **Duraklat** düğmesine tıklayın).

 ![Visual Studio tümünü Kes düğmesi](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 Uygulamayı çalıştırmaya devam etmek için F5 tuşuna basın (veya **devam** düğmesine tıklayın).

 ![Visual Studio hata ayıklama devam düğmesi](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 SHIFT + F5 tuşlarına basarak veya **Durdur** düğmesine tıklayarak uygulamanızı durdurabilirsiniz. Veya yalnızca uygulamanın ana pencere (veya komut satırı iletişim) kapatabilirsiniz.

 Kodunuzu mükemmel çalıştırdıysanız ve tam olarak bekleniyordu, Tebrikler! Derleme yapılandırmasını **yayın** olarak değiştirin ve dağıtım için yeniden derleyin! (Uzmanlar, en sonunda birim testinde bit 'e geçmek isteyebilir, ancak.) Ancak, askıda olursa veya kilitlenirse veya bazı garip sonuçlar verdiyse, bu sorunların kaynağını bulmanız ve hataları çözmeniz gerekir.

### <a name="setting-simple-breakpoints"></a>Basit kesme noktaları ayarlama
 Kesme noktaları güvenilir hata ayıklama en temel hem de temel özelliğidir. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız ya da bir dal kod getting run olup olmadığını gösterir. Bir projeyi ayarlama ve kesme noktaları kaldırma sonrasında yeniden gerekmez.

 Gerçekleşirse, kod satırını seçin veya F9 tuşuna basın, kesme istediğiniz kadar kenar boşluğunu satırının tıklayarak bir kesme noktası ayarlayın. Kodunuzu çalıştırmak, bu kod satırı yönergelerini yürütülmeden önce durdurur.

 ![Visual Studio kesme noktası](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 Kodu keserse işaretlenmiş kod satırının henüz yürütüldü değil. Bu noktada, kesme noktası işaretlenmiş kod satırının yönergeleri yürütmek ve değiştirilmiş değerleri incelemek isteyebilirsiniz. Bu, "içine kodu Adımlama" olarak adlandırılır. Bir yöntem çağrısının işaretlenmiş kod ise içine F11 tuşuna basarak geçebilirsiniz. Aynı zamanda "üzerinden kod satırının F10 tuşlarına basarak adım". Kesme noktası adımı eylemleri hakkında daha fazla bilgi için, [hata ayıklayıcıyla kod aracılığıyla gezinme](../debugger/navigating-through-code-with-the-debugger.md)makalesini okuyun.

 Kesme noktaları için yaygın kullanımları şunlardır:

1. Bir kilitlenme veya kapanma kaynağını daraltmak için bunları boyunca ve hataya neden olduğunu düşündüğünüz yöntem çağrısının kod etrafında dağılım. Kodunuz içinde adım adım olarak, kaldırmak ve kod geçemediğinde bulana kadar yakın kesme noktaları birlikte sıfırlayın.

2. Yeni kod yapılırsa ve beklendiği gibi davrandığından emin olmak için kodu adımlayın başında bir kesme noktası ayarlayın.

3. Karmaşık bir davranış uygulanırsa, program böldüğünde veri ve değişken değerlerini inceleyebilirsiniz. Bu nedenle algoritmik kodu için kesme noktaları ayarlayın.

4. Bunu C veya C++ koduna kodunu durdurmak için kullanım kesme noktaları yazıyorsanız, bellekle ilgili hataları için hata ayıklama sırasında adres değerlerini (NULL arayın) ve başvuru sayısı inceleyebilirsiniz.

   Kesme noktaları kullanma hakkında daha fazla bilgi için [kesme noktaları kullanarak](../debugger/using-breakpoints.md) okuyun

### <a name="setting-conditional-breakpoints"></a>Koşullu kesme noktaları ayarlama
 Bir döngüde veya özyinelemede içinde bir kesme noktası varsa veya çok sık adım adım kesme noktaları varsa, koşullu kesme noktası yalnızca belirli koşullar karşılandığında kodunuzu askıya alındığından emin olmak için kullanın. Aksi takdirde, F11 awful bir çok tuşuna basarak.

 Koşullu kesme noktası ayarlayın ve bir değişken, belirli bir değere ayarlayın veya belirli bir eşiği geçirir, kodunuzu askıya alma, bir kesme noktası ayarlamak için kenar boşluğunda tıklayın ve ardından görüntülenen vurgulu menüsünden "dişli" seçin için.

 ![Visual Studio 2015 kesme noktası ayarları](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 Şuna benzer bir iletişim kutusu görürsünüz kesmenin belirli koşulları ayarlayabileceğiniz.

 ![Visual Studio 2015 koşullu kesme noktası](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 Koşullu kesme noktalarını değerlendirmek için kullanılan ifadelerin nasıl bildirildiği hakkında daha fazla bilgi için [Visual Studio 2015 ' de Channel9 video kesme noktası yapılandırma deneyimine](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)göz atın.

### <a name="inspecting-your-code-at-run-time"></a>Çalışma zamanında kodunuzu inceleniyor
 Çalışan kodunuz bir kesme noktası ve durur ulaştığında, değişkenlerinizi inceleyin ve neler olduğunu belirlemek için yığınları çağırın. Görmeyi beklediğiniz aralıklara değerler? Aramalar doğru sırada yapılır?

 ![Visual Studio 2015 çalışma&#45;zamanı değeri incelemesi](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")

 Şu anda içerdiği başvuruları ve değerleri görmek için bir değişken üzerinde gezdirin. Beklemediğiniz bir değer görürseniz, önceki veya çağıran kod satırıyla muhtemelen hata vardır. Kesme noktaları Yukarı Taşı veya daha fazla aramanızı daraltmak için mevcut kesme noktaları için koşullar ekleyebilirsiniz.

 Ayrıca, Visual Studio 2015 tanılama araçları penceresi, burada, uygulamanızın CPU ve bellek kullanımı zamanla inceleyebileceğiniz görüntüler. Beklenmeyen yoğun CPU kullanımı veya bellek ayırma için aramak için bunları kullanın. Beklenmedik ağır kullanım veya yayınlanmamış kaynaklara neden olduğunu belirlemek için **izleme** penceresi ve kesme noktaları ile birlikte kullanın.

 ![Visual Studio 2015 Tanılama Araçları penceresi](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>Birim testleri çalıştırma
 Birim testlerini kod yollarında uygulamanızı veya hizmetinizi alıştırma programlardır. Visual Studio 2015 hem yönetilen hem de yerel kod için Microsoft birim testi çerçevelerini yükler. Birim testleri oluşturun, bunları çalıştırmak ve bu testlerin sonuçları rapor için bir birim testi Çerçevesi'ni kullanın. Kodunuzun düzgün çalışıp çalışmadığını test etmek için değişiklik yaptığınız zaman yeniden çalıştır birim testleri. Visual Studio 2015 Enterprise'ı kullandığınızda, her derleme sonrasında testleri otomatik olarak çalıştırabilir.

 Başlamak için, [IntelliTest ile kodunuz için birim testleri oluşturma](../test/generate-unit-tests-for-your-code-with-intellitest.md)makalesini okuyun.

 Visual Studio 2015 ' de birim testleri hakkında daha fazla bilgi edinmek ve bunların daha iyi kalite kodu oluşturmanıza nasıl yardımcı olabileceğini öğrenmek için [birim testi temel bilgilerini](../test/unit-test-basics.md)okuyun.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio](../debugger/debugging-in-visual-studio.md) [hata ayıklayıcı ayarlarında hata ayıklama ve hazırlık](../debugger/debugger-settings-and-preparation.md) [hata ayıklama 64-bit uygulamalar](../debugger/debug-64-bit-applications.md) [hata ayıklayıcı temelleri](../debugger/debugger-basics.md)
