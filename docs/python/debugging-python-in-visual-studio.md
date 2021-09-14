---
title: Python kodunda hata ayıklama
description: Visual Studio, kesme noktaları ayarlama, adımlama, değerleri inceleme, özel durumlara bakma ve etkileşimli pencerede hata ayıklama da dahil olmak üzere Python kodu için zengin hata ayıklama sağlar.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3ef8fc7ef3de032d4c4fba25e0e3b64a47b76ac1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636982"
---
# <a name="debug-your-python-code"></a>Python kodunuzda hata ayıklama

Visual Studio, çalışan işlemlere ekleme, **izleme** ve **anında** windows 'da ifadeleri değerlendirme, yerel değişkenleri belirleme, kesme noktaları, step ın/out/over deyimleri, **sonraki deyimi** ve daha fazlasını belirleme dahil olmak üzere Python için kapsamlı bir hata ayıklama deneyimi sağlar.

Ayrıca, senaryoya özgü aşağıdaki hata ayıklama makalelerine bakın:

- [Linux uzaktan hata ayıklama](debugging-python-code-on-remote-linux-machines.md)
- [Karma mod Python/C++ hata ayıklaması](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Karışık mod hata ayıklaması için semboller](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Visual Studio Python, proje olmadan hata ayıklamayı destekler. tek başına bir Python dosyası açıkken, düzenleyicide sağ tıklayın, **hata ayıklamaya başla**' yı seçin ve betiği genel varsayılan ortamla (bkz. [Python ortamları](managing-python-environments-in-visual-studio.md)) ve bağımsız değişken olmadan başlatır Visual Studio. Ancak bundan sonra tam hata ayıklama desteğiniz vardır.
>
> Ortamı ve bağımsız değişkenleri denetlemek için, kod için bir proje oluşturun, bu, [var olan Python kodu](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) proje şablonuyla kolayca yapılır.

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Temel hata ayıklama

Temel hata ayıklama iş akışı, ayarlar kesme noktaları, kod üzerinden atlama, değerleri İnceleme ve aşağıdaki bölümlerde açıklandığı gibi özel durumları işleme içerir.

Hata ayıklama **Oturumu hata ayıklama**  >  **başlatma hata ayıklama** komutu, araç çubuğundaki **Başlat** düğmesi veya **F5** tuşu ile başlar. bu eylemler, projenin etkin ortamı ve **Project özelliklerinde** belirtilmiş olan tüm komut satırı bağımsız değişkenleri veya arama yolları (bkz. [Project hata ayıklama seçenekleri](#project-debugging-options)) ile projenizin başlangıç dosyasını ( **Çözüm Gezgini** kalın olarak gösterilir) başlatır. Visual Studio 2017 sürüm 15,6 ve üzeri bir başlangıç dosyası ayarlanmamışsa sizi uyarır; önceki sürümler, Python yorumlayıcı çalıştıran bir çıkış penceresi açabilir veya çıkış penceresi kısa bir süre görünür ve kaybolur. Herhangi bir durumda, uygun dosyaya sağ tıklayın ve **başlangıç dosyası olarak ayarla**' yı seçin.

> [!Note]
> Hata ayıklayıcı her zaman proje için etkin Python ortamıyla başlar. Ortamı değiştirmek için, [bir proje Için Python ortamı seçme](selecting-a-python-environment-for-a-project.md)konusunda açıklandığı gibi farklı bir tane etkin yapın.

### <a name="breakpoints"></a>Kesme noktaları

Kesme noktaları, program durumunu incelemenize olanak sağlamak için işaretli bir noktada kodun yürütülmesini durdurur. Kod Düzenleyicisi 'nin sol kenar boşluğuna tıklayarak veya bir kod satırına sağ **tıklayıp kesme**  >  **noktası Ekle kesme noktası**' nı seçerek kesme noktaları ayarlayın. Her satırda bir kesme noktasıyla kırmızı bir nokta görünür.

![Visual Studio görünen kesme noktaları](media/debugging-breakpoints.png)

Kırmızı noktayı tıklatmak veya kod satırına sağ tıklayıp **kesme** noktası silme kesme noktası ' nı seçmek  >   , kesme noktasını kaldırır. **Kesme**  >  **noktasını devre dışı bırak** komutunu kullanarak kaldırmadan de devre dışı bırakabilirsiniz.

> [!Note]
> Python 'daki bazı kesme noktaları, diğer programlama dilleri ile çalışan geliştiriciler için de şaşırtıcı olabilir. Python 'da tüm dosya yürütülebilir koddur, bu nedenle Python, herhangi bir üst düzey sınıfı veya işlev tanımını işlemek üzere yüklendiğinde dosyayı çalıştırır. Bir kesme noktası ayarlandıysa, bir sınıf bildirimi aracılığıyla hata ayıklayıcıyı parçalı bir şekilde bulabilirsiniz. Bu davranış, bazen ortaya çıkmış olsa da doğrudur.

Yalnızca bir değişken belirli bir değere veya değer aralığına ayarlandığında bölme gibi, bir kesme noktasının tetiklendiği koşulları özelleştirebilirsiniz. Koşulları belirlemek için kesme noktasının kırmızı noktasına sağ tıklayın, **koşul**' ı seçin ve Python kodu kullanarak ifadeler oluşturun. Visual Studio bu özellik hakkında tam ayrıntılar için bkz. [kesme noktası koşulları](../debugger/using-breakpoints.md#breakpoint-conditions).

Koşulları ayarlarken, Ayrıca, isteğe bağlı olarak yürütmeye devam etmek için **eylem** ayarlayabilir ve çıkış penceresinde oturum açmak üzere bir ileti oluşturabilirsiniz. İleti günlüğe kaydetme, uygulamanıza doğrudan günlük kodu eklemeden *izleme noktası* olarak adlandırılan öğeleri oluşturur:

![Kesme noktasıyla izleme noktası oluşturma](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Kod üzerinden adımla

Bir kesme noktasında durdurulduktan sonra, yeniden kesmeden önce kod veya kod blokları çalıştırmak için çeşitli yöntemlere sahip olursunuz. Bu komutlar, en üstteki hata ayıklama araç çubuğu, **hata ayıklama** menüsü, kod düzenleyicisinde sağ tıklama bağlam menüsünde ve klavye kısayolları (tüm komutlar tüm yerlerde olmasa da) dahil olmak üzere birkaç yerde mevcuttur:

| Özellik | U | Description |
| --- | --- | --- |
| **Devam et** | **F5** | Sonraki kesme noktasına ulaşılana kadar kodu çalıştırır. |
| **Adımla** | **F11** | Sonraki ifadeyi çalıştırır ve duraklar. Next ifadesinde bir işlev çağrısı varsa, hata ayıklayıcı çağrılan işlevin ilk satırında duraklar. |
| **Adımla** | **F10** | Bir işleve çağrı yapma (tüm kodunu çalıştırma) ve herhangi bir dönüş değeri uygulama dahil olmak üzere sonraki ifadeyi çalıştırır. Adımlama, hata ayıklamanıza gerek olmayan işlevleri kolayca atlamanızı sağlar. |
| **Dışarı adımla** | **SHIFT** + **F11** | Geçerli işlevin sonuna kadar kodu çalıştırır ve ardından çağıran ifadeye adımları uygulayın.  Bu komut, geçerli işlevin geri kalanında hata ayıklamanıza gerek olmadığında yararlıdır. |
| **Imlece kadar Çalıştır** | **CTRL** + **F10** | Düzenleyicideki giriş işaretinin konumuna kadar kodu çalıştırır. Bu komut, hata ayıklamanıza gerek olmayan bir kod segmentinin üzerinde kolayca atlama yapmanıza olanak sağlar. |
| **Sonraki Deyimi Belirle** | **CTRL** + **SHIFT** + **F10** | Koddaki geçerli çalışma noktasını, giriş işaretinin konumuyla değiştirir. Bu komut, kodun hatalı olduğunu bildiğiniz veya istenmeyen yan etkisi üreten bir kod segmentini atlamanızı sağlar. |
| **Sonraki Ifadeyi göster** | **Alt** +  **&#42;** NUM| Çalıştırmak için sizi bir sonraki ifadeye döndürür. Bu komut, kodunuzda arama yaptıysanız ve hata ayıklayıcının durdurulduğu yeri anımsamıyorsanız yararlı olur. |

### <a name="inspect-and-modify-values"></a>Değerleri İnceleme ve değiştirme

Hata ayıklayıcıda durdurulduğunda, değişkenlerin değerlerini inceleyebilir ve değiştirebilirsiniz. Ayrıca, tek tek değişkenleri ve özel ifadeleri izlemek için **Gözcü** penceresini de kullanabilirsiniz. (Bkz. Genel Ayrıntılar için [değişkenleri İnceleme](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows) .)

**DataTips** kullanarak bir değeri görüntülemek için, fareyi düzenleyicideki herhangi bir değişkenin üzerine getirin. Değiştirmek için değere tıklayabilirsiniz:

![Visual Studio hata ayıklayıcısında gösterilen datatips](media/debugging-quick-tips.png)

**oto** penceresi (**hata ayıklama**  >  **Windows**  >  **oto**), geçerli ifadeye yakın olan değişkenleri ve ifadeleri içerir. Değer sütununa çift tıklayabilir veya seçin ve **F2** tuşuna basarak değeri düzenleyin:

![Visual Studio hata ayıklayıcısındaki oto penceresi](media/debugging-autos-window.png)

**yereller** penceresi (**hata ayıklama**  >  **Windows**  >  **yereller**) geçerli kapsamda olan tüm değişkenleri görüntüler, bu da yeniden düzenlenebilir:

![Visual Studio hata ayıklayıcısında yereller penceresi](media/debugging-locals-window.png)

**Oto ve yerelleri** kullanma hakkında daha fazla bilgi için bkz. [oto ve Yereller pencerelerinde değişkenleri İnceleme](../debugger/autos-and-locals-windows.md).

**gözcü** pencereleri (**hata ayıklama**  >  **Windows**  >  **izleme**  >  **izleme 1-4**), rastgele Python ifadeleri girmenize ve sonuçları görüntülemenize izin verir. İfadeler her adım için yeniden değerlendirilerek:

![Visual Studio hata ayıklayıcıda izleme penceresi](media/debugging-watch-window.png)

**İzleme** kullanımı hakkında daha fazla bilgi için bkz. [Izleme ve hızlı gözcü pencerelerini kullanarak değişkenlerde izleme ayarlama](../debugger/watch-and-quickwatch-windows.md).

Bir dize değeri incelenirken (, `str` , `unicode` `bytes` ve `bytearray` tüm dizeler bu amaçla kabul edildiğinde), değerin sağ tarafında bir büyüteç simgesi görüntülenir. Simgeye tıkladığınızda, bir açılan iletişim kutusunda tırnak işareti olmayan dize değeri görünür ve bu, uzun dizeler için yararlı olan sarmalama ve kaydırma sağlar. Ayrıca, simgenin üzerindeki açılan oku seçmek düz metin, HTML, XML ve JSON görselleştirmelerini seçmenizi sağlar:

![Visual Studio hata ayıklayıcısında dize görselleştiriciler](media/debugging-string-visualizers.png)

HTML, XML ve JSON görselleştirmeleri, sözdizimi vurgulaması ve ağaç görünümleri olan ayrı açılan pencereler halinde görünür.

### <a name="exceptions"></a>Özel durumlar

Programınızda hata ayıklama sırasında bir hata oluşursa, ancak bunun için bir özel durum işleyiciniz yoksa, hata ayıklayıcı özel durum noktasında kesilir:

![Visual Studio hata ayıklayıcısında özel durum açılan penceresi](media/debugging-exception-popup.png)

Bu noktada, çağrı yığını da dahil olmak üzere program durumunu inceleyebilirsiniz. Ancak, kodda adım adım ilerlemeye çalışırsanız, özel durum işlenene veya programınız çıkıncaya kadar bu durum oluşturulur.

**hata ayıklama**  >  **Windows**  >  **özel durum Ayarlar** menü komutu, **Python özel durumlarını** genişletebileceğiniz bir pencere getirir:

![Visual Studio hata ayıklayıcısındaki özel durumlar penceresi](media/debugging-exception-settings.png)

Her bir özel durum için onay kutusu *, hata ayıklayıcının ne zaman harekete* geçirilip bölünemediğini denetler. Belirli bir özel durum için daha sık daha fazla bölmek istiyorsanız bu kutuyu işaretleyin.

Varsayılan olarak, bir özel durum işleyicisi kaynak kodunda bulunamadığında, en çok özel durumlar kesilir. Bu davranışı değiştirmek için herhangi bir özel duruma sağ tıklayın ve **Kullanıcı kodunda Işlenmediğinde devam et** seçeneğini değiştirin. Bir özel durum için daha az sıklıkta bölmek istediğinizde bu kutuyu temizleyin.

Bu listede görünmeyen bir özel durumu yapılandırmak için **Ekle** düğmesine tıklayarak ekleyin. Ad, özel durumun tam adıyla eşleşmelidir.

## <a name="project-debugging-options"></a>Project hata ayıklama seçenekleri

Varsayılan olarak, hata ayıklayıcı programınızı standart Python başlatıcısı, komut satırı bağımsız değişkeni olmadan ve başka özel yollar veya koşullar olmadan başlatır. Başlangıç seçenekleri, projenin **Çözüm Gezgini**, **Özellikler**' i seçip ve **Hata Ayıkla** sekmesi seçilerek erişilen proje hata ayıklama özellikleri aracılığıyla değiştirilir.

![Visual Studio hata ayıklayıcıda hata ayıklama özellikleri Project](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Başlatma modu seçenekleri

| Seçenek | Açıklama |
| --- | --- |
| **Standart Python başlatıcısı** | , Cponthon, IronPython ve stackless Python gibi varyantlar ile uyumlu olan taşınabilir Python 'da yazılmış hata ayıklama kodunu kullanır. Saf Python kodunda hata ayıklamak için en iyi deneyimi sağlar. Çalışan bir *python.exe* işlemine iliştirmeye çalıştığınızda, bu başlatıcı kullanılır. Bu başlatıcı Ayrıca, Cpkullanım için [karışık modda hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) sağlar ve C/C++ kodu ile Python kodu arasında sorunsuz bir şekilde ilerlemenize olanak tanır. |
| **Web başlatıcısı** | Varsayılan tarayıcınızı başlatma sırasında başlatır ve şablonların hata ayıklamasını sağlar. Daha fazla bilgi için [Web şablonu hata ayıklama](python-web-application-project-templates.md#debugging) bölümüne bakın. |
| **Docgo Web başlatıcısı** | Web başlatıcısı ile özdeş ve yalnızca geriye dönük uyumluluk için gösteriliyor. |
| **IronPython (.NET) başlatıcısı** | Yalnızca IronPython ile birlikte çalışarak, ancak C# ve VB dahil .NET dil projeleri arasında adımlama sağlayan .NET hata ayıklayıcısını kullanır. Bu başlatıcı, IronPython 'u barındıran çalışan bir .NET işlemini iliştirmek için kullanılır. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Çalıştırma seçenekleri (arama yolları, başlangıç bağımsız değişkenleri ve ortam değişkenleri)

| Seçenek | Açıklama |
| --- | --- |
| **Arama yolları** | Bu değerler, projenin **Çözüm Gezgini** **arama yolları** düğümünde gösterilenlerin eşleşmesinden eşleşir. Bu değeri burada değiştirebilirsiniz, ancak klasörlere gözatmanıza ve yolları göreli biçime otomatik olarak dönüştürmenize olanak tanıyan **Çözüm Gezgini** kullanımı daha kolaydır. |
| **Betik bağımsız değişkenleri** | Bu bağımsız değişkenler, komut dosyanızı başlatmak için kullanılan komuta, betiğinizin dosya adından sonra görünen komuta eklenir. Buradaki ilk öğe, `sys.argv[1]` `sys.argv[2]` betiğinizin, ikincisi, vb. için kullanılabilir. |
| **Yorumlayıcı bağımsız değişkenleri** | Bu bağımsız değişkenler, betiğinizin adından önce Başlatıcı komut satırına eklenir. Burada ortak bağımsız değişkenler, `-W ...` uyarıları denetlemek, `-O` programınızı biraz iyileştirmek ve `-u` arabelleğe alınmamış GÇ kullanmak için kullanılır. IronPython kullanıcılarının, veya gibi seçenekleri geçirmek için bu alanı kullanması olasıdır `-X` `-X:Frames` `-X:MTA` . |
| **Yorumlayıcı yolu** | Geçerli ortamla ilişkili yolu geçersiz kılar. Bu değer, komut dosyanızı standart olmayan bir yorumlayıcıya başlatmak için yararlı olabilir. |
| **Ortam değişkenleri** | Bu çok satırlı metin kutusunda, form girdilerini ekleyin \<NAME> = \<VALUE> . Bu ayar son olarak, var olan genel ortam değişkenlerinin en üstünde ve sonra `PYTHONPATH` **arama yolları** ayarına göre ayarlandıktan sonra, bu diğer değişkenlerden herhangi birini el ile geçersiz kılmak için kullanılabilir. |

## <a name="immediate-and-interactive-windows"></a>Anında ve etkileşimli Windows

hata ayıklama oturumu sırasında kullanabileceğiniz iki etkileşimli windows vardır: standart Visual Studio **hemen** penceresi ve **Python hata ayıklama etkileşimli** penceresi.

**hemen** pencere (**hata ayıklama**  >  **Windows**  >  **anında**), Python ifadelerinin ve denetleme veya çalışan programdaki değişkenlerin atanması için hızlı değerlendirme için kullanılır. Ayrıntılar için genel [pencere](../ide/reference/immediate-window.md) makalesine bakın.

**python hata ayıklama etkileşimli** penceresi (**hata** ayıklama  >  **Windows**  >  **python hata ayıklama etkileşimli**), hata ayıklama sırasında kod yazma ve çalıştırma dahil olmak üzere tam [etkileşimli REPL](python-interactive-repl-in-visual-studio.md) deneyimini kullanılabilir hale getiren daha zengin bir deneyimdir. Standart Python başlatıcısı kullanılarak hata ayıklayıcıda başlatılan herhangi bir işleme otomatik olarak bağlanır ( **hata ayıklama** ekleme yoluyla eklenen işlemler dahil  >  ). Ancak, karma mod C/C++ hata ayıklama kullanılırken kullanılabilir değildir.

![Python hata ayıklama etkileşimli penceresi](media/debugging-interactive.png)

**Hata ayıklama etkileşimli** penceresi, [Standart REPL komutlarına](python-interactive-repl-in-visual-studio.md#meta-commands)ek olarak özel meta komutları destekler:

| Komut | Bağımsız değişkenler | Description |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Geçerli deyimden programı çalıştırmaya başlar. |
| `$down`, `$d` | Geçerli çerçeveyi yığın izlemesinde bir düzey aşağı taşıyın. |
| `$frame` | | Geçerli çerçeve KIMLIĞINI görüntüler.
| `$frame` | çerçeve KIMLIĞI | Geçerli çerçeveyi belirtilen çerçeve KIMLIĞINE geçirir.
| `$load` | Komutları dosyadan yükler ve tamamlanana kadar yürütülür |
| `$proc` |  | Geçerli işlem KIMLIĞINI görüntüler. |
| `$proc` | işlem KIMLIĞI | Geçerli işlemi belirtilen işlem KIMLIĞINE geçirir. |
| `$procs` | | Şu anda hataları ayıklanan işlemlerin listesini görüntüler. |
| `$stepin`, `$step`, `$s` | Mümkünse sonraki işlev çağrısının adımları. |
| `$stepout`, `$return`, `$r` | Geçerli işlevin adımları. |
| `$stepover`, `$until`, `$unt` | Sonraki işlev çağrısının üzerindeki adımlar. |
| `$thread` | | Geçerli iş parçacığı KIMLIĞINI görüntüler. |
| `$thread` | iş parçacığı KIMLIĞI | Geçerli iş parçacığını belirtilen iş parçacığı KIMLIĞINE geçirir. |
| `$threads` | | Şu anda hata ayıklanan iş parçacıklarını listeler. |
| `$up`, `$u` | | Geçerli çerçeveyi yığın izlemesinde bir düzey yukarı taşı. |
| `$where`, `$w`, `$bt` | Geçerli iş parçacığının çerçevelerini listeler. |

**Süreçler**, **Iş parçacıkları** ve **çağrı yığını** gibi standart hata ayıklayıcı pencerelerinin **hata ayıklama etkileşimli** penceresiyle eşitlenmediğini unutmayın. **Hata ayıklama etkileşimli** penceresindeki etkin işlem, iş parçacığı veya çerçeveyi değiştirmek, diğer hata ayıklayıcı pencerelerini etkilemez. Benzer şekilde, diğer hata ayıklayıcı pencerelerinin etkin işlem, iş parçacığı veya çerçeveyi değiştirmek, **hata ayıklama etkileşimli** penceresini etkilemez.

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Eski hata ayıklayıcıyı kullanın

Visual Studio 2017 sürümleri 15,8 ve üzeri, ptvsd sürüm 4.1 + tabanlı bir hata ayıklayıcı kullanır. Visual Studio 2019 sürümleri 16,5 ve üzeri, hata ayıklayıcı gpy tabanlı bir hata ayıklayıcı kullanır. Hata ayıklayıcının bu sürümleri Python 2,7 ve Python 3.5 + ile uyumludur. python 2,6, 3,1-3,4 veya ıronpython kullanıyorsanız, Visual Studio hatayı gösteriyorsa, hata **ayıklayıcı bu Python ortamını desteklemez**:

![Hata ayıklayıcı kullanılırken hata ayıklayıcı bu Python ortamı hatasını desteklemez](media/debugging-experimental-incompatible-error.png)

bu durumlarda, daha eski hata ayıklayıcıyı kullanmanız gerekir (Visual Studio 2017 sürümleri 15,7 ve önceki sürümlerde varsayılandır). **Araç**  >  **seçenekleri** menü komutunu seçin, **Python**  >  **hata ayıklama** bölümüne gidin ve **eski hata ayıklayıcı kullan** seçeneğini belirleyin.

geçerli ortamda ptvsd 'in daha eski bir sürümünü (önceki bir sürüm. x sürümü veya uzaktan hata ayıklama için gereken 3. x sürümü) yüklediyseniz Visual Studio bir hata veya uyarı gösterebilir.

Hata, hata **ayıklayıcı paketi yüklenemedi**, ptvsd 3. x 'i yüklediğinizde görünür:

![Hata ayıklayıcı kullanılırken hata ayıklayıcı paketi yüklenemedi](media/debugging-experimental-version-error.png)

Bu durumda, eski hata ayıklayıcıyı **kullan** seçeneğini ayarlamak için **eski hata ayıklayıcıyı kullan** ' ı seçin ve hata ayıklayıcıyı yeniden başlatın.

Uyarı, **hata ayıklayıcı paketi güncel değil**, ptvsd 'in önceki 4. x sürümünü yüklediğinizde görüntülenir:

![Hata ayıklayıcı kullanılırken hata ayıklayıcı paketi güncel değil uyarısı](media/debugging-experimental-version-warning.png)

> [!Important]
> bazı ptvsd sürümleri için uyarıyı yok saymayı tercih edebilirsiniz, ancak Visual Studio düzgün çalışmayabilir.

Ptvsd yüklemenizi yönetmek için:

1. **Python ortamları** penceresinde **paketler** sekmesine gidin.

1. Arama kutusuna "ptvsd" yazın ve ptvsd 'in yüklü sürümünü inceleyin:

    ![Python ortamları penceresinde ptvsd sürümü denetleniyor](media/debugging-experimental-check-ptvsd.png)

1. sürüm 4.1.1 a9 'den düşükse (Visual Studio ile paketlenmiş sürüm), eski sürümü kaldırmak için paketin sağ tarafındaki **X** ' i seçin. Visual Studio daha sonra paketlenmiş sürümünü kullanır. (Kullanarak PowerShell 'den da kaldırabilirsiniz `pip uninstall ptvsd` .)

1. Alternatif olarak, [sorun giderme](#troubleshooting) bölümündeki yönergeleri izleyerek ptvsd paketini en yeni sürümüne güncelleştirebilirsiniz.

## <a name="troubleshooting"></a>Sorun giderme

### <a name="for-visual-studio-2019-version-164-and-earlier-upgrade-ptvsd"></a>Visual Studio 2019 (sürüm 16,4 ve önceki sürümler) için yükseltme ptvsd
Hata ayıklayıcıyla ilgili sorunlarınız varsa, önce hata ayıklayıcı sürümünüzü aşağıdaki gibi yükseltin:

1. **Python ortamları** penceresinde **paketler** sekmesine gidin.

1. `ptvsd --upgrade`Arama kutusuna girin ve ardından **komutu Çalıştır: pttrvsd--Upgrade**' i seçin. (PowerShell 'in aynı komutunu da kullanabilirsiniz.)

    ![Python ortamları penceresinde ptvsd Upgrade komutuna verme](media/debugging-experimental-upgrade-ptvsd.png)

   sorun devam ederse lütfen [ptv GitHub deposunda](https://github.com/Microsoft/ptvs/issues)bir sorun bildirin.

   > [!NOTE]
   > Visual Studio 2019 sürüm 16,5 ve üzeri için, hata ayıklama gpy Visual Studio Python iş yükünün bir parçasıdır ve Visual Studio birlikte güncelleştirilir.

### <a name="enable-debugger-logging"></a>Hata ayıklayıcı günlüğünü etkinleştir

Bir hata ayıklayıcı sorunu araştırırken, Microsoft, tanılamada yardım veren hata ayıklayıcı günlüklerini etkinleştirmenizi ve toplamanızı isteyebilir.

aşağıdaki adımlar geçerli Visual Studio oturumunda hata ayıklamayı etkinleştirir:

1. Visual Studio   >  **diğer Windows** göster  >  **komut penceresi** menü komutunu kullanarak bir komut penceresi açın.

1. Aşağıdaki komutu girin:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Hata ayıklamayı başlatın ve sorununuzu yeniden oluşturmak için gereken adımlarla ilerleyin. Bu süre boyunca hata ayıklama günlüğü, **hata ayıklama bağdaştırıcısı ana bilgisayar günlüğü** altındaki **Çıkış** penceresinde görüntülenir. daha sonra bu penceredeki günlükleri kopyalayabilir ve GitHub bir sorun, e-posta vb. yapıştırabilirsiniz.

    ![Çıkış penceresinde hata ayıklayıcı günlüğü çıkışı](media/debugger-logging-output.png)

1. Visual Studio yanıt vermeyi durdurursa veya **çıkış** penceresine erişemeyebilirsiniz, Visual Studio yeniden başlatın, bir komut penceresi açın ve aşağıdaki komutu girin:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Hata ayıklamayı başlatın ve sorunu yeniden oluşturun. Hata ayıklayıcı günlükleri içinde bulunabilir `%temp%\DebugAdapterHostLog.txt` .

## <a name="see-also"></a>Ayrıca bkz.

Visual Studio hata ayıklayıcıyla ilgili tüm ayrıntılar için bkz. [Visual Studio hata ayıklama](../debugger/debugger-feature-tour.md).
