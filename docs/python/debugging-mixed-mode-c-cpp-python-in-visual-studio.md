---
title: Python için karma mod hata ayıklama
description: Ortamlar arasında adımlama, değerleri görüntüleme ve ifadeleri Visual Studio C++ ve Python'da aynı anda hata ayıklama.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a93abff7aa65e61830065c3217fb0fb4b37bd93a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637017"
---
# <a name="debug-python-and-c-together"></a>Python ve C++ ile birlikte hata ayıklama

Çoğu normal Python hata ayıklayıcısı yalnızca Python kodunda hata ayıklamayı destekler. Ancak uygulamada Python, yüksek performans gerektiren veya platform API'lerini doğrudan çağıran senaryolarda C veya C++ ile birlikte kullanılır. (Kılavuz [için bkz. Python için C++](working-with-c-cpp-python-in-visual-studio.md) uzantısı oluşturma.)

Visual Studio yükleyicisinde Python Geliştirme iş yükü için **Python** yerel geliştirme araçları seçeneğini seçmeniz şartıyla, Python ve  yerel C/C++ için tümleşik, eşzamanlı karma mod hata ayıklaması Visual Studio sağlar.

> [!Note]
> 2015 ve önceki sürümlerde Visual Studio için Python Araçları 1.x ile Visual Studio mod hata ayıklaması kullanılamaz.

Karma mod hata ayıklama özellikleri, bu makalede açıklanmıştır:

- Birleştirilmiş çağrı yığınları
- Python ile yerel kod arasında adım adım
- Her iki kod türünde de kesme noktaları
- Bkz. Yerel karelerde nesnelerin Python gösterimleri ve tam tersi
- Python projesi veya C++ projesi bağlamında hata ayıklama

