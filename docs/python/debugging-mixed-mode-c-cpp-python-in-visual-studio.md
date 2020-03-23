---
title: Python için karışık mod hata ayıklama
description: Aynı anda Ortamlar arasında adım atma, değerleri görüntüleme ve ifadeleri değerlendirme dahil olmak üzere Visual Studio'da C++ ve Python hata ayıklama.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bc90d659a32c14f92e1eff058dd22d4a17d0b1cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75679006"
---
# <a name="debug-python-and-c-together"></a>Hata Ayıklama Python ve C++ birlikte

En düzenli Python hata ayıklayıcıları yalnızca Python kodunun hata ayıklama destekler. Ancak uygulamada Python, yüksek performans gerektiren senaryolarda veya platform API'lerini doğrudan çağırabilme yeteneğinde C veya C++ ile birlikte kullanılır. (Bkz. Bir gözden geçirme için [Python için C++ uzantısı oluştur.)](working-with-c-cpp-python-in-visual-studio.md)

Visual Studio, Visual Studio yükleyicisinde **Python Geliştirme** iş yükü için Python yerel **geliştirme araçları** seçeneğini seçmeniz koşuluyla, Python ve yerel C/C++ için entegre, eşzamanlı karma mod hata ayıklama sağlar.

> [!Note]
> Visual Studio 2015 ve öncesi yıllarda Visual Studio 1.x için Python Tools ile karma modlu hata ayıklama kullanılamaz.

Karışık mod hata ayıklama özellikleri, bu makalede açıklandığı gibi şunlardır:

- Birleşik çağrı yığınları
- Python ve yerel kod arasındaki adım
- Her iki kod türünde de kesme noktaları
- Bkz. Nesnelerin yerel çerçevelerde Python gösterimleri ve tam tersi
- Python projesi veya C++ projesi bağlamında hata ayıklama

