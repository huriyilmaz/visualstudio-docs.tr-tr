---
title: Python kodunda hata ayıklama
description: Visual Studio kesme noktaları ayarlama, değerleri inceleme, özel durumlara bakma ve etkileşimli pencerede hata ayıklama da dahil olmak üzere Python kodu için zengin hata ayıklama sağlar.
ms.date: 01/17/2022
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 0122508789a889955f4f55e42b5811bb889f05ea
ms.sourcegitcommit: f81a8f381bcdbac96d112f815737ba1df55d97a3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137667479"
---
# <a name="debug-your-python-code"></a>Python kodunuzun hata ayıklaması

Visual Studio, çalışan işlemlere ekleme, İzleme ve Anında pencerelerde ifadeleri değerlendirme, yerel  değişkenleri inceleme, kesme noktaları, adım adım/dışarı/dışarı deyimleri, Sonraki Deyimi Ayarla ve daha fazlası dahil olmak üzere Python için kapsamlı bir hata ayıklama deneyimi sağlar. 

Ayrıca aşağıdaki senaryoya özgü hata ayıklama makalelerini de okuyun:

- [Linux uzaktan hata ayıklama](debugging-python-code-on-remote-linux-machines.md)
- [Karma mod Python/C++ hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Karışık mod hata ayıklaması için semboller](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Visual Studio Python, proje olmadan hata ayıklamayı destekler. Tek başına bir Python dosyası açıkken düzenleyicide sağ tıklayın, Hata Ayıklama ile Başla'yı seçin ve Visual Studio betiği genel varsayılan ortamla (bkz. [Python](managing-python-environments-in-visual-studio.md)ortamları) başlatıyor ve bağımsız değişken yok. Ancak bundan sonra tam hata ayıklama desteğine sahip oldur.
>
> Ortamı ve bağımsız değişkenleri kontrol etmek için kod için bir proje oluşturun. Bu proje, Mevcut Python kodundan [proje şablonuyla](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) kolayca yapılabilir.

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Temel hata ayıklama

Temel hata ayıklama iş akışı, aşağıdaki bölümlerde açıklandığı gibi ayarlar kesme noktaları, kodda adım adım ilerler, değerleri inceler ve özel durumları işlemeyi içerir.

Hata ayıklama oturumu Hata **AyıklamaYı** Başlat  >  **komutuyla,** araç **çubuğundaki Başlat** düğmesiyle veya **F5 tuşuyla** başlar. Bu eylemler, projenizin başlangıç dosyasını **(Çözüm Gezgini** kalın olarak gösterilir) projenin etkin ortamıyla ve **Project Özellikler'de** belirtilmiş komut satırı bağımsız değişkenleriyle veya arama yollarında (bkz. Project hata ayıklama seçenekleri) [başlatmaktadır.](#project-debugging-options) Visual Studio 2017 sürüm 15.6 ve sonraki sürümler, başlangıç dosya kümemiz yoksa sizi uyarabilir; önceki sürümler Python yorumlayıcısını çalıştıran bir çıkış penceresi açabilir veya çıkış penceresi kısa bir süre görünür ve kaybolur. Her durumda, uygun dosyaya sağ tıklayın ve Başlangıç Dosyası Olarak **Ayarla'yı seçin.**

> [!Note]
> Hata ayıklayıcısı her zaman proje için etkin Python ortamıyla başlar. Ortamı değiştirmek için, Proje için Python ortamı seçme konusunda [açıklandığı gibi farklı bir ortamı etkin hale seçin.](selecting-a-python-environment-for-a-project.md)

### <a name="breakpoints"></a>Kesme noktaları

Kesme noktaları, program durumunu incelerken işaretlenmiş bir noktada kodun yürütülmesini durdurur. Kod düzenleyicisinin sol kenar boşluğuna tıklayarak veya bir kod satırına sağ tıklar ve Kesme Noktası Ekle Kesme Noktası seçeneğini   >  **kullanarak kesme noktaları ayarlayın.** Her satırda kesme noktası olan kırmızı bir nokta görünür.

![Kesme noktaları Visual Studio](media/debugging-breakpoints.png)

Kırmızı noktaya tıklar veya kod satırına sağ tıklar ve Kesme Noktası Silme Kesme  >  **Noktası'nın seçimi** kesme noktası kaldırır. Kesme Noktası Kesme Noktası Devre Dışı Bırak komutunu kullanarak **kaldırmadan da**  >  **devre dışı abilirsiniz.**

> [!Note]
> Python'daki bazı kesme noktaları, diğer programlama dilleriyle çalışan geliştiriciler için şaşırtıcı olabilir. Python'da dosyanın tamamı yürütülebilir koddur; bu nedenle Python, herhangi bir üst düzey sınıf veya işlev tanımlarını işlemeye yüklendiğinde dosyayı çalıştırır. Bir kesme noktası ayarlanmışsa, hata ayıklayıcının bir sınıf bildirimi aracılığıyla parça parça hatasını bulabilirsiniz. Bazen şaşırtıcı olsa da bu davranış doğrudur.

Yalnızca bir değişken belirli bir değere veya değer aralığına ayarlanırken kesme noktası tetiklenen koşulları özelleştirebilirsiniz. Koşulları ayarlamak için kesme noktası kırmızı noktaya sağ tıklayın, Koşul'u **seçin** ve Python kodunu kullanarak ifadeler oluşturun. Bu özellik hakkında ayrıntılı bilgi için Visual Studio bkz. [Kesme noktası koşulları.](../debugger/using-breakpoints.md#breakpoint-conditions)

Koşulları ayarlarken Eylem'i de **ayarp** çıkış penceresinde oturum açmak için isteğe bağlı olarak yürütmeyi otomatik olarak devam ettiren bir ileti oluşturabilirsiniz. İletiyi günlüğe kaydetme, doğrudan *uygulamanıza günlük kodu* eklemeden izleme noktası olarak adlandırılan şeyi oluşturur:

![Kesme noktası ile izleme noktası oluşturma](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Kodda adım adım ilerler

Kesme noktası durdurulduktan sonra, yeniden kesmeden önce kodda adım adım veya kod bloklarını çalıştırmanın çeşitli yolları vardır. Bu komutlar, üst hata ayıklama araç çubuğu, Hata  Ayıklama menüsü, kod düzenleyicisinde sağ tıklama bağlam menüsü ve klavye kısayolları aracılığıyla (tüm komutlar her yerde yer alamasa da) gibi çeşitli yerlerde kullanılabilir:

| Özellik | Tuş | Description |
| --- | --- | --- |
| **Devam et** | **F5** | Sonraki kesme noktası ulaşıncaya kadar kodu çalıştırır. |
| **Adımla** | **F11** | Sonraki deyimi çalıştırır ve durur. Sonraki deyim bir işlev çağrısı ise, hata ayıklayıcı çağrılan işlevin ilk satırına durur. |
| **Adım At** | **F10** | Bir işleve çağrı yapma (tüm kodunu çalıştırma) ve herhangi bir dönüş değerini uygulama da dahil olmak üzere sonraki deyimi çalıştırır. Üzerine adımlama, hata ayıklamak zorunda olmadığınız işlevleri kolayca atlamanizi sağlar. |
| **Dışarı Adımla** | **Üstkrkt** + **F11** | Geçerli işlevin sonuna kadar kodu çalıştırır ve ardından çağırma deyimine doğru adımlar.  Bu komut, geçerli işlevin geri kalanında hata ayıklamaya gerek olmadığınız zaman kullanışlıdır. |
| **İmleç'e Çalıştır** | **Ctrl** + **F10** | Kodu düzenleyicide caret'in bulunduğu konuma kadar çalıştırır. Bu komut, hata ayıklamak zorunda olmadığınız bir kod kesimini kolayca atlayabilirsiniz. |
| **Sonraki Deyimi Belirle** | **Ctrl** + **Üstkrkt** + **F10** | Kodda geçerli çalışma noktasını, dikkat noktasının konumu olarak değiştirir. Bu komut, kodun hatalı olduğunu bildiğiniz veya istenmeyen bir yan etki ürettiğinde kod parçasının hiç çalıştırılamamalarını sağlar. |
| **Sonraki Deyimi Göster** | **Alt** + **Num** **&#42;**| Sizi çalıştıracak sonraki deyime döndürür. Bu komut, kodunuza bakıyorsanız ve hata ayıklayıcının nerede durdurulmuş olduğunu anımsamasanız yararlıdır. |

### <a name="inspect-and-modify-values"></a>Değerleri inceleme ve değiştirme

Hata ayıklayıcıda durdurulurken değişkenlerin değerlerini inceleyebilirsiniz ve değiştirebilirsiniz. Ayrıca, tek tek değişkenleri **ve** özel ifadeleri izlemek için İzleme penceresini de kullanabilirsiniz. (Genel [ayrıntılar için bkz.](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows) Değişkenleri inceleme.)

**DataTips** kullanarak bir değeri görüntülemek için fareyi düzenleyicide herhangi bir değişkenin üzerine gelmeniz gerekir. Değiştirmek için değeri seçin:

![Visual Studio hata ayıklayıcısında gösterilen DataTips](media/debugging-quick-tips.png)

Otomatikler **penceresi** (**Hata**  >  **ayıklama Windows**  >  **Autos**) geçerli deyime yakın değişkenleri ve ifadeleri içerir. Değer sütununa çift tıklar veya F2 tuşuna **basarak** değeri düzenleyebilirsiniz:

![Hata ayıklayıcısında otomatik Visual Studio penceresi](media/debugging-autos-window.png)

Yereller **penceresi** (**Hata**  >  **Windows**  >  **Yereller)** geçerli kapsamda bulunan ve yeniden düzenlenebilir tüm değişkenleri görüntüler:

![Visual Studio hata ayıklayıcısında yereller penceresi](media/debugging-locals-window.png)

Otomatikler ve **Yereller kullanma hakkında** daha fazla bilgi **için,** [Bkz. Otomatikler ve Yereller pencerelerinde değişkenleri inceleme.](../debugger/autos-and-locals-windows.md)

İzleme **pencereleri** (**İzleme**  >  **1-4 Windows** hata ayıkla ) rastgele Python ifadeleri girmenize ve sonuçları  >    >  görüntülemenize olanak sağlar. İfadeler her adım için yeniden değerlendirildi:

![izleme penceresi hata ayıklayıcısında Visual Studio hata ayıklayıcısı](media/debugging-watch-window.png)

İzleme kullanma hakkında **daha fazla bilgi** için bkz. Watch ve QuickWatch pencerelerini kullanarak değişkenler üzerinde izleme [ayarlama.](../debugger/watch-and-quickwatch-windows.md)

Bir dize değerini ( , , ve bu amaçla dize olarak kabul edilir) incelerken değerin sağ tarafında bir `str` `unicode` `bytes` `bytearray` büyüteç simgesi görünür. Simgeyi seçmek, uzun dizeler için yararlı olan sarmalama ve kaydırma ile birlikte bir açılan iletişim kutusunda, irdesiz dize değerini görüntüler. Ayrıca simgede açılan oku seçerek düz metin, HTML, XML ve JSON görselleştirmelerini de seçmenize olanak sağlar:

![Visual Studio hata ayıklayıcısında dize görselleştiricileri](media/debugging-string-visualizers.png)

HTML, XML ve JSON görselleştirmeleri, söz dizimi vurgulama ve ağaç görünümleri ile ayrı açılan pencerelerde görünür.

### <a name="exceptions"></a>Özel durumlar

Hata ayıklama sırasında programda hata oluşursa ama bunun için bir özel durum işleyiciniz yoksa, hata ayıklayıcı özel durumun noktasında bozar:

![Hata ayıklayıcısında özel Visual Studio açılır](media/debugging-exception-popup.png)

Bu noktada, çağrı yığını da dahil olmak üzere program durumunu incelersiniz. Ancak, kodda adım adım ilerlersanız, özel durum işilene veya programınız çıkana kadar özel durum yine de devam eder.

Hata **ayıklama**  >  **Windows**  >  **Özel Ayarlar** menü komutu, Python Özel Durumları'na genişletebilirsiniz: 

![Hata ayıklayıcısında özel Visual Studio penceresi](media/debugging-exception-settings.png)

Her özel durum için onay kutusu, hata ayıklayıcısının *her zaman hata* ayıklayıcısının ne zaman hataya neden olduğunu kontrol eder. Belirli bir özel durum için daha sık daha fazla bölmek istiyorsanız bu kutuyu işaretleyin.

Varsayılan olarak, bir özel durum işleyicisi kaynak kodunda bulunamadığında, en çok özel durumlar kesilir. Bu davranışı değiştirmek için herhangi bir özel duruma sağ tıklayın ve **Kullanıcı kodunda Işlenmediğinde devam et** seçeneğini değiştirin. Bir özel durum için daha az sıklıkta bölmek istediğinizde bu kutuyu temizleyin.

Bu listede görünmeyen bir özel durum yapılandırmak için **Ekle düğmesini seçerek ekleyin.** Ad, özel durumun tam adıyla eşleşmelidir.

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
| `$up`, `$u` | | Geçerli çerçeveyi yığın izlemesinde bir düzey yukarı taşıyın. |
| `$where`, `$w`, `$bt` | Geçerli iş parçacığının çerçevelerini listeler. |

**Süreçler**, **Iş parçacıkları** ve **çağrı yığını** gibi standart hata ayıklayıcı pencereleri **hata ayıklama etkileşimli** penceresiyle eşitlenmez. **Hata ayıklama etkileşimli** penceresinde etkin işlem, iş parçacığı veya çerçeveyi değiştirmek, diğer hata ayıklayıcı pencerelerini etkilemez. Benzer şekilde, diğer hata ayıklayıcı Windows 'daki etkin işlem, iş parçacığı veya çerçeveyi değiştirmek, **hata ayıklama etkileşimli** penceresini etkilemez.

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Eski hata ayıklayıcıyı kullanın

Visual Studio 2017 sürümleri 15,8 ve üzeri, ptvsd sürüm 4.1 + tabanlı bir hata ayıklayıcı kullanır. Visual Studio 2019 sürümleri 16,5 ve üzeri, hata ayıklayıcı gpy tabanlı bir hata ayıklayıcı kullanır. Hata ayıklayıcının bu sürümleri Python 2,7 ve Python 3.5 + ile uyumludur. python 2,6, 3,1-3,4 veya ıronpython kullanıyorsanız, Visual Studio hatayı gösteriyorsa, hata **ayıklayıcı bu Python ortamını desteklemez**:

![Hata ayıklayıcı kullanılırken hata ayıklayıcı bu Python ortamı hatasını desteklemez](media/debugging-experimental-incompatible-error.png)

bu durumlarda, eski hata ayıklayıcıyı kullanmanız gerekir (Visual Studio 2017 sürümleri 15,7 ve önceki sürümlerde varsayılandır). **Araç**  >  **seçenekleri** menü komutunu seçin, **Python**  >  **hata ayıklama** bölümüne gidin ve **eski hata ayıklayıcı kullan** seçeneğini belirleyin.

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