![Visual Studio'de Python için karışık mod hata ayıklaması](media/mixed-mode-debugging.png)

![video için film kamerası simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") Visual Studio ile yerel C modülleri oluşturma, test etme ve hata ayıklamaya giriş için bkz. Ayrıntılı [Giriş:](https://youtu.be/D9RlT06a1EI) Yerel Modüller Oluşturma (youtube.com, 9m 09'lar). Video hem 2015 hem Visual Studio 2017 için geçerlidir.


## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Python projesinde karma mod hata ayıklamayı etkinleştirme

1. **Çözüm Gezgini'da** Python projesine sağ tıklayın, Özellikler'i  **seçin,** Hata Ayıkla sekmesini seçin ve ardından Yerel **kodda hata ayıklamayı etkinleştir'i seçin.** Bu seçenek tüm hata ayıklama oturumları için karma modu sağlar.

    ![Yerel kodda hata ayıklamayı etkinleştirme](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Yerel kodda hata ayıklamayı etkinleştirerek program tamamlandıktan hemen sonra duraklatma devam etmek için herhangi bir tuşa bas'ı vermeden Python çıkış **penceresi kaybolabilir.** Duraklatma zorlamak için, yerel kodda hata ayıklamayı etkinleştirirken Hata Ayıklama sekmesindeki Yorumlayıcı `-i`   >   Bağımsız Değişkenlerini Çalıştır alanına seçeneğini ekleyin.  Bu bağımsız değişken, kod tamamlandikten sonra Python yorumlayıcıyı etkileşimli moda koyar. Bu noktada çıkış yapmak için **Ctrl** + **Z**  >  **Enter tuşuna basabilirsiniz.**

1. Karma mod hata ayıklayıcısını mevcut bir işleme **(** İşleme Eklemede Hata Ayıkla) iliştirme sırasında, Kod Türünü Seç iletişim kutusunu açmak için Seç  >   **düğmesini** kullanın.  Ardından Bu kod **türlerinde hata ayıkla seçeneğini** ayarlayın ve listeden **hem Yerel** hem **de Python'ı** seçin:

    ![Yerel ve Python kod türlerini seçme](media/mixed-mode-debugging-code-type.png)

    Kod türü ayarları kalıcıdır, bu nedenle daha sonra farklı bir işleme iliştirme sırasında karma mod hata ayıklamayı devre dışı bırakmak için **Python** kod türünü temizlemeniz gerekir.

    Yerel 'e ek olarak veya bunun yerine diğer kod türlerini de **seçmek mümkündür.** Örneğin, yönetilen bir uygulama CPython'u barındırıyorsa ve bu modüllerde yerel uzantı modülleri kullanıyorsa ve üçünün de hata ayıklamasını yapmak için birleştirilmiş çağrı yığınları ve üç çalışma zamanı arasında adımlama da dahil olmak üzere birleşik bir hata ayıklama deneyimi için **Python,** Yerel **ve** Yönetilen'i birlikte kontrol edebilirsiniz. 

1. Hata ayıklamaya karma modda ilk kez başlarken Python  Sembolleri Gerekli iletişim kutusuyla karşılaşabilirsiniz (bkz. Karma mod hata ayıklaması [için semboller).](debugging-symbols-for-mixed-mode-c-cpp-python.md) Herhangi bir Python ortamı için sembolleri yalnızca bir kez yüklemeniz gerekir. Python desteğini Visual Studio yükleyicisi (Visual Studio 2017 ve sonraki sürümler) aracılığıyla yükleyebiliyorsanız semboller otomatik olarak eklenir.

1. Hata ayıklama sırasında standart Python'ın kaynak kodunu kullanılabilir yapmak için, ziyaret edin, sürümünüz için uygun arşivi indirin [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/) ve bir klasöre ayıklar. Daha sonra Visual Studio klasördeki belirli dosyalara, sizden hangi noktada istendiğinde işaret edin.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>C/C++ projesinde karma mod hata ayıklamayı etkinleştirme

Visual Studio (2017 sürüm 15.5 ve sonrası), bir C/C++ projesinden karma mod hata ayıklamayı destekler (örneğin, Python'ı python.org'da açıklandığı gibi başka bir uygulamaya [ekleme).](https://docs.python.org/3/extending/embedding.html) Karışık mod hata ayıklamayı etkinleştirmek için C/C++ projesini **Python/Yerel Hata Ayıklamayı başlatarak yapılandırma:**

1. Içinde C/C++ projesine sağ **tıklayın ve Çözüm Gezgini'ı** **seçin.**
1. Hata Ayıklama **sekmesini seçin,** başlatmak için **Hata Ayıklayıcısından Python/Yerel** Hata **Ayıklama'ya tıklayın ve** Tamam'ı **seçin.**

    ![C/C++ projesinde Python/Yerel hata ayıklayıcısını seçme](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> **Python/Yerel** Hata Ayıklama seçeneğiniz yoksa, önce VS yükleyicisini kullanarak Python yerel **geliştirme araçlarını** yüklemeniz gerekir. Bunu Python geliştirme iş yükünün altında bir seçenek olarak bulabilirsiniz. Daha fazla bilgi için [bkz. Python desteğini Visual Studio'de Windows.](installing-python-support-in-visual-studio.md)

Bu yöntemi kullanarak, hata ayıklayıcının eklipy.exebir altpython.exeişlemi ortaya  çıktısı nedeniyle bu başlatıcının kendisinde hata ayıklayamayabilirsiniz.  *python.exe'i* doğrudan bağımsız değişkenlerle başlatmak için **Python/Yerel** Hata Ayıklama özelliklerinde Komut seçeneğini (önceki görüntüde gösterilmiştir) *değiştirerekpython.exe* yolunun tamamını belirtin ve ardından Komut Bağımsız Değişkenleri'ne bağımsız değişkenleri **belirtin.** 

### <a name="attaching-the-mixed-mode-debugger"></a>Karma mod hata ayıklayıcısını ekleme

C/C++ Visual Studio yalnızca yerel hata ayıklayıcıyı kullanmasından dolayı, önceki tüm Visual Studio sürümlerinde doğrudan karma mod hata ayıklaması yalnızca Visual Studio'de bir Python projesi başlatılırken etkinleştirilir. Ancak hata ayıklayıcıyı ayrı olarak iliştirebilirsiniz:

1. Hata ayıklama olmadan C++ projesini başlatma (**Hata Ayıklama** Olmadan Başlat veya  >   **Ctrl** + **F5**) .
1. İşleme **Eklemede**  >  **Hata Ayıkla'ya seçin.** Görüntülenen iletişim kutusunda uygun işlemi seçin ve  ardından Seç düğmesini  kullanarak Python'ı seçerek Kod Türünü Seç iletişim kutusunu **açın:**

    ![Hata ayıklayıcı ekleme sırasında hata ayıklama türü olarak Python'ı seçme](media/mixed-mode-debugging-attach-type.png)

1. **Tamam'ı** seçerek bu iletişim kutusunu kapatın ve ardından **Ekle'yi** seçerek hata ayıklayıcıyı açın.
1. Hata ayıklayıcıyı ekleme fırsatınız olmadan önce hata ayıklamak istediğiniz Python kodunu çağırmaması için C++ uygulamasında uygun bir duraklatma veya gecikmeye neden olması gerekir.

## <a name="mixed-mode-specific-features"></a>Karma moda özgü özellikler

- [Birleştirilmiş çağrı yığını](#combined-call-stack)
- [Python ile yerel kod arasında adım adım](#step-between-python-and-native-code)
- [Yerel kodda PyObject değerleri görünümü](#pyobject-values-view-in-native-code)
- [Python kodunda yerel değerler görünümü](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Birleştirilmiş çağrı yığını

Çağrı **Yığını penceresinde** hem yerel hem de Python yığın çerçeveleri araya ve ikisi arasında işaretlenen geçişler gösterilir:

![Karışık mod hata ayıklama ile birleştirilmiş çağrı yığını](media/mixed-mode-debugging-call-stack.png)

Geçişler, Araç Seçenekleri Hata Ayıklama Genel Olarak Etkinleştir seçeneği ayarlanmışsa, geçiş yönünü belirtmeden   >    >    >    >  **[Dış Kod] Yalnızca kendi kodum** görünür.

Herhangi bir çağrı çerçevesine çift tıklarsanız etkin olur ve mümkünse uygun kaynak kodu açılır. Kaynak kodu kullanılamıyorsa, çerçeve hala etkin yapılır ve yerel değişkenler inceleyebilirsiniz.

### <a name="step-between-python-and-native-code"></a>Python ile yerel kod arasında adım adım

**Step Into** (**F11**) veya **Step Out** (**Shift** + **F11**) komutlarını kullanırken, karma mod hata ayıklayıcısı kod türleri arasındaki değişiklikleri doğru şekilde işler. Örneğin, Python C'de uygulanan bir yöntem yöntemini çağırsa, bu yönteme yapılan bir çağrıda adımlama, yöntemini uygulayan yerel işlevin başında durur. Benzer şekilde, yerel kod bazı Python API işlevlerini çağırarak Python kodunun çağrılarak sonuç verir. Örneğin, Python'da ilk olarak tanımlanan bir işlev değerine `PyObject_CallObject` adımlama, Python işlevinin başında durur. Python'dan yerele adımlama, ctype'lar aracılığıyla Python'dan çağrılan yerel [işlevler için de de kullanılabilir.](https://docs.python.org/3/library/ctypes.html)

### <a name="pyobject-values-view-in-native-code"></a>Yerel kodda PyObject değerleri görünümü

Yerel (C veya C++) bir çerçeve etkin olduğunda, yerel değişkenleri hata ayıklayıcı **YerelLeri penceresinde** görünür. Yerel Python uzantısı modüllerinde, bu değişkenlerin çoğu `PyObject` türündedir (için bir typedeftir) veya birkaç temel Python türü `_object` (aşağıdaki listeye bakın). Karma mod hata ayıklamada, bu değerler **[Python görünümü]** etiketli ek bir alt düğüm gösterir. Bu düğüm genişletilirken değişkenin Python gösterimini gösterir. Aynı nesneye başvuran yerel bir değişkenin Python çerçevesinde mevcut olmasıyla aynı durumla aynıdır. Bu düğümün altları düzenlenebilir.

![YerelLer penceresinde Python Görünümü](media/mixed-mode-debugging-python-view.png)

Bu özelliği devre dışı bırakmak için  YerelLer penceresinde herhangi bir yere sağ tıklayın ve **Python Python**  >  **Görünüm Düğümlerini Göster menü seçeneğini** açın:

![YerelLer penceresinde Python Görünümünü etkinleştirme](media/mixed-mode-debugging-enable-python-view.png)

**[Python görünümü] düğümlerini** (etkinleştirildiyse) içeren C türleri:

- `PyObject`
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

**[Python görünümü]** kendi yazmanız için otomatik olarak görünmez. Python 3.x için uzantılar yazarken bu eksiklik genellikle sorun oluşturmaz çünkü herhangi bir nesne sonunda yukarıdaki türlerden birini içeren bir alana sahiptir ve `ob_base` **bu da [Python görünümü]** görünümünün görünmesine neden olur.

Ancak Python 2.x için her nesne türü genellikle üst bilgisini satır içi alan koleksiyonu olarak bildirmektedir ve C/C++ kodunda özel olarak yazılmış türler ile tür sistemi düzeyi arasında bir ilişki `PyObject` yoktur. Bu tür özel türlerde **[Python görünümü]** düğümlerini etkinleştirmek için [Python](installing-python-support-in-visual-studio.md#install-locations)araçları yükleme dizinindeki *PythonDkm.natvis* dosyasını düzenleyin ve C yapınız veya C++ sınıfınız için XML'de başka bir öğe ekleyin.

Alternatif (ve daha iyi) [seçenek, PEP 3123'ü](https://www.python.org/dev/peps/pep-3123/) takip etmek ve yerine açık bir alan kullanmaktır, ancak bu her zaman geriye dönük uyumluluk nedenleriyle `PyObject ob_base;` `PyObject_HEAD` mümkün olmayacaktır.

### <a name="native-values-view-in-python-code"></a>Python kodunda yerel değerler görünümü

Önceki bölüme benzer şekilde, Bir Python çerçevesi etkin olduğunda  Yereller penceresinde yerel değerler için **[C++ görünümü]** etkinleştirebilirsiniz. Bu özellik varsayılan olarak etkin değildir, bu nedenle Yereller  penceresine sağ tıklar ve **Python** Show C++ Görünüm Düğümleri menü  >   seçeneğini kapatarak özelliği açarsınız.

![YerelLer penceresinde C++ Görünümünü etkinleştirme](media/mixed-mode-debugging-enable-cpp-view.png)

**[C++ görünümü]** düğümü, bir değer için temel alınan C/C++ yapısının bir gösterimini sağlar ve yerel çerçevede gördüğünüzle aynıdır. Örneğin, Uzun Python tamsayısı için bir `_longobject` örneği (typedef) gösterir ve kendi yazmış olduğunuz yerel sınıflar için türleri çıkarım `PyLongObject` yapmaya çalışır. Bu düğümün altları düzenlenebilir.

![YerelLer penceresinde C++ Görünümü](media/mixed-mode-debugging-cpp-view.png)

Bir nesnenin alt alanı türünde veya desteklenen diğer türlerden biri `PyObject` ise, **[Python görünümü]** gösterim düğümüne sahiptir (bu gösterimler etkinleştirilirse), bağlantıların doğrudan Python'a açık olduğu nesne grafiklerinde gezinmeyi mümkün hale gelir.

Nesnenin türünü belirlemek için Python nesne meta verilerini kullanan **[Python görünümü]** düğümlerinin aksine, **[C++ görünümü]** için benzer şekilde güvenilir bir mekanizma yoktur. Genel olarak, bir Python değeri (yani başvuru) verilse, hangi C/C++ yapısının onu destekleyeni güvenilir `PyObject` bir şekilde belirlemek mümkün değildir. Karma mod hata ayıklayıcısı, nesne türünün çeşitli alanlarına (örneğin, alanı tarafından başvurulan) işlev işaretçisi türlerine bakarak bu `PyTypeObject` `ob_type` türü tahmin etmeye çalışır. Bu işlev işaretçilerinden biri çözümlenebilir bir işleve başvurursa ve bu işlevin türünden daha özel olan bir parametresi varsa bu tür, destek türü `self` `PyObject*` olarak kabul edilir. Örneğin, `ob_type->tp_init` belirli bir nesne aşağıdaki işlev gösteriyorsa:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

ardından, hata ayıklayıcı nesnenin C türünün olduğunu doğru şekilde belirleyebilir `FobObject` . ' Den daha kesin bir tür belirleyeleyemiyorsa `tp_init` , diğer alanlara gider. Bu alanlardan herhangi birinden türü çıkarılamıyor, **[C++ View]** düğümü nesneyi bir örnek olarak gösterir `PyObject` .

Özel olarak yazılan türler için her zaman yararlı bir gösterim sağlamak üzere, türü kaydederken en az bir özel işlevi kaydetmek ve kesin belirlenmiş bir parametre kullanmak en iyisidir `self` . Çoğu tür, bu gereksinimi doğal olarak karşılar; Böyle bir durum söz konusu değilse, `tp_init` genellikle bu amaçla kullanmak için en kullanışlı girdidir. `tp_init`Yalnızca hata ayıklayıcı tür çıkarımı sağlamak için mevcut olan bir tür için tam bir uygulama, yukarıdaki kod örneğinde olduğu gibi hemen sıfır döndürebilir.

## <a name="differences-from-standard-python-debugging"></a>Standart Python hata ayıklamasının farkları

Karışık modda hata ayıklayıcı, bazı ek özellikler sunmakta ancak Python ile ilgili bazı özelliklere sahip olmayan [Standart Python hata ayıklayıcısından](debugging-python-in-visual-studio.md) farklıdır:

- Desteklenmeyen özellikler: koşullu kesme noktaları, **hata ayıklama etkileşimli** penceresi ve platformlar arası uzaktan hata ayıklama.
- **Komut** penceresi: burada listelenen tüm sınırlamalar dahil olmak üzere, işlevlerinin sınırlı bir alt kümesiyle birlikte kullanılabilir.
- Desteklenen Python sürümleri: CPython 2,7 ve 3.3 + yalnızca.
- Visual Studio Shell: Visual Studio shell ile Python kullanılırken (örneğin, tümleşik yükleyiciyi kullanarak yüklediyseniz), Visual Studio c++ projelerini açamaz ve c++ dosyaları için düzenleme deneyimi yalnızca temel bir metin düzenleyicidir. Ancak, C/C++ hata ayıklama ve karışık modda hata ayıklama, kaynak kodu ile kabukta tam olarak desteklenir, yerel koda adımlanıyor ve hata ayıklayıcı Windows 'ta C++ ifade değerlendirmesi.
- Nesneleri görüntüleme ve genişletme: **Yereller** halinde Python nesnelerini görüntülerken ve hata ayıklayıcı araç pencerelerini **izlerken** , karışık modda hata ayıklayıcı yalnızca nesnelerin yapısını gösterir. Özellikleri otomatik olarak değerlendirmez veya hesaplanan öznitelikleri göstermez. Koleksiyonlar için yalnızca yerleşik koleksiyon türleri ( `tuple` , `list` , `dict` ,) için öğeleri gösterir `set` . Özel koleksiyon türleri, bazı yerleşik koleksiyon türünden devralınmadıkları sürece koleksiyonlar olarak görselleştirimez.
- İfade değerlendirmesi: aşağıya bakın.

### <a name="expression-evaluation"></a>İfade değerlendirmesi

Standart Python hata ayıklayıcı, bir g/ç işleminde veya başka benzer sistem çağrısında engellenmediği sürece, hata ayıklanan işlem kodda herhangi bir noktada duraklatıldığında, **izleme** ve **anında** Windows 'da rastgele Python ifadelerinin değerlendirilmesine olanak tanır. Karma mod hata ayıklamada, rastgele ifadeler yalnızca Python kodunda durdurulduğunda, bir kesme noktasından sonra veya koda adımlarken değerlendirilebilirler. İfadeler yalnızca kesme noktasının veya Adımlama işleminin gerçekleştiği iş parçacığında değerlendirilebilir.

Yerel kodda durdurulduğunda veya yukarıdaki koşulların uygulanmamakta olduğu Python kodunda (örneğin, bir adım dışı işlemden sonra veya farklı bir iş parçacığında), ifade değerlendirmesi, şu anda seçili olan çerçevenin kapsamındaki yerel ve genel değişkenlere erişim, alanlarına erişme ve yerleşik koleksiyon türlerini değişmez değerler ile dizin oluşturma ile sınırlıdır. Örneğin, aşağıdaki ifade herhangi bir bağlamda değerlendirilebilir (tüm tanımlayıcıların mevcut değişkenlere ve uygun türdeki alanlara başvurabileceği belirtildi):

```python
foo.bar[0].baz['key']
```

Karma mod hata ayıklayıcı Ayrıca bu tür ifadeleri farklı çözümler. Tüm üye erişim işlemleri, yalnızca nesnenin bir parçası olan (veya içindeki bir giriş `__dict__` `__slots__` ya da Python ile Python 'un açığa çıkarılan yerel bir yapının alanı `tp_members` ) ve herhangi bir `__getattr__` `__getattribute__` veya tanımlayıcı mantığını yok sayan alanlara bakar. Benzer şekilde, tüm dizin oluşturma işlemleri `__getitem__` , koleksiyonların iç veri yapılarına doğrudan göz ardı eder ve erişir.

Tutarlılık açısından, bu ad çözümleme şeması, geçerli durma noktasında rastgele ifadelere izin verilip verilmeyeceğini fark etmeksizin sınırlı ifade değerlendirmesi için kısıtlamalarla eşleşen tüm ifadeler için kullanılır. Tam özellikli bir değerlendirici kullanılabilir olduğunda doğru Python semantiğini zorlamak için, ifadeyi parantez içine alın:

```python
(foo.bar[0].baz['key'])
```
