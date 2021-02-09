---
title: Python için C++ uzantıları yazma
description: Visual Studio, Cpithon ve PyBind11 kullanarak Python için C++ uzantısı oluşturma konusunda izlenecek yol, karışık modda hata ayıklama da dahil.
ms.date: 11/19/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 461e68979de6c3b711c05cc4be3ef9d5bd761397
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885943"
---
# <a name="create-a-c-extension-for-python"></a>Python için C++ uzantısı oluşturma

C++ (veya C) ile yazılan modüller genellikle bir Python yorumlayıcısının yeteneklerini genişletmek için ve alt düzey işletim sistemi özelliklerine erişimi etkinleştirmek için kullanılır. Üç tür modül birincil vardır:

- Hızlandırıcı modülleri: Python, yorumlanan bir dil olduğundan, daha yüksek performans için belirli kod parçaları C++ dilinde yazılabilir.
- Sarmalayıcı modüller: mevcut C/C++ arabirimlerini Python kodu için kullanıma sunun veya Python 'dan kullanımı kolay bir "pythonic" API 'sini kullanıma sunun.
- Düşük düzey sistem erişim modülleri: CPython çalışma zamanının, işletim sisteminin veya temel alınan donanımın alt düzey özelliklerine erişmek için oluşturulur.

Bu makalede, bir hiperbolik tanjantı hesaplayan ve Python kodundan çağıran Cpyıthon için bir C++ uzantı modülü oluşturma adımları anlatılmaktadır. Bu yordam, C++ ' ta aynı yordamın uygulanması için göreli performans kazancı göstermek üzere Python 'da ilk olarak uygulanır.

Bu makale ayrıca, C++ ' ın Python için kullanılabilir hale getirme için iki yol gösterir:

