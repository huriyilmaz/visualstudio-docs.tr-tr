---
title: Python için karışık modda hata ayıklama
description: Ortamlar arasında adımlamayı, değerleri görüntülemeyi ve ifadeleri değerlendirmeyi de içeren Visual Studio 'da C++ ve Python için aynı anda hata ayıklayın.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 953ff26a6094a9de9dcf974d5e4cb5a02aaa503f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533568"
---
# <a name="debug-python-and-c-together"></a>Python ve C++ ile birlikte hata ayıklama

Çoğu normal Python hata ayıklayıcıları yalnızca Python kodunun hata ayıklamasını destekler. Bununla birlikte, Python, yüksek performans gerektiren senaryolarda C veya C++ ile birlikte kullanılır ve platform API 'Lerini doğrudan çağırabilme olanağı sağlar. (Bkz. bir izlenecek yol için bkz. [Python Için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md) .)

Visual Studio, Python ve yerel C/C++ için tümleşik, eşzamanlı karışık modda hata ayıklama sağlar ve Visual Studio yükleyicisindeki **Python geliştirme** iş yükü için **Python yerel geliştirme araçları** seçeneğini belirleyebilirsiniz.

> [!Note]
> Visual Studio 2015 ve önceki sürümlerde Visual Studio için Python Araçları 1. x ile karışık modda hata ayıklama kullanılamaz.

Karma mod hata ayıklama özellikleri, bu makalede açıklandığı gibi aşağıdakileri içerir:

- Birleşik çağrı yığınları
- Python ve yerel kod arasında adımla
- Her iki kod türündeki kesme noktaları
- Yerel çerçevelerdeki nesnelerin Python temsillerine veya bunun tersini görün
- Python projesi veya C++ projesi bağlamı içinde hata ayıklama

