---
title: Python için karışık modda hata ayıklama
description: ortamlar arasında atlama, değerleri görüntüleme ve ifadeleri değerlendirme dahil Visual Studio aynı anda C++ ve Python hatalarını ayıklayın.
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
ms.openlocfilehash: 71e2b5372daf56ac373b5a8d58ec4dd8a4a5ec5579a199e5277c0774efd532b8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410151"
---
# <a name="debug-python-and-c-together"></a>Python ve C++ ile birlikte hata ayıklama

Çoğu normal Python hata ayıklayıcıları yalnızca Python kodunun hata ayıklamasını destekler. Bununla birlikte, Python, yüksek performans gerektiren senaryolarda C veya C++ ile birlikte kullanılır ve platform API 'Lerini doğrudan çağırabilme olanağı sağlar. (Bkz. bir izlenecek yol için bkz. [Python Için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md) .)

Visual Studio python ve yerel C/C++ için tümleşik, eşzamanlı karışık modda hata ayıklama sağlar ve bu sayede, Visual Studio yükleyicisindeki **python geliştirme** iş yükü için **python yerel geliştirme araçları** seçeneğini belirleyebilirsiniz.

> [!Note]
> karışık modda hata ayıklama, Visual Studio 2015 ve önceki sürümlerde Visual Studio için Python Araçları 1. x ile kullanılamaz.

Karma mod hata ayıklama özellikleri, bu makalede açıklandığı gibi aşağıdakileri içerir:

- Birleşik çağrı yığınları
- Python ve yerel kod arasında adımla
- Her iki kod türündeki kesme noktaları
- Yerel çerçevelerdeki nesnelerin Python temsillerine veya bunun tersini görün
- Python projesi veya C++ projesi bağlamı içinde hata ayıklama

