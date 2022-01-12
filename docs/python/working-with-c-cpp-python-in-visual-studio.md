---
title: Python için C++ uzantıları yazma
description: bu makalede, karma mod hata ayıklama da dahil olmak üzere Visual Studio, cpyıthon ve PyBind11 kullanarak Python için C++ uzantısı oluşturma işlemi adım adım açıklanmaktadır.
ms.custom: devdivchpfy22
ms.date: 12/20/2021
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: b6a9d0e5c14283cd109d76e65be5b3e7797b1644
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803238"
---
# <a name="create-a-c-extension-for-python"></a>Python için C++ uzantısı oluşturma

Genellikle, bir Python yorumlayıcısının yeteneklerini genişletmek için C++ (veya C) dilinde yazılan modüller kullanılır. Bunları, alt düzey işletim sistemi özelliklerine erişimi etkinleştirmek için de kullanabilirsiniz.

Modüller üç birincil türde gelir:

- **Hızlandırıcı modülleri**: Python, yorumlanan bir dil olduğundan, daha yüksek performans için hızlandırma modüllerini C++ dilinde yazabilirsiniz.
- **Sarmalayıcı modüller**: Bu modüller, mevcut C/C++ arabirimlerini Python kodu 'na sunar veya Python 'dan kullanımı kolay bir "pythonic" API 'si sunar.
- **Alt düzey sistem erişim modülleri**: `CPython` çalışma zamanının, işletim sisteminin veya temeldeki donanımın alt düzey özelliklerine erişmek için bu modülleri oluşturabilirsiniz.

Bu makalede, `CPython` bir hiperbolik tanjantı hesaplayan ve Python kodundan çağıran için bir C++ uzantı modülü oluşturma işlemi adım adım açıklanmaktadır. Bu yordam, C++ ' ta aynı yordamın uygulanması için göreli performans kazancı göstermek üzere Python 'da ilk olarak uygulanır.

Makalede ayrıca C++ uzantısını Python için kullanılabilir hale getirmek için iki yol gösterilmektedir:

