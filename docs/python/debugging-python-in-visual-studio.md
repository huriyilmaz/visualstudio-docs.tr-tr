---
title: Python kodunda hata ayıklama
description: Visual Studio için Python kodu, kesme noktaları ayarlama, Adımlama, değerler geçirerek, özel durumlar arama ve etkileşimli pencerede hata ayıklama da dahil olmak üzere zengin hata ayıklama sağlar.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 4678e3508c16b38fec2a10cdeb79bc499eaf15fd
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409957"
---
# <a name="debug-your-python-code"></a>Python kodunuzun hatalarını ayıklama

Visual Studio, çalışan işlemlere ekleme, **izleme** ve **anında** Windows 'da ifadeleri değerlendirme, yerel değişkenler, kesme noktaları, Step in/out/Over deyimlerini **belirleme, sonraki deyimi ayarlama**ve daha fazlası dahil olmak üzere Python için kapsamlı bir hata ayıklama deneyimi sağlar.

Ayrıca aşağıdaki senaryoya özgü hata ayıklama makalelere bakın:

- [Linux uzaktan hata ayıklama](debugging-python-code-on-remote-linux-machines.md)
- [Karma mod Python/C++ hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Karışık mod hata ayıklaması için semboller](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Visual Studio'da Python, bir proje hata ayıklamayı destekler. Tek başına bir Python dosyası açıkken, düzenleyicide sağ tıklayın, **hata ayıklamaya başla**' yı seçin ve Visual Studio betiği genel varsayılan ortam (bkz. [Python ortamları](managing-python-environments-in-visual-studio.md)) ve bağımsız değişken olmadan başlatır. Ancak daha sonra tam hata ayıklama desteği gerekir.
>
> Ortamı ve bağımsız değişkenleri denetlemek için, kod için bir proje oluşturun, bu, [var olan Python kodu](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) proje şablonuyla kolayca yapılır.

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Temel hata ayıklama

Temel hata ayıklama iş akışından kod içerisinde ilerlemeye değerlerini inceleme ve aşağıdaki bölümlerde açıklandığı gibi özel durumları işleme ayarlarını kesme noktaları içerir.

Hata ayıklama oturumu, hata **ayıklamayı Başlat** komutuyla, araç çubuğundaki **Başlat** düğmesinden veya **F5** tuşuyla **başlar > .** Bu eylemler, projenin etkin ortamı ve tüm komut satırı bağımsız değişkenleri veya **proje özelliklerinde** belirtilen arama yolları (bkz. [proje hata ayıklama seçenekleri](#project-debugging-options)) ile projenizin başlangıç dosyasını ( **Çözüm Gezgini**kalın olarak gösterilir) başlatır. Visual Studio 2017 sürüm 15,6 ve üzeri bir başlangıç dosyası ayarlanmamışsa sizi uyarır; önceki sürümler, Python yorumlayıcı çalıştıran bir çıkış penceresi açabilir veya çıkış penceresi kısa bir süre görünür ve kaybolur. Herhangi bir durumda, uygun dosyaya sağ tıklayın ve **başlangıç dosyası olarak ayarla**' yı seçin.

> [!Note]
> Hata ayıklayıcı her zaman etkin Python ortamı proje için başlar. Ortamı değiştirmek için, [bir proje Için Python ortamı seçme](selecting-a-python-environment-for-a-project.md)konusunda açıklandığı gibi farklı bir tane etkin yapın.

### <a name="breakpoints"></a>Kesme noktaları

Program durumunu inceleyebilirsiniz. Bu nedenle işaretli bir noktada kod yürütme kesme noktaları durdurun. Kod Düzenleyicisi 'nin sol kenar boşluğuna tıklayarak veya bir kod satırına sağ tıklayıp **kesme** noktası Ekle > kesme **noktası**' nı seçerek kesme noktaları ayarlayın. Her satırda bir kesme noktası ile kırmızı bir nokta belirir.

![Visual Studio'da görünen kesme noktaları](media/debugging-breakpoints.png)

Kırmızı noktayı tıklatmak veya kod satırına sağ tıklayıp **kesme** noktası ' nı seçmek > kesme noktasını **Sil** kesme noktasını kaldırır. Kesme noktasını **devre dışı bırak** komutunu > **kesme noktası** kullanarak kaldırmadan de devre dışı bırakabilirsiniz.

> [!Note]
> Bazı kesme noktaları python'da şaşırtıcı diğer programlama dilleriyle hakkında deneyimli olduğunuzu geliştiriciler için olabilir. Herhangi bir üst düzey bir sınıf veya işlev tanımları işlenecek yüklendiğinde Python dosyası çalıştığında, Python tüm yürütülebilir kod dosyasıdır. Bir kesme noktası ayarlarsanız, hata ayıklayıcı kesme bölümü-şekilde bir sınıf bildirimine bulabilirsiniz. Bazen şaşırtıcı olmasına rağmen bu davranışı doğrudur.

Koşullar altında bir kesme noktası, yalnızca bir değişken belirli bir değer veya değer aralığı için ayarlandığında bozucu gibi tetiklenir özelleştirebilirsiniz. Koşulları belirlemek için kesme noktasının kırmızı noktasına sağ tıklayın, **koşul**' ı seçin ve Python kodu kullanarak ifadeler oluşturun. Visual Studio 'da bu özellikle ilgili tüm ayrıntılar için bkz. [kesme noktası koşulları](../debugger/using-breakpoints.md#breakpoint-conditions).

Koşulları ayarlarken, Ayrıca, isteğe bağlı olarak yürütmeye devam etmek için **eylem** ayarlayabilir ve çıkış penceresinde oturum açmak üzere bir ileti oluşturabilirsiniz. İleti günlüğe kaydetme, uygulamanıza doğrudan günlük kodu eklemeden *izleme noktası* olarak adlandırılan öğeleri oluşturur:

![İzleme noktası ile bir kesme noktası oluşturma](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Kodunuz içinde adım adım

Bir kesme noktasında durduruldu sonra kodunuz içinde adım adım veya yeniden kesmeden önce kod bloklarını çalıştırmak için çeşitli yollar vardır. Bu komutlar, en üstteki hata ayıklama araç çubuğu, **hata ayıklama** menüsü, kod düzenleyicisinde sağ tıklama bağlam menüsünde ve klavye kısayolları (tüm komutlar tüm yerlerde olmasa da) dahil olmak üzere birkaç yerde mevcuttur:

| Özellik | Tuş vuruşu | Açıklama |
| --- | --- | --- |
| **Continue** | **F5** | Kod, sonraki kesme noktasına ulaşılıncaya kadar çalışır. |
| **Adımla** | **F11** | Sonraki deyimi çalıştırır ve durdurur. Sonraki ifade bir işlev çağrısı ise, hata ayıklayıcı çağrılan işlevin ilk satırına durdurur. |
| **Adımla** | **F10** | (Çalışan tüm kodun) bir işlev çağrısını yapmadan dahil olmak üzere, sonraki deyimi çalıştırır ve herhangi bir dönüş değeri uygulanıyor. Üzerinden Adımlama kolayca hata ayıklama gerekmez işlevleri atlamanızı sağlar. |
| **Dışarı adımla** | **Shıft**+**F11** | Kod için çağırma deyimine adımları sonra geçerli işlevin sonuna kadar çalışır.  Bu komut, geçerli işlevin geri kalanında hata ayıklamak ihtiyacınız kalmadığında yararlıdır. |
| **Imlece kadar Çalıştır** | **Ctrl**+**F10** | Kod Düzenleyicisi'nde şapka konumuna çalıştırır. Bu komut bir parçası olduğundan, hata ayıklamak için ihtiyacınız olmayan kod üzerinde kolayca atlamanızı sağlar. |
| **Sonraki Deyimi Belirle** | **Ctrl**+**SHIFT**+**F10** | Giriş işareti konumuna kod noktası çalıştırma geçerli değiştirir. Bu komut, gibi bildiğiniz kodu bozuk veya istenmeyen bir yan etkisi üretir, çalıştırılan kodun bir parçasını atlamak sağlar. |
| **Sonraki Ifadeyi göster** | **Alt**+**num** **&#42;**| Sonraki deyimi çalıştırmak için döndürür. Bu komut, kodunuzda arıyorsunuz geçici bir çözüm ve hata ayıklayıcı durduğu hatırlamıyorum yararlıdır. |

### <a name="inspect-and-modify-values"></a>Denetleme ve değerleri değiştirme

Hata ayıklayıcıda durdurulduklarında inceleyin ve değişkenlerin değerlerini değiştirin. Ayrıca, tek tek değişkenleri ve özel ifadeleri izlemek için **Gözcü** penceresini de kullanabilirsiniz. (Bkz. Genel Ayrıntılar için [değişkenleri İnceleme](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows) .)

**DataTips**kullanarak bir değeri görüntülemek için, fareyi düzenleyicideki herhangi bir değişkenin üzerine getirin. Değeri değiştirmek için tıklayabilirsiniz:

![Visual Studio hata ayıklayıcıda gösteren DataTips](media/debugging-quick-tips.png)

**Oto** penceresi (**hata ayıklama** > **Windows** > **oto**), geçerli ifadeye yakın olan değişkenleri ve ifadeleri içerir. Değer sütununa çift tıklayabilir veya seçin ve **F2** tuşuna basarak değeri düzenleyin:

![Visual Studio hata ayıklayıcısı otomatik değişkenler penceresi](media/debugging-autos-window.png)

**Yereller** penceresi (**hata ayıklama** > **Windows** > **Yereller**) geçerli kapsamda olan tüm değişkenleri görüntüler, bu da yeniden düzenlenebilir:

![Visual Studio hata ayıklayıcısını Yereller penceresinde](media/debugging-locals-window.png)

**Oto ve yerelleri** kullanma hakkında dahafazla bilgi için bkz. [oto ve Yereller pencerelerinde değişkenleri İnceleme](../debugger/autos-and-locals-windows.md).

**Gözcü** pencereleri (**hata ayıklama** > **windows** > **Watch** > **izleme 1-4**), rastgele Python ifadeleri girmenize ve sonuçları görüntülemenize olanak sağlar. İfadeler her adım için değerlendirilerek:

![Visual Studio hata ayıklayıcı penceresinde izleyin](media/debugging-watch-window.png)

**İzleme**kullanımı hakkında daha fazla bilgi için bkz. [Izleme ve hızlı gözcü pencerelerini kullanarak değişkenlerde izleme ayarlama](../debugger/watch-and-quickwatch-windows.md).

Bir dize değeri incelenirken (`str`, `unicode`, `bytes`ve `bytearray` bu amaçla dizeler kabul edildiğinde), değerin sağ tarafında bir büyüteç simgesi görüntülenir. Simgeye tıklayarak uzun dizeler için yararlı olan tırnak işareti olmayan bir dize değeri sarmalama ve kaydırmayı, açılan iletişim kutusunda görüntüler. Ayrıca, açılan ok simgesini seçerek, düz metin seçmenizi sağlar HTML, XML ve JSON görselleştirmeler:

![Visual Studio hata ayıklayıcısı görselleştiriciler dize](media/debugging-string-visualizers.png)

HTML, XML ve JSON görselleştirmeler ayrı açılır pencereleri söz dizimi vurgulama ve ağaç görünümleri ile görünür.

### <a name="exceptions"></a>Özel Durumlar

Hata ayıklama sırasında programınızdaki bir hata meydana gelir, ancak bunun için bir özel durum işleyicisi yok, hata ayıklayıcı özel durum noktasında keser:

![Visual Studio hata ayıklayıcı özel durum açılan menüsü](media/debugging-exception-popup.png)

Bu noktada çağrı yığını da dahil olmak üzere program durumunu inceleyebilirsiniz. Ancak, kodunuz içinde adım adım denerseniz, özel durum ya da işlenir veya programınızın çıkar kadar oluşturulan devam eder.

**Hata ayıklama** > **Windows** > **özel durum ayarları** menü komutu, **Python özel durumlarını**genişletebileceğiniz bir pencere getirir:

![Visual Studio hata ayıklayıcısını özel durumlar penceresi](media/debugging-exception-settings.png)

Her bir özel durum için onay kutusu *, hata ayıklayıcının ne zaman harekete* geçirilip bölünemediğini denetler. Daha sık için belirli bir özel durumun kesmek istediğinizde bu kutuyu işaretleyin.

Kaynak kodunda özel durum işleyicisi bulunamadığında varsayılan olarak, çoğu özel durumların bölün. Bu davranışı değiştirmek için herhangi bir özel duruma sağ tıklayın ve **Kullanıcı kodunda Işlenmediğinde devam et** seçeneğini değiştirin. Daha az sıklıkta için bir özel durum kesmek istediğinizde bu kutusunun işaretini kaldırın.

Bu listede görünmeyen bir özel durumu yapılandırmak için **Ekle** düğmesine tıklayarak ekleyin. Özel durumun tam adı eşleşmelidir.

## <a name="project-debugging-options"></a>Proje hata ayıklama seçenekleri

Varsayılan olarak, hata ayıklayıcı, programınızın standart Python başlatıcısı, hiçbir komut satırı bağımsız değişkenleri ve başka hiçbir özel yollar veya koşullar ile başlatır. Başlangıç seçenekleri, projenin **Çözüm Gezgini**, **Özellikler**' i seçip ve **Hata Ayıkla** sekmesi seçilerek erişilen proje hata ayıklama özellikleri aracılığıyla değiştirilir.

![Visual Studio hata ayıklayıcısı proje hata ayıklama özellikleri](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Modu seçeneklerini başlatma

| Seçenek | Açıklama |
| --- | --- |
| **Standart Python başlatıcısı** | CPython, IronPython ve Stackless Python gibi çeşitler uyumludur taşınabilir python'da yazılan kod hata ayıklamayı kullanır. Bu, saf Python kodunda hata ayıklama için en iyi deneyimi sağlar. Çalışan bir *Python. exe* işlemine iliştirmeye çalıştığınızda, bu başlatıcı kullanılır. Bu başlatıcı Ayrıca, Cpkullanım için [karışık modda hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) sağlar ve C/C++ Code ve Python kodu arasında sorunsuz bir şekilde ilerlemenize olanak tanır. |
| **Web başlatıcısı** | Varsayılan tarayıcınız başlatma sırasında başlatılır ve şablonları hata ayıklamasını etkinleştirir. Daha fazla bilgi için [Web şablonu hata ayıklama](python-web-application-project-templates.md#debugging) bölümüne bakın. |
| **Docgo Web başlatıcısı** | Aynı Web Başlatıcısı'nı ve yalnızca geriye dönük uyumluluk gösterilir. |
| **IronPython (.NET) başlatıcısı** | .NET hata ayıklayıcı, IronPython yalnızca hangi çalışır kullanır ancak C# ve VB'nin dahil olmak üzere herhangi bir .NET dil projesine arasında atlamak için izin verir IronPython barındıran çalışan bir .NET işleme eklerseniz bu Başlatıcısı kullanılır. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Çalıştırma Seçenekleri (arama yolları, başlangıç bağımsız değişkenleri ve ortam değişkenlerini)

| Seçenek | Açıklama |
| --- | --- |
| **Arama yolları** | Bu değerler, projenin **Çözüm Gezgini** **arama yolları** düğümünde gösterilenlerin eşleşmesinden eşleşir. Bu değeri burada değiştirebilirsiniz, ancak klasörlere gözatmanıza ve yolları göreli biçime otomatik olarak dönüştürmenize olanak tanıyan **Çözüm Gezgini** kullanımı daha kolaydır. |
| **Betik bağımsız değişkenleri** | Bu bağımsız değişkenler komut dosyanızın filename sonra görünen betiğinizi başlatmak için kullanılan komut eklenir. Buradaki ilk öğe, betiğinizin `sys.argv[1]`, ikincisi `sys.argv[2]`ve benzeri olarak kullanılabilir. |
| **Yorumlayıcı bağımsız değişkenleri** | Bu bağımsız komut dosyanız adının önünde Başlatıcısı komut satırına eklenir. Burada yaygın bağımsız değişkenler, uyarıları denetlemek, programınızı biraz iyileştirmek için `-O` ve arabelleğe alınmamış GÇ kullanmak `-u` `-W ...`. IronPython kullanıcıları, `-X:Frames` veya `-X:MTA`gibi `-X` seçeneklerini geçirmek için bu alanı kullanabilir. |
| **Yorumlayıcı yolu** | Geçerli ortam ile ilişkili yolu geçersiz kılar. Değer bir standart yorumlayıcı komut dosyanızı başlatmak için yararlı olabilir. |
| **Ortam Değişkenleri** | Bu çok satırlı metin kutusunda form \<adı > =\<değer > girdilerini ekleyin. Bu ayar en son, var olan genel ortam değişkenlerinin en üstünde ve `PYTHONPATH` **arama yolları** ayarına göre ayarlandıktan sonra, bu diğer değişkenlerden herhangi birini el ile geçersiz kılmak için kullanılabilir. |

## <a name="immediate-and-interactive-windows"></a>Hemen ve etkileşimli windows

Hata ayıklama oturumu sırasında kullanabileceğiniz iki etkileşimli Windows vardır: standart Visual Studio **komut** penceresi ve **Python hata ayıklama etkileşimli** penceresi.

**Komut** penceresi (**hata ayıklama** > **Windows** > **Hemen**), Python ifadelerinin ve denetleme veya çalışan programdaki değişkenlerin atanması için hızlı değerlendirme için kullanılır. Ayrıntılar için genel [pencere](../ide/reference/immediate-window.md) makalesine bakın.

**Python hata ayıklama etkileşimli** penceresi (**hata** ayıklama ** > Windows** > **Python hata ayıklama etkileşimli**), hata ayıklama sırasında kod yazma ve çalıştırma dahil olmak üzere tam [etkileşimli REPL](python-interactive-repl-in-visual-studio.md) deneyimini kullanılabilir hale getiren daha zengin bir deneyimdir. Standart Python başlatıcısı kullanılarak hata ayıklayıcıda başlatılan herhangi bir işleme otomatik olarak bağlanır ( **hata ayıklama** > **işleme**yoluyla eklenen işlemler dahil). Ancak, C/C++ karışık mod hata ayıklaması kullanırken kullanılabilir değilse.

![Python hata ayıklama etkileşimli penceresi](media/debugging-interactive.png)

**Hata ayıklama etkileşimli** penceresi, [Standart REPL komutlarına](python-interactive-repl-in-visual-studio.md#meta-commands)ek olarak özel meta komutları destekler:

| Komut | Arguments | Açıklama |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Geçerli deyimden programı çalıştırmaya başlar. |
| `$down`, `$d` | Geçerli çerçeve bir düzey aşağıya yığın izlemesi taşıyın. |
| `$frame` | | Geçerli çerçeve KIMLIĞINI görüntüler.
| `$frame` | çerçeve KIMLIĞI | Geçerli çerçeveyi belirtilen çerçeve KIMLIĞINE geçirir.
| `$load` | Komut dosyasını yükler ve tamamlanana kadar yürütür |
| `$proc` |  | Geçerli işlem KIMLIĞINI görüntüler. |
| `$proc` | işlem KIMLIĞI | Geçerli işlemi belirtilen işlem KIMLIĞINE geçirir. |
| `$procs` | | Şu anda hataları ayıklanan işlemlerin listeler. |
| `$stepin`, `$step`, `$s` | Sonraki işlev çağrısı, eğer mümkünse adımlamayla girin. |
| `$stepout`, `$return`, `$r` | Geçerli işlev dışında adımları. |
| `$stepover`, `$until`, `$unt` | Sonraki işlev deyime çağırın. |
| `$thread` | | Geçerli iş parçacığı KIMLIĞINI görüntüler. |
| `$thread` | iş parçacığı KIMLIĞI | Geçerli iş parçacığını belirtilen iş parçacığı KIMLIĞINE geçirir. |
| `$threads` | | Şu anda hataları ayıklanmakta olan iş parçacıkları listeler. |
| `$up`, `$u` | | Yığın izlemeyle uygulamanızda geçerli çerçeve bir düzey yukarı. |
| `$where`, `$w`, `$bt` | Geçerli iş parçacığı çerçevelerini listeler. |

**Süreçler**, **Iş parçacıkları**ve **çağrı yığını** gibi standart hata ayıklayıcı pencerelerinin **hata ayıklama etkileşimli** penceresiyle eşitlenmediğini unutmayın. **Hata ayıklama etkileşimli** penceresindeki etkin işlem, iş parçacığı veya çerçeveyi değiştirmek, diğer hata ayıklayıcı pencerelerini etkilemez. Benzer şekilde, diğer hata ayıklayıcı pencerelerinin etkin işlem, iş parçacığı veya çerçeveyi değiştirmek, **hata ayıklama etkileşimli** penceresini etkilemez.

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Eski hata ayıklayıcıyı kullanın

Visual Studio 2017 sürüm 15,8 ve daha sonra bir hata ayıklayıcısı ptvsd sürümüne 4.1 + dayanan kullanın. Ptvsd bu sürümü, Python 2.7 ve Python 3.5 + ile uyumludur. Python 2,6, 3,1, 3,4 veya IronPython kullanıyorsanız, Visual Studio hatayı gösterir, hata **ayıklayıcı bu Python ortamını desteklemez**:

![Hata ayıklayıcı hata ayıklayıcı kullanırken bu Python ortamı hatası desteklemiyor](media/debugging-experimental-incompatible-error.png)

Bu gibi durumlarda, daha eski hata ayıklayıcı (Visual Studio 2017 sürüm 15.7 ve önceki varsayılan olan) kullanmanız gerekir. **Araçlar** > **Seçenekler** menü komutunu seçin, **Python** > **hata ayıklama**bölümüne gidin ve **eski hata ayıklayıcı kullan** seçeneğini belirleyin.

Geçerli ortama (örneğin, önceki 4.0.x sürümü veya uzaktan hata ayıklama için gereken bir 3.x sürümü) ptvsd daha eski bir sürümünü yüklediyseniz Visual Studio bir hata veya uyarı gösterebilir.

Hata, hata **ayıklayıcı paketi yüklenemedi**, ptvsd 3. x 'i yüklediğinizde görünür:

![Hata ayıklayıcısı paket hata ayıklayıcı kullanırken yüklenen hata bulunamadı](media/debugging-experimental-version-error.png)

Bu durumda, eski hata ayıklayıcıyı **kullan** seçeneğini ayarlamak için **eski hata ayıklayıcıyı kullan** ' ı seçin ve hata ayıklayıcıyı yeniden başlatın.

Uyarı, **hata ayıklayıcı paketi güncel değil**, ptvsd 'in önceki 4. x sürümünü yüklediğinizde görüntülenir:

![Hata ayıklayıcısı paket hata ayıklayıcı kullanırken uyarı güncel değil](media/debugging-experimental-version-warning.png)

> [!Important]
> Ptvsd'ün bazı sürümleri için bir uyarıyı yoksaymak seçebilirsiniz ancak Visual Studio doğru şekilde çalışmayabilir.

Ptvsd yüklemenizi yönetmek için:

1. **Python ortamları** penceresinde **paketler** sekmesine gidin.

1. Arama kutusuna "ptvsd" ve ptvsd'ın yüklü sürümü inceleyin:

    ![Python ortamları penceresinde ptvsd sürüm denetimi](media/debugging-experimental-check-ptvsd.png)

1. Sürüm 4.1.1 A9 'den düşükse (Visual Studio ile paketlenmiş sürüm), eski sürümü kaldırmak için paketin sağ tarafındaki **X** ' i seçin. Visual Studio, ardından ile birlikte gelen sürümünü kullanır. (`pip uninstall ptvsd`kullanarak PowerShell 'den da kaldırabilirsiniz.)

1. Alternatif olarak, [sorun giderme](#troubleshooting) bölümündeki yönergeleri izleyerek ptvsd paketini en yeni sürümüne güncelleştirebilirsiniz.

## <a name="troubleshooting"></a>Sorun giderme

Hata ayıklayıcısı ile sorun yaşarsanız, ilk gibi ptvsd sürümünüzü yükseltin:

1. **Python ortamları** penceresinde **paketler** sekmesine gidin.

1. Arama kutusuna `ptvsd --upgrade` girin, sonra **komutu Çalıştır: pttrvsd--Upgrade**' i seçin. (Ayrıca aynı PowerShell komutu kullanabilirsiniz.)

    ![Python ortamları penceresinde ptvsd yükseltme komut vererek](media/debugging-experimental-upgrade-ptvsd.png)

Sorun devam ederse lütfen [PTV GitHub deposunda](https://github.com/Microsoft/ptvs/issues)bir sorun bildirin.

### <a name="enable-debugger-logging"></a>Hata ayıklayıcı günlüğü etkinleştir

Bir hata ayıklayıcı sorunu araştırmaya sırasında Microsoft, etkinleştirmek ve tanılama aşamasında yardımcı hata ayıklayıcı günlükleri toplamak için isteyebilir.

Aşağıdaki adımlar, geçerli Visual Studio oturumunda hata ayıklamayı etkinleştir:

1. Visual Studio **'da > ** **diğer Windows** > **komut penceresi** menü komutunu kullanarak bir komut penceresi açın.

1. Aşağıdaki komutu girin:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Hata ayıklamayı başlatmak ve tüm adımları sorununuzu yeniden oluşturmak için gerekli olan aracılığıyla gidin. Bu süre boyunca hata ayıklama günlüğü, **hata ayıklama bağdaştırıcısı ana bilgisayar günlüğü**altındaki **Çıkış** penceresinde görüntülenir. Ardından, günlükleri pencereden kopyalayın ve bir GitHub sorunu, e-posta, vb. yapıştırın.

    ![Hata ayıklayıcı çıkış penceresinde günlük çıktısı](media/debugger-logging-output.png)

1. Visual Studio askıda kalırsa veya **Çıkış** penceresine erişemeyebilirsiniz, Visual Studio 'yu yeniden başlatın, bir komut penceresi açın ve aşağıdaki komutu girin:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Hata ayıklamayı başlatmak ve sorunu yeniden oluşturun. Hata ayıklayıcı günlükleri daha sonra `%temp%\DebugAdapterHostLog.txt`bulunabilir.

## <a name="see-also"></a>Ayrıca bkz.

Visual Studio hata ayıklayıcısı hakkında tüm ayrıntılar için bkz. [Visual Studio 'Da hata ayıklama](../debugger/debugger-feature-tour.md).