- [Python belgelerinde](https://docs.python.org/3/c-api/) açıklandığı gibi standart Cpenthon uzantıları
- [PyBind11](https://github.com/pybind/pybind11), C++ 11 basitliği nedeniyle önerilir.

Bu ve diğer yollardan bir karşılaştırma, bu makalenin sonundaki [alternatif yaklaşımlar](#alternative-approaches) altında bulunur.

Bu izlenecek yolda tamamlanan örnek [Python-Samples-vs-cpp-Extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub) üzerinde bulunabilir.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017 veya üzeri, **C++ Ile masaüstü geliştirme** ve **Python geliştirme** iş yükleri için varsayılan seçeneklerle birlikte yüklenir.
- **Python geliştirme** iş yükünde, **Python yerel geliştirme araçları** için sağdaki kutuyu da seçin. Bu seçenek, bu makalede açıklanan yapılandırmanın çoğunu ayarlar. (Bu seçenek ayrıca C++ iş yükünü otomatik olarak içerir.)

    ![Python yerel geliştirme araçları seçeneğini belirleme](media/cpp-install-native.png)

    > [!Tip]
    > **Veri bilimi ve analitik uygulamalar** iş yükü yükleme, varsayılan olarak Python ve **Python yerel geliştirme araçları** seçeneğini de içerir.

Daha fazla bilgi için bkz. Visual Studio 'nun diğer sürümlerini kullanma dahil olmak üzere [Visual Studio Için Python desteğini yüklemeyin](installing-python-support-in-visual-studio.md). Python 'u ayrı olarak yüklerseniz, **hata ayıklama sembollerini indir** ve yükleyicideki **Gelişmiş Seçenekler** altında **hata ayıklama ikililerini indir** ' i seçtiğinizden emin olun. Bu seçenek, hata ayıklama derlemesi oluşturmayı seçerseniz gerekli hata ayıklama kitaplıklarının kullanılabilir olmasını sağlar.

## <a name="create-the-python-application"></a>Python uygulaması oluşturma

1. **Dosya**  >  **Yeni**  >  **Proje**' ye tıklayarak Visual Studio 'da yeni bir Python projesi oluşturun. "Python" araması yapın, **Python uygulama** şablonunu seçin, uygun bir ad ve konum verin ve **Tamam**' ı seçin.

1. C++ ile çalışma, 32 bitlik bir Python yorumlayıcısı kullanmanızı gerektirir (Python 3,6 veya üzeri önerilir). Visual Studio 'nun **Çözüm Gezgini** penceresinde, proje düğümünü genişletin ve ardından **Python ortamları** düğümünü genişletin. Varsayılan olarak 32 bitlik bir ortam görmüyorsanız (kalın veya **genel varsayılan** ile etiketlenmiş), [bir proje Için Python ortamı seçme](selecting-a-python-environment-for-a-project.md)konusundaki yönergeleri izleyin. 32 bit yorumlayıcı yüklü değilse bkz. [Python yorumlayıcıları 'Nı yükleme](installing-python-interpreters.md).

1. Projenin *. Kopyala* dosyasında, bir hiperbolik tanjantın (daha kolay karşılaştırma için matematik kitaplığı kullanılmadan uygulanır) hesaplamasını kıyaslandıran aşağıdaki kodu yapıştırın. [Python düzenlemesi özelliklerinden](editing-python-code-in-visual-studio.md)bazılarını denemek için kodu el ile girmeyi de ücretsiz olarak deneyin.

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. Sonuçları görmek için hata **ayıklama**  >  **olmadan Başlat** (**CTRL** + **F5**) komutunu kullanarak programı çalıştırın. Bu `COUNT` değişkeni, kıyaslama süresini değiştirmek için ayarlayabilirsiniz. Bu izlenecek yolun amaçları doğrultusunda, sayımı iki saniye boyunca alacak şekilde ayarlayın.

> [!TIP]
> Kıyaslama çalıştırılırken,   >  Visual Studio hata ayıklayıcısında kod çalıştırırken oluşan ek yükün oluşmasını önlemek için her zaman hata ayıklama **olmadan Başlat** ' ı kullanın.

## <a name="create-the-core-c-projects"></a>Core C++ projelerini oluşturma

"Superfastcode" ve "superfastcode2" adlı iki özdeş C++ projesi oluşturmak için bu bölümdeki yönergeleri izleyin. Daha sonra, C++ kodunu Python 'da kullanıma sunmak için her bir projede farklı yollardan yararlanabilirsiniz.

1. `PYTHONHOME`Ortam değişkeninin kullanmak Istediğiniz Python Yorumlayıcısına ayarlandığından emin olun. Visual Studio 'daki C++ projeleri, Python uzantısı oluştururken kullanılan *Python. h* gibi dosyaları bulmak için bu değişkene bağımlıdır.

1. **Çözüm Gezgini** çözüme sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin. Visual Studio çözümü, hem Python hem de C++ projelerini birlikte içerebilir (Python için Visual Studio kullanmanın avantajlarından biridir).

1. "C++" üzerinde arama yapın, **boş proje**' yi seçin, "superfastcode" (ikinci proje için "superfastcode2") adını belirtin ve **Tamam**' ı seçin.

    > [!Tip]
    > Visual Studio 'da **Python yerel geliştirme araçları** sayesinde, bunun yerine, aşağıda açıklananlar daha fazla olan Python **uzantı modülü** şablonuyla başlayabilirsiniz. Bu kılavuzda, ancak boş bir projeden başlamak, uzantı modülünün adım adım şekilde oluşturulmasını gösterir. İşlemi anladıktan sonra şablon, kendi uzantılarınızı yazarken size zaman kazandırır.

1. Yeni projede, **kaynak dosyaları** düğümüne sağ tıklayıp yeni öğe **Ekle**' yi seçin,  >   **C++ dosyası**' nı seçin `module.cpp` ve ardından **Tamam**' ı seçin.

    > [!Important]
    > *. Cpp* uzantısına sahip bir dosya, Izleyen adımlarda C++ Özellik sayfalarını açmak için gereklidir.

1. **Çözüm Gezgini**' de C++ projesine sağ tıklayın, **Özellikler**' i seçin.

1. Görüntülenen **Özellik sayfaları** iletişim kutusunun üst kısmında, **yapılandırmayı** **tüm yapılandırmalar** ve **Platform** için **Win32** olarak ayarlayın.

1. Aşağıdaki tabloda açıklandığı gibi belirli özellikleri ayarlayın ve ardından **Tamam**' ı seçin.

    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Genel**  >  **Hedef adı** | Deyimlerdeki Python 'dan başvurmak istediğiniz modülün adını belirtin `from...import` . Python için modül tanımlarken aynı adı C++ ' da kullanırsınız. Projenin adını modül adı olarak kullanmak istiyorsanız, **$ (ProjectName)** varsayılan değerini bırakın. |
    | | **Genel**  >  **Hedef uzantısı** | **. PYD** |
    | | **Proje Varsayılanları**  >  **Yapılandırma türü** | **Dinamik kitaplık (. dll)** |
    | **C/C++**  >  **Genel** | **Ek Içerme dizinleri** | Yükleme için uygun şekilde Python *içerme* klasörünü (örneğin,) ekleyin `c:\Python36\include` .  |
    | **C/C++**  >  **Önişlemci** | **Önişlemci tanımları** | **Yalnızca CPython**: `Py_LIMITED_API;` dizenin başına (noktalı virgül dahil) ekleyin. Bu tanım, Python 'dan çağırabilmeniz için bazı işlevleri kısıtlar ve kodu farklı Python sürümleri arasında taşınabilir hale getirir. PyBind11 ile çalışıyorsanız, bu tanımı eklemeyin, aksi takdirde derleme hatalarını görürsünüz. |
    | **C/C++**  >  **Kod oluşturma** | **Çalışma zamanı kitaplığı** | **Çok iş PARÇACıKLı dll (/MD)** (aşağıdaki uyarıya bakın) |
    | **Bağlayıcı**  >  **Genel** | **Ek kitaplık dizinleri** | Yükleme için uygun şekilde *. lib* dosyaları içeren Python *Kitaplıklar* klasörünü ekleyin (örneğin,) `c:\Python36\libs` . (. Lib *dosyalarını Içeren* *LIB* klasörünü *değil* , *. lib* dosyalarını içeren *LIBS* klasörünü işaret ettiğinizden emin olun.) |

    > [!Tip]
    > Proje özelliklerinde C/C++ sekmesini görmüyorsanız, proje C/C++ kaynak dosyaları olarak tanımladığı herhangi bir dosya içermediği için olur. *. C* veya *. cpp* uzantısı olmadan bir kaynak dosyası oluşturursanız bu durum oluşabilir. Örneğin, `module.coo` `module.cpp` daha önce yeni öğe iletişim kutusu yerine yanlışlıkla girdiyseniz, Visual Studio dosyayı oluşturur ancak dosya türünü "C/C + Code" olarak (c/C++ özellikleri sekmesini etkinleştirir) olarak ayarlar. Bu tür hatalı kimlik, dosyayı ile yeniden adlandırsanız bile durum durumunda kalır `.cpp` . Dosya türünü düzgün bir şekilde ayarlamak için **Çözüm Gezgini** dosyasında dosyaya sağ tıklayın, **Özellikler**' i seçin ve ardından  **dosya türünü** **C/C++ kodu** olarak ayarlayın.

    > [!Warning]
    > Hata ayıklama   >    >  olmayan Python ikililerinin ile oluşturulduğu durum, bu ayar, hata ayıklama yapılandırması için bile C/C++ kod oluşturma **çalışma zamanı kitaplığı** seçeneğini her zaman **çok iş parçacıklı DLL (/MD)** olarak ayarlayın. CPython ile, **çok iş parçacıklı hata ayıklama dll (/MDd)** seçeneğini ayarlamanız durumunda, hata **ayıklama** yapılandırması oluşturmak **C1189, Py_TRACE_REFS ve Py_REF_DEBUG Py_DEBUG uyumlu değildir: Py_LIMITED_API**. Ayrıca, `Py_LIMITED_API` derleme hatasını önlemek için (CPython, PyBind11 değil) öğesini kaldırırsanız, modül içeri aktarmaya çalışırken Python kilitleniyor. (Kilitlenme, DLL 'in `PyModule_Create` , **önemli Python hatası: PyThreadState_Get: geçerli iş parçacığı olmayan** çıkış iletisiyle daha sonra açıklanan çağrısı içinde olur.)
    >
    > /MDd seçeneği, Python hata ayıklama ikililerini (örneğin *python_d.exe*) oluşturmak için kullanılır, ancak uzantı dll 'si için seçilmesi hala derleme hatasına neden olur `Py_LIMITED_API` .

1. C++ projesine sağ tıklayın ve yapılandırmaların ( **hata ayıklama** ve **yayın**) test etmek için **Oluştur** ' u seçin. *. PYD* dosyaları, C++ proje klasörünün kendisi değil, **hata ayıklama** ve **yayın** altındaki **çözüm** klasöründe bulunur.

1. Aşağıdaki kodu C++ projesinin *Module. cpp* dosyasına ekleyin:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Kodunuzun doğru olduğunu onaylamak için C++ projesini tekrar oluşturun.

1. Daha önce yapmadıysanız, aynı içeriğe sahip "superfastcode2" adlı ikinci bir proje oluşturmak için yukarıdaki adımları tekrarlayın.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>C++ projelerini Python için uzantılara Dönüştür

C++ DLL 'yi Python için bir uzantıya dönüştürmek üzere, ilk olarak, içe aktarılmış yöntemleri Python türleriyle etkileşim kuracak şekilde değiştirirsiniz. Daha sonra modül yöntemlerinin tanımlarıyla birlikte modülü dışarı aktaran bir işlev eklersiniz.

Aşağıdaki bölümlerde, bu adımların her ikisi de Cpyıthon uzantılarını ve PyBind11 kullanarak nasıl gerçekleştirileceği açıklanmaktadır.

### <a name="cpython-extensions"></a>Cpyıthon uzantıları

Python 3. x için bu bölümde gösterilmekte olan bir arka plan için, [Python/C API başvurusu el kitabına](https://docs.python.org/3/c-api/index.html) ve Python.org üzerindeki özellikle [Modül nesnelerine](https://docs.python.org/3/c-api/module.html) bakın (doğru belgeleri görüntülemek için sağ üstteki aşağı açılan denetimden Python sürümünüzü seçmenizi unutmayın).

Python 2,7 ile çalışıyorsanız, [C veya C++ Ile python 2,7](https://docs.python.org/2.7/extending/extending.html) ' i genişletmek ve [Python 3 ' e](https://docs.python.org/2.7/howto/cporting.html) (Python.org) uzantı modülleri eklemek için bunun yerine bakın.

1. *Module. cpp*' nin en üstünde *Python. h*' yi ekleyin:

    ```cpp
    #include <Python.h>
    ```

1. Metodu, `tanh_impl` Python türlerini kabul etmek ve döndürmek için değiştirin (a `PyObject*` , yani):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. C++ `tanh_impl` Işlevinin Python 'a nasıl sunulduğunu tanımlayan bir yapı ekleyin:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Özel olarak ifadesini kullanırken, Python kodunuzda başvurmak istediğiniz modülü tanımlayan bir yapı ekleyin `from...import` . ( **Yapılandırma özellikleri**  >  altındaki proje özelliklerinde bu değeri eşleştirin **Genel**  >  **Hedef adı**.) Aşağıdaki örnekte, "superfastcode" modül adı, `from superfastcode import fast_tanh` içinde tanımlandığı Için Python 'da kullanabileceğiniz anlamına gelir `fast_tanh` `superfastcode_methods` . ( *Module. cpp* gibi C++ projesine yönelik dosya adları önemsizdir.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Modül `PyInit_<module-name>` &lt; adının &gt; C++ projesinin **genel**  >  **hedef adı** özelliğiyle tam olarak eşleştiği (yani, proje tarafından oluşturulan *. PYD* dosya adı ile eşleşmesi), adlandırılmış olması gereken modülü yüklediğinde Python tarafından çağrı yaptığı bir yöntem ekleyin.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Kodunuzu doğrulamak için hedef yapılandırmayı **serbest bırakma** ve C++ projesini yeniden derleme olarak ayarlayın. Hatalarla karşılaşırsanız aşağıdaki [sorun giderme](#troubleshooting) bölümüne bakın.

### <a name="pybind11"></a>PyBind11

Önceki bölümde yer alan adımları tamamladıysanız, C++ kodu için gerekli modül yapılarını oluşturmak üzere çok sayıda ortak kod kullanıldığını kesinlikle fark etmiş olursunuz. PyBind11, bir C++ üstbilgi dosyasındaki makroları, çok daha az kodla aynı sonucu gerçekleştiren makrolarla basitleştirir. Bu bölümde gösterilmekte olan arka plan için bkz. [PyBind11 temelleri](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (GitHub.com).

1. PIP: veya kullanarak PyBind11 'i yükler `pip install pybind11` `py -m pip install pybind11` .

1. *Module. cpp*' nin en üstünde, *pybind11. h* öğesini ekleyin:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. *Module. cpp*' nin en altında, `PYBIND11_MODULE` C++ işlevine giriş noktasını tanımlamak için makrosunu kullanın:

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. Kodunuzu doğrulamak için hedef yapılandırmayı **serbest bırakma** ve C++ projesini derleme olarak ayarlayın. Hatalarla karşılaşırsanız sorun giderme konusunda bir sonraki bölüme bakın.

### <a name="troubleshooting"></a>Sorun giderme

C++ modülü aşağıdaki nedenlerden dolayı derlenmeyebilir:

- *Python. h* (**E1696: kaynak dosyası açılamıyor "Python. h"** ve/veya **C1083: içerme dosyası açılamıyor: "Python. h": böyle bir dosya veya dizin yok**): **C/C++**  >  **genel**  >  **ek dahil** , proje özelliklerindeki yolun, Python yüklemenizin *içerme* klasörünü işaret ettiğini doğrulayın. [Core C++ projesi oluşturma](#create-the-core-c-projects)altındaki 6. adıma bakın.

- Python kitaplıkları bulunamıyor: **bağlayıcı**  >    >  , proje özelliklerindeki genel **Ek kitaplık dizinlerindeki** yolun Python yüklemenizin *LIBS* klasörüne işaret ettiğini doğrulayın. [Core C++ projesi oluşturma](#create-the-core-c-projects)altındaki 6. adıma bakın.

- Hedef mimarisiyle ilgili bağlayıcı hataları: C++ hedefinin proje mimarisini Python yüklemenizin ile eşleşecek şekilde değiştirin. Örneğin, C++ projesi ile x64 'u hedefliyorsanız, ancak Python yüklemeniz x86 ise, C++ projesini Target x86 olarak değiştirin.

## <a name="test-the-code-and-compare-the-results"></a>Kodu test edin ve sonuçları karşılaştırın

Dll 'Leri artık Python uzantıları olarak yapılandırılmış olduğuna göre, bu dosyalara Python projesinden başvurabilir, modülleri içeri aktarabilir ve yöntemlerini kullanabilirsiniz.

### <a name="make-the-dll-available-to-python"></a>DLL dosyasını Python için kullanılabilir hale getirme

DLL 'yi Python için kullanılabilir hale getirmek için iki yol vardır.

Python projesi ve C++ projesi aynı çözümde ise, ilk yöntem işe yarar. **Çözüm Gezgini**' e gidin, Python projenizde **Başvurular** düğümüne sağ tıklayın ve ardından **Başvuru Ekle**' yi seçin. Görüntülenen iletişim kutusunda, **Projeler** sekmesini seçin, hem **superfastcode** ve **superfastcode2** projelerini hem de **Tamam**' ı seçin.

![Superfastcode projesine başvuru ekleme](media/cpp-add-reference.png)

Aşağıdaki adımlarda açıklanan alternatif yöntem, modülü genel Python ortamına yükleyerek diğer Python projeleri için de kullanılabilir hale getirir. (Bunu yapmak genellikle Visual Studio 2017 sürüm 15,5 ve önceki sürümlerde bu ortam için IntelliSense tamamlama veritabanını yenilemektir. Modül ortamdan kaldırılırken yenileme de gereklidir.)

1. Visual Studio 2017 veya sonraki bir sürümünü kullanıyorsanız, Visual Studio yükleyicisini çalıştırın, **Değiştir**' i seçin, **tek tek bileşenler**  >  **derleyicileri, derleme araçları ve çalışma zamanları**  >  **Visual C++ 2015,3 v140 araç takımı**' nı seçin. Python (Windows için), Visual Studio 2015 (sürüm 14,0) ile oluşturulmuş olduğundan ve burada açıklanan yöntem aracılığıyla bir uzantı oluşturulurken bu araçların kullanılabilmesini beklediği için bu adım gereklidir. (Python 'un 32 bitlik bir sürümünü yüklemeniz ve DLL 'yi, x64 değil, Win32 'e hedeflemek) gerekebileceğini unutmayın.)

1. C++ projesinde *Setup.py* adlı bir dosya oluşturun ve projeye sağ tıklayıp   >  **Yeni öğe** Ekle ' yi seçin. Ardından **C++ dosyası (. cpp)** öğesini seçin, dosyayı adlandırın `setup.py` ve **Tamam** ' ı seçin (dosyanın *. Kopyala* uzantısıyla adlandırılması, Visual Studio 'nun bunu C++ dosya şablonunu kullanarak Python olarak tanımasını sağlar). Dosya düzenleyicide göründüğünde, uzantı yöntemine uygun şekilde aşağıdaki kodu yapıştırın:

    **CPython uzantıları (superfastcode Projesi):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Bu betik hakkındaki belgeler için bkz. [C ve C++ uzantıları oluşturma](https://docs.python.org/3/extending/building.html) (Python.org).

    **PyBind11 (superfastcode2 Projesi):**

    ```python
    import os, sys

    from distutils.core import setup, Extension
    from distutils import sysconfig

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2', sources = ['module.cpp'],
        include_dirs=['pybind11/include'],
        language='c++',
        extra_compile_args = cpp_args,
        )

    setup(
        name = 'superfastcode2',
        version = '1.0',
        description = 'Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules = [sfc_module],
    )
    ```

1. *Setup.py* kodu, Python 'a, komut satırından kullanıldığında Visual Studio 2015 C++ araç takımını kullanarak uzantıyı oluşturmasını sağlar. Yükseltilmiş bir komut istemi açın, C++ projesini (yani *Setup.py* içeren klasör) içeren klasöre gidin ve aşağıdaki komutu girin:

    ```command
    pip install .
    ```

    veya:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Python 'dan DLL 'i çağırma

Önceki bölümde açıklandığı gibi, DLL dosyasını Python için kullanılabilir hale geçirdikten sonra, `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` Python kodundan ve işlevlerini Python uygulamasıyla de karşılaştırabilirsiniz:

1. Dll 'lerden içe aktarılmış yöntemleri çağırmak ve çıktılarını göstermek için *. Kopyala* dosyanıza aşağıdaki satırları ekleyin:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Python programını **çalıştırın (hata ayıklama**  >  **olmadan Başlat** veya **CTRL** + **F5**) ve C++ yordamlarının Python uygulamasından yaklaşık beş ila yirmi kat daha hızlı çalışacağını gözlemleyin. Tipik çıktı aşağıdaki gibi görünür:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    **Hata ayıklama olmadan Başlat** komutu devre dışıysa, **Çözüm Gezgini** ' de Python projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

1. `COUNT`Farkların daha fazla görünmesi için değişkeni artırmayı deneyin. Hata **ayıklama** derlemesi daha az iyileştirildiğinden ve çeşitli hata denetimleri Içerdiğinden, C++ modülünün **hata ayıklama** derlemesi bir **yayın** yapıından daha yavaş çalışır. Karşılaştırma için bu yapılandırmaların arasında geçiş yapmak ücretsizdir.

> [!NOTE]
> Çıktıda, PyBind11 uzantısının CPython uzantısı kadar hızlı olmadığını, ancak yine de düz Python uygulamasından daha hızlı bir şekilde daha hızlı olduğunu görebilirsiniz. Fark, PyBind11 tarafından C++ arabirimini önemli ölçüde daha kolay hale getirmek için çok az sayıdaki çağrı başına yükün olmamasıdır. Bu çağrı başına fark, gerçekten göz ardı edilebilir: test kodu, 500.000 kez uzantı işlevlerini çağırdığı için, burada gördüğünüz sonuçlar bu ek yükü önemli ölçüde ortadan kaldırır! Genellikle, bir C++ işlevi burada kullanılan önemsiz metotlardan çok daha fazla çalışır `fast_tanh[2]` ve bu durumda ek yük önemli değildir. Ancak, saniyede binlerce kez çağrılabilen Yöntemler gerçekleştiriyorsanız, Cponthon yaklaşımını kullanmak PyBind11 göre daha iyi performans sağlayabilir.

## <a name="debug-the-c-code"></a>C++ kodunda hata ayıklama

Visual Studio, Python ve C++ kod hatalarını birlikte ayıklamayı destekler. Bu bölüm, **superfastcode** projesini kullanarak işlemi adım adım gösterir. adımlar **superfastcode2** projesi için aynıdır.

1. **Çözüm Gezgini**' de Python projesine sağ tıklayın, **Özellikler**' i seçin, **Hata Ayıkla** sekmesini seçin ve ardından hata ayıklama   >  **yerel kod hata ayıklamayı etkinleştir** seçeneğini belirleyin.

    > [!Tip]
    > Yerel kod hata ayıklamasını etkinleştirdiğinizde, bir program her ne kadar her zaman, duraklatmaya **devam etmek için herhangi bir tuşa basmadan** , Python çıkış penceresi hemen kaybolabilir. Bir duraklatma zorlamak için, `-i`   >  yerel kod hata ayıklamasını etkinleştirdiğinizde **hata ayıklama** sekmesindeki **yorumlayıcı bağımsız değişkenlerini** Çalıştır alanına seçeneği ekleyin. Bu bağımsız değişken, kod bittikten sonra Python yorumlayıcısını etkileşimli moda koyar, bu noktada  + çıkmak için CTRL **Z**  >  **ENTER** tuşlarına basmanız önerilir. (Alternatif olarak, Python kodunuzun değiştirilmesini görmüyorsanız `import os` `os.system("pause")` programınızın sonuna ve deyimlerini ekleyebilirsiniz. Bu kod, özgün duraklatma uyarısını çoğaltır.)

1.   >  Özellik değişikliklerini kaydetmek için dosya **Kaydet** ' i seçin.

1. Visual Studio araç çubuğunda derleme yapılandırmasını **hata ayıklama** olarak ayarlayın.

    ![Derleme yapılandırması hata ayıklama olarak ayarlanıyor](media/cpp-set-debug.png)

1. Kod hata ayıklayıcıda genellikle daha uzun sürdüğü için, `COUNT` *. Kopyala* dosyanızdaki değişkeni beş kat daha küçük bir değere değiştirmek isteyebilirsiniz (örneğin, öğesini `500000` olarak değiştirin `100000` ).

1. C++ kodunuzda, yöntemin ilk satırında bir kesme noktası ayarlayın `tanh_impl` ve ardından hata ayıklayıcıyı başlatın (**F5** veya **Debug**  >  **Start Debugging**). Hata ayıklayıcı, bu kod çağrıldığında duraklar. Kesme noktası isabet değilse, yapılandırmanın **hata ayıklama** olarak ayarlandığını ve projeyi kaydettiğinizden (hata ayıklayıcı başlatılırken otomatik olarak gerçekleşmeyecek) emin olun.

    ![C++ kodunda kesme noktasında durdurma](media/cpp-debugging.png)

1. Bu noktada, C++ kodunda ilerleyebileceğiniz gibi değişkenleri inceleyebilir ve bu şekilde devam edebilirsiniz. Bu özellikler, [hata ayıklama C++ ve Python ile birlikte](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)ayrıntılı olarak açıklanmıştır.

## <a name="alternative-approaches"></a>Alternatif yaklaşımlar

Aşağıdaki tabloda açıklandığı gibi Python uzantıları oluşturmak için çeşitli araçlar vardır. Cpıthon ve PyBind11 için ilk iki giriş bu makalede zaten ele alınmıştır.

| Yaklaşım | Vinsat | Temsilci Kullanıcı (ler) | Pro (ler) | Con (ler) |
| --- | --- | --- | --- | --- |
| Cpyıthon için C/C++ uzantı modülleri | 1991 | Standart Kitaplık | [Kapsamlı belge ve öğreticiler](https://docs.python.org/3/c-api/). Toplam denetim. | Derleme, taşınabilirlik, başvuru yönetimi. Yüksek C bilgisi. |
| [PyBind11](https://github.com/pybind/pybind11) (C++ için önerilir) | 2015 |  | Mevcut C++ kodunun Python bağlamalarını oluşturmak için yalnızca hafif ve üst bilgi kitaplığı. Birkaç bağımlılık. PyPy uyumluluğu. | Daha yeni, daha az olgun. C++ 11 özelliklerinin ağır kullanımı. Desteklenen derleyicilerin kısa listesi (Visual Studio dahildir). |
| Cython (C için önerilir) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Python benzeri. Yüksek olgun. Yüksek performans. | Derleme, yeni sözdizimi, yeni araç zinciri. |
| [Boost. Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Yalnızca her C++ derleyicisi ile birlikte kullanılır. | Büyük ve karmaşık kitaplıklar paketi; Eski derleyiciler için birçok geçici çözüm içerir. |
| ctypes | 2003 | [scryptoto](https://github.com/wbond/oscrypto) | Derleme, geniş kullanılabilirlik yok. | C yapılarına erişme ve bunları azaltma ve hataya açıktır. |
| YÜZIK | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Aynı anda birçok dil için bağlama oluşturun. | Python tek hedef ise aşırı yük yükü. |
| cffi | 2013 | [şifreleme](https://cryptography.io/en/latest/), [PyPy](https://pypy.org/) | Tümleştirme kolaylığı, PyPy uyumluluğu. | Daha yeni, daha az olgun. |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | C++ kullanarak cffı 'ye benzer. | Daha yeni bir deyişle VS 2017 ile ilgili bazı sorunlar olabilir. |

## <a name="see-also"></a>Ayrıca bkz.

Bu izlenecek yolda tamamlanan örnek [Python-Samples-vs-cpp-Extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub) üzerinde bulunabilir.
