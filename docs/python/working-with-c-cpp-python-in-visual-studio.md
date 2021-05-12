---
title: Python için C++ uzantıları yazma
description: Karma mod hata ayıklama dahil olmak üzere Visual Studio, CPython ve PyBind11 kullanarak Python için C++ uzantısı oluşturma adım adım kılavuz.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 286d5f2c316379316b1a1cf55334cab39cdc247c
ms.sourcegitcommit: 69256dc47489853dc66a037f5b0c1275977540c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2021
ms.locfileid: "109782640"
---
# <a name="create-a-c-extension-for-python"></a>Python için C++ uzantısı oluşturma

C++ (veya C) ile yazılmış modüller genellikle Python yorumlayıcının özelliklerini genişletmek ve alt düzey işletim sistemi özelliklerine erişimi etkinleştirmek için kullanılır. Üç temel modül türü vardır:

- Hızlandırıcı modülleri: Python yorumlanır bir dil olduğundan, daha yüksek performans için C++ dilinde belirli kod parçaları yazabilir.
- Sarmalayıcı modülleri: Mevcut C/C++ arabirimlerini Python koduna veya Python'dan kullanımı kolay bir "Pythonic" API'sini ortaya çıkarma.
- Düşük düzeyli sistem erişim modülleri: çalışma zamanının, işletim sisteminin veya temel alınan donanımın alt düzey `CPython` özelliklerine erişmek için oluşturulur.

Bu makalede, hiperbolik tanjı hesaplarak Python kodundan çağıran bir C++ uzantısı `CPython` modülü oluşturma hakkında bilgi edinebilirsiniz. Yordam, C++ dilinde aynı yordamı uygulamanın göreli performans kazancını göstermek için ilk olarak Python'da uygulanır.

Bu makalede ayrıca C++ kodunu Python'da kullanılabilir hale etmenin iki yolu da açıklanmıştır:

