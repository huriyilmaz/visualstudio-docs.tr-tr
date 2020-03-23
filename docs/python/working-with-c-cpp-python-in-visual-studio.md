---
title: Python için C++ uzantıları yazma
description: Visual Studio, CPython ve PyBind11 kullanarak Python için karışık modhatabing dahil olmak üzere bir C++ uzantısı oluşturma nın bir walkthrough.
ms.date: 11/19/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9c81984e8921e44e32b58ae7f5c5c27c5fe8b12f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62956981"
---
# <a name="create-a-c-extension-for-python"></a>Python için C++ uzantısı oluşturma

C++ (veya C) ile yazılmış modüller, Python yorumlayıcısının yeteneklerini genişletmek ve düşük düzeyli işletim sistemi yeteneklerine erişimi sağlamak için yaygın olarak kullanılır. Üç ana modül türü vardır:

- Hızlandırıcı modülleri: Python yorumlanmış bir dil olduğundan, daha yüksek performans için C++'da belirli kod parçaları yazılabilir.
- Sarmalayıcı modülleri: Varolan C/C++ arabirimlerini Python koduna maruz bırakveya Python'dan kullanımı kolay daha "Pythonik" API'yi ortaya çıkar.
- Düşük düzeyli sistem erişim modülleri: CPython çalışma zamanının, işletim sisteminin veya altta yatan donanımın alt düzey özelliklerine erişmek için oluşturulmuştur.

Bu makalede, cpython için hiperbolik bir teğet hesaplayan ve Python kodundan çağıran bir C++ uzantı modülü oluşturma yoluyla yürür. Yordam, C++'da aynı yordamı uygulamanın göreceli performans kazancını göstermek için ilk olarak Python'da uygulanır.

Bu makalede, C++ Python için kullanılabilir hale getirmek için iki yol da göstermektedir:

