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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156636"
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

| Özellik | U | Açıklama |
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

Her bir özel durum için onay kutusu *, hata ayıklayıcının ne zaman harekete* geçirilip bölünemediğini denetler. Belirli bir özel durum için daha sık kesme yapmak istediğinizde bu kutuyu işaretleyin.

Varsayılan olarak, bir özel durum işleyicisi kaynak kodda bulunamazsa çoğu özel durum bozabilir. Bu davranışı değiştirmek için herhangi bir özel duruma sağ tıklayın ve Kullanıcı Kodunda **İşlenilen Durumda Devam'ı** seçin. Bir özel durum için daha az sıklıkta kesme yapmak istediğiniz zaman bu kutuyu temizleyin.

Bu listede görünmeen bir özel durum yapılandırmak için Ekle **düğmesine** tıklayarak ekleyin. Ad, özel durumun tam adıyla eşleşmeli.

## <a name="project-debugging-options"></a>Project ayıklama seçenekleri

Varsayılan olarak, hata ayıklayıcı programınızı standart Python başlatıcısı, komut satırı bağımsız değişkeni ve başka özel yol veya koşullar ile başlatır. Başlangıç seçenekleri, projesinde projenize sağ tıklar, Özellikler **'i** seçerek ve Çözüm Gezgini Hata ayıkla sekmesini seçerek projenin hata ayıklama **özellikleriyle** değiştirilir.

