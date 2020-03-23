---
title: Hata Ayıklama Python kodu
description: Visual Studio, kesme noktaları ayarlama, adım atma, değerleri denetleme, özel durumlara bakma ve etkileşimli pencerede hata ayıklama dahil olmak üzere Python kodu için zengin hata ayıklama sağlar.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302891"
---
# <a name="debug-your-python-code"></a>Python kodunuzu hata ayıklama

Visual Studio, Python için çalışan işlemlere bağlanma, **Watch** ve **Immediate** pencerelerinde ifadeleri değerlendirme, yerel değişkenleri inceleme, kesme noktaları, adım/çıkış/çıktı ifadeleri, **Sonraki Bildirimi Ayarla**ve daha fazlası dahil olmak üzere kapsamlı bir hata ayıklama deneyimi sağlar.

Ayrıca aşağıdaki senaryoya özgü hata ayıklama makalelerini de görebilirsiniz:

- [Linux uzaktan hata ayıklama](debugging-python-code-on-remote-linux-machines.md)
- [Karışık modlu Python/C++ hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Karışık mod hata ayıklaması için semboller](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Visual Studio'daki Python, proje olmadan hata ayıklamayı destekler. Tek başına python dosyası açıkken, düzenleyicide sağ tıklatMa, **Hata Ayıklama ile Başlat'ı**seçin ve Visual Studio komut dosyasını genel varsayılan ortamla başlatır [(Bkz. Python ortamları)](managing-python-environments-in-visual-studio.md)ve bağımsız değişken yok. Ama o andan itibaren, tam hata ayıklama desteğine sahipsin.
>
> Ortamı ve bağımsız değişkenleri denetlemek için, [varolan Python kodu](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) proje şablonu yla kolayca yapılabilen kod için bir proje oluşturun.

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Temel hata ayıklama

Temel hata ayıklama iş akışı ayarları kesme noktalarını, kod üzerinden adım atmayı, değerleri denetlemeyi ve aşağıdaki bölümlerde açıklandığı gibi özel durumları işlemeyi içerir.

Hata ayıklama oturumu Hata **Ayıklama** > **Başlat** komutu, araç çubuğundaki **Başlat** düğmesi veya **F5** tuşu ile başlar. Bu eylemler, projenin etkin ortamı ve **Proje Özellikleri'nde** belirtilen komut satırı bağımsız değişkenleri veya arama yolları ile projenizin başlangıç dosyasını **(Çözüm Gezgini'nde**kalın olarak gösterilir) başlatın (bkz. Proje [hata ayıklama seçenekleri).](#project-debugging-options) Visual Studio 2017 sürüm 15.6 ve daha sonra bir başlangıç dosyası seti yoksa sizi uyarır; Önceki sürümler Python yorumlayıcısı çalışırken bir çıkış penceresi açabilir veya çıktı penceresi kısa bir süre görünür ve kaybolur. Her durumda, uygun dosyayı sağ tıklatın ve **Başlangıç Dosyası olarak ayarla'yı**seçin.

> [!Note]
> Hata ayıklayıcısı her zaman proje için etkin Python ortamı yla başlar. Ortamı değiştirmek [için, proje için Python ortamı nı seçin'de](selecting-a-python-environment-for-a-project.md)açıklandığı gibi farklı bir etkin olun.

### <a name="breakpoints"></a>Kesme Noktaları

Kesme noktaları, program durumunu inceleyebilmeniz için kodun işaretli bir noktada yürütülmesini durdurur. Kod düzenleyicisinin sol kenar boşluğuna tıklayarak veya bir kod satırına sağ tıklayarak ve **Breakpoint** > Ekle Kesme Noktası'nı seçerek kesme**noktalarını**ayarlayın. Her satırda bir kesme noktası olan kırmızı bir nokta görünür.

![Visual Studio'da görünen kırılma noktaları](media/debugging-breakpoints.png)

Kırmızı noktayı tıklatmak veya kod satırına sağ tıklayıp **Kesme Noktası** > **Silme noktasını** seçmek kesme noktasını kaldırır. **Ayrıca, Breakpoint** > Devre Dışı Kaldırma Noktası komutunu kullanarak kaldırmadan devre dışı**kullanabilirsiniz.**

> [!Note]
> Python'daki bazı kesme noktaları, diğer programlama dilleriyle çalışmış geliştiriciler için şaşırtıcı olabilir. Python'da, dosyanın tamamı yürütülebilir koddur, bu nedenle Python dosyayı yüklendiğinde üst düzey sınıf veya işlev tanımlarını işlemek için çalıştırılır. Bir kesme noktası ayarlanmışsa, hata ayıklayıcının sınıf bildiriminde yarı yolda kırıldığını görebilirsiniz. Bu davranış bazen şaşırtıcı olsa da, doğrudur.

Yalnızca bir değişken belirli bir değer veya değer aralığına ayarlandığında kesme gibi bir kesme noktasının tetiklendiği koşulları özelleştirebilirsiniz. Koşulları ayarlamak için kesme noktasının kırmızı noktasını sağ tıklatın, **Koşul'u**seçin ve Python kodunu kullanarak ifadeler oluşturun. Visual Studio'daki bu özellik hakkında tüm ayrıntılar için [Breakpoint koşullarına](../debugger/using-breakpoints.md#breakpoint-conditions)bakın.

Koşulları ayarlarken, **Eylem'i** de ayarlayabilir ve çıkış penceresine günlüğe kaydacak ve isteğe bağlı olarak yürütmeyi otomatik olarak devam ettirecek bir ileti oluşturabilirsiniz. İletiyi günlüğe kaydetme, doğrudan uygulamanıza günlük kodu eklemeden *izleme noktası* olarak adlandırılan noktayı oluşturur:

![Kesme noktası yla izleme noktası oluşturma](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Kodda adım atma

Bir kesme noktasında durdurulduktan sonra, yeniden bölmeden önce kod üzerinden adım veya kod blokları çalıştırmak için çeşitli yolları vardır. Bu komutlar, kod düzenleyicisindeki sağ tıklama bağlam menüsünde üst hata ayıklama araç çubuğu, **Hata Ayıklama** menüsü ve klavye kısayolları (tüm komutlar her yerde olmasa da) dahil olmak üzere birçok yerde kullanılabilir:

| Özellik | Tuş | Açıklama |
| --- | --- | --- |
| **Devam** | **F5** | Bir sonraki kesme noktasına ulaşılana kadar kodu çalıştırın. |
| **Adım Adım** | **F11** | Bir sonraki ifadeyi çalıştırın ve durur. Bir sonraki deyim bir işleve çağrı ysa, hata ayıklama çağrılan işlevin ilk satırında durur. |
| **Adım Adım** | **F10** | Bir işleve çağrı yapmak (tüm kodunu çalıştırma) ve herhangi bir iade değeri uygulamak dahil olmak üzere bir sonraki deyimi çalıştırın. Üzerine basma, hata ayıklamanız gerekmeyen işlevleri kolayca atlayabilmenizi sağlar. |
| **Dışarı Adım** | **Shift**+**F11** | Geçerli işlevin sonuna kadar kodu çalıştırır, ardından çağrı deyimine adımlar atar.  Bu komut, geçerli işlevin geri kalanını hata ayıklamanız gerekmediğinde yararlıdır. |
| **İmlec'e Çalıştır** | **Ctrl**+**F10** | Kodu düzenleyicideki bakıcının konumuna kadar çalıştırıyor. Bu komut, hata ayıklamanız gerekmeyen bir kod kesimini kolayca atlayabilmenizi sağlar. |
| **Sonraki Deyimi Belirle** | **Ctrl**+**Shift**+**F10** | Koddaki geçerli çalışma noktasını bakıcının konumuyla değiştirir. Bu komut, kodun hatalı olduğunu bildiğiniz veya istenmeyen bir yan etki ürettiği nde olduğu gibi, kodun bir kesiminin çalıştırılmaktan tamamen atlamasına olanak tanır. |
| **Sonraki İfadeyi Göster** | **Alt**+**Num** **&#42;**| Çalıştırmak için bir sonraki deyim için döndürür. Bu komut, kodunuzda etrafa bakıyorsanız ve hata ayıklayıcının nerede durdurulduğunu hatırlamıyorsanız yararlıdır. |

### <a name="inspect-and-modify-values"></a>Değerleri inceleyin ve değiştirin

Hata ayıklamada durdurulduğunda, değişkenlerin değerlerini inceleyebilir ve değiştirebilirsiniz. Tek tek değişkenleri ve özel ifadeleri izlemek için **İzle** penceresini de kullanabilirsiniz. (Genel ayrıntılar için [değişkenleri inceleyin.)](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows)

**DataTips**kullanarak bir değeri görüntülemek için, yalnızca düzenleyicideki herhangi bir değişkenin üzerinde farenin üzerinde gezinmek yeterlidir. Değiştirmek için değeri tıklatabilirsiniz:

![Visual Studio hata ayıklamada gösterilen Veri İpuçları](media/debugging-quick-tips.png)

**Otomatik Ler** penceresi **(Hata Ayıklama** > **Windows** > **Autos)** geçerli deyime yakın değişkenler ve ifadeler içerir. Değer sütununa çift tıklayabilir veya değeri yeniden leştirmek için **F2** tuşuna basabilirsiniz:

![Visual Studio hata ayıklamasında otomatik pencere](media/debugging-autos-window.png)

**Yerel Aygıtlar** penceresi **(Hata Ayıklama** > **Windows** > **Locals),** geçerli kapsamda bulunan ve yeniden düzenlenebilecek tüm değişkenleri görüntüler:

![Visual Studio hata ayıklama yerel pencere](media/debugging-locals-window.png)

Otomatik ve **Yerel'leri** kullanma hakkında daha fazla şey için bkz: Otomatik ler [ve Locals pencerelerinde değişkenleri inceleyin.](../debugger/autos-and-locals-windows.md) **Locals**

**Watch** pencereleri **(Hata Ayıklama** > **Windows** > **Watch** > **Watch 1-4),** rasgele Python ifadeleri girmenize ve sonuçları görüntülemenize olanak sağlar. İfadeler her adım için yeniden değerlendirilir:

![Visual Studio hata ayıklama penceresini izleyin](media/debugging-watch-window.png)

**Watch'u**kullanma hakkında daha fazla bilgi için bkz: [Watch ve QuickWatch pencerelerini kullanarak değişkenleri](../debugger/watch-and-quickwatch-windows.md)ayarla.

Bir dize değerini`str`incelerken (, `unicode`, `bytes`, ve `bytearray` bu amaç için tüm dizeleri olarak kabul edilir), bir büyüteç simgesi değeri sağ tarafında görünür. Simgeyi tıklattığınızda, uzun dizeleri için yararlı olan kaydırma ve kaydırma ile bir pop-up iletişim kutusunda tırnak içinde tırnak içinde dize değeri görüntülenir. Buna ek olarak, simgedeki açılır ok seçilerek düz metin, HTML, XML ve JSON görselleştirmeleri seçmenize olanak tanır:

![Visual Studio hata ayıklayıcısında string görselleştiricileri](media/debugging-string-visualizers.png)

HTML, XML ve JSON görselleştirmeleri sözdizimi vurgulama ve ağaç görünümleri ile ayrı açılır pencerelerde görünür.

### <a name="exceptions"></a>Özel durumlar

Hata ayıklama sırasında programınızda bir hata oluşursa, ancak bunun için bir özel durum işleyiciniz yoksa, hata ayıklayıcı özel durum noktasında kırılır:

![Visual Studio hata ayıklama özel durum açılır](media/debugging-exception-popup.png)

Bu noktada, çağrı yığını da dahil olmak üzere program durumunu inceleyebilirsiniz. Ancak, kodu aşmaya çalışırsanız, özel durum işlenir veya programınız çıkana kadar atılmaya devam eder.

**Hata Ayıklama** > **Windows** > **Özel Durum Ayarları** menüsü komutu, Python Özel **Durumlarını**genişletebileceğiniz bir pencere yi getirir:

![Visual Studio hata ayıklamasındaki özel durumlar penceresi](media/debugging-exception-settings.png)

Her özel durum için onay kutusu, hata ayıklamanın yükseltildiğinde *her zaman* kırılıp kırılmadığını denetler. Belirli bir özel durum için daha sık kırmak istediğinizde bu kutuyu işaretleyin.

Varsayılan olarak, bir özel durum işleyicisi kaynak kodunda bulunamadığında çoğu özel durum kırılır. Bu davranışı değiştirmek için, herhangi bir özel durumu sağ tıklatın ve **Kullanıcı Kodu'nda İşlenmediğinde Devam** et seçeneğini değiştirin. Bir istisna için daha az sıklıkta kırmak istediğinizde bu kutuyu temizleyin.

Bu listede görünmeyen bir özel durumu yapılandırmak için eklemek için **Ekle** düğmesini tıklatın. Ad, özel durum tam adı eşleşmelidir.

## <a name="project-debugging-options"></a>Proje hata ayıklama seçenekleri

Varsayılan olarak, hata ayıklayıcı programınızı standart Python başlatıcısı, komut satırı bağımsız değişkeni ve başka özel yollar veya koşullarla başlatır. Başlangıç seçenekleri, **Çözüm Gezgini'nde**projenizi sağ tıklatarak, **Özellikler'i**seçerek ve **Hata** Ayıklama sekmesini seçerek projeye erişilen hata ayıklama özellikleri yle değiştirilir.

![Visual Studio hata ayıklamasındaproje hata ayıklama özellikleri](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Başlatma modu seçenekleri

| Seçenek | Açıklama |
| --- | --- |
| **Standart Python başlatıcısı** | CPython, IronPython ve Stackless Python gibi türevleri ile uyumlu taşınabilir Python yazılmış hata ayıklama kodunu kullanır. Saf Python kodunu hata ayıklamak için en iyi deneyimi sağlar. Çalışan bir *python.exe* işlemine bağlandığınızda, bu başlatıcı kullanılır. Bu başlatıcı ayrıca CPython için [karışık mod hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) sağlar, C / C++ kodu ve Python kodu arasında sorunsuz adım sağlar. |
| **Web başlatıcısı** | Varsayılan tarayıcınızı başlatmada başlatır ve şablonların hata ayıklanmasını sağlar. Daha fazla bilgi için [Web şablonu hata ayıklama](python-web-application-project-templates.md#debugging) bölümüne bakın. |
| **Django Web başlatıcısı** | Web başlatıcısı ile aynıdır ve yalnızca geriye dönük uyumluluk için gösterilir. |
| **IronPython (.NET) başlatıcısı** | Yalnızca IronPython ile çalışan ancak C# ve VB dahil olmak üzere herhangi bir .NET dil projesi arasında adım atmaya olanak tanıyan .NET hata ayıklayıcısı kullanır. Bu başlatıcı, IronPython barındıran çalışan bir .NET işlemine iliştirilerseniz kullanılır. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Çalışma seçenekleri (arama yolları, başlangıç bağımsız değişkenleri ve ortam değişkenleri)

| Seçenek | Açıklama |
| --- | --- |
| **Arama Yolları** | Bu değerler, **çözüm gezgininde**projenin **Arama Yolları** düğümünde gösterilenlerle eşleşir. Bu değeri burada değiştirebilirsiniz, ancak klasörlere göz atmanızı ve yolları otomatik olarak göreli forma dönüştürmenizi sağlayan **Solution Explorer'ı** kullanmak daha kolaydır. |
| **Komut Dosyası Bağımsız Değişkenleri** | Bu bağımsız değişkenler, komut dosyanızın dosya adından sonra görünen komutunuzu başlatmak için kullanılan komuta eklenir. Buradaki ilk öğe komut dosyanız `sys.argv[1]`için , `sys.argv[2]`ikinci öğe olarak ve benzeri olarak kullanılabilir. |
| **Tercüman Argümanları** | Bu bağımsız değişkenler komut dosyanızın adından önce başlatıcı komut satırına eklenir. Burada sık `-W ...` karşılaşılan bağımsız `-O` değişkenler uyarıları denetlemek, `-u` programınızı biraz optimize etmek ve arabelleğe alamayan IO'ları kullanmaktır. IronPython kullanıcıları gibi `-X` `-X:Frames` seçenekleri geçmek için bu alanı `-X:MTA`kullanmak olasıdır. |
| **Tercüman Yolu** | Geçerli ortamla ilişkili yolu geçersiz kılar. Bu değer, komut dosyanızı standart olmayan bir yorumlayıcıyla başlatmak için yararlı olabilir. |
| **Çevre Değişkenleri** | Bu çok satırlı metin kutusuna, \<NAME>\<= VALUE> formunun girişlerini ekleyin. Bu ayar en son uygulandığından, varolan tüm genel `PYTHONPATH` ortam değişkenlerinin üstüne ve **Arama Yolları** ayarına göre ayarlandıktan sonra, diğer değişkenlerden herhangi birini el ile geçersiz kılmak için kullanılabilir. |

## <a name="immediate-and-interactive-windows"></a>Anında ve Etkileşimli pencereler

Hata ayıklama oturumu sırasında kullanabileceğiniz iki etkileşimli pencere vardır: standart Visual Studio **Immediate** penceresi ve **Python Hata Ayıklama Etkileşimli** penceresi.

**Hemen** penceresi **(Hata Ayıklama** > **Windows** > **Immediate)** Python ifadelerinin hızlı değerlendirilmesi ve çalışan programdaki değişkenlerin incelenmesi veya atanması için kullanılır. Ayrıntılar için genel [Acil pencere](../ide/reference/immediate-window.md) makalesine bakın.

**Python Hata Ayıklama Etkileşimli** penceresi **(Hata Ayıklama** > **Windows** > **Python Debug Interactive)** yazı yazma ve kod çalıştırma dahil olmak üzere hata ayıklama sırasında tam [Etkileşimli REPL](python-interactive-repl-in-visual-studio.md) deneyimini kullanılabilir hale getirir gibi daha zengindir. Standart Python başlatıcısını kullanarak hata ayıklayıcıda başlatılan herhangi bir işleme otomatik olarak bağlanır **(Hata Ayıklama** > Ile**İşleme**Ekle ile eklenen işlemler dahil). Ancak, karışık modlu C/C++ hata ayıklama kullanılırken kullanılamaz.

![Python Hata Ayıklama Etkileşimli pencere](media/debugging-interactive.png)

**Hata Ayıklama Etkileşimli** [pencere, standart REPL komutlarına](python-interactive-repl-in-visual-studio.md#meta-commands)ek olarak özel meta komutları destekler:

| Komut | Bağımsız Değişkenler | Açıklama |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Geçerli deyimden programı çalıştırmaya başlar. |
| `$down`, `$d` | Geçerli çerçeveyi yığın izinde bir düzey aşağı taşıyın. |
| `$frame` | | Geçerli çerçeve kimliğini görüntüler.
| `$frame` | çerçeve kimliği | Geçerli çerçeveyi belirtilen çerçeve kimliğine değiştirir.
| `$load` | Komutları dosyadan yükler ve tamamlanana kadar yürütür |
| `$proc` |  | Geçerli işlem kimliğini görüntüler. |
| `$proc` | işlem kimliği | Geçerli işlemi belirtilen işlem kimliğine değiştirir. |
| `$procs` | | Şu anda debugged olan işlemleri listeler. |
| `$stepin`, `$step`, `$s` | Mümkünse bir sonraki işlev çağrısına adım. |
| `$stepout`, `$return`, `$r` | Geçerli işlevin dışına adım. |
| `$stepover`, `$until`, `$unt` | Bir sonraki işlev çağrısının üzerinden adımlar. |
| `$thread` | | Geçerli iş parçacığı kimliğini görüntüler. |
| `$thread` | iş parçacığı kimliği | Geçerli iş parçacığının belirtilen iş parçacığı kimliğine geçişini. |
| `$threads` | | Şu anda debugged olan iş parçacıklarını listeler. |
| `$up`, `$u` | | Geçerli çerçeveyi yığın izinde bir üst düzeyyukarı taşıyın. |
| `$where`, `$w`, `$bt` | Geçerli iş parçacığının çerçevelerini listeler. |

**İşlemler,** **İş Parçacıkları**ve **Çağrı Yığını** gibi standart hata ayıklama pencerelerinin **Hata Ayıklama Etkileşimli** penceresiyle eşitlenmediğini unutmayın. **Hata Ayıklama Etkileşimli** penceredeki etkin işlem, iş parçacığı veya çerçevenin değiştirilmesi diğer hata ayıklayıcı pencerelerini etkilemez. Benzer şekilde, diğer hata ayıklayıcı penceredeki etkin işlem, iş parçacığı veya çerçevenin değiştirilmesi **Debug Interactive** penceresini etkilemez.

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Eski hata ayıklamayı kullanma

Visual Studio 2017 sürümleri 15.8 ve daha sonra ptvsd sürüm 4.1+ dayalı bir hata ayıklayıcı kullanın. ptvsd'nin bu sürümü Python 2.7 ve Python 3.5+ ile uyumludur. Python 2.6, 3.1- 3.4 veya IronPython kullanıyorsanız, Visual Studio hatayı **gösterirse, Hata Ayıklayıcı bu Python ortamını desteklemez:**

![Hata ayıklama, hata ayıklamayı kullanırken bu Python ortamı hatasını desteklemez](media/debugging-experimental-incompatible-error.png)

Bu gibi durumlarda eski hata ayıklama (Visual Studio 2017 sürümleri 15.7 ve önceki varsayılan) kullanmanız gerekir. **Araçlar** > **Seçenekleri** menüsü komutunu seçin, **Python** > **Hata Ayıklama'ya**gidin ve eski hata **ayıklama** aracını kullan seçeneğini seçin.

Geçerli ortama ptvsd'nin eski bir sürümünü yüklediyseniz (örneğin, daha önceki bir 4.0.x sürümü veya uzaktan hata ayıklama için gerekli olan 3.x sürümü gibi), Visual Studio bir hata veya uyarı gösterebilir.

Hata, **Hata Ayıklayıcı paketi yüklenemedi**, ptvsd 3.x yüklediğinizde görünür:

![Hata ayıklama paketi hata ayıklama kullanırken hata yüklenemedi](media/debugging-experimental-version-error.png)

Bu durumda, **eski hata ayıklama** seçeneğini kullanmak ve hata ayıklama aracını yeniden başlatmak için **eski hata ayıklama** aracını kullan'ı seçin.

Uyarı, **Hata Ayıklayıcı paketi eski,** ptvsd önceki bir 4.x sürümünü yüklediğinizde görünür:

![Hata ayıklama paketi hata ayıklama kullanırken eski uyarı](media/debugging-experimental-version-warning.png)

> [!Important]
> Eğer ptvsd bazı sürümleri için uyarı yoksaymayı seçebilirsiniz rağmen, Visual Studio doğru çalışmayabilir.

Ptvsd kurulumunuzu yönetmek için:

1. **Python Ortamları** penceresindeki **Paketler** sekmesine gidin.

1. Arama kutusuna "ptvsd" girin ve ptvsd yüklü sürümünü inceleyin:

    ![Python Ortamları penceresindeki ptvsd sürümünü denetleme](media/debugging-experimental-check-ptvsd.png)

1. Sürüm 4.1.1a9'dan (Visual Studio ile birlikte verilen sürüm) daha düşükse, eski sürümü kaldırmak için paketin sağındaki **X'i** seçin. Visual Studio daha sonra birlikte verilen sürümünü kullanır. (PowerShell'den de kaldırabilirsiniz.) `pip uninstall ptvsd`

1. Alternatif olarak, [Sorun Giderme](#troubleshooting) bölümündeki yönergeleri izleyerek ptvsd paketini en yeni sürümüne güncelleştirebilirsiniz.

## <a name="troubleshooting"></a>Sorun giderme

Hata ayıklayıcı ile ilgili sorunlarınız varsa, öncelikle ptvsd sürümünüzü aşağıdaki gibi yükseltin:

1. **Python Ortamları** penceresindeki **Paketler** sekmesine gidin.

1. Arama `ptvsd --upgrade` kutusuna girin, sonra **Çalıştır komutunu seçin: pip yüklemek ptvsd --yükseltme**. (PowerShell'den de aynı komutu kullanabilirsiniz.)

    ![Python Ortamları penceresinde ptvsd yükseltme komutunu verme](media/debugging-experimental-upgrade-ptvsd.png)

Sorunlar devam ederse, lütfen [PTVS GitHub deposunda](https://github.com/Microsoft/ptvs/issues)bir sorun dosyalayın.

### <a name="enable-debugger-logging"></a>Hata ayıklama günlüğe kaydetmeyi etkinleştirme

Bir hata ayıklama sorununu araştırma süresince Microsoft, tanıda yardımcı olan hata ayıklama günlüklerini etkinleştirmenizi ve toplamanızı isteyebilir.

Aşağıdaki adımlar, geçerli Visual Studio oturumunda hata ayıklama sağlar:

1. **Diğer Windows** > **Komut Penceresini** **Görüntüle** > menüsü komutunu kullanarak Visual Studio'da bir komut penceresi açın.

1. Aşağıdaki komutu girin:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Hata ayıklamaya başlayın ve sorununuzu yeniden oluşturmak için gereken adımları atın. Bu süre zarfında hata ayıklama günlükleri **Hata Ayıklama Bağdaştırıcısı Ana Günlüğü'nün**altında **Çıktı** penceresinde görünür. Daha sonra bu pencereden günlükleri kopyalayabilir ve bir GitHub sorunu, e-posta, vb içine yapıştırın.

    ![Çıkış penceresinde hata ayıklama günlüğe kaydetme çıktısı](media/debugger-logging-output.png)

1. Visual Studio askıda ysa veya **Çıktı** penceresine erişemezseniz, Visual Studio'yu yeniden başlatın, bir komut penceresini açın ve aşağıdaki komutu girin:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Hata ayıklamaya başlayın ve sorununuzu yeniden çoğaltın. Hata ayıklama günlükleri daha sonra `%temp%\DebugAdapterHostLog.txt`.

## <a name="see-also"></a>Ayrıca bkz.

Visual Studio hata ayıklama hakkında tüm ayrıntılar için Visual [Studio'da Hata Ayıklama](../debugger/debugger-feature-tour.md)bölümüne bakın.