![Visual Studio 'de Python için karışık modda hata ayıklama](media/mixed-mode-debugging.png)

![video için film kamerası simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") Visual Studio ile yerel C modüllerini oluşturmaya, test etmeye ve hata ayıklamaya giriş için bkz. [derinlemesine bakış: yerel modüller oluşturma](https://youtu.be/D9RlT06a1EI) (youtube.com, 9 dk 09s). video hem Visual Studio 2015 hem de 2017 için geçerlidir.


## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Python projesinde karışık modda hata ayıklamayı etkinleştir

1. **Çözüm Gezgini**' de Python projesine sağ tıklayın, **Özellikler**' i seçin, **Hata Ayıkla** sekmesini seçin ve ardından **yerel kod hata ayıklamayı etkinleştir**' i seçin. Bu seçenek tüm hata ayıklama oturumları için karışık mod sağlar.

    ![Yerel kod hata ayıklamasını etkinleştirme](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Yerel kod hata ayıklamasını etkinleştirdiğinizde, bir program her ne kadar her zaman, duraklatmaya **devam etmek için herhangi bir tuşa basmadan** , Python çıkış penceresi hemen kaybolabilir. Bir duraklatma zorlamak için, `-i`   >  yerel kod hata ayıklamasını etkinleştirdiğinizde **hata ayıklama** sekmesindeki **yorumlayıcı bağımsız değişkenlerini** Çalıştır alanına seçeneği ekleyin. Bu bağımsız değişken, kod bittikten sonra Python yorumlayıcısını etkileşimli moda koyar, bu noktada  + çıkmak için CTRL **Z**  >  **ENTER** tuşlarına basmanız önerilir.

1. Karışık modda hata ayıklayıcıyı varolan bir işleme iliştirirken (**hata ayıklama**  >  **işleme ekleme**), **Select** düğmesini kullanarak **kod türünü seç** iletişim kutusunu açın. Sonra **Bu kod türlerini hata ayıkla** seçeneğini belirleyin ve listede hem **Yerel** hem de **Python** 'u seçin:

    ![Yerel ve Python kod türlerini seçme](media/mixed-mode-debugging-code-type.png)

    Kod türü ayarları kalıcıdır, bu nedenle daha sonra farklı bir işleme eklenirken karışık modda hata ayıklamayı devre dışı bırakmak istiyorsanız **Python** kod türünü temizleyin.

    Diğer kod türlerini, veya yerine, **Yerel** olarak veya yerine seçebilirsiniz. Örneğin, yönetilen bir uygulama, sırasıyla yerel uzantı modüllerini kullanır ve bu üç üçüne hata ayıklamak istiyorsanız, **Python**, **Yerel** ve **yönetilen** bir hata ayıklama deneyimi için birleştirilmiş çağrı yığınlarını ve üç çalışma alanı arasında adımlamayı bir araya getirebilirsiniz.

1. Karma modda hata ayıklamaya ilk kez başladığınızda, bir **Python sembolleri gerekli** iletişim kutusu görebilirsiniz (bkz. [karışık mod hata ayıklama sembolleri](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Sembolleri, belirli bir Python ortamı için yalnızca bir kez yüklemeniz gerekir. Visual Studio yükleyicisi aracılığıyla Python desteği yüklerseniz semboller otomatik olarak eklenir (Visual Studio 2017 ve üzeri).

1. Hata ayıklarken standart Python 'nun kendisi için kaynak kodu kullanılabilir hale getirmek için, [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/) sürümünüz için uygun Arşivi indirin ve bir klasöre ayıklayın. daha sonra bu klasördeki belirli dosyalara, sizden hangi noktada Visual Studio işaret edersiniz.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>C/C++ projesinde karışık modda hata ayıklamayı etkinleştir

Visual Studio (2017 sürüm 15,5 ve üzeri), bir C/C++ projesinden karışık modda hata ayıklamayı destekler (örneğin, Python 'u [python.org ' de açıklandığı gibi başka bir uygulamaya katıştırırken](https://docs.python.org/3/extending/embedding.html)). Karışık modda hata ayıklamayı etkinleştirmek için, C/C++ projesini **Python/yerel hata ayıklamayı** başlatmak üzere yapılandırın:

1. **Çözüm Gezgini** ' de C/C++ projesine sağ tıklayın ve **Özellikler**' i seçin.
1. **Hata ayıklama** sekmesini seçin, **başlatılacak hata ayıklayıcıdan** **Python/yerel hata ayıklama** öğesini seçin ve **Tamam**' ı seçin.

    ![Bir C/C++ projesinde Python/Native hata ayıklayıcıyı seçme](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> **Python/yerel hata ayıklamayı** seçme seçeneğiniz yoksa, önce vs yükleyicisini kullanarak **Python yerel geliştirme araçlarını** yüklemeniz gerekir. Bunu, Python geliştirme iş yükü altında bir seçenek olarak bulabilirsiniz. daha fazla bilgi için, bkz. [Windows Visual Studio Python desteğini yüklemek](installing-python-support-in-visual-studio.md).

Bu yöntemi kullanarak, hata ayıklayıcının iliştirilemediği bir alt *python.exe* işlemini oluşturduğundan *py.exe* başlatıcısı 'nın kendisinde hata ayıklayamayacağınız farkında olun. Bağımsız değişkenlerle *python.exe* doğrudan başlatmak istiyorsanız **Python/yerel hata ayıklama** özelliklerindeki (önceki görüntüde gösterilen) **komut** seçeneğini değiştirerek *python.exe* tam yolunu belirtin ve ardından **komut bağımsız** değişkenlerinde bağımsız değişkenleri belirtin.

### <a name="attaching-the-mixed-mode-debugger"></a>Karışık modda hata ayıklayıcıyı iliştirme

önceki Visual Studio tüm sürümleri için doğrudan karışık modda hata ayıklama yalnızca, Visual Studio içinde bir Python projesi başlatılırken etkinleştirilir, çünkü C/C++ projeleri yalnızca yerel hata ayıklayıcıyı kullanır. Ancak, hata ayıklayıcıyı ayrı olarak iliştirebilirsiniz:

1. C++ projesini hata ayıklama olmadan **başlatın (hata ayıklama**  >  **olmadan Başlat** veya **CTRL** + **F5**).
1. İşleme **Ekle hata ayıkla** öğesini seçin  >  . Görüntülenen iletişim kutusunda, uygun işlemi seçin ve ardından **seçim** düğmesini kullanarak **Python** seçebileceğiniz **kod türünü seç** iletişim kutusunu açın:

    ![Hata ayıklayıcı eklenirken hata ayıklama türü olarak Python seçme](media/mixed-mode-debugging-attach-type.png)

1. Bu iletişim kutusunu kapatmak için **Tamam** ' ı seçin ve ardından hata ayıklayıcıyı başlatmak için **iliştirin** .
1. Hata ayıklayıcıyı iliştirme şansınız olmadan önce, hata ayıklamak istediğiniz Python kodunu çağırmadığından emin olmak için C++ uygulamasında uygun bir duraklatma veya gecikme yapmanız gerekebilir.

## <a name="mixed-mode-specific-features"></a>Karma moda özgü özellikler

- [Birleşik çağrı yığını](#combined-call-stack)
- [Python ve yerel kod arasında adımla](#step-between-python-and-native-code)
- [Yerel koddaki PyObject değerleri görünümü](#pyobject-values-view-in-native-code)
- [Python kodundaki yerel değerler görünümü](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Birleşik çağrı yığını

**Çağrı yığını** penceresi hem yerel hem de Python yığın çerçevelerini araya eklemeli, aralarında iki arasında işaretlenmiş geçişlerle birlikte görüntülenir:

![Karışık modda hata ayıklama ile Birleşik çağrı yığını](media/mixed-mode-debugging-call-stack.png)

Geçiş yönü belirtilmeden geçişler **[Dış kod]** olarak görünür yalnızca kendi kodum,   >    >  genel etkinleştir için **hata ayıklama** seçenekleri  >    >   seçeneği ayarlanırsa Araçlar Seçenekler.

Herhangi bir çağrı çerçevesini çift tıklamak etkin hale getirir ve mümkünse uygun kaynak kodu açar. Kaynak kodu kullanılabilir değilse, çerçeve hala etkin hale getirilir ve yerel değişkenler incelenebilir.

### <a name="step-between-python-and-native-code"></a>Python ve yerel kod arasında adımla

**Step Into** (**F11**) veya **Step Out** (**SHIFT** + **F11**) komutlarının kullanıldığı durumlarda, karışık modda hata ayıklayıcı kod türleri arasındaki değişiklikleri doğru şekilde işler. Örneğin, Python, C 'de uygulanan bir türün yöntemini çağırdığında, yöntemi çağıran yerel işlevin başlangıcında bu yönteme atlama yapılır. Benzer şekilde, yerel kod, Python kodunun çağrılması ile sonuçlanan bazı Python API işlevlerini çağırır. Örneğin, Python `PyObject_CallObject` işlevinin başlangıcında, Python 'da ilk olarak tanımlanan bir işlev değerinde bir üzerinde adımlanın. Python 'dan Native 'e Adımlama, [ctypes](https://docs.python.org/3/library/ctypes.html)aracılığıyla Python 'dan çağrılan yerel işlevler için de desteklenir.

### <a name="pyobject-values-view-in-native-code"></a>Yerel koddaki PyObject değerleri görünümü

Yerel (C veya C++) çerçevesi etkin olduğunda, yerel değişkenleri hata ayıklayıcı **Yereller** penceresinde görünür. Yerel Python uzantısı modüllerinde, bu değişkenlerin çoğu türü `PyObject` (için bir typedef `_object` ) ya da başka bir temel Python türü (aşağıdaki listeye bakın) vardır. Karışık modda hata ayıklamada, bu değerler **[Python görünümü]** etiketli ek bir alt düğüm sunar. Bu düğüm, genişletildiğinde, bir Python çerçevesinde aynı nesneye başvuran yerel bir değişken varsa, değişkenin Python gösterimini gösterir. Bu düğümün alt öğeleri düzenlenebilir.

![Yereller penceresinde Python görünümü](media/mixed-mode-debugging-python-view.png)

Bu özelliği devre dışı bırakmak için **Yereller** penceresinde herhangi bir yere sağ tıklayın ve **Python**  >  **görünüm düğümlerini göster** menü seçeneğini değiştirin:

![Yereller penceresinde Python görünümünü etkinleştirme](media/mixed-mode-debugging-enable-python-view.png)

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

**[Python görünümü]** yazdığınız türler için otomatik olarak görünmez. Python 3. x için uzantı yazma sırasında, genellikle herhangi bir nesne yukarıdaki türlerden birine sahip olduğu için bu eksik bir sorun değildir çünkü bu, `ob_base` **[Python görünümü]** ' nin görünmesine neden olur.

Ancak Python 2. x için, her nesne türü genellikle üst bilgisini bir satır içi alan koleksiyonu olarak bildirir ve özel olarak yazılan türler arasında ve `PyObject` C/C++ kodunda sistem düzeyinde tür ilişkisi yoktur. Bu tür özel türler için **[Python görünümü]** düğümlerini etkinleştirmek Için, [Python araçları Install dizinindeki](installing-python-support-in-visual-studio.md#install-locations) *PythonDkm. natvis* dosyasını düzenleyin ve C struct veya C++ sınıfınız için XML 'e başka bir öğe ekleyin.

Alternatif (ve daha iyi) seçeneği, [Pep 3123](https://www.python.org/dev/peps/pep-3123/) ' `PyObject ob_base;` i takip `PyObject_HEAD` etmekle birlikte, geriye doğru uyumluluk nedenleriyle her zaman mümkün olmayabilir.

### <a name="native-values-view-in-python-code"></a>Python kodundaki yerel değerler görünümü

Önceki bölüme benzer şekilde, bir Python çerçevesi etkin olduğunda **Yereller** penceresindeki yerel değerler için bir **[C++ görünümü]** sağlayabilirsiniz. Bu özellik varsayılan olarak etkin değildir, bu nedenle **Yereller** penceresinde sağ tıklayıp **Python**  >  **göster C++ görünüm düğümleri** menü seçeneğini değiştirerek etkinleştirin.

![Locals penceresinde C++ görünümünü etkinleştirme](media/mixed-mode-debugging-enable-cpp-view.png)

**[C++ View]** düğümü, bir değer Için temeldeki C/C++ yapısının bir gösterimini sağlar ve bir yerel çerçevede gördüklerle aynıdır. Örneğin, bir `_longobject` `PyLongObject` Python uzun tamsayısı için (bir typedef olan) örneğini gösterir ve kendi yazdığınız yerel sınıfların türlerini çıkarmaya çalışır. Bu düğümün alt öğeleri düzenlenebilir.

![Locals penceresinde C++ görünümü](media/mixed-mode-debugging-cpp-view.png)

Bir nesnenin alt alanı tür `PyObject` veya desteklenen diğer türlerden biri ise, bir **[Python görünümü]** temsili düğümüne sahiptir (Bu gösterimler etkinse), bağlantıların doğrudan Python 'a sunulmadığı nesne grafiklerine gidebilmesini sağlar.

Nesnenin türünü belirlemekte Python nesne meta verilerini kullanan **[Python View]** düğümlerinden farklı olarak **[C++ görünümü]** için benzer bir güvenilir mekanizma yoktur. Genellikle bir Python değeri (yani bir `PyObject` başvuru) verildiğinde, hangi C/C++ yapısının bu dosyayı yedekleyeceğini güvenilir bir şekilde belirleme mümkün değildir. Karışık modda hata ayıklayıcı, nesne türünün ( `PyTypeObject` alanı tarafından başvurulan `ob_type` ) işlev işaretçisi türleri olan çeşitli alanlarına bakarak bu türü tahmin etmeye çalışır. Bu işlev işaretçilerinden biri çözülebilenbir işleve başvuruyorsa ve bu işlev `self` , ' den daha belirgin bir parametreye sahipse `PyObject*` , bu tür, yedekleme türü olarak kabul edilir. Örneğin, aşağıdaki `ob_type->tp_init` işlevde verilen bir nesne noktaları varsa:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

ardından hata ayıklayıcısı, nesnenin C türünün olduğunu doğru şekilde `FobObject` ayıklar. türünden daha kesin bir tür belirleyeyene `tp_init` kadar diğer alanlara taşınır. Bu alanların herhangi bir türünden tür ayıklayamasa, **[C++ görünümü]** düğümü nesneyi örnek olarak `PyObject` sunar.

Özel olarak yazma türleri için her zaman yararlı bir gösterim elde etmek için, türü kaydettirirken en az bir özel işlevi kaydetmek ve kesin olarak türü kesin olarak belirtilen bir parametre kullanmak `self` en iyisidir. Çoğu tür bu gereksinimi doğal olarak karşılar; Böyle bir durum yoksa, bu `tp_init` amaçla kullanmak için genellikle en kullanışlı giriştir. Yalnızca hata ayıklayıcı türü çıkarıcısını etkinleştirmek için mevcut olan bir türün sahte uygulaması, yukarıdaki kod örneğinde olduğu gibi hemen `tp_init` sıfırı geri getirebilirsiniz.

## <a name="differences-from-standard-python-debugging"></a>Standart Python hata ayıklama arasındaki farklar

Karma mod hata ayıklayıcısı, bazı ek özelliklere sahip olması ancak Python ile ilgili bazı özelliklere sahip olmaması nedeniyle standart [Python](debugging-python-in-visual-studio.md) hata ayıklayıcısından farklıdır:

- Desteklenmeyen özellikler: koşullu kesme noktaları, **Etkileşimli Hata** Ayıklama penceresi ve platformlar arası uzaktan hata ayıklama.
- **Hemen** pencere: kullanılabilir ancak burada listelenen tüm sınırlamalar da dahil olmak üzere işlevlerinin sınırlı bir alt kümesine sahiptir.
- Desteklenen Python sürümleri: Yalnızca CPython 2.7 ve 3.3+ .
- Visual Studio Kabuk: Python'ı Visual Studio Shell ile kullanırken (örneğin, tümleşik yükleyiciyi kullanarak yüklemiş olursanız), Visual Studio C++ projelerini açamaz ve C++ dosyalarının düzenleme deneyimi yalnızca temel bir metin düzenleyicisidir. Ancak, kaynak kod, yerel koda adımlama ve hata ayıklayıcı pencerelerinde C++ ifadesi değerlendirmesi ile C/C++ hata ayıklama ve karma mod hata ayıklaması Kabuk'ta tam olarak değerlendirilmesi.
- Nesneleri görüntüleme ve genişletme: Python nesnelerini  **Yereller** ve İzleme hata ayıklayıcısı araç pencerelerinde görüntülerken, karma mod hata ayıklayıcısı yalnızca nesnelerin yapısını gösterir. Özellikleri otomatik olarak değerlendirmez veya hesaplanan öznitelikleri göstermez. Koleksiyonlar için yalnızca yerleşik koleksiyon türleri ( , , , ) `tuple` `list` öğelerini `dict` `set` gösterir. Özel koleksiyon türleri, bazı yerleşik koleksiyon türlerinden devralınmadıkça koleksiyonlar olarak görselleştirlanmaz.
- İfade değerlendirmesi: Aşağıya bakın.

### <a name="expression-evaluation"></a>İfade değerlendirmesi

Standart Python hata ayıklayıcısı, bir I/O  işlemi veya benzer bir sistem çağrısında engellenmiş olmayan sürece, hata ayıklama işlemi kodun herhangi bir noktasında duraklatıldıklarında İzleme ve Anlık pencerelerde rastgele Python ifadelerinin değerlendirilmesine olanak sağlar.  Karma mod hata ayıklamada rastgele ifadeler yalnızca Python kodunda durdurulurken, bir kesme noktası sonrasında veya koda adımlarken değerlendirebilirsiniz. İfadeler yalnızca kesme noktası veya adımlama işlemi meydana gelen iş parçacığında değerlendirebilirsiniz.

Yerel kodda veya yukarıdaki koşulların (örneğin, bir adım dışarı çıkma işlemi sonrasında veya farklı bir iş parçacığında) geçerli olduğu Python kodunda durdurulursa, ifade değerlendirmesi şu anda seçili olan çerçeve kapsamında yerel ve genel değişkenlere erişmek, alanlarına erişmek ve yerleşik koleksiyon türlerini değişmez değerlerle dizine dahil etmekle sınırlıdır. Örneğin, aşağıdaki ifade herhangi bir bağlamda değerlendirebilirsiniz (tüm tanımlayıcılar mevcut değişkenlere ve uygun türlere sahip alanlara başvurursa):

```python
foo.bar[0].baz['key']
```

Karma mod hata ayıklayıcısı da bu tür ifadeleri farklı şekilde çözümler. Tüm üye erişimi işlemleri yalnızca nesnenin doğrudan parçası olan alanları (veya içinde bir giriş veya aracılığıyla Python'a açık olan yerel bir yapının alanı gibi) arama ve herhangi bir veya tanımlayıcı mantığını `__dict__` `__slots__` `tp_members` `__getattr__` `__getattribute__` yoksayma. Benzer şekilde, tüm dizin oluşturma işlemleri `__getitem__` yoksayar ve koleksiyonların iç veri yapılarına doğrudan erişer.

Tutarlılık açısından bu ad çözümleme şeması, geçerli durdurma noktasında rastgele ifadelere izin verilip verilmeyip izin verilmeyilmesine bakılmaksızın, sınırlı ifade değerlendirmesinin kısıtlamalarıyla eşan tüm ifadeler için kullanılır. Tam özellikli bir değerlendirici kullanılabilir olduğunda düzgün Python semantiği zorlamak için, ifadeyi parantez içine alan:

```python
(foo.bar[0].baz['key'])
```