![Project hata ayıklayıcısında Visual Studio ayıklama özellikleri](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Başlatma modu seçenekleri

| Seçenek | Açıklama |
| --- | --- |
| **Standart Python başlatıcısı** | CPython, IronPython ve Stackless Python gibi çeşitlemelerle uyumlu taşınabilir Python'da yazılmış hata ayıklama kodunu kullanır. Saf Python kodunda hata ayıklamak için en iyi deneyimi sağlar. Çalışan bir uygulama işlem *python.exe,* bu başlatıcı kullanılır. Bu başlatıcı ayrıca [CPython](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) için karma mod hata ayıklaması sağlayarak C/C++ kodu ile Python kodu arasında sorunsuz bir şekilde adım çalışmanıza olanak sağlar. |
| **Web başlatıcısı** | Başlatma sırasında varsayılan tarayıcınızı başlatır ve şablonların hata ayıklamasını sağlar. Daha fazla [bilgi için Web şablonu](python-web-application-project-templates.md#debugging) hata ayıklama bölümüne bakın. |
| **Django Web başlatıcısı** | Web başlatıcısı ile aynıdır ve yalnızca geriye dönük uyumluluk için gösterilir. |
| **IronPython (.NET) başlatıcısı** | Yalnızca IronPython ile çalışan ancak C# ve VB dahil olmak üzere herhangi bir .NET dil projesi arasında adımlama sağlayan .NET hata ayıklayıcısını kullanır. Bu başlatıcı, IronPython'un barındırıcısı olan çalışan bir .NET sürecine iliştirmek için kullanılır. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Çalıştırma seçenekleri (arama yolları, başlangıç bağımsız değişkenleri ve ortam değişkenleri)

| Seçenek | Açıklama |
| --- | --- |
| **Arama Yolları** | Bu değerler, projedeki arama yolları düğümünde **gösterilenlerle Çözüm Gezgini.**  Bu değeri burada değiştirebilirsiniz, ancak klasörlere göz **atmanıza ve yolları Çözüm Gezgini** göre biçime otomatik olarak dönüştürmenize olanak sağlayan bir dosya adı kullanmak daha kolaydır. |
| **Betik Bağımsız Değişkenleri** | Bu bağımsız değişkenler, betiğinizi başlatmak için kullanılan komuta eklenir ve betiğinizin dosya adı sonrasında görünür. Buradaki ilk öğe betiğiniz için `sys.argv[1]` olarak, ikinci öğe olarak kullanılabilir `sys.argv[2]` ve bu şekilde devam etti. |
| **Yorumlayıcı Bağımsız Değişkenleri** | Bu bağımsız değişkenler, betiğinizin adının önünde başlatıcı komut satırına eklenir. Buradaki yaygın bağımsız değişkenler uyarıları kontrol etmek, programınızı biraz iyileştirmek ve bağımsız olmayan bir `-W ...` `-O` `-u` IO kullanmaktır. IronPython kullanıcıları, veya gibi seçenekleri geçmek için `-X` büyük olasılıkla bu alanı `-X:Frames` `-X:MTA` kullanır. |
| **Yorumlayıcı Yolu** | Geçerli ortamla ilişkili yolu geçersiz kılar. Değeri, betiğinizi standart olmayan bir yorumlayıcıyla başlatmak için yararlı olabilir. |
| **Ortam Değişkenleri** | Bu çok satırlı metin kutusuna formun girdilerini \<NAME> = \<VALUE> ekleyin. Bu ayar en son uygulandığı için, mevcut genel ortam değişkenlerinin üzerine uygulanır ve sonra Arama Yolları ayarına göre ayarlanırsa, bu diğer değişkenlerden herhangi birini el ile geçersiz `PYTHONPATH` kılmak için kullanılabilir.  |

## <a name="immediate-and-interactive-windows"></a>Anlık ve Etkileşimli pencereler

Hata ayıklama oturumu sırasında kullanabileceğiniz iki etkileşimli pencere vardır: standart Visual Studio **Penceresi** ve **Python Hata** Ayıklama Etkileşimli penceresi.

Hemen **penceresi** (**Hata ayıklama** Windows Anında), Python ifadelerinin hızlı değerlendirilmesi ve çalışan program içindeki değişkenlerin incelemesi veya  >    >  ataması için kullanılır. Ayrıntılar için [genel Anında pencere](../ide/reference/immediate-window.md) makalesine bakın.

Python **Hata Ayıklama Etkileşimli** penceresi ( Hata Ayıklama Windows Python Hata Ayıklama Etkileşimli ), kod yazma ve çalıştırma dahil olmak üzere hata ayıklama sırasında tam EtkileşimliREPL deneyimini kullanılabilir yapan daha  >    >  zengindir. [](python-interactive-repl-in-visual-studio.md) Standart Python başlatıcısını kullanarak hata ayıklayıcıda başlatan işlemlere otomatik olarak bağlanır (İşleme Hata Ayıklama  >  **İliştir aracılığıyla eklenen işlemler de dahil).** Ancak karma mod C/C++ hata ayıklaması kullanırken kullanılamaz.

![Python Hata Ayıklama Etkileşimli penceresi](media/debugging-interactive.png)

Etkileşimli **Hata Ayıklama penceresi,** standart REPL komutlarının yanı sıra özel [meta komutlarını da destekler:](python-interactive-repl-in-visual-studio.md#meta-commands)

| Komut | Bağımsız değişkenler | Açıklama |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Programı geçerli deyiminden çalıştırmaya başlar. |
| `$down`, `$d` | Geçerli çerçeveyi yığın izlemesinde bir düzey aşağı taşıma. |
| `$frame` | | Geçerli çerçeve kimliğini görüntüler.
| `$frame` | çerçeve kimliği | Geçerli kareyi belirtilen çerçeve kimliğine geçiştir.
| `$load` | Dosyadan komutları yükler ve tamamlayana kadar yürütülür |
| `$proc` |  | Geçerli işlem kimliğini görüntüler. |
| `$proc` | işlem kimliği | Geçerli işlemi belirtilen işlem kimliğine geçiştir. |
| `$procs` | | Şu anda hata ayıklama işlemi yapılan işlemleri listeler. |
| `$stepin`, `$step`, `$s` | Mümkünse sonraki işlev çağrısına adım adım gösterir. |
| `$stepout`, `$return`, `$r` | Geçerli işlevin dışında adımlar. |
| `$stepover`, `$until`, `$unt` | Sonraki işlev çağrısının adımları. |
| `$thread` | | Geçerli iş parçacığı kimliğini görüntüler. |
| `$thread` | iş parçacığı kimliği | Geçerli iş parçacığını belirtilen iş parçacığı kimliğine geçiştir. |
| `$threads` | | Şu anda hata ayıklaması yapılan iş parçacıklarını listeler. |
| `$up`, `$u` | | Geçerli çerçeveyi yığın izlemesinde bir düzey yukarı taşı. |
| `$where`, `$w`, `$bt` | Geçerli iş parçacığı için çerçeveleri listeler. |

İşlemler, İş Parçacıkları ve Çağrı Yığını gibi  standart hata ayıklayıcı pencerelerini Etkileşimli Hata Ayıklama **penceresiyle eşitlenmez.**  Etkileşimli Hata Ayıklama penceresinde etkin işlemi, iş **parçacığını** veya çerçeveyi değiştirmek diğer hata ayıklayıcı pencerelerini etkilemez. Benzer şekilde, diğer hata ayıklayıcı pencerelerinde etkin işlemi, iş parçacığını veya çerçeveyi değiştirmek Etkileşimli Hata Ayıklama **penceresini etkilemez.**

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Eski hata ayıklayıcısını kullanma

Visual Studio 2017 sürüm 15.8 ve sonrası ptvsd sürüm 4.1+ tabanlı bir hata ayıklayıcı kullanır. Visual Studio 2019 sürüm 16.5 ve sonrası, hata ayıklamayı temel alan bir hata ayıklayıcı kullanır. Hata ayıklayıcının bu sürümleri Python 2.7 ve Python 3.5+ ile uyumludur. Python 2.6, 3.1 ile 3.4 veya IronPython kullanıyorsanız Visual Studio hata gösterir, Hata Ayıklayıcı **şu Python ortamını desteklemez:**

![Hata ayıklayıcısı, hata ayıklayıcıyı kullanırken bu Python ortamı hatasını desteklemez](media/debugging-experimental-incompatible-error.png)

Bu durumlarda eski hata ayıklayıcısını (2017 sürüm 15.7 ve Visual Studio varsayılandır) kullan gerekir. Araçlar Seçenekler **menü**  >  **komutunu** seçin, Python Hata **Ayıklama'ya** gidin ve Eski hata  >   **ayıklayıcıyı kullan seçeneğini** belirleyin.

Geçerli ortama ptvsd'nin eski bir sürümünü yüklemiş (örneğin, önceki bir 4.0.x sürümü veya uzaktan hata ayıklama için gereken 3.x sürümü) Visual Studio bir hata veya uyarı gösterebilir.

Hata: **Ptvsd** 3.x'i yüklemişken Hata ayıklayıcısı paketi yüklenemedi:

![Hata ayıklayıcı kullanırken hata ayıklayıcı paketi yüklenemedi hatası](media/debugging-experimental-version-error.png)

Bu durumda Eski hata **ayıklayıcıyı kullan'ı seçerek** Eski hata ayıklayıcıyı **kullan** seçeneğini belirleyin ve hata ayıklayıcıyı yeniden başlatın.

Ptvsd'nin **önceki** 4.x sürümünü yüklemişken Hata ayıklayıcı paketi güncel değil uyarısı görüntülenir:

![Hata ayıklayıcı kullanırken hata ayıklayıcı paketinde zamandıldı uyarısı](media/debugging-experimental-version-warning.png)

> [!Important]
> Bazı ptvsd sürümleri için uyarıyı yoksayabilirsiniz ancak Visual Studio düzgün çalışmayabilir.

Ptvsd yüklemenizi yönetmek için:

1. Python Ortamları **penceresinde** Paketler **sekmesine** gidin.

1. Arama kutusuna "ptvsd" yazın ve ptvsd'nin yüklü sürümünü inceler:

    ![Python Ortamları penceresinde ptvsd sürümünü denetleme](media/debugging-experimental-check-ptvsd.png)

1. Sürüm 4.1.1a9'dan küçükse (Visual Studio ile paketlenmiş sürüm), eski sürümü kaldırmak için paketin sağ **köşesindeki X'i** seçin. Visual Studio paket sürümünü kullanır. (Ayrıca kullanarak PowerShell'den `pip uninstall ptvsd` kaldırabilirsiniz.)

1. Alternatif olarak, Sorun Giderme bölümündeki yönergeleri izleyerek ptvsd paketini en yeni sürümüne [güncelleştirebilirsiniz.](#troubleshooting)

## <a name="troubleshooting"></a>Sorun giderme

### <a name="for-visual-studio-2019-version-164-and-earlier-upgrade-ptvsd"></a>2019 Visual Studio (Sürüm 16.4 ve önceki sürümler) ptvsd'ye yükseltme
Hata ayıklayıcısıyla ilgili sorunlarınız varsa, önce hata ayıklayıcı sürümünü aşağıdaki gibi yükseltin:

1. Python Ortamları **penceresinde** Paketler **sekmesine** gidin.

1. Arama `ptvsd --upgrade` kutusuna yazın ve çalıştır komutu: pip install **ptvsd --upgrade öğesini seçin.** (Aynı komutu PowerShell'den de kullanabilirsiniz.)

    ![Python Ortamları penceresinde ptvsd upgrade komutu verme](media/debugging-experimental-upgrade-ptvsd.png)

   Sorunlar devam ederse lütfen PTVS depolama deposunda [GitHub kaydedin.](https://github.com/Microsoft/ptvs/issues)

   > [!NOTE]
   > 2019 Visual Studio 16.5 ve sonraki sürümler için hata ayıklama, Visual Studio Python iş yükünün bir parçası ve Visual Studio.

### <a name="enable-debugger-logging"></a>Hata ayıklayıcı günlüğünü etkinleştirme

Bir hata ayıklayıcı sorunu araştırırken, Microsoft tanılamaya yardımcı olan hata ayıklayıcı günlüklerini etkinleştirmenizi ve toplamayı sorabilir.

Aşağıdaki adımlar geçerli oturumda hata ayıklamayı Visual Studio sağlar:

1. Komut Penceresi menü Visual Studio **kullanarak** Windows  >    >  **penceresinde bir** komut penceresi açın.

1. Aşağıdaki komutu girin:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Hata ayıklamaya başlama ve sorunlarınızı yeniden oluşturmak için gereken adımların üzerinden geçebilirsiniz. Bu süre boyunca hata ayıklama günlükleri, Hata Ayıklama Bağdaştırıcısı Ana **Bilgisayar** Günlüğü altındaki **Çıkış penceresinde görüntülenir.** Ardından bu pencereden günlükleri kopyalayıp bir sorun, e-posta GitHub yapıştırabilirsiniz.

    ![Çıkış penceresinde hata ayıklayıcı günlüğü çıkışı](media/debugger-logging-output.png)

1. Yanıt Visual Studio veya Çıkış penceresine erişemiyorsanız,  Visual Studio yeniden başlatın, bir komut penceresi açın ve aşağıdaki komutu girin:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Hata ayıklamaya başlama ve sorunlarınızı yeniden oluşturma. Hata ayıklayıcı günlükleri daha sonra içinde `%temp%\DebugAdapterHostLog.txt` bulunabilir.

## <a name="see-also"></a>Ayrıca bkz.

Hata ayıklayıcısıyla ilgili tüm Visual Studio için [bkz.](../debugger/debugger-feature-tour.md)Visual Studio.