- [Python belgelerinde](https://docs.python.org/3/c-api/) açıklandığı gibi standart CPython uzantıları
- [PyBind11](https://github.com/pybind/pybind11), sadeliği nedeniyle C++ 11 için tavsiye edilir.

Bu makalenin sonunda [alternatif yaklaşımlar](#alternative-approaches) altında bu ve diğer araçlar arasında bir karşılaştırma bulunur.

Bu izlenecek yoldan tamamlanan örnek [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub) bulunabilir.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017 veya daha sonra hem **C++ ile Masaüstü Geliştirme** hem de Varsayılan seçeneklerle yüklü **Python Geliştirme** iş yükleri.
- Python **Geliştirme** iş yükünde, Python yerel **geliştirme araçları**için sağdaki kutuyu da seçin. Bu seçenek, bu makalede açıklanan yapılandırmanın çoğunu ayarlar. (Bu seçenek, C++ iş yükünü de otomatik olarak içerir.)

    ![Python yerel geliştirme araçları seçeneğini seçme](media/cpp-install-native.png)

    > [!Tip]
    > Veri **bilimi ve analitik uygulamalar** iş yükünü yüklemek, Python ve **Python yerel geliştirme araçları** seçeneğini de içerir.

Daha fazla bilgi için Visual Studio'nun diğer sürümlerini kullanma da dahil olmak üzere [Visual Studio için Python yükle'sini yükleyin](installing-python-support-in-visual-studio.md)bölümüne bakın. Python'u ayrı olarak yüklerseniz, hata **ayıklama sembollerini karşıdan yükleme** ve yükleyicide **Gelişmiş Seçenekler** altında **hata ayıklama ikililerini karşıdan yükleme** seçeneğini seçtiğinizden emin olun. Bu seçenek, hata ayıklama oluşturmayı seçerseniz, gerekli hata ayıklama kitaplıklarına sahip olduğunuzu sağlar.

## <a name="create-the-python-application"></a>Python uygulamasını oluşturma

1. **Dosya** > **Yeni** > **Projesi'ni**seçerek Visual Studio'da yeni bir Python projesi oluşturun. "Python"u arayın, **Python Application** şablonunu seçin, uygun bir ad ve konum verin ve **Tamam'ı**seçin.

1. C++ ile çalışmak için 32 bit Python yorumlayıcısı kullanmanız gerekir (Python 3.6 veya üzeri önerilir). Visual **Studio'nun Çözüm Gezgini** penceresinde proje düğümünün genişletilmesini ve **Python Ortamları** düğümünün genişletilmesi. 32 bitlik bir ortamı varsayılan olarak görmüyorsanız (kalın veya genel **varsayılan**olarak etiketlenmiş), [proje için Python ortamı nı seçin'deki](selecting-a-python-environment-for-a-project.md)yönergeleri izleyin. Yüklü 32 bit bir yorumlayıcınız yoksa, [bkz.](installing-python-interpreters.md)

1. Projenin *.py* dosyasında, hiperbolik bir teğetin hesaplanmasını karşılaştıran (daha kolay karşılaştırma için matematik kitaplığını kullanmadan uygulanan) aşağıdaki kodu yapıştırın. [Python düzenleme özelliklerinden](editing-python-code-in-visual-studio.md)bazılarını deneyimlemek için kodu el ile girmekten çekinmeyin.

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

1. Sonuçları görmek için Hata Ayıklama **(Ctrl**+**F5)** olmadan **Hata Ayıklama** > **Başlat'ı** kullanarak programı çalıştırın. Kıyaslama `COUNT` çalışması nın ne kadar süreceğini değiştirmek için değişkeni ayarlayabilirsiniz. Bu gözden geçirme nin amaçları için, sayım yaklaşık iki saniye sürecek şekilde saymayı ayarlayın.

> [!TIP]
> Kıyaslama ları çalıştırırken, Visual Studio hata ayıklayıcıiçinde kod çalıştırırken oluşan genel giderleri önlemek için hata**ayıklama yapmadan** **hata** > ayıklama yı her zaman kullanın.

## <a name="create-the-core-c-projects"></a>Çekirdek C++ projelerini oluşturma

"Superfastcode" ve "superfastcode2" adlı iki özdeş C++ projesi oluşturmak için bu bölümdeki yönergeleri izleyin. Daha sonra her projede C++ kodunu Python'a maruz bırakmak için farklı araçlar kullanırsınız.

1. Ortam değişkeninin `PYTHONHOME` kullanmak istediğiniz Python yorumlayıcısına ayarlandığınızdan emin olun. Visual Studio'daki C++ projeleri python uzantısı oluştururken kullanılan *python.h*gibi dosyaları bulmak için bu değişkene güvenir.

1. **Solution Explorer'da** çözüme sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin. Visual Studio çözümü hem Python hem de C++ projelerini birlikte içerebilir (Python için Visual Studio kullanmanın avantajlarından biridir).

1. "C++"da arama yapın, **Boş projeyi**seçin, ikinci proje için "superfastcode" ("superfastcode2" adını belirtiniz) ve **Tamam'ı**seçin.

    > [!Tip]
    > Visual Studio'da yüklü **olan Python yerel geliştirme araçlarıyla,** aşağıda açıklananların çoğuna sahip olan Python **Uzantı Modülü** şablonuyla başlayabilirsiniz. Bu walkthrough için, ancak, boş bir proje ile başlayan adım adım uzatma modülü bina gösterir. İşlemi anladıktan sonra şablon, kendi uzantılarınızı yazarken size zaman kazandırır.

1. **Kaynak Dosyalar** düğümüne sağ tıklayarak yeni projede bir C++ dosyası oluşturun, ardından**Yeni Öğe** `module.cpp` **Ekle'yi** > seçin, **C++ Dosyasını**seçin, adlandırın ve **Tamam'ı**seçin.

    > [!Important]
    > *.cpp* uzantılı bir dosya, izleyen adımlardaki C++ özellik sayfalarını açmak için gereklidir.

1. **Çözüm Gezgini'nde**C++ projesine sağ tıklayın, **Özellikler'i**seçin.

1. Görünen **Özellik Sayfaları** iletişim kutusunun üst kısmında, **Yapılandırmayı** **Tüm Yapılandırmalar** ve **Platform** için **Win32**olarak ayarlayın.

1. Aşağıdaki tabloda açıklandığı gibi belirli özellikleri ayarlayın, sonra **Tamam'ı**seçin.

    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Genel** > **Hedef Adı** | Python'dan başvurmak istediğiniz şekilde modülün adını ifadelerde `from...import` belirtin. Python için modülü tanımlarken C++'da aynı adı kullanırsınız. Projenin adını modül adı olarak kullanmak istiyorsanız, varsayılan değeri **$(ProjectName)** bırakın. |
    | | **Genel** > **Hedef Uzantısı** | **.pyd** |
    | | **Proje Varsayılan yapılandırma** > **türü** | **Dinamik Kitaplık (.dll)** |
    | **C/C++** > **Genel** | **Ek Dahil Dizinler** | Python *ekle* klasörünü yüklemenize uygun olarak `c:\Python36\include`ekleyin, örneğin.  |
    | **C/C++** > **Ön işlemci** | **Önişlemci Tanımları** | **Yalnızca CPython** `Py_LIMITED_API;` : dize başına ekleyin (semicolon dahil). Bu tanım, Python'dan arayaabileceğiniz bazı işlevleri kısıtlar ve kodu Python'un farklı sürümleri arasında daha taşınabilir hale getirir. PyBind11 ile çalışıyorsanız, bu tanımı eklemeyin, aksi takdirde yapı hataları görürsünüz. |
    | **C/C++** > **Kod Oluşturma** | **Çalışma Zamanı Kitaplığı** | **Çok iş parçacığı DLL (/MD)** (aşağıdaki Uyarı'ya bakın) |
    | **Linker** > **Genel** | **Ek Kütüphane Dizinleri** | Yüklemeniz için uygun *.lib* dosyaları içeren Python *libs* `c:\Python36\libs`klasörünü ekleyin, örneğin. *(.py* dosyaları içeren *Lib* klasörünü *değil.lib* *not* dosyalarını içeren *libs* klasörünü işaret etmeyi unutmayın.) |

    > [!Tip]
    > Proje özelliklerinde C/C++ sekmesini görmüyorsanız, bunun nedeni projenin C/C++ kaynak dosyaları olarak tanımladığı dosyaları içermemesidir. *.c* veya *.cpp* uzantısı olmayan bir kaynak dosya oluşturursanız bu durum oluşabilir. Örneğin, yeni öğe `module.coo` iletişim `module.cpp` kutusu yerine yanlışlıkla girdiyseniz, Visual Studio dosyayı oluşturur, ancak dosya türünü C/C++ özellikleri sekmesini etkinleştiren "C/C+ Kodu" olarak ayarlamaz. Bu tür yanlış tanımlama, dosyayı `.cpp`yeniden adlandırsanız bile durum devam eder. Dosya türünü düzgün ayarlamak **için, Solution Explorer'da**dosyayı sağ tıklatın, **Özellikler'i**seçin, ardından **Dosya Türünü** **C/C++ Kodu'na**ayarlayın.

    > [!Warning]
    > Hata ayıklama yapılandırması için bile **C/C++** > **Kod Oluşturma** > **Çalışma Zamanı Kitaplığı** seçeneğini her zaman hata ayıklama yapılandırmasına **(/MD)** ayarlayın, çünkü bu ayar hata ayıklama olmayan Python ikililerinin oluşturduğu şeydir. CPython ile, Çok iş **parçacığı hata ayıklama DLL (/MDd)** seçeneğini ayarlarsanız, **Hata Ayıklama** yapılandırması oluşturmak **C1189 hatası üretir: Py_LIMITED_API Py_DEBUG, Py_TRACE_REFS ve Py_REF_DEBUG ile uyumsuzdur.** Ayrıca, yapı hatasını önlemek için (CPython ile gerekli olan, ancak PyBind11 ile değil) kaldırırsanız, `Py_LIMITED_API` Python modülü almaya çalışırken çöker. (Kilitlenme, DLL'nin daha `PyModule_Create` sonra açıklandığı gibi, Fatal Python hatasının çıktı iletisi ile birlikte **gerçekleşir: PyThreadState_Get: geçerli iş parçacığı yoktur**.)
    >
    > /MDd seçeneği Python hata ayıklama ikilileri oluşturmak için kullanılır *(python_d.exe*gibi), ancak bir uzantısı DLL için seçerek hala yapı hatası neden `Py_LIMITED_API`olur .

1. C++ projesine sağ tıklayın ve yapılandırmalarınızı test etmek için **Yapı'yı** seçin (hem **Hata Ayıklama** hem de **Sürüm).** *.pyd* dosyaları **Hata Ayıklama** ve **Serbest Bırakma**altındaki **çözüm** klasöründe yer alır, C++ proje klasöründe değil.

1. C++ projesinin *module.cpp* dosyasına aşağıdaki kodu ekleyin:

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

1. Kodunuzun doğru olduğunu doğrulamak için C++ projesini yeniden oluşturun.

1. Bunu daha önce yapmadıysanız, aynı içeriklere sahip "superfastcode2" adlı ikinci bir proje oluşturmak için yukarıdaki adımları yineleyin.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>C++ projelerini Python uzantılarına dönüştürme

C++ DLL'yi Python için bir uzantı haline getirmek için, önce dışa aktarılan yöntemleri Python türleri ile etkileşimde bulunmak üzere değiştirirsiniz. Daha sonra modülü dışa aktaran bir işlev ve modül yöntemlerinin tanımlarını eklersiniz.

İzleyen bölümler, hem CPython uzantılarını hem de PyBind11'i kullanarak bu adımların nasıl gerçekleştirildiğini açıklar.

### <a name="cpython-extensions"></a>CPython uzantıları

Python 3.x için bu bölümde gösterilenler hakkında bilgi almak için, [Python/C API Başvuru Kılavuzu'na](https://docs.python.org/3/c-api/index.html) ve özellikle [python.org'daki Modül Nesneleri'ne](https://docs.python.org/3/c-api/module.html) bakın (Python'un sürümünü sağ üstteki açılır denetimden doğru belgeleri görüntülemek için seçmeyi unutmayın).

Python 2.7 ile çalışıyorsanız, bunun yerine [C veya C++ ile Python 2.7'yi genişletme](https://docs.python.org/2.7/extending/extending.html) ve [Uzantı Modüllerini Python 3'e (python.org) taşımaya](https://docs.python.org/2.7/howto/cporting.html) bakın.

1. *Module.cpp'nin*üst kısmında *Python.h*bulunmaktadır:

    ```cpp
    #include <Python.h>
    ```

1. Python `tanh_impl` türlerini kabul etmek ve `PyOjbect*`döndürmek için yöntemi değiştirin (a , yani):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. C++ `tanh_impl` işlevinin Python'a nasıl sunulduğunu tanımlayan bir yapı ekleyin:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Özellikle deyimi kullanırken Python kodunuzda modülü başvurmak istediğiniz şekilde tanımlayan bir `from...import` yapı ekleyin. (Yapılandırma **Özellikleri** > **Genel** > **Hedef Adı**altında proje özelliklerindeki değeri eşleştirin.) Aşağıdaki örnekte, "superfastcode" modül adı Python'da kullanabileceğiniz `from superfastcode import fast_tanh` anlamına gelir, çünkü `fast_tanh` . `superfastcode_methods` (C++ projesinin dahili dosya adları, *module.cpp*gibi, önemsizdir.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Python'un modülü yüklerken çağırdığı ve `PyInit_<module-name>` &lt;modül adı verilmesi gereken&gt; ve modül adının C++ projesinin **Genel** > **Hedef Adı** özelliğiyle tam olarak eşleştiği (diğer bir şekilde proje tarafından oluşturulmuş *.pyd'nin* dosya adıile eşleştiği) bir yöntem ekleyin.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Kodunuzu doğrulamak için hedef yapılandırmayı **Serbest Bırakma** ve C++ projesini yeniden oluşturmaya ayarlayın. Hatalarla karşılaşırsanız, aşağıdaki [Sorun Giderme](#troubleshooting) bölümüne bakın.

### <a name="pybind11"></a>PyBind11

Önceki bölümdeki adımları tamamladıysanız, C++ kodu için gerekli modül yapılarını oluşturmak için çok sayıda ortak kodu kullandığınızı kesinlikle fark etmişsinizdir. PyBind11, c++ üstbilgi dosyasındaki makrolar aracılığıyla işlemi basitleştirir ve aynı sonucu çok daha az kodla gerçekleştirir. Bu bölümde gösterilenler hakkında bilgi için [Bkz. PyBind11 temelleri](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com).

1. Pip kullanarak PyBind11 `pip install pybind11` `py -m pip install pybind11`yükleyin: veya .

1. *Module.cpp*üst kısmında, *pybind11.h*içerir:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. *module.cpp'nin*alt kısmında, `PYBIND11_MODULE` C++ fonksiyonunun giriş noktasını tanımlamak için makroyu kullanın:

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

1. Hedef yapılandırmayı **Serbest Bırakma** ve kodunuzu doğrulamak için C++ projesini oluşturmaya ayarlayın. Hatalarla karşılaşırsanız, sorun giderme yle ilgili bir sonraki bölüme bakın.

### <a name="troubleshooting"></a>Sorun giderme

C++ modülü aşağıdaki nedenlerden dolayı derlemeyi başaramayabilir:

- *Python.h'yi* bulamıyor (**E1696: kaynak dosyasını açamamak "Python.h"** ve/veya **C1083: Dosyayı açamazsınız: "Python.h": Böyle bir dosya veya dizin yok):** Proje özelliklerindeki **C/C++** > **Ek** > **Ek Dizinlerdeki** yolun Python yüklemenizin *dahil* klasörüne işaret ettiğini doğrulayın. Çekirdek C++ projesini oluştur'un altındaki adım [6'ya](#create-the-core-c-projects)bakın.

- Python kitaplıklarını bulamıyoruz: **Proje** > **General** > özelliklerindeki Bağlantı Genel**Ek Kitaplık Dizinleri'ndeki** yolun Python yüklemenizin *libs* klasörünü işaret ettiğini doğrulayın. Çekirdek C++ projesini oluştur'un altındaki adım [6'ya](#create-the-core-c-projects)bakın.

- Hedef mimariyle ilgili bağlayıcı hataları: C++ hedefinin proje mimarisini Python yüklemenizinkiyle eşleşecek şekilde değiştirin. Örneğin, C++ projesiyle x64'u hedefliyorsanız ancak Python yüklemeniz x86 ise C++ projesini x86'yı hedef alacak şekilde değiştirin.

## <a name="test-the-code-and-compare-the-results"></a>Kodu test edin ve sonuçları karşılaştırın

Artık Python uzantıları olarak yapılandırılan DL'ler olduğuna göre, Python projesinden bunlara başvurabilir, modülleri içe aktarabilir ve yöntemlerini kullanabilirsiniz.

### <a name="make-the-dll-available-to-python"></a>DLL'yi Python için kullanılabilir hale getirin

DLL'yi Python'da kullanılabilir hale getirmenin iki yolu vardır.

Python projesi ve C++ projesi aynı çözümdeyse ilk yöntem çalışır. Solution **Explorer'a**gidin, Python projenizdeki **Başvuru** düğümüne sağ tıklayın ve ardından **Başvuru Ekle'yi**seçin. Görünen iletişim kutusunda **Projeler** sekmesini seçin, hem **superfastcode** hem de **superfastcode2** projelerini seçin ve ardından **Tamam'ı**seçin.

![Superfastcode projesine başvuru ekleme](media/cpp-add-reference.png)

Aşağıdaki adımlarda açıklanan alternatif yöntem, modülü genel Python ortamına yükleyerek diğer Python projelerine de kullanılabilir hale getirir. (Bunu yapmak genellikle Visual Studio 2017 sürüm 15.5 ve daha önceki ortam için IntelliSense tamamlama veritabanını yenilemenizi gerektirir. Modülü ortamdan çıkarırken yenileme de gereklidir.)

1. Visual Studio 2017 veya daha sonra kullanıyorsanız, Visual Studio yükleyicisini çalıştırın, **Değiştir'i**seçin, **Bireysel Bileşenler** > **Derleyicileri seçin, araçlar oluşturun ve çalışma saatleri** > **Visual C++ 2015.3 v140 araç seti**. Python (Windows için) Visual Studio 2015 (sürüm 14.0) ile oluşturulmuş olduğundan ve bu araçların burada açıklanan yöntem aracılığıyla bir uzantı oluşturulurken kullanılabilir olmasını beklediğinden bu adım gereklidir. (Python'un 32 bit sürümünü yüklemeniz ve DLL'yi x64 değil Win32'ye hedeflemeniz gerekebileceğini unutmayın.)

1. Projeye sağ tıklayarak ve**Yeni Öğe** **Ekle'yi** > seçerek C++ projesinde *setup.py* adlı bir dosya oluşturun. Ardından **C++ Dosyası (.cpp)** seçeneğini `setup.py`seçin, dosyayı adlandırın ve **Tamam'ı** seçin (dosyayı *.py* uzantısı ile adlandırmak Visual Studio'nun C++ dosya şablonunu kullanmasına rağmen dosyayı Python olarak tanımasını sağlar). Dosya düzenleyicide göründüğünde, uzantı yöntemine uygun olarak aşağıdaki kodu yapıştırın:

    **CPython uzantıları (superfastcode projesi):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Bu komut dosyasındaki belgeler için [C ve C++ uzantıları](https://docs.python.org/3/extending/building.html) oluşturma (python.org) yazısına bakın.

    **PyBind11 (superfastcode2 projesi):**

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

1. *setup.py* kodu, Python'a komut satırından kullanıldığında Visual Studio 2015 C++ araç kümesini kullanarak uzantıyı oluşturmasını bildirir. Yükseltilmiş bir komut istemi açın, C++ projesini içeren klasöre gidin (diğer bir *setup.py)* klasöre gidin ve aşağıdaki komutu girin:

    ```command
    pip install .
    ```

    veya:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Python'dan DLL'yi arayın

DLL'yi önceki bölümde açıklandığı gibi Python'da kullanıma sunduktan `superfastcode.fast_tanh` sonra, artık Python kodundan ve işlevlerini arayabilir ve `superfastcode2.fast_tanh2` performanslarını Python uygulamasıyla karşılaştırabilirsiniz:

1. DL'lerden dışa aktarılan yöntemleri aramak ve çıktılarını görüntülemek için *.py* dosyanıza aşağıdaki satırları ekleyin:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Python programını çalıştırın **(Hata Ayıklama veya** **Ctrl**+**F5**olmadan Hata**Ayıklama** > Başlat) ve C++ yordamlarının Python uygulamasından yaklaşık beş ila yirmi kat daha hızlı çalışmasını gözlemleyin. Tipik çıktı aşağıdaki gibi görünür:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Hata **Ayıklama olmadan Başlat** komutu devre dışı bırakılırsa, **Solution Explorer'daki** Python projesini sağ tıklatın ve Başlangıç Projesi **olarak ayarla'yı**seçin.

1. Farklar `COUNT` daha belirgin olacak şekilde değişkeni artırmayı deneyin. Hata Ayıklama **yapısı** daha az optimize olduğundan ve çeşitli hata denetimleri içerdiğinden, C++ modülünün **hata ayıklama** yapısı da **Sürüm** yapısından daha yavaş çalışır. Karşılaştırma için bu yapılandırmalar arasında geçiş yapmakiçin çekinmeyin.

> [!NOTE]
> Çıktıda, PyBind11 uzantısı cpython uzantısı kadar hızlı olmadığını görebilirsiniz, ancak düz Python uygulamasından önemli ölçüde daha hızlıdır. Aradaki fark, PyBind11'in C++ arabirimini önemli ölçüde daha basit hale getirmek için sunduğu az miktardaki çağrı başına yükünden kaynaklanmaktadır. Bu çağrı başına fark aslında oldukça önemsizdir: test kodu uzantı işlevlerini 500.000 kez aradığı için, burada gördüğünüz sonuçlar bu yükü büyük ölçüde yükseltebilir! Genellikle, bir C++ işlevi burada kullanılan `fast_tanh[2]` önemsiz yöntemlerden çok daha fazla iş yapar ve bu durumda ek yükü önemsizdir. Ancak, saniyede binlerce kez çağrılabilecek yöntemler uyguluyorsanız, CPython yaklaşımını kullanmak PyBind11'den daha iyi performansa neden olabilir.

## <a name="debug-the-c-code"></a>C++ kodunu hata ayıklama

Visual Studio, Python ve C++ kodunu birlikte hata ayıklamayı destekler. Bu **bölüm, superfastcode** projesini kullanarak işlem boyunca yürür; adımlar **superfastcode2** projesi için aynıdır.

1. **Solution Explorer'da**Python projesine sağ tıklayın, **Özellikler'i**seçin, **Hata Ayıklama** sekmesini seçin ve ardından hata **ayıklama** > yerel**kodu hata ayıklama** seçeneğini seçin.

    > [!Tip]
    > Yerel kod hata ayıklamaetkinleştirdiğinizde, Python çıkış penceresi, program tamamlandığında size her zamanki **basın tuşunu** vermeden duraklatmaya devam etmek için hemen kaybolabilir. Duraklatma zorlamak için, yerel kod hata `-i` ayıklama etkinleştirdiğinizde Hata **Ayıklama** sekmesinde**Yorumlayıcı Bağımsız Değişkenler** **çalıştır** > seçeneği ekleyin. Bu bağımsız değişken, Python yorumlayıcısını kod bittikten sonra etkileşimli moda sokar ve bu noktada çıkmak için **Ctrl**+**Z** > **Enter** tuşuna basmanızı bekler. (Alternatif olarak, Python kodunuzu değiştirmenin sakıncası yoksa, `import os` `os.system("pause")` programın sonuna ek ve ekstreler ekleyebilirsiniz. Bu kod özgün duraklatma istemini yineler.)

1. Özellik değişikliklerini kaydetmek için **Dosya** > **Kaydet'i** seçin.

1. Yapı yapılandırmasını Visual Studio araç çubuğunda **Hata Ayıklama** olarak ayarlayın.

    ![Yapı yapılandırmasını Hata Ayıklama olarak ayarlama](media/cpp-set-debug.png)

1. `COUNT` Kod genellikle hata ayıklayıcıda çalıştırılabilmek daha uzun sürdüğünden, *.py* dosyanızdaki değişkeni yaklaşık beş kat daha küçük bir `500000` `100000`değerle değiştirmek isteyebilirsiniz (örneğin, hata ayıklayıcıdan değiştirin).

1. C++ `tanh_impl` kodunuzda, yöntemin ilk satırında bir kesme noktası ayarlayın ve hata ayıklayıcıyı **(F5** veya Hata >  **Ayıklama****Hata Ayıklama Başlatma) başlatın.** Hata ayıklayıcı, kod çağrıldığında durur. Kesme noktası isabet edilmezse, yapılandırmanın **Hata Ayıklama** olarak ayarlanıp ayarlanmadığını ve projeyi kaydettiğinizi (hata ayıklayıcıyı başlatırken otomatik olarak gerçekleşmez) denetleyin.

    ![C++ kodunda bir kesme noktasında durma](media/cpp-debugging.png)

1. Bu noktada C++ koduna basabilir, değişkenleri inceleyebilir ve böylece devam edebilirsiniz. Bu özellikler [Hata Ayıklama C++ ve Python'da birlikte](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)ayrıntılı olarak açıklanmaktadır.

## <a name="alternative-approaches"></a>Alternatif yaklaşımlar

Aşağıdaki tabloda açıklandığı gibi Python uzantıları oluşturmak için çeşitli araçlar vardır. CPython ve PyBind11 için ilk iki girişleri zaten bu makalede ele alınmıştır.

| Yaklaşım | Vintage | Temsilci kullanıcı(lar) | Pro(lar) | Con(lar) |
| --- | --- | --- | --- | --- |
| CPython için C/C++ uzantı modülleri | 1991 | Standart Kitaplık | [Kapsamlı belgeler ve öğreticiler](https://docs.python.org/3/c-api/). Tam kontrol. | Derleme, taşınabilirlik, referans yönetimi. Yüksek C bilgisi. |
| [PyBind11](https://github.com/pybind/pybind11) (C++için önerilir) | 2015 |  | Varolan C++ kodunun Python bağlamalarını oluşturmak için yalnızca üstbilgi için hafif, üstbilgi kitaplığı. Birkaç bağımlılık. PyPy uyumluluğu. | Daha yeni, daha az olgun. C++11 özelliklerinin yoğun kullanımı. Desteklenen derleyicilerin kısa listesi (Visual Studio dahildir). |
| Cython (C için önerilir) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Python gibi. Son derece olgun. Yüksek performans. | Derleme, yeni sözdizimi, yeni araç zinciri. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Hemen hemen her C++ derleyicisi ile çalışır. | Büyük ve karmaşık kütüphaneler paketi; eski derleyiciler için birçok geçici çözüm içerir. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Derleme yok, geniş kullanılabilirlik. | C yapılarına erişim ve mutasyona uğrama sıcak ve hataya yatkın. |
| Yu -dum | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Aynı anda birçok dil için bağlamalar oluşturun. | Python tek hedef ise aşırı yükü. |
| cffi | 2013 | [kriptografi](https://cryptography.io/en/latest/), [pypy](https://pypy.org/) | Entegrasyon kolaylığı, PyPy uyumluluğu. | Daha yeni, daha az olgun. |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | C++'ı kullanarak cffi'ye benzer. | Yeni, VS 2017 ile ilgili bazı sorunlar olabilir. |

## <a name="see-also"></a>Ayrıca bkz.

Bu izlenecek yoldan tamamlanan örnek [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub) bulunabilir.