![Visual Studio 'da Python için karışık modda hata ayıklama](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![video için film kamerası simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") | Visual Studio ile yerel C modülleri oluşturmaya, test etmeye ve hata ayıklamaya giriş için bkz. [derinlemesine bakış: yerel modüller oluşturma](https://youtu.be/D9RlT06a1EI) (YouTube.com, 9 dk 09s). Video hem Visual Studio 2015 hem de 2017 için geçerlidir. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Python projesinde karışık modda hata ayıklamayı etkinleştir

1. **Çözüm Gezgini**' de Python projesine sağ tıklayın, **Özellikler**' i seçin, **Hata Ayıkla** sekmesini seçin ve ardından **yerel kod hata ayıklamayı etkinleştir**' i seçin. Bu seçenek tüm hata ayıklama oturumları için karışık mod sağlar.

    ![Yerel kod hata ayıklamasını etkinleştirme](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Yerel kod hata ayıklamasını etkinleştirdiğinizde, bir program her ne kadar her zaman, duraklatmaya **devam etmek için herhangi bir tuşa basmadan** , Python çıkış penceresi hemen kaybolabilir. Bir duraklatma zorlamak için, `-i` **Run**  >  yerel kod hata ayıklamasını etkinleştirdiğinizde **hata ayıklama** sekmesindeki**yorumlayıcı bağımsız değişkenlerini** Çalıştır alanına seçeneği ekleyin. Bu bağımsız değişken, kod bittikten sonra Python yorumlayıcısını etkileşimli moda koyar, bu noktada **Ctrl** + çıkmak için CTRL**Z**  >  **ENTER** tuşlarına basmanız önerilir.

1. Karışık modda hata ayıklayıcıyı varolan bir işleme iliştirirken (**hata ayıklama**  >  **işleme ekleme**), **Select** düğmesini kullanarak **kod türünü seç** iletişim kutusunu açın. Sonra **Bu kod türlerini hata ayıkla** seçeneğini belirleyin ve listede hem **Yerel** hem de **Python** 'u seçin:

    ![Yerel ve Python kod türlerini seçme](media/mixed-mode-debugging-code-type.png)

    Kod türü ayarları kalıcıdır, bu nedenle daha sonra farklı bir işleme eklenirken karışık modda hata ayıklamayı devre dışı bırakmak istiyorsanız **Python** kod türünü temizleyin.

    Diğer kod türlerini, veya yerine, **Yerel**olarak veya yerine seçebilirsiniz. Örneğin, yönetilen bir uygulama, sırasıyla yerel uzantı modüllerini kullanır ve bu üç üçüne hata ayıklamak istiyorsanız, **Python**, **Yerel**ve **yönetilen** bir hata ayıklama deneyimi için birleştirilmiş çağrı yığınlarını ve üç çalışma alanı arasında adımlamayı bir araya getirebilirsiniz.

1. Karma modda hata ayıklamaya ilk kez başladığınızda, bir **Python sembolleri gerekli** iletişim kutusu görebilirsiniz (bkz. [karışık mod hata ayıklama sembolleri](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Sembolleri, belirli bir Python ortamı için yalnızca bir kez yüklemeniz gerekir. Visual Studio yükleyicisi aracılığıyla Python desteği yüklerseniz semboller otomatik olarak eklenir (Visual Studio 2017 ve üzeri).

1. Hata ayıklarken standart Python 'nun kendisi için kaynak kodu kullanılabilir hale getirmek için, [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/) sürümünüz için uygun Arşivi indirin ve bir klasöre ayıklayın. Ardından, Visual Studio 'Yu bu klasördeki belirli dosyalara hangi noktada sorar.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>C/C++ projesinde karışık modda hata ayıklamayı etkinleştir

Visual Studio (2017 sürüm 15,5 ve üzeri), bir C/C++ projesinden karışık modda hata ayıklamayı destekler (örneğin, [Python.org ' de açıklandığı gibi başka bir uygulamaya Python](https://docs.python.org/3/extending/embedding.html)eklenirken). Karışık modda hata ayıklamayı etkinleştirmek için, C/C++ projesini **Python/yerel hata ayıklamayı**başlatmak üzere yapılandırın:

1. **Çözüm Gezgini** ' de C/C++ projesine sağ tıklayın ve **Özellikler**' i seçin.
1. **Hata ayıklama** sekmesini seçin, **başlatılacak hata ayıklayıcıdan** **Python/yerel hata ayıklama** öğesini seçin ve **Tamam**' ı seçin.

    ![Bir C/C++ projesinde Python/Native hata ayıklayıcıyı seçme](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> **Python/yerel hata ayıklamayı** seçme seçeneğiniz yoksa, önce vs yükleyicisini kullanarak **Python yerel geliştirme araçlarını** yüklemeniz gerekir. Bunu, Python geliştirme iş yükü altında bir seçenek olarak bulabilirsiniz. Daha fazla bilgi için bkz. [Windows üzerinde Visual Studio 'Da Python desteği nasıl yüklenir](installing-python-support-in-visual-studio.md).

Bu yöntemi kullanarak, hata ayıklayıcının iliştirilemediği bir alt *python.exe* işlemini oluşturduğundan *py.exe* başlatıcısı 'nın kendisinde hata ayıklayamayacağınız farkında olun. Bağımsız değişkenlerle *python.exe* doğrudan başlatmak istiyorsanız **Python/yerel hata ayıklama** özelliklerindeki (önceki görüntüde gösterilen) **komut** seçeneğini değiştirerek *python.exe*tam yolunu belirtin ve ardından **komut bağımsız**değişkenlerinde bağımsız değişkenleri belirtin.

### <a name="attaching-the-mixed-mode-debugger"></a>Karışık modda hata ayıklayıcıyı iliştirme

Visual Studio 'nun önceki tüm sürümlerinde doğrudan karışık modda hata ayıklama yalnızca Visual Studio 'da bir Python projesi başlatılırken etkindir çünkü C/C++ projeleri yalnızca yerel hata ayıklayıcıyı kullanır. Ancak, hata ayıklayıcıyı ayrı olarak iliştirebilirsiniz:

1. C++ projesini hata ayıklama olmadan**başlatın (hata ayıklama**  >  **olmadan Başlat** veya **CTRL** + **F5**).
1. İşleme **Ekle hata ayıkla**öğesini seçin  >  **Attach to Process**. Görüntülenen iletişim kutusunda, uygun işlemi seçin ve ardından **seçim** düğmesini kullanarak **Python**seçebileceğiniz **kod türünü seç** iletişim kutusunu açın:

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

Geçiş yönü belirtilmeden geçişler **[Dış kod]** olarak görünür yalnızca kendi kodum, **Tools**  >  **Options**  >  genel etkinleştir için**hata ayıklama**seçenekleri  >  **General**  >  **Enable Just My Code** seçeneği ayarlanırsa Araçlar Seçenekler.

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

Nesnenin türünü belirlemekte Python nesne meta verilerini kullanan **[Python View]** düğümlerinden farklı olarak **[C++ görünümü]** için benzer bir güvenilir mekanizma yoktur. Genellikle bir Python değeri (yani bir `PyObject` başvuru) verildiğinde, hangi C/C++ yapısının bu dosyayı yedekleyeceğini güvenilir bir şekilde belirleme mümkün değildir. Karışık modda hata ayıklayıcı, nesne türünün ( `PyTypeObject` alanı tarafından başvurulan `ob_type` ) işlev işaretçisi türleri olan çeşitli alanlarına bakarak bu türü tahmin etmeye çalışır. Bu işlev işaretçilerinden biri çözülebilenbir işleve başvuruyorsa ve bu işlev `self` , ' den daha belirgin bir parametreye sahipse `PyObject*` , bu tür, yedekleme türü olarak kabul edilir. Örneğin, `ob_type->tp_init` belirli bir nesne aşağıdaki işlev gösteriyorsa:

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
- Visual Studio Kabuğu: Visual Studio Kabuğu ile Python kullanırken (örneğin, tümleşik yükleyiciyi kullanarak yüklediyseniz), Visual Studio C++ projelerini açamaz ve C++ dosyaları için düzenleme deneyimi yalnızca temel bir metin düzenleyicidir. Ancak, C/C++ hata ayıklama ve karışık modda hata ayıklama, kaynak kodu ile kabukta tam olarak desteklenir, yerel koda adımlanıyor ve hata ayıklayıcı Windows 'ta C++ ifade değerlendirmesi.
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