- `CPython` [Python belgelerinde](https://docs.python.org/3/c-api/)açıklandığı gibi standart uzantıları kullanın.
- Basitliği nedeniyle C++ 11 için önerdiğimiz [PyBind11](https://github.com/pybind/pybind11)kullanın.

bu izlenecek yolda, [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension)' de GitHub olan tamamlanmış örneği bulacaksınız.

## <a name="prerequisites"></a>Önkoşullar

- Python geliştirme iş yükü yüklüyken Visual Studio 2017 veya üzeri. İş yükü, yerel uzantılar için gerekli olan C++ iş yükünü ve araç kümelerini getiren Python yerel geliştirme araçlarını içerir.

    ![Python geliştirme seçeneklerinin listesinin ekran görüntüsü, Python yerel geliştirme araçları seçeneğini vurgular.](media/cpp-install-native.png)

    > [!NOTE]
    > **Veri bilimi ve analitik uygulamalar** iş yükünü yüklediğinizde, Python ve **Python yerel geliştirme araçları** seçeneği varsayılan olarak yüklenir.

Yükleme seçenekleri hakkında daha fazla bilgi için bkz. [Visual Studio Için Python desteğini yükleme](installing-python-support-in-visual-studio.md). Python 'u ayrı olarak yüklerseniz, yükleyicisindeki **Gelişmiş Seçenekler** altında **hata ayıklama sembollerini indir** ' i seçtiğinizden emin olun. Bu seçenek, Python kodunuz ve yerel kodunuz arasında karışık modda hata ayıklama kullanmanız için gereklidir.

## <a name="create-the-python-application"></a>Python uygulaması oluşturma

1. yeni **dosya** Project ' i seçerek Visual Studio yeni bir Python projesi oluşturun  >    >  . 

1. **Python** için arama yapın, **Python uygulama** şablonunu seçin, bir ad ve konum girin ve ardından **Tamam**' ı seçin.

1. Projenin *. Kopyala* dosyasında aşağıdaki kodu yapıştırın. [Python ile düzenlenen bazı özellikler](editing-python-code-in-visual-studio.md)hakkında daha fazla deneyim için kodu el ile girmeyi deneyin.  

   Bu kod, matematik kitaplığını kullanmadan bir hiperbolik tanjantı hesaplar ve yerel uzantılara göre hızlandırılırsınız.

    > [!Tip]
    > C++ ' da yeniden yazmadan önce kodunuzu saf Python 'da yazın. Bu şekilde, yerel kodunuzun doğru olduğundan emin olmak için daha kolay denetleyebilirsiniz.

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

1. Sonuçları görüntülemek için programı hata **ayıklama**  >  **olmadan Başlat** ' ı seçerek veya **CTRL + F5**' i seçerek çalıştırın.

   Bu `COUNT` değişkeni, kıyaslama süresini değiştirmek için ayarlayabilirsiniz. Bu izlenecek yol için, sayımı, kıyaslama iki saniye sürer şekilde ayarlayın.

   > [!TIP]
   > Değerlendirmeleri çalıştırdığınızda, her **zaman hata ayıklama**  >  **başlangıcını hata ayıklama olmadan** kullanın. bu, kodu Visual Studio hata ayıklayıcı içinde çalıştırdığınızda tabi olduğunuz ek yükün oluşmasını önlemeye yardımcı olur.

## <a name="create-the-core-c-projects"></a>Core C++ projelerini oluşturma

İki özdeş C++ projesi, *superfastcode* ve *superfastcode2* oluşturmak için bu bölümdeki yönergeleri izleyin. Daha sonra, her bir projede C++ kodunu Python 'da göstermek için ayrı bir yaklaşım kullanacaksınız.

1. **Çözüm Gezgini**, çözüme sağ tıklayın ve sonra   >  **yeni Project** ekle ' yi seçin. Visual Studio bir çözüm python ve C++ projelerini içerebilir ve bu, python için Visual Studio kullanmanın avantajlarından biridir.

1. **C++** üzerinde arama yapın, **boş proje**' yi seçin, ilk proje için **superfastcode** ' u veya ikinci proje için **superfastcode2** belirtin ve ardından **Tamam**' ı seçin.

    > [!Tip]
    > alternatif olarak, python yerel geliştirme araçlarının Visual Studio ' de yüklü olduğundan, python uzantı modülü şablonuyla başlayabilirsiniz. Şablonda daha fazla açıklananlar zaten var. 
    > 
    > Bu kılavuzda, ancak boş bir projeden başlamak, uzantı modülünün adım adım şekilde oluşturulmasını gösterir. İşlemi anladıktan sonra, kendi uzantılarınızı yazdığınızda zaman kazanmak için şablonu kullanabilirsiniz.

1. Yeni projede bir C++ dosyası oluşturmak için, **kaynak dosyalar** düğümüne sağ tıklayın ve ardından   >  **Yeni öğe** Ekle ' yi seçin.

1. **C++ dosyasını** seçin, It *Module. cpp* olarak adlandırın ve ardından **Tamam**' ı seçin.

    > [!Important]
    > *. Cpp* uzantısına sahip bir dosya, Izleyen adımlarda C++ Özellik sayfalarını açmak için gereklidir.

1. Ana araç çubuğunda aşağıdaki yapılandırmalardan birini seçmek için açılan menüyü kullanın:

   * 64 bitlik bir Python çalışma zamanı için **x64** yapılandırmasını etkinleştirin. 
   * 32 bitlik bir Python çalışma zamanı için **Win32** yapılandırmasını etkinleştirin.

1. **Çözüm Gezgini**, C++ projesine sağ tıklayın, **Özellikler**' i seçin ve ardından aşağıdakileri yapın: 

   a. **Yapılandırma** için **etkin (hata ayıklama)** girin.  
   b. **Platform** için, önceki adımda seçiminize bağlı olarak **etkin (x64)** veya **etkin (Win32)** girin.

    > [!NOTE]
    > Kendi projelerinizi oluştururken, hem *hata ayıklama* hem de *Sürüm* yapılandırmasını yapılandırmak isteyeceksiniz. Bu birimde, yalnızca hata ayıklama yapılandırmasını yapılandırıyorsunuz ve bunu Cpyıthon yayın yapısını kullanacak şekilde ayarlarız. Bu yapılandırma, bazı hata ayıklama özelliklerini onaylar dahil, C++ çalışma zamanının devre dışı bırakır. Cpyıthon hata ayıklama ikililerini kullanma (*python_d.exe*) farklı ayarlar gerektirir.

1. Aşağıdaki tabloda açıklandığı gibi özellikleri ayarlayın:

    ::: moniker range=">=vs-2019"

    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Hedef Adı** | Deyimlerdeki Python 'dan başvurmak için modülün adını belirtin `from...import` . Python için modül tanımladığınızda, C++ kodunda aynı adı kullanırsınız. Projenin adını modül adı olarak kullanmak için varsayılan değerini bırakın **$\<ProjectName>** .  İçin `python_d.exe` , `_d` adının sonuna ekleyin. |
    | | **Yapılandırma türü** | **Dinamik kitaplık (.dll)** |
    | | **Gelişmiş** > **Hedef dosya uzantısı** | **. PYD** |
    | | **Project varsayılanları** > **yapılandırma türü** | **Dinamik kitaplık (.dll)** |
    | **C/C++** > **Genel** | **Ek Içerme dizinleri** | Yüklemeniz için uygun olan Python *içerme* klasörünü ekleyin (örneğin, `c:\Python36\include` ).  |
    | **C/C++** > **Önişlemci** | **Önişlemci tanımları** | Varsa, **_DEBUG** değerini **ndebug** hata ayıklama sürümü olmayan bir tthon sürümüyle eşleşecek şekilde değiştirin. *python_d.exe* kullanırken, bu değeri değiştirmeden bırakın. |
    | **C/C++** > **Kod oluşturma** | **Çalışma zamanı kitaplığı** | **Çok iş PARÇACıKLı dll (/MD)** , Cpyıthon hata ayıklama sürümüyle eşleşecek şekilde. *python_d.exe* kullanırken, bu değeri **çok Iş PARÇACıKLı hata ayıklama dll (/MDD)** olarak bırakın. |
    | **Bağlayıcı** > **Genel** | **Ek kitaplık dizinleri** | Yüklemenize uygun şekilde *. lib* dosyaları içeren Python *Kitaplıklar* klasörünü ekleyin (örneğin, *c:\Python36\libs*). *.* Lib dosyalarını içeren *LIB* klasörünü *değil* ,. *lib* dosyalarını içeren *LIBS* klasörünü işaret ettiğinizden emin olun. |
    | | |

    ::: moniker-end

    ::: moniker range="=vs-2017"

    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Genel** > **Hedef adı** | Deyimlerdeki Python 'dan başvurmak için modülün adını belirtin `from...import` . Python için modül tanımladığınızda, C++ kodunda aynı adı kullanırsınız. Projenin adını modül adı olarak kullanmak için varsayılan değerini bırakın **$\<ProjectName>** . İçin `python_d.exe` , `_d` adının sonuna ekleyin. |
    | | **Genel** > **Hedef uzantısı** | **. PYD** |
    | | **Project varsayılanları** > **yapılandırma türü** | **Dinamik kitaplık (.dll)** |
    | **C/C++** > **Genel** | **Ek Içerme dizinleri** | Yüklemenize uygun şekilde Python *içerme* klasörünü ekleyin (örneğin, *c:\Python36\include*).  |
    | **C/C++** > **Önişlemci** | **Önişlemci tanımları** | Varsa, **_DEBUG** değerini **ndebug** , hata ayıklama sürümü olmayan sürümüyle eşleşecek şekilde değiştirin `CPython` . Kullanırken `python_d.exe` , bu değeri değiştirmeden bırakın. |
    | **C/C++** > **Kod oluşturma** | **Çalışma zamanı kitaplığı** | **Çok iş PARÇACıKLı dll (/MD)** , hata ayıklama sürümü olmayan sürümüyle eşleşecek şekilde `CPython` . Kullanırken `python_d.exe` , bu değeri değiştirmeden bırakın. |
    | **Bağlayıcı** > **Genel** | **Ek kitaplık dizinleri** | Yüklemenize uygun şekilde *. lib* dosyaları içeren Python *Kitaplıklar* klasörünü ekleyin (örneğin, *c:\Python36\libs*). *.* Lib dosyalarını içeren *LIB* klasörünü *değil* ,. *lib* dosyalarını içeren *LIBS* klasörünü işaret ettiğinizden emin olun. |
    | | |

    ::: moniker-end
    
    > [!NOTE]
    > **C/c++** sekmesi proje özelliklerinde görüntülenmiyorsa, proje c/c++ kaynak dosyaları olarak tanımlayan hiçbir dosya içermez. *. C* veya *. cpp* dosya uzantısı olmadan bir kaynak dosyası oluşturursanız bu durum oluşabilir. 
    > 
    > örneğin, yeni öğe iletişim kutusunda *modül. cpp* yerine yanlışlıkla *module. coo* 'yu girdiyseniz, Visual Studio dosyayı oluşturur, ancak c/C++ özellikleri sekmesini etkinleştiren dosya türünü *c/c + Code* olarak yapmaz. Bu tür hatalı kimlik, dosyayı *. cpp* dosya uzantısıyla yeniden adlandırsanız bile kalır. 
    > 
    > Dosya türünü düzgün şekilde ayarlamak için, **Çözüm Gezgini**' de dosyaya sağ tıklayın ve **Özellikler**' i seçin. Ardından, **dosya türü** için **C/C++ kodu**' nu seçin.

1. **Tamam**’ı seçin.

1. Yapılandırmaların (hem *hata ayıklama* hem de *yayın*) test etmek için C++ projesine sağ tıklayın ve ardından **Oluştur**' u seçin. 

   *. PYD* dosyalarını, C++ proje klasörünün kendisinde değil, *hata ayıklama* ve *yayın* altında bulunan *çözüm* klasöründe bulabilirsiniz.

1. C++ projesinin *Module. cpp* dosyasında aşağıdaki kodu ekleyin:

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

1. Daha önce yapmadıysanız, *superfastcode2* adlı ikinci bir projeyi aynı yapılandırmayla oluşturmak için önceki adımları tekrarlayın.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>C++ projelerini Python için uzantılara Dönüştür

C++ DLL 'ini Python için bir uzantı haline getirmek için, ilk olarak, içe aktarılmış yöntemleri Python türleriyle etkileşime geçmek üzere değiştirin. Daha sonra, modülün yöntemlerinin tanımlarıyla birlikte modülü dışarı aktaran bir işlev ekleyin.

Aşağıdaki bölümlerde, hem Cpyıthon uzantılarını hem de PyBind11 kullanarak bu adımları nasıl gerçekleştireceğiniz açıklanmaktadır.

### <a name="use-cpython-extensions"></a>Cpyıthon uzantılarını kullanma

Bu bölümde gösterilen koda daha fazla arka plan için, [Python/C API başvurusu el ile](https://docs.python.org/3/c-api/index.html) ve özellikle de [Modül nesneleri](https://docs.python.org/3/c-api/module.html) sayfasına bakın. Sağ üst taraftaki açılan listede Python sürümünüzü seçtiğinizden emin olun.

1. *Module. cpp* dosyasının en üstünde *Python. h* öğesini ekleyin:

    ```cpp
    #include <Python.h>
    ```

1. Metodu, `tanh_impl` Python türlerini kabul etmek ve döndürmek için değiştirin (yani, a `PyObject*` ):

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

1. Özel olarak, ifadesini kullandığınızda, Python kodunuzda başvurmak istediğiniz modülü tanımlayan bir yapı ekleyin `from...import` . 

   Bu kodda içeri aktarılan adın, **yapılandırma özellikleri**  >  **genel**  >  **hedef adı** altındaki proje özelliklerindeki değerle eşleşmesi gerekir. 

   Aşağıdaki örnekte, `"superfastcode"` Modül adı, `from superfastcode import fast_tanh` içinde tanımlandığı için Python 'da kullanabileceğiniz anlamına gelir `fast_tanh` `superfastcode_methods` . C++ projesine ait *modül. cpp* gibi dosya adları önemsizdir.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. `PyInit_<module-name>` *\<module-name>* C++ projesinin **genel**  >  **hedef adı** özelliğiyle tam olarak eşleşen, adlandırılmış olması gereken modül yüklediğinde Python tarafından çağrı yapan bir yöntem ekleyin. Diğer bir deyişle, proje tarafından oluşturulan *. PYD* dosyasının dosya adıyla eşleşir.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Kodunuzu doğrulamak için C++ projesini tekrar oluşturun. Hatalarda, ["sorun giderme"](#troubleshoot-compiling-failures) bölümüne bakın.

### <a name="use-pybind11"></a>PyBind11 kullanma

Önceki bölümde yer alan adımları tamamladıysanız, C++ kodu için gerekli modül yapılarını oluşturmak üzere çok sayıda ortak kod kullanıldığını fark etmiş olursunuz. PyBind11, aynı sonucu elde eden, ancak çok daha az kodlu bir C++ üstbilgi dosyasındaki makrolar aracılığıyla işlemi basitleştirir. 

Bu bölümdeki kod hakkında daha fazla bilgi için bkz. [PyBind11 temelleri](https://github.com/pybind/pybind11/blob/master/docs/basics.rst).

1. PIP: veya kullanarak PyBind11 'i yükler `pip install pybind11` `py -m pip install pybind11` . 

   Alternatif olarak, Python ortamları penceresini kullanarak PyBind11 yükleyebilirsiniz ve sonra bir sonraki adımda **PowerShell 'In aç** komutunu kullanabilirsiniz.

1. Aynı terminalde, veya öğesini `python -m pybind11 --includes` çalıştırın `py -m pybind11 --includes` . 

   Bu eylem, projenizin **C/C++**  >  **genel**  >  **ek içerme dizinleri** özelliğine eklemeniz gereken yolların bir listesini yazdırır. Varsa `-I` , ön eki kaldırmayı unutmayın.

1. Önceki bölümde yer alan herhangi bir değişikliği içermeyen yeni bir *Module. cpp* üst kısmında, *pybind11. h* ekleyin:

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

1. Kodunuzu doğrulamak için C++ projesi oluşturun. Hatalarla karşılaşırsanız, çözümler için "derleme hatalarını giderme" başlıklı sonraki bölüme bakın.

### <a name="troubleshoot-compiling-failures"></a>Derleme hataları sorunlarını giderme

C++ modülü aşağıdaki nedenlerden dolayı derlenemeyebilir:

- Hata: *Python. h* bulunamıyor (**E1696: kaynak dosya "Python. h"** ve/veya **C1083: Içerme dosyası açılamıyor: "Python. h": böyle bir dosya veya dizin yok**) 

  Çözüm: proje özelliklerindeki **C/C++**  >  **genel**  >  **ek içerme dizinlerinin** yolu, Python yüklemenizin *içerme* klasörünü işaret ettiğini doğrulayın. [Core C++ projesi oluşturma](#create-the-core-c-projects)altındaki 6. adıma bakın.

- Hata: Python kitaplıkları bulunamıyor 
 
   Çözüm: yol: **bağlayıcı**  >  **genel**  >  **Ek kitaplık dizinlerinin** proje özelliklerinde, Python yüklemenizin *LIBS* klasörüne işaret ettiğini doğrulayın. [Core C++ projesi oluşturma](#create-the-core-c-projects)altındaki 6. adıma bakın.

- Hedef mimarisiyle ilgili bağlayıcı hataları
   
   Çözüm: C++ hedefinin proje mimarisini Python yüklemenizin ile eşleşecek şekilde değiştirin. Örneğin, C++ projesi ile Win32 hedefliyorsanız, ancak Python yüklemeniz 64 bit ise, C++ projesini x64 olarak değiştirin.

## <a name="test-the-code-and-compare-the-results"></a>Kodu test edin ve sonuçları karşılaştırın

Dll 'Leri artık Python uzantıları olarak yapılandırılmış olduğuna göre, bu dosyalara Python projesinden başvurabilir, modülleri içeri aktarabilir ve yöntemlerini kullanabilirsiniz.

### <a name="make-the-dll-available-to-python"></a>DLL dosyasını Python için kullanılabilir hale getirme

DLL 'yi çeşitli yollarla Python için kullanılabilir hale getirebilirsiniz. Dikkate alınması gereken iki yaklaşım aşağıda verilmiştir: 

* Python projesi ve C++ projesi aynı çözümde ise bu ilk yöntem işe yarar. Şunları yapın: 

   1. **Çözüm Gezgini**, Python projenizde **Başvurular** düğümüne sağ tıklayın ve ardından **Başvuru Ekle**' yi seçin. 
   1. Görüntülenen iletişim kutusunda, **Projeler** sekmesini seçin, hem **superfastcode** ve **superfastcode2** projelerini hem de **Tamam**' ı seçin.

      !["Superfastcode" projesine nasıl başvuru ekleneceğini gösteren ekran görüntüsü.](media/cpp-add-reference.png)

* Alternatif bir yöntem, modülü diğer Python projeleri için kullanılabilir hale getiren Python ortamınıza modülünü de yüklüyor. Daha fazla bilgi için bkz. [ **setuptools** proje belgeleri](https://setuptools.readthedocs.io/). Şunları yapın:

    1. C++ projesinde *Setup.py* adlı bir dosya oluşturun ve projeye sağ tıklayıp   >  **Yeni öğe** Ekle ' yi seçin. 
    
    1. **C++ dosyası (. cpp)** öğesini seçin, dosyayı *Setup.py* olarak adlandırın ve ardından **Tamam**' ı seçin.
    
       dosyayı *. kopyala* uzantısıyla adlandırırken, C++ dosya şablonunun kullanılmasına karşın bunu bir Python dosyası olarak tanıması Visual Studio olur. 

       Dosya düzenleyicide göründüğünde, uzantı yöntemine uygun şekilde aşağıdaki kodu yapıştırın:
    
        **`CPython` Uzantılar için (superfastcode Projesi)**:
    
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
    
        **İçin `PyBind11` (superfastcode2 Projesi)**:
    
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
    
    1. C++ projesinde *pyproject. TOML* adlı ikinci bir dosya oluşturun ve içine aşağıdaki kodu yapıştırın:
    
        ```toml
        [build-system]
        requires = ["setuptools", "wheel", "pybind11"]
        build-backend = "setuptools.build_meta"
        ```
    
    1. Uzantıyı derlemek için Open *pyproject. TOML* sekmesine sağ tıklayın ve ardından **tam yolu Kopyala**' yı seçin. Bu adı kullanmadan önce, *pyproject. TOML* adını yolundan silmelisiniz.
    
    1. **Çözüm Gezgini**' de, etkin Python ortamına sağ tıklayın ve ardından **Python paketlerini Yönet**' i seçin.
    
        > [!Tip]
        > Paketi zaten yüklediyseniz, burada listelendiğini görürsünüz. Devam etmeden önce **X** simgesini tıklatarak kaldırın.
    
    1. Arama kutusunda, kopyalanmış yolu yapıştırın, sonundaki *pyproject. TOML* dosyasını silin ve ardından bu dizinden modülü yüklemek için **ENTER** ' u seçin.
    
        > [!Tip]
        > Yükleme bir izin hatası nedeniyle başarısız olursa, sonuna *--User* ekleyin ve komutu yeniden deneyin.


### <a name="call-the-dll-from-python"></a>Python'dan DLL'i çağırma

Önceki bölümde açıklandığı gibi DLL'i Python için kullanılabilir olduktan sonra Python kodundan ve işlevlerini çağırabilir ve bunların performansını Python uygulamasıyla `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` karşılaştırabilirsiniz. DLL'i aramak için şunları yapın:

1. DLL'lerden dışarı aktaran yöntemleri çağıran ve çıkışlarını görüntülemek için *.py* dosyanıza aşağıdaki satırları ekleyin:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Hata Ayıklama Olmadan Başlat'ı **veya**  >   Ctrl+F5 tuşlarını seçerek Python programını çalıştırın.

    > [!NOTE]
    > Hata Ayıklama **Olmadan Başlat komutu devre** dışı **bırakılırsa, Çözüm Gezgini'da** Python projesine sağ tıklayın ve Başlangıç Olarak Ayarla'yı **Project.**  

    C++ yordamlarının Python uygulamasından yaklaşık beş ile 20 kat daha hızlı çalıştırılana dikkat edin. Tipik çıkış aşağıdaki gibi görünür:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

1. Farklılıkların daha `COUNT` belirgin hale gelir ve değişkenlerini artırmayı deneyin. 

    Hata *ayıklama derlemesi* daha az iyileştirilmiş  olduğundan ve çeşitli hata denetimleri içerdiğinden, C++ modülünün hata ayıklama derlemesi de yayın derlemelerinden daha yavaş çalışır. Karşılaştırma için bu yapılandırmalar arasında geçiş yapmakta serbestsiniz, ancak geri dönüp sürüm yapılandırması için daha önce ayara sahip özellikleri güncelleştirmeyi unutmayın.

Çıktıda PyBind11 uzantısının CPython uzantısı kadar hızlı olmadığını, ancak saf Python uygulamasından daha hızlı olması gerektiğini göreceksiniz. Bu fark büyük ölçüde, birden çok parametreyi, parametre adlarını veya anahtar sözcük bağımsız değişkenlerini `METH_O` desteklemez çağrısını kullandınız. PyBind11, çağıranlara Daha Python'a benzer bir arabirim sağlamak için biraz daha karmaşık kod üretir. Ancak test kodu işlevi 500.000 kez çağıran sonuçlar bu ek yükü önemli ölçüde artırır!

Döngüyü yerel koda dönüştürerek ek `for` yükü daha da azaltabilirsiniz. Bu yaklaşım, her öğeyi [işlemeye yönelik](https://docs.python.org/c-api/iter.html) bir kez daha fazla iterator protokolünü (veya işlev parametresi için PyBind11 `py::iterable` türünü) [](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)kullanmayı içerir. Python ve C++ arasındaki yinelenen geçişleri kaldırmak, diziyi işleme süresini azaltmanın etkili bir yolu olur.

### <a name="troubleshoot-importing-errors"></a>İçeri aktarma hatalarını giderme

Modülünü `ImportError` içeri aktarmaya çalışırken bir ileti alırsanız, bu iletiyi aşağıdaki yöntemlerden birini kullanabilirsiniz:

* Bir proje başvurusu aracılığıyla derlerken, C++ proje özelliklerinizin Başta Dahil Ve Kitaplık dizinleri  olmak üzere Python projeniz için etkinleştirilen Python ortamıyla *eşleşir.*

* Çıkış dosyanıza *superfastcode.pyd adını verin.* Başka bir ad veya uzantı, uzantının içe aktarılamayacak.

* *modülünü* setup.py dosyasını kullanarak yükledikten sonra Python projeniz için etkinleştirilen Python ortamında *pip* komutunu çalıştırarak emin olun. Içinde Python ortamını Çözüm Gezgini süper kod için bir *giriş görüntülemesi gerekir.*

## <a name="debug-the-c-code"></a>C++ kodunda hata ayıklama

Visual Studio Python ve C++ kodunda birlikte hata ayıklamayı destekler. Bu bölümde, süper kod projesini kullanarak *işlemi adım adım ilerlersiniz.* Bu işlem *superfastcode2 projesi için aynıdır.*

1. Bu **Çözüm Gezgini** Python projesine sağ tıklayın, Özellikler'i  **seçin,** Hata Ayıkla sekmesini seçin ve yerel kodda hata ayıklamayı etkinleştir  >  **seçeneğini** belirleyin.

    > [!Tip]
    > Yerel kod hata ayıklamayı etkinleştirdikten sonra, program tamam olduktan hemen sonra duraklatma devam etmek için herhangi bir tuşa bas'ı vermeden Python çıkış **penceresi kapanabilir.** 
    >
    > Çözüm: Yerel kod hata ayıklamayı etkinleştirdikten sonra duraklatma zorlamak için Hata Ayıklama sekmesindeki Yorumlayıcı Bağımsız Değişkenlerini `-i` Çalıştır alanına   >   **seçenek** ekleyin. Bu bağımsız değişken, kod çalıştır edildikten sonra Python yorumlayıcıyı etkileşimli moda koyar. Bu noktada Ctrl+Z ve enter tuşlarına basarak pencereyi kapatmanız gerekir. 
    >
    > Alternatif olarak, Python kodunuzu değiştirmekte sorun yoksa program sonunda `import os` ve `os.system("pause")` deyimleri abilirsiniz. Bu kod, özgün duraklatma istemini yineler.

1. Özellik   >  **değişikliklerini kaydetmek** için Dosya Kaydet'i seçin.

1. Uygulama araç Visual Studio, derleme yapılandırmasını Hata Ayıkla **olarak ayarlayın.**

    ![Araç çubuğundaki "Hata Ayıkla" ayarının Visual Studio görüntüsü.](media/cpp-set-debug.png)

1. Kodun hata ayıklayıcıda çalışması genellikle daha uzun sürer, .py dosyanız değişkenini varsayılan değerden yaklaşık beş kat daha küçük bir `COUNT` değerle değiştirmek iyi olabilir.  Örneğin, **500000 ile** **100000 arasında bir değişiklik.**

1. C++ kodunda, yönteminin ilk satırına bir kesme noktası ayarlayın ve F5'i veya Hata Ayıklamayı Başlat Hata Ayıklamayı Başlat'ı seçerek `tanh_impl` **hata**   >  **ayıklayıcıyı başlatabilirsiniz.** 

    Kesme noktası kodu çağrıldında hata ayıklayıcı durur. Kesme noktası isabet etmese yapılandırmanın Hata Ayıkla olarak  ayar olup olmadığını ve hata ayıklayıcıyı başlatmanız sırasında otomatik olarak olmayan projeyi kayded onay kutusunu kontrol edin.

    ![Kesme noktası içeren C++ kodunun ekran görüntüsü.](media/cpp-debugging.png)

1. Kesme noktası üzerinde C++ kodunda adım adım atabilir, değişkenleri inceleyebilirsiniz ve bu şekilde devam eder. Bu özellikler hakkında daha fazla bilgi için bkz. [Python ve C++'da birlikte hata ayıklama.](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)

## <a name="alternative-approaches"></a>Alternatif yaklaşımlar

Python uzantılarını aşağıdaki tabloda açıklandığı gibi çeşitli yollarla oluşturabilirsiniz. İlk iki satır olan `CPython` ve , bu makalede ele `PyBind11` alınmıştır.

| Yaklaşım | Vintage | Temsili kullanıcılar | 
| --- | --- | --- |
| için C/C++ uzantı modülleri `CPython` | 1991 | Standart Kitaplık | 
| [PyBind11](https://github.com/pybind/pybind11) (C++için önerilir) | 2015 |  |
| [Cython](https://cython.org) (C için önerilir) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| ctype'lar | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [şifreleme ,](https://cryptography.io/) [pypy](https://pypy.org/) |
| YU -DUM | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Ayrıca bkz.

Bu kılavuzda yer alan tamamlanmış örneği [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension)GitHub üzerinde bulabilirsiniz.