- Python `CPython` belgelerinde açıklandığı gibi standart [uzantılar](https://docs.python.org/3/c-api/)
- [Basitliği nedeniyle](https://github.com/pybind/pybind11)C++ 11 için önerilen PyBind11.

Bu kılavuzdan tamamlanmış örnek [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub) üzerinde bulunabilir.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio C++ iş yükünü ve yerel uzantılar için gerekli araç takımlarını getiren **Python** yerel geliştirme araçları dahil olmak üzere **Python** Geliştirme iş yükü yüklü 2017 veya sonraki bir sürümü içerir.

    ![Python yerel geliştirme araçları seçeneğini seçme](media/cpp-install-native.png)

    > [!Tip]
    > Veri bilimi **ve analitik uygulamalar iş yükünü yüklemek** varsayılan olarak Python ve Python yerel geliştirme **araçları** seçeneğini de içerir.

Yükleme seçenekleri hakkında daha fazla bilgi için bkz. Visual Studio için [Python desteğini yükleme.](installing-python-support-in-visual-studio.md) Python 'u ayrı olarak yüklerseniz, yükleyicisindeki **Gelişmiş Seçenekler** altında **hata ayıklama sembollerini indir** ' i seçtiğinizden emin olun. Bu seçenek, Python kodunuz ve yerel kodunuz arasında karışık modda hata ayıklama kullanmak için gereklidir.

## <a name="create-the-python-application"></a>Python uygulaması oluşturma

1. **Dosya**  >  **Yeni**  >  **Proje**' ye tıklayarak Visual Studio 'da yeni bir Python projesi oluşturun. "Python" araması yapın, **Python uygulama** şablonunu seçin, seçtiğiniz bir ad ve konum verin ve **Tamam**' ı seçin.

1. Projenin *. Kopyala* dosyasında, aşağıdaki kodu yapıştırın (veya [Python 'u düzenleyen özelliklerden](editing-python-code-in-visual-studio.md)bazılarını yaşamak için el ile girin). Bu kod, matematik kitaplığını kullanmadan bir hiperbolik tanjantı hesaplar ve yerel uzantılara göre hızlandıracağız.

    > [!Tip]
    > C++ ' da yeniden yazmadan önce kodunuzu saf Python 'da yazın. Bu şekilde, yerel kodunuzun doğru olup olmadığını daha kolay denetleyebilirsiniz

    ```python
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = [(random() - 0.5) * 3 for _ in range(COUNT)]

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

"Superfastcode" ve "superfastcode2" adlı iki özdeş C++ projesi oluşturmak için bu bölümdeki yönergeleri izleyin. Daha sonra, her bir projede C++ kodunu Python 'da göstermek için iki farklı yaklaşım kullanacaksınız.

1. **Çözüm Gezgini** çözüme sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin. Visual Studio çözümü, hem Python hem de C++ projelerini birlikte içerebilir (Python için Visual Studio kullanmanın avantajlarından biridir).

1. "C++" araması yazın, Boş proje'yi **seçin,**"superfastcode" adını ("ikinci proje için superfastcode2" ) belirtin ve Tamam'ı **seçin.**

    > [!Tip]
    > Visual Studio'de Python yerel geliştirme araçları yüklü olarak, aşağıda açıklananların büyük bir'lerini içeren **Python** Uzantısı Modülü şablonuyla başlayabilirsiniz.  Ancak bu izlenecek yol için boş bir projeyle başlayarak uzantı modülünün adım adım nasıl ekli olduğunu göstereceğiz. Süreci anlasanız, şablon kendi uzantılarınızı yazarken size zaman kazandırır.

1. Kaynak Dosyalar düğümüne sağ tıklayarak yeni projede  bir C++ dosyası oluşturun, ardından Yeni Öğe Ekle'yi seçin, C++ Dosyası'nın adını ve  >    `module.cpp` Tamam'ı **seçin.**

    > [!Important]
    > Aşağıdaki adımlarda C++ özellik sayfalarını açmak için *.cpp* uzantısına sahip bir dosya gereklidir.

1. 64 bit Python çalışma zamanı kullanıyorsanız ana araç çubuğundaki açılan menüyü kullanarak **x64** yapılandırmasını etkinleştirin. 32 bit Python çalışma zamanı için **Win32 yapılandırmasını** etkinleştirin.

1. içinde C++ projesine sağ tıklayın ve **Çözüm Gezgini'yi** **seçin.** Yapılandırma değeri **Etkin** **(Hata Ayıklama)** olmalı ve önceki adımda seçiminize bağlı olarak **Platform** Etkin **(x64)** veya Etkin **(Win32)** olur.

    > [!Tip]
    > Kendi projeleriniz için hem Hata Ayıklama hem de Yayın yapılandırmalarını yapılandırmanız gerekir. Burada yalnızca Hata Ayıklama yapılandırmasını yapılandırıyoruz ve  onaylar dahil olmak üzere C++ çalışma zamanının bazı hata ayıklama özelliklerini devre dışı bırakan bir yayın `CPython` derlemesi kullanmak üzere ayarlamış oluyoruz. Hata `CPython` *ayıklama ikilileri* ( `python_d.exe` ) farklı ayarlar gerektirir.

1. Aşağıdaki tabloda açıklandığı gibi belirli özellikleri ayarlayın ve Tamam'ı **seçin.**
    ::: moniker range=">=vs-2019"
    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Hedef Adı** | Deyiminde Python'dan başvurmak istediğiniz modülün adını `from...import` belirtin. Python için modülü tanımlarken C++ içinde de aynı adı kullanırız. Projenin adını modül adı olarak kullanmak istiyorsanız, **$ (ProjectName)** varsayılan değerini bırakın. İçin `python_d.exe` , `_d` adının sonuna ekleyin. |
    | | **Yapılandırma türü** | **Dinamik kitaplık (. dll)** |
    | **Gelişmiş** | **Hedef dosya uzantısı** | **. PYD** |
    | **C/C++** > **Genel** | **Ek Içerme dizinleri** | Yükleme için uygun şekilde Python *içerme* klasörünü (örneğin,) ekleyin `c:\Python36\include` .  |
    | **C/C++** > **Önişlemci** | **Önişlemci tanımları** | Varsa, hata ayıklama sürümü olmayan sürümüyle eşleşecek şekilde **_DEBUG** değerini **ndebug** olarak değiştirin `CPython` . (Kullanırken `python_d.exe` , bunu değiştirmeden bırakın.) |
    | **C/C++** > **Kod oluşturma** | **Çalışma zamanı kitaplığı** | **Çok iş PARÇACıKLı dll (/MD)** , hata ayıklama sürümü olmayan sürümüyle eşleşecek şekilde `CPython` . (Kullanırken `python_d.exe` , bunu değiştirmeden bırakın.) |
    | **Bağlayıcı** > **Genel** | **Ek kitaplık dizinleri** | Yükleme için uygun şekilde *. lib* dosyaları içeren Python *Kitaplıklar* klasörünü ekleyin (örneğin,) `c:\Python36\libs` . *(.py* dosyalarını içeren *Lib* klasörünü *değil, .lib* dosyalarını içeren *lib* klasörünü işaret edin.)  |
    ::: moniker-end
    ::: moniker range="=vs-2017"
    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Genel** > **Hedef Ad** | Deyiminde Python'dan başvurmak istediğiniz modülün adını `from...import` belirtin. Python için modülü tanımlarken C++ içinde de aynı adı kullanırız. Proje adını modül adı olarak kullanmak için varsayılan **$(ProjectName) değerini bırakın.** `python_d.exe`için, `_d` adının sonuna ekleyin. |
    | | **Genel** > **Hedef Uzantı** | **.pyd** |
    | | **Proje Varsayılanları** > **Yapılandırma Türü** | **Dinamik Kitaplık (.dll)** |
    | **C/C++** > **Genel** | **Ek Dahil Dizinleri** | Python *include klasörünü,* örneğin, yüklemeniz için uygun şekilde `c:\Python36\include` ekleyin.  |
    | **C/C++** > **Ön işlemci** | **Önişlemci Tanımları** | Varsa, hata **ayıklama _DEBUG** sürümüyle eşleşmesi için hata ayıklama değerini **NDEBUG** olarak değiştirebilirsiniz. `CPython` `python_d.exe`(kullanırken, bunu değiştirmeden bırakın.) |
    | **C/C++** > **Kod Oluşturma** | **Çalışma Zamanı Kitaplığı** | **hata ayıklaması olmayan sürümüyle eşleşmesi** için çok iş parçacıklı DLL (/MD). `CPython` `python_d.exe`(kullanırken, bunu değiştirmeden bırakın.) |
    | **Linker** > **Genel** | **Ek Kitaplık Dizinleri** | *.lib* *dosyalarını içeren* Python libs klasörünü, örneğin, yüklemeniz için uygun şekilde `c:\Python36\libs` ekleyin. *(.py* dosyalarını içeren *Lib* klasörünü *değil, .lib* dosyalarını içeren *lib* klasörünü işaret edin.)  |
    ::: moniker-end
    
    > [!Tip]
    > Proje özelliklerinde C/C++ sekmesini görmüyorsanız, bunun nedeni projenin C/C++ kaynak dosyaları olarak tanımlayan herhangi bir dosya içermesidir. Bu durum, *.c* veya *.cpp* uzantısı olmadan bir kaynak dosya oluşturmanız durumunda ortaya çıkabilir. Örneğin, daha önce yeni öğe iletişim kutusunun yerine yanlışlıkla girdiyebilirsiniz, ancak Visual Studio dosyayı oluşturur ancak C/C++ özellikleri sekmesini etkinleştiren dosya türünü `module.coo` `module.cpp` "C/C+ Kod" olarak ayarlamaz. Dosyayı ile yeniden adlandırsanız bile bu tür yanlış kimlikler söz konusu olmaya devam `.cpp` ediyor. Dosya türünü düzgün ayarlamak için, dosyanın içinde dosyaya sağ tıklayın  **Çözüm Gezgini, Özellikler'i** seçin **ve** ardından Dosya Türü'lerini **C/C++ Kodu olarak ayarlayın.**

1. C++ projesine sağ tıklayın  ve yapılandırmalarınızı test etmek için Oluştur'u seçin (hem **Hata** Ayıkla hem de **Yayın).** *.pyd* dosyaları C++ proje **klasörünün** **değil** Hata Ayıklama ve **Sürüm** altındaki çözüm klasöründe bulunur.

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

1. Kodunuzun doğru olduğunu onaylamak için C++ projesini yeniden derleme.

1. Henüz bunu yapmadıysanız yukarıdaki adımları tekrarlayın ve aynı içeriklere sahip "superfastcode2" adlı ikinci bir proje oluşturun.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>C++ projelerini Python için uzantılara dönüştürme

C++ DLL'yi Python uzantısına yapmak için önce dışarı aktaran yöntemleri Python türleriyle etkileşimde bulunmak için değiştirmeniz gerekir. Ardından modülü dışarı aktaran bir işlev ve modülün yöntemlerinin tanımlarını eklersiniz.

Aşağıdaki bölümlerde, hem uzantıları hem de PyBind11 kullanarak bu adımların nasıl gerçekleştirileceği açıklanmaktadır `CPython` .

### <a name="cpython-extensions"></a>Cpyıthon uzantıları

Bu bölümde gösterilen özellikler hakkında daha fazla arka plan için, [Python/C API başvurusu el kitabına](https://docs.python.org/3/c-api/index.html) ve Python.org üzerindeki özellikle [Modül nesnelerine](https://docs.python.org/3/c-api/module.html) bakın (doğru belgeleri görüntülemek için sağ üstteki aşağı açılan denetimden Python sürümünüzü seçmenizi unutmayın).

1. *Module. cpp*' nin en üstünde *Python. h*' yi ekleyin:

    ```cpp
    #include <Python.h>
    ```

1. Metodu, `tanh_impl` Python türlerini kabul etmek ve döndürmek için değiştirin (a `PyObject*` , yani):

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. C++ `tanh_impl` Işlevinin Python 'a nasıl sunulduğunu tanımlayan bir yapı ekleyin:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh
        // The second is the C++ function with the implementation
        // METH_O means it takes a single PyObject argument
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

1. Kodunuzu doğrulamak için C++ projesini tekrar oluşturun. Hatalarla karşılaşırsanız aşağıdaki [sorun giderme](#troubleshooting) bölümüne bakın.

### <a name="pybind11"></a>PyBind11

Önceki bölümde yer alan adımları tamamladıysanız, C++ kodu için gerekli modül yapılarını oluşturmak üzere çok sayıda ortak kod kullanıldığını kesinlikle fark etmiş olursunuz. PyBind11, bir C++ üstbilgi dosyasındaki makroları, çok daha az kodla aynı sonucu gerçekleştiren makrolarla basitleştirir. Bu bölümde gösterilmekte olan arka plan için bkz. [PyBind11 temelleri](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (GitHub.com).

1. PIP: veya kullanarak PyBind11 'i yükler `pip install pybind11` `py -m pip install pybind11` . (Alternatif olarak, Python Ortamları penceresini kullanarak yükleyebilir ve sonraki adım için "PowerShell'de Aç" komutunu kullanabilirsiniz.)

1. Aynı terminalde veya `python -m pybind11 --includes` `py -m pybind11 --includes` çalıştırın. Bu, projenizin **C/C++** Genel Ek Dahil Dizinleri özelliğine eklemeniz gereken yolların listesini yazdıracak  >    >   (varsa `-I` ön eki kaldırma).

1. Yeni *bir module.cpp'nin* en üstünde, önceki bölümde yapılan değişikliklerden herhangi birini içermemektedir: *pybind11.h:*

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. *module.cpp'nin en* altında, `PYBIND11_MODULE` C++ işlevine giriş noktası tanımlamak için makroyu kullanın:

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

1. Kodunuzu doğrulamak için C++ projesini derleme. Hatalarla karşılaşırsanız sorun gidermeyle ilgili sonraki bölüme bakın.

### <a name="troubleshooting"></a>Sorun giderme

C++ modülü aşağıdaki nedenlerden dolayı derleyenene kadar başarısız olabilir:

- *Python.h* bulunamıyor (**E1696: "Python.h"** ve/veya C1083 kaynak dosyası açamıyor: Include dosyası açamıyor: **"Python.h":** Böyle bir dosya veya dizin yok): Proje özelliklerinde **C/C++** Genel Ek Dahil Dizinleri'nin yolunun Python yüklemenizin include klasörüne yönelik olduğunu  >    >   doğrulayın.  Çekirdek C++ projesi oluşturma [altında 6. adıma bakın.](#create-the-core-c-projects)

- Python kitaplıkları bulunamıyor: Proje özelliklerinde **Linker** Genel Ek Kitaplık Dizinleri'nde yolunun Python yüklemenizin kitaplık klasörüne sahip  >    >   *olduğunu* doğrulayın. Çekirdek C++ projesi oluşturma [altında 6. adıma bakın.](#create-the-core-c-projects)

- Hedef mimariyle ilgili linker hataları: C++ hedefinin proje mimarisini Python yüklemenizinkiyle eş olacak şekilde değiştirme. Örneğin, **Win32'yi** C++ projesiyle hedeflediniz ancak Python yüklemeniz 64 bit ise C++ projesini **x64 olarak değiştirebilirsiniz.**

## <a name="test-the-code-and-compare-the-results"></a>Kodu test etmek ve sonuçları karşılaştırmak

Artık PYTHON uzantıları olarak yapılandırılmış OLAN DLL'lere Python projesinden başvurabilirsiniz, modülleri içeri aktarabilirsiniz ve yöntemlerini kullanabilirsiniz.

### <a name="make-the-dll-available-to-python"></a>DLL'i Python için kullanılabilir yapma

DLL 'yi Python için kullanılabilir hale getirmek için iki yol vardır.

Python projesi ve C++ projesi aynı çözümde ise, ilk yöntem işe yarar. **Çözüm Gezgini**' e gidin, Python projenizde **Başvurular** düğümüne sağ tıklayın ve ardından **Başvuru Ekle**' yi seçin. Görüntülenen iletişim kutusunda, **Projeler** sekmesini seçin, hem **superfastcode** ve **superfastcode2** projelerini hem de **Tamam**' ı seçin.

![Superfastcode projesine başvuru ekleme](media/cpp-add-reference.png)

Aşağıdaki adımlarda açıklanan alternatif yöntem, modülü Python ortamınıza yükleyerek diğer Python projeleri için de kullanılabilir hale getirir. Daha kapsamlı belgeler için [ **setuptools** projesini](https://setuptools.readthedocs.io/) ziyaret edin.

1. C++ projesinde *Setup.py* adlı bir dosya oluşturun ve projeye sağ tıklayıp   >  **Yeni öğe** Ekle ' yi seçin. Ardından **C++ dosyası (. cpp)** öğesini seçin, dosyayı adlandırın `setup.py` ve **Tamam** ' ı seçin (dosyanın *. Kopyala* uzantısıyla adlandırılması, Visual Studio 'nun bunu C++ dosya şablonunu kullanarak Python olarak tanımasını sağlar). Dosya düzenleyicide göründüğünde, uzantı yöntemine uygun şekilde aşağıdaki kodu yapıştırın:

    **`CPython` Uzantılar (superfastcode Projesi):**

    ```python
    from setuptools import setup, Extension

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(
        name='superfastcode',
        version='1.0',
        description='Python Package with superfastcode C++ extension',
        ext_modules=[sfc_module]
    )
    ```

    **`PyBind11` (superfastcode2 Projesi):**

    ```python
    from setuptools import setup, Extension
    import pybind11

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2',
        sources=['module.cpp'],
        include_dirs=[pybind11.get_include()],
        language='c++',
        extra_compile_args=cpp_args,
        )

    setup(
        name='superfastcode2',
        version='1.0',
        description='Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules=[sfc_module],
    )
    ```

1. C++ projesinde *pyproject. TOML* adlı ikinci bir dosya oluşturun ve içine aşağıdaki kodu yapıştırın.

    ```toml
    [build-system]
    requires = ["setuptools", "wheel", "pybind11"]
    build-backend = "setuptools.build_meta"
    ```

1. Uzantıyı oluşturmak için, *pyproject. TOML* sekmesine sağ tıklayın ve "tam yolu Kopyala" yı seçin. (kullanmadan önce, *pyproject. TOML* adı yolundan silinir).

1. Çözüm Gezgini ' de, etkin Python ortamına sağ tıklayın ve *Python paketlerini Yönet*' i seçin.

    > [!Tip]
    > Paketi zaten yüklediyseniz, burada listelendiğini göreceksiniz. Devam etmeden önce kaldırmak için "X" düğmesine tıklayın.

1. Kopyalanmış yolu arama kutusuna yapıştırın ve `pyproject.toml` uçtan silin. Sonra bu dizinden yüklemek için ENTER tuşuna basın.

    > [!Tip]
    > Yükleme bir izin hatası nedeniyle başarısız olursa komutunu `--user` ekleyin ve yeniden deneyin.


### <a name="call-the-dll-from-python"></a>Python'dan DLL'i çağırma

Önceki bölümde açıklandığı gibi DLL'i Python'da kullanılabilir olduktan sonra, artık Python kodundan ve işlevlerini çağırabilir ve bunların performansını Python uygulamasıyla `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` karşılaştırabilirsiniz:

1. DLL'lerden dışarı aktaran yöntemleri çağırarak çıkışlarını görüntülemek için *.py* dosyanıza aşağıdaki satırları ekleyin:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Python programını **çalıştırın**( Hata Ayıklama olmadan Başlat veya Ctrl F5 ) ve C++ yordamlarının Python uygulamasından yaklaşık beş ile yirmi kat daha hızlı  >    + çalıştırılana dikkat edin. Tipik çıkış aşağıdaki gibi görünür:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Hata Ayıklama **Olmadan Başlat komutu devre** dışı bırakılırsa, Çözüm Gezgini'de Python projesine sağ **tıklayın** ve Başlangıç Projesi **Olarak Ayarla'yı seçin.**

1. Farklılıkların `COUNT` daha belirgin hale gelir ve değişkenlerini artırmayı deneyin. Hata **ayıklama derlemesi** daha az iyileştirilmiş  olduğundan ve  çeşitli hata denetimleri içerdiğinden, C++ modülünün hata ayıklama derlemesi de Yayın derlemelerinden daha yavaş çalışır. Karşılaştırma için bu yapılandırmalar arasında geçiş yapmaktan serbestsiniz (ancak geri dönüp Sürüm yapılandırması için önceki özellikleri **güncelleştirmeyi unutmayın).**

Çıktıda PyBind11 uzantısının uzantı kadar hızlı olmadığını, ancak saf Python uygulamasından çok daha hızlı `CPython` olması gerektiğini göreceksiniz. Bu farkın nedeni büyük ölçüde birden çok parametre, parametre adı veya anahtar sözcük bağımsız `METH_O` değişkenlerini desteklemeen çağrısını kullandık. PyBind11, çağıranlara Daha Python'a benzer bir arabirim sağlamak için biraz daha karmaşık bir kod oluşturur, ancak test kodu işlevi 500.000 kez çağıran bir kod olduğundan, sonuçlar bu ek yükü büyük ölçüde artırır!

Döngüyü yerel koda dönüştürerek ek `for` yükü daha da azaltabilirsiniz. Bu, her öğeyi işlemek için [Yineleyici protokolünü](https://docs.python.org/c-api/iter.html) (veya `py::iterable` [işlev parametresi](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)için PyBind11's türünü) kullanmayı kapsar. Python ve C++ arasındaki yinelenen geçişleri kaldırmak, diziyi işlemek için geçen süreyi azaltmak için etkili bir yoldur.

### <a name="troubleshooting"></a>Sorun giderme

`ImportError`Modülünüzü içeri aktarmaya çalışırken bir sorun varsa, bunun nedeni aşağıdakilerden biri olabilir:

* Bir proje başvurusu aracılığıyla oluştururken, C++ proje özelliklerinin, özellikle dahil etme ve kitaplık dizinleri için Python projeniz için etkinleştirilen Python ortamıyla eşleştiğinden emin olun.

* Çıkış dosyanızın adlandırılmış olduğundan emin olun `superfastcode.pyd` . Farklı bir ad veya uzantı içeri aktarılmasını engelleyecek.

* Modülünüzü *Setup.py* dosyasını kullanarak yüklediyseniz, Python projeniz için etkinleştirilmiş olan Python ortamında *PIP* komutunu çalıştırmanızdan emin olun. Çözüm Gezgini 'de Python ortamının genişletilmesi için bir girdi göstermelidir `superfastcode` .

## <a name="debug-the-c-code"></a>C++ kodunda hata ayıklama

Visual Studio, Python ve C++ kod hatalarını birlikte ayıklamayı destekler. Bu bölüm, **superfastcode** projesini kullanarak işlemi adım adım gösterir. adımlar **superfastcode2** projesi için aynıdır.

1. **Çözüm Gezgini**' de Python projesine sağ tıklayın, **Özellikler**' i seçin, **Hata Ayıkla** sekmesini seçin ve ardından hata ayıklama   >  **yerel kod hata ayıklamayı etkinleştir** seçeneğini belirleyin.

    > [!Tip]
    > Yerel kod hata ayıklamasını etkinleştirdiğinizde, bir program her ne kadar her zaman, duraklatmaya **devam etmek için herhangi bir tuşa basmadan** , Python çıkış penceresi hemen kaybolabilir. Bir duraklatma zorlamak için, `-i`   >  yerel kod hata ayıklamasını etkinleştirdiğinizde **hata ayıklama** sekmesindeki **yorumlayıcı bağımsız değişkenlerini** Çalıştır alanına seçeneği ekleyin. Bu bağımsız değişken, kod bittikten sonra Python yorumlayıcısını etkileşimli moda koyar, bu noktada  + çıkmak için CTRL **Z**  >  **ENTER** tuşlarına basmanız önerilir. (Alternatif olarak, Python kodunuzu değiştirmekte sorun yoksa program sonunda ve `import os` `os.system("pause")` deyimleri ebilirsiniz. Bu kod özgün duraklatma istemini yineler.)

1. Özellik   >  **değişikliklerini kaydetmek** için Dosya Kaydet'i seçin.

1. Derleme yapılandırmasını araç çubuğunda **Hata** ayıkla Visual Studio ayarlayın.

    ![Derleme yapılandırmasını Hata Ayıklama olarak ayarlama](media/cpp-set-debug.png)

1. Kodun hata ayıklayıcıda çalışması genellikle daha uzun sürer, .py dosyanız içinde değişkenini yaklaşık beş kat daha küçük bir değerle değiştirmek (örneğin, olarak değiştirmek) iyi `COUNT`  `500000` `100000` olabilir.

1. C++ kodunda, yönteminin ilk satırına bir kesme noktası ayarlayın, sonra hata ayıklayıcıyı `tanh_impl` (**F5** veya Hata Ayıklamayı Başlat   >  **) başlatın.** Kod çağrıldında hata ayıklayıcı durur. Kesme noktası isabeti yoksa yapılandırmanın Hata Ayıkla olarak ayar olup olmadığını ve projeyi (hata ayıklayıcıyı başlatılırken otomatik olarak olmaz) kayded olup olmadığını kontrol edin. 

    ![C++ kodunda kesme noktası durduruluyor](media/cpp-debugging.png)

1. Bu noktada C++ kodunda adım adım inceleyebilirsiniz, değişkenleri inceleyebilirsiniz ve bu şekilde devam edersiniz. Bu özellikler C++ ve [Python'da birlikte hata ayıklama içinde ayrıntılı olarak açıktır.](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)

## <a name="alternative-approaches"></a>Alternatif yaklaşımlar

Aşağıdaki tabloda açıklandığı gibi Python uzantıları oluşturmanın çeşitli bir anlamı vardır. ve için ilk iki `CPython` `PyBind11` giriş, bu makalede daha önce ele alınmıştır.

| Yaklaşım | Vintage | Temsili kullanıcılar | 
| --- | --- | --- |
| için C/C++ uzantı modülleri `CPython` | 1991 | Standart Kitaplık | 
| [PyBind11](https://github.com/pybind/pybind11) (C++için önerilir) | 2015 |  |
| [Cython](https://cython.org) (C için önerilir) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HNA](https://hpyproject.org/) | 2019 | |
| [myprivc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [scryptoto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [şifreleme](https://cryptography.io/), [PyPy](https://pypy.org/) |
| YÜZIK | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost. Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Ayrıca bkz.

Bu izlenecek yolda tamamlanan örnek [Python-Samples-vs-cpp-Extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub) üzerinde bulunabilir.