![Visual Studio'da Python için karışık mod hata ayıklama](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![video için film kamera simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") | Visual Studio ile yerel C modüllerinin oluşturulması, test edilmesi ve hata ayıklanmasına giriş için [Deep Dive: Create Native Modules](https://youtu.be/D9RlT06a1EI) (youtube.com, 9m 09s) bölümüne bakın. Video visual studio 2015 ve 2017 için geçerlidir. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Python projesinde karışık mod hata ayıklamayı etkinleştirme

1. **Solution Explorer'da**Python projesine sağ tıklayın, **Özellikler'i**seçin, **Hata Ayıklama** sekmesini seçin ve ardından **yerel kodu hata ayıklama özelliğini etkinleştir'i**seçin. Bu seçenek, tüm hata ayıklama oturumları için karışık mod sağlar.

    ![Yerel kod hata ayıklama etkinleştirme](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Yerel kod hata ayıklamaetkinleştirdiğinizde, Python çıkış penceresi, program tamamlandığında size her zamanki **basın tuşunu** vermeden duraklatmaya devam etmek için hemen kaybolabilir. Duraklatma zorlamak için, yerel kod hata `-i` ayıklama etkinleştirdiğinizde Hata **Ayıklama** sekmesinde**Yorumlayıcı Bağımsız Değişkenler** **çalıştır** > seçeneği ekleyin. Bu bağımsız değişken, Python yorumlayıcısını kod bittikten sonra etkileşimli moda sokar ve bu noktada çıkmak için **Ctrl**+**Z** > **Enter** tuşuna basmanızı bekler.

1. Karışık mod hata ayıklayıcısını varolan bir işleme **(İşleme Hata** > **Ayıklama)** takarken, **Kod Türü Seç** iletişim kutusunu açmak için **Seç** düğmesini kullanın. Ardından **hata ayıklama bu kod türleri** seçeneğini ayarlayın ve listede hem **Yerel** Hem de **Python'u** seçin:

    ![Yerel ve Python kod türlerini seçme](media/mixed-mode-debugging-code-type.png)

    Kod türü ayarları kalıcıdır, bu nedenle daha sonra farklı bir işleme iliştirirken karışık mod hata ayıklamaişlemini devre dışı kakmak istiyorsanız **Python** kod türünü temizleyin.

    Diğer kod türlerini **Yerel'e**ek olarak veya bunun yerine seçmek mümkündür. Örneğin, yönetilen bir uygulama, yerel uzantı modüllerini kullanan CPython'u barındırıyorsa ve üçünü de hata ayıklamak istiyorsanız, **python,** **yerel**ve **yönetilen** leri, birleşik arama yığınları ve üç çalışma süresi arasında adım atma dahil olmak üzere birleştirilmiş hata ayıklama deneyimi için birlikte denetleyebilirsiniz.

1. Karışık modda ilk kez hata ayıklamaya başladığınızda, **Python Symbols Required** iletişim kutusunu görebilirsiniz [(bkz. karışık mod hata ayıklama için Semboller).](debugging-symbols-for-mixed-mode-c-cpp-python.md) Belirli bir Python ortamı için yalnızca bir kez semboller yüklemeniz gerekir. Visual Studio yükleyicisi (Visual Studio 2017 ve sonrası) aracılığıyla Python desteğini yüklerseniz semboller otomatik olarak dahil edilir.

1. Hata ayıklama yaparken standart Python'un kaynak kodunu [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/)kullanılabilir hale getirmek için, sürümünüze uygun arşivi ziyaret edin ve bir klasöre ayıklayın. Daha sonra Visual Studio'u sizden ne istenirse istendiği noktada o klasördeki belirli dosyalara yönlendirirsiniz.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>C/C++ projesinde karışık mod hata ayıklamayı etkinleştirme

Visual Studio (2017 sürüm 15.5 ve sonrası) bir C/C++ projesinden karışık mod hata ayıklamayı destekler (örneğin, [Python'u python.org açıklandığı gibi başka bir uygulamaya katıştırırken).](https://docs.python.org/3/extending/embedding.html) Karışık mod hata ayıklamayı etkinleştirmek için, C/C++ projesini **Python/Yerel Hata Ayıklama'yı**başlatmak için yapılandırın:

1. **Solution Explorer'daki** C/C++ projesine sağ tıklayın ve **Özellikler'i**seçin.
1. Hata **Ayıklama** sekmesini seçin, **başlatmaiçin Hata** **Ayıklama'dan Python/Yerel Hata Ayıklama'yı** seçin ve **Tamam'ı**seçin.

    ![C/C++ projesinde Python/Native hata ayıklayıcısı seçme](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> **Python/Yerel Hata Ayıklama'yı** seçme seçeneğiniz yoksa, önce VS yükleyicisini kullanarak **Python yerel geliştirme araçlarını** yüklemeniz gerekir. Python geliştirme iş yükü altında bir seçenek olarak bulabilirsiniz. Daha fazla bilgi için [Windows'da Visual Studio'da Python desteği nasıl yüklenir'](installing-python-support-in-visual-studio.md)e bakın.

Bu yöntemi kullanarak, hata ayıklayıcının bağlı olmayacağı bir alt *python.exe* işlemi *oluşturduğundan, py.exe* başlatıcısının kendisini hata ayıklamadığınızı unutmayın. *Python.exe'yi* doğrudan bağımsız değişkenlerle başlatmak istiyorsanız, **Python/Native Hata Ayıklama** özelliklerindeki **(önceki** resimde gösterilen) Komut seçeneğini değiştirerek *python.exe'ye*tam yolu belirtin, ardından **Komut Bağımsız Değişkenleri'ndeki**bağımsız değişkenleri belirtin.

### <a name="attaching-the-mixed-mode-debugger"></a>Karışık mod hata ayıklama ekleme

Visual Studio'nun önceki tüm sürümlerinde, C/C++ projeleri yalnızca yerel hata ayıklayıcısı kullandığından, visual studio'da bir Python projesi başlatılırken doğrudan karma mod hata ayıklama etkinleştirilir. Ancak, hata ayıklama yı ayrı ayrı ekleyebilirsiniz:

1. Hata ayıklama olmadan C++ projesini başlatın ( Hata Ayıklama veya **Ctrl**+**F5**olmadan**Hata Ayıklama** > **Başlat).**
1. İşleme **Hata Ayıklama** > **Ekle'yi**seçin. Görünen iletişim kutusunda, uygun işlemi seçin ve **python'u**seçebileceğiniz **Kod Türünü Seç** iletişim kutusunu açmak için **Seç** düğmesini kullanın:

    ![Hata ayıklama takarken hata ayıklama türü olarak Python'u seçme](media/mixed-mode-debugging-attach-type.png)

1. Bu iletişim kutusunu kapatmak için **Tamam'ı** seçin ve hata ayıklamayı başlatmak için **Ekle'yi** seçin.
1. Hata ayıklayıcıyı takma fırsatınız olmadan önce hata ayıklamak istediğiniz Python kodunu aramadığından emin olmak için C++ uygulamasında uygun bir duraklama veya gecikme getirmeniz gerekebilir.

## <a name="mixed-mode-specific-features"></a>Karışık moda özgü özellikler

- [Birleşik çağrı yığını](#combined-call-stack)
- [Python ve yerel kod arasındaki adım](#step-between-python-and-native-code)
- [PyObject değerleri yerel kodgörünümü](#pyobject-values-view-in-native-code)
- [Python kodunda yerel değerler görünümü](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Birleşik çağrı yığını

**Çağrı Yığını** penceresi, hem yerel hem de Python yığın çerçevelerini ara sıra gösterir ve geçişler ikisi arasında işaretlenir:

![Karışık mod hata ayıklama ile birleşik arama yığını](media/mixed-mode-debugging-call-stack.png)

**Araçlar** >  > **General** > **Enable Just My Code** **Options****Debugging** **[External Code]** > Seçenekleri Hata Ayıklama Genel IDamı Yalnızca Kodumu Etkinleştir seçeneği ayarlanmışsa, geçiş yönünü belirtmeden geçişler [Dış Kod] olarak görünür.

Herhangi bir çağrı çerçevesine çift tıklatma, onu etkin kılar ve mümkünse uygun kaynak kodunu açar. Kaynak kodu kullanılamıyorsa, çerçeve hala etkin hale getirilir ve yerel değişkenler denetlenebilir.

### <a name="step-between-python-and-native-code"></a>Python ve yerel kod arasındaki adım

**Step Into** (**F11**) veya **Step Out** (**Shift**+**F11**) komutlarını kullanırken, karışık mod hata ayıklayıcı kod türleri arasındaki değişiklikleri doğru şekilde işler. Örneğin, Python C'de uygulanan bir tür yöntemi çağırdığında, bu yönteme çağrıya adım atma yöntemi uygulayan yerel işlevin başında durur. Benzer şekilde, yerel kod python kodunun çağrılmış olmasıyla sonuçlanan bazı Python API işlevini çağırdığında. Örneğin, Python işlevi `PyObject_CallObject` başında Python durur başlangıçta tanımlanan bir işlev değeri üzerinde bir adım. Python'dan yerel e vere kadar adım atmak, [Python'dan çağrılan yerel](https://docs.python.org/3/library/ctypes.html)işlevler için de desteklenir.

### <a name="pyobject-values-view-in-native-code"></a>PyObject değerleri yerel kodgörünümü

Yerel (C veya C++) bir çerçeve etkin olduğunda, yerel değişkenleri hata ayıklama **Yerel leri** penceresinde gösterir. Yerel Python uzantımodüllerinde, bu değişkenlerin `PyObject` çoğu türdedir (typedef için `_object`dir), veya birkaç temel Python türü (aşağıdaki listeye bakın). Karışık mod hata ayıklamada, bu değerler **[Python görünümü]** etiketli ek bir alt düğüm sunar. Genişletildiğinde, bu düğüm değişkenin Python gösterimini gösterir ve aynı nesneye başvuran yerel bir değişkenin Python çerçevesinde bulunsun da aynı olduğunu görürsünüz. Bu düğümün çocukları değiştirilebilir.

![Yerel ler penceresinde Python Görünümü](media/mixed-mode-debugging-python-view.png)

Bu özelliği devre dışı katmak için **Yerel Ler** penceresinde herhangi bir yere sağ tıklayın ve **Python** > **Show Python Görünüm Düğümleri** menüsü seçeneğini değiştirin:

![Yerel Ler penceresinde Python Görünümünü Etkinleştirme](media/mixed-mode-debugging-enable-python-view.png)

**[Python görünümü]** düğümlerini gösteren C türleri (etkinse):

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

**[Python görünümü]** kendi yazdığınız türler için otomatik olarak görünmez. Python 3.x uzantıları yazarken, herhangi bir nesne sonuçta `ob_base` **[Python görünümü]** görünmesine neden olan yukarıdaki türlerden biri bir alana sahip olduğundan, bu eksikliği genellikle bir sorun değildir.

Ancak Python 2.x için, her nesne türü genellikle üstbilgisini satır içinde alanlar topluluğu olarak bildirir ve `PyObject` özel yazar türleri ile C/C++ kodundaki tür sistemi düzeyinde arasında bir ilişki yoktur. Bu tür özel türler için **[Python görünümü]** düğümlerini etkinleştirmek için Python [dizinyükleme dizinindeki](installing-python-support-in-visual-studio.md#install-locations) *PythonDkm.natvis* dosyasını edin ve C veya C++ sınıfınız için XML'ye başka bir öğe ekleyin.

Alternatif (ve daha iyi) bir seçenek [PEP 3123](https://www.python.org/dev/peps/pep-3123/) takip etmek ve yerine açık `PyObject ob_base;` bir alan kullanmak `PyObject_HEAD`, her zaman geriye dönük uyumluluk nedenlerle mümkün olmayabilir rağmen.

### <a name="native-values-view-in-python-code"></a>Python kodunda yerel değerler görünümü

Önceki bölüme benzer şekilde, Python çerçevesi etkin olduğunda **Yereller** penceresinde yerel değerler için bir **[C++ görünümü]** etkinleştirebilirsiniz. Bu özellik varsayılan olarak etkinleştirilmez, bu nedenle **Yerel Ler** penceresinde sağ tıklayarak ve **Python** > **Show C++ Görünüm Düğümleri** menüsü seçeneğini değiştirerek etkinleştirirsiniz.

![Yerel ler penceresinde C++ Görünümünü Etkinleştirme](media/mixed-mode-debugging-enable-cpp-view.png)

**[C++ görünüm]** düğümü, yerel bir çerçevede göreceğiniz değerle aynı olan temel C/C++ yapısının bir temsilini sağlar. Örneğin, Python uzun tamsayı `_longobject` için `PyLongObject` bir örnek (typedef olan) gösterir ve kendi yazdığınız yerel sınıflar için türleri çıkartmaya çalışır. Bu düğümün çocukları değiştirilebilir.

![Yerel ler penceresinde C++ Görünümü](media/mixed-mode-debugging-cpp-view.png)

Bir nesnenin alt alanı türdeyse `PyObject`veya diğer desteklenen türlerden biriyse, bir **[Python görünümü]** gösterim düğümü (bu gösterimler etkinse) vardır ve bağlantıların doğrudan Python'a maruz kalınmadığı nesne grafiklerinde gezinmeyi mümkün kılar.

Nesnenin türünü belirlemek için Python nesne meta verilerini kullanan **[Python görünümü]** düğümlerinin aksine, **[C++ görünümü]** için benzer şekilde güvenilir bir mekanizma yoktur. Genel olarak konuşursak, Python değeri (yani bir `PyObject` başvuru) göz önüne alındığında, hangi C/C++ yapısının onu desteklediğini güvenilir bir şekilde belirlemek mümkün değildir. Karışık mod hata ayıklama, işlev işaretçisi türlerine sahip nesnenin türündeki `PyTypeObject` `ob_type` (alanı tarafından başvurulan gibi) çeşitli alanlara bakarak bu türü tahmin etmeye çalışır. Bu işlev işaretçilerinden biri çözülebilen bir işleve başvuruyorsa ve bu işlevin türünden daha spesifik bir `self` parametresi `PyObject*`varsayılsa, bu tür destek türü olarak kabul edilir. Örneğin, belirli `ob_type->tp_init` bir nesneaşağıdaki işlevi işaret ederse:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

sonra hata ayıklama doğru nesnenin C türü olduğunu `FobObject`anlayabilir. Daha kesin bir tür `tp_init`belirleyemiyorsa, diğer alanlara geçer. Bu alanlardan herhangi birinden türü çıkaramıyorsa, **[C++ görünümü]** düğümü nesneyi örnek `PyObject` olarak sunar.

Her zaman özel yazartürleri için yararlı bir gösterim almak için, türü kaydederken en az bir özel işlevi `self` kaydetmek ve güçlü bir şekilde yazılmış bir parametre kullanmak en iyisidir. Çoğu tür doğal olarak bu gereksinimi yerine getirmek; bu durumda değilse, o `tp_init` zaman genellikle bu amaç için kullanmak için en uygun giriştir. Yalnızca hata ayıklayıcı türü çıkarımını etkinleştirmek `tp_init` için mevcut olan bir tür için sahte bir uygulama, yukarıdaki kod örneğinde olduğu gibi hemen sıfır döndürebilir.

## <a name="differences-from-standard-python-debugging"></a>Standart Python hata ayıklama farklılıkları

Karışık mod hata ayıklayıcısı, bazı ek özellikler sunması açısından [standart Python hata ayıklayıcısından](debugging-python-in-visual-studio.md) farklıdır, ancak Python ile ilgili bazı özelliklerden yoksundur:

- Desteklenmeyen özellikler: koşullu kesme noktaları, **Hata Ayıklama Etkileşimli** pencere ve platform ötesi uzaktan hata ayıklama.
- **Hemen** pencere: kullanılabilir ancak burada listelenen tüm sınırlamalar da dahil olmak üzere işlevselliğinin sınırlı bir alt kümesi ile.
- Desteklenen Python sürümleri: Yalnızca CPython 2.7 ve 3.3+
- Visual Studio Shell: Python'u Visual Studio Shell ile kullanırken (örneğin, tümleşik yükleyiciyi kullanarak yüklediyseniz), Visual Studio C++ projelerini açamaz ve C++ dosyalarının düzenleme deneyimi yalnızca temel bir metin düzenleyicisi dir. Ancak, C/C++ hata ayıklama ve karışık mod hata ayıklama, kaynak kodu yla Shell'de tam olarak desteklenir, yerel koda adım atar ve hata ayıklama pencerelerinde C++ ifade değerlendirmesi.
- Nesneleri görüntüleme ve genişletme: **Yerel olarak** Python nesneleri ve Hata ayıklama aracı pencerelerinde **izle,** karışık modhatager yalnızca nesnelerin yapısını gösterir. Özellikleri otomatik olarak değerlendirmez veya hesaplanmış öznitelikleri göstermez. Koleksiyonlar için yalnızca yerleşik koleksiyon türleri için`tuple`öğeleri `list` `dict`gösterir `set`( , , , , . Özel koleksiyon türleri, bazı yerleşik koleksiyon türünden devralınmadıkları sürece koleksiyon olarak görselleştirilmez.
- İfade değerlendirmesi: aşağıya bakın.

### <a name="expression-evaluation"></a>İfade değerlendirmesi

Standart Python hata ayıklayıcı, bir G/Ç işlemi veya diğer benzer sistem çağrısında engellenmemesi sürece, hata ayıklama işlemi kodun herhangi bir noktasında duraklatılmış olduğunda **İzle** ve **Hemen** pencerelerinde rasgele Python ifadelerinin değerlendirilmesine olanak tanır. Karışık modhatabing,rasgele ifadeler yalnızca Python kodunda durdurulduğunda, bir kesme noktasından sonra veya koda adım attığında değerlendirilebilir. İfadeler yalnızca kesme noktasının veya basamak işleminin oluştuğu iş parçacığında değerlendirilebilir.

Yerel kodda veya yukarıdaki koşulların geçerli olmadığı Python kodunda durdurulduğunda (örneğin, bir adım çıkarma işleminden sonra veya farklı bir iş parçacığı üzerinde), ifade değerlendirmesi şu anda seçili olan yerel ve genel değişkenlere erişmekle sınırlıdır çerçeve, alanlarına erişme ve yerleşik koleksiyon türlerini gerçek lerle dizine ekleyerek. Örneğin, aşağıdaki ifade herhangi bir bağlamda değerlendirilebilir (tüm tanımlayıcıların varolan değişkenlere ve uygun türdeki alanlara başvurması koşuluyla):

```python
foo.bar[0].baz['key']
```

Karışık mod hata ayıklama da bu tür ifadeleri farklı şekilde çözer. Tüm üye erişim işlemleri yalnızca nesnenin doğrudan parçası olan alanları (örneğin, `__dict__` kendi veya `__slots__`veya , veya python `tp_members`üzerinden Python'a maruz `__getattr__` `__getattribute__` kalan yerel bir yapının alanı gibi) arar ve herhangi bir veya açıklayıcı mantığı yok sayar. Benzer şekilde, tüm dizin oluşturma işlemleri yoksama `__getitem__`ve koleksiyonların iç veri yapılarına doğrudan erişin.

Tutarlılık adına, bu ad çözümleme düzeni, geçerli durak noktasında rasgele ifadelere izin verilip verilmedidiğine bakılmaksızın, sınırlı ifade değerlendirmesi için kısıtlamalarla eşleşen tüm ifadeler için kullanılır. Tam özellikli bir değerlendirici kullanılabilir olduğunda uygun Python semantiklerini zorlamak için, ifadeyi parantez içine avurun:

```python
(foo.bar[0].baz['key'])
```
